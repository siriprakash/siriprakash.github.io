---
title: CKA CHEAT SHEET
date: 2023-11-23
categories: [CKA]
tags: [studyresources]     
---
# CKA Cheat Sheet

Owner: siri prakash
URL: https://kubernetes.io/docs/reference/kubectl/quick-reference/

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
| kubectl edit node <nodename> |  |

# pods

| kubectl get pod |  |
| --- | --- |
| kubectl get pod -o wide  |  |
| kubectl get pod -A |  |
| kubectl describe pod |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |

kubectl get po
kubectl get po -o wide

kubectl get po --show-labels
kubectl get po -l app=nginx
kubectl get po -o yaml
kubectl get pod [pod_name] -o yaml --export
kubectl get pod [pod_name] -o yaml --export > nameoffile.yaml
kubectl get pods --field-selector status.phase=Running

# resource utilization

| kubectl top node <node_name> |  |
| --- | --- |
| kubectl top pod <pod_name> |  |

# namespaces

|  |  |  |
| --- | --- | --- |
|  | kubectl get ns |  |
|  |  |  |

kubectl get ns
kubectl get ns -o yaml
kubectl describe ns

# deployments

kubectl get deploy
kubectl describe deploy
kubectl get deploy -o wide
kubectl get deploy -o yaml

# services

kubectl get svc
kubectl describe svc
kubectl get svc -o wide
kubectl get svc -o yaml
kubectl get svc --show-labels

# daemonsets

kubectl get ds
kubectl get ds --all-namespaces
kubectl describe ds [daemonset_name] -n [namespace_name]
kubectl get ds [ds_name] -n [ns_name] -o yaml

# events

kubectl get events
kubectl get events -n kube-system
kubectl get events -w

# logs

kubectl logs [pod_name]
kubectl logs --since=1h [pod_name]
kubectl logs --tail=20 [pod_name]
kubectl logs -f -c [container_name] [pod_name]
kubectl logs [pod_name] > pod.log

# service accounts

kubectl get sa
kubectl get sa -o yaml
kubectl get serviceaccounts default -o yaml > ./sa.yaml
kubectl replace serviceaccount default -f ./sa.yaml

# replicasets

kubectl get rs
kubectl describe rs
kubectl get rs -o wide
kubectl get rs -o yaml

# roles

kubectl get roles --all-namespaces
kubectl get roles --all-namespaces -o yaml

# secrets

kubectl get secrets
kubectl get secrets --all-namespaces
kubectl get secrets -o yaml

# configmaps

kubectl get configmaps
kubectl get configmaps --all-namespaces
kubectl get configmaps --all-namespaces -o yaml

# ingress

kubectl get ing
kubectl get ing --all-namespaces

# persistentvolumes

kubectl get pv
kubectl describe pv

# persistentvolumeclaims

kubectl get pv
kubectl describe pvc

# storageclass

kubectl get sc
kubectl get sc -o yaml

# multiple resources

kubectl get svc, po
kubectl get deploy, no
kubectl get all
kubectl get all --all-namespaces

########### CHANGING RESOURCE ATTRIBUTES ###############

# taint

kubectl taint [node_name] [taint_name]

# labels

kubectl label [node_name] disktype=ssd
kubrectl label [pod_name] env=prod

# nodes/pods

kubectl delete node [node_name]
kubectl delete pod [pod_name]
kubectl edit node [node_name]
kubectl edit pod [pod_name]

# deployments/namespaces

kubectl edit deploy [deploy_name]
kubectl delete deploy [deploy_name]
kubectl expose deploy [deploy_name] --port=80 --type=NodePort
kubectl scale deploy [deploy_name] --replicas=5
kubectl delete ns
kubectl edit ns [ns_name]

# services

kubectl edit svc [svc_name]
kubectl delete svc [svc_name]

# daemonsets

kubectl edit ds [ds_name] -n kube-system
kubectl delete ds [ds_name]

# serviceaccounts

kubectl edit sa [sa_name]
kubectl delete sa [sa_name]

# annotate

kubectl annotate po [pod_name] [annotation]
kubectl annotate no [node_name]

########### ADDING RESOURCES ###############

# creating a pod

kubectl create -f [name_of_file]
kubectl apply -f [name_of_file]
kubectl run [pod_name] --image=nginx --restart=Never
kubectl run [pod_name] --generator=run-pod/v1 --image=nginx
kubectl run [pod_name] --image=nginx --restart=Never

# creating a service

kubectl create svc nodeport [svc_name] --tcp=8080:80

# creating a deployment

kubectl create -f [name_of_file]
kubectl apply -f [name_of_file]
kubectl create deploy [deploy_name] --image=nginx

# interactive pod

kubectl run [pod_name] --image=busybox --rm -it --restart=Never -- sh

# output YAML to a file

kubectl create deploy [deploy_name] --image=nginx --dry-run -o yaml > deploy.yaml
kubectl get po [pod_name] -o yaml --export > pod.yaml

# getting help

kubectl -h
kubectl create -h
kubectl run -h
kubectl explain deploy.spec

# API calls

kubectl get --raw /apis/metrics.k8s.io/

# cluster info

kubectl config
kubectl cluster-info
kubectl get componentstatuses
