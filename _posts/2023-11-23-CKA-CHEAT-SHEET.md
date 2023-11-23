---
title: CKA STUDY RESOURCES
date: 2023-11-23
categories: [CKA]
tags: [studyresources]     
---
# CKA Cheat Sheet

################################# KUBERNETES CHEAT SHEET #############################################

########### VIEWING RESOURCE INFORMATION ###############

### View resource information

|  |  |
| --- | --- |
|  | kubectl get node |
|  | kubectl get node -o wide |
|  |  kubectl describe node <nodename> |
|  | kubectl get node <nodename> -o yaml |
|  | kubectl get node  - - show-labels |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  | kubectl top node <node_name> |
|  | kubectl top pod <pod_name> |
|  |  |

kubectl get no
kubectl get no -o wide
kubectl describe no
kubectl get no -o yaml
kubectl get node --selector=[label_name]
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}'

# pods

kubectl get po
kubectl get po -o wide
kubectl describe po
kubectl get po --show-labels
kubectl get po -l app=nginx
kubectl get po -o yaml
kubectl get pod [pod_name] -o yaml --export
kubectl get pod [pod_name] -o yaml --export > nameoffile.yaml
kubectl get pods --field-selector status.phase=Running

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

$ kubectl get events
$ kubectl get events -n kube-system
$ kubectl get events -w

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

