## Spinning up MySQL Database with Docker

This is the best way to start, since you don't have to install MySQL locally and configure it and run into like thousands of issue and in the end not being able to make it, docker makes it much easier for me or probably for you also to spin up a MySQL database in minutes.

- Pull the latest image, `docker pull mysql:latest`, don't have to do it manually it will download automatically if not installed when we spin up the container.
- Start the container using the following command
  ```bash
  docker run --name <container_name> \
-p 3306:3306 \
-v mysql_volume:/var/lib/mysql/ -d \
-e "MYSQL_ROOT_PASSWORD=<root_password>"\
 mysql
  ```
  This will create a new container with name *<container_name>*, with the *mysql* image and publish the ports *3306* to the local environment to use the instance outside the container.

This also setup up the volume for the container to persist the database's data, so that it doesn't reset on restarts of the host system or the container.

You can pass in the following **Environment Variables** when starting the container:
- `MYSQL_ROOT_PASSWORD`: Set up your password using this environment variable.
- `MYSQL_ALLOW_EMPTY_PASSWORD`: Blank or Null password will be set. You have to set `MYSQL_ALLOW_EMPTY_PASSWORD=1`.
- `MYSQL_RANDOM_ROOT_PASSWORD`: a random password will be generated when the container is started. You have to set `MYSQL_RANDOM_ROOT_PASSWORD=1` to generate the random password.

> Don't pass in the permanent password in production, as the password will be visible in the shell history, which we obviously don't want. A possible solution is that we pass in a temporary password like temp123 and then change it afterwards.

We can **change the root password** as follows:
- Get into the container using 
```bash
docker exec -it <container_name> bash
```
- Login in to the MySQL shell using `mysql -u root -p`, this will prompt to enter the password which we set up before, in our case it was _temp123_.
- After logging into the shell, run the following SQL query to change the password
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY '<new_password>';
```

**References**:
- View [this](https://www.instapaper.com/read/1523582174/20140126) article on Instapaper with notes.
- View the original one [here](https://ostechnix.com/setup-mysql-with-docker-in-linux/).