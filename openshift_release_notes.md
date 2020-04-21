---

copyright:
  years: 2014, 2020
lastupdated: "2020-04-21"

keywords: openshift, roks, rhos, rhoks

subcollection: openshift

---

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


# Release notes
{: #iks-release}

Use the release notes to learn about the latest changes to the {{site.data.keyword.openshiftlong}} documentation that are grouped by month.
{:shortdesc}

## April 2020
{: #apr20}

| Date | Description |
| ---- | ----------- |
| 20 April 2020 | <ul><li>**General availability**: Red Hat OpenShift on IBM Cloud version 4.3 is generally available as of 20 April 2020 at 12:00 UTC. Any beta clusters that you created remain for only 30 days. You can [create a GA cluster](/docs/openshift?topic=openshift-openshift_tutorial) and then redeploy any apps that you used in any expired beta clusters.</li><li>**Debugging guide**: Added a [Debugging guide](/docs/openshift?topic=openshift-cs_troubleshoot#oc_console_fails) for default OpenShift components such as the console, internal registry, or OperatorHub.</li><li>**Version changelog**: [Patch updates](/docs/openshift?topic=openshift-openshift_changelog#4312_1520_master) are available for master fix pack `4.3.12_1520_openshift` and worker node fix pack `4.3.10_1518_openshift`.</li></ul>
| 16 April 2020 | **Ingress ALB changelog**: Updated the [`ingress-auth` image build to 394](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).|
| 13 April 2020 | <ul><li>**Gateway appliance firewalls**: Updated the [required IP addresses and ports](/docs/openshift?topic=openshift-firewall#firewall_private) that you must open in a private gateway device firewall for {{site.data.keyword.registrylong_notm}}.</li><li>**New! Private Ingress and routes**: In version 4.3 clusters, you can now create [private Ingress controllers](/docs/openshift?topic=openshift-ingress-roks4#ingress-roks4-private) and [private routes](/docs/openshift?topic=openshift-openshift_routes#private-routes-setup-43) to expose your apps on the private network only.</li><li>**Version changelogs**: Worker node patch updates are available for OpenShift [3.11.200_1546_openshift](/docs/openshift?topic=openshift-openshift_changelog#311200_1546_worker).</li></ul>
| 06 April 2020 | <ul><li>**CLI changelog**: Updated the Red Hat OpenShift on IBM Cloud CLI plug-in changelog page for the [release of version 1.0.28](/docs/openshift?topic=openshift-cs_cli_changelog#10).</li></ul> |
{: summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three."}
{: caption="Documentation updates in April 2020"}

## March 2020
{: #mar20}

| Date | Description |
| ---- | ----------- |
| 30 March 2020 | <ul><li>**Version changelogs**: Worker node patch updates are available for OpenShift [3.11.188_1545_openshift](/docs/openshift?topic=openshift-openshift_changelog#311188_1545_worker).</li><li>**`gid` file storage classes**: Added `gid` file storage classes to specify a supplemental group ID that you can assign to a non-root user ID so that the non-root user can read and write to the file storage instance. For more information, see the [storage class reference](/docs/openshift?topic=openshift-file_storage#file_storageclass_reference). </li></ul> |
| 27 March 2020 | **Tech overview**: Added an [Overview of personal and sensitive data storage and removal options](/docs/containers?topic=containers-service-arch#ibm-data). |
| 25 March 2020 | <ul><li>**Gateway appliance firewalls**: Updated the [required IP addresses and ports](/docs/openshift?topic=openshift-firewall#firewall_outbound) that you must open in a public gateway device firewall.</li><li>**Ingress ALB changelog**: Updated the [`nginx-ingress` image build to 627](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li></ul> |
| 24 March 2020 | <ul><li>**CLI changelog**: Updated the Red Hat OpenShift on IBM Cloud CLI plug-in changelog page for the [release of version 1.0.15](/docs/openshift?topic=openshift-cs_cli_changelog#10).</li><li>**Service dependencies**: Added information about [dependencies on other {{site.data.keyword.cloud_notm}} and 3rd party services](/docs/containers?topic=containers-service-arch#dependencies-ibmcloud).</li></ul> |
| 18 March 2020 | <ul><li>**Gateway appliance firewalls**: Updated the [required IP addresses and ports](/docs/openshift?topic=openshift-firewall#firewall_outbound) that you must open in a public gateway device firewall.</li><li>**IAM issuer details**: Added a [reference topic](/docs/openshift?topic=openshift-access_reference#iam_issuer_users) for the IAM issuer details of RBAC users.</li></ul> |
| 16 March 2020 | <ul><li>**New! CLI 1.0**: Updated the Red Hat OpenShift on IBM Cloud CLI plug-in changelog page for the [release of version 1.0.0](/docs/openshift?topic=openshift-cs_cli_changelog#10). This version contains permanent syntax and behavior changes that are not backwards compatible, so before you update be sure to follow the guidance in [Using version 1.0 of the plug-in](/docs/openshift?topic=openshift-cs_cli_changelog#changelog_beta).</li><li>**Default service settings**: Added a page to describe the [default service settings for OpenShift components](/docs/openshift?topic=openshift-service-settings).</li><li>**Image build errors**: Added a troubleshooting topic for [build errors due to image pull authentication](/docs/openshift?topic=openshift-cs_troubleshoot_app#ts_build_img_pull).</li><li>**Installing SGX drivers**: Added a topic for [installing SGX drivers and platform software on SGX-capable worker nodes](/docs/openshift?topic=openshift-add_workers#install-sgx).</li><li>**Sizing workloads**: Enhanced the topic with a [How do I monitor resource usage and capacity in my cluster?](/docs/openshift?topic=openshift-strategy#sizing_manage) FAQ.</li><li>**`sticky-cookie-services` annotation**, OpenShift version 3.11 only: Added the `secure` and `httponly` parameters to the [`sticky-cookie-services` annotation](/docs/openshift?topic=openshift-ingress_annotation#sticky-cookie-services).</li><li>**Enabling TLS for Ingress**, OpenShift version 4.3 only: If you use a custom domain and want to enable TLS for Ingress, you must [add a TLS section to each Ingress resource](/docs/openshift?topic=openshift-ingress-roks4#ingress-roks4-public-3) instead of specifying the certificate in the configuration file for the custom Ingress controller.</li><li>**Version changelogs**: Master and worker node patch updates are available for OpenShift [3.11.170_1544_openshift](/docs/openshift?topic=openshift-openshift_changelog#311170_1544)</li></ul> |
| 12 March 2020 | **Feature gates**: Added the [feature gates for Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-service-settings#feature-gates) that differ from community OpenShift distributions.|
| 09 March 2020 | **Managing Ingress ALBs**: For version 3.11 clusters only: Added a page for [managing the lifecycle of your ALBs](/docs/openshift?topic=openshift-ingress-manage), including information about creating, updating, and moving ALBs. |
| 04 March 2020 | <ul><li>**CLI changelog**: Updated the Red Hat OpenShift on IBM Cloud CLI plug-in changelog page for the [release of version 0.4.102](/docs/openshift?topic=openshift-cs_cli_changelog#04).</li><li>**Ingress ALB changelog**: Updated the [`ingress-auth` image build to 390](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li></ul> |
| 02 March 2020 | **Version changelogs**: Worker node patch updates are available for OpenShift [3.11.170_1543_openshift](/docs/openshift?topic=openshift-openshift_changelog#311170_1543_worker). |
{: summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three."}
{: caption="Documentation updates in March 2020"}

## February 2020
{: #feb20}

| Date | Description |
| ---- | ----------- |
| 19 February 2020 | <ul><li>**CLI changelog**: Updated the Red Hat OpenShift on IBM Cloud CLI plug-in changelog page for the [release of version 0.4.90](/docs/openshift?topic=openshift-cs_cli_changelog).</li><li>**Troubleshooting Ingress**: Added a [debugging guide](/docs/openshift?topic=openshift-cs_troubleshoot_debug_ingress#ingress-debug-roks4) and [troubleshooting topic](/docs/openshift?topic=openshift-cs_troubleshoot_debug_ingress#cs_subnet_limit_43) for Ingress in version 4.3 clusters.</li><li>**Developing and deploying apps**: You can now find expanded information on how to develop and deploy an app to your OpenShift cluster in the following pages:<ul><li>[Planning app deployments](/docs/openshift?topic=openshift-plan_deploy)</li><li>[Building images for your apps](/docs/openshift?topic=openshift-images)</li><li>[Developing apps to run on OpenShift](/docs/openshift?topic=openshift-openshift_apps)</li><li>[Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-deploy_app)</li><li>[Managing the app lifecycle](/docs/openshift?topic=openshift-update_app)</li></ul></li><li>**Learning paths**: Curated learning paths for [administrators](/docs/openshift?topic=openshift-learning-path-admin) and [developers](/docs/openshift?topic=openshift-learning-path-dev) are now available to help guide you through your Red Hat OpenShift on IBM Cloud experience.</li><li>**Setting up image build pipelines**: You can now find expanded information on how to set up an image registry and build pipelines in the following pages:<ul><li>[Setting up an image registry](/docs/openshift?topic=openshift-registry)</li><li>[Setting up continuous integration and delivery](/docs/openshift?topic=openshift-cicd)</li></ul></li><li>**Firewall subnets**: Removed outdated [subnet IP addresses for {{site.data.keyword.registrylong_notm}}](/docs/openshift?topic=openshift-firewall#vyatta_firewall).</li></ul> |
| 18 February 2020 | **Version changelogs**: OpenShift master fix pack for [3.11.161_1542_openshift](/docs/openshift?topic=openshift-openshift_changelog#311161_1542_master).|
| 17 February 2020 | <ul><li>**Migration operator**: Updated the [migration operator storage configuration file](/docs/openshift?topic=openshift-openshift_versions#ocp3to4-migrate-destination) to clarify {{site.data.keyword.cos_short}} endpoints.</li><li>**Version changelogs**: Master and worker node patch updates are available for OpenShift worker fix pack [3.11.161_1542_openshift](/docs/openshift?topic=openshift-openshift_changelog#311161_1542_worker)</li></ul>|
| 10 February 2020 | **New! OpenShift 4.3**: OpenShift 4.3 is now available as a beta. During the beta, the OpenShift license fee is waived. Any 4.3 beta clusters that you create remain for only 30 days after the beta ends and version 4.3 becomes generally available. Also, you cannot update 3.11 clusters to 4.3 clusters. For more information, review the [version release topic](/docs/openshift?topic=openshift-openshift_versions#ocp43). |
| 06 February 2020 | <ul><li>**Cluster autoscaler**: Added a [debugging guide for the cluster autoscaler](/docs/openshift?topic=openshift-troubleshoot_cluster_autoscaler).</li><li>**Expanded troubleshooting**: You can now find troubleshooting steps for OpenShift clusters in the following pages:<ul><li>[Clusters and masters](/docs/openshift?topic=openshift-cs_troubleshoot)</li><li>[Worker nodes](/docs/openshift?topic=openshift-cs_troubleshoot_clusters)</li><li>[Cluster networking](/docs/openshift?topic=openshift-cs_troubleshoot_network)</li><li>[Apps and integrations](/docs/openshift?topic=openshift-cs_troubleshoot_app)</li><li>[Load balancers](/docs/openshift?topic=openshift-cs_troubleshoot_lb)</li><li>[Ingress](/docs/openshift?topic=openshift-cs_troubleshoot_debug_ingress)</li><li>[Persistent storage](/docs/openshift?topic=openshift-cs_troubleshoot_storage)</li></ul></li><li>**Tags**: Added how to [add {{site.data.keyword.cloud_notm}} tags to existing clusters](/docs/openshift?topic=openshift-add_workers#cluster_tags).</li></ul> |
| 03 February 2020 | **Version changelog**: Updates are available for OpenShift master fix pack[3.11.161_1539_openshift](/docs/openshift?topic=openshift-openshift_changelog#311161_1539) and worker fix pack [3.11.161_1540_openshift](/docs/openshift?topic=openshift-openshift_changelog#311161_1540). |
{: summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three."}
{: caption="Documentation updates in February 2020"}

## January 2020
{: #jan20}

| Date | Description |
| ---- | ----------- |
| 30 January 2020 | **Ingress ALB changelog**: Updated the [`nginx-ingress` image build to 625](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog). |
| 27 January 2020 | <ul><li>**Back up and restore File and Block storage**: Added steps for deploying the [<code>ibmcloud-backup-restore</code> Helm chart](/docs/openshift?topic=openshift-utilities#ibmcloud-backup-restore).</li></ul> |
| 22 January 2020 | <ul><li>**Changing VLANs**: After you [change your worker node VLAN connections](/docs/openshift?topic=openshift-cs_network_cluster#change-vlans), you can now [move router services across VLANs](/docs/openshift?topic=openshift-openshift_routes#migrate-router-vlan).</li><li>**Storage utilities**: [IBM Cloud storage utilities](/docs/openshift?topic=openshift-utilities) are now available for OpenShift clusters.</li></ul> |
| 20 January 2020 | <ul><li>**Helm version 3**: Updated [Adding services by using Helm charts](/docs/openshift?topic=openshift-helm) to include steps for installing Helm v3 in your cluster. Migrate to Helm v3 today for several advantages over Helm v2, such as the removal of the Helm server, Tiller.</li><li>**Ingress ALB changelog**: Updated the [`nginx-ingress` image build to 621](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li><li>**Version changelog**: Patch updates are available for OpenShift [3.11.161_1538_openshift](/docs/openshift?topic=openshift-openshift_changelog#311161_1538).</li></ul> |
| 06 January 2020 | **Ingress ALB changelog**: Updated the [`ingress-auth` image to build 373](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).|
| 03 January 2020 | **Version changelog**: Worker node patch updates are available for OpenShift [3.11.157_1537_openshift](/docs/openshift?topic=openshift-openshift_changelog#311154_1536).|
{: summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three."}
{: caption="Documentation updates in January 2020"}

## December 2019
{: #dec19}

| Date | Description |
| ---- | ----------- |
| 18 December 2019 | **Ingress ALB changelog**: Updated the [`nginx-ingress` image build to 615 and the `ingress-auth` image to build 372](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog). |
| 17 December 2019 | **Version changelog**: Master patch updates are available for OpenShift [3.11.154_1536_openshift](/docs/openshift?topic=openshift-openshift_changelog#311154_1536).<li>**Assigning access**: Updated the steps to [assign access to your clusters through the {{site.data.keyword.cloud_notm}} IAM console](/docs/openshift?topic=openshift-users#add_users).</li></ul>|
| 11 December 2019 | <ul><li>**CLI changelog**: Updated the Red Hat OpenShift on IBM Cloud CLI plug-in changelog page for the [release of version 0.4.64](/docs/openshift?topic=openshift-cs_cli_changelog).</li><li>**CLI installation**: Updated the link to download the [`oc` CLI client](/docs/openshift?topic=openshift-openshift-cli).</li></ul>|
| 09 December 2019 | **Version changelog**: Worker node patch updates are available for OpenShift [3.11.154_1534_openshift](/docs/openshift?topic=openshift-openshift_changelog#311154_1534_worker). |
| 04 December 2019 | <ul><li>**Exposing apps with load balancers or Ingress ALBs**: Added quick start pages to help you get up and running with [load balancers](/docs/openshift?topic=openshift-loadbalancer-qs) and [Ingress ALBs](/docs/openshift?topic=openshift-ingress-qs).</li><li>**OpenShift charges**: Now when you create OpenShift clusters, you are not charged for the Red Hat Enterprise Linux operating system that is installed on the worker nodes. For more information, see [What am I charged for when I use OpenShift clusters?](/docs/openshift?topic=openshift-faqs#charges).</li><li>**OpenShift routes**: Added steps for [bringing your own hostname](/docs/openshift?topic=openshift-openshift_routes#routes-setup) for public routes and steps for [setting up private routes](/docs/openshift?topic=openshift-openshift_routes#private-routes-setup).</li><li>**Use the internal KVDB in Portworx**: Automatically set up a key-value database (KVDB) during the Portworx installation to store your Portworx metadata. For more information, see [Using the Portworx KVDB](/docs/openshift?topic=openshift-portworx#portworx-kvdb).</li></ul>|
{: summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three."}
{: caption="Documentation updates in December 2019"}

## November 2019
{: #nov19}

<table summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Documentation updates in November 2019</caption>
<thead>
<th>Date</th>
<th>Description</th>
</thead>
<tbody>
<tr>
  <td>26 November 2019</td>
  <td><ul><li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.61](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Diagnostics and Debug Tool add-on for OpenShift clusters</strong>: The [Diagnostics and Debug Tool](/docs/openshift?topic=openshift-cs_troubleshoot#debug_utility) add-on is now available for OpenShift clusters.</li>
  <li><strong>Version changelog</strong>: Worker node patch updates are available for OpenShift [3.11.154_1533_openshift](/docs/openshift?topic=openshift-openshift_changelog#311154_1533_worker).</li></ul></td>
</tr>
<tr>
<td>22 November 2019</td>
<td><ul>
<li><strong>Bring your own DNS for load balancers</strong>: Added steps for bringing your own custom domain for [NLBs](/docs/openshift?topic=openshift-loadbalancer_hostname#loadbalancer_hostname_dns)</li>
<li><strong>Gateway appliance firewalls</strong>: Updated the [required IP addresses and ports](/docs/openshift?topic=openshift-firewall#vyatta_firewall) that you must open in a public gateway device firewall.</li>
<li><strong>Ingress ALB subdomain format</strong>: [Changes are made to the Ingress subdomain](/docs/openshift?topic=openshift-ingress-about#ingress-resource). New clusters are assigned an Ingress subdomain in the format `<cluster_name>.<globally_unique_account_HASH>-0000.<region>.containers.appdomain.cloud` and an Ingress secret in the format `<cluster_name>.<globally_unique_account_HASH>-0000`. Any existing clusters that use the `<cluster_name>.<region>.containers.mybluemix.net` subdomain are assigned a CNAME record that maps to a `<cluster_name>.<region_or_zone>.containers.appdomain.cloud` subdomain.</li>
</ul></td>
</tr>
<tr>
<td>21 November 2019</td>
<td><ul>
<li><strong>Ingress ALB changelog</strong>: Updated the [ALB `nginx-ingress` image to 597 and the `ingress-auth` image to build 353](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
<li><strong>Version changelog</strong>: Master patch updates are available for OpenShift [3.11.154_1533_openshift](/docs/openshift?topic=openshift-openshift_changelog#311154_1533).</li>
</ul></td>
</tr>
<tr>
<td>15 November 2019</td>
<td><strong>New! Single zone location for OpenShift clusters</strong>:  You can create single zone Red Hat OpenShift on IBM Cloud clusters in São Paulo, Brazil (`sao01`).</td>
</tr>
<tr>
<td>11 November 2019</td>
<td><ul>
<li><strong>OpenShift overview</strong>: Added an [OpenShift overview page](/docs/openshift?topic=openshift-overview).</li>
<li><strong>Setting pod priority</strong>: Added a [pod priority page](/docs/openshift?topic=openshift-pod_priority).</li>
<li><strong>Using {{site.data.keyword.registrylong_notm}}</strong>: Added the following topics about using {{site.data.keyword.registrylong_notm}}:
<ul><li>[Understanding how to authorize your cluster to pull images from a registry](/docs/openshift?topic=openshift-registry#cluster_registry_auth).</li>
<li>[Copying the `default-<region>-icr-io` secrets](/docs/openshift?topic=openshift-registry#copy_imagePullSecret) from the `default` project to the project that you want to pull images from.</li>
<li>[Creating your own image pull secret](/docs/openshift?topic=openshift-registry#other_registry_accounts).</li>
<li>[Adding the image pull secret](/docs/openshift?topic=openshift-registry#use_imagePullSecret) to your deployment configuration or to the project service account.</li></ul>
</li>
<li><strong>Exposing apps that are external to your cluster by using Ingress</strong>: Added information for how to use the [`proxy-external-service` Ingress annotation](/docs/openshift?topic=openshift-ingress#proxy-external) to include an app that is external to your cluster in Ingress application load balancing.</li>
<li><strong>Version changelog</strong>: Worker node patch updates are available for OpenShift [3.11.146_1530_openshift](/docs/openshift?topic=openshift-openshift_changelog#311153_1530).</li>
</ul></td>
</tr>
<tr>
<td>07 November 2019</td>
<td><ul><li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.51](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
<li><strong>Ingress ALB changelog</strong>: Updated the [ALB `ingress-auth` image to build 345](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li></ul></td>
</tr>
<tr>
<td>01 November 2019</td>
<td><strong>New! Keep your own key (KYOK) support (beta)</strong>: You can now [enable several key management service (KMS) providers](/docs/openshift?topic=openshift-encryption#kms), so that you can use your own root key to encrypt the secrets in your cluster.</td>
</tr>
</tbody>
</table>

## October 2019
{: #oct19}

<table summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Documentation updates in October 2019</caption>
<thead>
<th>Date</th>
<th>Description</th>
</thead>
<tbody>
<tr>
<td>31 October 2019</td>
<td><strong>Refreshed Red Hat OpenShift on IBM Cloud docs</strong>: Includes the following new content:<ul>
  <li>[Setting up VPN connectivity](/docs/openshift?topic=openshift-vpn)</li>
  <li>[Changing service endpoints or VLAN connections for OpenShift clusters](/docs/openshift?topic=openshift-access_cluster)</li>
  <li>[Exposing apps with routes](/docs/openshift?topic=openshift-openshift_routes)</li>
  <li>[Exposing apps with network load balancers (NLBs)](/docs/openshift?topic=openshift-loadbalancer-about)</li>
  <li>[Exposing apps with Ingress application load balancers (ALBs)](/docs/openshift?topic=openshift-ingress-about)</li></ul>
</td>
</tr>
<tr>
<td>28 October 2019</td>
<td><strong>Version changelogs</strong>: Worker node patch updates are available for Kubernetes [1.15.5_1521](/docs/containers?topic=containers-changelog#1155_1521), [1.14.8_1537](/docs/containers?topic=containers-changelog#1148_1537), [1.13.12_1540](/docs/containers?topic=containers-changelog#11312_1540), [1.12.10_1570](/docs/containers?topic=containers-changelog#11210_1570), and OpenShift [3.11.153_1529_openshift](/docs/openshift?topic=openshift-openshift_changelog#311153_1529).</td>
</tr><tr>
<td>24 October 2019</td>
  <td><ul>
    <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.42](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
    <li><strong>Ingress subdomain troubleshooting</strong>: Added troubleshooting steps for when [no Ingress subdomain exists after cluster creation](/docs/openshift?topic=openshift-cs_troubleshoot_debug_ingress#ingress_subdomain)</li>
  </ul></td>
</tr>
<tr>
<td>23 October 2019</td>
  <td><ul>
    <li><strong>Ingress ALB changelog</strong>: Updated the ALB [`nginx-ingress` image to build 584 and `ingress-auth` image build to 344](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
    <li><strong>Ingress annotations</strong>: Added the [`proxy-ssl-verify-depth` and `proxy-ssl-name` optional parameters to the `ssl-services` annotation](/docs/openshift?topic=openshift-ingress_annotation#ssl-services).</li></ul></td>
</tr>
<tr>
  <td>22 October 2019</td>
  <td><strong>Version changelogs</strong>: Master patch updates are available for Kubernetes [1.15.5_1520](/docs/containers?topic=containers-changelog#1155_1520), [1.14.8_1536](/docs/containers?topic=containers-changelog#1148_1536), [1.13.12_1539](/docs/containers?topic=containers-changelog#11312_1539), and OpenShift [3.11.146_1528_openshift](/docs/openshift?topic=openshift-openshift_changelog#311146_1528).</td>
</tr>
<tr>
  <td>14 October 2019</td>
  <td><ul>
  <li><strong>Calico MTU</strong>: Added [steps](/docs/containers?topic=containers-kernel#calico-mtu) for changing the Calico plug-in maximum transmission unit (MTU) to meet the network throughput requirements of your environment.</li>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.38](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  </li>
  <li><strong>Cloud Paks</strong>: By using the {{site.data.keyword.cloud_notm}} catalog, you can [add Cloud Paks to your OpenShift clusters](/docs/openshift?topic=openshift-openshift_cloud_paks).</li>
  <li><strong>Cluster autoscaler</strong>: You can [install the cluster autoscaler](/docs/openshift?topic=openshift-ca) Helm chart on OpenShift clusters with Helm Tiller version 2.12 or later.</li>
  <li><strong>Let's Encrypt rate limits for Ingress</strong>: Added [troubleshooting steps] for when no subdomain or secret is generated for the Ingress ALB when you create or delete clusters of the same name.</li>
  <li><strong>Version changelogs</strong>: Worker node patch updates are available for Kubernetes [1.15.4_1519](/docs/containers?topic=containers-changelog#1154_1519_worker), [1.14.7_1535](/docs/containers?topic=containers-changelog#1147_1535_worker), [1.13.11_1538](/docs/containers?topic=containers-changelog#11311_1538_worker), [1.12.10_1569](/docs/containers?topic=containers-changelog#11210_1569_worker), and OpenShift [3.11.146_1527_openshift](/docs/openshift?topic=openshift-openshift_changelog#311146_1527).</li>
  </ul></td>
</tr>
<tr>
  <td>04 October 2019</td>
  <td><ul>
  <li><strong>Version changelog</strong>: Master fix pack updates are available for OpenShift [3.11.146_1526_openshift](/docs/openshift?topic=openshift-openshift_changelog#311146_1526).</li>
  <li><strong>Software-defined storage with Portworx</strong>: You can now install Portworx on your OpenShift cluster as a highly available data management platform for your containerized apps. For more information, see [Storing data software-defined storage (SDS) with Portworx](/docs/openshift?topic=openshift-portworx).</li></ul>
  </td>
</tr>
<tr>
  <td>03 October 2019</td>
  <td><ul>
  <li><strong>Ingress ALB changelog</strong>: Updated the ALB [`nginx-ingress` image to build 579 and `ingress-auth` image build to 341](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  <li><strong>DevOps toolchain</strong>: You can now use the **DevOps** tab on the cluster details page to configure your DevOps toolchain. For more information, see [Setting up a continuous delivery pipeline for a cluster](/docs/openshift?topic=openshift-cicd#continuous-delivery-pipeline).</li>
  <li><strong>Version changelog</strong>: Patch updates are available for OpenShift [3.11.146_1525_openshift](/docs/openshift?topic=openshift-openshift_changelog#311146_1525).</li>
  </ul>
  </td>
</tr>
<tr>
  <td>01 October 2019</td>
  <td><ul>
    <li><strong>End of service of {{site.data.keyword.loganalysislong_notm}} and {{site.data.keyword.monitoringlong_notm}}</strong>: Removed steps for using {{site.data.keyword.loganalysislong_notm}} and {{site.data.keyword.monitoringlong_notm}} to work with cluster logs and metrics. You can collect logs and metrics for your cluster by setting up [{{site.data.keyword.la_full_notm}}](/docs/containers?topic=containers-health#logdna) and [{{site.data.keyword.mon_full_notm}}](/docs/Monitoring-with-Sysdig/tutorials?topic=Sysdig-kubernetes_cluster#kubernetes_cluster) instead.</li>
    <li><strong>OpenShift options</strong>: To help you decide whether to use built-in OpenShift capabilities or integration with {{site.data.keyword.cloud_notm}} services, the following topics are added:<ul>
      <li>[Choosing an image registry solution](/docs/openshift?topic=openshift-registry#openshift_registry_options)</li>
      <li>[Choosing among load balancing solutions](/docs/openshift?topic=openshift-cs_network_planning#routes-vs-ingress) like router or Ingress</li>
      <li>[Understanding options for logging and monitoring](/docs/openshift?topic=openshift-health#oc_logmet_options)</li></ul></li>
    <li><strong>New! Single zone location for OpenShift clusters</strong>: The following locations are now supported. For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).<ul>
      <li>Oslo, Norway</li>
      <li>San Jose, California, US</li></ul></li>
  </ul>
  </td>
</tr>
</tbody></table>

<br />


## September 2019
{: #sept19}

<table summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Documentation updates in September 2019</caption>
<thead>
<th>Date</th>
<th>Description</th>
</thead>
<tbody>
<tr>
  <td>24 September 2019</td>
  <td><ul>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.31](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the ALB [`nginx-ingress` image to build 566](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  </ul></td>
</tr>
<tr>
  <td>19 September 2019</td>
  <td><strong>Sending custom Ingress certificates to legacy clients</strong>: Added [steps](/docs/openshift?topic=openshift-ingress-settings#default_server_cert) for ensuring that your custom certificate, instead of the default IBM-provided certificate, is sent by the Ingress ALB to legacy clients that do not support SNI.</td>
</tr>
<tr>
  <td>17 September 2019</td>
  <td><strong>New! Single zone location for OpenShift clusters</strong>: The following locations are now supported. For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).<ul>
    <li>Amsterdam, the Netherlands</li>
    <li>Hong Kong SAR of the PRC, China</li>
    <li>Mexico City, Mexico</li>
    <li>Milan, Italy</li>
    </ul></td>
</tr>
<tr>
  <td>16 September 2019</td>
  <td><ul><li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.23](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>{{site.data.keyword.at_full_notm}} events</strong>: Added information about [which {{site.data.keyword.at_short}} location your events are sent to](/docs/openshift?topic=openshift-at_events#at-ui) based on the {{site.data.keyword.containerlong_notm}} location where the cluster is located.</li>
  <li><strong>New! Melbourne, Australia `mel01` single zone location for OpenShift clusters</strong>: For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).</li>
  <li><strong>Version changelog</strong>: Master fix pack updates are available for OpenShift [3.11.141_1524_openshift](/docs/openshift?topic=openshift-openshift_changelog#311141_1524).</li></ul>
  </td>
</tr>
<tr>
  <td>13 September 2019</td>
  <td><ul>
  <li><strong>Refreshed Red Hat OpenShift on IBM Cloud docs</strong>: Includes the following new content:<ul>
    <li>[Security information for OpenShift clusters](/docs/openshift?topic=openshift-security).
    <li>[Accessing clusters](/docs/openshift?topic=openshift-access_cluster).</li>
    <li>[App networking options](/docs/openshift?topic=openshift-cs_network_planning) with comparisons of routes, NodePort, load balancers, and Ingress.</li>
    <li>[Common app modification scenarios](/docs/openshift?topic=openshift-plan_deploy#openshift_move_apps_scenarios) for moving apps from community Kubernetes to OpenShift.</li>
    <li>Updated [pricing FAQ](/docs/openshift?topic=openshift-faqs#charges) to explain the monthly license in more detail.</li>
    <li>[Resizing and externally exposing the internal registry](/docs/openshift?topic=openshift-registry#openshift_internal_registry).</li>
    <li>[Tutorial overview](/docs/openshift?topic=openshift-tutorials-ov) with links to tutorials.</li>
    <li>[Using the internal registry in OpenShift](/docs/openshift?topic=openshift-registry#openshift_internal_registry)</ul>
  </li>
    <li><strong>Entitled software</strong>: If you have licensed products from your [MyIBM.com ![External link icon](../icons/launch-glyph.svg "External link icon")](https://myibm.ibm.com) container software library, you can [set up your cluster to pull images from the entitled registry](/docs/openshift?topic=openshift-registry#secret_entitled_software).</li>
  <li><strong>`script update` command</strong>: Added [steps for using the `script update` command](/docs/openshift?topic=openshift-kubernetes-service-cli#script_update) to prepare your automation scripts for the release of version 1.0 of the Red Hat OpenShift on IBM Cloud plug-in.</li>
  </ul></td>
</tr>
<tr>
  <td>12 September 2019</td>
  <td><strong>Ingress ALB changelog</strong>: Updated the ALB [`nginx-ingress` image to build 552](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</td>
</tr>
<tr>
  <td>06 September 2019</td>
  <td><strong>New! Chennai, India `che01` single zone location for OpenShift clusters</strong>: For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).</td>
</tr>
<tr>
  <td>05 September 2019</td>
  <td><strong>Ingress ALB changelog</strong>: Updated the ALB [`ingress-auth` image to build 340](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</td>
</tr>
<tr>
  <td>04 September 2019</td>
  <td><ul><li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.4.3](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>IAM whitelisting</strong>: If you use an IAM whitelist, you must [whitelist the CIDRs of the {{site.data.keyword.containerlong_notm}} control plane](/docs/openshift?topic=openshift-firewall#iam_whitelist) for the zones in the region where your cluster is located so that {{site.data.keyword.containerlong_notm}} can create Ingress ALBs and `LoadBalancers` in your cluster.</li>
  <li><strong>New! Montreal, Canada `mon01` single zone location for OpenShift clusters</strong>: For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).</li></ul></td>
</tr>
<tr>
  <td>03 September 2019</td>
  <td><ul><li><strong>New! Red Hat OpenShift on IBM Cloud plug-in version `0.4`</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for multiple changes in the [release of version 0.4.1](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Version changelog</strong>: Worker node patch updates are available for Kubernetes [1.15.3_1516](/docs/containers?topic=containers-changelog#1153_1516_worker), [1.14.6_1532](/docs/containers?topic=containers-changelog#1146_1532_worker), [1.13.10_1535](/docs/containers?topic=containers-changelog#11310_1535_worker), [1.12.10_1566](/docs/containers?topic=containers-changelog#11210_1566_worker), and OpenShift [3.11.135_1523](/docs/openshift?topic=openshift-openshift_changelog#311135_1523_worker).</li></ul></td>
</tr>
</tbody></table>

<br />


## August 2019
{: #aug19}

<table summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>Documentation updates in August 2019</caption>
<thead>
<th>Date</th>
<th>Description</th>
</thead>
<tbody>
<tr>
  <td>30 August 2019</td>
  <td><strong>New! Paris, France `par01` single zone location for OpenShift clusters</strong>: For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).</td>
</tr>
<tr>
  <td>29 August 2019</td>
  <td><strong>Forwarding Kubernetes API audit logs to {{site.data.keyword.la_full_notm}}</strong>: Added steps to [create an audit webhook in your cluster](/docs/containers?topic=containers-health#webhook_logdna) to collect Kubernetes API audit logs from your cluster and forward them to {{site.data.keyword.la_full_notm}}.</td>
</tr>
<tr>
  <td>28 August 2019</td>
  <td><ul>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.3.112](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Version changelog</strong>: Changelog added for master fix pack [3.11.135_1522_openshift](/docs/openshift?topic=openshift-openshift_changelog#311135_1522).</li>
  </ul></td>
</tr>
<tr>
  <td>26 August 2019</td>
  <td><ul>
  <li><strong>Cluster autoscaler</strong>: With the latest version of the cluster autoscaler, you can [enable autoscaling for worker pools during the Helm chart installation](/docs/openshift?topic=openshift-ca#ca_helm) instead of modifying the config map after installation.</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the ALB [`nginx-ingress` image to build 524 and `ingress-auth` image to build 337](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  <li><strong>New! Seoul, Korea `seo01` single zone location for OpenShift clusters</strong>: For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).</li></ul></td>
</tr>
<tr>
  <td>23 August 2019</td>
  <td>
  <strong>New! Single zone locations for OpenShift clusters</strong>: You can create OpenShift clusters in Toronto, Canada `tor01` and Singapore `sng01` single zone locations. For more locations, see [Single and multizone locations in Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-regions-and-zones#zones).</td>
</tr>
<tr>
  <td>20 August 2019</td>
  <td><strong>Ingress ALB changelog</strong>: Updated the ALB [`nginx-ingress` image to build 519](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog) for a `custom-ports` bug fix.</td>
</tr>
<tr>
  <td>17 August 2019</td>
  <td><ul>
  <li><strong>{{site.data.keyword.at_full}}</strong>: The [{{site.data.keyword.at_full_notm}} service](/docs/openshift?topic=openshift-at_events) is now supported for you to view, manage, and audit user-initiated activities in your clusters.</li>
  <li><strong>Version changelog</strong>: Changelog added for master fix pack [3.11.135_1521_openshift](/docs/openshift?topic=openshift-openshift_changelog#311135_1521_master).</li></ul></td>
</tr>
<tr>
  <td>15 August 2019</td>
  <td>
  <strong>Version changelog</strong>: Changelogs added for master fix pack [3.11.135_1520_openshift](/docs/openshift?topic=openshift-openshift_changelog#311135_1520_master).</td>
</tr>
<tr>
  <td>12 August 2019</td>
  <td><ul>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.3.103](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the ALB `ingress-auth` image to build 335 for [`musl libc` vulnerabilities](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li></ul></td>
</tr>
<tr>
  <td>05 August 2019</td>
  <td><ul>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.3.99](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Version changelog</strong>: Changelogs added for worker node patch [3.11.129_1518_openshift](/docs/openshift?topic=openshift-openshift_changelog#311129_1518_worker).</li></ul></td>
</tr>
<tr>
  <td>02 August 2019</td>
  <td><strong>Version changelog</strong>: Changelogs added for [3.11.129_1517_openshift](/docs/openshift?topic=openshift-openshift_changelog#311129_1517).</td>
</tr>
<tr>
  <td>01 August 2019</td>
  <td><strong>Red Hat OpenShift on IBM Cloud</strong>: Red Hat OpenShift on IBM Cloud is generally available as of 1 August 2019 at 0:00 UTC. You can [create a GA cluster](/docs/openshift?topic=openshift-openshift_tutorial) and then redeploy any apps that you used in any expired beta clusters.</td>
</tr>
</tbody></table>

## July 2019
{: #jul19}

<table summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>{{site.data.keyword.containerlong_notm}} documentation updates in July 2019</caption>
<thead>
<th>Date</th>
<th>Description</th>
</thead>
<tbody>
<tr>
  <td>30 July 2019</td>
  <td><ul>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.3.95](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the ALB `nginx-ingress` image to build 515 for the [ALB pod readiness check](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  <li><strong>Removing subnets from a cluster</strong>: Added steps for removing subnets [in an IBM Cloud infrastructure account](/docs/openshift?topic=openshift-subnets#remove-sl-subnets) or [in an on-premises network](/docs/openshift?topic=openshift-subnets#remove-user-subnets) from a cluster. </li>
  </ul></td>
</tr>
<tr>
  <td>26 July 2019</td>
  <td><strong>Red Hat OpenShift on IBM Cloud</strong>: Added [integrations](/docs/openshift?topic=openshift-supported_integrations), [locations](/docs/openshift?topic=openshift-regions-and-zones), and [security context constraints](/docs/openshift?topic=openshift-openshift_scc) topics. Added the `basic-users` and `self-provisioning` cluster roles to the [IAM service role to RBAC sync](/docs/openshift?topic=openshift-access_reference#service) topic.</td>
</tr>
<tr>
  <td>23 July 2019</td>
  <td><strong>Fluentd changelog</strong>: Fixes [Alpine vulnerabilities](/docs/containers?topic=containers-cluster-add-ons-changelog#fluentd_changelog).</td>
</tr>
<tr>
  <td>19 July 2019</td>
  <td><strong>Red Hat OpenShift on IBM Cloud</strong>: Added the [Red Hat OpenShift on IBM Cloud documentation to a separate repository](/docs/openshift?topic=openshift-getting-started). Because the {{site.data.keyword.containerlong_notm}} logic and underlying cloud infrastructure is the same, many topics are reused across the documentation for community Kubernetes and OpenShift cluster documentation, such as this release notes topic.
  </td>
</tr>
<tr>
  <td>17 July 2019</td>
  <td><strong>Ingress ALB changelog</strong>: [Fixes `rbash` vulnerabilities](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).
  </td>
</tr>
<tr>
  <td>15 July 2019</td>
  <td><ul>
  <li><strong>Ingress ALB changelog</strong>: Updated the [ALB `nginx-ingress` image to build 497](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  <li><strong>Troubleshooting clusters</strong>: Added [troubleshooting steps](/docs/containers?topic=containers-cs_troubleshoot_clusters#cs_totp) for when you cannot manage clusters and worker nodes because the time-based one-time passcode (TOTP) option is enabled for your account.</li></ul>
  </td>
</tr>
<tr>
  <td>02 July 2019</td>
  <td><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of version 0.3.58](/docs/openshift?topic=openshift-cs_cli_changelog).</td>
</tr>
<tr>
  <td>01 July 2019</td>
  <td><ul>
  <li><strong>Infrastructure permissions</strong>: Updated the [classic infrastructure roles](/docs/openshift?topic=openshift-access_reference#infra) required for common use cases.</li>
  <li><strong>OpenShift FAQs</strong>: Expanded the [FAQs](/docs/openshift?topic=openshift-faqs#container_platforms) to include information about OpenShift clusters.</li>
  <li><strong>strongSwan VPN service</strong>: If you install strongSwan in a multizone cluster and use the `enableSingleSourceIP=true` setting, you can now [set `local.subnet` to the `%zoneSubnet` variable and use the `local.zoneSubnet` to specify an IP address as a /32 subnet for each zone of the cluster](/docs/openshift?topic=openshift-vpn#strongswan_4).</li>
  </ul></td>
</tr>
</tbody></table>


## June 2019
{: #jun19}

<table summary="The table shows release notes. Rows are to be read from the left to right, with the date in column one, the title of the feature in column two and a description in column three.">
<caption>{{site.data.keyword.containerlong_notm}} documentation updates in June 2019</caption>
<thead>
<th>Date</th>
<th>Description</th>
</thead>
<tbody>
<tr>
  <td>24 June 2019</td>
  <td><ul>
  <li><strong>Calico network policies</strong>: Added a set of [public Calico policies](/docs/openshift?topic=openshift-network_policies#isolate_workers_public) and expanded the set of [private Calico policies](/docs/openshift?topic=openshift-network_policies#isolate_workers) to protect your cluster on public and private networks.</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the [ALB `nginx-ingress` image to build 477](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  </ul></td>
</tr>
<tr>
  <td>21 June 2019</td>
  <td><ul>
  <li><strong>Accessing OpenShift clusters</strong>: Added steps for [automating access to an OpenShift cluster by using an OpenShift login token](/docs/openshift?topic=openshift-access_cluster#access_oc_console).</li>
  <li><strong>Troubleshooting OpenShift clusters</strong>: Added a [troubleshooting section](/docs/openshift?topic=openshift-cs_troubleshoot) to the Creating a Red Hat OpenShift on IBM Cloud cluster tutorial.</li></ul>
  </td>
</tr>
<tr>
  <td>18 June 2019</td>
  <td><ul>
  <li><strong>CLI changelog</strong>: Updated the {{site.data.keyword.containerlong_notm}} CLI plug-in changelog page for the [release of versions 0.3.47 and 0.3.49](/docs/openshift?topic=openshift-cs_cli_changelog).</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the [ALB `nginx-ingress` image to build 473 and `ingress-auth` image to build 331](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  <li><strong>Removing persistent storage</strong>: Updated the information for how you are billed when you [delete persistent storage](/docs/containers?topic=containers-cleanup).</li>
  <li><strong>Service bindings with private endpoint</strong>: [Added steps](/docs/openshift?topic=openshift-service-binding) for how to manually create service credentials with the private service endpoint when you bind the service to your cluster.</li>
  </ul></td>
</tr>
<tr>
  <td>14 June 2019</td>
  <td><ul>
  <li><strong>`kubectl` troubleshooting</strong>: Added a [troubleshooting topic](/docs/openshift?topic=openshift-cs_troubleshoot#kubectl_fails) for when you have a `kubectl` client version that is 2 or more versions apart from the server version or the OpenShift version of `kubectl`, which does not work with community Kubernetes clusters.</li>
  <li><strong>Tutorials landing page</strong>: Replaced the related links page with a new [tutorials landing page](/docs/containers?topic=containers-tutorials-ov) for all tutorials that are specific to {{site.data.keyword.containershort_notm}}.</li>
  <li><strong>Using existing subnets to create a cluster</strong>: To [reuse subnets from an unneeded cluster when you create a new cluster](/docs/openshift?topic=openshift-subnets#subnets_custom), the subnets must be user-managed subnets that you manually added from an on-premises network. All subnets that were automatically ordered during cluster creation are immediately deleted after you delete a cluster, and you cannot reuse these subnets to create a new cluster.</li>
  </ul></td>
</tr>
<tr>
  <td>12 June 2019</td>
  <td><strong>Aggregating cluster roles</strong>: Added steps for [extending users' existing permissions by aggregating cluster roles](/docs/openshift?topic=openshift-users#rbac_aggregate).</td>
</tr>
<tr>
  <td>07 June 2019</td>
  <td><ul>
  <li><strong>Access to the Kubernetes master through the private service endpoint</strong>: Added [steps](/docs/openshift?topic=openshift-access_cluster#access_private_se) to expose the private service endpoint through a private load balancer. After you complete these steps, your authorized cluster users can access the Kubernetes master from a VPN or {{site.data.keyword.cloud_notm}} Direct Link connection.</li>
  <li><strong>{{site.data.keyword.BluDirectLink}}</strong>: Added {{site.data.keyword.cloud_notm}} Direct Link to the [VPN connectivity](/docs/openshift?topic=openshift-vpn) and [hybrid cloud](/docs/containers?topic=containers-hybrid_iks_icp) pages as a way to create a direct, private connection between your remote network environments and {{site.data.keyword.containerlong_notm}} without routing over the public internet.</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the [ALB `ingress-auth` image to build 330](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  <li><strong>OpenShift beta</strong>: [Added a lesson](/docs/openshift?topic=openshift-health#openshift_logdna) about how to modify app deployments for privileged security context constraints for {{site.data.keyword.la_full_notm}} and {{site.data.keyword.mon_full_notm}} add-ons.</li>
  </ul></td>
</tr>
<tr>
  <td>06 June 2019</td>
  <td><ul>
  <li><strong>Fluentd changelog</strong>: Added a [Fluentd version changelog](/docs/containers?topic=containers-cluster-add-ons-changelog#fluentd_changelog).</li>
  <li><strong>Ingress ALB changelog</strong>: Updated the [ALB `nginx-ingress` image to build 470](/docs/containers?topic=containers-cluster-add-ons-changelog#alb_changelog).</li>
  </ul></td>
</tr>
<tr>
  <td>05 June 2019</td>
  <td><ul>
  <li><strong>CLI reference</strong>: Updated the [CLI reference page](/docs/openshift?topic=openshift-kubernetes-service-cli) to reflect multiple changes for the [release of version 0.3.34](/docs/openshift?topic=openshift-cs_cli_changelog) of the {{site.data.keyword.containerlong_notm}} CLI plug-in.</li>
  <li><strong>New! Red Hat OpenShift on IBM Cloud clusters</strong>: With the Red Hat OpenShift on IBM Cloud beta, you can create {{site.data.keyword.containerlong_notm}} clusters with worker nodes that come installed with the OpenShift container orchestration platform software. You get all the advantages of managed {{site.data.keyword.containerlong_notm}} for your cluster infrastructure environment, along with the [OpenShift tooling and catalog ![External link icon](../icons/launch-glyph.svg "External link icon")](https://docs.openshift.com/container-platform/3.11/welcome/index.html) that runs on Red Hat Enterprise Linux for your app deployments. To get started, see [Tutorial: Creating a Red Hat OpenShift on IBM Cloud cluster](/docs/openshift?topic=openshift-openshift_tutorial).</li>
  </ul></td>
</tr>
</tbody></table>

