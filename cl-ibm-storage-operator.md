---

copyright: 
  years: 2024, 2024
lastupdated: "2024-12-11"


keywords: storage operator, add-on, changelog, openshift

subcollection: openshift


---

{{site.data.keyword.attribute-definition-list}}



# IBM storage operator add-on change log 
{: #versions-ibm-storage-operator}

View information for patch updates to the IBM storage-operator add-on in your {{site.data.keyword.openshiftlong_notm}} clusters.
{: shortdesc}

The `ibm-storage-operator` is enabled by default on VPC clusters beginning with version 4.15.
{: note}

To view a list of add-ons and the supported cluster versions in the CLI, run the following command.
```sh
ibmcloud oc cluster addon versions --addon ibm-storage-operator
```
{: pre}

To view a list of add-ons and the supported cluster versions, see the [Supported cluster add-ons table](/docs/openshift?topic=openshift-supported-cluster-addon-versions).


## Version 1.0.0
{: #ibm-storage-operator-1.0.0}

### Change log for version 1.0.16_169, released 11 December 2024
{: #ibm-storage-operator-1.0.16_169}


- Resolves [CVE-2024-51744](https://nvd.nist.gov/vuln/detail/CVE-2024-51744){: external}.



### Change log for version 1.0.15_163, released 3 October 2024
{: #ibm-storage-operator-1.0.15_163}

- Fixes issue with reconciliation of the `file-csi-driver-status` and `addon-vpc-file-csi-driver-configmap` in case it is deleted.
- Updates the golang base image to `1.22.7`.
- Resolves [CVE-2024-2398](https://nvd.nist.gov/vuln/detail/CVE-2024-2398){: external}, [CVE-2024-37370](https://nvd.nist.gov/vuln/detail/CVE-2024-37370){: external}, [CVE-2024-37371](https://nvd.nist.gov/vuln/detail/CVE-2024-37371){: external}.


### Change log for version 1.0.13_151, released 26 August 2024
{: #ibm-storage-operator-1.0.13_151}

- Applies the `PACKAGE_DEPLOYER_VERSION` image automatically on the worker pools where EIT is enabled.
- Updates the golang image to `1.21.13-community`.


### Change log for version 1.0.12_147, released 15 July 2024
{: #ibm-storage-operator-1.0.12_147}

- Updates the golang image to `1.21.12-community`.
- Resolves [CVE-2024-28182](https://nvd.nist.gov/vuln/detail/CVE-2024-28182){: external} and [CVE-2023-2953](https://nvd.nist.gov/vuln/detail/CVE-2023-2953){: external}.


### 1.0.10_141, released 03 July 2024
{: #ibm-storage-operator-1.0.0-initial}

- Initial release.
