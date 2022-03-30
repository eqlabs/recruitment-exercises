Periodic Self-Rehydrating Cache

## Requirements

The challenge is to implement a periodic self-rehydrating cache. In order to do so, the cache must be able to register 0-arity functions (each under a new key) that will recompute periodically and store their results in the cache for fast-access instead of being called every time the values are needed.

In addition your code must be thoroughly tested and documented.

### Context for the exercise

This type of cache is useful when we the we are working with data that doesn't change often and its benefits become clear if computing the data is expensive in the first place.

As an example, let's consider an application that makes multiple queeries to an external service returning weather data categorized by cities. Because of API rate-limiting, the queries could take multiple minutes or more to execute but the weather can be fast changing. In order to have fresh data in the cache at all times, we can register function like `:weather_data` with a `ttl` ("time to live") of 1 hour and a `refresh_interval` of 10 minutes. Similarly to a [cron job](https://en.wikipedia.org/wiki/Cron), the function is executed at a given interval of time and the cache holds the most recently computed value and can provide it as needed.

Our focus in this challenge are on:

- The execution of tasks at given intervals.
- The concurrent execution of tasks.
- The concurrent waiting on task results.

The data must be in memory, persistance over application restarts isn't in scope for this exercise.

### Code skeletons

We provide a code skeleton to get you started on the exercise [`cache.ex`](./cache.ex).

