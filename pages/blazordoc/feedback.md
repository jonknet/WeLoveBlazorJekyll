---
title: Feedback
keywords: blazor
last_updated: October 9, 2020
tags: 
summary: 
sidebar: mydoc_sidebar
permalink: feedback.html
folder: blazordoc
---

<form action="https://formspree.io/f/xoqpjbdg" method="POST">
  <div class="form-group">
    <label for="exampleInputEmail1">Email address</label>
    <input type="email" name="replyto" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
    <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
  </div>
  <div class="form-group">
    <label for="exampleInputPassword1">Feedback</label>
    <textarea class="form-control" name="feedbackText"></textarea>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>