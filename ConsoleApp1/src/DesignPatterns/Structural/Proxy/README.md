Provides a proxy, or agent, object to control access to another object, allowing for additional functionality such as caching, logging, lazy loading or access control, without changing the client's code.

## In Practice

### Bad Example

```cs
var videoList = new VideoList();
String[] videoIds = { "1234", "abcde", "javasc123" };
foreach (var videoId in videoIds)
{
videoList.Add(new YouTubeVideo(videoId));
}
// Logs from each loop:
// 1. Downloading video with id 1234 from YouTube API
// 2. Downloading video with id abcde from YouTube API
// 3. Downloading video with id javasc123 from YouTube API

videoList.Watch("abcde"); // Rendering video abcde
```

### Good Example

```cs
var videoList = new VideoList();
String[] videoIds = { "1234", "abcde", "javasc123" };
foreach (var videoId in videoIds)
{
    videoList.Add(new YouTubeVideoProxy(videoId)); // We now use
    our "placeholder", or "proxy" class
}

// Video is now only downloaded when user wants to watch it:
videoList.Watch("abcde");
// Logs:
// Downloading video with id abcde from YouTube API
// Rendering video abcde
```
