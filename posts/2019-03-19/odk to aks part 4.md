Draft: yes
Category: Lab Notes
Tags: #kubernetes , #labnotes , #migratingodktok8s , #odk , #migratingodktok8s , migrating-odk-to-k8s

# Lab Notes Part 4

*I'm working on deploying an Aggregate 2.0 instance to Kubernetes in the cleanest possible way, and documenting my [progress in these lab notes](/tagged/migrating-odk-to-k8s).*

Now that I know the config magic I've worked on in the past couple posts is working, I can try spinning up and connecting to a real database! 

I don't believe in managing my own databases, so I'm going to use [Azure Database for MySQL](https://azure.microsoft.com/en-us/services/mysql/). Thankfully, it's pretty easy to launch a database using Azure Database Service - I won't walk through that process here. 



 