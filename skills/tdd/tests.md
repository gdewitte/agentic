# Good And Bad Tests

## Good Tests

Good tests verify observable behavior through public interfaces.

```typescript
test("user can checkout with valid cart", async () => {
  const cart = createCart();
  cart.add(product);

  const result = await checkout(cart, paymentMethod);

  expect(result.status).toBe("confirmed");
});
```

Characteristics:

- Tests behavior users or callers care about.
- Uses the public interface.
- Survives internal refactors.
- Describes what happens, not how it happens.
- Keeps each test focused on one behavior.

## Bad Tests

Implementation-detail tests couple to internal structure.

```typescript
test("checkout calls paymentService.process", async () => {
  const mockPayment = jest.mock(paymentService);

  await checkout(cart, payment);

  expect(mockPayment.process).toHaveBeenCalledWith(cart.total);
});
```

Red flags:

- Mocking internal collaborators.
- Testing private methods.
- Asserting internal call counts or order.
- Breaking when behavior is unchanged but internals are refactored.
- Naming the test after how the code works instead of what behavior exists.

Side-channel verification also couples tests to implementation details.

```typescript
test("createUser saves to database", async () => {
  await createUser({ name: "Alice" });

  const row = await db.query("SELECT * FROM users WHERE name = ?", ["Alice"]);

  expect(row).toBeDefined();
});
```

Prefer verifying through the public interface.

```typescript
test("createUser makes user retrievable", async () => {
  const user = await createUser({ name: "Alice" });

  const retrieved = await getUser(user.id);

  expect(retrieved.name).toBe("Alice");
});
```

Tautological tests repeat the implementation in the assertion.

```typescript
test("calculateTotal sums line items", () => {
  const items = [{ price: 10 }, { price: 5 }];
  const expected = items.reduce((sum, item) => sum + item.price, 0);

  expect(calculateTotal(items)).toBe(expected);
});
```

Use an independent expected value instead.

```typescript
test("calculateTotal sums line items", () => {
  expect(calculateTotal([{ price: 10 }, { price: 5 }])).toBe(15);
});
```
