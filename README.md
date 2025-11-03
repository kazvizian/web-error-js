# @kazvizian/web-error

Utilities for modeling, validating, and handling web-app errors in TypeScript.

## Install

```sh
bun add @kazvizian/web-error
# or
npm i @kazvizian/web-error
# or
pnpm add @kazvizian/web-error
```

## Usage

```ts
import { FEError, BEError, BEMultiError, isFEError, isBEError, isBEMultiError } from "@kazvizian/web-error"

throw new FEError("INVALID_INPUT", "Form has an invalid field", "signup-form", { field: "email" })

const beErr = new BEError("USER_NOT_FOUND", "No user with that id", 404, "GET /api/users/:id")

const multi = new BEMultiError([
  { code: "INVALID_EMAIL", message: "Email invalid", status: 400 },
  { code: "PASSWORD_WEAK", message: "Password too weak", status: 400 }
], "VALIDATION_ERRORS", 400, "POST /api/register")

function handle(e: unknown) {
  if (isFEError(e)) {
    // FEErrorObject
  } else if (isBEError(e)) {
    // BEErrorObject
  } else if (isBEMultiError(e)) {
    // BEMultiErrorObject
  }
}
```

## API

- FEError, BEError, BEMultiError: strongly-typed Error classes with optional details metadata.
- isFEError, isBEError, isBEMultiError: type guards for runtime checking.
- Types: FEErrorObject, BEErrorObject, BEMultiErrorObject, BEErrorRespone, FieldKey.

## License

MIT © KazViz
