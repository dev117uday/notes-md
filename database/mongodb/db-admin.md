# DB admin

### Taking backups 
Json 
	mongoimport
	mongoexport
Bson
	mongorestore
	mongodump

```sh
mongoexport --uri="mongodb+srv://admin:ThisIsMyDSXMPH01@mycluster.aog3s.mongodb.net/sample_weatherdata" --collection=data --out=sales.json

// dont specifiy --out on bson
mongodump --uri="mongodb+srv://admin:ThisIsMyDSXMPH01@mycluster.aog3s.mongodb.net/sample_weatherdata" --collection=data 

mongorestore --uri "mongodb+srv://admin:ThisIsMyDSXMPH01@mycluster.aog3s.mongodb.net/sample_weatherdata"  --drop dump

mongoimport --uri="mongodb+srv://admin:ThisIsMyDSXMPH01@mycluster.aog3s.mongodb.net/sample_weatherdata" --drop sales.json
```

## Options to configure 

* default DB path : `mongod --dbpath`
* to change DB path : `mongod --dbpath` 
* to change PORT : `mongod --port` 
* to enable auth : `mongod --auth`
* to bind\_ip : `mongod --bind_ip 123.123.123.123`
* example configuration file : 
* to start the mongod with the config file : `mongod --config mongod.conf`

## Logging

#### To get log config \(containing verbosity\)

```sh
db.getLogComponents()
```

### To get logs

```sh
db.adminCommand({ "getLog" : "global" })
```

### View the logs through the command line:

```sh
tail -f /data/db/mongod.log
```

## Profiling DB

### Profiler Levels

### Commands

```sh
db.getProfiliingLevel()
db.setProfilingLevel(1)

# get profiling data
db.system.profile.find().pretty()
```

**Things profiled by profiler**

* CRUD operations
* administrative operations
* configuration operations

