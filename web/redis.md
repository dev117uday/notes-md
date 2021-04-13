# Redis

## Setup

```
sudo docker run --name redis-learn -p 6370:6370 -d redis 
sudo docker exec -it redis-learn redis-cli

# to benchmark
sudo docker exec -it redis-learn redis-benchmark -n 1000 -d 10000
# -d for bytes of data

$ to set max memory limit (as LRU cache)
> config set maxmemory 128M
```

## Commands

**Set & Get value**

```
set name "uday"
get name
exists name
```

**All commands**

```
# Get all keys
keys *

# Delete all keys
flushall 
## options : async|sync
```



**Set key with expiry time**

```
# After 5 seconds, this  key will be deleted
set nametemp "uday" EX 5
get nametemp
exists nametemp

set a 2
get a
# expire after 3 seconds
expire a 3

# to check time remaining 
ttl a

# Another way, to expire after 10 seconds
setex b 10 "uday"
```

**Delete Key**

```
del name
```

**Set & Get multiple values**

```
mset first "uday" last "yadav"
mget first last
```

**Miscellaneous**

```
# Specifies the range : from 0th char to 3rd char
getrange name 0 3
strlen first

# Append to key
append name "uday"
append name " yadav"
```

**Math operations**

```
set count 1
incr count
incrby count 10
decr count 
decrby count 2
set pi 3.14
incrbyfloat pi 0.1
```

**Lists in redis**

```
lpush country india
lpush country USA
lpush country UK
lindex country 2
# lpush adds value infront
# to add values to the bottom
rpush country Australia

# to get all values in list
lrange country 0 -1
# to get first 2 values
lrange country 0 1

# get list length
llen country

# use lpop and rpop to remove the data from top and bottom, and it returns the element
lpop country
rpop country

# to change a key's value
lset country 0 germany

# to insert values before and after 
linsert country before "germany" "new zealand"
linsert country after "germany" "UAE"

# use lpushx and rpushx to add key to list only if it exists, else returns 0
```

**Sorting List**

```
# Alpha is needed only for strings, nothing for integers
sort country ALPHA
sort country desc ALPHA
```

**Sets in Redis**

```
sadd tech golang
sadd tech postgis python aws
sadd tech1 aws python mysql nodejs

# to see all members
smembers tech
# to get the length of set
scard tech
# to search the set
sismember tech aws

# to get the diff between to sets
sdiff tech tech1
# to store the difference btw 2 sets to a new set 
sdiffstore 	tech3 tech tech1
# to check intersection
sinter tech tech1
```

**Sorted Set Redis**

```
# add key values
zadd users 10 uday
zadd users 5 saatvik 8 kunal

# to get all users
zrange users 0 -1
zrange users 0 -1 withscores
zrevrange users 0 -1

# to get the length of the string
zcard users
# to get key's value over a range
zcount users 0 2
# to remove member
zrem users uday
```

**Hashes in Redis**

```
# add keys to a set
hset myhash name uday
hset myhash email dev117uday@gmail.com

# get all keys from hashset
hkeys myhash
# to get all values
hvals myhash
# to check for keys 
hexists myhash name
# check the length	
hlen myhash
# to set multiple values at once
hmset myhash country india phone_no 9810039759 age 24
# to get multiple values
hmget myhash country name email
# increment some value
hincrby myhash age 2
# to delete key from set
hdel myhash age
# to avoid over writting the values
hsetnx myhash name Uday
```

**Transaction**

```
# to go in transaction mode
multi
set name1 uday
set name2 yadav
set a 1
exec

# to discard transaction
discard
```

**Pub/Sub**

```
subscribe my-chat
publish my-chat "hello world"

# to subscribe to channel with patterns in name
psubscribe chats*
psubscribe h?llo
```

- If no one is sub to the channel you specify in publish, it returns 0

**Benchmarking Redis**

```
redis-benchmark -n 1000 -d 10000
```

**GeoSpatial Data**

```
# add geo spatial data ing long : lat
GEOADD maps 77.216721 28.644800 delhi
GEOADD maps 72.877426 19.076090 mumbai

# data is tored in sorted set data structure
zrange maps 0 -1
# use withscores to get the values

# to get the geohash of city
GEOHASH maps delhi

# to get long:lat
GEOPOS maps delhi
# to get distance, in meter (default)
GEODIST maps delhi mumbai
GEODIST maps delhi mumbai km
# within distance
GEORADIUS maps 77.216721 28.644800 2000 km
GEORADIUS maps 77.216721 28.644800 2000 km withcoord
GEORADIUS maps 77.216721 28.644800 2000 km withcoord withdist
GEORADIUSBYMEMBER maps delhi 1300 km
GEORADIUSBYMEMBER maps delhi 1300 km withcoord withdist desc|asc
```

