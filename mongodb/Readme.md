For import existing collections:

1. Copy to container
`sudo docker cp posts.json mongodb:/data/posts.json`
3. paste to database
`sudo docker exec -it mongodb mongoimport --db orcus --collection posts --file /data/posts.json --jsonArray --username <username> --password <password> --authenticationDatabase admin`
