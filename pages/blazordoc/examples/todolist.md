---
title: Todo List
keywords: blazor
last_updated: October 7, 2020
tags: [projects]
summary: 
sidebar: mydoc_sidebar
permalink: todolist.html
folder: blazordoc
---

I wrote this simple Todo list app to demonstrate how Blazor stores and manipulates component state.

``` csharp
Todo.razor

@using System.Collections.Generic;
@using System.ComponentModel.DataAnnotations;

@page "/todo"

<table>
    <tr>
        <th>Description</th>
        <th>Delete</th>
    </tr>
    @foreach (TodoItem t in todos){
        <tr>
            <td>@t.Description</td>
            <td><button @onclick="(()=>todos.Remove(t))">Delete</button></td>
        </tr>
    }
    <tr>
        <td>
            <EditForm Model="@todoModel" OnValidSubmit="@HandleSubmit">
                <DataAnnotationsValidator />
                <label for="description">Description</label>
                <InputText id="description" @bind-Value="todoModel.Description" class="form-control"/>
                <button type="submit" class="btn btn-primary">Add</button>
            </EditForm>
        </td>
    </tr>
</table>

@code {
    private List<TodoItem> todos = new List<TodoItem>();
    
    private TodoItem todoModel = new TodoItem();
    
    public class TodoItem {
        [Required]
        public string Description { get; set; }
    }
    
    private void HandleSubmit(){
        TodoItem t = new TodoItem();
        t.Description = todoModel.Description;
        todos.Add(t);
        todoModel.Description = "";
    }
}
```
