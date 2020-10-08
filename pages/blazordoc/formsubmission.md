---
title: Form Submission
keywords: blazor
last_updated: October 7, 2020
tags: [blazor]
summary: 
sidebar: mydoc_sidebar
permalink: formsubmission.html
folder: blazordoc
---

This app allows you to add people to a list as well as modify their data in place by clicking on their name.

```
@using System.Collections.Generic;
@using System.ComponentModel.DataAnnotations;

@page "/formsubmit"

<table>
    <tr>
        <td>
            <table>
                <tr>
                    <th>Name</th>
                    <th>Address</th>
                    <th>City</th>
                    <th>State</th>
                </tr>
                @foreach(Person p in people){
                    <tr>
                        <td><a @onclick="(()=>personModel=p)">@p.Name</a></td>
                        <td>@p.Address</td>
                        <td>@p.City</td>
                        <td>@p.State</td>
                    </tr>
                }
            </table>
        </td>
        <td>
            <EditForm Model="@personModel" OnValidSubmit="@HandleSubmit">
                <DataAnnotationsValidator />
                <label for="name">Name</label>
                <InputText id="name" @bind-Value="personModel.Name" class="form-control"/>
                <label for="address">Address</label>
                <InputText id="address" @bind-Value="personModel.Address" class="form-control"/>
                <label for="city">City</label>
                <InputText id="city" @bind-Value="personModel.City" class="form-control"/>
                <label for="state">State</label>
                <InputText id="state" @bind-Value="personModel.State" class="form-control"/>
                <button type="submit" class="btn btn-primary">Add</button>
            </EditForm>
        </td>
    </tr>
</table>

@code {

    private List<Person> people = new List<Person>();

    private Person personModel = new Person();

    private bool updateMode = false;

    private void HandleSubmit(){
        Person p = new Person();
        p.Name = personModel.Name;
        p.Address = personModel.Address;
        p.City = personModel.City;
        p.State = personModel.State;
        people.Add(p);
    }
    public class Person {
        [Required]
        public string Name { get; set; }
        public string Address { get; set; }
        public string City { get; set; }
        [StringLength(2,ErrorMessage = "Must be 2 characters")]
        public string State { get; set; }
    }
}
```
