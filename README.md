# URL Shortener

## Demo
https://user-images.githubusercontent.com/92099051/195704601-3a3b1fba-a4df-46fa-b969-344b6dffcf94.mp4



## How to Run
While in the directory enter the following line: `flask run -p <port>`

## API Endpoints for Requests
### Generate a short URL-
POST - http://127.0.0.1/shorten <br>
POST - http://127.0.0.1/shorten/<user_id>

Body: must include "url"
```json
{
  "url": "www.hello.com"
}
```

Response:<br>
```json
{
    "short_url": "http://127.0.0.1/3GSJrD"
}
```

### Redirect URL -
GET - http://127.0.0.1/<suffix_hash>

### Sign up -
POST - http://127.0.0.1/sign_up

Body: must include "email" and "name"
```json
{
  "email": "lior@walla.com",
  "name": "lior"
}
```

### Log in -
POST - http://127.0.0.1/log_in

Body: must include "email"
```json
{
  "email": "lior@walla.com",
}
```

### Get user's URLs -
GET - http://127.0.0.1/shorten/<user_id>

Response:<br>
```json
{
  "url_data": [
    {
      "short_url:" "http://127.0.0.1/5gDZEF",
      "original_url": "https://github.com/LiorSB/url-shortener/tree/feature/backend-db-ds",
      "creation_date": "2022-10-08T23:14:47.558657",
      "expiration_date": "2027-10-07T23:14:47.558657"
    },
    {
      "short_url": "http://127.0.0.1/1bqOQw",
      "original_url": "https://www.w3schools.com/python/python_mongodb_find.asp",
      "creation_date": "2022-10-08T23:56:03.839908",
      "expiration_date": "2027-10-07T23:56:03.839908"
    }
  ]
}
```

## Load Balancer
The load balancer used in this system is HAProxy with the `RoundRobin` strategy.<br>
Guide links: 
- [HAProxy Configuration](https://www.haproxy.com/blog/the-four-essential-sections-of-an-haproxy-configuration/#:~:text=There%20are%20four%20essential%20sections,routed%20to%20your%20backend%20servers.)
- [How to Use HAProxy](https://www.digitalocean.com/community/tutorials/how-to-use-haproxy-to-set-up-http-load-balancing-on-an-ubuntu-vps)
- [HAProxy Manual](https://www.haproxy.org/download/1.4/doc/configuration.txt)

## Cache
`flask_caching` has been used with the `SimpleCache` cache type. [Flask Caching Docs](https://flask-caching.readthedocs.io/en/latest/)

## Data Base
MongoDB has been used as the DB and its collections have been sharded by their ID with the `hashed` strategy.<br>
How it was built: [Deploy a Sharded Cluser](https://www.mongodb.com/docs/manual/tutorial/deploy-shard-cluster/)

## Reason
Shortening URLs can be handy where there is a limit for the number of characters, for example: chat boxes of twitter, instagram, facebook and other platforms.

## Requirements
- Create front-end with React.
- Create back-end with Python.
- Create database with MongoDB.

- Generate a short URL from a long URL.
- Encode short URL path.
- Once a short URL has been entered to the address bar, redirect to the original (long) URL.
- Handle expired URL’s.
- Store: short URL, long URL, creation date, expiration date and the user to the DB.
- Load balancer.
- Create premium users.
- Make the search function as efficient as possible to prevent latency issues.
- Premium users can view their URLs history.

## Nice to Have
- Premium users have a longer expiration time.
- Premium users can choose a path to the short URL by following a set of rules that match the format.
