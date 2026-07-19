# When To Mock

Mock at system boundaries only:

- External APIs.
- Email, payment, auth, and analytics providers.
- Time and randomness.
- File system calls when a real fixture would be brittle or slow.
- Databases only when a test database is impractical.

Do not mock:

- Your own modules.
- Internal collaborators.
- Code you control.

## Designing For Mockability

At system boundaries, design interfaces that are easy to replace in tests.

Use dependency injection for external dependencies.

```typescript
function processPayment(order, paymentClient) {
  return paymentClient.charge(order.total);
}
```

Avoid constructing external clients deep inside behavior you need to test.

```typescript
function processPayment(order) {
  const client = new StripeClient(process.env.STRIPE_KEY);

  return client.charge(order.total);
}
```

Prefer SDK-style interfaces over generic fetchers.

```typescript
const api = {
  getUser: (id) => fetch(`/users/${id}`),
  getOrders: (userId) => fetch(`/users/${userId}/orders`),
  createOrder: (data) => fetch("/orders", { method: "POST", body: data }),
};
```

Avoid generic fetch wrappers that force conditional logic inside mocks.

```typescript
const api = {
  fetch: (endpoint, options) => fetch(endpoint, options),
};
```

Specific boundary methods make test setup clearer, return shapes smaller, and type contracts more precise.
