---
id: S2QXzyqfCZTpgUE8OXUKq
title: Deploy Jar
desc: ""
updated: 1641492257105
created: 1641489787412
---

- right click target and select open in terminal

* then type java -jar {the jar name start of it then can press tab to autocomplete}

After that the server is deployed.

application.properties is where you define your connection details.

flyaway is for database migrations, manage db schema as we evolve

to create the database inside of the docker instance we are using so we can use the name of the db in our java app.

we have to remove into the contianer and create the DB

we do that by

```terminal
docker exec -it {CONTAINER ID} bin/bash

psql -U {username}


\l

CREATE DATABASE {name}

\c {db name}

\d
\dt
```

the second line logs in to postgress as user

the third line lists all the database currently have

connect to the database using the fourth command

5 and 6 are used for describing the database 5 is for everything 6 is just for tables
