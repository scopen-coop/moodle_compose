# How to use it ?

The docker-compose.yml file is used to build and run Moodle in the current workspace.
This docker image intended for developpement usage.

Structure des dossiers
www/docker/docker_moodle
www/moodle

First times create volume for maria db

    mkdir -p /opt/data/moodle
    
    docker volume create --driver local \
        --opt type=none \
        --opt device=/opt/data/moodle \
        --opt o=bind mariadb-moodle

And then, you can run :

        docker-compose up

### .env file

Then, create a .env file all environment variables, including the root password, as follows (the password is raw after the equal sign) :

       `MYSQL_ROOT_PASSWORD=root`

PLEASE, do apply secure permissions to this .env file (in **production**):

        chmod 600 .env


### Run compose

This will run 4 container Docker : Moodle, MariaDB, PhpMyAdmin and Maildev.

On first install set
        
            moodle-mariadb
        
as databse host

The URL to go to the Dolibarr is :

        http://0.0.0.0

The URL to go to PhpMyAdmin is (login/password is root/root) :

        http://0.0.0.0:8080

In Dolibarr configuration Email let PHP mail function, To see all mail send by Dolibarr go to maildev

        http://0.0.0.0:6081
