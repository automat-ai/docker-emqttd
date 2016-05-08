# MQTT & Postgres

This is an emqttd container that is preconfigured to use Postgres for user credentials and ACL.

## To start the container

```bash
$ docker-compose up --build
```

Then you can access mqtt dashbaord at http://_YOUR_DOCKER_HOST_:18083/

Only one user is preconfigured:
	Username: client
	Password: public

	The only topic it has access is: /World

You can modify the users and ACL in the provisioning/data/030-database/mqtt-table-*.sql


## Connect to Postgres

```bash
$ PGPASSWORD=postgres psql -h 192.168.99.100 --user postgres --port 5432 -d mqtt
```

## To create a new user with salt

```bash
$ PASSWORD=MySecretPassword SALT=$(uuidgen) && echo SALT=$SALT && printf ${SALT}${PASSWORD} | shasum -a 256
```
