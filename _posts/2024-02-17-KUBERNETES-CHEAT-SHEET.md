---
title: KUBERNETES CHEAT SHEET
date: 2024-02-17
categories: [KUBERNETES,DEVNET,CKA]
tags: [studyresources]     
---

# help & basic troubleshooting commands

| kubectl - h  | help for kubectl |
| --- | --- |
| kubectl <command>  - - help  | Describe the command  |
| kubectl explain <resource> | Describe fields and structure of various resources. |
| alias k=kubectl
echo 'alias k=kubectl' >>~/.bashrc | Set an alias for kubectl command |
| kubectl logs -l name=<label name> | Get logs from pod of a label type |
| JSONPATH='{range .items[]}{@.metadata.name}:{range @.status.conditions[]}{@.type}={@.status};{end}{end}' \
&& kubectl get nodes -o jsonpath="$JSONPATH" | grep "Ready=True" | Check which nodes are ready |
| kubectl get node -o custom-columns='NODE_NAME:.metadata.name,STATUS:.status.conditions[?(@.type=="Ready")].status’ | Get ready nodes with custom columns  |
| kubectl get events --sort-by=.metadata.creationTimestamp | Get events by time stamp |
| kubectl events --types=Warning | Get warning events  |

# cluster info

| kubectl config view | Show Merged kubeconfig settings. |
| --- | --- |
| kubectl cluster-info | Display addresses of the master and services |
| kubectl get componentstatuses | Check cluster status |
| kubectl cluster-info dump | Dump current cluster state to stdout |
| kubectl config get-contexts | display list of contexts |
| kubectl config set-context --current --namespace=<ns> | save the namespace for all subsequent kubectl commands in that context. |

# creating objects

| kubectl create -f <name_of_file> | Imperative approach. tells kubectl exactly what to do. Creates a new k8s resource in the cluster |
| --- | --- |
| kubectl apply -f <name_of_file> | Declarative approach. kubectl apply uses the provided spec to create a resource if it does not exist and update, i.e., patch, it if it does. |
| kubectl replace -f <name_of_file> | Imperative approach. The kubectl replace completely replaces the existing resource with the one defined by the provided spec. |
| kubectl delete -f <name_of_file> | Delete resources from a file |

# node

| kubectl get node | To lists all nodes in the cluster. Displays NAME, STATUS, ROLES, AGE & VERSION |
| --- | --- |
| kubectl get node -o wide | To lists all nodes in the cluster. Displays NAME, STATUS, ROLES, AGE, VERSION, INTERNAL-IP, EXTERNAL-IP, OS-IMAGE, KERNEL-VERSION & CONTAINER-RUNTIME |
|  kubectl describe node <nodename> | To describe nod |
| kubectl get node <nodename> -o yaml | To get the node in yaml output format |
| kubectl get node --show-labels | To lists all nodes in the cluster with associated labels |
| kubectl get node --selector=[label_name] | To lists all nodes with certain labels |
| kubectl cordon <nodename> | To mark a node unschedulable |
| kubectl drain <nodename> - -ignore-daemonsets | To drain the node.If there are pods managed by a DaemonSet, you will need to specify --ignore-daemonsets with kubectl to successfully drain the node. |
| kubectl uncordon <nodename> | To mark a node schedulable |
| kubectl delete node <nodename> | To safely delete a node, cordon and drain first |
| kubectl edit node <nodename> | To change node values |

# pods

| kubectl get pod | To list all pods in default namespace with basic info like NAME, READY, STATUS, RESTARTS, AGE |
| --- | --- |
| kubectl get pod -o wide  | To list all pods with additional info like IP, NODE, NOMINATED NODE, READINESS GATES |
| kubectl get pod -A | To list all pods in the cluster across namespace |
| kubectl describe pod | Gives a detailed description of the pod  |
| kubectl get pod --show-labels | Lists pod with labels assigned  |
| kubectl get pod -o yaml | Pod details in yaml output format |
| kubectl get pods --field-selector status.phase=Running | Prints only Running pods  |
| kubectl run [pod_name] --image=nginx --restart=Never | Create a pod with nginx image and never restart |
| kubectl run [pod_name] --generator=run-pod/v1 --image=nginx | Create a pod with nginx image |

# resource utilization

| kubectl top node <node_name> | allows us to see the resource consumption of the pod  |
| --- | --- |
| kubectl top pod <pod_name> | allows us to see the resource consumption of the node |

# namespaces

| kubectl get ns | list namespaces |
| --- | --- |
| kubectl get ns <namespace> -o yaml | provides namespace details in yaml format  |
| kubectl describe ns <namespace>  | detailed description of a node with event details |

# **resource management**

| kubectl rollout history <resourceType>/<resourceName> | get rollout history |
| --- | --- |
| kubectl rollout undo <resourceType>/<resourceName> | undo the latest rollout |
| kubectl rollout status -w <resourceType>/<resourceName> | get rollout status |
| kubectl rollout restart <resourceType>/<resourceName> | Rolling restart of the resource  |
| kubectl set image <resourceType>/<resourceName>  <container> = image:<version> | update container image version |

# labels, taints and tolreations

| kubectl label nodes <node-name> <label> | Add label to node |
| --- | --- |
| kubectl label node <nodename> <labelname>- | Remove label from node |
| kubectl label pods <pod-name> <label-name> | Add label to a pod |
| kubectl label pod <pod-name> {key1=value1,key2=value2,key3=value3} | Add multiple labels to a pod |
| kubectl taint nodes <node-name> key1=value1:NoSchedule | Taint a node |
| kubectl taint nodes <node-name> key1- | Remove taint from a node |

# rbac

| kubectl create role NAME --verb=verb --resource=resource.group/subresource [--resource-name=resourcename]  | Create role |
| --- | --- |
| kubectl create rolebinding NAME --clusterrole=NAME|--role=NAME [--user=username] [--group=groupname] [--serviceaccount=namespace:serviceaccountname]  | Create role-binding |
| kubectl create serviceaccount NAME  | Create sa |
| kubectl create clusterrole NAME --verb=verb --resource=resource.group [--resource-name=resourcename]  | Create cluster role |
| kubectl create clusterrolebinding NAME --clusterrole=NAME [--user=username] [--group=groupname] [--serviceaccount=namespace:serviceaccountname]  | Create cluster role-binding |
