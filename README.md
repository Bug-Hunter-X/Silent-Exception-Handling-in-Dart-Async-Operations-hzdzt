# Silent Exception Handling in Dart Async Operations

This repository demonstrates a subtle bug in Dart asynchronous programming involving exception handling. The `fetchData` function fetches data from a remote API and includes error handling within a `try-catch` block. However, if the `rethrow` keyword is omitted, exceptions are silently caught without proper propagation, potentially masking errors.

## Bug

The primary issue lies in the `fetchData` function. The `catch` block logs the error but doesn't explicitly re-throw the exception, resulting in the `main` function not noticing any error even if `fetchData` fails. This leads to silent failures, making debugging difficult.

## Solution

The solution involves explicitly re-throwing the caught exception using `rethrow;`. This ensures the exception propagates up the call stack, allowing the `main` function to handle it appropriately.  The corrected code is provided in `bugSolution.dart`.