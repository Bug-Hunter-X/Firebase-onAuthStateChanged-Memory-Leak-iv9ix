# Firebase onAuthStateChanged Memory Leak
This repository demonstrates a common error when using Firebase's onAuthStateChanged function: forgetting to unsubscribe from the listener. This can lead to memory leaks and unexpected behavior in your application.

## The Problem
The `onAuthStateChanged` function returns an unsubscribe function that must be called when the listener is no longer needed.  Failure to do so will leave the listener active, potentially leading to multiple listeners being attached and consuming unnecessary resources.

## The Solution
The solution is simple: call the returned unsubscribe function when you're finished with the listener. This will cleanly remove the listener and prevent memory leaks.

## How to reproduce the bug
1. Clone the repository.
2. Run `npm install`
3. Run the `bug.js` file.  Observe the repeated console logs.
4. Run the `bugSolution.js` file. Observe that console logs stop after the initial event.