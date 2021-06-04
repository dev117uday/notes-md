# Mongodb

## MongoDB native

**To connect to database**

use the connect settings in mongodb atlas

**Starting local database server**

After installing, you can start the mongod by

```bash
sudo systemctl start mongod
```

if you receive an error : **Failed to start mongod.service: Unit mongod.service not found.**

**Run the following command first:**

```bash
sudo systemctl daemon-reload
```

**Verify that MongoDB has started successfully.**

```bash
sudo systemctl status mongod
```

**You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:**

```bash
sudo systemctl enable mongod
```

**Stop MongoDB.**

As needed, you can stop the [`mongod`](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) process by issuing the following command:

```bash
sudo systemctl stop mongod
```

**Restart MongoDB.**

You can restart the [`mongod`](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) process by issuing the following command:

```bash
sudo systemctl restart mongod
```

**Begin using MongoDB.**

Start a [`mongo`](https://docs.mongodb.com/manual/reference/program/mongo/#bin.mongo) shell on the same host machine as the [`mongod`](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod). You can run the [`mongo`](https://docs.mongodb.com/manual/reference/program/mongo/#bin.mongo) shell without any command-line options to connect to a [`mongod`](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) that is running on your localhost with default port 27017:

```bash
mongo
```

**To show collections**

```bash
show collections
```

### Basic Commands

* List all databases : `show dbs`
* to switch to db : `use <name_of_db>`
* to run a query : `db.<name_of_collection>.[function name]`
* to iterate over many results : `it` 
* add : `.pretty()` to see json better
* to find any one document from collection, just use `.findOne()` 
* to insert a document in collection : `db.<name of collection>.insert({ *your object* })` 
* to insert multiple documents, add \[ \] in your insert\(\) query function `db.<name of collection>.insert([ {"your": "objects"}, {"yours":"object"} ])`
* something `ordered : false`
* to create new collection : `db.createCollection("employees")`
* to shutdown db server : 

```text
use admin
db.shutdownServer()
exit
```

