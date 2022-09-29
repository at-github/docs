# Shell

## Summary
- [Install](Install)
- [Configuration](Configuration)

## Install
`sudo apt install mongodb`

> The data directory /var/lib/mongodb and the log directory /var/log/mongodb are created during the installation.
> By default, MongoDB runs using the mongodb user account. If you change the user that runs the MongoDB process, you must also modify the permission to the data and log directories to give this user access to these directories.
> - [Source](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/)

## Init System
`sudo systemctl start mongod`

> If you receive an error similar to the following when starting mongod:
> Failed to start mongod.service: Unit mongod.service not found.
> Run the following command first:
`sudo systemctl daemon-reload`
> Then run the start command above again.
> - [Source](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/)
Doesn’t work anyway, …

### Another solution
Create file `/etc/systemd/system/mongodb.service`
And put this code inside:
```
[Unit]
Description=High-performance, schema-free document-oriented database
After=network.target

[Service]
User=mongodb
ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf

[Install]
WantedBy=multi-user.target
```
[Source](https://askubuntu.com/questions/770054/mongodb-3-2-doesnt-start-on-lubuntu-16-04-lts-as-a-service/770133#770133)

## Configuration

### Configuration File
> The official MongoDB package includes a configuration file (/etc/mongod.conf).
> - [Source](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/)
