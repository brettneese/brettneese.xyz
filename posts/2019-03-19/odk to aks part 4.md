Draft: yes
Category: Lab Notes
Tags: #kubernetes , #labnotes , #migratingodktok8s , #odk , #migratingodktok8s , migrating-odk-to-k8s

# Lab Notes Part 4

*I'm working on deploying an Aggregate 2.0 instance to Kubernetes in the cleanest possible way, and documenting my [progress in these lab notes](/tagged/migrating-odk-to-k8s).*

Now that I know the config magic I've worked on in the past couple posts is working, I can try spinning up and connecting to a real database! 


## Spinning up a staging MySQL DB 

Our existing ODK installation uses MySQL, although this is no longer recommended and fresh installs should use PostgreSQL. I don't believe in managing my own databases, so I'm going to use [Azure Database for MySQL](https://azure.microsoft.com/en-us/services/mysql/). Thankfully, it's pretty easy to launch a database using Azure Database Service - I won't walk through that process here.

I do, however, have to login to the database and initialize it. I initially struggled to find the right command to connect, often running into an error such as:

```
ERROR 9002 (28000): The connection string may not be right. Please visit portal for references.
````

Thanks to [StackOverflow](https://stackoverflow.com/questions/44035710/connection-to-azure-mysql-server-fails-due-to-incorrect-connection-string#44035711), I learned the correct connection command for `mysql` is actually: 

```
mysql -u mysql@odk-staging.mysql.database.azure.com -h odk-staging.mysql.database.azure.com -p

```
 
My mistake was that the username _must_ be `mysql@odk-staging.mysql.database.azure.com` -- including the hostname.
 
I also ran into an issue with my IP address:

```
ERROR 9000 (HY000): Client with IP address '$MYIP' is not allowed to connect to this MySQL server.
```

And had to manually navigate to the "Connection Security" tab in the Azure Portal and add my IP to the whitelist.

![](_1.png)

Now that I'm in, I can simply execute:

```
CREATE DATABASE aggregate;
CREATE USER aggregate@'%' IDENTIFIED BY 'aggregate';
GRANT ALL ON aggregate.* TO odk@'%' IDENTIFIED BY 'aggregate';
FLUSH PRIVILEGES;
```

After I confirmed I can log in with this user, I logged in again as the `mysql` user to update the password to something more secure than `aggregate`:


```
ALTER USER 'aggregate'@'%' IDENTIFIED BY 'newPass';
```

I can now update 
