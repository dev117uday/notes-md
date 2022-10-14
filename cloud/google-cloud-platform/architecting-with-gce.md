# Architecting with GCE

VPC : Virtual Private Cloud

<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>

In Google Cloud each virtual machine can have two IP addresses assigned.&#x20;

* One of them is an internal IP address which is going to be assigned via DHCP internally. Every VM that starts up and any service that depends on virtual machines gets an internal IP address. An example of such services are App Engine and Google Kubernetes Engine which are explored in other courses. When you create a VM in Google Cloud, it's symbolic name is registered with an internal DNS service that translates the name to an internal IP address. The DNS is scoped to the network, so it can translate web URLs and VM names of hosts in the same network. But it can't translate host names of from VMs in a different network.&#x20;
* The other IP address is the external IP address. But this one's optional. You can assign an external IP address if your device or machine is externally facing. That external IP address can be assigned from a pool making it ephemeral or it can be assigned from a reserved external IP address making it static. If you reserve a static external IP address and do not assign it to a resource such as a VM instance or a forwarding rule, you are charged at a higher rate than for static and ephemeral external IP addresses that are in use. You can use your own publicly routable IP address prefixes as Google Cloud external IP addresses and advertise them on the Internet. In order to be eligible, you must own and bring a slash 24 block or large

<figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Every network has:

* Routes that let instances in a network send traffic directly to each other
* A default route that directs packets to destinations that are outside the network

<figure><img src="../../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17) (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (9) (2).png" alt=""><figcaption></figcaption></figure>

