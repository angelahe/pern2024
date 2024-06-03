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

## setup
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

