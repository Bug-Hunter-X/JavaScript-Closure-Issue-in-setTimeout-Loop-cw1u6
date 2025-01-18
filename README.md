# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common closure-related issue in JavaScript when using `setTimeout` within a loop.  The expected behavior is to log numbers 0-9 after a one-second delay each.  However, due to how closures work with loop variables, this code produces an unexpected result.

## Bug Description
The `setTimeout` callback function does not capture the value of `i` at each iteration of the loop.  Instead, it captures the reference to `i`. By the time the `setTimeout` functions finally execute, the loop has already completed, and `i` will be its final value (10). Therefore, the code logs '10' ten times.

## Solution
The solution involves using an immediately invoked function expression (IIFE) to create a new scope for each iteration of the loop, ensuring each callback captures the correct value of `i`.