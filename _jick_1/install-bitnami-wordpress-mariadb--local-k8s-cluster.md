---
category:
  - "[[Lessons]]"
author:
cover:
genre:
length:
year: 2025-08-21
rating:
topics:
last: 2025-08-22
via: ""
tags:
  - references
  - lessons
created: 2025-08-22
---

## Wordpress and Mariadb on k8s cluster


## 
[[Clean uninstall of Rancher Desktop]]


Here’s a step-by-step guide to deploy **WordPress** and **MariaDB** using **Helm charts** from Docker Hub on your local **Kubernetes cluster** running via **Rancher Desktop** on **Pop!_OS 22.04 LTS**.

---

## ✅ Requirements

Make sure the following tools are installed and configured:

-  Rancher Desktop (with Kubernetes enabled)
    
-  kubectl (`kubectl version`)
    
-  Helm (`helm version`)
    
-  Internet access to pull Docker images from Docker Hub
    

---

## 🔧 Step 1: Set the Kubernetes Context

Ensure your kubectl context is pointing to Rancher Desktop’s Kubernetes:

```bash
kubectl config get-contexts
kubectl config use-context rancher-desktop
```

---

## 📂 Step 2: Create a Namespace (optional but recommended)

```bash
kubectl create namespace wordpress
```

---

## 📦 Step 3: Add the Bitnami Helm Repository

Bitnami provides well-maintained Helm charts for WordPress and MariaDB.

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
```

---

## 🐬 Step 4: Deploy MariaDB

Create a MariaDB instance using the Bitnami Helm chart. Customize passwords and storage as needed.

```bash
helm install mariadb bitnami/mariadb \
  --namespace wordpress \
  --set auth.rootPassword=secretpassword \
  --set auth.database=wordpress \
  --set auth.username=wp_user \
  --set auth.password=wp_password \
  --set primary.persistence.enabled=false
```

📌 `primary.persistence.enabled=false` disables persistent storage (useful for testing).

---

## 🌐 Step 5: Deploy WordPress

Now deploy WordPress and connect it to the MariaDB instance.

```bash
helm install wordpress bitnami/wordpress \
  --namespace wordpress \
  --set wordpressUsername=admin \
  --set wordpressPassword=adminpassword \
  --set mariadb.enabled=false \
  --set externalDatabase.host=mariadb.wordpress.svc.cluster.local \
  --set externalDatabase.user=wp_user \
  --set externalDatabase.password=wp_password \
  --set externalDatabase.database=wordpress \
  --set service.type=NodePort
```

---

## 🚀 Step 6: Verify the Deployments

Check the pods:

```bash
kubectl get pods -n wordpress
```

Check services:

```bash
kubectl get svc -n wordpress
```

---

## 🌍 Step 7: Access WordPress

Since we used `NodePort`, get the NodePort of the WordPress service:

```bash
kubectl get svc wordpress -n wordpress
```

Look for a port under `PORT(S)` like `http://127.0.0.1:<NodePort>`. Open that in your browser.

You can also port-forward as an alternative:

```bash
kubectl port-forward svc/wordpress 8080:80 -n wordpress
```

Then access WordPress at [http://localhost:8080](http://localhost:8080)

---

## 🧼 Optional: Uninstall WordPress and MariaDB

```bash
helm uninstall wordpress -n wordpress
helm uninstall mariadb -n wordpress
kubectl delete namespace wordpress
```

---

## ✅ Summary

| Component  | Tool/Command                                     |
| ---------- | ------------------------------------------------ |
| Helm Chart | Bitnami (`bitnami/wordpress`, `bitnami/mariadb`) |
| Namespace  | `wordpress`                                      |
| DB Auth    | wp_user / wp_password                            |
| WordPress  | admin / adminpassword                            |
| Access URL | via NodePort or port-forward                     |

Let me know if you want persistent storage or use Ingress!