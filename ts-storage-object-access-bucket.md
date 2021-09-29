---

copyright: 
  years: 2014, 2021
lastupdated: "2021-09-24"

keywords: openshift, roks, rhoks, rhos

subcollection: openshift
content-type: troubleshoot

---



{{site.data.keyword.attribute-definition-list}}

# Why can't my PVC access an existing bucket?
{: #cos_access_bucket_fails}

**Infrastructure provider**:
* <img src="../images/icon-classic.png" alt="Classic infrastructure provider icon" width="15" style="width:15px; border-style: none"/> Classic
* <img src="../images/icon-vpc.png" alt="VPC infrastructure provider icon" width="15" style="width:15px; border-style: none"/> VPC


<img src="../images/icon-version-311.png" alt="Version 3.11 icon" width="30" style="width:30px; border-style: none"/> This troubleshooting topic applies only to {{site.data.keyword.openshiftshort}} clusters that run version 3.11.
{: note}




When you create the PVC, the bucket in {{site.data.keyword.cos_full_notm}} cannot be accessed. You see an error message similar to the following:
{: tsSymptoms}

```sh
Failed to provision volume with StorageClass "ibmc-s3fs-standard-regional": pvc:1b2345678b69175abc98y873e2:cannot access bucket <bucket_name>: NotFound: Not Found
```
{: screen}


You might have used the wrong storage class to access your existing bucket, or you tried to access a bucket that you did not create. You cannot access a bucket that you did not create.
{: tsCauses}


Verify your bucket details and storage class and recreate your PVC.
{: tsResolve}

1. From the [{{site.data.keyword.cloud_notm}} dashboard](https://cloud.ibm.com/){: external}, select your {{site.data.keyword.cos_full_notm}} service instance.
2. Select **Buckets**.
3. Review the **Class** and **Location** information for your existing bucket.
4. Choose the appropriate [storage class](/docs/openshift?topic=openshift-object_storage#cos_storageclass_reference).
5. Make sure that you provide the correct name of your existing bucket.





