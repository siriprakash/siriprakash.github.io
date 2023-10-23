---
title: GCP PCN STUDY RESOURCES
date: 2023-10-23
categories: [GCP]
tags: [studyresources]     
---
### **Section 1: Designing, planning, and prototyping a Google Cloud network**

**1.1 Designing an overall network architecture. Considerations include:**

●  High availability, failover, and disaster recovery strategies

●  DNS strategy (e.g., on-premises, Cloud DNS)

https://cloud.google.com/dns/docs/overview

https://cloud.google.com/dns/docs/zones/zones-overview

●  Security and data exfiltration requirements

●  Load balancing

●  Applying quotas per project and per VPC

●  Hybrid connectivity (e.g., Google private access for hybrid connectivity)

●  Container networking

●  IAM roles

●  SaaS, PaaS, and IaaS services

●  Microsegmentation for security purposes (e.g., using metadata, tags, service accounts)

**1.2 Designing Virtual Private Cloud (VPC) instances. Considerations include:**

●  IP address management and bring your own IP (BYOIP)

●  Standalone vs. Shared VPC

●  Multiple vs. single

●  Regional vs. multi-regional

●  VPC Network Peering

●  Firewalls (e.g., service account-based, tag-based)

●  Custom routes

●  Using managed services (e.g., Cloud SQL, Memorystore)

●  Third-party device insertion (NGFW) into VPC using multi-NIC and internal load balancer as a next hop or equal-cost multi-path (ECMP) routes

**1.3 Designing a hybrid and multi-cloud network. Considerations include:**

●  Dedicated Interconnect vs. Partner Interconnect

●  Multi-cloud connectivity

●  Direct Peering

●  IPsec VPN

●  Failover and disaster recovery strategy

●  Regional vs. global VPC routing mode

●  Accessing multiple VPCs from on-premises locations (e.g., Shared VPC, multi-VPC peering topologies)

●  Bandwidth and constraints provided by hybrid connectivity solutions

●  Accessing Google Services/APIs privately from on-premises locations

●  IP address management across on-premises locations and cloud

●  DNS peering and forwarding

**1.4 Designing an IP addressing plan for Google Kubernetes Engine. Considerations include:**

●  Public and private cluster nodes

●  Control plane public vs. private endpoints

●  Subnets and alias IPs

●  RFC 1918, non-RFC 1918, and privately used public IP (PUPI) address options

### **Section 2: Implementing Virtual Private Cloud (VPC) instances**

**2.1 Configuring VPCs. Considerations include:**

●  Google Cloud VPC resources (e.g., networks, subnets, firewall rules)

●  VPC Network Peering

●  Creating a Shared VPC network and sharing subnets with other projects

●  Configuring API access to Google services (e.g., Private Google Access, public interfaces)

●  Expanding VPC subnet ranges after creation

**2.2 Configuring routing. Considerations include:**

●  Static vs. dynamic routing

●  Global vs. regional dynamic routing

●  Routing policies using tags and priority

●  Internal load balancer as a next hop

●  Custom route import/export over VPC Network Peering

**2.3 Configuring and maintaining Google Kubernetes Engine clusters. Considerations include:**

●  VPC-native clusters using alias IPs

●  Clusters with Shared VPC

●  Creating Kubernetes Network Policies

●  Private clusters and private control plane endpoints

●  Adding authorized networks for cluster control plane endpoints

**2.4 Configuring and managing firewall rules. Considerations include:**

●  Target network tags and service accounts

●  Rule priority

●  Network protocols

●  Ingress and egress rules

●  Firewall rule logging

●  Firewall Insights

●  Hierarchical firewalls

**2.5 Implementing VPC Service Controls. Considerations include:**

●  Creating and configuring access levels and service perimeters

●  VPC accessible services

●  Perimeter bridges

●  Audit logging

●  Dry run mode

### **Section 3: Configuring network services**

**3.1 Configuring load balancing. Considerations include:**

