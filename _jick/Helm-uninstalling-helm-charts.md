---
categories:
  - "[[Troubleshoots]]"
author:
  - "[[Me]]"
url:
published:
topics: []
status:
created:
last:
rating:
---
# Issues
## Description
If a PV isn't deleted after a PVC is removed, it's likely because a resource is still attached, or the PV is stuck in a finalizer state. To fix this, ==first delete any pods or workloads using the PVC, then manually edit the PV to remove finalizers, and finally delete the PV and PVC==. 

## Environments

## How to reproduce - steps

```code
  395  minikube start --driver=docker
  396  helm list
  397  hel uninstall local-wp
  398  helm uninstall local-wp
  399  kubectl get pod
  400  kubectl get svc
  401  kubectl delete svc local-wp
  402  kubectl get svc
  403  kubectl get pv,pvc
  404  kubectl get pvc
  405  kubectl describe pvc data-local-wp-mariadb-0
  406  kubectl describe storageclass standard

  408  kubectl delete pvc data-local-wp-mariadb-0
  410  kubectl get pvc
  411  kubectl get pv
  412  echo "here pv still stays after deleting pvc"
  413  kubectl delete pv data-local-wp-mariadb-0
  414  kubectl get pv
  415  kubectl describe storageclass standard
  416  kubectl get pv
  417  describe pv pvc-9712dc02-3474-4ed3-9600-9b34d718b604
  418  kubectl describe pv pvc-9712dc02-3474-4ed3-9600-9b34d718b604
  419  kubectl delete pv pvc-9712dc02-3474-4ed3-9600-9b34d718b604
  420  kubectl delete pvc-c42a263a-ef18-421a-9bc1-68431d82b57b
  421  kubectl get pvc
  422  kubectl get pv
  423  minikube stop
  424  ps x
  425  kubectl get pvc
  426  minikube start
  427  kubectl get pvc
  428  kubectl get pv
  429  kubectl get pod
  430  kubectl get svc
  431  kubectl delete local-wp-wordpress
  432  kubectl delete pvc-c42a263a-ef18-421a-9bc1-68431d82b57b
  433  kubectl get pod
  434  kubectl get svc
  435  kubectl get pv
```

# Resolution steps

## 1. Delete resources using the PVC

