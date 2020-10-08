---
title: Components
keywords: blazor
last_updated: October 7, 2020
tags: [blazor]
summary: 
sidebar: mydoc_sidebar
permalink: components.html
folder: blazordoc
---

## What are Components?

A Blazor Component is a .razor file containing HTML and CSharp code acting on the HTML. They can be considered the legos with which we build Blazor apps. 

## Description

A component must have an HTML section and optionally a @code section.

## Example 

```
Component.razor

<h2>Hi there, @Name</h2>

@code {
    public string Name = "Jon"
}
```

```
Output

<h2>Hi there, Jon</h2>
```

We use the @ identifier in the HTML code to indicate the piece after is referring to CSharp code. In the above example, I set `Name` to be my name and referred to that variable in the HTML. When this component is used, the output will be that above.

## Using a Component

One uses a component via a HTML tag with the name of the component. For example, the component above is in file Component.razor. I would use this component in the following manner:

```
<Component/>

<Component></Component>
```

Both ways would have the same result for such a simple component. If the component took input, the two ways demonstrated may have differing results. We will discuss inputting into a component later.

## Component Parameters

Sometimes we want to pass data *into* a component. For example, say I modify Component.razor to accept any name as input. A parameter in a component must be a public property with a getter and setter, and must be labeled with the [Parameter] annotation.

```
Component.razor

<h2>Hi there, @Name</h2>

@code {
    [Parameter]
    public string Name { get; set; }
}
```

And here's how I would then use the component:

```
<Component Name="George"></Component>
```

```
Output

<h2>Hi there, George</h2>
```