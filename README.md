# URL Shortener REST API Service

We need a URL shortener REST API service that allows you to create and manage short URLs. Each short URL created has statistics that track the time it was created, the last time it was accessed, the number of times it was accessed since the start of the day, and the minimum/maximum/average number of times it was accessed in a day and the total number of times it was accessed since created, time(im ms) taken to create shortened URL, minimum/maximum/average/last time(in milliseconds) taken to access shortened url. Additionally it also maintains service level stats.

It is expected to not use any other database service and use data structures, libraries or solutions within the language instead, for example HashTable. It is fine if all the data is lost when the service is restarted.

## Short URL Statistics

For each short URL created using the API, you can retrieve statistics about the URL. These statistics include:

- Time the short URL was created
- Time taken(in ms) to create the short URL
- Time the short URL was last accessed
- Minimum/Maximum/Average/Last Time taken(in ms) to access the short URL
- Number of times the short URL was accessed today
- Minimum/Maximum/Average number of times the short URL was accessed in a day
- Number of times the short URL was accessed since created

## URL Shortener REST API Service Statistics
In addition to the statistics for each individual URL, there are also statistics for the entire service. These statistics include:
- Time when the last short URL was created
- The last shortened URL that was created.
- Minimum/Maximum/Average/Last Time taken(in ms) to create short URLs
- Number of short URLs created today
- Minimum/Maximum/Average number of short URLs created in a day
- Total number of short URLs created
- Time when the last short URL was accessed
- The last shortened URL that was accessed.
- Minimum/Maximum/Average/Last Time taken(in ms) to access short URLs
- Number of short URLs accessed today
- Minimum/Maximum/Average number of short URLs accessed in a day
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
    "createTimeTaken": 7,
    "lastAccessed": "2023-05-06T12:34:56.789Z",
    "accessCountToday": 0,
    "accessCountDailyMin": 0,
    "accessCountDailyMax": 0,
    "accessCountDailyAvg": 0,
    "accessCount": 0,
    "accessTimeTakenLast": 0,
    "accessTimeTakenMin": 0,
    "accessTimeTakenMax": 0,
    "accessTimeTakenAvg": 0  
  }
}
```

- **\`GET /:shortUrl\`**: Redirects to the original URL associated with the short URL

To redirect to the original URL associated with a short URL, make a **\`GET\`** request to the **\`/:shortUrl\`** endpoint, where **\`:shortUrl\`** is the shortened URL you want to redirect to. Here's an example using cURL:
```
curl http://localhost:3000/abc123
```
The response will be a redirect to the original URL(https://example.com) associated with the short URL. This should work from a browser e.g Chrome.


- **\`GET /api/:shortUrl/stats\`**: Retrieves statistics about a specific short URL

To retrieve statistics about a specific short URL, make a **\`GET\`** request to the **\`/api/:shortUrl/stats\`** endpoint, where **\`:shortUrl\`** is the shortened URL you want to retrieve statistics for. Here's an example using cURL:
```
curl http://localhost:3000/api/abc123/stats
```
The response will be a JSON object containing the statistics for the short URL:
```
{
  "created": "2023-05-06T12:34:56.789Z",
  "createTimeTaken": 7,
  "lastAccessed": "2023-05-06T12:34:56.789Z",
  "accessCountToday": 0,
  "accessCountDailyMin": 0,
  "accessCountDailyMax": 0,
  "accessCountDailyAvg": 0,
  "accessCount": 0,
  "accessTimeTakenLast": 0,
  "accessTimeTakenMin": 0,
  "accessTimeTakenMax": 0,
  "accessTimeTakenAvg": 0
}
```

- **\`GET /api/stats\`**: Retrieves statistics about the entire service and all short URLs

To retrieve statistics about all short URLs, make a **\`GET\`** request to the **\`/api/stats\`** endpoint. Here's an example using cURL:
```
curl http://localhost:3000/api/stats
```
The response will be a JSON object containing an array of statistics for each short URL:
```
{
  "stats": {
             "lastCreated": "2023-05-06T12:34:56.789Z",
             "lastCreatedShortUrl": "http://localhost:3000/abc123",
             "lastAccessed": "2023-05-06T12:34:56.789Z",
             "lastAccessedShortUrl": "http://localhost:3000/abc123",
             "createCountToday": 0,
             "createCountDailyMin": 0,
             "createCountDailyMax": 0,
             "createCountDailyAvg": 0,
             "createCount": 2,
             "accessCountToday": 0,
             "accessCountDailyMin": 0,
             "accessCountDailyMax": 0,
             "accessCountDailyAvg": 0,
             "accessCount": 0,
             "accessTimeTakenLast": 0,
             "accessTimeTakenMin": 0,
             "accessTimeTakenMax": 0,
             "accessTimeTakenAvg": 0,
             "createTimeTakenLast": 0,
             "createTimeTakenMin": 0,
             "createTimeTakenMax": 0,
             "createTimeTakenAvg": 0
	},
  "shortUrls": [
                 {
                   "shortUrl": "http://localhost:3000/abc123",
                   "stats": {
                              "created": "2023-05-06T12:34:56.789Z",
                              "createTimeTaken": 7,
                              "lastAccessed": "2023-05-06T12:34:56.789Z",
                              "accessCountToday": 0,
                              "accessCountDailyMin": 0,
                              "accessCountDailyMax": 0,
                              "accessCountDailyAvg": 0,
                              "accessCount": 0,
                              "accessTimeTakenLast": 0,
                              "accessTimeTakenMin": 0,
                              "accessTimeTakenMax": 0,
                              "accessTimeTakenAvg": 0
			 }
                 },
                 {
                   "shortUrl": "http://localhost:3000/def456",
                   "stats": {
                              "created": "2023-05-05T12:34:56.789Z",
                              "createTimeTaken": 5,
                              "lastAccessed": "2023-05-05T12:34:56.789Z",
                              "accessCountToday": 0,
                              "accessCountDailyMin": 0,
                              "accessCountDailyMax": 0,
                              "accessCountDailyAvg": 0,
                              "accessCount": 0,
                              "accessTimeTakenLast": 0,
                              "accessTimeTakenMin": 0,
                              "accessTimeTakenMax": 0,
                              "accessTimeTakenAvg": 0
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

## Suggested project plan / Indicative evaluation Plan
| API Endpoint    | Points |
| --------------- | ------- |
| **\`POST /api/shorten\`** (without stats object) | 15    |
| **\`GET /:shortUrl\`** (without stats) | 10    |
| **\`POST /api/shorten\`** (shortUrl level stats) | 20    |
| **\`GET /:shortUrl\`** (shortUrl level stats) | 20    |
| **\`GET /api/:shortUrl/stats\`** | 10 |
| **\`POST /api/shorten\`** (service level stats) | 15    |
| **\`GET /:shortUrl\`** (service level stats) | 15    |
| **\`GET /api/stats\`** | 10 |

It may be best to follow the above order and resist temptation to aim for more points first, as there is dependency of the second item on the first item and so on.


## TODO
- More user friendly, possibility to create a short URL from browser itself(GET) just by prefixing the service url in some manner to the target URL.
- What if memory is full and we are not able to create new short URLS? expiry of shortURLs, eviction, HTTP_NOT_OK, HTTP Status codes for various scenarios etc.
- What if we get requests for invalid shortURLs? stats, etc.
- HTTP status codes
