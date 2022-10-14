# GCP Core Infra

## Why Core Infrastructure

* Identify the purpose and value of Google Cloud
* Choose best deployment environment
* Choose storage options
* Interact and experience google cloud

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 1.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 2.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 3.png>)

* IaaS : Pay for what they allocate
* PaaS : Pay for what they use

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 4.png>)

Nine of Google's nine products have more than one billion users each. Google designs and builds its own data centers, which incorporate multiple layers of physical security protections. Access to these datacenters is limited to only a very small number of Google employees. Security features include encryption using centrally managed keys and hardware encryption in hard drives and SSDs. The GFE additionally applies protections against denial-of-service attacks. Google also has multi-tier, multi-layer DoS protections that further reduce the risk of any DoS impact on a service running behind the GFE.

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 5.png>)

Specifically, when you run an instance for more than 25% of a month, Compute Engine automatically gives you a discount for every incremental minute you use for that instance. Custom virtual machine types allow Compute Engine virtual machines to be fine tuned with optimal amounts of vCPU and memory for the applications so that you can tailor your pricing for your workloads.

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 6.png>)

* folder can contain sub folders
* policies are applied at project, folder and org node level
  * some can be applied at resource level
  * policies are inherited downwards

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 7.png>)

Attributes of project

* project\_id
* project\_name
* project\_number

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 8.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 9.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 10.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 11.png>)

who can do what and on which part

* who can be :
  * a google account
  * a google group
  * service account
  * cloud identity domain
* can do what
  * defined by a role

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 12.png>)

**Basic role**

* Owner
* Editor
* Viewer
* Billing Admin

Can be too general when working with sensitive data

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 13.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 14.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 15.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 16.png>)

* service accounts do need to be managed

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 17.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 18.png>)

* more on cloud identity

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 19.png>)

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

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 20.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 21.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 22.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 23.png>)

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 24.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 25.png>)

A preemptible VM is different from an ordinary Compute Engine VM in only one respect. Compute Engine has permission to terminate a job if its resources are needed elsewhere. Although savings are possible with preemptible VMs, you need to ensure that your job can be stopped and restarted. In terms of storage, Compute Engine doesn't require a particular option or machine type to get high-throughput between processing and persistent disks.

Let's say, you have a workload that doesn't require a human to sit and wait for it to finish, such as a batch job analyzing a large dataset. You can save money, in some cases up to 90 percent by choosing preemptible VMs to run the job

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 26.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 27.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 28.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 29.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 30.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 31.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 32.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 33.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 34.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 35.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 36.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 37.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 38.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 39.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 40.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 41.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 42.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 43.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 44.png>)

* Object versioning

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 45.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 46.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 47.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 48.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 49.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 50.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 51.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 52.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 53.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 54.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 55.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 56.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 57.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 58.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 59.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 60.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 61.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 62.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 63.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 64.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 65.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 66.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 67.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 68.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 69.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 70.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 71.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 72.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 73.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 74.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 75.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 76.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 77.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 78.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 79.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 80.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 81.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 82.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 83.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 84.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 85.png>)

Number of good events / count of all valid events

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 86.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 87.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 88.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 89.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 90.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 91.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 92.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 93.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 94.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 95.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 96.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 97.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 98.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 99.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 100.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 101.png>)

![Untitled](<GCP Core Infrastructure 85a519ee6b6f4393a749a5bd4eee42ce/Untitled 102.png>)
