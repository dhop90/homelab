![screenshot_2025-05-09_at_08.45.23.jpg](/Screenshot_2025-05-09_at_08.45.23.jpg)
# HomeLab

#### Table of Contents

- [Purpose](#purpose)
- [netbox](#netbox)
- [NetAlert^x^](#netalertx)
- [Homebox](#homebox)
- [AFFiNE](#affine)
- [Wiki-js](#wiki-js)
- [rancher](#rancher)
- [longhorn](#longhorn)
- [homepage](#homepage)
- [todo](#todo)

---

# Purpose
While following the [r/selfhosted](https://www.reddit.com/r/selfhosted/) sub-reddit, its asked multiple-times, "What do you use to document your homelab?"  This is an attempt to document what I use to document my homelab.  There is no one tool that I use, because there is no one tool with all the features that I need.

Firstly, a little bit of information on my homelab.  I’m running a 24 node K8s cluster using a mix of ARM Raspberry Pi’s and AMD x86 small-form factor computers.  I'm using 3 nodes as control-plane nodes for high availability, utilizing haproxy and keepalived.  The remaining 21 systems are worker nodes.  I've configured both NFS and Longhorn for persistent storage.  Network routing is done by Traefik with DNS overloading, and "Let’s Encrypt" for providing SSL certs.

I use the following tools for documentation:

- [netbox](#netbox)
- [netalertx](#netalertx)
- [homebox](#homebox)
- [affine](#affine)
- [wiki-js](#wiki-js)

And the following tools to manage and enhance the documentation:

- [rancher](#rancher)
- [longhorn](#longhorn)

The dashboard app I use for launching apps is:

- [homepage](#homepage)

# <img src="/netbox.png" width="100" height="100">[netbox](https://netboxlabs.com/oss/netbox/)

Description: 

> Source of Truth for your network
{.is-info}

What is NetBox? 

> NetBox is the source of truth for everything on your network, from physical components like power systems and cabling to virtual assets like IP addresses and VLANs. Network automation and observability tools depend on NetBox’s authoritative data to roll out configurations, monitor changes, and accelerate operations across the enterprise.
{.is-success}

Per device cross links to

> [homebox](#homebox)
> [netalertx](#netalertx)
> [rancher](#rancher)
{.is-warning}

Device (kube0) netbox example with links to homebox, netalertx and rancher:
![netbox-kube0.png](/netbox-kube0.png)

Overview cross links to

> [wiki-js](#wiki-js)
> [affine](#affine)
{.is-warning}

Netbox site example with links to affine and wiki-js:
![netbox-site.png](/netbox-site.png)

How I use NetBox:
> Netbox is my goto app with cross links to all other apps and allows me to document my entire homelab.
{.is-success}


What it does best:
> fine tuned documentation, down to the port/interface level
> describe rack layout
> IP/Mac address assignment
> describe connections between devices
{.is-danger}


# <img src="/netalertx.png" width="100" height="100">[NetAlert^X^](https://jokob-sk.github.io/NetAlertX/)

Description: 

> Network, presence scanner and alert framework
{.is-info}

What is NetAlertX? 

> NetAlertX is a powerful tool designed to simplify the management and monitoring of your network.  Get visibility of what's going on on your WIFI/LAN network and enable presence detection of important devices. Schedule scans for devices, port changes and get alerts if unknown devices or changes are found. Write your own Plugin with auto-generated UI and in-build notification system. Build out and easily maintain your network source of truth (NSoT).
{.is-success}

NetAlertX interface displaying favorite devices.  The Props/Actions column links to netbox entry for device:
![netalertx-favorites.png](/netalertx-favorites.png)

Per device cross links

> [netbox](#netbox)
{.is-warning}

NetAlertX device (kube0) details
![netalertx-kube0.png](/netalertx-kube0.png)

How I use NetAlertX:
> NetAlertX does periodic arp scans and documents the <kbd>actual</kbd> systems on my network.  Given an ip or mac address I can retrive all the documentation I have on the associated device.
>
> NetAlertX also draws a pretty good physical network diagram.
{.is-success}

NetAlertX network diagram
![netalertx-diagram.jpg](/netalertx-diagram.jpg)
Zoomed in section of network diagram
![netalertx-diagram2.jpg](/netalertx-diagram2.jpg)


# <img src="/rancher.png" width="100" height="100">[rancher](https://ranchermanager.docs.rancher.com)
Description:  

> Centralize auth, RBAC and management for all of your Kubernetes clusters everywhere.
{.is-info}

What is Rancher?  

> Rancher is a Kubernetes management tool to deploy and run clusters anywhere and on any provider.  
{.is-success}

> Rancher can provision Kubernetes from a hosted provider, provision compute nodes and then install Kubernetes onto them, or import existing Kubernetes clusters running anywhere.
> 
> Rancher adds significant value on top of Kubernetes, first by centralizing authentication and role-based access control (RBAC) for all of the clusters, giving global admins the ability to control cluster access from one location.
> 
> It then enables detailed monitoring and alerting for clusters and their resources, ships logs to external providers, and integrates directly with Helm via the Application Catalog. If you have an external CI/CD system, you can plug it into Rancher, but if you don't, Rancher even includes Fleet to help you automatically deploy and upgrade workloads.
> 
> Rancher is a complete container management platform for Kubernetes, giving you the tools to successfully run Kubernetes anywhere.
{.is-success}

Rancher interface displaying the current pods (services) running on this node (kube0)
![rancher-kube0.jpg](/rancher-kube0.jpg)

Per device cross links

> None
{.is-warning}

How I use Rancher:
> Rancher is the tool I use to manager my k8s cluster, from provisioning to altering pods.  From netbox, I link to the individual nodes that allow my to see which pods (services) are running on that node.  There are no cross links to the other documentation apps.
{.is-success}


# <img src="/homebox.png" width="100" height="100">[homebox](https://homebox.software/en/)
Description: 
> Home inventory management software
{.is-info}


What is HomeBox?  

> Homebox is the inventory and organization system built for the Home User! With a focus on simplicity and ease of use, Homebox is the perfect solution for your home inventory, organization, and management needs. 
{.is-success}

Development principles:

> Simple - Homebox is designed to be simple and easy to use. No complicated setup or configuration required. Use either a single docker container, or deploy yourself by compiling the binary for your platform of choice.
> 
> Blazingly Fast - Homebox is written in Go, which makes it extremely fast and requires minimal resources to deploy. In general idle memory usage is less than 50MB for the whole container.
> 
> Portable - Homebox is designed to be portable and run on anywhere. We use SQLite and an embedded Web UI to make it easy to deploy, use, and backup. However, a Postgres backend is also supported for larger installations. 
{.is-success}

Per device cross link

> [netbox](#netbox)
{.is-warning}

Homebox interface with link to netbox
![homebox-kube0.png](/homebox-kube0.png)


How I use HomeBox:
> I use HomeBox to not only inventory my homelab, but all other items in my house, such as electronics and furniture with price tags.
{.is-success}

# <img src="/wiki-js.png" width="100" height="100">[Wiki-js](https://js.wiki/)
Description:  

> Powerful and extensible open source Wiki software platform
{.is-info}

What is Wiki-js?

> Wiki.js is a powerful, extensible, and free open-source wiki software built on Node.js and written in JavaScript. It allows users to collaborate and create structured information using a web browser, similar to how Wikipedia operates. Wiki.js offers features like multiple editors (Markdown, WYSIWYG, HTML), version tracking, multilingual support, and integration with external storage services. 
{.is-success}

Cross Links - Per device
> None
{.is-warning}

How I use wiki-js:
> I use wiki-js to document the high-level architecture of my homelab.  Specifically I use [plantuml](https://plantuml.com/) to describe my homelab connectivity and it builds the network topology for me.
{.is-success}

> <kbd>PlantUML</kbd> is an open-source tool that lets you create diagrams by writing simple, human-readable text descriptions. This allows you to create various types of diagrams, including UML diagrams like sequence, use case, and class diagrams, as well as non-UML diagrams like network diagrams, mind maps, and more. Instead of manually drawing diagrams, you describe them using a special syntax, and PlantUML then renders the diagram into a visual representation.
{.is-danger}


Example plantuml diagram in wiki-js
![wikijs.png](/wikijs.png)

# <img src="/affine-light.png" width="100" height="100"> [AFFiNE](https://affine.pro/)
Description:

> Next-gen knowledge base that brings planning, sorting, and creating all together
{.is-info}

What is affine?

> AFFiNE is a workspace with fully merged docs, whiteboards and databases.
Get more things done, your creativity isn’t monotone.  Write, Draw, Plan all at Once with AI.
{.is-success}

Cross Links
> None
{.is-warning}

affine example
![affine.jpg](/affine.jpg)

How I use wiki-js:
> I use affine to document the high-level architecture of my homelab.
{.is-success}

# <img src="/rancher-longhorn.png" width="100" height="100">[longhorn](https://longhorn.io/)

Description: 

> Cloud native distributed block storage for Kubernetes
{.is-info}

What is longhorn?  

> Longhorn is a lightweight, reliable and easy-to-use distributed block storage system for Kubernetes.
>
> Longhorn is free, open source software. Originally developed by Rancher Labs, it is now being developed as a incubating project of the Cloud Native Computing Foundation.
{.is-success}

With Longhorn, you can:
> Use Longhorn volumes as persistent storage for the distributed stateful applications in your Kubernetes cluster
>  
> Partition your block storage into Longhorn volumes so that you can use Kubernetes volumes with or without a cloud provider
>  
> Replicate block storage across multiple nodes and data centers to increase availability
>  
> Store backup data in external storage such as NFS or AWS S3
>  
> Create cross-cluster disaster recovery volumes so that data from a primary Kubernetes cluster can be quickly recovered from backup in a second Kubernetes cluster
>  
> Schedule recurring snapshots of a volume, and schedule recurring backups to NFS or S3-compatible secondary storage
>  
> Restore volumes from backup
>
> Upgrade Longhorn without disrupting persistent volumes
  Longhorn comes with a standalone UI, and can be installed using Helm, kubectl, or the Rancher app catalog.
{.is-success}

longhorn Dashboard
![longhorn.jpg](/longhorn.jpg)
Cross Links - Per device
> None
{.is-warning}

How I use longhorn
> I use longhorn to view current persistent volumes used by the cluster.
{.is-success}

# <img src="/homepage.png" width="100" height="100">[homepage](https://gethomepage.dev/)
Description:

> Homelab dashboard
{.is-info}

What is homepage?

> A modern, fully static, fast, secure fully proxied, highly customizable application dashboard with integrations for over 100 services and translations into multiple languages. Easily configured via YAML files or through docker label discovery.
{.is-success}

Cross Links
> Links to all apps
{.is-warning}

homepage example
![homepage.jpg](/homepage.jpg)

How I use homepage:
> I use homepage as my dashboard to launch apps and view stats.
{.is-success}

# :bulb: ToDo
- document backup/restore
	- database backup
  		- postgresql
    	- pgbackweb
  - longhorn backup
  - nfs storage backup
  - k8s manifest backup