- First, delete any pods, Deployments, or StatefulSets that are using the PVC. The PV is likely still bound to these resources, preventing its deletion.
- You can check for attached resources with [kubectl get pv <pv-name](https://www.google.com/search?q=kubectl+get+pv+%3Cpv-name&sca_esv=63c7fd65582f6674&rlz=1C1VDKB_enUS1132US1132&sxsrf=AE3TifNj0JpoPEKJir2kdJ7vqO59lYu9xQ%3A1763405300582&ei=9G0baa-eI-atptQPxNPGgAU&ved=2ahUKEwiAlvfY7PmQAxVprYkEHbkaIxAQgK4QegQIAxAC&oq=in+minikube+kubectl%2C+what+to+do+if+deleting+pvc+didn%27t+delete+pv+and+when+trying+to+delete+pv+i+get+error+deleting+pv&gs_lp=Egxnd3Mtd2l6LXNlcnAidWluIG1pbmlrdWJlIGt1YmVjdGwsIHdoYXQgdG8gZG8gaWYgZGVsZXRpbmcgcHZjIGRpZG4ndCBkZWxldGUgcHYgYW5kIHdoZW4gdHJ5aW5nIHRvIGRlbGV0ZSBwdiBpIGdldCBlcnJvciBkZWxldGluZyBwdkgAUABYAHAAeAGQAQCYAQCgAQCqAQC4AQzIAQCYAgCgAgCYAwCSBwCgBwCyBwC4BwDCBwDIBwA&sclient=gws-wiz-serp&mstk=AUtExfCdOx152Sof5ipwXu4k_Ma0jqkXJ1RoaXiySKCtQ1YRROCtBmMTrd_NrVcmK-dXpKbsqjhwArhikRHMI_PhY9cChd5d2tNcbIbf5V6LJPJFoOTCvK3MV6c4tEse6rpVy1tnLbQ5VMGLzaxgIACQIikBD3z-WLIltoc-jklBmIHv6Cfw0wiL1fLy-ybzbrX2jfdJL2Nu4vJ1FxCVm3QjkULeEj_sx70aT3oQwfbeP5Gu_C2W9AigYAf_qBAC_8bEZff4ixzZ8PA-6mCibFMbjlcbydQSYtKrXOfVjK-MMvzMk7FygISFmZx_stdeCru8GHoW2fILg8Fx9fVtV1TNYsWW9RLJ2jNQdyZ5cTMb8AOo&csui=3) or use [kubectl get pods](https://www.google.com/search?q=kubectl+get+pods&sca_esv=63c7fd65582f6674&rlz=1C1VDKB_enUS1132US1132&sxsrf=AE3TifNj0JpoPEKJir2kdJ7vqO59lYu9xQ%3A1763405300582&ei=9G0baa-eI-atptQPxNPGgAU&ved=2ahUKEwiAlvfY7PmQAxVprYkEHbkaIxAQgK4QegQIAxAD&oq=in+minikube+kubectl%2C+what+to+do+if+deleting+pvc+didn%27t+delete+pv+and+when+trying+to+delete+pv+i+get+error+deleting+pv&gs_lp=Egxnd3Mtd2l6LXNlcnAidWluIG1pbmlrdWJlIGt1YmVjdGwsIHdoYXQgdG8gZG8gaWYgZGVsZXRpbmcgcHZjIGRpZG4ndCBkZWxldGUgcHYgYW5kIHdoZW4gdHJ5aW5nIHRvIGRlbGV0ZSBwdiBpIGdldCBlcnJvciBkZWxldGluZyBwdkgAUABYAHAAeAGQAQCYAQCgAQCqAQC4AQzIAQCYAgCgAgCYAwCSBwCgBwCyBwC4BwDCBwDIBwA&sclient=gws-wiz-serp&mstk=AUtExfCdOx152Sof5ipwXu4k_Ma0jqkXJ1RoaXiySKCtQ1YRROCtBmMTrd_NrVcmK-dXpKbsqjhwArhikRHMI_PhY9cChd5d2tNcbIbf5V6LJPJFoOTCvK3MV6c4tEse6rpVy1tnLbQ5VMGLzaxgIACQIikBD3z-WLIltoc-jklBmIHv6Cfw0wiL1fLy-ybzbrX2jfdJL2Nu4vJ1FxCVm3QjkULeEj_sx70aT3oQwfbeP5Gu_C2W9AigYAf_qBAC_8bEZff4ixzZ8PA-6mCibFMbjlcbydQSYtKrXOfVjK-MMvzMk7FygISFmZx_stdeCru8GHoW2fILg8Fx9fVtV1TNYsWW9RLJ2jNQdyZ5cTMb8AOo&csui=3) to see which pods are running. 

## 2. Manually delete the PV

- If you still can't delete the PV, you'll need to manually edit it to remove the "finalizer" that's blocking the deletion.
- Get the PV's YAML definition:

```code
# to see pv paym
kubectl get pv -o yaml

pl@NYC-WI-902H3J3:~$ kubectl get pv -o yaml
apiVersion: v1
items:
- apiVersion: v1
  kind: PersistentVolume
  metadata:
    annotations:
      hostPathProvisionerIdentity: c8a39914-06fd-4c39-a3e3-71007a67bed2
      pv.kubernetes.io/provisioned-by: k8s.io/minikube-hostpath
    creationTimestamp: "2025-11-10T21:59:23Z"
    finalizers:
    - kubernetes.io/pv-protection
    name: pvc-c42a263a-ef18-421a-9bc1-68431d82b57b
    resourceVersion: "38987"
    uid: bf7cda49-6ae2-4bfb-8db8-064abe13885c
  spec:
    accessModes:
    - ReadWriteOnce
    capacity:
      storage: 10Gi
    claimRef:
      apiVersion: v1
      kind: PersistentVolumeClaim
      name: local-wp-wordpress
      namespace: default
      resourceVersion: "3318"
      uid: c42a263a-ef18-421a-9bc1-68431d82b57b
    hostPath:
      path: /tmp/hostpath-provisioner/default/local-wp-wordpress
      type: ""
    persistentVolumeReclaimPolicy: Delete
    storageClassName: standard
    volumeMode: Filesystem
  status:
    lastPhaseTransitionTime: "2025-11-17T18:25:39Z"
    phase: Released
kind: List
metadata:
  resourceVersion: ""
```
```code

# Backup origial yaml and save edits in a file
# 
kubectl edit pv pvc-c42a263a-ef18-421a-9bc1-68431d82b57b

pl@NYC-WI-902H3J3:~$ ls pv_*
pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-nofinalizers.yaml
pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-orig.yaml
pl@NYC-WI-902H3J3:~$

```
- Remove the `finalizers` section from the YAML - pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-nofinalizers.yaml
```code
apiVersion: v1
items:
- apiVersion: v1
  kind: PersistentVolume
  metadata:
    annotations:
      hostPathProvisionerIdentity: c8a39914-06fd-4c39-a3e3-71007a67bed2
      pv.kubernetes.io/provisioned-by: k8s.io/minikube-hostpath
    creationTimestamp: "2025-11-10T21:59:23Z"
    finalizers:
    - kubernetes.io/pv-protection # remove this
    name: pvc-c42a263a-ef18-421a-9bc1-68431d82b57b
    resourceVersion: "38987"
    uid: bf7cda49-6ae2-4bfb-8db8-064abe13885c
  spec:
```

- Apply the modified YAML: 
```code
kubectl apply -f pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-nofinalizers.yaml
```

- error:
```code
pl@NYC-WI-902H3J3:~$ kubectl apply -f pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-nofinalizers.yaml
Warning: resource persistentvolumes/pvc-c42a263a-ef18-421a-9bc1-68431d82b57b is missing the kubectl.kubernetes.io/last-applied-configuration annotation which is required by kubectl apply. kubectl apply should only be used on resources created declaratively by either kubectl create --save-config or kubectl apply. The missing annotation will be patched automatically.
Error from server (Conflict): error when applying patch:
{"metadata":{"annotations":{"kubectl.kubernetes.io/last-applied-configuration":"{\"apiVersion\":\"v1\",\"kind\":\"PersistentVolume\",\"metadata\":{\"annotations\":{\"hostPathProvisionerIdentity\":\"c8a39914-06fd-4c39-a3e3-71007a67bed2\",\"pv.kubernetes.io/provisioned-by\":\"k8s.io/minikube-hostpath\"},\"creationTimestamp\":\"2025-11-10T21:59:23Z\",\"finalizers\":null,\"name\":\"pvc-c42a263a-ef18-421a-9bc1-68431d82b57b\",\"resourceVersion\":\"38987\",\"uid\":\"bf7cda49-6ae2-4bfb-8db8-064abe13885c\"},\"spec\":{\"accessModes\":[\"ReadWriteOnce\"],\"capacity\":{\"storage\":\"10Gi\"},\"claimRef\":{\"apiVersion\":\"v1\",\"kind\":\"PersistentVolumeClaim\",\"name\":\"local-wp-wordpress\",\"namespace\":\"default\",\"resourceVersion\":\"3318\",\"uid\":\"c42a263a-ef18-421a-9bc1-68431d82b57b\"},\"hostPath\":{\"path\":\"/tmp/hostpath-provisioner/default/local-wp-wordpress\",\"type\":\"\"},\"persistentVolumeReclaimPolicy\":\"Delete\",\"storageClassName\":\"standard\",\"volumeMode\":\"Filesystem\"},\"status\":{\"lastPhaseTransitionTime\":\"2025-11-17T18:25:39Z\",\"phase\":\"Released\"}}\n"},"finalizers":null,"resourceVersion":"38987"}}
to:
Resource: "/v1, Resource=persistentvolumes", GroupVersionKind: "/v1, Kind=PersistentVolume"
Name: "pvc-c42a263a-ef18-421a-9bc1-68431d82b57b", Namespace: ""
for: "pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-nofinalizers.yaml": error when patching "pv_yaml-pvc-c42a263a-ef18-421a-9bc1-68431d82b57b-yaml-nofinalizers.yaml": Operation cannot be fulfilled on persistentvolumes "pvc-c42a263a-ef18-421a-9bc1-68431d82b57b": the object has been modified; please apply your changes to the latest version and try again
pl@NYC-WI-902H3J3:~$ ps x

```
- 


## 3. Delete the PVC and PV again 
After removing the finalizers, you can delete both the PVC and PV using [kubectl delete pvc <pvc-name](https://www.google.com/search?q=kubectl+delete+pvc+%3Cpvc-name&sca_esv=63c7fd65582f6674&rlz=1C1VDKB_enUS1132US1132&sxsrf=AE3TifNj0JpoPEKJir2kdJ7vqO59lYu9xQ%3A1763405300582&ei=9G0baa-eI-atptQPxNPGgAU&ved=2ahUKEwiAlvfY7PmQAxVprYkEHbkaIxAQgK4QegQIBxAB&oq=in+minikube+kubectl%2C+what+to+do+if+deleting+pvc+didn%27t+delete+pv+and+when+trying+to+delete+pv+i+get+error+deleting+pv&gs_lp=Egxnd3Mtd2l6LXNlcnAidWluIG1pbmlrdWJlIGt1YmVjdGwsIHdoYXQgdG8gZG8gaWYgZGVsZXRpbmcgcHZjIGRpZG4ndCBkZWxldGUgcHYgYW5kIHdoZW4gdHJ5aW5nIHRvIGRlbGV0ZSBwdiBpIGdldCBlcnJvciBkZWxldGluZyBwdkgAUABYAHAAeAGQAQCYAQCgAQCqAQC4AQzIAQCYAgCgAgCYAwCSBwCgBwCyBwC4BwDCBwDIBwA&sclient=gws-wiz-serp&mstk=AUtExfCdOx152Sof5ipwXu4k_Ma0jqkXJ1RoaXiySKCtQ1YRROCtBmMTrd_NrVcmK-dXpKbsqjhwArhikRHMI_PhY9cChd5d2tNcbIbf5V6LJPJFoOTCvK3MV6c4tEse6rpVy1tnLbQ5VMGLzaxgIACQIikBD3z-WLIltoc-jklBmIHv6Cfw0wiL1fLy-ybzbrX2jfdJL2Nu4vJ1FxCVm3QjkULeEj_sx70aT3oQwfbeP5Gu_C2W9AigYAf_qBAC_8bEZff4ixzZ8PA-6mCibFMbjlcbydQSYtKrXOfVjK-MMvzMk7FygISFmZx_stdeCru8GHoW2fILg8Fx9fVtV1TNYsWW9RLJ2jNQdyZ5cTMb8AOo&csui=3) and [kubectl delete pv <pv-name](https://www.google.com/search?q=kubectl+delete+pv+%3Cpv-name&sca_esv=63c7fd65582f6674&rlz=1C1VDKB_enUS1132US1132&sxsrf=AE3TifNj0JpoPEKJir2kdJ7vqO59lYu9xQ%3A1763405300582&ei=9G0baa-eI-atptQPxNPGgAU&ved=2ahUKEwiAlvfY7PmQAxVprYkEHbkaIxAQgK4QegQIBxAC&oq=in+minikube+kubectl%2C+what+to+do+if+deleting+pvc+didn%27t+delete+pv+and+when+trying+to+delete+pv+i+get+error+deleting+pv&gs_lp=Egxnd3Mtd2l6LXNlcnAidWluIG1pbmlrdWJlIGt1YmVjdGwsIHdoYXQgdG8gZG8gaWYgZGVsZXRpbmcgcHZjIGRpZG4ndCBkZWxldGUgcHYgYW5kIHdoZW4gdHJ5aW5nIHRvIGRlbGV0ZSBwdiBpIGdldCBlcnJvciBkZWxldGluZyBwdkgAUABYAHAAeAGQAQCYAQCgAQCqAQC4AQzIAQCYAgCgAgCYAwCSBwCgBwCyBwC4BwDCBwDIBwA&sclient=gws-wiz-serp&mstk=AUtExfCdOx152Sof5ipwXu4k_Ma0jqkXJ1RoaXiySKCtQ1YRROCtBmMTrd_NrVcmK-dXpKbsqjhwArhikRHMI_PhY9cChd5d2tNcbIbf5V6LJPJFoOTCvK3MV6c4tEse6rpVy1tnLbQ5VMGLzaxgIACQIikBD3z-WLIltoc-jklBmIHv6Cfw0wiL1fLy-ybzbrX2jfdJL2Nu4vJ1FxCVm3QjkULeEj_sx70aT3oQwfbeP5Gu_C2W9AigYAf_qBAC_8bEZff4ixzZ8PA-6mCibFMbjlcbydQSYtKrXOfVjK-MMvzMk7FygISFmZx_stdeCru8GHoW2fILg8Fx9fVtV1TNYsWW9RLJ2jNQdyZ5cTMb8AOo&csui=3). The PV might be in a "Released" state at this point. 

## 4. Check for issues in Minikube

- In Minikube, you may need to manually remove the volume from your Minikube node's host machine.

## 5. Clean up

- To clean up, you can use kubectl get pv | grep Released | awk '{print  \$1}' | while read -r line; do kubectl delete pv "$line"; done to delete any PVs that are in a "Released" state.
- You may also be able to use [kubectl delete pvc,pv --all -n namespace](https://www.google.com/search?q=kubectl+delete+pvc%2Cpv+--all+-n+namespace&sca_esv=63c7fd65582f6674&rlz=1C1VDKB_enUS1132US1132&sxsrf=AE3TifNj0JpoPEKJir2kdJ7vqO59lYu9xQ%3A1763405300582&ei=9G0baa-eI-atptQPxNPGgAU&ved=2ahUKEwiAlvfY7PmQAxVprYkEHbkaIxAQgK4QegQIDBAC&oq=in+minikube+kubectl%2C+what+to+do+if+deleting+pvc+didn%27t+delete+pv+and+when+trying+to+delete+pv+i+get+error+deleting+pv&gs_lp=Egxnd3Mtd2l6LXNlcnAidWluIG1pbmlrdWJlIGt1YmVjdGwsIHdoYXQgdG8gZG8gaWYgZGVsZXRpbmcgcHZjIGRpZG4ndCBkZWxldGUgcHYgYW5kIHdoZW4gdHJ5aW5nIHRvIGRlbGV0ZSBwdiBpIGdldCBlcnJvciBkZWxldGluZyBwdkgAUABYAHAAeAGQAQCYAQCgAQCqAQC4AQzIAQCYAgCgAgCYAwCSBwCgBwCyBwC4BwDCBwDIBwA&sclient=gws-wiz-serp&mstk=AUtExfCdOx152Sof5ipwXu4k_Ma0jqkXJ1RoaXiySKCtQ1YRROCtBmMTrd_NrVcmK-dXpKbsqjhwArhikRHMI_PhY9cChd5d2tNcbIbf5V6LJPJFoOTCvK3MV6c4tEse6rpVy1tnLbQ5VMGLzaxgIACQIikBD3z-WLIltoc-jklBmIHv6Cfw0wiL1fLy-ybzbrX2jfdJL2Nu4vJ1FxCVm3QjkULeEj_sx70aT3oQwfbeP5Gu_C2W9AigYAf_qBAC_8bEZff4ixzZ8PA-6mCibFMbjlcbydQSYtKrXOfVjK-MMvzMk7FygISFmZx_stdeCru8GHoW2fILg8Fx9fVtV1TNYsWW9RLJ2jNQdyZ5cTMb8AOo&csui=3) to delete all PVCs and PVs in a namespace.

```code

```

## Steps


