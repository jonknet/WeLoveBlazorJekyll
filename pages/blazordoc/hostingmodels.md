---
title: Hosting Models
keywords: blazor
last_updated: October 7, 2020
tags: [blazor]
summary: 
sidebar: mydoc_sidebar
permalink: hostingmodels.html
folder: blazordoc
---

So you may be wondering what the difference between WebAssembly and Server Hosted is, so before we go any further I'll explain briefly.

## WebAssembly

WebAssembly is a Javascript library that allows code from various languages to be compiled into low-level instructions that can run natively and securely in a web browser. However, WASM code running in the browser *cannot* touch the operating system, for example delete files or cause other mayhem. Blazor compiles to WASM and can run standalone in the browser without any backend server. This is called Blazor WebAssembly and is ideal for smaller web apps requiring good responsiveness. Blazor WebAssembly can interact with APIs over the internet for other services (data storage, processing, etc).

## Server Hosted

Server Hosted mode runs the code on a central server instead of in the client's browser. The browser "sees" the application exactly the same as if it were running locally, but this is a trick. Microsoft uses a technology called SignalIR to broadcast the visual state of the application to the browser and, vice versa, any inputs are sent to the server. A lightweight code is all that is running in the web browser to display the state and handle inputs. The advantage of server hosted is one can access backend services (think databases) more securely and easily without exposing a public API out to the internet, while the disadvantage is the app will not be as responsive as the WASM version. 

## Summary

The important thing to note is a WASM app can be made a Server app and vice versa with little change to the code and no difference seen by the end user.

WebAssembly can be more responsive but requires more legwork if having to use backend services.

Server is more secure and requires less setup to use backend services, but may be less responsive in high traffic situations (like fast paced games or a bad network connection).
