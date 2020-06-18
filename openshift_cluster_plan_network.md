---

copyright:
  years: 2014, 2020
lastupdated: "2020-06-16"

keywords: openshift, rhoks, roks, rhos, multi az, multi-az, szr, mzr

subcollection: openshift

---

{:beta: .beta}
{:codeblock: .codeblock}
{:deprecated: .deprecated}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:gif: data-image-type='gif'}
{:help: data-hd-content-type='help'}
{:important: .important}
{:new_window: target="_blank"}
{:note: .note}
{:pre: .pre}
{:preview: .preview}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:support: data-reuse='support'}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}



# Planning your cluster network setup   
{: #plan_clusters}

Design a network setup for your {{site.data.keyword.openshiftlong}} cluster that meets the needs of your workloads and environment.
{: shortdesc}

Get started by planning your setup for a VPC or a classic cluster.
* With [Red Hat OpenShift on IBM Cloud clusters in VPC](#plan_vpc_basics), you can create your cluster in the next generation of the {{site.data.keyword.cloud_notm}} platform, in [Virtual Private Cloud](/docs/vpc?topic=vpc-about-vpc) for Generation 2 compute resources. VPC gives you the security of a private cloud environment with the dynamic scalability of a public cloud.
* With [Red Hat OpenShift on IBM Cloud classic clusters](#plan_basics), you can create your cluster on classic infrastructure. Classic clusters include all of the Red Hat OpenShift on IBM Cloud mature and robust features for compute, networking, and storage.

First time creating a cluster? First, try out the [tutorial for creating OpenShift clusters](/docs/openshift?topic=openshift-openshift_tutorial). Then, come back here when you’re ready to plan out your production-ready clusters.
{: tip}


## Understanding network basics of VPC clusters
{: #plan_vpc_basics}

When you create your cluster, you must choose a networking setup so that certain cluster components can communicate with each other and with networks or services outside of the cluster.
{: shortdesc}

* [Worker-to-worker communication](#vpc-worker-worker): All worker nodes must be able to communicate with each other on the private network through VPC subnets.
* [Worker-to-master and user-to-master communication](#vpc-workeruser-master): Your worker nodes and your authorized cluster users can communicate with the Kubernetes master securely over the private network through a private service endpoint, or the public network with TLS through a public service endpoint.
* [Worker communication to other services or networks](#vpc-worker-services-onprem): Allow your worker nodes to securely communicate with other {{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.registrylong}}, to on-premises networks, to other VPCs, or to classic infrastructure resources.
* [External communication to apps that run on worker nodes](#vpc-external-workers): Allow public or private requests into the cluster as well as requests out of the cluster to a public endpoint.
</br>

### Worker-to-worker communication: VPC subnets
{: #vpc-worker-worker}

Before you create a VPC cluster for the first time, you must [create a VPC subnet](https://cloud.ibm.com/vpc/provision/network){: external} in each zone where you want to deploy worker nodes. A VPC subnet is a specified private IP address range (CIDR block) and configures a group of worker nodes and pods as if they are attached to the same physical wire.
{: shortdesc}

When you create a cluster, you specify an existing VPC subnet for each zone. Each worker node that you add in a cluster is deployed with a private IP address from the VPC subnet in that zone. After the worker node is provisioned, the worker node IP address persists after a `reboot` operation, but the worker node IP address changes after `replace` and `update` operations.

Subnets provide a channel for connectivity among the worker nodes within the cluster. Additionally, any system that is connected to any of the private subnets in the same VPC can communicate with workers. For example, all subnets in one VPC can communicate through private layer 3 routing with a built-in VPC router. If you have multiple clusters that must communicate with each other, you can create the clusters in the same VPC. However, if your clusters do not need to communicate, you can achieve better network segmentation by creating the clusters in separate VPCs. You can also create [access control lists (ACLs)](/docs/openshift?topic=openshift-vpc-network-policy#acls) for your VPC subnets to mediate traffic on the private network. ACLs consist of inbound and outbound rules that define which ingress and egress is permitted for each VPC subnet.

To run default OpenShift components such as the web console or OperatorHub, you must attach a public gateway to one or more subnets that the worker nodes are deployed to.

The default IP address range for VPC subnets is 10.0.0.0 – 10.255.255.255. For a list of IP address ranges per VPC zone, see the [VPC default address prefixes](/docs/vpc?topic=vpc-configuring-address-prefixes). If you enable your VPC with classic access, or access to classic infrastructure resources, the default IP ranges per VPC zone are different. For more information, see [Classic access VPC default address prefixes](/docs/vpc?topic=vpc-setting-up-access-to-classic-infrastructure#classic-access-default-address-prefixes).

Need to create your cluster by using custom-range subnets? Check out this guidance on [custom address prefixes](/docs/vpc?topic=vpc-configuring-address-prefixes). If you use custom-range subnets for your worker nodes, you must [ensure that your worker node subnets do not overlap with your cluster's pod subnet](/docs/openshift?topic=openshift-vpc-subnets#vpc-ip-range).
{: tip}

Do not delete the subnets that you attach to your cluster during cluster creation or when you add worker nodes in a zone. If you delete a VPC subnet that your cluster used, any load balancers that use IP addresses from the subnet might experience issues, and you might be unable to create new load balancers.
{: important}

When you create VPC subnets for your clusters, keep in mind the following features and limitations. For more information about VPC subnets, see [Characteristics of subnets in the VPC](/docs/vpc?topic=vpc-about-networking-for-vpc#subnets-in-the-vpc).
* The default CIDR size of each VPC subnet is `/24`, which can support up to 253 worker nodes. If you plan to deploy more than 250 worker nodes per zone in one cluster, consider creating a subnet of a larger size.
* After you create a VPC subnet, you cannot resize it or change its IP range.
* Multiple clusters in the same VPC can share subnets.
* VPC subnets are bound to a single zone and cannot span multiple zones or regions.
* After you create a subnet, you cannot move it to a different zone, region, or VPC.
* If you have worker nodes that are attached to an existing subnet in a zone, you cannot change the subnet for that zone in the cluster.
* The `172.16.0.0/16`, `172.18.0.0/16`, `172.19.0.0/16`, and `172.20.0.0/16` ranges are prohibited.

</br>

### Worker-to-master and user-to-master communication: Service endpoints
{: #vpc-workeruser-master}

A communication channel must be set up so that worker nodes and authorized cluster users can establish a connection to the Kubernetes master. You can allow communication to the Kubernetes master by enabling the public and private service endpoints or the private service endpoint only. Note that using private service endpoint only incurs no billed or metered bandwidth charges.
{: shortdesc}

To secure communication over public and private service endpoints, Red Hat OpenShift on IBM Cloud automatically sets up an OpenVPN connection between the Kubernetes master and the worker node when the cluster is created. Workers securely talk to the master through TLS certificates, and the master talks to workers through the OpenVPN connection. Note that you must enable your account to use service endpoints. To enable service endpoints, run `ibmcloud account update --service-endpoint-enable true`.

In VPC clusters in Red Hat OpenShift on IBM Cloud, you cannot disable the private service endpoint or set up a cluster with the public service endpoint only.
{: note}

**Public and private service endpoints**</br>
* Communication between worker nodes and master is established over the private network through the private service endpoint only.
* By default, all calls to the master that are initiated by authorized cluster users are routed through the public service endpoint. If authorized cluster users are in your VPC network or are connected through a [VPC VPN connection](/docs/openshift?topic=openshift-vpc-vpnaas), the master is privately accessible through the private service endpoint.

**Private service endpoint only**</br>
* Communication between worker nodes and master is established over the private network through the private service endpoint.
* To access the master through the private service endpoint, authorized cluster users must either be in your VPC network or are connected through a [VPC VPN connection](/docs/openshift?topic=openshift-vpc-vpnaas).

Your VPC cluster is created with both a public and a private service endpoint by default. To create a VPC cluster with only a private service endpoint, create the cluster [in the CLI](/docs/openshift?topic=openshift-clusters#cluster_vpcg2_cli) and include the `--disable-public-service-endpoint` flag. If you include this flag, your cluster is created with routers and Ingress controllers that expose your apps on the private network only by default. If you later want to expose apps to a public network, you must manually create public routers and Ingress controllers.
{: note}

</br>

### Worker communication to other services or networks
{: #vpc-worker-services-onprem}

Allow your worker nodes to securely communicate with other {{site.data.keyword.cloud_notm}} services, on-premises networks, other VPCs, and {{site.data.keyword.cloud_notm}} classic infrastructure resources.
{: shortdesc}

**Communication with other {{site.data.keyword.cloud_notm}} services over the private or public network**</br>
Your worker nodes can automatically and securely communicate with other [{{site.data.keyword.cloud_notm}} services that support private service endpoints](/docs/resources?topic=resources-private-network-endpoints), such as {{site.data.keyword.registrylong}}, over the private network. If an {{site.data.keyword.cloud_notm}} service does not support private service endpoints, worker nodes can securely communicate with the services over the public network through the subnet's public gateway.

Note that if you use [access control lists (ACLs)](/docs/openshift?topic=openshift-vpc-network-policy#acls) for your VPC subnets, you must create inbound or outbound rules to allow your worker nodes to communicate with these services.

**Communication with resources in on-premises data centers**</br>
With the {{site.data.keyword.vpc_short}} VPN, you connect an entire VPC to an on-premises data center. You can also use the {{site.data.keyword.vpc_short}} VPN to connect two VPCs so that your cluster can access resources in the network of another VPC in your account. To get started, you must create a VPC gateway for your subnets. For more information, see [Using VPN with your VPC](/docs/openshift?topic=openshift-vpc-vpnaas).

<p class="tip">If you plan to connect your cluster to on-premises networks, check out the following helpful features:<ul><li>You might have subnet conflicts with the IBM-provided default 172.30.0.0/16 range for pods and 172.21.0.0/16 range for services. You can avoid subnet conflicts when you [create a cluster from the CLI](/docs/openshift?topic=openshift-kubernetes-service-cli#cli_cluster-create-vpc-classic) by specifying a custom subnet CIDR for pods in the `--pod-subnet` flag and a custom subnet CIDR for services in the `--service-subnet` flag.</li><li>If your VPN solution preserves the source IP addresses of requests, you can [create custom static routes](/docs/openshift?topic=openshift-static-routes) to ensure that your worker nodes can route responses from your cluster back to your on-premises network.</li></p>

**Communication with resources in other VPCs**</br>
To connect an entire VPC to another VPC in your account, you can use the {{site.data.keyword.vpc_short}} VPN. For example, you can use the {{site.data.keyword.vpc_short}} VPN to connect subnets in a VPC in one region to subnets in a VPC in another region. To get started by creating a VPC gateway for your subnets, see [Using VPN with your VPC](/docs/openshift?topic=openshift-vpc-vpnaas). Note that if you use [access control lists (ACLs)](/docs/openshift?topic=openshift-vpc-network-policy#acls) for your VPC subnets, you must create inbound or outbound rules to allow your worker nodes to communicate with the subnets in other VPCs.

**Communication with {{site.data.keyword.cloud_notm}} classic resources**</br>
If you need to connect your cluster to resources in your {{site.data.keyword.cloud_notm}} classic infrastructure, you can set up access between one VPC in each region to one {{site.data.keyword.cloud_notm}} classic infrastructure account. You must enable the VPC for classic access when you create the VPC, and you cannot convert an existing VPC to use classic access. To get started, see [Setting up access to classic infrastructure](/docs/vpc?topic=vpc-setting-up-access-to-classic-infrastructure).

When you create a VPC with classic infrastructure access, you can set up an [{{site.data.keyword.cloud_notm}} Direct Link](/docs/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link) connection between your classic infrastructure and your remote networks. Any clusters that you create in the VPC with classic infrastructure access can access the Direct Link connection.

</br>

### External communication to apps that run on worker nodes
{: #vpc-external-workers}

Allow private or public traffic requests from outside the cluster to your apps that run on worker nodes.
{: shortdesc}

**Private traffic to cluster apps**</br>
When you deploy an app in your cluster, you might want to make the app accessible to only users and services that are on the same private network as your cluster. Private load balancing is ideal for making your app available to requests from outside the cluster without exposing the app to the general public. You can also use private load balancing to test access, request routing, and other configurations for your app before you later expose your app to the public with public network services.

To allow private network traffic requests from outside the cluster to your apps, you can use private Kubernetes networking services, such as creating [`LoadBalancer` services](/docs/openshift?topic=openshift-vpc-lbaas). For example, when you create a Kubernetes `LoadBalancer` service in your cluster, a load balancer for VPC is automatically created in your VPC outside of your cluster. The VPC load balancer is multizonal and routes requests for your app through the private NodePorts that are automatically opened on your worker nodes. You can then create access control lists (ACLs) for your VPC subnets to allow inbound network traffic requests from specified sources.

For more information, see [Planning private external load balancing](/docs/openshift?topic=openshift-cs_network_planning#private_access).

**Public traffic to cluster apps**</br>
To make your apps accessible from the public internet, you can use public networking services. Even though your worker nodes are connected to private VPC subnets only, the VPC load balancer that is created for public networking services can route public requests to your app on the private network by providing your app a public URL. When an app is publicly exposed, anyone that has the public URL can send a request to your app.

You can use public Kubernetes networking services, such as creating [`LoadBalancer` services](/docs/openshift?topic=openshift-vpc-lbaas). For example, when you create a Kubernetes `LoadBalancer` service in your cluster, a load balancer for VPC is automatically created in your VPC outside of your cluster. The VPC load balancer is multizonal and routes requests for your app through the private NodePorts that are automatically opened on your worker nodes. You can then create access control lists (ACLs) for your VPC subnets to allow inbound network traffic requests from specified sources.

<br />


## Example scenarios for VPC cluster network setups
{: #vpc-scenarios}

Now that you understand the basics of cluster networking, check out some example scenarios in which various VPC cluster network setups can meet your workload needs.
{: shortdesc}

### Scenario: Run internet-facing app workloads in a VPC cluster
{: #vpc-no-pgw}

In this scenario, you run workloads in a VPC cluster that are accessible to requests from the Internet. Public access is controlled by ACLs so that end users can access your apps while unwanted public requests to your apps are denied. Additionally, your workers have automatic access to any {{site.data.keyword.cloud_notm}} services that support private service endpoints.
{: shortdesc}

<p>
<figure>
 <img src="images/roks_ov_vpc_pub.png" width="850" style="width:850px; border-style: none" alt="Network setup for a VPC cluster that runs internet-facing app workloads"/>
 <figcaption>Network setup for a VPC cluster that runs internet-facing app workloads</figcaption>
</figure>
</p>

**Worker-to-worker communication**

To achieve this setup, you create VPC subnets in each zone where you want to deploy worker nodes. To run default OpenShift components such as the web console or OperatorHub, public gateways are required for these subnets. Then, you create a VPC cluster that uses these VPC subnets.

**Worker-to-master and user-to-master communication**

You can choose to allow worker-to-master and user-to-master communication over the public and private networks, or over the private network only.
* Public and private service endpoints: Communication between worker nodes and master is established over the private network through the private service endpoint. By default, all calls to the master that are initiated by authorized cluster users are routed through the public service endpoint.
* Private service endpoint only: Communication to master from both worker nodes and cluster users is established over the private network through the private service endpoint. Cluster users must either be in your VPC network or connect through a [VPC VPN connection](/docs/openshift?topic=openshift-vpc-vpnaas).

**Worker communication to other services or networks**

If your app workload requires other {{site.data.keyword.cloud_notm}} services, your worker nodes can automatically, securely communicate with {{site.data.keyword.cloud_notm}} services that support private service endpoints over the private VPC network.

**External communication to apps that run on worker nodes**

After you test your app, you can expose it to the internet by creating a public Kubernetes `LoadBalancer` service or using the default public Ingress application load balancers (ALBs). The VPC load balancer that is automatically created in your VPC outside of your cluster when you use one of these services routes traffic to your app. You can improve the security of your cluster and control public network traffic to your apps by creating access control lists (ACLs). ACLs consist of rules that define which inbound traffic is permitted for the VPC subnets that your worker nodes are connected to.

Ready to get started with a cluster for this scenario? After you plan your [high availability](/docs/openshift?topic=openshift-ha_clusters) and [worker node](/docs/openshift?topic=openshift-planning_worker_nodes) setups, see [Creating VPC Gen 2 compute clusters](/docs/openshift?topic=openshift-clusters).

<br />



### Scenario: Extend your on-premises data center to a VPC cluster
{: #vpc-vpn}

In this scenario, you run workloads in a VPC cluster. However, you want these workloads to be accessible only to services, databases, or other resources in your private networks in an on-premises data center. Your cluster workloads might need to access a few other {{site.data.keyword.cloud_notm}} services that support communication over the private network.
{: shortdesc}

<p>
<figure>
 <img src="images/roks_ov_vpc_priv.png" width="850" style="width:850px; border-style: none" alt="Network setup for a VPC cluster that extends an on-prem data center"/>
 <figcaption>Network setup for a VPC cluster that extends an on-prem data center</figcaption>
</figure>
</p>

**Worker-to-worker communication**

To achieve this setup, you create VPC subnets in each zone where you want to deploy worker nodes. To run default OpenShift components such as the web console or OperatorHub, public gateways are required for these subnets.. Then, you create a VPC cluster that uses these VPC subnets.

Note that you might have subnet conflicts between the default ranges for workers nodes, pods, and services, and the subnets in your on-premises networks. When you create your VPC subnets, you can choose [custom address prefixes](/docs/vpc?topic=vpc-configuring-address-prefixes) and the create your cluster by using these subnets. Additionally, you can specify a custom subnet CIDR for pods and services by using the `--pod-subnet` and `--service-subnet` flags in the `ibmcloud oc cluster create` command when you create your cluster.

**Worker-to-master and user-to-master communication**

When you create the cluster, you enable private service endpoint only to allow worker-to-master and user-to-master communication over the private network. Cluster users must either be in your VPC network or connect through a [VPC VPN connection](/docs/openshift?topic=openshift-vpc-vpnaas).

**Worker communication to other services or networks**

To connect your cluster with your on-premises data center, you can set up the VPC VPN service. The {{site.data.keyword.vpc_short}} VPN connects your entire VPC to an on-premises data center. If your app workload requires other {{site.data.keyword.cloud_notm}} services that support private service endpoints, your worker nodes can automatically, securely communicate with these services over the private VPC network.

**External communication to apps that run on worker nodes**

After you test your app, you can expose it to the private network by creating a private Kubernetes `LoadBalancer` service or using the default private Ingress application load balancers (ALBs). The VPC load balancer that is automatically created in your VPC outside of your cluster when you use one of these services routes traffic to your app. Note that the VPC load balancer exposes your app to the private network only so that any on-premises system with a connection to the VPC subnet can access the app. You can improve the security of your cluster and control public traffic apps by creating access control lists (ACLs). ACLs consist of rules that define which inbound traffic is permitted for the VPC subnets that your worker nodes are connected to.

Ready to get started with a cluster for this scenario? After you plan your [high availability](/docs/openshift?topic=openshift-ha_clusters) and [worker node](/docs/openshift?topic=openshift-planning_worker_nodes) setups, see [Creating VPC Gen 2 compute clusters](/docs/openshift?topic=openshift-clusters).

<br />


## Understanding network basics of classic clusters
{: #plan_basics}

When you create a classic cluster, you must choose a networking setup so that certain cluster components can communicate with each other and with networks or services outside of the cluster.
{: shortdesc}

* [Worker-to-worker communication](#worker-worker): All worker nodes must be able to communicate with each other on the private network. In many cases, communication must be permitted across multiple private VLANs to allow workers on different VLANs and in different zones to connect with each other.
* [Worker-to-master and user-to-master communication](#workeruser-master): Your worker nodes and your authorized cluster users can communicate with the Kubernetes master securely over the public network with TLS or over the private network through private service endpoints.
* [Worker communication to other {{site.data.keyword.cloud_notm}} services or on-premises networks](#worker-services-onprem): Allow your worker nodes to securely communicate with other {{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.registrylong}}, and to an on-premises network.
* [External communication to apps that run on worker nodes](#external-workers): Allow public or private requests into the cluster as well as requests out of the cluster to a public endpoint.

### Worker-to-worker communication: classic VLANs and subnets
{: #worker-worker}

When you create a classic cluster, the cluster's worker nodes are connected automatically to a private VLAN and a public VLAN. A VLAN configures a group of worker nodes and pods as if they were attached to the same physical wire and provides a channel for connectivity among the workers.
{: shortdesc}

**VLAN connections for worker nodes**</br>
All worker nodes must be connected to a private VLAN so that each worker node can send information to and receive information from other worker nodes. The private VLAN provides private subnets that are used to assign private IP addresses to your worker nodes and private app services. Your worker nodes also must be connected to a public VLAN. </openshift-priv-lim>The public VLAN provides public subnets that are used to assign public IP addresses to your worker nodes and public app services. However, if you need to secure your apps from the public network interface, several options are available to secure your cluster such as using [Calico network policies](/docs/openshift?topic=openshift-network_policies) or isolating external network workloads to [edge worker nodes](/docs/openshift?topic=openshift-edge).

In standard clusters, the first time that you create a cluster in a zone, a public VLAN and a private VLAN in that zone are automatically provisioned for you in your IBM Cloud infrastructure account. For every subsequent cluster that you create in that zone, you can specify the VLAN pair that you want to use. You can reuse the same public and private VLANs that were created for you because multiple clusters can share VLANs.

For more information about VLANs, subnets, and IP addresses, see [Overview of networking in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-subnets#basics).

Need to create your cluster by using custom subnets? Check out [Using existing subnets to create a cluster](/docs/openshift?topic=openshift-subnets#subnets_custom).
{: tip}

**Worker node communication across subnets and VLANs**</br>
In several situations, components in your cluster must be permitted to communicate across multiple private VLANs. For example, if you want to create a multizone cluster, if you have multiple VLANs for a cluster, or if you have multiple subnets on the same VLAN, the worker nodes on different subnets in the same VLAN or in different VLANs cannot automatically communicate with each other. You must enable either Virtual Routing and Forwarding (VRF) or VLAN spanning for your IBM Cloud infrastructure account.

* [Virtual Routing and Forwarding (VRF)](/docs/dl?topic=dl-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud): VRF enables all the private VLANs and subnets in your infrastructure account to communicate with each other. Additionally, VRF is required to allow your workers and master to communicate over the private service endpoint, and to communicate with other {{site.data.keyword.cloud_notm}} instances that support private service endpoints. To check whether a VRF is already enabled, use the `ibmcloud account show` command. To enable VRF, run `ibmcloud account update --service-endpoint-enable true`. This command output prompts you to open a support case to enable your account to use VRF and service endpoints. VRF eliminates the VLAN spanning option for your account because all VLANs are able to communicate.</br></br>
When VRF is enabled, any system that is connected to any of the private VLANs in the same {{site.data.keyword.cloud_notm}} account can communicate with the cluster worker nodes. You can isolate your cluster from other systems on the private network by applying [Calico private network policies](/docs/openshift?topic=openshift-network_policies#isolate_workers).</dd>
* [VLAN spanning](/docs/vlans?topic=vlans-vlan-spanning#vlan-spanning): If you cannot or do not want to enable VRF, such as if you do not need the master to be accessible on the private network or if you use a gateway appliance to access the master over the public VLAN, enable VLAN spanning. For example, if you have an existing gateway appliance and then add a cluster, the new portable subnets that are ordered for the cluster aren't configured on the gateway appliance but VLAN spanning enables routing between the subnets. To enable VLAN spanning, you need the **Network > Manage Network VLAN Spanning** [infrastructure permission](/docs/openshift?topic=openshift-users#infra_access), or you can request the account owner to enable it. To check whether VLAN spanning is already enabled, use the `ibmcloud oc vlan spanning get` [command](/docs/openshift?topic=openshift-kubernetes-service-cli#cs_vlan_spanning_get). You cannot enable the private service endpoint if you choose to enable VLAN spanning instead of VRF.

</br>

### Worker-to-master and user-to-master communication: Service endpoints
{: #workeruser-master}

A communication channel must be set up so that worker nodes can establish a connection to the Kubernetes master. You must enable the public service endpoint in your cluster. You can optionally enable the private service endpoint for version 3.11 clusters, but not for version 4.3 clusters, which must be public only. Furthermore, you cannot have only the private service endpoint for any cluster.
{: shortdesc}

To secure communication over public and private service endpoints, Red Hat OpenShift on IBM Cloud automatically sets up an OpenVPN connection between the Kubernetes master and the worker node when the cluster is created. Workers securely talk to the master through TLS certificates, and the master talks to workers through the OpenVPN connection.

**Public service endpoint only**</br>
By default, your worker nodes can automatically connect to the Kubernetes master over the public VLAN through the public service endpoint.
* Communication between worker nodes and master is established securely over the public network through the public service endpoint.
* The master is publicly accessible to authorized cluster users only through the public service endpoint. Your cluster users can securely access your Kubernetes master over the internet to run `oc` commands, for example.

**Version 3.11 clusters only: Public and private service endpoints**</br>
To make your master publicly or privately accessible to cluster users, you can enable the public and private service endpoints. You can enable the private service endpoint only by using the CLI to create a cluster. Before you can create a version 3.11 cluster with public and private service endpoints, VRF is required in your {{site.data.keyword.cloud_notm}} account, and you must enable your account to use service endpoints. To enable VRF and service endpoints, run `ibmcloud account update --service-endpoint-enable true`.
* Communication between worker nodes and master is established over both the private network through the private service endpoint and the public network through the public service endpoint. By routing half of the worker-to-master traffic over the public endpoint and half over the private endpoint, your master-to-worker communication is protected from potential outages of the public or private network.
* The master is publicly accessible to authorized cluster users through the public service endpoint. The master is privately accessible through the private service endpoint if authorized cluster users are in your {{site.data.keyword.cloud_notm}} private network or are connected to the private network through a VPN connection or {{site.data.keyword.cloud_notm}} Direct Link. Note that you must [expose the master endpoint through a private load balancer](/docs/openshift?topic=openshift-access_cluster#access_private_se) so that users can access the master through a VPN or {{site.data.keyword.cloud_notm}} Direct Link connection.
* To create a cluster with the public and private service endpoints enabled, use the `ibmcloud oc cluster create classic` [CLI command](/docs/openshift?topic=openshift-kubernetes-service-cli#cs_cluster_create) and include the `--public-service-endpoint` and `--private-service-endpoint` flags.

</br>

### Worker communication to other {{site.data.keyword.cloud_notm}} services or on-premises networks
{: #worker-services-onprem}

Allow your worker nodes to securely communicate with other {{site.data.keyword.cloud_notm}} services and to an on-premises network.
{: shortdesc}

**Communication with other {{site.data.keyword.cloud_notm}} services over the private or public network**</br>
Your worker nodes can automatically and securely communicate with other [{{site.data.keyword.cloud_notm}} services that support private service endpoints](/docs/resources?topic=resources-private-network-endpoints), such as {{site.data.keyword.registrylong}}, over your IBM Cloud infrastructure private network. If an {{site.data.keyword.cloud_notm}} service does not support private service endpoints, your worker nodes must be connected to a public VLAN so that they can securely communicate with the services over the public network.

If you use Calico policies or a gateway appliance to control the public or private networks of your worker nodes, you must allow access to the public IP addresses of the services that support public service endpoints, and optionally to the private IP addresses of the services that support private service endpoints.
* [Allow access to services' public IP addresses in Calico policies](/docs/openshift?topic=openshift-network_policies#isolate_workers_public)
* [Allow access to the private IP addresses of services that support private service endpoints in Calico policies](/docs/openshift?topic=openshift-network_policies#isolate_workers)
* [Allow access to services' public IP addresses and to the private IP addresses of services that support private service endpoints in a gateway appliance firewall](/docs/openshift?topic=openshift-firewall#firewall_outbound)

**{{site.data.keyword.BluDirectLink}} for communication over the private network with resources in on-premises data centers**</br>
To connect your cluster with your on-premises data center, such as with {{site.data.keyword.icpfull_notm}}, you can set up [{{site.data.keyword.cloud_notm}} Direct Link](/docs/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link). With {{site.data.keyword.cloud_notm}} Direct Link, you create a direct, private connection between your remote network environments and Red Hat OpenShift on IBM Cloud without routing over the public internet.

**strongSwan IPSec VPN connection for communication over the public network with resources in on-premises data centers**
Set up a [strongSwan IPSec VPN service](https://www.strongswan.org/about.html){: external} directly in your cluster. The strongSwan IPSec VPN service provides a secure end-to-end communication channel over the internet that is based on the industry-standard Internet Protocol Security (IPSec) protocol suite. To set up a secure connection between your cluster and an on-premises network, [configure and deploy the strongSwan IPSec VPN service](/docs/openshift?topic=openshift-vpn#vpn-setup) directly in a pod in your cluster.

If you plan to use a gateway appliance, set up an IPSec VPN endpoint on a gateway appliance, such as a Virtual Router Appliance (Vyatta). Then, [configure the strongSwan IPSec VPN service](/docs/openshift?topic=openshift-vpn#vpn-setup) in your cluster to use the VPN endpoint on your gateway. If you do not want to use strongSwan, you can [set up VPN connectivity directly with VRA](/docs/openshift?topic=openshift-vpn#vyatta).
{: note}

<p class="tip">If you plan to connect your cluster to on-premises networks, check out the following helpful features:<ul><li>You might have subnet conflicts with the IBM-provided default 172.30.0.0/16 range for pods and 172.21.0.0/16 range for services. You can avoid subnet conflicts when you [create a cluster from the CLI](/docs/openshift?topic=openshift-kubernetes-service-cli#cs_cluster_create) by specifying a custom subnet CIDR for pods in the `--pod-subnet` flag and a custom subnet CIDR for services in the `--service-subnet` flag.</li><li>If your VPN solution preserves the source IP addresses of requests, you can [create custom static routes](/docs/openshift?topic=openshift-static-routes) to ensure that your worker nodes can route responses from your cluster back to your on-premises network.</li></p>

</br>

### External communication to apps that run on worker nodes
{: #external-workers}

Allow public or private traffic requests from outside the cluster to your apps that run on worker nodes.
{: shortdesc}

**Private traffic to cluster apps**</br>
When you deploy an app in your cluster, you might want to make the app accessible to only users and services that are on the same private network as your cluster. Private load balancing is ideal for making your app available to requests from outside the cluster without exposing the app to the general public. You can also use private load balancing to test access, request routing, and other configurations for your app before you later expose your app to the public with public network services. To allow private traffic requests from outside the cluster to your apps, you can create private Kubernetes networking services, such as private NodePorts, NLBs, and Ingress ALBs. You can then use Calico pre-DNAT policies to block traffic to public NodePorts of private networking services. For more information, see [Planning private external load balancing](/docs/openshift?topic=openshift-cs_network_planning#private_access).

**Public traffic to cluster apps**</br>
To make your apps externally accessible from the public internet, you can create public NodePorts, network load balancers (NLBs), and Ingress application load balancers (ALBs). Public networking services connect to this public network interface by providing your app with a public IP address and, depending on the service, a public URL. When an app is publicly exposed, anyone that has the public service IP address or the URL that you set up for your app can send a request to your app. You can then use Calico pre-DNAT policies to control traffic to public networking services, such as whitelisting traffic from only certain source IP addresses or CIDRs and blocking all other traffic. For more information, see [Planning public external load balancing](/docs/openshift?topic=openshift-cs_network_planning#openshift_routers).

Edge worker nodes can improve the security of your cluster by allowing fewer worker nodes that are connected to public VLANs to be accessed externally and by isolating the networking workload. When you [label worker nodes as edge nodes](/docs/openshift?topic=openshift-edge#edge_nodes), NLB and ALB pods are deployed to only those specified worker nodes. Router pods remain deployed to the non-edge worker nodes. To also prevent other workloads from running on edge nodes, you can [taint the edge nodes](/docs/openshift?topic=openshift-edge#edge_workloads). Then, you can deploy both public and private NLBs and ALBs to edge nodes.

<br />


## Example scenarios for classic cluster network setups
{: #classic-scenarios}

Now that you understand the basics of cluster networking, check out some example scenarios in which various classic cluster network setups can meet your workload needs.
{: shortdesc}

### Scenario: Run internet-facing app workloads in a classic cluster
{: #internet-facing}

In this scenario, you want to run workloads in a classic cluster that are accessible to requests from the Internet so that end users can access your apps. You want the option of isolating public access in your cluster and of controlling what public requests are permitted to your cluster. Additionally, your workers have automatic access to any {{site.data.keyword.cloud_notm}} services that you want to connect with your cluster.
{: shortdesc}

<p>
<figure>
 <img src="images/cs_clusters_planning_internet.png" alt="Architecture image for a cluster that runs internet-facing workloads"/>
 <figcaption>Network setup for a cluster that runs internet-facing workloads</figcaption>
</figure>
</p>

**Worker-to-worker communication**

To achieve this setup, you create a cluster by connecting worker nodes to public and private VLANs.

If you create the cluster with both public and private VLANs, you cannot later remove all public VLANs from that cluster. Removing all public VLANs from a cluster causes several cluster components to stop working. Instead, create a new worker pool that is connected to a private VLAN only.
{: note}

**Worker-to-master and user-to-master communication**

You can choose to allow worker-to-master and user-to-master communication over the public and private networks, or over the public network only.
* Public and private service endpoints: Your account must be enabled with VRF and enabled to use service endpoints. Communication between worker nodes and master is established over both the private network through the private service endpoint and the public network through the public service endpoint. The master is publicly accessible to authorized cluster users through the public service endpoint.
* Public service endpoint: If you don’t want to or cannot enable VRF for your account, your worker nodes and authorized cluster users can automatically connect to the Kubernetes master over the public network through the public service endpoint.

**Worker communication to other services or networks**

Your worker nodes can automatically, securely communicate with other {{site.data.keyword.cloud_notm}} services that support private service endpoints over your IBM Cloud infrastructure private network. If an {{site.data.keyword.cloud_notm}} service does not support private service endpoints, workers can securely communicate with the services over the public network. You can lock down the public or private interfaces of worker nodes by using Calico network policies for public network or private network isolation. You might need to allow access to the public and private IP addresses of the services that you want to use in these Calico isolation policies.

If your worker nodes need to access services in private networks outside of your {{site.data.keyword.cloud_notm}} account, you can configure and deploy the strongSwan IPSec VPN service in your cluster or leverage {{site.data.keyword.cloud_notm}} {{site.data.keyword.cloud_notm}} Direct Link services to connect to these networks.

**External communication to apps that run on worker nodes**

To expose an app in your cluster to the internet, you can create a public network load balancer (NLB) or Ingress application load balancer (ALB) service. You can improve the security of your cluster by creating a pool of worker nodes that are labeled as edge nodes. The pods for public network services are deployed to the edge nodes so that external traffic workloads are isolated to only a few workers in your cluster. You can further control public traffic to the network services that expose your apps by creating Calico pre-DNAT policies, such as whitelist and blacklist policies.

Ready to get started with a cluster for this scenario? After you plan your [high availability](/docs/openshift?topic=openshift-ha_clusters) and [worker node](/docs/openshift?topic=openshift-planning_worker_nodes) setups, see [Creating clusters](/docs/openshift?topic=openshift-clusters).

<br />


### Scenario: Extend your on-premises data center to a classic cluster and add limited public access
{: #limited-public}

In this scenario, you want to run workloads in a classic cluster that are accessible to services, databases, or other resources in your on-premises data center. However, you might need to provide limited public access to your cluster, and want to ensure that any public access is controlled and isolated in your cluster. For example, you might need your workers to access an {{site.data.keyword.cloud_notm}} service that does not support private service endpoints, and must be accessed over the public network. Or you might need to provide limited public access to an app that runs in your cluster.
{: shortdesc}

To achieve this cluster setup, you can create a firewall by [using a gateway appliance](#vyatta-gateway).

#### Using a gateway appliance
{: #vyatta-gateway}

Allow limited public connectivity to your classic cluster by configuring a gateway appliance, such as a Virtual Router Appliance (Vyatta), as a public gateway and firewall.
{: shortdesc}

<p>
<figure>
 <img src="images/cs_clusters_planning_gateway.png" width="850" style="width:850px; border-style: none" alt="Architecture image for a cluster that uses a gateway appliance for secure public access"/>
 <figcaption>Network setup for a cluster that uses a gateway appliance for secure public access</figcaption>
</figure>
</p>

**Worker-to-worker communication, worker-to-master and user-to-master communication**

Configure a gateway appliance to provide network connectivity between your worker nodes and the master over the public network. For example, you might choose to set up a [Virtual Router Appliance](/docs/virtual-router-appliance?topic=virtual-router-appliance-about-the-vra) or a [Fortigate Security Appliance](/docs/vmwaresolutions/services?topic=vmwaresolutions-fsa_considerations).

You can set up your gateway appliance with custom network policies to provide dedicated network security for your cluster and to detect and remediate network intrusion. When you set up a firewall on the public network, you must open up the required ports and private IP addresses for each region so that the master and the worker nodes can communicate. If you also configure this firewall for the private network, you must also open up the required ports and private IP addresses to allow communication between worker nodes and let your cluster access infrastructure resources over the private network. You must also enable VLAN spanning for your account so that subnets can route on the same VLAN and across VLANs.

**Worker communication to other services or networks**

To securely connect your worker nodes and apps to an on-premises network or services outside of {{site.data.keyword.cloud_notm}}, set up an IPSec VPN endpoint on your gateway appliance and the strongSwan IPSec VPN service in your cluster to use the gateway VPN endpoint. If you do not want to use strongSwan, you can set up VPN connectivity directly with VRA.

Your worker nodes can securely communicate with other {{site.data.keyword.cloud_notm}} services and public services outside of {{site.data.keyword.cloud_notm}} through your gateway appliance. You can configure your firewall allow access to the public and private IP addresses of only the services that you want to use

**External communication to apps that run on worker nodes**

To provide private access to an app in your cluster, you can create a private network load balancer (NLB) or Ingress application load balancer (ALB) to expose your app to the private network only. If you need to provide limited public access to an app in your cluster, you can create a public NLB or ALB to expose your app. Because all traffic goes through your gateway appliance firewall, you can control public and private traffic to the network services that expose your apps by opening up the service's ports and IP addresses in your firewall to permit inbound traffic to these services.

Ready to get started with a cluster for this scenario? After you plan your [high availability](/docs/openshift?topic=openshift-ha_clusters) and [worker node](/docs/openshift?topic=openshift-planning_worker_nodes) setups, see [Creating clusters](/docs/openshift?topic=openshift-clusters).

<br />




