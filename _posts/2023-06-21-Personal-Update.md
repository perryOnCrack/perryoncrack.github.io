---
layout: post
categories: DevLog
title: What I've Been Doing In The Past Year
date: 2023-06-21 12:00:00 +0800
tags: [Personal Update]
---

### When you were a graduated and get in to a job you don't like and decided quit after just 6 months, what do you do next?

Find a new job immediately? Spend another 6 months in your new hobby? Or learn some new skills? I definitely didn't do one of them 🫣

---

So what exactly I've been doing?

### First thing I did: I learned a lot about 3D Printing.

I always want a 3D printer since I was a freshman in university. It's a fascinating concept to me that you can just build stuff out of a 3D model.

So I bought a 3D printer, an Ender 3 S1 Pro to be exact, a month before I quit my job last year, thinking it would be fun just print and print and print...

But no, it's a frustrating machine to work with and has a heap of problems coming from the factory:

- The aluminum build plate is warped like crazy coming from factory.
- Creality knew the problem so they included CRTouch to the model, BUT the stock firmware sucks and couldn't even store and use the bed mesh properly.
- Also, the stock firmware's bed leveling sequence is confusing and did't work at all.
- The spring steel PEI plate won't stick anymore after just a few use.
- The stock cooling fan for the nozzle is not even close to adequate.
- Extrude aluminum and v-wheels are not a great design anymore by today's standard.

So for the next 6 months I've been fixing the problem it had, learning a lot of 3D printed tips & tricks and printing a lot of stuff and even designed some stuff along the way.

You can check out my [Printable profile](https://www.printables.com/@perryOnCrack), there might be something you might be interested.

### Second thing: Android development.

One of the things I think I can do for my career path before quitting the job is doing Android development.

I have a little experience in these from the time in the university, it's a course I took and I even go beyond the course to put the final, the [Morse Code Torch](https://play.google.com/store/apps/details?id=com.perryoncrack.mcfleshlite), on the Play Store. It didn't do very well on the store but I didn't do any advertisement and it still got over 100 downloads somehow.

I do have some app idea I want to make but I was too focus on 3D printing at the time, so I only started to look into this until November.

I started with the poc's Toolbox project but it didn't go anywhere. At then I was still using the old XML way of designing UI so it took a really long time for just one screen. I was also trying to learn how to use Fragment and use on the project, but learning it got me too frustrated and the code just becomes too unnecessarily complicated. I shelved the project not long after.

In mid-December, I dug out the Morse Code Torch project folder and decide to give it a overhaul. I converted it from Java to Kotlin and after that... I bailed again? Looking at its Git log right now, I finished converting in mid-January and the next git commit is March 3rd, and within a few day the overhaul was done, and later the hotfix was pushed out.

Anyway... After the update was pushed out, I was dead set I need to get my act together and start doing something productive. I had the idea & some drawing lay down for the next project, poc's Film Tracker, and I set my goal to learn Jetpack Compose this time. I go through some of the beginner course Google made to get familiar with the framework, and off to work on the project.

It's frustrating in the beginning: What's a Composable? How the is TextField work? What is state hoisting? But after a while I start to understand things and it become clear, designing UI on Compose is way way way easier than XML and it forces you to use MVVM which is a good thing.

In XML way, in the code you have to inflate the View, find the view, and read from or modify it when needed and write all the other logic in the same code, which clogs up really quick.

Now with Compose, doing thing the MVVM way is enforced by design essentially: now the View only display the state it wants to present and send actions to the ViewModel, View doesn't hold state anymore and things get separated which means cleaner code and tidier workspace.

And for the next 3 and a half months, I just working on the project. (Although I took 2 weeks off and design and printed a camera body...) Learning how to organize the project files, learning the different libraries Jetpack provides, learning the frustration others have with the framework online... etc. And just yesterday, the project is ready for release!

This is probably the fastest 3 months I've been so far. Everyday I woke up, turn on my PC, went for breakfast, and back to working this project until night. And time just went by and I finished the project! How crazy is that!? There're several times I got too frustrated on something and didn't know how to solve and the progress staggered but I overcome each of them eventually.

I might take a few days off for now, or just start the next project which I won't tell what it is just now. And I'll make a post about the new app and the roadmap I have for it in the next few day.

See ya, whoever is reading my rambling ✌️
