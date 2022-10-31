# GCP Core Infra

## Why Core Infrastructure

* Identify the purpose and value of Google Cloud
* Choose best deployment environment
* Choose storage options
* Interact and experience google cloud

### GCP service categories

![gcp service categories](gcp-core-infra-img/gcp-core-infra-0.png)

### Cloud advantages

![cloud advantages](gcp-core-infra-img/gcp-core-infra-1.png)

### Evolution of cloud

![evolution of cloud](gcp-core-infra-img/gcp-core-infra-2.png)

### Infrastructure as service

![Infrastructure as service](gcp-core-infra-img/gcp-core-infra-3.png)

* IaaS : Pay for what they allocate
* PaaS : Pay for what they use

### Cloud structure

![cloud structure](gcp-core-infra-img/gcp-core-infra-4.png)

Google's nine products have more than one billion users each. Google designs and builds its own data centers, which incorporate multiple layers of physical security protections. Access to these datacenters is limited to only a very small number of Google employees. Security features include encryption using centrally managed keys and hardware encryption in hard drives and SSDs. The GFE additionally applies protections against denial-of-service attacks. Google also has multi-tier, multi-layer DoS protections that further reduce the risk of any DoS impact on a service running behind the GFE.

### Cloud cost

![cloud cost](gcp-core-infra-img/gcp-core-infra-5.png)

Specifically, when you run an instance for more than 25% of a month, Compute Engine automatically gives you a discount for every incremental minute you use for that instance. Custom virtual machine types allow Compute Engine virtual machines to be fine tuned with optimal amounts of vCPU and memory for the applications so that you can tailor your pricing for your workloads.

### Project structure gcp

![project structure gcp](gcp-core-infra-img/gcp-core-infra-6.png)

* folder can contain sub folders
* policies are applied at project, folder and org node level
  * some can be applied at resource level
  * policies are inherited downwards

### Projects in GCP

![projects in GCP](gcp-core-infra-img/gcp-core-infra-7.png)

Attributes of project

* project\_id
* project\_name
* project\_number

### Info about projects

![info about projects](gcp-core-infra-img/gcp-core-infra-8.png)

### Resource manager

![resource manager](gcp-core-infra-img/gcp-core-infra-9.png)

### Organization nodes

![organization nodes](gcp-core-infra-img/gcp-core-infra-10.png)

### Top level of org

![top level of org](gcp-core-infra-img/gcp-core-infra-11.png)

who can do what and on which part

* who can be :
  * a google account
  * a google group
  * service account
  * cloud identity domain
* can do what
  * defined by a role

### Types of IAM

![types of IAM](gcp-core-infra-img/gcp-core-infra-12.png)

**Basic role**

* Owner
* Editor
* Viewer
* Billing Admin

Can be too general when working with sensitive data

### Basic IAM role

![basic IAM role](gcp-core-infra-img/gcp-core-infra-13.png)

### Pre-define IAM role

![pre-define IAM role](gcp-core-infra-img/gcp-core-infra-14.png)

### Custom IAM role

![custom IAM role](gcp-core-infra-img/gcp-core-infra-15.png)

### Custom IAM role

![custom IAM role](gcp-core-infra-img/gcp-core-infra-16.png)

* service accounts do need to be managed

### Service account

![service account](gcp-core-infra-img/gcp-core-infra-17.png)

### Cloud identity

![Cloud identity](gcp-core-infra-img/gcp-core-infra-18.png)

* more on cloud identity

### Ways to access gcp

![ways to access gcp](gcp-core-infra-img/gcp-core-infra-19.png)

## Quiz

Q1 : When would you choose to have an organization node? (Select two)

* When you want to create folders
* When you want to centrally apply organization-wide policies

Q2 : Which statement best describes how Google Cloud resources are associated within the resource hierarchy?

* Google Cloud resources are not associated with the resource hierarchy.

Q3 : Consider a single hierarchy of Google Cloud resources. Which of these situations is possible? (Choose 3 responses.)

* There is no organization node, and there are no folders.
* There is an organization node, and there is at least one folder.

Your company has two Google Cloud projects and you want them to share policies. What is the least error-prone way to set this up?

* Define the new shared policy in the organization node.

Q5 : What is the difference between Identity and Access Management (IAM) basic roles and IAM predefined roles?

* Basic roles can only be granted to single users. Predefined roles can be associated with a group.

