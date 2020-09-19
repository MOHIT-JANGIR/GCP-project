# Deployment of WordPress Web Application by Integrating Google Cloud Platform with Kubernetes
🔰 PROJECT DESCRIPTION :

1. Create multi projects with dev and prod

2. Create VPC network for dev project

3.Create VPC network for prod project

4. Connect both the VPC network with VPC peering

5. Create a Kubernetes Cluster in dev project and launch a wordpress/Joomla application with the Load balancer

6. Create a SQL server in prod project and create a database

7. Connect the SQL database with the application launched in the K8s cluster

🛑 I completed this project using Google Qwiklab and since I use single project for both development and production .

![image](https://user-images.githubusercontent.com/61896468/93665629-8c59fc00-fa95-11ea-89ad-a238593e64bb.png) 
Before doing any practical we have to know some basic knowledge about that technology , so that anyone can admire our knowledge & thought process. So first we have to know about the what is the google cloud platform why do we use it ?

What is Google Cloud Platform ( GCP ) ?
Google Cloud is a suite of Cloud Computing services offered by Google. The platform provides various services like compute, storage, networking, Big Data , and many more that run on the same infrastructure that Google uses internally for its end users like Google Search and YouTube.

Google server hasn’t gone down in years. So, if you are planning to run your application on the Google Cloud infrastructure, then you can be assured of your applications being safe and secure.

Why Google Cloud?
Google Cloud has been one of the top cloud providers in the IT industry. The services they offer can be accessed by software developers, as it provides a reliable and highly scalable infrastructure to build, test, and deploy their applications.

Best Pricing: Google Cloud hosting plans are cheaper than other platforms’ hosting plans. Google Cloud offers to its customers the pay-as-you-go feature where the users only have to pay for the resources they use.

Work from Anywhere: Employees gain complete access to information across devices from anywhere in the world through web-based applications powered by Google.

Private Network: Google provides its own network to every customer so that they have more control and scalability over the network. It uses fiber-optic cables to spread its network, as they tend to bear any amount of traffic. Users get maximum time and efficiency due to this private network.

Security: Google has hired a large set of security professionals who help in protecting the data on servers. All data on the Cloud platform is encrypted. So, users can be sure of their data being safe and secure.

Redundant Backup: Google has its own in-built redundant backups. So, if the data stored by the user is lost, then Google would have created a backup for it. So, your data is technically not lost! Redundancy helps ensure data integrity, reliability, and durability.

So here i want to discuss about the some services provide by the GCP that will used by me to performing this task. So the services are followings:

→ Compute Services:

Compute Engine: Infrastructure as a Service to run Microsoft Windows and Linux Virtual Machine. It is a component of the Google Cloud platform which is built on the same infrastructure that runs Google’s search engine, YouTube, and other services.
Kubernetes Engine: It aims at providing a platform for automating deployment, scaling, and operations of application containers across clusters of hosts. It works with a wide range of container tools including docker.
→ Storage Services

Google Cloud Storage: An online file storage web service for storing and accessing data on a Google Cloud platform infrastructure. The service combines the performance and scalability of Google Cloud with advanced security and sharing capabilities.
Cloud SQL: A web service that allows you to create, configure, and use relational databases that live in Google Cloud. It maintains, manages, and administers your databases allowing you to focus on your applications and services.
→ Networking

VPC: Virtual Private Cloud provides a private network with IP allocation, routing, and network firewall policies to create a secure environment for your deployments.
Cloud Load Balancing: It is a process of distributing workloads across multiple computing resources. This reduces the cost and maximizes the availability of the resources.
So while doing this we need the kubernetes services provide the deploy our wordpress pods , so we have to know some basic concepts of the kubernetes.

What is Kubernetes ?
Kubernetes is an open-source system that allows organizations to deploy and manage containerized applications like platforms as a service (PaaS), batch processing workers, and micro services in the cloud at scale. Through an abstraction layer created on top of a group of hosts, development teams can let Kubernetes manage a host of functions — including load balancing, monitoring, deployment , providing the storage and controlling resource consumption by team or application, limiting resource consumption and leveraging additional resources from new hosts added to a cluster, and other workflows.

We can use kubernetes on our local system as well as on the top of cloud also . So in this task we are using the cloud to deploy our app or website on it.

🎯 PROJECT COMPLETION :

This project is based on deployment of WordPress application using Integration of Google Cloud Platform and Kubernetes by Google Kubernetes Engine .

So , Lets start building these real use case based cloud architecture ⏩

☁ Google Cloud Platform ☁

Google Cloud Platform (GCP), offered by Google, is a suite of cloud computing services that runs on the same infrastructure that Google uses internally for its end-user products, such as Google Search, Gmail and You tube.

1) For building any kind of Infrastructure on Google Cloud Platform we have to build it under a project . So, I created one project named as cloudproject for both platforms as development and production .

