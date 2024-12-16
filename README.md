# Express.js Route Handler Bug: Missing Error Handling

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input.

The `bug.js` file contains a vulnerable route that doesn't handle cases where the user ID is not a valid integer.  This can lead to unexpected errors or crashes.

The `bugSolution.js` file provides a corrected version with robust error handling to prevent such issues. 

## Bug Description
The route handler attempts to parse the user ID as an integer using `parseInt()` without verifying if the input is actually a number. If the input is not a number (e.g., a string or special character), `parseInt()` will return `NaN`, causing the `users.find()` method to fail silently or throw an error, leading to application instability.

## How to reproduce
1. Clone this repository.
2. Run `npm install express`.
3. Run `node bug.js`.
4. Send a GET request to `/users/abc` (or any non-numeric ID). You'll encounter an error.

## Solution
The solution involves adding input validation to check if the `userId` is a number. If it's not a number, return a suitable error response.
