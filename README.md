# URL Shortener REST API Service

We need a URL shortener REST API service that allows you to create and manage short URLs. Each short URL created has statistics that track the time it was created, the last time it was accessed, the number of times it was accessed since the start of the day, and the maximum number of times it was accessed in a day and the total number of times it was accessed since created. Additionally it also maintains service level stats.

## Short URL Statistics

For each short URL created using the API, you can retrieve statistics about the URL. These statistics include:

- Time the short URL was created
- Time the short URL was last accessed
- Number of times the short URL was accessed today
- Maximum number of times the short URL was accessed in a day
- Number of times the short URL was accessed since created

## URL Shortener REST API Service Statistics
In addition to the statistics for each individual URL, there are also statistics for the entire service. These statistics include:
- Time when the last short URL was created
- Time when the last short URL was accessed
- Number of short URLs created today
- Maximum number of short URLs created in a day
- Total number of short URLs created
- Number of short URLs accessed today
- Maximum number of short URLs accessed in a day
- Total number of short URLs accessed

## API Endpoints

The following API endpoints should be available:

- **\`POST /api/shorten\`**: Creates a new short URL

To create a new short URL, make a **\`POST\`** request to the **\`/api/shorten\`** endpoint with a JSON payload containing the original URL. Here's an example using cURL:
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
    "accessCountToday": 0,
    "accessCountDailyMax": 0,
    "accessCount": 0
  }
}
```

- **\`GET /:shortUrl\`**: Redirects to the original URL associated with the short URL

To redirect to the original URL associated with a short URL, make a **\`GET\`** request to the **\`/:shortUrl\`** endpoint, where **\`:shortUrl\`** is the shortened URL you want to redirect to. Here's an example using cURL:
```
curl http://localhost:3000/abc123
```
The response will be a redirect to the original URL associated with the short URL.


- **\`GET /api/:shortUrl/stats\`**: Retrieves statistics about a specific short URL

To retrieve statistics about a specific short URL, make a **\`GET\`** request to the **\`/api/:shortUrl/stats\`** endpoint, where **\`:shortUrl\`** is the shortened URL you want to retrieve statistics for. Here's an example using cURL:
```
curl http://localhost:3000/api/abc123/stats
```
The response will be a JSON object containing the statistics for the short URL:
```
{
  "created": "2023-05-06T12:34:56.789Z",
  "lastAccessed": "2023-05-06T12:34:56.789Z",
  "accessCountToday": 0,
  "accessCountDailyMax": 0,
  "accessCount": 0
}
```

- **\`GET /api/stats\`**: RRetrieves statistics about the entire service and all short URLs

To retrieve statistics about all short URLs, make a **\`GET\`** request to the **\`/api/stats\`** endpoint. Here's an example using cURL:
```
curl http://localhost:3000/api/stats
```
The response will be a JSON object containing an array of statistics for each short URL:
```
{
	"stats": {
		"lastCreated": "2023-05-06T12:34:56.789Z",
		"lastAccessed": "2023-05-06T12:34:56.789Z",
		"createCountToday": 0,
		"createCountDailyMax": 0,
		"createCount": 2,
		"accessCountToday": 0,
		"accessCountDailyMax": 0,
		"accessCount": 0
	},
	"shortUrls": [{
			"shortUrl": "http://localhost:3000/abc123",
			"stats": {
				"created": "2023-05-06T12:34:56.789Z",
				"lastAccessed": "2023-05-06T12:34:56.789Z",
				"accessCountToday": 0,
				"accessCountDailyMax": 0,
				"accessCount": 0
			}
		},
		{
			"shortUrl": "http://localhost:3000/def456",
			"stats": {
				"created": "2023-05-05T12:34:56.789Z",
				"lastAccessed": "2023-05-05T12:34:56.789Z",
				"accessCountToday": 0,
				"accessCountDailyMax": 0,
				"accessCount": 0
			}
		}
	]
}
```

## Installation

To install and run the URL shortener service, we should be able to follow these steps:

1. Clone this Git repository
2. Install the required dependencies using **\`npm install\`**
3. Start the server using \`**npm start\`**


