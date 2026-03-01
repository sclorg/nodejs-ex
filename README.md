
![Node.js CI](https://github.com/nodeshift-starters/nodejs-rest-http-crud/workflows/ci/badge.svg)
[![Coverage Status](https://coveralls.io/repos/github/nodeshift-starters/nodejs-rest-http-crud/badge.svg?branch=master)](https://coveralls.io/github/nodeshift-starters/nodejs-rest-http-crud?branch=master) 

Example CRUD Application

Test Push to Openshift

### Getting Started

#### Running Locally

First, install the dependencies

`npm install`

A Postgres DB is needed, so if you are using Docker, then you can start a postgres db easily.

`docker run --name os-postgres-db -e POSTGRESQL_USER=luke -e POSTGRESQL_PASSWORD=secret -e POSTGRESQL_DATABASE=my_data -d -p 5432:5432 centos/postgresql-10-centos7`

In this example, the db user is `luke`, the password is `secret` and the database is `my_data`

You can then start the application like this:

`DB_USERNAME=luke DB_PASSWORD=secret ./bin/www`


Then go to http://localhost:8080


Other options:

* `npm run dev` same as `npm start` but with pretty output log.
* `npm run dev:debug` shows debug information.


#### Running on Openshift

First, make sure you have an instance of Openshift setup and are logged in using `oc login`.

Then create a new project using the `oc` commands

`oc new-project fun-node-fun`

For this example, you will also need a postgres db running on your Openshift cluster.

`oc new-app -e POSTGRESQL_USER=luke -ePOSTGRESQL_PASSWORD=secret -ePOSTGRESQL_DATABASE=my_data centos/postgresql-10-centos7 --name=my-database`

Then run `npm run openshift` to deploy your app

Run the following command to show the newly exposed route that you can navigate:
```
oc get route nodejs-rest-http-crud
NAME                    HOST/PORT                                        PATH   SERVICES                PORT   TERMINATION   WILDCARD
nodejs-rest-http-crud   nodejs-rest-http-crud-opentel.apps-crc.testing          nodejs-rest-http-crud   8080                 None
```
#### Running on Openshift with traces enabled

* [Read more](./OTEL.md)
