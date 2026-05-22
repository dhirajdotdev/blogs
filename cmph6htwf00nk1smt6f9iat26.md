---
title: "How Instagram, WhatsApp, Uber & Netflix Would Be Built Today Using Expo Router"
seoTitle: "Built Today Using Expo Router"
seoDescription: "How Instagram, WhatsApp, Uber & Netflix Would Be Built Today Using Expo Router"
datePublished: 2026-05-22T17:13:23.107Z
cuid: cmph6htwf00nk1smt6f9iat26
slug: built-today-using-expo-router
tags: react-native, react, typescript

---

Most React Native apps look clean in the beginning.

You create a few folders:

```txt
/screens
/components
/hooks
/utils
```

everything feels organized…

until the app grows.

You add:

*   authentication
    
*   realtime systems
    
*   notifications
    
*   caching
    
*   analytics
    
*   deep linking
    
*   background sync
    
*   offline support
    
*   100+ screens
    
*   multiple developers
    

and suddenly the codebase starts fighting you.

This is where architecture becomes more important than UI.

Apps like Instagram, WhatsApp, Uber and Netflix are not difficult because of screens.

They are difficult because of:

*   scale
    
*   synchronization
    
*   maintainability
    
*   performance
    
*   navigation complexity
    
*   realtime infrastructure
    

If these apps were built today using React Native + Expo Router, the architecture would look very different from typical tutorial apps.

This blog is about that architecture thinking.

Not UI cloning.

* * *

# Why Simple Folder Structures Fail at Scale

Most beginner apps organize code like this:

```txt
/components
/screens
/apis
/hooks
```

This works for small projects.

But large apps slowly become impossible to manage because everything is grouped by “type” instead of “business feature”.

Example:

```txt
/components
```

eventually becomes:

```txt
/components
  FeedCard.tsx
  ChatBubble.tsx
  DriverMarker.tsx
  MovieCard.tsx
  PaymentSheet.tsx
  NotificationItem.tsx
```

Now nobody knows:

*   ownership
    
*   dependencies
    
*   feature boundaries
    
*   what can safely change
    

This is why production apps move toward feature-based architecture.

* * *

# How Large Apps Think About Architecture

Small apps are built around screens.

Production apps are built around systems.

Instead of thinking:

```txt
"profile screen"
```

large teams think:

```txt
"user identity system"
```

Instead of:

```txt
"chat UI"
```

they think:

```txt
"realtime messaging infrastructure"
```

That mindset shift changes everything.

* * *

# Why Expo Router Fits Modern React Native Apps

Before Expo Router, navigation usually became one giant file.

Something like:

```txt
navigation/
  AppNavigator.tsx
  AuthNavigator.tsx
  HomeTabs.tsx
  FeedStack.tsx
```

As the app grows:

*   navigation becomes deeply nested
    
*   imports explode
    
*   route ownership becomes unclear
    
*   feature teams collide constantly
    

Expo Router fixes this by making routing filesystem-based.

Example:

```txt
app/
  (tabs)/
    home.tsx
    search.tsx

  profile/
    [username].tsx
```

The folder structure becomes the navigation structure.

This sounds simple…

but at scale it becomes extremely powerful.

* * *

# Production-Grade Expo Router Structure

A scalable Expo Router app would look more like this:

```txt
app/
  (public)/
    login/
    signup/
    onboarding/

  (protected)/
    (tabs)/
      home/
      search/
      activity/
      profile/

    chat/
    rides/
    media/
    settings/

  _layout.tsx

features/
  auth/
  feed/
  messaging/
  maps/
  video/
  payments/

services/
  api/
  realtime/
  analytics/
  storage/

store/
hooks/
types/
lib/
```

Notice something important:

```txt
/screens
```

barely exists anymore.

Features become the center of the architecture.

* * *

# Feature-Based Architecture

This is one of the biggest differences between beginner apps and production apps.

Instead of:

```txt
/components
/hooks
/apis
```

large apps organize by domain:

```txt
/features/feed
/features/chat
/features/location
/features/payments
```

Each feature contains its own:

```txt
components/
hooks/
api/
types/
state/
utils/
```

Example:

```txt
/features/chat
  /components
  /hooks
  /api
  /store
  /types
```

Benefits:

*   easier scaling
    
*   independent development
    
*   fewer merge conflicts
    
*   cleaner ownership
    
*   easier testing
    

This is how large engineering teams work without constantly breaking each other’s code.

* * *

# Shared Layouts and Nested Routing

One underrated thing about Expo Router is layouts.

Example:

```txt
app/
  (protected)/
    _layout.tsx

    (tabs)/
      _layout.tsx
      home.tsx
      profile.tsx

    chat/
      _layout.tsx
      [id].tsx
```

This allows:

*   protected route wrappers
    
*   shared headers
    
*   nested navigation stacks
    
*   feature-level navigation control
    

Instead of one massive navigator, each feature owns its own navigation logic.

That becomes extremely important at scale.

* * *

# Authentication Architecture

Most tutorial apps handle auth like this:

```js
if (loggedIn) {
  return <Home />
}
```

Production apps are far more complex.

Because authentication is not just login.

It includes:

*   token refresh
    
*   deep linking
    
*   onboarding state
    
*   secure storage
    
*   session restoration
    
*   role permissions
    
*   splash coordination
    

A real startup flow looks closer to this:

```txt
Open App
   ↓
Restore Session
   ↓
Validate Token
   ↓
Fetch User Data
   ↓
Resolve Feature Flags
   ↓
Enter Protected Routes
```

Expo Router route groups make this clean:

```txt
(public)
(protected)
(admin)
```

* * *

# State Management in Large Apps

One of the biggest mistakes in React Native apps:

