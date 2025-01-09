Tags: [[Redis]] [[Cybersecurity]] [[Penetration Testing]] [[Databases]] 

## Introduction

#### What is Redis?
Redis (Remote Dictionary Server) is an open-source advanced No-SQL key-value data store used as a database, cache, and message broker. The data is stored in a dictionary format having key-value pairs. It is typically used for short term storage of data that needs fast retrieval. Redis does backup data to hard drives to provide consistency.

Redis is a database that stores its data in-memory. This is different than standard databases that store data in the HD or SSD. Redis is much faster than other databases in this way. It is used to cache data that is frequently requested for quick retrial. 

## Enumeration

```Bash
sudo nano -p- -sV $target
```


### Install Redis

```Bash
sudo apt isntall redis-tools
```

### Help 

```bash
redis-cli help
```

## Connect to Redis Database

```bash
redis-cli -h $target
```

## Get information about Server

```Bash
info
```


## Select Database

```bash
select 0
```

## Get Keys
```bash
keys * 
```

## Display key

```Bash
get <key>
```

