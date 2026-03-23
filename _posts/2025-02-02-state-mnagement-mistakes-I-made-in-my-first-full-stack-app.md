---
title: "State Management Mistakes I Made in My First Full-Stack App"
date: 2025-02-02 20:33:00 +0530
categories: [frontend, debugging]
tags: [react, state-management, authentication, bug-fix]
State Management Mistakes: I Made in My First Full-Stack App
---

# When I built my first full-stack application, I thought state management was simple.

`Login → Store user → Show UI`

That assumption didn’t last long.

## The Problem

After implementing login, something felt off:
- User logs in successfully
- Token is stored
- But the Navbar still shows “Login”

Refreshing the page fixed it.
***That was the first red flag.***

##### Mistake #1: Relying Only on localStorage

I stored everything in localStorage: 
- Token
- Role
- isLoggedIn flag

But React doesn’t re-render when localStorage changes.
So even though the data existed, the UI didn’t update.

##### Mistake #2: No Central State
Different components were handling their own logic:
- Navbar checked localStorage
- Login updated localStorage
- No shared state

This led to inconsistent behavior across the app.

##### Mistake #3: No Sync Between UI and State
There was no real connection between:
 - Authentication state
 - UI rendering

Everything was loosely coupled.

#### The Fix

I introduced React Context.
Created a global AuthContext
Stored:
- isLoggedIn
- userRole
- Updated context on login/logout

#### Now:

Navbar updates instantly.
No page refresh needed.
State stays consistent across components.

## ✅ Key Takeaway
localStorage is storage, not state.
UI needs a reactive state layer to stay in sync.

Final Thought
---
State management isn’t just about storing data.
It’s about keeping your UI and your data in sync.
That’s where real frontend development begins.
---

