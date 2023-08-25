# URL Shortener Service

## Tech Used

- [Go](https://go.dev/)
- [Fiber](https://gofiber.io/)
- [Redis](https://github.com/redis/go-redis/)
- [Docker](https://www.docker.com/)

## Overview

This project was an exploration into Go, Fiber, Redis, and Docker to create a service that takes in a url to shorten, like [bit.ly](https://bitly.com/).

Currently, the API is exposed on port `3000` and is accessed via `POST localhost:3000/api/v1/`. When provided a `url` of type `string` in the body, the API will do some checks to make sure the provided URL doesn't already exist in the Redis database, normalizes the URL to be of the expected format, and provides a shortened url to the user that can be used to redirect people who click on the shortened URL to the original URL.

There is rate limiting implemented in this design and only allows 10 requests per 30 minutes to be made per IP address. Redis, normally used in a caching system, was chosen as the DB of choice due to it's K/V nature and also due to the design choice of shortened links having an expiry time of 24 hours.
