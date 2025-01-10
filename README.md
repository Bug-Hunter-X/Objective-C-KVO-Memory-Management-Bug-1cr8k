# Objective-C KVO Memory Management Bug
This repository demonstrates a common bug in Objective-C related to Key-Value Observing (KVO) and memory management.  Failure to properly remove observers before the observed object is deallocated can lead to crashes or undefined behavior. The example shows how to reproduce the bug and demonstrates a solution to prevent it. 

## Problem
When an object is deallocated while an observer is still registered, the observer might attempt to access deallocated memory leading to a crash.  This is particularly problematic with weak references. 

## Solution
Always remove KVO observers in the `-dealloc` method of the observer object.  In the example, we show how this can be done and how to check for nil before removing the observer to prevent errors if the object is already deallocated.