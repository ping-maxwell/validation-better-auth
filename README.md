# validation-better-auth

A flexible and extensible validation plugin for the Better Auth framework. This package allows developers to validate API request using any standard schema library (e.g. Zod, Valibot, ArkType). We also support Yup by wrapping the schema internally to Standard Schema.

## usage

```ts
import { betterAuth } from "better-auth"
import { validator, StandardAdapter} from "validation-better-auth"
 
export const auth = betterAuth({
    // ... other config options
    appName: "My App", // provide your app name. It'll be used as an issuer.
    plugins: [
        validator(
      [
        {path: "/sign-up/email", adapter: StandardAdapter(SignupSchema)},
        {path: "/sign-in/email", adapter: StandardAdapter(SignInSchema)},
        {path: "/two-factor/enable", adapter: StandardAdapter(PasswordSchema)},
        {path: "/two-factor/disable", adapter: StandardAdapter(PasswordSchema)},
        {path: "/two-factor/verify-otp", adapter: StandardAdapter(twoFactorSchema)},
        {path: "/forgot-password", adapter: StandardAdapter(ForgotPasswordSchema)},
      ]
    ),
    ]
})```
