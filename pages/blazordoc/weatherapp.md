---
title: A simple weather app
keywords: blazor
last_updated: October 7, 2020
tags: [blazor]
summary: 
sidebar: mydoc_sidebar
permalink: weatherapp.html
folder: blazordoc
---
The following example is included in the templates Microsoft provides. We will go through line by line to explain how it works.
```
FetchData.razor

@page "/fetchdata"                                                  
@inject HttpClient Http

<h1>Weather forecast</h1>

<p>This component demonstrates fetching data from the server.</p>

@if (forecasts == null)
{
    <p><em>Loading...</em></p>
}
else
{
    <table class="table">
        <thead>
            <tr>
                <th>Date</th>
                <th>Temp. (C)</th>
                <th>Temp. (F)</th>
                <th>Summary</th>
            </tr>
        </thead>
        <tbody>
            @foreach (var forecast in forecasts)
            {
                <tr>
                    <td>@forecast.Date.ToShortDateString()</td>
                    <td>@forecast.TemperatureC</td>
                    <td>@forecast.TemperatureF</td>
                    <td>@forecast.Summary</td>
                </tr>
            }
        </tbody>
    </table>
}

@code {
    private WeatherForecast[] forecasts;

    protected override async Task OnInitializedAsync()
    {
        forecasts = await Http.GetFromJsonAsync<WeatherForecast[]>("sample-data/weather.json");
    }

    public class WeatherForecast
    {
        public DateTime Date { get; set; }

        public int TemperatureC { get; set; }

        public string Summary { get; set; }

        public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
    }
}
```
The @page directive on the first line tells Blazor how the user can get to this page (http://domain/fetchdata)

@inject directive exposes the HttpClient object as `Http` to the rest of the code. HttpClient can be used to make API calls out to the internet and load data.

If forecasts == null, the page will display "Loading...".

Once this page has been fully loaded, the OnInitializedAsync() callback is triggered. This initializes forecasts by retrieving a list of weather conditions from a local json file.

Forecasts is no longer null so we proceed into displaying the weather forecasts.

We use a @foreach to loop through each forecast object and output it's properties into a table.

We're all done! 