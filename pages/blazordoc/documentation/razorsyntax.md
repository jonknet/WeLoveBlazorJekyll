---
title: Razor Syntax
keywords: blazor
last_updated: October 7, 2020
tags: [documentation]
summary: 
sidebar: mydoc_sidebar
permalink: razorsyntax.html
folder: blazordoc
---


Blazor leverages Razor pages for components and layouts so it's important to understand the basic syntax.

## Implicit and Explicit Expressions

The expression immediately following the @ is executed as C# and is *implicit*.
``` html
<div>@Name</div>
<div>@Add(5)</div>
```
@Name would return the string value of Name and @Add(5) would return the value of the function.

If parentheses are involved then the expression is said to be *explicit*.
``` html
<div>@(5 - 2)</div>
```
In this case, it would return 3.

Implicit expressions don't allow spaces while explicit ones do.

## Code Blocks

You can execute code without rendering it using code blocks

``` csharp
@{ name = "Jon" }
<h2>@Name</h2>
```

## Conditionals

To use a conditional like if, place a @ in front like so and surround the output with brackets, just like a code block.

Here are some examples.

``` csharp
@if (val == 1) {
    <p>Hi!</p>
}

@if (val == 1) {
    <p>One</p>
} else if (val == 2) {
    <p>Two</p>
} else {
    <p>Not one or two</p>
}

@switch (val) {
    case 1:
        <p>One</p>
        break;
    case 2:
        <p>Two</p>
        break;
    default:
        // Do nothing
        break;
}
```

## Looping

You can, of course, also use looping constructs.

``` csharp
@for (var i = 0; i < 5; i++){
    <p>Hello there</p>
}

@foreach (Droid d in Droids){
    <p>Not the droid I was looking for</p>
}

@{ var i = 0; }
@while (i < 5){
    <p>@i</p>
    i++;
}
```