Distributed Systems

basic setup:
    -URL "www.facebook.com"
    -dns lookup to 
    -http request to webserver server (webrick, puma)
        -rack hands off http request to application (rails, sinatra)
    -Application SQL request to database (Postgres, MySQL)