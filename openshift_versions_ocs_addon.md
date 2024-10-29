---

copyright:
  years: 2014, 2024
lastupdated: "2024-10-29"


keywords: odf, openshift data foundation add-on, change log

subcollection: openshift

---

{{site.data.keyword.attribute-definition-list}}





# OpenShift Data Foundation add-on change log
{: #odf_addon_changelog}


View information for updates to the OpenShift Data Foundation add-on in your {{site.data.keyword.openshiftlong}} clusters.
{: shortdesc}

Note that the add-on supports`n+1` cluster versions.
{: note}

To view a list of add-ons and the supported {{site.data.keyword.redhat_openshift_notm}} versions, see the [supported add-on versions table](/docs/openshift?topic=openshift-supported-cluster-addon-versions) or run the following command.

```sh
ibmcloud oc cluster addon versions --addon openshift-data-foundation
```
{: pre}

## Version 4.16
{: #4.16_odf}

### Version 4.16.3, released 28 October 2024

- Resolves [CVE-2024-5535](https://nvd.nist.gov/vuln/detail/CVE-2024-5535){: external}.

## Version 4.15
{: #4.15_odf}

### Version 4.15.6, released 28 October 2024
{: #4.15.6_odf}

- Resolves [CVE-2024-5535](https://nvd.nist.gov/vuln/detail/CVE-2024-5535){: external} and [CVE-2023-37920](https://nvd.nist.gov/vuln/detail/CVE-2023-37920){: external}.


### Version 4.15.4, released 03 August 2024
{: #4.15.5_odf}

- Resolves [CVE-2024-37370](https://nvd.nist.gov/vuln/detail/CVE-2024-37370){: external} and [CVE-2024-37371](https://nvd.nist.gov/vuln/detail/CVE-2024-37371){: external}.

### Version 4.15.4, released 15 July 2024
{: #4.15.4_odf}

- Updates golang updated to `1.21.12`.
- Resolves vulnerabilities.

### Version 4.15.3, released 24 June 2024
{: #4.15.3_odf}

- Resolves [CVE-2023-45288](https://nvd.nist.gov/vuln/detail/CVE-2023-45288){: external}

### Version 4.15.2, released 5 June 2024
{: #4.15.2_odf}

- Updates `golang` to `1.21.10`.

### Version 4.15.0, released 10 May 2024
{: #4.15.0_odf}

- Initial release of version `4.15.0`.
- Adds the `useCephRBDAsDefaultStorageClass`, `enableNFS`, and `resourceProfile` parameters. For more information, see the [parameter reference](/docs/openshift?topic=openshift-openshift_storage_parameters).

## Version 4.14
{: #4.14_odf}

### Version 4.14.16, released 03 August 2024
{: #4.14.16_odf}

- Resolves [CVE-2024-37370](https://nvd.nist.gov/vuln/detail/CVE-2024-37370){: external} and [CVE-2024-37371](https://nvd.nist.gov/vuln/detail/CVE-2024-37371){: external}.

### Version 4.14.15, released 15 July 2024
{: #4.14.15_odf}

- Updates golang updated to `1.21.12`.
- Resolves vulnerabilities.

### Version 4.14.14, released 24 June 2024
{: #4.14.14_odf}

- Resolves [CVE-2023-45288](https://nvd.nist.gov/vuln/detail/CVE-2023-45288){: external}

### Version 4.14.13, released 5 June 2024
{: #4.14.13_odf}

- Updates `golang` to `1.21.10`.

### Version 4.14.11, released 19 April 2024
{: #4.14.11_odf}

- Updates `golang` to `1.21.9`.
- Adds a node watcher.


### Version 4.14.10, released 08 April 2024
{: #4.14.10_odf}

- Fixes a memory leak in the configmap watcher.

### Version 4.14.9, released 26 March 2024
{: #4.14.9_odf}

- Adds support to specify worker pools.
- Adds an OSD size check.

### Version 4.14.8, released 08 March 2024
{: #4.14.8_odf}

- Vulnerability fixes.

### Version 4.14.7, released 29 February 2024
{: #4.14.7_odf}

- Adds a taint node toleration for the Local Storage Operator.
- Fixes a bug in the DR annotation.


### Version 4.14.5, 14 February 2024
{: #4.14.5_odf}

- Changes the default base image.
- Fixes vulnerabilities.


### Version 4.14.0, released 19 January 2024
{: #4.14.0_odf}

- Adds the `disableNoobaaLB`, `taintNodes`, `addSingleReplicaPool`, and `prepareForDisasterRecovery` parameters. For more information, see the [OpenShift Data Foundation add-on parameter reference](/docs/openshift?topic=openshift-openshift_storage_parameters).


## Version 4.13
{: #4.13_odf}

### Version 4.13.19, released 03 August 2024
{: #4.13.19_odf}

- Resolves [CVE-2024-37370](https://nvd.nist.gov/vuln/detail/CVE-2024-37370){: external} and [CVE-2024-37371](https://nvd.nist.gov/vuln/detail/CVE-2024-37371){: external}.

### Version 4.13.18, released 15 July 2024
{: #4.13.18_odf}

- Updates golang updated to `1.21.12`.
- Resolves vulnerabilities.

### Version 4.13.17, released 5 June 2024
{: #4.13.17_odf}

- Updates `golang` to `1.21.10`.

### Version 4.13.16, released 19 April 2024
{: #4.13.16_odf}

- Updates `golang` to `1.21.9`.
- Adds a node watcher.


### Version 4.13.15, released 08 March 2024
{: #4.13.15_odf}

- Fixes a memory leak in the configmap watcher.

### Version 4.13.14, released 14 March 2024
{: #4.13.14_odf}

- Adds an OSD size check.

### Version 4.13.13, released 08 March 2024
{: #4.13.13_odf}

- Vulnerability fixes.

### Version 4.13.12, released 04 March 2024
{: #4.13.12_odf}

- Adds a taint node toleration for the Local Storage Operator.

### Version 4.13.11, released 14 February 2024
{: #4.13.11_odf}

- Default base image changed.
- Vulnerability fixes.


### Version 4.13.9, released 23 January 2024
{: #4.13.9_odf}

- Adds a new parameter to disable the Noobaa public load balancer.
- Fixes a bug with uninstalling.

### Version 4.13.7, released 02 November 2023
{: #4.13.7_odf}

- Updates the UBI image to `8.8-10721697`.

### Version 4.13.6, released 20 October 2023
{: #4.13.6_odf}

- Updates the UBI image to `8.8-10721696`.

### Version 4.13.4, released 12 September 2023
{: #4.13.4_odf}

- Golang updated to `1.20.07`.
- Updates the UBI image to `8.8-1037`.

### Version 4.13.3, released 31 July 2023
{: #4.13.3_odf}

- Golang updated to `1.20.06`.
- Updates the UBI image to `8.8-1014`.


### Version 4.13.0, released 10 July 2023
{: #4.13.0_odf}

- Initial 4.13 release. 
- Adds support for encryption in transit by specifying the `encryptionInTransit` parameter when installing the add-on.

## Version 4.12
{: #4.12_odf}

### Version 4.12.21, released 03 August 2024
{: #4.12.21_odf}

- Resolves [CVE-2024-37370](https://nvd.nist.gov/vuln/detail/CVE-2024-37370){: external} and [CVE-2024-37371](https://nvd.nist.gov/vuln/detail/CVE-2024-37371){: external}.

### Version 4.12.20, released 15 July 2024
{: #4.12.20_odf}

- Updates golang updated to `1.21.12`.
- Resolves vulnerabilities.

### Version 4.12.19, released 5 June 2024
{: #4.12.19_odf}

- Updates `golang` to `1.21.10`.

### Version 4.12.18, released 19 April 2024
{: #4.12.18_odf}

- Updates `golang` to `1.21.9`.
- Adds a node watcher.


### Version 4.12.17, released 04 March 2024
{: #4.12.17_odf}

- Vulnerability fixes

### Version 4.12.16, released 14 February 2024
{: #4.12.16_odf}

- Default base image changed

### Version 4.12.15, released 02 February 2024
{: #4.12.15_odf}

- Vulnerability fixes.

### Version 4.12.13, released 29 November 2023 
{: #4.12.13_odf}

- Golang updated to `1.20.11`.
- Updates the UBI image to `8.9-1029`.
- Resolves the following CVEs: [CVE-2023-45283](https://nvd.nist.gov/vuln/detail/CVE-2023-45283){: external} and [CVE-2023-45284](https://nvd.nist.gov/vuln/detail/CVE-2023-45284){: external}.

### Version 4.12.12, released 02 November 2023
{: #4.12.12_odf}

- Updates the UBI to`8.8-1072.1697`.

### Version 4.12.11, released 20 October 2023
{: #4.12.11_odf}

- Updates the UBI to`8.8-1072.1696`.

### Version 4.12.9, released 12 September 2023
{: #4.12.9_odf}

- Golang updated to `1.20.7`.
- Updates the UBI to`8.8-1037`.

### Version 4.12.8, released 31 July 2023
{: #4.12.8_odf}

- Golang updated to `1.20.6`.
- Updates the UBI to`8.8-1014`.

### Version 4.12.6, released 28 June 2023
{: #4.12.6_odf}

- Golang updated to `1.20.5`.


### Version 4.12.5, released 09 June 2023
{: #4.12.5_odf}

- Golang updated to `1.19.9`.
- Updates the UBI image to `8.8-860`.


### Version 4.12.4, released 05 May 2023
{: #4.12.4_odf}

- LSO channel updated.
- Golang updated to `1.19.8`.
- Resolves the following CVEs: [CVE-2023-0361](https://nvd.nist.gov/vuln/detail/CVE-2023-0361){: external}, [CVE-2023-24536](https://nvd.nist.gov/vuln/detail/CVE-2023-24536){: external}, [CVE-2023-24537](https://nvd.nist.gov/vuln/detail/CVE-2023-24537){: external}, [CVE-2023-24538](https://nvd.nist.gov/vuln/detail/CVE-2023-24538){: external}.


### Version 4.12.0, released 16 March 2023
{: #4.12.0_odf}

Initial release.

## Version 4.11
{: #4.11_odf}


### Version 4.11.21, released 04 March 2024
{: #4.11.21_odf}

- Vulnerability fixes

### Version 4.11.20, released 14 February 2024
{: #4.11.20_odf}

- Default base image changed

### Version 4.11.19, released 02 February 2024
{: #4.11.19_odf}

- Vulnerability fixes.

### Version 4.11.18, released 29 November 2023 
{: #4.11.18_odf}

- Golang updated to `1.20.11`.
- Updates the UBI image to `8.9-1029`.
- Resolves the following CVEs: [CVE-2023-45283](https://nvd.nist.gov/vuln/detail/CVE-2023-45283){: external} and [CVE-2023-45284](https://nvd.nist.gov/vuln/detail/CVE-2023-45284){: external}.

### Version 4.11.17, released 02 November 2023
{: #4.11.17_odf}

- Updates the UBI image to `8.9-10721697`.

### Version 4.11.16, released 20 October 2023
{: #4.11.16_odf}

- Updates the UBI image to `8.9-10721696`.

### Version 4.11.14, released 12 September 2023
{: #4.11.14_odf}

- Golang updated to `1.20.7`.
- Updates the UBI image to `8.9-1037`.

### Version 4.11.13, released 31 July 2023
{: #4.11.13_odf}

- Golang updated to `1.20.6`.
- Updates the UBI image to `8.9-1014`.


### Version 4.11.11, released 09 June 2023
{: #4.11.11_odf}

- Golang updated to `1.19.9`.
- Updates the UBI image to `8.8-860`.

### Version 4.11.10, released 05 May 2023
{: #4.11.10_odf}

- LSO channel updated.
- Golang updated to `1.19.8`.
- Resolves the following CVEs: [CVE-2023-0361](https://nvd.nist.gov/vuln/detail/CVE-2023-0361){: external}, [CVE-2023-24536](https://nvd.nist.gov/vuln/detail/CVE-2023-24536){: external}, [CVE-2023-24537](https://nvd.nist.gov/vuln/detail/CVE-2023-24537){: external}, [CVE-2023-24538](https://nvd.nist.gov/vuln/detail/CVE-2023-24538){: external}.

### Version 4.11.4, released 14 February 2023
{: #4.11.4_odf}

Updates the UBI image to version `8.7-1049.1675784874`.

### Version 4.11.3, released 18 January 2023
{: #4.11.3_odf}

Updates the UBI image to version `8.7-1049`.

### Version 4.11.2, released 03 January 2023
{: #4.11.2_odf}

Updates Golang to `1.18.9`.

### Version 4.11.0, released 21 December 2022
{: #4.11.0_odf}

Initial release.

## Version 4.10
{: #4.10_odf}

### Version 4.10.32, released 29 November 2023 
{: #4.10.32_odf}

- Golang updated to `1.20.11`.
- Updates the UBI image to `8.9-1029`.
- Resolves the following CVEs: [CVE-2023-45283](https://nvd.nist.gov/vuln/detail/CVE-2023-45283){: external} and [CVE-2023-45284](https://nvd.nist.gov/vuln/detail/CVE-2023-45284){: external}.


### Version 4.10.31, released 02 November 2023
{: #4.10.31_odf}

- Updates the UBI image to `8.8-10721697`.

### Version 4.10.30 released 20 October 2023
{: #4.10.30_odf}

- Updates the UBI image to `8.8-10721696`.

### Version 4.10.29, released 12 September 2023
{: #4.10.29_odf}

- Updates the UBI image to `8.8-1037`.
- Golang updated to `1.20.7`.

### Version 4.10.28, released 31 July 2023
{: #4.10.28_odf}

- Updates the UBI image to `8.8-1014`.
- Golang updated to `1.20.6`.

### Version 4.10.27, released 28 June 2023
{: #4.10.27_odf}

- Golang updated to `1.20.5`.

### Version 4.10.26 released 09 June 2023
{: #4.10.26_odf}

- Golang updated to `1.19.9`.
- Updates the UBI image to `8.8-860`.

### Version 4.10.24, released 05 May 2023
{: #4.10.24_odf}

- Golang updated to `1.19.8`.
- Resolves the following CVEs: [CVE-2023-0361](https://nvd.nist.gov/vuln/detail/CVE-2023-0361){: external}, [CVE-2023-24536](https://nvd.nist.gov/vuln/detail/CVE-2023-24536){: external}, [CVE-2023-24537](https://nvd.nist.gov/vuln/detail/CVE-2023-24537){: external}, [CVE-2023-24538](https://nvd.nist.gov/vuln/detail/CVE-2023-24538){: external}.

### Version 4.10.14, released 17 November 2023
{: #4.10.14_odf}

Updates the UBI.

### Version 4.10.12, released 02 November 2022
{: #4.10.12_odf}

Updates the UBI.

### Version 4.10.11, released 16 September 2022
{: #4.10.11_odf}

- Updates Golang.
- Updates the UBI.

### Version 4.10.10, released 01 September 2022
{: #4.10.10_odf}

Updates the UBI.

### Version 4.10.9, released 12 August 2022
{: #4.10.9_odf}

- Updates Golang.
- Updates the UBI.


### Version 4.10.7, released 02 August 2022
{: #4.10.7_odf}

Adds standalone OCS operator.

### Version 4.10.6, released 12 July 2022
{: #4.10.6_odf}

Updates the UBI.

### Version 4.10.5, released 7 July 2022
{: #4.10.5_odf}

- Updates GoLang update.
- Includes bug fixes.

### Version 4.10.4, released 22 June 2022
{: #4.10.4_odf}

Updates the UBI.

### Version 4.10.3, released 13 June 2022
{: #4.10.3_odf}

Includes bug fixes.

### Version 4.10.2, released 23 May 2022
{: #4.10.2_odf}

Includes storage class encryption parameter parsing improvements.


### Version 4.10.1, released 20 May 2022
{: #4.10.1_odf}

- Includes support for {{site.data.keyword.hscrypto}} encryption.
- Updates the UBI to version `8.6-751`.

### Version 4.10.0, released 9 May 2022
{: #4.10.0_odf}

Initial release.


## Version 4.9
{: #4.9_odf}

### Version 4.9.29, released 28 June 2023
{: #4.9.29_odf}

- Golang updated to `1.20.5`.

### Version 4.9.28, released 09 June 2023
{: #4.9.28_odf}

- Golang updated to `1.19.9`
- Updates the UBI image to `8.8-860`

### Version 4.9.26, released 05 May 2023
{: #4.9.26_odf}

- Golang updated to `1.19.8`.
- Resolves the following CVEs: [CVE-2023-0361](https://nvd.nist.gov/vuln/detail/CVE-2023-0361){: external}, [CVE-2023-24536](https://nvd.nist.gov/vuln/detail/CVE-2023-24536){: external}, [CVE-2023-24537](https://nvd.nist.gov/vuln/detail/CVE-2023-24537){: external}, [CVE-2023-24538](https://nvd.nist.gov/vuln/detail/CVE-2023-24538){: external}.

### Version 4.9.5, released 20 May 2022
{: #4.9.5_odf}

- Support update and scaling on {{site.data.keyword.satelliteshort}}.
- Golang update.
- Updates the UBI.

### Version 4.9.4, released 13 April 2022
{: #4.9.4_odf}

UBI update.

### Version 4.9.3, released 23 March 2022
{: #4.9.3_odf}

- Updates Golang.
- Updates the UBI.

### Version 4.9.2, released 24 February 2022
{: #4.9.2_odf}

Use PVC for mon on VPC.

### Version 4.9.1, released 23 February 2022
{: #4.9.1_odf}

Updates the UBI.

### Version 4.9.0, released 11 February 2022
{: #4.9.0_odf}

Initial release.


## Version 4.8
{: #4.8_odf}

### Version 4.8.31, released 05 May 2023
{: #4.8.31_odf}

- Golang updated to `1.19.8`.
- Resolves the following CVEs: [CVE-2023-0361](https://nvd.nist.gov/vuln/detail/CVE-2023-0361){: external}, [CVE-2023-24536](https://nvd.nist.gov/vuln/detail/CVE-2023-24536){: external}, [CVE-2023-24537](https://nvd.nist.gov/vuln/detail/CVE-2023-24537){: external}, [CVE-2023-24538](https://nvd.nist.gov/vuln/detail/CVE-2023-24538){: external}.

### Version 4.8.4, released 17 January 2022
{: #4.8.4_odf}

Updates Golang version to 1.16.13.

### Version 4.8.3, released Jan 07, 2022
{: #4.8.3_odf}

- Updates UBI image.
- Adds increased logging.


### Version 4.8.2, released 03 January 2022
{: #4.8.2_odf}

- Removes MON parameters.
- Introduces local disk discovery.


### Version 4.8.1, released 17 November 2021
{: #4.8.1_odf}

- Removes {{site.data.keyword.satelliteshort}} link parameter.
- Updates Golang to 1.16.10.
- Updates the UBI.

### Version 4.8.0, released 25 October 2021
{: #4.8.0_odf}

Updates Golang to 1.16.9.

## Version 4.7
{: #4.7_odf}

### Version 4.7.14, released 25 October 2021
{: #4.7.14_odf}

Updates Golang to 1.16.9.

### Version 4.7.13, released 13 October 2021
{: #4.7.13_odf}

Adds an agent health check.


### Version 4.7.12, released 30 September 2021
{: #4.7.12_odf}

Includes an NC check fix.

### Version 4.7.11, released 29 September 2021
{: #4.7.11_odf}

- Adds NC check.
- Updates the UBI.

### Version 4.7.10, released 15 September 2021
{: #4.7.10_odf}

Adds a fix for multiple operator groups. 


### Version 4.7.9, released 06 September 2021
{: #4.7.9_odf}

- Adds agent check
- Adds enhancements to cleanup.

### Version 4.7.8, released 16 August 202
{: #4.7.8_odf}

- Updates the UBI.
- Updates Golang to 1.16.7.

### Version 4.7.7, released 27 July 2021
{: #4.7.7_odf}

- Updates the UBI.
- Updates Golang to 1.16.6.

### Version 4.7.6, released 05 July 2021
{: #4.7.6_odf}

- Updates the UBI.
