# db-administration

## DB administration

* default DB path : `mongod --dbpath`
* to change DB path : `mongod --dbpath` 
* to change PORT : `mongod --port` 
* to enable auth : `mongod --auth`
* to bind\_ip : `mongod --bind_ip 123.123.123.123`
* example configuration file : 

```bash
storage:
  dbPath: "/data/db"
systemLog:
  path: "/data/log/mongod.log"
  destination: "file"
replication:
  replSetName: M103
net:
  bindIp : "127.0.0.1,192.168.103.100"
tls:
  mode: "requireTLS"
  certificateKeyFile: "/etc/tls/tls.pem"
  CAFile: "/etc/tls/TLSCA.pem"
security:
  keyFile: "/data/keyfile"
processManagement:
  fork: true
```

```bash
storage:
  dbPath: "/var/mongodb/db/"
net:
  bindIp: localhost
  port: 27000
security:
  authorization: enabled
```

* to start the mongod with the config file : `mongod --config mongod.conf`

## Logging

#### To get log config \(containing verbosity\)

```text
db.getLogComponents()
```

### To get logs

```text
db.adminCommand({ "getLog" : "global" })
```

### View the logs through the command line:

```text
tail -f /data/db/mongod.log
```

## Profiling DB

### Profiler Levels

### Commands

```text
db.getProfiliingLevel()
db.setProfilingLevel(1)

# get profiling data
db.system.profile.find().pretty()
```

**Things profiled by profiler**

* CRUD operations
* administrative operations
* configuration operations