![image](https://user-images.githubusercontent.com/61896468/93665650-c2977b80-fa95-11ea-92b3-d95a2797027f.png)
2)Under these project we have to create two VPC ( Virtual Private Cloud ) one for WordPress deployment and second for MySQL Database Instance . I have created these VPC in different regions as VPC1 in us-central1 and VPC2 in us-east1 resp . As inside VPC we have to create subnet for networking actions of the instances . One more thing we have to do is attaching firewall rule which allows all traffic to come inside the VPC as Ingress Rule .

-->Creating firewall rule for Ingress traffic :

![image](https://user-images.githubusercontent.com/61896468/93665662-e35fd100-fa95-11ea-9d18-c5a3e4d39f6f.png)
--> Creating VPC network for development and production platforms :

![image](https://user-images.githubusercontent.com/61896468/93665670-fa062800-fa95-11ea-8ccc-9e8aeaab4b32.png)
3)For connecting these VPC's we have to use VPC Peering service of GCP . For peering the VPC'S we have to create VPC peer for both VPC1 and VPC2 as peer1 and peer2 .

![image](https://user-images.githubusercontent.com/61896468/93665827-4140e880-fa97-11ea-8490-97638f95429a.png)
![image](https://user-images.githubusercontent.com/61896468/93665840-4a31ba00-fa97-11ea-95b0-9338254dfd5b.png)
4) Now both VPC got connected by VPC peering .Then we have build a kubernetes master slave architecture i.e cluster for deployment of WordPress application .For kubernetes we don't need to create our own cluster and configure master and all because Google Cloud Platform provides Kubernetes As A Service by Google Kubernetes Engine .

To use Google Kubernetes Engine service we just have to tell the specifications in terms of Node Pool to them .Then they take all the responsibility further to create kubernetes cluster and about cluster management .

--> Creating Kubernetes Cluster for development platform in VPC1 :

![image](https://user-images.githubusercontent.com/61896468/93665849-73524a80-fa97-11ea-994a-593fb166bc3d.png)
![image](https://user-images.githubusercontent.com/61896468/93665862-82d19380-fa97-11ea-842b-6d0cbc913ea6.png)
-->Specifying node information for kubernetes cluster :

![image](https://user-images.githubusercontent.com/61896468/93665876-9da40800-fa97-11ea-9c90-1fb9a4418156.png)
![image](https://user-images.githubusercontent.com/61896468/93665890-a4cb1600-fa97-11ea-8438-298dc308b4e3.png)
--->Cluster Created Successfully...

![image](https://user-images.githubusercontent.com/61896468/93665903-b7dde600-fa97-11ea-8ce8-41c898bd9c29.png) 
5)For deploying the WordPress application in kubernetes cluster we have to contact with Google Kubernetes Engine .As to communicate with kubernetes master which send further task to its slave nodes we require kubectl program to be configured in our system .

In these case we are using Google Cloud Platform which provides us Kubernetes As A Service using Google Kubernetes Engine and for these we have to contact to GCP from our system .For these we have to install Google Cloud SDK Shell Program in our system which provides us all the GCP respective commands to use Google Cloud .

--> Log in to Google Cloud Platform using Google Cloud SDK :

gcloud auth login
![image](https://user-images.githubusercontent.com/61896468/93665918-cc21e300-fa97-11ea-912d-147c9e7291ac.png) 

---> Use of Google Cloud Native Commands :

gcloud project list
![image](https://user-images.githubusercontent.com/61896468/93665931-e65bc100-fa97-11ea-8338-1369c772c91b.png) 
To communicate with kubernetes cluster running on Google Cloud we have to update the kubeconfig file such that kubectl command is configured to contact to Google Kubernetes Engine .

To see the node information use command :

kubectl get nodes
6)To deploy the WordPress application using kubernetes we have to create deployment in kubernetes which using WordPress image for launching the pods .

kubectl create deployment (name) --image=(image_name)
In our case,

kubectl create deployment webapp --image=wordpress
After creating the kubernetes deployment we have to launch the WordPress application on internet as by default in kubernetes environment is isolated .For these we have to expose the deployment on port number 80 to access the application .Here we also require one load balancer for the deployment which balances all the traffic load coming from public world on the application .

⏩ Load Balancer : As we are using Google Kubernetes Engine which by default uses load balancer of Google Cloud Platform .But for kubernetes it is an external load balancer since we have to provide the load balancer to kubernetes deployment .

kubectl expose deployment (deployment_name) --type=LoadBalancer --port=80
In kubernetes the load balancer is known as Service .We can see all the services used by the deployment using command -->

kubectl get services
We can see through GUI one load balancer got created -->

![image](https://user-images.githubusercontent.com/61896468/93665949-fecbdb80-fa97-11ea-8ae4-678909f08b72.png) 
To see everything is properly created or not in kubernetes use command -->

kubectl get all
7)Now our front end of WordPress application got ready .To create the back end means to store the user data of WordPress application we use MySQL database . For us the critical thing is to manage the database for that we use Database As A Service by Google Cloud as MySQL .

So,we have to launch these MySQL Database instance using SQL service of Google Cloud in production environment i.e in VPC2.

![image](https://user-images.githubusercontent.com/61896468/93665959-160ac900-fa98-11ea-8591-f3dc12fdcd4b.png) 
--> Adding authorized network to public ip of MySQL Instance :

![image](https://user-images.githubusercontent.com/61896468/93665977-3470c480-fa98-11ea-95a2-2925ce45ebcd.png) 
--> Log in to MySQL Instance to see available databases :

mysql -h (public_ip) -u (user_name) -p
![image](https://user-images.githubusercontent.com/61896468/93665992-4e120c00-fa98-11ea-9481-a420749aa5ff.png)
![image](https://user-images.githubusercontent.com/61896468/93666005-59fdce00-fa98-11ea-86d1-98eb74865cca.png)
![image](https://user-images.githubusercontent.com/61896468/93666008-62560900-fa98-11ea-867d-cff75738382d.png)
-->Creating new database :

![image](https://user-images.githubusercontent.com/61896468/93666021-77329c80-fa98-11ea-9c2b-a28f575f97af.png) 
8) Final step is to connect WordPress application to back end i.e with MySQL Database . Using public ip of load balancer we can connect to WordPress application .

![image](https://user-images.githubusercontent.com/61896468/93666043-8fa2b700-fa98-11ea-954b-d596eaf69a9b.png) 
⏩ Now to connect MySQL database with WordPress application we have to add database login and password of the database user .

![image](https://user-images.githubusercontent.com/61896468/93666052-a77a3b00-fa98-11ea-9821-305e82d000d1.png) 
After successfully connecting the database and login to WordPress we can run the installation of the WordPress application .

![image](https://user-images.githubusercontent.com/61896468/93666066-bcef6500-fa98-11ea-8ae4-a5236f818792.png)
![image](https://user-images.githubusercontent.com/61896468/93666072-c547a000-fa98-11ea-9a89-85aa85a64246.png)
Finally In these way I successfully completed the Project of Google Cloud Platform Workshop based on Integrating Kubernetes with Google Cloud Platform using Google Kubernetes Engine to deploy WordPress web application .

✅ I would like to thanks Mr.Vimal Daga Sir for giving such great training on Google Cloud Platform and real use case kind of project which helps to enhance my skills in the world of Google Cloud Computing .
