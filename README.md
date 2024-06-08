# pern2024

## purpose
learn how to use PERN so I can migrate from MERN to PERN
and can also upgrade gtdxm to use secured db

following this medium article:
https://medium.com/@ritapalves/get-started-with-the-pern-stack-an-introduction-and-implementation-guide-e33c55d09994#id_token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjQ1MjljNDA5Zjc3YTEwNmZiNjdlZTFhODVkMTY4ZmQyY2ZiN2MwYjciLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2FjY291bnRzLmdvb2dsZS5jb20iLCJhenAiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJhdWQiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJzdWIiOiIxMDUxOTI3NTY0MDg3NDE2OTc4MTkiLCJoZCI6ImF2aWFrLmNhIiwiZW1haWwiOiJhbmdlbGFAYXZpYWsuY2EiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwibmJmIjoxNzIzMzkzNDc0LCJuYW1lIjoiQW5nZWxhIEhlbmRlcnMiLCJwaWN0dXJlIjoiaHR0cHM6Ly9saDMuZ29vZ2xldXNlcmNvbnRlbnQuY29tL2EvQUNnOG9jSW93RC05X0xsNGctYmRuenhRSm54LW10aGlUUlFYazJsRkxxWXJSX3hPS21rdXBKQ3o9czk2LWMiLCJnaXZlbl9uYW1lIjoiQW5nZWxhIiwiZmFtaWx5X25hbWUiOiJIZW5kZXJzIiwiaWF0IjoxNzIzMzkzNzc0LCJleHAiOjE3MjMzOTczNzQsImp0aSI6ImMyYTI5ZjVmZTg2MGM2MjkwZTU0YWI2ZjcyZjcwMGZkMDUxNDA3ZjUifQ.oRcKQWR4dKfCytUxRn8wTLCG0yJUtGRRzdOxaLrQ7gf223frDElusLPKrK89o1bsd4vvkowNfLqXcEhr1YMQm1Qh7CEQMLxMsf5UASd6oPuwFdSbMtrYLACjUHAaaF1lQuOoBkH14RwBR9qGsFH_uXjZBFNqRPXcDDQVfmmGLciI5Ge_iMQqI87Rkf4XZsP52Zkmlrf_CMyDVuYLMXf2yYKB7x36m_2QOj9uE-N3GgxXAlqHVoW1fAhNLoQ-q-vgy0bEIzsFul60QKipWrM1ucLiWwBywuAuOj4Uwv1aalH7LG96Inq618QL5GCQWfiGlUW6l2SsdXTfgxyxAM7juw

## introduction

PERN - PostgreSQL, Express, React, Node.js
PostgreSQL - open source object relational db mgmt systm
supports both sql and json
is ACID compliant and table based
complete constraints, triggers, roles
benefits: extensible, scalable, reliable, performant, robust

express - free js web framework design to use with node.js
build apis quickly and easily
features for routing, middleware, handling http requests and responses
(application back end)

react - for UI (front end)

Node.js - js runtime for serverside and networking applications e.g. web servers

client interacts with frontend
react receives client request and sends to server side
server side receives request and handles request with Express to connect to the db

## Needed for this implementation
docker
node.js
vscode
npx
(pgAdmin, postman, nodemon) optional

## setup client and server
> cd server
> nvm use 20 (v20.9.0)
> npm init
install express, pg, dotenv
> npm install express
> npm install pg
> npm install dotenv --save

> nvm use 20
> npx create-react-app client
> cd client
> npm install axios
note: axios has 6 high vulnerabilities, 2 moderate

## setup db
will use a docker postgresql image
docker login --username your_username_here.
ie angelahe

go to hub.docker.com search for postgres
docker pull postgres
docker images

docker postgreSQL image:

see .env which wasn't committed to git
docker run --name postgres16 -e POSTGRES_USER=<username> -e POSTGRES_PASSWORD=<password> -p 8070:8070 -d postgres 

(port already in use), used 8070
netstat -an | grep LISTEN

docker ps // to see the docker process is up and running

docker exec -it postgres16 psql -U root
select now();  //to confirm I'm connected
\q to quit

## create db and populate it
> docker cp ./<path_to_file>/init.sql <container_name>:/tmp/init.sql
ie docker cp ./init.sql postgres16:/tmp/init.sql

> docker exec -it <container_name> /bin/bash -c "psql -U <postgres_user> -d <postgres_database> -f /tmp/init.sql"

ie docker exec -ti postgres16 /bin/bash -c "psql -U root -d public -f /tmp/init.sql"
psql: error: connection to server on socket "/var/run/postgresql/.s.PGSQL.5432" failed: FATAL:  database "public" does not exist

instead do right from command line:
> after docker exec -it
> psql -h localhost -U postgres
# CREATE DATABASE public
# \l // for list of databases
# q
# \c public // to connect to db I just created
paste content of init.sql to insert the table and data
confirm it's in by SELECT * from products;

## create the API
index.js to create the API
> node index.js
Server listening on port 9000

test http://localhost:9000 and should return 'Hello World'

optional files for organization:
- Routes: Forward the requests to the appropriate controller functions, to handle them;
- Controllers: Contain functions to handle specific routes and determine the appropriate response to send back to the user;
- Services: Contain functions to handle possible errors;
- Database files: Contain functions to perform CRUD operations in a database.

## configure the postgresql connection

create connection between the db and the api
create db.config.js - config file to connect to postgresql using a connection string

use pg to create a connection pool (cache of db connections maintained for efficient reuse in future db requests)

check if connection is working:
create route for products

## troubleshoot the connection
lsof -i :9000 // make sure port not used elsewhere
> node index.js
then try get http://localhost:9000/products

get error:
Error: read ECONNRESET
    at TCP.onStreamRead (node:internal/stream_base_commons:217:20) {
  errno: -54,
  code: 'ECONNRESET',
  syscall: 'read'
}

and in postman, get socket hang up

docker logs postgres16i

## see Mike discussion in backend master
changed env to port 5432, will need to recreate the data again

TODO: next layer is to have a db container that has an external volume for writing the data

## re-enter the data
create docker with -p 8070:5432
docker exec -it postgres16 psql -U root
CREATE DATABASE public
\q
docker exec -ti postgres16 /bin/bash -c "psql -U root -d public -f /tmp/init.sql"

## make API calls from the UI
2 options:
axios * using here
fetch

update package.json to have proxy 9000
update App.js
- useState: A React hook that allows declaring a state variable and its setter function to update the state;
- useEffect: A React hook that allows declaring an effect that should run after every render, in this case, or when certain values change.

> npm i bootstrap

