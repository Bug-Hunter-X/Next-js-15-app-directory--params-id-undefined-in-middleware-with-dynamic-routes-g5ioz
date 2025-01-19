# Next.js 15 Middleware Bug: Undefined params.id in Dynamic Routes

This repository demonstrates a potential bug in Next.js 15's `app` directory when using middleware with dynamic routes.  The problem arises because the middleware function might execute *before* the route parameters are fully resolved. This can lead to `params.id` being `undefined` even when a valid ID is passed in the URL.

## Reproduction Steps

1. Clone this repository.
2. Run `npm install`.
3. Run `npm run dev`.
4. Navigate to a route like `/users/1`.  You'll see the error in the console.

## Solution

The solution involves ensuring proper handling of potential `undefined` values in middleware.  This usually involves adding a check for the existence of the parameters or carefully structuring the middleware logic to only access them once they are available.

## Additional Notes

This bug is specific to the way Next.js 15 handles middleware and dynamic routes. Older versions or different routing strategies might not exhibit this behavior.