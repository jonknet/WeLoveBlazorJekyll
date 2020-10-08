---
title: Simple Counter
keywords: blazor
last_updated: October 7, 2020
tags: [projects]
summary: 
sidebar: mydoc_sidebar
permalink: simplecounter.html
folder: blazordoc
---
The following example is included in the templates Microsoft provides. We will go through line by line to explain how it works.
``` csharp
Counter.razor

@page "/counter"

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```
@page tells us this component is located at /counter

On the button, we can assign a callback function of IncrementCount to the onclick event.

When the button is pressed, IncrementCount() is called causing currentCount to be incremented.

It will automatically re-render the new value on the page.