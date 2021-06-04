---
description: pr0
---

# Cassandra : Scylla

### Setup : Docker

```bash
sudo docker run --name scyllaTest -d scylladb/scylla
sudo docker exec -it scyllaTest nodetool status
sudo docker exec -it scyllaTest cqlsh
```



