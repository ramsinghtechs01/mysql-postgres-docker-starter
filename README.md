# How to Run Postgres in a Docker Container

1. Go to https://hub.docker.com/_/mysql and pull mysql image
	docker pull mysql:latest

2. Create docker-compose.yml file

3. Run mysql docker container
	--docker-compose up -d

4. Check logs
	--docker logs <container-id> -f

5. Connect to mysql
	docker exec -it mysql-docker bash
    mysql -uroot -p

6. Mysql queries
	--View all available databases in mysql
		show databases;
	--Using a selected database
	    use <database-name>
	--create table
		CREATE TABLE persons (
	    personid int,
	    lastname varchar(255),
	    firstname varchar(255)
	    );

    -- to view tables
       show tables;

    -- Insert into table   
		INSERT INTO persons (personid, lastname, FirstName) VALUES (1,'aveti','tutorial');
		INSERT INTO persons (personid, lastname, firstname) VALUES (2,'John','Doe');    

7. Persist Data of mysql 
	--use volume mount in docker-compose file
	sudo mkdir -p ./data/db
	map above directory in docker-compose.yml

8. Use custom configuration file
	-- store conf in your local machine and use it mysql container
	-- validate 
	mysql -p -e "show variables like '%max_allowed_packet%';"

	mysql -p -e "show variables like '%max_connections%';"
