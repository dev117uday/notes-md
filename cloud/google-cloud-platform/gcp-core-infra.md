# GCP Core Infrastructure

## Why Core Infrastructure

- Identify the purpose and value of Google Cloud
- Choose best deployment environment
- Choose storage options
- Interact and experience google cloud

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%201.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%202.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%203.png)

- IaaS : Pay for what they allocate
- PaaS : Pay for what they use

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%204.png)

Nine of Google's nine products have more than one billion users each. Google designs and builds its own data centers, which incorporate multiple layers of physical security protections. Access to these datacenters is limited to only a very small number of Google employees. Security features include encryption using centrally managed keys and hardware encryption in hard drives and SSDs. The GFE additionally applies protections against denial-of-service attacks. Google also has multi-tier, multi-layer DoS protections that further reduce the risk of any DoS impact on a service running behind the GFE.

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%205.png)

Specifically, when you run an instance for more than 25% of a month, Compute Engine automatically gives you a discount for every incremental minute you use for that instance. Custom virtual machine types allow Compute Engine virtual machines to be fine tuned with optimal amounts of vCPU and memory for the applications so that you can tailor your pricing for your workloads.

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%206.png)

- folder can contain sub folders
- policies are applied at project, folder and org node level
    - some can be applied at resource level
    - policies are inherited downwards

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%207.png)

Attributes of project

- project_id
- project_name
- project_number

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%208.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%209.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2010.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2011.png)

who can do what and on which part

- who can be :
    - a google account
    - a google group
    - service account
    - cloud identity domain
- can do what
    - defined by a role
    

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2012.png)

**Basic role** 

- Owner
- Editor
- Viewer
- Billing Admin

Can be too general when working with sensitive data

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2013.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2014.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2015.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2016.png)

- service accounts do need to be managed

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2017.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2018.png)

- more on cloud identity

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2019.png)

## Quiz

Q1 : When would you choose to have an organization node? (Select two)

- When you want to create folders
- When you want to centrally apply organization-wide policies

Q2 : Which statement best describes how Google Cloud resources are associated within the resource hierarchy?

- Google Cloud resources are not associated with the resource hierarchy.

Q3 : Consider a single hierarchy of Google Cloud resources. Which of these situations is possible? (Choose 3 responses.)

- There is no organization node, and there are no folders.
- There is an organization node, and there is at least one folder.

Your company has two Google Cloud projects and you want them to share policies. What is the least error-prone way to set this up?

- Define the new shared policy in the organization node.

Q5 : What is the difference between Identity and Access Management (IAM) basic roles and IAM predefined roles?

- Basic roles can only be granted to single users. Predefined roles can be associated with a group.

Q6 : Select the option that displays IAM roles from general to specific.

- Predefined roles, custom roles, basic roles

Q7 : How does the resource hierarchy control how IAM policies are inherited?

- IAM policies are only implemented at the project level; they cannot be amended by lower levels of the resource hierarchy.

Q8 : Which way of accessing Google Cloud lets you control services through the code you write?

- APIs

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2020.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2021.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2022.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2023.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2024.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2025.png)

A preemptible VM is different from an ordinary Compute Engine VM in only one respect. Compute Engine has permission to terminate a job if its resources are needed elsewhere. Although savings are possible with preemptible VMs, you need to ensure that your job can be stopped and restarted. In terms of storage, Compute Engine doesn't require a particular option or machine type to get high-throughput between processing and persistent disks.

Let's say, you have a workload that doesn't require a human to sit and wait for it to finish, such as a batch job analyzing a large dataset. You can save money, in some cases up to 90 percent by choosing preemptible VMs to run the job

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2026.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2027.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2028.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2029.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2030.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2031.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2032.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2033.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2034.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2035.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2036.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2037.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2038.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2039.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2040.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2041.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2042.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2043.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2044.png)

- Object versioning

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2045.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2046.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2047.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2048.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2049.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2050.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2051.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2052.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2053.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2054.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2055.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2056.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2057.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2058.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2059.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2060.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2061.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2062.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2063.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2064.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2065.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2066.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2067.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2068.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2069.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2070.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2071.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2072.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2073.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2074.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2075.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2076.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2077.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2078.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2079.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2080.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2081.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2082.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2083.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2084.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2085.png)

Number of good events / count of all valid events

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2086.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2087.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2088.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2089.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2090.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2091.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2092.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2093.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2094.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2095.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2096.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2097.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2098.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%2099.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%20100.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%20101.png)

![Untitled](GCP%20Core%20Infrastructure%2085a519ee6b6f4393a749a5bd4eee42ce/Untitled%20102.png)