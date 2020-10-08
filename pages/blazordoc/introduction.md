---
title: Introduction to Blazor
keywords: blazor
last_updated: October 7, 2020
tags: [blazor]
summary: 
sidebar: mydoc_sidebar
permalink: introduction.html
folder: blazordoc
---

Unless you've been living under a rock, it is of no doubt you've heard of the latest front end frameworks. React, Angular, Vue... these technologies were developed to make web application development more understandable and enjoyable. And they've all accomplished a lot in pushing the state of web development forward. The backbone of the major players in these tools happens to be Javascript. Javascript as a language can be extremely messy, owing to it being type-agnostic. You can assign any variable to any other variable; javascript doesn't care and expects you, the programmer, to know at runtime which variables are which types and how to appropriately use them. This can lead to some confusing code that is difficult to debug. If we only had explictly defined our types in the code we might have been able to hone in on errors more effectively. There is a very real term called "Javascript Fatigue" known to those developers who have to stare at code all day. Don't get me wrong, Javascript can do amazing things and is incredibly powerful, but it lacks the guard rails of other languages that promote (read: force) good coding practices. 

There are several languages available to us that do employ type checking: C++, Java, Typescript (which was based off Javascript), C#, and countless others. Why not use one of these instead for full stack programming? Microsoft came along and thought the same thing, so they created Blazor on top of ASP.NET. Blazor allows the developer to write full stack web applications with minimal need to write any javascript; the only technologies needed are HTML, CSS, and C#. We can even wrap javascript functions through JSInterop into native C# calls to expose features that Blazor might not have yet, for example, drawing directly to a HTML5 canvas. Furthermore, there is full support for Blazor in Visual Studio for debugging and tracing making bugs a breeze to find. The one downside is how young Blazor is; it hasn't been fully optimized yet and it sometimes lacks functionality that other frameworks have. But it's catching up quickly!

I would implore you to try Blazor out... design a simple web application or game and see how much more quickly the pieces come together. As the website says, we LOVE Blazor!