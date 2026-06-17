---
name: commit-message
description: Generate concise commit messages with a conventional header, optional structured body, and optional reference section.
---
# Commit Message

Use this skill when drafting commit messages or reviewing commit style.

## Preferred Header

Use this default format:

```text
<type>(<scope>): <short summary>
```

The value inside `(<scope>)` is the area of change, such as the component, subsystem, or surface affected by the work.

If no clear scope exists, omit it:

```text
<type>: <short summary>
```

Determine the scope from the context of the changes rather than forcing a fixed set of scope names.

Examples:

```text
feat(terraform): add artifact storage module
fix: handle empty monitor response
```

## Suggested Body

Use a short markdown body only when it adds value:

```text
## 🚀 Summary/Context
- readable bullet that explains why the change is needed
- readable bullet that explains what changed

## 🔎 Scope
- readable bullet that names the affected area, behavior, or resource

## 🔬 Validation
- run `command-that-was-actually-executed`
- not run: short reason if validation was not executed
```

Keep each section as bullet points. Each bullet should read like a short sentence, not a fragment, so a reviewer can immediately understand the context, scope, and validation for the change.

Use backticks for code references, file paths, resource names, config keys, literals, and commands. For example, write `terraform plan`, `ci-key-vaults.tf`, `azurerm_key_vault`, and `runner_role` instead of plain text.

The `## 🔬 Validation` section must reflect actual validation commands that were run. Do not use it for passive inspection such as "reviewed files" or "checked the diff". If no validation command was run, say `not run:` and include the reason.

For Terraform changes, prefer concrete commands such as `terraform fmt -check`, `terraform init -backend=false`, `terraform validate`, `terraform plan`, or `pre-commit run terraform_tflint --files <paths>` when those commands were actually executed.

When amending an existing commit message, remember that `git commit --amend` normally runs commit hooks. If hooks run, mention their result separately from the `## 🔬 Validation` commands unless they are the explicit validation being recorded. Use `--no-verify` only when the user has approved bypassing hooks or when the surrounding task already established that hook execution is inappropriate.

## Optional Reference

Only add a `## Reference` section when the user explicitly asks for one or provides a ticket/reference they want included. If no reference is provided, do not add that section.

Example:

```text
fix(api): handle empty monitor response

## 🚀 Summary/Context
- handle empty responses returned by the monitor API
- add test coverage for the empty payload path

## 🔎 Scope
- update the `monitor` API response handling path

## 🔬 Validation
- run `pytest tests/test_monitor.py`

## Reference
```

## Workflow

1. Keep the header concise and action-oriented.
2. Prefer conventional commit types such as `feat`, `fix`, `chore`, `refactor`, `docs`, `test`, and `ci`.
3. Include a body only when it improves clarity.
4. Use `## 🚀 Summary/Context`, `## 🔎 Scope`, and `## 🔬 Validation` for structured bodies.
5. Wrap code references, commands, file paths, resource names, config keys, and literals in backticks.
6. In `## 🔬 Validation`, list only commands actually run, or write `not run:` with the reason.
7. Add `## Reference` only when the user explicitly provides or requests a reference.

## Validation Template

```text
feat(scope): short summary

## 🚀 Summary/Context
- readable bullet that explains why the change is needed
- readable bullet that explains what changed

## 🔎 Scope
- readable bullet that names the affected area or behavior

## 🔬 Validation
- run `command-that-was-actually-executed`
```
