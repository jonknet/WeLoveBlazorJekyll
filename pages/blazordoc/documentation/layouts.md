---
title: Layouts
keywords: blazor
last_updated: October 7, 2020
tags: [documentation]
summary: 
sidebar: mydoc_sidebar
permalink: layouts.html
folder: blazordoc
---

## What are Layouts?

Any webpage likely has a desired look made out of several sections. For instance, a page may have a navbar at the top, a section for content in the middle, and a footer containing company contact information. This is the *layout* of the webpage. 

Blazor has components called layouts which work to make it easier to organize the sections of an application. They act as a kind of template. 

## Description

A layout must inherit (using @inherits) from LayoutComponentBase class and contain a @Body directive somewhere inside itself.

## Example

Any component can be defined to belong to a layout via the ```@layout``` directive at the top of the component file. 

``` csharp
Component.razor

@layout MyLayout
<h2>Hi there!</h2>
```

And here is what MyLayout looks like

``` csharp
MyLayout.razor

@inherits LayoutComponentBase
<div>@Body</div>
```

The final output when Component.razor is used will be

``` html
<div><h2>Hi there!</h2></div>
```

The contents of the component with the @layout directive gets *inserted* into the parent layout at the @Body.

