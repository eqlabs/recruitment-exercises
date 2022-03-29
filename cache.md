Periodic Self-Rehydrating Cache

## Requirements

The challenge is to implement `Cache`, which is able to:

- Register a function with `0` arguments under some key.
- To keep the last computated value of the executed function.

When the given function is registered, at some period of time,
it will be computated again and the returned value will be stored,
so it can be fast-accesible, basically the cache will be returning the recorded value instead of executing the function.


### What kind of problem we are solving here

In practice, we often are working with data which is not changing much over time,
but the function that is producing this data is slow.

> Example: Function, which does multiple queries to an external service, which is returing weather data categorized by cities.
> Because of the rate limit of the APIs, the function can take 2 or more minutes to be executed.
> The weather is changing, sometimes very often during the day, so we need to register the function under the key
> `:weather_data` with `ttl` of 1 hour and `refresh_interval` 10 minutes.
> This way after the function is registered, we would have almost accurate data at any time, but we won't have to wait for the data.

In a similar fashion to a [cron job](https://en.wikipedia.org/wiki/Cron),
the function is executed at a given interval of time.
In addition to that, `Cache` is keeping the last computated value and can provide it when needed.
​
The main problems, which are solved in this challenge are not the ones for keeping the data (we can use some DB like Postgres/MySQL/MariaDB/etc for that).
The problems solved are:

- Planning the execution of tasks at a given interval.
- Concurrent execution of tasks (More in [Details](Details)).
- Concurrent wait for the results (More in [Details](Details)).

### Code skeletons

cache.ex
```elixir

defmodule Cache do
  use GenServer

  @type result ::
          {:ok, any()}
          | {:error, :timeout}
          | {:error, :not_registered}

  @impl GenServer
  def start_link(opts \\ []) do
  end

  @doc ~s"""
  Register a function `fun` that will be computed and its value stored.
  Arguments:
    - fun - 0-arity function that computes the value and returns either {:ok, value}
    or {:error, reason} tuple.
    - key - A term which is associated with the function and is used to retrieve
    the stored value
    - ttl - Time to live, how long (in milliseconds) the value is stored before it is
    discarded if the value is not refreshed.
    - refresh_interval - How often (in milliseconds) is the function recomputed and
    the new value stored. refresh_interval is strictly smaller than ttl. After
    the value is refreshed, the ttl counter is restarted.
  Details:
  The function value is stored only if {:ok, value} is returned. {:error, reason}
  results are not stored. If {:error, reason} is returned the value is not stored
  and the function will be again computed on the next run.
  """
  @spec register_function(
          fun :: (() -> {:ok, any()} | {:error, any()}),
          key :: any,
          ttl :: non_neg_integer(),
          refresh_interval :: non_neg_integer()
        ) :: :ok | {:error, :already_registered}
  def register_function(fun, key, ttl, refresh_interval) when is_function(fun, 0) do
  end

  @doc ~s"""
  Get the value associated with `key`.
  If the value for `key` is stored in the cache, the value is returned immediately.
  If a recomputation is in progress, the last stored value is returned.
  If the value for `key` is not stored in the cache but a computation of the function
  associated with this key is in progress, wait up to `timeout` milliseconds. If
  the value is computed in this interval, the value is returned. If the computation
  does not finish in this interval, {:error, :timeout} is returned
  If `key` is not associated with any function return {:error, :not_registered}
  """
  @spec get(any(), non_neg_integer(), Keyword.t()) :: result
  def get(key, timeout \\ 30_000, opts \\ []) when is_integer(timeout) and timeout > 0 do
  end
end
```

store.ex
```elixir

defmodule Cache.Store do
  def store(store, key, value, ttl) do
  end

  def get(store, key) do
  end
end
```
