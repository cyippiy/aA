# Distributed Systems

## basic setup:
* URL www.facebook.com
* dns lookup to www.faceboo.com => xyz.ec2.aws.com
* http request to webserver server (webrick, puma)
    *  rack hands off http request to application (rails, sinatra)
* Application SQL request to database (Postgres, MySQL)
    * db data fetched from or saved to disk 

## terms for terminal:
* dig - lookup ip address, kinda like a phonebook
    * dig www.google.com
        * 172.217.164.100
* nc - netcat
    * nc some ip address
        * GET / HTTP 1.1
        * host: www.google.com


## DNS
* after you receive the domain name, you have to redirect the DNS so the application reflects based on CNAME and the IP address associated with it
    * for github, it'll require CNAME with url, then one of the 4 IP addresses


## scaling
* Parallel tasks: we have CPUs that can execute and evaluate code simutaneously
* run application on a server with many CPU cores to handle more users
    * scaling up


## app tier ai
* user to DNS
* user to NGIX 
    * load balancer
* splits off into application tier
    * multiple servers that handle the appplication request
* communicates to the POSTGRES which communicates to the database tier

# Distributed Database
* want to use RAM over disk because it's faster for lookup. so if possible
    * however, need to write to disk because ram can/will be deleted
* if possible, try to copy database to ram for faster read
* ways to stress database
    * writeload is too high and readload too low
        * disk can only handle so much writeload
    * small active set for ram but entire huge active set is evenly used too much
* can either scale up or scale out
    * scale up means buying better equipment
    * scale out means buying more cheaper equipment

## Leader Follower Replication
* tells a leader and then leader ships logs (aka updates) to other followers so the app tier can properly read from any POSTGRES at the database tier
* sync replication
    * go to POSTGRES leader for update
    * leader tells follower to update, but one gets updated.
    * if someone queries for account balance, the first follower will have it
        * however, there's a chance another follower who wasn't updated yet will have the original data
            * back in time
            * this can be remediated if the machines are sticky and forces a user to only communicate with the same database over and over
            * Serializability failure
* what happens when the leader dies/fails?
    * assign the follower to be new leader. but how do you determine it? need to sync up before assigning leader
* what happens when the leader fails before the update?
    * it's okay to fail before unconfirmed
        * if async, window of dataloss possible where the sync occurs during confirm.
            * generally updates are in batches parallel
* async is more efficient but limited dataloss

## Mult Leader Replication
* two leaders will handle 50% of writes and then shipped logs
    * every machine still needs to have the update. increasing surface area
* uniqueness constrant difficult between two db
* bigger chance of conflict with two database updating without conflict
    * before update, coordinate with other database to halt/check
        * costs time
* async database may not update other databases quickly enough
* sync has more latency, but more efficient
## Sharding
* separate data through hashes
    * also known as point query, or one row query

# Distributed Systems day 3
# linearlization failure
* when leader is updated, then a user tries to see the data from a follower db, returns new data, but refreshes and the data is received from an non-updated follower db
# partition doesn't work well on join tables
* denormalize the database by storing names
* have to to name change all tables that reference that changed data
# __ACID__ (_Atomicity_, _Consistency_, _Isolation_, _Durability_) database
* __Durability__
    * saved data is never lost
    * accomplished by writing data out to disk before acknoledging it is saved
    * database should never enters a corrupted, unrecoverable state
* __Consistency__
    * database constraints are enforced
    * if you add a foreign key constraint or a uniqueness constraint, DB must enforce these
* __Atomicity__
    * A transation is a grouping of SQL statements
    * db writes log lines that describe the steps of the transaction
    * if middle of transaction your DB loses power or transaction fails, on recovery it "replays" all committed transactions in order
* __Isolation__
    * Transactions that update disjoint data can be processed in parallel
    * Parallel execution is essential to fast DB performance
        * takes advantage of multiple CPU cores
        * gives the db something to do as it waits for data to be read from or written to disk
    * oppoiste is called serial execution: transactions are processed one-at-a-time. you don't start next transaction until current one is finished
## Two phase locking
* whenever read or write a record, you must first "lock" it
* if two transactions try to lock a row at the same time, only one of them gets the lock
* if a transaction can't lock a row, it must wait until it's unlocked
* locks are held until the end of the transaction. then they are released
* two phase locking achieves "serializability"
    * serializability means the transactions are processed as if they are a single serial executor
    * if transaction starts only after the previous finishes
    * but serializability lets you process in parallel, as long as the result is always the same as a serial order

# Distributed Systems day 4

* two transactions being processed at the same time
    * it's considered slow if it's not async, realistic situations have multiple transactions parallel at once
* because transactions are not commutative, result is not compatible with a linear ordering of the transaction
* locking addresses this issue
    * acquire lock on row first, then either read or write (mutate)
    * all locks will be released at the end
        * two phase locking
    * deadlock is when a transaction attempts to access a locked row
* how does lock work
    * lock table
        * naive
        * atomic solution with test-and-set
## multiversion concurrency control
* isolation across partititions
* idempotent transactions can allow coordinator to redo logs from the last transaction completed
    * solves atomicity but doesn't solve isolation
## two phase commit
* what happens when a db gets locked out and the user's connection dies
    * coordinator failure => unavailability of other machine's data
    * can be solved with timeout
        * reintroduces isolation
## leader/followers
* when a leader fails, one of the followers will be promoted to leader
* manual intervention
    * requires operator
    * determines leader is dead, can promote one
## netsplit
* when leader is split from the followers
* how do we choose from the new leader
    * through voting. systems have random interval for an election if no connection
    * not byzentine fault tolerance