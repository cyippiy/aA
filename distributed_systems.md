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

## Distributed Database
* want to use RAM over disk because it's faster for lookup. so if possible
    * however, need to write to disk because ram can/will be deleted
* if possible, try to copy database to ram for faster read
* ways to stress database
    * writeload is too high and readload too low
        * disk can only handle so much writeload
    * small active set for ram but entire huge active set is evenly used too much