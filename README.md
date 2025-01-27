# React Native useRef: Accessing 'current' Property Before Assignment

This repository demonstrates a common but subtle bug in React Native when using the `useRef` hook. The issue arises from attempting to access the `current` property of a ref before it has been properly assigned a value, typically during the initial render or subsequent re-renders.  This often leads to unexpected behavior, especially when working with animations or frequent component updates.

## Problem

The provided code attempts to access `animation.current` immediately within the `useRef` hook initialization. This is problematic because `useRef` doesn't guarantee that the `current` property is populated synchronously.  Although it might work during the initial render, subsequent renders could cause undefined behavior or errors.

## Solution

A solution is to access the ref inside a `useEffect` hook.  This ensures the ref has been assigned a value before the access attempts are made. Additionally, always check if a value exists in the ref before manipulating it. 