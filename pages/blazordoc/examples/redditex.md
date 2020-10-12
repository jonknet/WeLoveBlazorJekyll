---
title: Reddit OAUTH2 Example
keywords: blazor
last_updated: October 7, 2020
tags: [examples]
summary: 
sidebar: mydoc_sidebar
permalink: redditex.html
folder: blazordoc
---

A basic Reddit API example that uses OAUTH2 to authenticate.

``` csharp
@page "/"
@inject HttpClient Http

@using System.Text.Json;

@foreach(Post p in posts)
{
<div class="post">
    <a href="@p.url">
        @if (p.thumbnail != "self")
        {
            <img src="@p.thumbnail" />
        } 
        @p.title
    </a>
</div>
}


@code {
    public List<Post> posts = new List<Post>();

    public string token = "";

    protected override async Task OnInitializedAsync()
    {
        var appId = "";
        var secretId = ""

        var plainTextBytes = System.Text.Encoding.ASCII.GetBytes(appId + ":" + secretId);

        HttpRequestMessage httpRequest = new HttpRequestMessage(HttpMethod.Post, 
                                                                "https://www.reddit.com/api/v1/access_token");
        Dictionary<string, string> param = new Dictionary<string, string>();
        param.Add("grant_type", "client_credentials");
        httpRequest.Content = new FormUrlEncodedContent(param);
        httpRequest.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Basic", System.Convert.ToBase64String(plainTextBytes));

        HttpResponseMessage response = await Http.SendAsync(httpRequest);

        var output = await response.Content.ReadAsStringAsync();

        JsonDocument doc = JsonDocument.Parse(output);
        token = doc.RootElement.GetProperty("access_token").GetString();

        httpRequest = new HttpRequestMessage(HttpMethod.Get, "https://oauth.reddit.com/r/popular/hot?g=US");
        httpRequest.Headers.Authorization = new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);

        response = await Http.SendAsync(httpRequest);

        token = await response.Content.ReadAsStringAsync();

        byte[] rawBytes = System.Text.Encoding.UTF8.GetBytes(token);
        System.IO.MemoryStream memoryStream = new System.IO.MemoryStream(rawBytes);

        doc = await JsonDocument.ParseAsync(memoryStream);
        JsonElement elem = doc.RootElement.GetProperty("data").GetProperty("children");

        foreach(JsonElement post in elem.EnumerateArray())
        {
            Post p = new Post();
            p.title = post.GetProperty("data").GetProperty("title").GetString();
            p.url = post.GetProperty("data").GetProperty("url").GetString();
            p.thumbnail = post.GetProperty("data").GetProperty("thumbnail").GetString();
            posts.Add(p);
        }
    }

    public class Post
    {
        public string title { get; set; }
        public string url { get; set; }
        public string thumbnail { get; set; }
    }

}
```
