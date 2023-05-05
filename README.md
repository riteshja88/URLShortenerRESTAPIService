# URL Shortener REST API Service

This Git repository contains a URL shortener REST API service that allows you to create and manage short URLs. Each short URL created has statistics that track the time it was created, the last time it was accessed, the number of times it was accessed since the start of the day, and the maximum number of times it was accessed in a day.

## Short URL Statistics

For each short URL created using the API, you can retrieve statistics about the URL. These statistics include:

- Time the short URL was created
- Time the short URL was last accessed
- Number of times the short URL was accessed since the start of the day
- Maximum number of times the short URL was accessed in a day

## URL Shortener REST API Service Statistics
In addition to the statistics for each individual URL, there are also statistics for the entire service. These statistics include:
- Time when the last short URL was created
- Time when the last short URL was accessed
- Number of short URLs created since the start of the day
- Maximum number of short URLs created in a day
- Number of short URLs accessed since the start of the day
- Maximum number of short URLs accessed in a day
- Total number of short URLs active on the system

## API Endpoints

The following API endpoints are available:

- **\`POST /api/shorten\`**: Creates a new short URL
To create a new short URL, make a POST request to the /api/shorten endpoint with a JSON payload containing the original URL. Here's an example using cURL:
```
curl -X POST -H "Content-Type: application/json" -d '{"url": "https://example.com"}' http://localhost:3000/api/shorten
```
The response will be a JSON object containing the shortened URL and its statistics:
```
{
  "shortUrl": "http://localhost:3000/abc123",
  "stats": {
    "created": "2023-05-06T12:34:56.789Z",
    "lastAccessed": "2023-05-06T12:34:56.789Z",
    "accessCount": 0,
    "maxDailyAccessCount": 0
  }
}
```
- **\`GET /api/stats\`**: Retrieves statistics about the entire service

```
The response will be a JSON object containing the shortened URL and its statistics:
{
  "shortUrl": "http://localhost:3000/abc123",
  "stats": {
    "created": "2023-05-06T12:34:56.789Z",
    "lastAccessed": "2023-05-06T12:34:56.789Z",
    "accessCount": 0,
    "maxDailyAccessCount": 0
  }
}
```
- **\`GET /api/:shortUrl/stats\`**: Retrieves statistics about a specific short URL
To retrieve statistics about a specific short URL, make a GET request to the /api/:shortUrl/stats endpoint, where :shortUrl is the shortened URL you want to retrieve statistics for. Here's an example using cURL:
```
curl http://localhost:3000/api/abc123/stats
```
The response will be a JSON object containing the statistics for the short URL:
```
{
  "created": "2023-05-06T12:34:56.789Z",
  "lastAccessed": "2023-05-06T12:34:56.789Z",
  "accessCount": 0,
  "maxDailyAccessCount": 0
}
```

- **\`GET /:shortUrl\`**: Redirects to the original URL associated with the short URL



## Installation

To install and run the URL shortener service, follow these steps:

Clone this Git repository
Install the required dependencies using npm install
Start the server using npm start
Usage

To use the API, send HTTP requests to the appropriate endpoints using your favorite tool or library. For example, you could use the fetch function in JavaScript to make requests to the API.

Here's an example of how to create a new short URL using the API:

javascript
Copy code
fetch('/api/shorten', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    url: 'https://example.com'
  })
}).then(response => {
  // Handle the response
});
To retrieve statistics about a specific short URL, you could use a URL like /api/:shortUrl/stats, where :shortUrl is replaced with the short URL you want to retrieve statistics for.

License

This project is licensed under the MIT License. See the LICENSE file for details.
