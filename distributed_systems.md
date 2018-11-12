# Distributed Systems

## basic setup:
* URL www.facebook.com
* dns lookup to www.faceboo.com => xyz.abc.com
* http request to webserver server (webrick, puma)
    *  rack hands off http request to application (rails, sinatra)
* Application SQL request to database (Postgres, MySQL)

## terms for terminal:
* dig - lookup ip address, kinda like a phonebook
    * dig www.google.com
        * 172.217.164.100
* nc - netcat
    * nc some ip address
        * GET / HTTP 1.1
        * host: www.google.com
