# Operations

## Inserting Operations

```bash
db.<name of collection>.insert({ *your object* })

## To insert multiple objects

db.<name of collection>.insert([ {"your": "objects"}, {"yours":"object"} ])

## example : one
db.zips.insert({ "city" : "ALBANY", "zip" : "12210", "loc" : { "y" : 42.65677, "x" : 73.76052 }, "pop" : 9374, "state" : "NY" } )

## example : many
db.zips.insert( [{ "city" : "ALBANY", "zip" : "12210", "loc" : { "y" : 42.65677, "x" : 73.76052 }, "pop" : 9374, "state" : "NY" },{ "city" : "ALBANY", "zip" : "12210", "loc" : { "y" : 42.65677, "x" : 73.76052 }, "pop" : 9374, "state" : "NY" }] )
```

add : `, {"ordered"true}` before the last `)` to insert many docs orderly

## Finding document

```bash
db.zips.findOne({"state":"NY"})
db.zips.findMany({"state":"NY"})
```

## Updating documents

* `updateOne()` and `findOne()` for one document only
* `updateMany()` and `find()` for many documents
* to increment a field docs :

  ```bash
  db.zips.updateMany({ "city": "HUDSON" }, { "$inc": { "pop": 10 } })
  ```

* to set value :

  ```bash
  db.zips.updateOne({ "zip": "12534" }, { "$set": { "pop": 17630 } })
  ```

* to push new fields to array

  ```bash
  db.grades.updateOne({ "student_id": 250, "class_id": 339 },
                    { "$push": { "scores": { "type": "extra credit",
                                              "score": 100 }
                                }
                      })
  ```

## To delete

* `deleteOne()` for one doc and `deleteMany()` to delete multiple

```bash
db.inspections.deleteMany({ "test": 1 })

db.inspections.deleteOne({ "test": 3 })
```