Q6 : Select the option that displays IAM roles from general to specific.

* Predefined roles, custom roles, basic roles

Q7 : How does the resource hierarchy control how IAM policies are inherited?

* IAM policies are only implemented at the project level; they cannot be amended by lower levels of the resource hierarchy.

Q8 : Which way of accessing Google Cloud lets you control services through the code you write?

* APIs

### Type of VPC

![type of VPC](gcp-core-infra-img/gcp-core-infra-20.png)

### Virtual Private Cloud Network ( VPC )

![what is vpc](gcp-core-infra-img/gcp-core-infra-21.png)

![info on VPC](gcp-core-infra-img/gcp-core-infra-22.png)

A **virtual private cloud (VPC)** is a secure, isolated private cloud hosted within a public cloud. VPC customers can run code, store data, host websites, and do anything else they could do in an ordinary private cloud, but the private cloud is hosted remotely by a public cloud provider. (Not all private clouds are hosted in this fashion.) VPC's combine the scalability and convenience of public cloud computing with the data isolation of private cloud computing.

You can 

- segment your networks

- use firewall rules to restrict access to instances

- create static routes to forward traffic to specific destinations.

![](images/image-20210103012024708.png)

### Compute Engine

- Compute Engine lets you create and run virtual machines on Google infrastructure. 

![what is compute engine](gcp-core-infra-img/gcp-core-infra-23.png)

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>range of compute services</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (9) (3).png" alt=""><figcaption><p>virtual machine VM lifecycle</p></figcaption></figure>

### What are virtual machine

![what are virtual machine](gcp-core-infra-img/gcp-core-infra-24.png)

### VM and disk relation

![vm and disk relation](gcp-core-infra-img/gcp-core-infra-25.png)

A preemptible VM is different from an ordinary Compute Engine VM in only one respect. Compute Engine has permission to terminate a job if its resources are needed elsewhere. Although savings are possible with preemptible VMs, you need to ensure that your job can be stopped and restarted. In terms of storage, Compute Engine doesn't require a particular option or machine type to get high-throughput between processing and persistent disks.

Let's say, you have a workload that doesn't require a human to sit and wait for it to finish, such as a batch job analyzing a large dataset. You can save money, in some cases up to 90 percent by choosing preemptible VMs to run the job

### Autoscale vs manual scale

![autoscale vs manual scale](gcp-core-infra-img/gcp-core-infra-26.png)


### VM upper limit

![vm upper limit](gcp-core-infra-img/gcp-core-infra-27.png)

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>general purpose virtual machone</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>compute optimized virtual machone</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption><p>memory optimized virtual machone</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>preemptible virtual machine</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>spot virtual machine</p></figcaption></figure>


### App Engine

- The App Engine platform manages the hardware and networking infrastructure required to run your code. To deploy an application on App Engine, you just hand App Engine your code and the App Engine service takes care of the rest. 

- App Engine provides you with a built-in services that many web applications need. App engine will scale your application automatically in response to the amount of traffic it receives. App Engine is especially suited for applications where the workload is highly variable or unpredictable like web applications and mobile backend. 
- App Engine offers two environments: standard and flexible.

![image-20210107010843408](images/image-20210107010843408.png)

- Standard is the simpler. It offers a simpler deployment experience than the Flexible environment and fine-grained auto-scale.  Low utilisation applications might be able to run at no charge. Google provides App Engine SDK's in several languages, so that you can test your application locally before you upload it to the real App Engine service. The SDK's also provide simple commands for deployment.

- In App Engine SE, you use a runtime provided by Google. App Engine Standard Environment provides runtimes for specific versions of Java, Python, PHP and Go. The runtimes also include libraries that support App Engine APIs. The Standard Environment also enforces restrictions on your code by making it run in a so-called "Sandbox." That's a software construct that's independent of the hardware, operating system, or physical location of the server it runs on.

![image-20210107011113713](images/image-20210107011113713.png)

- App Engine flexible environment lets you specify the container your App Engine runs in. App Engine manages these Compute Engine machines for you. They're health checked, healed as necessary, and you get to choose which geographical region they run in, and critical backward-compatible updates to their operating systems are automatically applied. All this so that you can just focus on your code. 

![image-20210107011202378](images/image-20210107011202378.png)



### Routing tables

![routing tables](gcp-core-infra-img/gcp-core-infra-28.png)

### Firewall in GCP

