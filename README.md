# Express.js Route Handler Error

This repository demonstrates a common error in Express.js route handlers:  failure to handle invalid input.  Specifically, the route `/users/:id` does not handle cases where `:id` is not a valid integer, leading to a server-side error.

The `bug.js` file contains the buggy code. The `bugSolution.js` file provides a corrected version with robust error handling.

## Bug

The original code attempts to parse the user ID as an integer using `parseInt()` without checking if the result is actually a number.  If the ID is not an integer (e.g., a string or a non-numeric value), `parseInt()` returns `NaN`, leading to a runtime error when the code attempts to use it for comparison.

## Solution

The solution adds error handling to check if the parsed ID is a valid number using `isNaN()`. If the ID is invalid, it returns an appropriate HTTP error response (400 Bad Request) to the client.  This prevents server crashes and provides a meaningful error message.