putting everything into one global store.

At scale that becomes:

*   slow
    
*   difficult to debug
    
*   tightly coupled
    
*   rerender heavy
    

Large apps separate state into layers.

* * *

# 1\. Server State

This is data coming from APIs.

Examples:

*   feed posts
    
*   chats
    
*   movies
    
*   rides
    

Usually handled with tools like:

*   TanStack Query
    
*   caching layers
    
*   background revalidation
    

* * *

# 2\. UI State

Things like:

```txt
modal open
active tab
sheet visibility
```

Usually local state.

Not everything belongs globally.

* * *

# 3\. Persistent App State

Things like:

*   auth
    
*   session
    
*   preferences
    

Usually stored with:

*   Zustand
    
*   Redux Toolkit
    
*   MMKV
    

* * *

# How Instagram Would Be Built

Instagram is basically:

```txt
feeds + media delivery + engagement systems
```

The hardest problems are not UI.

They are:

*   infinite scrolling
    
*   image caching
    
*   upload systems
    
*   feed ranking
    
*   memory optimization
    
*   preloading
    

* * *

# Feed Architecture

Large feeds are usually built like this:

```txt
Feed Engine
   ↓
Pagination Layer
   ↓
Cache Layer
   ↓
Virtualized Rendering
```

This is why apps use:

*   FlashList
    
*   aggressive caching
    
*   lazy image loading
    
*   pagination systems
    

Without optimization, React Native feeds become laggy very quickly.

* * *

# The Real Bottleneck in Social Apps

Most people think JavaScript is the bottleneck.

Usually it’s actually:

```txt
images and rendering
```

Large apps spend huge effort optimizing:

*   image decoding
    
*   caching
    
*   prefetching
    
*   memory pressure
    
*   scroll performance
    

That’s why Instagram feels smooth even with massive media feeds.

* * *

# How WhatsApp Would Be Built

WhatsApp is fundamentally a realtime synchronization system.

The chat UI itself is relatively easy.

The difficult part is:

*   websocket reliability
    
*   offline delivery
    
*   message ordering
    
*   retries
    
*   synchronization
    
*   media uploads
    
*   typing indicators
    

* * *

# Realtime Messaging Flow

A production messaging system often works like this:

```txt
User Sends Message
       ↓
Optimistic UI Update
       ↓
Save Locally
       ↓
WebSocket Send
       ↓
Server ACK
       ↓
Message Status Update
```

The message appears instantly before the server confirms it.

That instant feeling matters.

* * *

# Offline-First Messaging

Apps like WhatsApp assume networks will fail.

So messages are usually:

*   stored locally
    
*   queued offline
    
*   retried automatically
    
*   synced later
    

This is why production apps use:

*   SQLite
    
*   MMKV
    
*   background sync queues
    

Offline-first architecture is one of the biggest differences between serious apps and beginner apps.

* * *

# How Uber Would Be Built

Uber is mostly a realtime location platform.

Core challenges:

*   live GPS tracking
    
*   websocket streams
    
*   route recalculation
    
*   map rendering
    
*   background location updates
    

* * *

# Ride Tracking Architecture

A simplified version:

```txt
Driver GPS
   ↓
Realtime Transport Layer
   ↓
Location Processing
   ↓
Passenger Live Updates
```

This sounds simple…

until updates happen every few seconds for millions of users.

* * *

# Why Maps Become Difficult

Maps are expensive.

At scale, apps optimize:

*   marker rendering
    
*   animation frequency
    
*   region updates
    
*   rerender control
    
*   battery usage
    

Without optimization:

*   FPS drops
    
*   battery drains
    
*   phones heat up
    

Realtime systems force you to think differently about rendering.

* * *

# How Netflix Would Be Built

Netflix is heavily optimized around content delivery.

The app architecture focuses on:

*   startup speed
    
*   streaming reliability
    
*   offline downloads
    
*   recommendation loading
    
*   media caching
    

* * *

# Netflix-Style Architecture

Apps like Netflix separate systems aggressively:

```txt
UI Layer
Playback Engine
Content Metadata
Download Engine
Recommendation Engine
```

Video playback is often isolated because streaming systems become highly specialized.

* * *

# App Startup Optimization

Large apps obsess over startup speed.

Because slow startup kills retention.

Bad startup strategy:

```txt
load everything immediately
```

Better strategy:

```txt
load minimum shell
↓
restore session
↓
lazy load features
↓
prefetch likely screens
```

Production apps aggressively optimize:

*   lazy imports
    
*   route-level splitting
    
*   deferred rendering
    
*   background hydration
    
*   asset preloading
    

* * *

# Offline-First Architecture

Production apps assume internet can fail anytime.

Typical flow:

```txt
User Action
   ↓
Local Update
   ↓
Sync Queue
   ↓
Background Retry
   ↓
Server Confirmation
```

This creates apps that feel instant even on bad networks.

That’s a huge architectural advantage.

* * *

# Performance at Scale

Large React Native apps optimize constantly for:

*   memory usage
    
*   rerenders
    
*   JS thread blocking
    
*   navigation performance
    
*   image rendering
    
*   startup time
    

Common strategies:

*   FlashList
    
*   memoization
    
*   background prefetching
    
*   selective hydration
    
*   virtualization
    

Performance engineering becomes a full-time concern in large apps.

* * *

# The Biggest Architecture Lesson

The most important shift is this:

Small apps are built around pages.

Large apps are built around systems.

*   feed systems
    
*   caching systems
    
*   realtime systems
    
*   synchronization systems
    
*   navigation systems
    
*   offline systems
    

The UI is only the surface layer.

That’s why apps like Instagram, WhatsApp, Uber and Netflix require much more than “React Native knowledge”.

They require architecture thinking.