![firewall in GCP](gcp-core-infra-img/gcp-core-infra-29.png)

### DNS 

![DNS ](gcp-core-infra-img/gcp-core-infra-30.png)

### Google's DNS

![Google's DNS](gcp-core-infra-img/gcp-core-infra-31.png)

###  Managed DNS

![ Managed DNS](gcp-core-infra-img/gcp-core-infra-32.png)

### Cloud CDN

![Cloud CDN](gcp-core-infra-img/gcp-core-infra-33.png)

### type of networking

![type of networking](gcp-core-infra-img/gcp-core-infra-34.png)

### IPsec VPN protocol

![IPsec VPN protocol](gcp-core-infra-img/gcp-core-infra-35.png)

### Direct peering

![Direct peering](gcp-core-infra-img/gcp-core-infra-36.png)

### Carrier peering

![carrier peering](gcp-core-infra-img/gcp-core-infra-37.png)

### Dedicated interconnect

![dedicated interconnect](gcp-core-infra-img/gcp-core-infra-38.png)

### Partner interconnect

![partner interconnect](gcp-core-infra-img/gcp-core-infra-39.png)

### Blob in storage bucket

![blob in storage bucket](gcp-core-infra-img/gcp-core-infra-40.png)

### GCP cloud storage bucket

![GCP cloud storage bucket](gcp-core-infra-img/gcp-core-infra-41.png)

### Why use cloud storage

![why use cloud storage](gcp-core-infra-img/gcp-core-infra-42.png)

### Blob

![blob](gcp-core-infra-img/gcp-core-infra-43.png)

### Object version in storage bucket

![object version in storage bucket](gcp-core-infra-img/gcp-core-infra-44.png)

* Object versioning

### Scope and permisson object storage

![scope and permisson object storage](gcp-core-infra-img/gcp-core-infra-45.png)

### Type of storage options

![type of storage options](gcp-core-infra-img/gcp-core-infra-46.png)

### Type of storage options

![type of storage options](gcp-core-infra-img/gcp-core-infra-47.png)

### Storage options

![storage options](gcp-core-infra-img/gcp-core-infra-48.png)

### Database & Storage :

![image-20210103022816378](images/image-20210103022816378.png)

![image-20210103023014178](images/image-20210103023014178.png)

- **Cloud Bigtable** uses the interface of the open source database **Apache HBase**.
- **Cloud Dataproc** offers the open source big data environment **Hadoop**, as a managed service.
- **Cloud storage** allows you to save data and files.
- **Cloud SQL** is a fully managed service that makes it easy to set up, manage, and administer relational databases: PostgreSQL, MySQL, and SQL Server.
- **Cloud Spanner** is a NewSQL database developed by Google.
- **Cloud Datastore** is a highly scalable, fully managed NoSQL database service.

### Compute : 

- **Google Stackdriver** lets customers monitor workload across multiple cloud providers.
- **Compute Engine** lets you create and run virtual machines on Google infrastructure. 
- **Kubernetes Engine** secure and managed Kubernetes service.
- **App Engine** fully managed application runtime. Standard & Flexible.
- **Cloud Endpoint** Develop, deploy, protect, and monitor your APIs with Cloud Endpoints.
- **Cloud Functions** Scalable pay-as-you-go (FaaS) to run your code with zero server management.

### Code & Monitoring

- **Cloud Source Repository** Fully featured Git Repo hosted on GCP

![image-20210107014046277](images/image-20210107014046277.png)

![image-20210107014354503](images/image-20210107014354503.png)



### Google Cloud Big Data Platform

![image-20210107014606939](images/image-20210107014606939.png)

- **Cloud Dataflow** fully managed streaming analytics service that minimizes latency, processing time, and cost through autoscaling and batch processing.
- **Big Query**  serverless, highly scalable, and cost-effective data warehouse designed to help you turn big data into informed business decisions.
- **Cloud Pub/Sub** Messaging and ingestion for event-driven systems and streaming analytics.
- **Cloud DataLab** easily explore, visualize, analyze, and transform data using familiar languages, such as Python and SQL

### Google Cloud Machine Learning Platform

![image-20210107015846097](images/image-20210107015846097.png)



### Cloud SQL

![Cloud SQL](gcp-core-infra-img/gcp-core-infra-49.png)

### More info on cloud SQL

![more info on cloud SQL](gcp-core-infra-img/gcp-core-infra-50.png)

### Intro to cloud spanner

![intro to cloud spanner](gcp-core-infra-img/gcp-core-infra-51.png)

### Intro to firestore

![intro to firestore](gcp-core-infra-img/gcp-core-infra-52.png)

### Intro to bigtable

![intro to bigtable](gcp-core-infra-img/gcp-core-infra-53.png)

### Type database to choose

![type database to choose](gcp-core-infra-img/gcp-core-infra-54.png)



### Google Cloud Storage

![](images/big_table.png)

What's object storage? It's not the same as file storage, in which you manage your data as a hierarchy of folders. It's not the same as block storage, in which your operating system manages your data as chunks of disk. Instead, object storage stores arbitrary bunch of bytes with a unique key. often in the form of URLs which means object storage interacts nicely with Web technologies. It's a fully managed scalable service.

Use case 

- serving website content

- storing data for archival and disaster recovery

- distributing large data objects to your end users via Direct Download.

It is comprised of buckets you create and configure and use to hold your storage objects. The storage objects are immutable, you create new versions every time you update. Data in-transit is encrypted using HTTPS. 

### Cloud Storage classes

![](images/image-20210103014201867.png)

![](images/image-20210103014340390.png)

## Cloud Bigtable

![](images/Cloud_Bigtable.png)

Cloud Bigtable is Google's NoSQL, big data database service.

Your databases in Bigtable are sparsely populated tables that can scale to billions of rows and thousands of columns allowing you to store petabytes of data. GCP fully manages the surface. It's ideal for data that has a single lookup key. 

Some applications developers think of Bigtable as a persistent hash table. Cloud Bigtable is ideal for storing large amounts of data with very low latency. It supports high throughput, both read and write,

Use cases : 

- Internet of Things

- user analytics
- financial data analysis. 

![](images/image-20210103015836826.png)

## Cloud SQL & Cloud Spanner

![](images/image-20210103021631899.png)

![](images/sql-spanner.png)

- Cloud SQL offers both MySQL and PostgreSQL database engines as a fully managed service, that are capable of handling terabytes of storage. 

- Cloud SQL provides several replica services like read, failover, and external replicas. It can replicate data between multiple zones with automatic failover. It also helps you backup your data with either on-demand or scheduled backups. It can also scale both vertically by changing the machine type, and horizontally via read replicas. 

- Cloud SQL instances include network firewalls, and customer data is encrypted when on Google's internal networks, and when stored in database tables, temporary files, and backups. 

- They are accessible by other GCP services and even external services. You can authorise Compute Engine instances for access Cloud SQL instances and configure the Cloud SQL instance to be in the same zone as your virtual machine. 

- Cloud SQL also supports other applications and tools that you might be used to, like SQL WorkBench, Toad, and other external applications using standard MySQL drivers. 

If Cloud SQL does not fit your requirements because you need horizontal scalability, consider using ***\*Cloud Spanner\****. It offers transactional consistency at a global scale, schema, SQL, and automatic synchronous replication for high availability. And, it can provide petabytes of capacity. Consider using Cloud Spanner if you have outgrown any relational database, or sharding your databases for throughput high performance, need transactional consistency, global data and strong consistency, or just want to consolidate your database.

- Use cases include : 
  - financial applications
  - inventory applications.

## Cloud DataStore

![](images/Cloud_Datastore.png)

Cloud Datastore highly scalable NoSQL database. One of its main use cases is to store structured data from App Engine apps. It is a from a fully-managed service, Cloud Datastore automatically handles sharding and replication, providing you with a highly available and durable database that scales automatically to handle load. Unlike Cloud Bigtable, it also offers transactions that affect multiple database rows, and it lets you do SQL-like queries. 

### What is a container

![what is a container](gcp-core-infra-img/gcp-core-infra-55.png)

### What is kuberentes

![what is kuberentes](gcp-core-infra-img/gcp-core-infra-56.png)

### Kubernetes cluster

![kubernetes cluster](gcp-core-infra-img/gcp-core-infra-57.png)

### Google managed Kubernetes Engine

![Google managed Kubernetes Engine](gcp-core-infra-img/gcp-core-infra-58.png)

### Hybrid and multi-cloud 

![hybrid and multi-cloud ](gcp-core-infra-img/gcp-core-infra-59.png)

### Anthos

![Anthos](gcp-core-infra-img/gcp-core-infra-60.png)

### GKE

![GKE](gcp-core-infra-img/gcp-core-infra-61.png)

### GKE autopilot

![GKE autopilot](gcp-core-infra-img/gcp-core-infra-62.png)

### microservice in gCP

![microservice in gCP](gcp-core-infra-img/gcp-core-infra-63.png)

### Why container

![why container](gcp-core-infra-img/gcp-core-infra-64.png)

### Standard env vs flexible env

![standard env vs flexible env](gcp-core-infra-img/gcp-core-infra-65.png)

### cloud endpoints

![cloud endpoints](gcp-core-infra-img/gcp-core-infra-66.png)

### APIgee Engine

![APIgee Engine](gcp-core-infra-img/gcp-core-infra-67.png)

### Cloud RUN

![Cloud RUN](gcp-core-infra-img/gcp-core-infra-68.png)

### Simple deployment model

![Simple deployment model](gcp-core-infra-img/gcp-core-infra-69.png)

### Cloud functions

![Cloud functions](gcp-core-infra-img/gcp-core-infra-70.png)

### Intro to terraform

![intro to terraform](gcp-core-infra-img/gcp-core-infra-71.png)

### What is SRE

![what is Sre](gcp-core-infra-img/gcp-core-infra-72.png)

### Monitoring

![monitoring](gcp-core-infra-img/gcp-core-infra-73.png)

### SRE pyramid

![SRE pyramid](gcp-core-infra-img/gcp-core-infra-74.png)

### SRE job

![SRE job](gcp-core-infra-img/gcp-core-infra-75.png)

### Latency

![Latency](gcp-core-infra-img/gcp-core-infra-76.png)

### Latency

![Latency](gcp-core-infra-img/gcp-core-infra-77.png)

### Traffic

![Traffic](gcp-core-infra-img/gcp-core-infra-78.png)

### Traffic part2

![Traffic part2](gcp-core-infra-img/gcp-core-infra-79.png)

### Saturation

![Saturation](gcp-core-infra-img/gcp-core-infra-80.png)

### Saturation 2

![Saturation 2](gcp-core-infra-img/gcp-core-infra-81.png)

### Handling error in cloud

![Handling error in cloud](gcp-core-infra-img/gcp-core-infra-82.png)

### Handling error in cloud 2

![Handling error in cloud 2](gcp-core-infra-img/gcp-core-infra-83.png)

### SLI vs SLO vs SLA

![SLI vs SLO vs SLA](gcp-core-infra-img/gcp-core-infra-84.png)

### SLI

![SLI](gcp-core-infra-img/gcp-core-infra-85.png)

Number of good events / count of all valid events

### SLO

![SLO](gcp-core-infra-img/gcp-core-infra-86.png)

### SLO

![SLO](gcp-core-infra-img/gcp-core-infra-87.png)

### SLA

![SLA](gcp-core-infra-img/gcp-core-infra-88.png)

### Improve service reliability

![Improve service reliability](gcp-core-infra-img/gcp-core-infra-89.png)

### SLO

![SLO](gcp-core-infra-img/gcp-core-infra-90.png)

### OPS team functions

![OPS team functions](gcp-core-infra-img/gcp-core-infra-91.png)

### Who to maintain OPS

![who to maintain OPS](gcp-core-infra-img/gcp-core-infra-92.png)

### How to maintain OPS

![how to maintain OPS](gcp-core-infra-img/gcp-core-infra-93.png)

### Cloud monitoring

![Cloud monitoring](gcp-core-infra-img/gcp-core-infra-94.png)

### Cloud logging

![Cloud logging](gcp-core-infra-img/gcp-core-infra-95.png)

### Cloud logging

![Cloud logging](gcp-core-infra-img/gcp-core-infra-96.png)

### Cloud logging

![Cloud logging](gcp-core-infra-img/gcp-core-infra-97.png)

### Type of Cloud logging

![type of Cloud logging](gcp-core-infra-img/gcp-core-infra-98.png)

### Error reporting

![error reporting](gcp-core-infra-img/gcp-core-infra-99.png)

### Debugger

![debugger](gcp-core-infra-img/gcp-core-infra-100.png)

### Cloud trace

![Cloud trace](gcp-core-infra-img/gcp-core-infra-101.png)

### Cloud profiler

![Cloud profiler](gcp-core-infra-img/gcp-core-infra-102.png)
