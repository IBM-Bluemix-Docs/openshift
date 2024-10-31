---

copyright: 
  years: 2014, 2024
lastupdated: "2024-10-30"


keywords: openshift, {{site.data.keyword.openshiftlong_notm}}, kubernetes, help, network, connectivity

subcollection: openshift

content-type: troubleshoot

---


{{site.data.keyword.attribute-definition-list}}





# Why is the transport endpoint not connected?
{: #cos_transport_ts_connect}
{: support}

[Virtual Private Cloud]{: tag-vpc} [Classic infrastructure]{: tag-classic-inf}

The following steps apply to the {{site.data.keyword.cos_full_notm}} plug-in only.
{: important}


When you create a PVC, you see an error message similar to the following:
{: tsSymptoms}

```sh
Transport endpoint is not connected.
```
{: screen}


To find the cause of the issue, gather system logs by deploying an `inspectnode` pod.
{: tsCauses}


Follow the steps to gather logging information.
{: tsResolve}

1. Create a `debug-pvc.yaml` file and specify the `ibm.io/debug-level: "info"` and `ibm.io/curl-debug: "true"` annotations.
   ```yaml
   apiVersion: v1
   kind: PersistentVolumeClaim
   metadata:
      annotations:
        ibm.io/auto-create-bucket: "false"
        ibm.io/auto-delete-bucket: "false"
        ibm.io/bucket: <bucket-name> # Enter the name of your bucket.
        ibm.io/secret-name: <cos-secret-name> # Enter the name of your Kubernetes secret that contains your COS credentails
        ibm.io/debug-level: "info"
        ibm.io/curl-debug: "true"
      name: debug-pvc
      namespace: default
   spec:
     storageClassName: ibmc-s3fs-standard-perf-regional
     accessModes:
     - ReadWriteOnce
     resources:
       requests:
         storage: 10Gi
   ```
   {: codeblock}

1. Create the `debug-pvc` PVC in your cluster.
    ```sh
    oc create -f debug-pvc.yaml>
    ```
    {: pre}

1. Redeploy your app and reference the `debug-pvc`. Alternatively, you can use the following sample pod.
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: debug-pod
    spec:
      volumes:
      - name: nginx
        persistentVolumeClaim:
            claimName: cos-debug
      containers:
      - name: nginx
        image: nginx
        volumeMounts:
        - mountPath: /debug
          name: nginx
    ```
    {: codeblock}

1. Save the following DaemonSet configuration file as `inspectnode-ds.yaml`. After you deploy an app that references the PVC that you created earlier, deploy the DaemonSet when the `Transport endpoint is not connected` error occurs to gather the logs.
    ```yaml
    apiVersion: apps/v1
    kind: DaemonSet
    metadata:
        namespace: default
        name: ibm-inspectnode
        labels:
          app: ibm-inspectnode
    spec:
        selector:
          matchLabels:
              app: ibm-inspectnode
        updateStrategy:
          type: RollingUpdate
        template:
          metadata:
              labels:
                app: ibm-inspectnode
          spec:
              tolerations:
              - operator: "Exists"
              hostNetwork: true
              containers:
                - name: inspectnode
                image: alpine:latest
                command: ["/bin/sh"]
                args: ["-c", "while true; do msg=$(date); echo $msg; sleep 30; done"]
                securityContext:
                    runAsUser: 0
                volumeMounts:
                  - mountPath: /host/var/log
                    name: host-log
              volumes:
                - name: host-log
                  hostPath:
                    path: /var/log
    ```
    {: codeblock}

1. Create the DaemonSet in your cluster when the `Transport endpoint is not connected` error occurs.

    ```sh
    oc create -f ./inspectnode-ds.yaml
    ```
    {: pre}

1. Get the name of the `inspectnode` pod.

    ```sh
    oc get pods -n default -l app=ibm-inspectnode -o wide
    ```
    {: pre}

1. Copy the logs from `inspectnode` pod to your local machine. In the copy command, give your directory a name so that you can identify which node the logs are from. For example, `node-one.log`. You might also use the node IP in the directory name, for example: `10.XXX.XX.XXX.log`.

    ```sh
    oc cp <inspectnode_pod_name>:/host/var/log  ./<node_name>.log
    ```
    {: pre}

1. Review the `syslog` and the `s3fslog` for information about the `Transport endpoint` error. [Open a support ticket](/docs/openshift?topic=openshift-get-help) and share the log files that you gathered.

1. Delete the `ibm-inspectnode` DaemonSet that you deployed.

    ```sh
    oc delete daemonset ibm-inspectnode
    ```
    {: pre}


1. If the issue persists, contact support. Open a [support case](/docs/account?topic=account-using-avatar). In the case details, be sure to include any relevant log files, error messages, or command outputs.
