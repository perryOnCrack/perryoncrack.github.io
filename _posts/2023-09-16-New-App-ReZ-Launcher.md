---
layout: post
categories: DevLog
title: "New App & What's Wrong With It: ReZ Launcher"
date: 2023-09-16 21:00:00 +0800
tags: [android, devlog]
---

*(This post should be up in July, but my stupid a\*\* decide to rush the app cause too much issues at launch so here it is.)*

Once upon a time there's a small Swedish company call Nokia, they release a tablet called N1, in it there's a really special launcher call Z Launcher.

Not long after the release of the tablet, the launcher got a standalone release on the Play Store and highschool kid tried it and fell in love with it.

But tragedy struck, the launcher soon fell out of support by that small Swedish company and stopped getting updates. And soon enough, it got pulled out of the store, but the app still worked well and the kid still using it nonetheless.

An ick started to grow as the Android version grew, a popup appeared saying `The app might not work properly because it's made for older version of Android`  every time the kid installed it on a new device. The app still works, but the dread of it become unusable someday grew daily and the kid grew a will that someday he'll write he's own Z Launcher.

As of today, the kid got the mean and build the dream Android launcher of his on his own.

---

Ok that's some corny story I just told you and that kid in the story is, you guessed it, yours truly.

To the main topic...

## What's this app?

My recreation of Nokia's Z Launcher that is built using Jetpack Compose and Google ML Kit Digital Ink with ~~some~~ one of the more modern features.

If you don't know what Z Launcher is, here's a short feature summary of it:

- Scribble to search app.
- Automatically shows apps that are most likely to be used.
- Minimalistic design.

My main goal of this project is to recreate these core features using Compose and other libraries.

## What I built so far...

The core features mention above are built, and I also added app shortcut feature which was not a thing when Z Launcher released.

I released the app back in mid-July, but things didn't go smoothly...

## What went wrong?

A lots of thing went wrong:

- The first iteration of the scribble in Compose was a huge mess, the performance was bad and the code were all over the place.
- The layout was badly layed out, and locked to portrait mode only.
- The logic on suggesting apps was too computational intense because of the data structure I used.
- The original usage collection database table was not thought out at all (rewrote it at version 1.2.)
- The constant app crashing because I used a number of bad key value on `LazyListScope`'s `item{}` (Fixed in version 1.1-fix1.)

## What now?

Fortunately, I spent the last a week refactored and rewritten a whole bunch of components to fixed all the above unsolved problems, and released version 1.3.

As for now, I might just have some time to work on the missing features that were seen on Z Launcher that I haven't implemented yet.

Go to this [link](/apps/rez) if you are interested on what features I've planned & the changlogs.

And the [Play Store link](/rez) if you want to try out the launcher.

---

See you in the next post!
