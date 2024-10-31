---

copyright: 
  years: 2014, 2024
lastupdated: "2024-10-30"


keywords: pvc, pending, file, storage, error

subcollection: openshift

content-type: troubleshoot

---


{{site.data.keyword.attribute-definition-list}}

# Why does my file storage PVC remain in a pending state?
{: #file_pvc_pending}
{: support}

[Virtual Private Cloud]{: tag-vpc} [Classic infrastructure]{: tag-classic-inf}


When you create a PVC and you run `oc get pvc <pvc_name>`, your PVC remains in a **Pending** state, even after waiting for some time.
{: tsSymptoms}


During the PVC creation and binding, many different tasks are executed by the file and block storage plug-in. Each task can fail and cause a different error message.
{: tsCauses}


Find the root cause by describing your PVC and reviewing the common error messages.
{: tsResolve}

1. Describe the PVC and state.

    ```sh
    oc describe pvc <pvc_name> -n <project>
    ```
    {: pre}

2. Review common error message descriptions and resolutions.

| Error message | Description | Steps to resolve |
| --- | --- | --- |
| `User doesn't have permissions to create or manage Storage` \n `Failed to find any valid softlayer credentials in configuration file` \n `Storage with the order ID %d could not be created after retrying for %d seconds.` \n `Unable to locate datacenter with name <datacenter_name>.` | The IAM API key or the IBM Cloud infrastructure API key that is stored in the `storage-secret-store` Kubernetes secret of your cluster does not have all the required permissions to provision persistent storage. | See [PVC creation fails because of missing permissions](/docs/openshift?topic=openshift-missing_permissions). |
| `Your order will exceed the maximum number of storage volumes allowed. Please contact Sales` | Every {{site.data.keyword.cloud_notm}} account is set up with a maximum number of file and block storage instances that can be created. By creating the PVC, you exceed the maximum number of storage instances. For more information about the maximum number of volumes that you can create and how to retrieve the number of volumes in your account, see the documentation for [file](/docs/FileStorage?topic=FileStorage-managinglimits) and [block](/docs/BlockStorage?topic=BlockStorage-managingstoragelimits) storage. | To create a PVC, choose from the following options. \n  - Remove any unused PVCs.  \n - Ask the {{site.data.keyword.cloud_notm}} account owner to increase your storage quota by [opening a support case](/docs/account?topic=account-using-avatar). |
| `Unable to find the exact ItemPriceIds for the specified storage` \n `Failed to place storage order with the storage provider` | The storage size and IOPS that you specified in your PVC are not supported by the storage type that you chose and can't be used with the specified storage class. | Review [Deciding on the file storage configuration](/docs/openshift?topic=openshift-file_storage#file_predefined_storageclass) and [Deciding on the block storage configuration](/docs/openshift?topic=openshift-block_storage#block_predefined_storageclass) to find supported storage sizes and IOPS for the storage class that you want to use. Correct the size and IOPS, and re-create the PVC. |
| Failed to find the datacenter name in configuration file. | The data center that you specified in your PVC does not exist. | Run `ibmcloud oc locations` to list available data centers. Correct the data center in your PVC and re-create the PVC. |
| `Failed to place storage order with the storage provider` \n `Storage with the order ID 12345 could not be created after retrying for xx seconds.` \n `Failed to do subnet authorizations for the storage 12345.` \n `Storage 12345 has ongoing active transactions and could not be completed after retrying for xx seconds.` | The storage size, IOPS, and storage type might be incompatible with the storage class that you chose, or the {{site.data.keyword.cloud_notm}} infrastructure API endpoint is currently unavailable. | Review [Deciding on the file storage configuration](/docs/openshift?topic=openshift-file_storage#file_predefined_storageclass) and [Deciding on the block storage configuration](/docs/openshift?topic=openshift-block_storage#block_predefined_storageclass) to find supported storage sizes and IOPS for the storage class and storage type that you want to use. Then, delete the PVC and re-create the PVC. |
| Failed to find the storage with storage id 12345. | You want to create a PVC for an existing storage instance by using Kubernetes static provisioning, but the storage instance that you specified could not be found. | Follow the instructions to provision existing [file storage](/docs/openshift?topic=openshift-file_storage#existing_file) or [block storage](/docs/openshift?topic=openshift-block_storage#existing_block) in your cluster and make sure to retrieve the correct information for your existing storage instance. Then, delete the PVC and re-create the PVC. |
| Storage type not provided, expected storage type is `Endurance` or `Performance`. | You created your own storage class and specified a storage type that is not supported. | Update your own storage class to specify `Endurance` or `Performance` as your storage type. To find examples for your own storage classes, see the sample storage classes for [file storage](/docs/openshift?topic=openshift-file_storage#file_custom_storageclass) and [block storage](/docs/openshift?topic=openshift-block_storage#block_custom_storageclass). | 
| `SoftLayer_Exception_User_Customer_Unauthorized: Invalid API key`  | You specified an IAM API key when a classic infrastructure API key is required. Or, the classic infrastructure API key you specified does not exist.   |  Follow the instructions in [Invalid API key](/docs/openshift?topic=openshift-ts-perms-creds#invalid_apikey)|
{: caption="Storage error messages" caption-side="bottom"}
