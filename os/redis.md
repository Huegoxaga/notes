# Redis

- It stands for REmote DIctionary Server
- It is a NoSQL Database that stores data in memory.
- It provides caches services in servers, it is fast.
- It can be used as a message broker.
- It is open source, BSD licensed.
- It provides persistence store option using snapshots.
- It is written in C.
- It stores key-value pairs, values can be either strings, hashes(dictionaries), lists, sets, and sorted sets.
  - The key should contain only printable ASCII characters.
  - The string value should anything smaller than 512MB.

## Installation

- run `brew install redis` for Mac.
- Optional, its binaries can be downloaded from its [Official Download](https://redis.io/download) page
  - Run `src/redis-server` to start the server after compilation, other installation will start redis server automatically.
  - Use `make install` for compilation will compile the binaries to the system, then environment path setting is no longer required.

## Configuration

- Config file is located at `/etc/redis/redis.conf`
- To run redis under systemd, set `supervised systemd`

## Redis CLI

- It can be used to access the database.
- Run `redis-server` to start the Redis server
- Run `redis-cli` to start the Redis CLI prompt.
- `ping` returns `pong` if the redis server is running.
- `flushall` will delete all records
- For some commands, returning `0` means not found or fail to execute, returning `1` means success. Returning `(nil)` means does not exist.
- `keys *` show all keys.
- Work with String Values
  - `set <key> <value>` add a key-value pair to the database.
  - `get <key>` get the key's value.
  - `del <key>` delete a record.
  - `setex <key> <ttl> <value>` add and key-value pair that will only exist in the number of second specified in `<ttl>`(time to live).
    - `psetex` will use millisecond for TTL value.
    - `ttl <key>` the number of seconds it will be avaliable.
  - `setnx <key> <ttl> <value>` add a key-value pair only when the key is not already used.
  - `strlen <key>` return the length of the string value.
  - `mset <key1> <value1> <key2> <value2>` add multiple value pairs at a time.
  - `decr <key>` return the value decreased by one, return the value as integer if it can be parsed to integer.
    - `incr <key>`
  - `decrby <key> <step>` decreased the value by the specified step.
    - `incrby <key> <step>`
  - `append <key> <value>` append a value to the key's value.
- Work with Dictionary Values
  - `hmset <Key> <DictKey1> <DictValue1> <DictKey2> <DictValue2>` add a dictionary.
  - `hget <Key> <DictKey>` get a value.
  - `hgetall <Key>` get all keys followed by their values in a dictionary.
  - `hexists <Key> <DictKey>` check if a dictionay key exists.
  - `hdel <Key> <DictKey>` delete a value.
  - `hsetnx <Key> <DictKey> <DictValue>` add a value only if it does not exist.
  - `hkeys <Key>` get all keys of a dictionary.
  - `hvals` get all values of a dictionary.
  - `hincrby <Key> <DictKey> <Step>` increase a value by a step.
  - `hlen <Key>` get the number of key-value pairs in the dictionary.
  - `hmget <Key> <DictKey1> <DictKey2>` get multiple values
- Work with Lists(Ordered) Values
  - For all the following command starting with `l`, replace it with `r` will make it execute from the right of the list.
  - `lpush <key> <value>` add one value to the left of the list.
    - `lpush <key> <value1> <value2>` add values to the left of the list, rightmost value will be added last.
  - `lrange <key> <start> <end>` get all values within the range from left to right.
    - `lrange key 0 -1` will return all records.
  - `lpop <key>` remove one value from the left.
  - `llen <key>` get the length of the list.
  - `lindex <key> <index>` get value based on the index starting from left at `0`.
  - `lset <key> <index>` set value according to the index from left.
  - `lpushx <key> <value>` add new value to the list only if the key exists.
  - `linsert <key> before <value> <value>` insert value before a value in the list.
  - `linsert <key> after <value> <value>` insert value after a value in the list.
- Work with Sets(Unordered) Values
  - It stores non duplicated values.
  - `sadd <key> <value1> <value2> <value3>` add one or multiple values to the set.
    - only non existing elements can be added.
  - `smembers <key>` get all values of the set.
  - `scard <key>` get the number of members in the set.
  - `sdiff <key1> <key2>` return set `key1` substruct set `key2`
    - `sdiffstore <key> <key1> <key2>` store the result into a new set.
  - `sunion <key1> <key2>` get the union of two sets.
    - `sunionstore <key> <key1> <key2>` store the result into a new set.
  - `sinter <key1> <key2>` intersection of two sets.
    - `sinterstore <key> <key1> <key2>` store the result into a new set.
  - `srem <key> <value1> <value2>` remove one or more members from a set.
  - `spop <key> <number>` remove a number of random members from the set.
  - `smove <key1> <key2> <value>` move one member from one set to the other set.
- Work with Sorted Sets Values
  - Each member in the set is corresponding to a score which determined its order(lower score goes first).
  - `zadd <key> <score1> <value1> <score2> <value2>` add member to the set with scores.
    - Multiple member can have the same score, then it will be order the the sequence it was added.
  - `zrange <key> <start> <end>` show the members of the sorted set.
  - `zcard` return the total number of members in the set.
  - `zcount <MinScore> <MaxScore>` count all member within the score range.
  - `zrem <key> <value>` remove a member.
  - `zrank <key> <value>` return the index of the member
  - `zrevrank <key> <value>` return the reversed index of the member
  - `zscore <key> <value>` return the score of a member
  - `zrangebyscore <key> <MinScore> <MaxScore>` return all members within the score range.
- Work with Messages
  - `SUBSCRIBE <topic>` start to subscribe a topic
  - `PSUBSCRIBE <topic>` subscribe to a topic name which matches a pattern
  - `PUBLISH <topic> <message>` publish a message to a topic
    - Use double qoutes for long message
