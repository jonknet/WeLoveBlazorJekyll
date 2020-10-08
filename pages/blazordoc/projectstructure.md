---
title: Project Structure
keywords: blazor
last_updated: October 7, 2020
tags: [blazor]
summary: 
sidebar: mydoc_sidebar
permalink: projectstructure.html
folder: blazordoc
---

Project code structures will vary depending on how complex the application, but there are some practices held commonly. Here is a screenshot of the tree for the example WASM project provided by Microsoft:

## Basic Structure

{% include image.html file="screenshots/blazorwasm_codetree.png" %}

The 'Pages' folder contains the routable razor pages for the application (http://url/route).

The 'Shared' folder contains Components that, as the name implies, can be reused among multiple pages.

The 'Properties' folder contains one file, launchSettings.json, which determines the parameters for the IIS server when it runs to serve the WASM code to the browser.

The 'wwwroot' folder contains static assets and will be placed in the root when the app is built.

_Imports.razor defines namespaces that are being imported so we don't have to write using statements on the top of every file.

App.razor is the root component and sets up routing for the application.

BlazorWASM.csproj has some details on what framework and SDK we are targeting, as well as references to be included. 

Program.cs contains the entry point Main and also may add ("inject") additional services into the application.

## Basic Design Principles

**Keep Logic and HTML as Separated as Possible**

Razor pages are specifically designed to promote this practice. Only small amounts of code should be embedded within the HTML.

**Utilize Components to Enable Code Reuse and Reduce Bugs**

Find yourself writing the same code? Put it in a Component! That way if it breaks, you only have to fix it at the source. It also cleans up the HTML substantially.