●  Backend services and network endpoint groups (NEGs)

●  Firewall rules to allow traffic and health checks to backend services

●  Health checks for backend services and target instance groups

●  Configuring backends and backend services with balancing method (e.g., RPS, CPU, Custom), session affinity, and capacity scaling/scaler

●  TCP and SSL proxy load balancers

●  Load balancers (e.g., External TCP/UDP Network Load Balancing, Internal TCP/UDP Load Balancing, External HTTP(S) Load Balancing, Internal HTTP(S) Load Balancing)

●  Protocol forwarding

●  Accommodating workload increases using autoscaling vs. manual scaling

**3.2 Configuring Google Cloud Armor policies. Considerations include:**

●  Security policies

●  Web application firewall (WAF) rules (e.g., SQL injection, cross-site scripting, remote file inclusion)

●  Attaching security policies to load balancer backends

**3.3 Configuring Cloud CDN. Considerations include:**

●  Enabling and disabling

●  Cloud CDN

●  Cache keysInvalidating cached objects

●  Signed URLs

●  Custom origins

**3.4 Configuring and maintaining Cloud DNS. Considerations include:**

●  Managing zones and records

●  Migrating to Cloud DNS

●  DNS Security Extensions (DNSSEC)

●  Forwarding and DNS server policies

●  Integrating on-premises DNS with Google Cloud

●  Split-horizon DNS

●  DNS peering

●  Private DNS logging

**3.5 Configuring Cloud NAT. Considerations include:**

●  Addressing

●  Port allocations

●  Customizing timeouts

●  Logging and monitoring

●  Restrictions per organization policy constraints

**3.6  Configuring network packet inspection. Considerations include:**

●  Packet Mirroring in single and multi-VPC topologies

●  Capturing relevant traffic using Packet Mirroring source and traffic filters

●  Routing and inspecting inter-VPC traffic using multi-NIC VMs (e.g., next-generation firewall appliances)

●  Configuring an internal load balancer as a next hop for highly available multi-NIC VM routing

### **Section 4: Implementing hybrid interconnectivity**

**4.1 Configuring Cloud Interconnect. Considerations include:**

●  Dedicated Interconnect connections and VLAN attachments

●  Partner Interconnect connections and VLAN attachments

**4.2 Configuring a site-to-site IPsec VPN. Considerations include:**

●  High availability VPN (dynamic routing)

●  Classic VPN (e.g., route-based routing, policy-based routing)

**4.3 Configuring Cloud Router. Considerations include:**

●  Border Gateway Protocol (BGP) attributes (e.g., ASN, route priority/MED, link-local addresses)

●  Custom route advertisements via BGP

●  Deploying reliable and redundant Cloud Routers

### **Section 5: Managing, monitoring, and optimizing network operations**

**5.1 Logging and monitoring with Google Cloud’s operations suite. Considerations include:**

●  Reviewing logs for networking components (e.g., VPN, Cloud Router, VPC Service Controls)

●  Monitoring networking components (e.g., VPN, Cloud Interconnect connections and interconnect attachments, Cloud Router, load balancers, Google Cloud Armor, Cloud NAT)

**5.2 Managing and maintaining security. Considerations include:**

●  Firewalls (e.g., cloud-based, private)

●  Diagnosing and resolving IAM issues (e.g., Shared VPC, security/network admin)

**5.3 Maintaining and troubleshooting connectivity issues. Considerations include:**

●  Draining and redirecting traffic flows with HTTP(S) Load Balancing

●  Monitoring ingress and egress traffic using VPC Flow Logs

●  Monitoring firewall logs and Firewall Insights

●  Managing and troubleshooting VPNs

●  Troubleshooting Cloud Router BGP peering issues

**5.4 Monitoring, maintaining, and troubleshooting latency and traffic flow. Considerations include:**

●  Testing network throughput and latency

●  Diagnosing routing issues

●  Using Network Intelligence Center to visualize topology, test connectivity, and monitor performance
