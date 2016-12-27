# fdb

Flat Data Base

# data model

Tablespace -> Table + Indices

Table -> Tablet -> Row = <RowID, <AttrName, AttrValue>>

AttrName -> Index -> Idxlet -> <AttrValue, <RowID>>

RowID is automatically increasing, ordered on the insert time, and generated by the system

A Tablespace can contain billions of tables and a table can consist of unlimited number of rows

# concepts

Master

Node

Disk

Range

node -> disk -> range

# replication

Range works as the replication unit

Raft consensus

# split

Option A: a split is also a replicated write operation which creates a new range within the original disk, so it is triggered by the range leader without coordination by the master

Option B: a split is not local to the source node but migrates one or two new shards to other nodes so coordinated by the master; each range has a state machine - Creating, Active, Frozen, Removing, et al.

# rebalancing

data/load is rebalanced via replica adjustment coordinated by the master



