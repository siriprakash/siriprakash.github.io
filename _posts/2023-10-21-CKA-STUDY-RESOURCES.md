---
title: CKA STUDY RESOURCES
date: 2023-10-21
categories: [CKA]
tags: [studyresources]     
---
# Certified Kubernetes Administrator

### **Storage—10%**

**Understand storage classes, persistent volumes**

Official Documentation 

[https://kubernetes.io/docs/concepts/storage/storage-classes/](https://kubernetes.io/docs/concepts/storage/storage-classes/)

[https://kubernetes.io/docs/concepts/storage/persistent-volumes/](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)

Notes

****Volumes:**** 

Why do we need Volumes?

files in a container are ephemeral(lost when the container crashes or is stopped)

multiple containers are running in a pod need to share files. 

mountPath: the destination inside the Pod where the volume gets mounted to.

Types of Volumes:

1. **cephfs**: allows an existing CephFS volume to be mounted into your pod
    
    volume is preserved but unmounted when the pod is removed.
    
    volume can be pre-populated with data, and that data can be shared between pods
    
2. ****configMap:**** used to inject configuration data into pods
    
    When referencing a ConfigMap, you provide the name of the ConfigMap in the volume and customize the path to use for a specific entry in the ConfigMap.
    
3. **emptyDir:** the volume is created when the Pod is assigned to a node. It is initially empty.
    
    When a Pod is removed from a node for any reason, the data is deleted permanently.
    
    ```jsx
    apiVersion: v1
    kind: Pod
    metadata:
      name: emptydir-pod
    spec:
      containers:
      - image: alpine
        imagePullPolicy: IfNotPresent
        name: emptydir-container
        command: [    'sh', '-c', 'echo Hello! ; sleep 3600']
        volumeMounts:
        - mountPath: /demo
          name: demo-volume
      volumes:
      - name: demo-volume
        emptyDir: {}
    ```
    
4. ****hostPath:**** mounts a file or directory from the host node's filesystem into your Pod
    
    used container that needs access to node-level system components
    

**Understand volume mode, access modes and reclaim policies for volumes**

Official Documentation 

[https://kubernetes.io/docs/concepts/storage/persistent-volumes/#volume-mode](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#volume-mode)

[https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)

[https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy)

**Understand persistent volume claims primitive**

[https://kubernetes.io/docs/concepts/storage/persistent-volumes/](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)

**Know how to configure applications with persistent storage**

[https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/)

### **Troubleshooting—30%**

**Evaluate cluster and node logging**

**Understand how to monitor applications**

**Manage container stdout & stderr logs**

**Troubleshoot application failure**

**Troubleshoot cluster component failure**

**Troubleshoot networking**

### **Workloads & Scheduling—15%**

**Understand deployments and how to perform rolling update and rollbacks**

**Use ConfigMaps and Secrets to configure applications**

**Know how to scale applications**

**Understand the primitives used to create robust, self-healing, application deployments**

**Understand how resource limits can affect Pod scheduling**

**Awareness of manifest management and common templating tools**

### **Cluster Architecture, Installation & Configuration—25%**

**Manage role-based access control (RBAC)**

**Use Kubeadm to install a basic cluster**

**Manage a highly-available Kubernetes cluster**

**Provision underlying infrastructure to deploy a Kubernetes cluster**

**Perform a version upgrade on a Kubernetes cluster using Kubeadm**

**Implement etcd backup and restore**

### **Services & Networking—20%**

**Understand host networking configuration on the cluster nodes**

**Understand connectivity between Pods**

**Understand ClusterIP, NodePort, LoadBalancer service types and endpoints**

**Know how to use Ingress controllers and Ingress resources**

**Know how to configure and use CoreDNS**

**Choose an appropriate container network interface plugin**


