# GCP Core Infra

## Why Core Infrastructure

* Identify the purpose and value of Google Cloud
* Choose best deployment environment
* Choose storage options
* Interact and experience google cloud

![gcp service categories](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled.png>)

![cloud advantages](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 1.png>)

![evolution of cloud](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 2.png>)

![Infrastructure as service](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 3.png>)

* IaaS : Pay for what they allocate
* PaaS : Pay for what they use

![cloud structure](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 4.png>)

Google's nine products have more than one billion users each. Google designs and builds its own data centers, which incorporate multiple layers of physical security protections. Access to these datacenters is limited to only a very small number of Google employees. Security features include encryption using centrally managed keys and hardware encryption in hard drives and SSDs. The GFE additionally applies protections against denial-of-service attacks. Google also has multi-tier, multi-layer DoS protections that further reduce the risk of any DoS impact on a service running behind the GFE.

![cloud cost](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 5.png>)

Specifically, when you run an instance for more than 25% of a month, Compute Engine automatically gives you a discount for every incremental minute you use for that instance. Custom virtual machine types allow Compute Engine virtual machines to be fine tuned with optimal amounts of vCPU and memory for the applications so that you can tailor your pricing for your workloads.

![project structure gcp](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 6.png>)

* folder can contain sub folders
* policies are applied at project, folder and org node level
  * some can be applied at resource level
  * policies are inherited downwards

![projects in GCP](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 7.png>)

Attributes of project

* project\_id
* project\_name
* project\_number

![info about projects](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 8.png>)

![resource manager](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 9.png>)

![organization nodes](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 10.png>)

![top level of org](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 11.png>)

who can do what and on which part

* who can be :
  * a google account
  * a google group
  * service account
  * cloud identity domain
* can do what
  * defined by a role

![types of IAM](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 12.png>)

**Basic role**

* Owner
* Editor
* Viewer
* Billing Admin

Can be too general when working with sensitive data

![basic IAM role](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 13.png>)

![pre-define IAM role](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 14.png>)

![custom IAM role](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 15.png>)

![custom IAM role](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 16.png>)

* service accounts do need to be managed

![service account](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 17.png>)

![Cloud identity](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 18.png>)

* more on cloud identity

![ways to access gcp](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 19.png>)

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

![type of VPC](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 20.png>)

![what is vpc](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 21.png>)

![info on VPC](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 22.png>)

![what is compute engine](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 23.png>)

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>range of compute services</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (9) (3).png" alt=""><figcaption><p>virtual machine VM lifecycle</p></figcaption></figure>

![what are virtual machine](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 24.png>)

![vm and disk relation](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 25.png>)

A preemptible VM is different from an ordinary Compute Engine VM in only one respect. Compute Engine has permission to terminate a job if its resources are needed elsewhere. Although savings are possible with preemptible VMs, you need to ensure that your job can be stopped and restarted. In terms of storage, Compute Engine doesn't require a particular option or machine type to get high-throughput between processing and persistent disks.

Let's say, you have a workload that doesn't require a human to sit and wait for it to finish, such as a batch job analyzing a large dataset. You can save money, in some cases up to 90 percent by choosing preemptible VMs to run the job

![autoscale vs manual scale](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 26.png>)

![vm upper limit](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 27.png>)

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>general purpose virtual machone</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>compute optimized virtual machone</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption><p>memory optimized virtual machone</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>preemptible virtual machine</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>spot virtual machine</p></figcaption></figure>



![routing tables](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 28.png>)

![firewall in GCP](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 29.png>)

![DNS ](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 30.png>)

![Google's DNS](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 31.png>)

![ Managed DNS](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 32.png>)

![Cloud CDN](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 33.png>)

![type of networking](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 34.png>)

![IPsec VPN protocol](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 35.png>)

![Direct peering](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 36.png>)

![carrier peering](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 37.png>)

![dedicated interconenct](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 38.png>)

![partner interconnect](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 39.png>)

![blob in storage bucket](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 40.png>)

![GCP cloud storage bucket](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 41.png>)

![why use cloud storage](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 42.png>)

![blob](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 43.png>)

![obejct version in storage bucket](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 44.png>)

* Object versioning

![scope and permisson object storage](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 45.png>)

![type of storage options](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 46.png>)

![type of storage options](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 47.png>)

![storage options](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 48.png>)

![Cloud SQL](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 49.png>)

![more info on cloud SQL](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 50.png>)

![intro to cloud spanner](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 51.png>)

![intro to firestore](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 52.png>)

![intro ot bigtable](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 53.png>)

![type database to choose](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 54.png>)

![what is a container](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 55.png>)

![what is kuberentes](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 56.png>)

![kubernetes cluster](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 57.png>)

![Google managed Kubernetes Engine](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 58.png>)

![hybrid and multi-cloud ](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 59.png>)

![Anthos](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 60.png>)

![GKE](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 61.png>)

![GKE autopilot](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 62.png>)

![microservice in gCP](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 63.png>)

![why container](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 64.png>)

![standard env vs flexible env](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 65.png>)

![cloud endpoints](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 66.png>)

![APIgee Engine](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 67.png>)

![Cloud RUN](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 68.png>)

![Simple deployment model](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 69.png>)

![Cloud functions](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 70.png>)

![intro to terraform](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 71.png>)

![what is Sre](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 72.png>)

![monitoring](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 73.png>)

![SRE pyramid](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 74.png>)

![SRE job](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 75.png>)

![latency](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 76.png>)

![latency](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 77.png>)

![traffic](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 78.png>)

![traffic part2](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 79.png>)

![saturation](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 80.png>)

![saturation 2](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 81.png>)

![handling error in cloud](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 82.png>)

![handling error in cloud 2](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 83.png>)

![SLI vs SLO vs SLA](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 84.png>)

![SLI](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 85.png>)

Number of good events / count of all valid events

![SLO](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 86.png>)

![SLO](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 87.png>)

![SLA](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 88.png>)

![improve service reliability](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 89.png>)

![SLO](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 90.png>)

![ops team functions](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 91.png>)

![who to maintain ops](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 92.png>)

![how to maintain ops](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 93.png>)

![cloud monitoring](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 94.png>)

![cloud logging](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 95.png>)

![cloud logging](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 96.png>)

![cloud logging](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 97.png>)

![type of cloud logging](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 98.png>)

![error reporting](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 99.png>)

![debugger](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 100.png>)

![cloud trace](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 101.png>)

![cloud profiler](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 102.png>)
