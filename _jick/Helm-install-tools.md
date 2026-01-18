---
categories:
  - "[[Lessons]]"
tags:
  - lesson
  - udemy
author: []
url: ""
topics:
  - "[[Helm]]"
  - "[[Kubernetes]]"
created: 2025-11-14
title: "Helm: Install docker minikube kubectl"
last: 2025-11-14
subject: "Helm: Install docker minikube kubectl"
---
# Source
Udemy  on [[Helm]] - Helm: The Definitive Guide from Beginner to Master

You will learn how to set up the following tools on your computer:
- docker
- minikube
- kubectl

# docker - kubectl - helm

```code

install-docker-wsl-ubuntu-env.sh

#!/bin/bash
#
# Install Docker within your Ubuntu WSL environment, as it will serve as the Minikube driver.
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker $USER
newgrp docker # Apply group changes or restart your terminal
#
# Kubectl is the command-line tool for interacting with Kubernetes clusters, including Minikube.
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
#
# Installl minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
#
# Start minikube
# minikube start --driver=docker
#
# Get Helm and install
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
$ chmod 700 get_helm.sh
$ ./get_helm.sh
```



# wordpress - local-wp-3 - version=27.1.7

- run this for a new install where the passwords are set
```code
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ ./install-helm-setpwds-local-wp-3.sh
I1118 17:10:04.834750   46301 warnings.go:110] "Warning: spec.SessionAffinity is ignored for headless services"
NAME: local-wp-3
LAST DEPLOYED: Tue Nov 18 17:10:04 2025
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: wordpress
CHART VERSION: 27.1.7
APP VERSION: 6.8.3

⚠ WARNING: Since August 28th, 2025, only a limited subset of images/charts are available for free.
    Subscribe to Bitnami Secure Images to receive continued support and security updates.
    More info at https://bitnami.com and https://github.com/bitnami/containers/issues/83267

** Please be patient while the chart is being deployed **

Your WordPress site can be accessed through the following DNS name from within your cluster:

    local-wp-3-wordpress.default.svc.cluster.local (port 80)

To access your WordPress site from outside the cluster follow the steps below:

1. Get the WordPress URL by running these commands:

  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        Watch the status with: 'kubectl get svc --namespace default -w local-wp-3-wordpress'

   export SERVICE_IP=$(kubectl get svc --namespace default local-wp-3-wordpress --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
   echo "WordPress URL: http://$SERVICE_IP/"
   echo "WordPress Admin URL: http://$SERVICE_IP/admin"

2. Open a browser and access WordPress using the obtained URL.

3. Login with the following credentials below to see your blog:

  echo Username: user
  echo Password: $(kubectl get secret --namespace default local-wp-3-wordpress -o jsonpath="{.data.wordpress-password}" | base64 -d)
WARNING: Rolling tag detected (bitnami/wordpress:latest), please note that it is strongly recommended to avoid using rolling tags in a production environment.
+info https://techdocs.broadcom.com/us/en/vmware-tanzu/application-catalog/tanzu-application-catalog/services/tac-doc/apps-tutorials-understand-rolling-tags-containers-index.html
WARNING: Rolling tag detected (bitnami/apache-exporter:latest), please note that it is strongly recommended to avoid using rolling tags in a production environment.
+info https://techdocs.broadcom.com/us/en/vmware-tanzu/application-catalog/tanzu-application-catalog/services/tac-doc/apps-tutorials-understand-rolling-tags-containers-index.html
WARNING: Rolling tag detected (bitnami/os-shell:latest), please note that it is strongly recommended to avoid using rolling tags in a production environment.
+info https://techdocs.broadcom.com/us/en/vmware-tanzu/application-catalog/tanzu-application-catalog/services/tac-doc/apps-tutorials-understand-rolling-tags-containers-index.html

WARNING: There are "resources" sections in the chart not set. Using "resourcesPreset" is not recommended for production. For production installations, please set the following values according to your workload needs:
  - resources
+info https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ echo "local-wp-3 a new wp chart installed via script. so you cant set password after installing. you need to do it at time of install"
local-wp-3 a new wp chart installed via script. so you cant set password after installing. you need to do it at time of install
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl get secret local-wp-3-mariadb -o jsonpath='{.data.mariadb-password}' | base64 -d
myuserpasswordpl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl logs
error: expected 'logs [-f] [-p] (POD | TYPE/NAME) [-c CONTAINER]'.
POD or TYPE/NAME is a required argument for the logs command
See 'kubectl logs -h' for help and examples
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl logs local-wp-3
error: error from server (NotFound): pods "local-wp-3" not found in namespace "default"
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl get pod
NAME                                    READY   STATUS             RESTARTS         AGE
local-wp-2-mariadb-0                    1/1     Running            1 (63m ago)      24h
local-wp-2-wordpress-5ccdd7b7db-zk24b   1/1     Running            1 (63m ago)      24h
local-wp-3-mariadb-0                    1/1     Running            0                2m49s
local-wp-3-wordpress-69bd6dbbbd-vzgs2   1/1     Running            0                2m49s
local-wp-mariadb-0                      0/1     CrashLoopBackOff   202 (119s ago)   25h
local-wp-wordpress-c76c778fc-4rmmr      0/1     Running            1 (63m ago)      25h
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl local-wp-3-wordpress-69bd6dbbbd-vzgs2
error: unknown command "local-wp-3-wordpress-69bd6dbbbd-vzgs2" for "kubectl"
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl get pod local-wp-3-wordpress-69bd6dbbbd-vzgs2
NAME                                    READY   STATUS    RESTARTS   AGE
local-wp-3-wordpress-69bd6dbbbd-vzgs2   1/1     Running   0          5m12s
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl logs local-wp-3-wordpress-69bd6dbbbd-vzgs2
Defaulted container "wordpress" out of: wordpress, prepare-base-dir (init)
wordpress 22:10:10.74 INFO  ==>
wordpress 22:10:10.79 INFO  ==> Welcome to the Bitnami wordpress container
wordpress 22:10:10.79 INFO  ==> Subscribe to project updates by watching https://github.com/bitnami/containers
wordpress 22:10:10.79 INFO  ==> NOTICE: Starting August 28th, 2025, only a limited subset of images/charts will remain available for free. Backup will be available for some time at the 'Bitnami Legacy' repository. More info at https://github.com/bitnami/containers/issues/83267
wordpress 22:10:10.79 INFO  ==>
wordpress 22:10:10.80 INFO  ==> ** Starting WordPress setup **
wordpress 22:10:10.82 WARN  ==> The Apache configuration file '/opt/bitnami/apache/conf/httpd.conf' is not writable. Configurations based on environment variables will not be applied.
wordpress 22:10:10.95 INFO  ==> Generating sample certificates
Certificate request self-signature ok
subject=CN = example.com
realpath: /bitnami/apache/conf: No such file or directory
wordpress 22:10:15.51 INFO  ==> Configuring the HTTP port
wordpress 22:10:15.52 INFO  ==> Configuring the HTTPS port
wordpress 22:10:15.53 INFO  ==> Configuring Apache ServerTokens directive
wordpress 22:10:15.62 INFO  ==> Configuring PHP options
wordpress 22:10:15.69 INFO  ==> Setting PHP expose_php option
wordpress 22:10:15.71 INFO  ==> Setting PHP output_buffering option
wordpress 22:10:15.80 INFO  ==> Validating settings in MYSQL_CLIENT_* env vars
wordpress 22:10:16.00 WARN  ==> You set the environment variable ALLOW_EMPTY_PASSWORD=yes. For safety reasons, do not use this flag in a production environment.
wordpress 22:10:16.51 INFO  ==> Ensuring WordPress directories exist
wordpress 22:10:16.51 INFO  ==> Trying to connect to the database server
wordpress 22:10:46.91 INFO  ==> Configuring WordPress with settings provided via environment variables
wordpress 22:10:50.33 INFO  ==> Installing WordPress
wordpress 22:10:57.41 INFO  ==> Persisting WordPress installation
wordpress 22:10:57.93 INFO  ==> ** WordPress setup finished! **

wordpress 22:10:58.01 INFO  ==> ** Starting Apache **
[Tue Nov 18 22:10:58.205856 2025] [ssl:notice] [pid 1:tid 1] AH01884: OpenSSL has FIPS mode enabled
[Tue Nov 18 22:10:58.301420 2025] [ssl:notice] [pid 1:tid 1] AH01884: OpenSSL has FIPS mode enabled
[Tue Nov 18 22:10:58.395403 2025] [mpm_prefork:notice] [pid 1:tid 1] AH00163: Apache/2.4.65 (Unix) OpenSSL/3.0.18 configured -- resuming normal operations
[Tue Nov 18 22:10:58.395471 2025] [core:notice] [pid 1:tid 1] AH00094: Command line: '/opt/bitnami/apache/bin/httpd -f /opt/bitnami/apache/conf/httpd.conf -D FOREGROUND'
10.244.0.1 - - [18/Nov/2025:22:11:01 +0000] "GET /wp-login.php HTTP/1.1" 200 4455
10.244.0.1 - - [18/Nov/2025:22:11:11 +0000] "GET /wp-login.php HTTP/1.1" 200 4455
```




```code
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl get secret local-wp-3-mariadb -o jsonpath='{.data.mariadb-password}' | base64 -d
myuserpasswordpl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ kubectl get secret local-wp-3-mariadb -o jsonpath='{.data.mariadb-root-password}' | base64 -d
myawsomepasswordpl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$
```
# wordpress - local-wp-2 - version=27.1.7

```code
404  echo "reinstall wordpress diff chart version 27.1.7"
  405  #helm install my-wordpress bitnami/wordpress --version 27.1.7
  406  helm repo add bitnami https://charts.bitnami.com/bitnami
  407  helm repo update
  408  helm repo list
  409  echo "browser: https://repo.broadcom.com/bitnami-files/index.yaml/index.yaml"
  410  help search repo wordpress
  411  help repo search wordpress
  412  helm repo search wordpress
  413  helm search repo wordpress
  414  helm search repo prometheus
  415  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  416  helm repo list
  417  helm repo list --max-col-width=20
  418  helm repo list --max-col-width 20
  419  helm search repo prometheus --max-col-width 20
  420  helm show chart bitnami/wordpress
  421  helm search repo cms
  422  helm search repo wordpress --version
  423  helm search repo wordpress --versions
  424  helm search repo wordpress --versions | less
  425  helm show readme bitnami/wordpress
  426  helm show values bitnami/wordpress
  427  helm --help
  428  helm repo upate
  429  helm repo update
  430  get pod
  431  echo "install wordpress"
  432  helm repo list
  433  kubectl version
  434  kubectl config current-context
  435  helm search repo wordpress
  436  helm install local-wp bitnami/wordpress --version=27.1.7
  437  helm install local-wp-2 bitnami/wordpress --version=27.1.7
  438  kubectl get pod
  439  kubectl stop pod local-wp-wordpress-c76c778fc-4rmmr
  440  kubectl help
  441  kubectl delete help
  442  kubectl delete --help
  443  kubectl get pod
  444  kubectl get svc
  445  kubectl get secret
  446  kubectl get pod
  447  kubectl describe pod local-wp-wordpress-c76c778fc-4rmmr
  448  kubectl get deploy
  449  kubectl expose deploy local-wp-2-wordpress --type=NodePort
  450  kubectl expose deploy local-wp-2-wordpress --type=NodePort --name=local-wp-2
  451  kubectl get svc
  452  minikube service local-wp-2
  453  ls
  454  cd helm-fbte/
  455  ls -l
  456  vi install-helm-local-wp-2.sh
  457  history
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$
```

# wordpress - local-wp - version=27.1.8

```code
#/bin/bash

helm install local-wp bitnami/wordpress --version=27.1.8 --set "mariadb.auth.rootPassword=myawesomepassword" -- set"mariadb.auth.password=myuserpassword"
# Retrieve used commands - WSL Ubuntu on Windows 11
#
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ history | egrep 'helm|kubectl|minikube|docker' > helm-commands-history.txt

   10  docker run -d -p 80:8080 swaggerapi/swagger-editor
  108  cd k8s-minikube/
  110  vi intall-docker-ubuntu-wsl-env.sh
  111  helm get notes local-wp | grep VERSION
  113  cd /mnt/c/pjs/k8s-minikube/
  115  helm install local-wp bitnami/wordpress --version=27.1.8         -- set "mariadb.auth.roorPassword=myawesomepassword"         -- set "mariadb.auth.password=myuserpassword"
  116  helm install local-wp bitnami/wordpress --version=27.1.8         -- set "mariadb.auth.roorPassword=myawesomepassword"         -- set "mariadb.auth.password=myuserpassword"
  117  helm install local-wp bitnami/wordpress --version=27.1.8         -- set "mariadb.auth.roorPassword=myawesomepassword"         -- set "mariadb.auth.password=myuserpassword"
  119  helm install local-wp bitnami/wordpress --version=27.1.8 -- set "mariadb.auth.rootPassword=myawesomepassword" -- set "mariadb.auth.password=myuserpassword"
  120  kubectl get secret local-wp-wordpress -o jsonpath='{.data.wordpress-password}' | base64 -d
  121  helm show values
  122  helm show values bitnami/wordpress
  125  helm get values local-wp
  126  helm get values local-wp --all
  127  helm get metadata local-wp
  128  kubectl pod --watch
  129  kubectl get pod --watch
  130  kubectl get secrets
  131  kubectl get secret local-wp-mariadb
  132  kubectl describe secret local-wp-mariadb
  142  mkdir helm-course
  143  cd helm-course/
  145  cd /mnt/c/pjs/k8s-minikube/
  147  kubectl get secret local-wp-mariadb
  148  kubectl get pod --watch
  149  kubectl describe secret local-wp-mariadb
  150  history | grep kubectl
  151  helm get notes
  152  helm get meta-data local-wp
  153  helm -?
  154  helm help
  155  kubectl help
  156  history | grep helm
  157  helm get meta-data local-wp
  158  kubectl
  159  kubectl get pos -A
  160  kubectl get pod -A
  162  kubectl describe secret local-wp-mariadb
  163  helm help
  164  helm list
  165  history | grep 'helm install
  166  history | grep 'helm install'
  167  history | grep helm
  170  kubectl config current-context
  171  helm search repo wordpress
  172  helm get notes
  173  helm get notes wordpress
  174  history | grep helm
  175  helm get notes
  176  helm get notes local-wp
  178  vi helm-install-local-wp.sh
  182  cd k8s-minikube/
  184  vi intall-docker-ubuntu-wsl-env.sh 
  185  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
  186  chmod +x kubectl
  187  sudo mv kubectl /usr/local/bin/
  188  vi intall-docker-ubuntu-wsl-env.sh 
  189  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  190  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  191  vi intall-docker-ubuntu-wsl-env.sh 
  192  minikube start --driver=docker
  193  minikube status
  194  kubectl version
  195  kubectl get pod -a
  196  kubectl get pod -A
  197  vi intall-docker-ubuntu-wsl-env.sh 
  198  $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  199  $ chmod 700 get_helm.sh
  200  $ ./get_helm.sh
  202  $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  203  curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  205  $ chmod 700 get_helm.sh
  206  chmod 700 get_helm.sh
  207  $ ./get_helm.sh
  208  ./get_helm.sh
  209  vi intall-docker-ubuntu-wsl-env.sh 
  210  helm version
  211  helm repo add bitnami https://charts.bitnami.com/bitnami
  212  helm repo update
  213  helm search repo wordpress
  214  helm search repo prometheus
  215  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  216  helm search repo prometheus
  217  helm repo list
  218  helm search repo prometheus
  219  helm search repo prometheus --max-col-width 20
  221  helm show chart bitnami/wordpress
  222  helm show chart bitnami/wordpress --versions
  223  helm serch repo wordpress --versions
  224  helm search repo wordpress
  225  helm search repo wordpress --versions
  226  helm search repo cms
  227  helm serch repo wordpress --versions
  228  helm serch repo bitnami/wordpress
  229  helm show repo bitnami/wordpress
  230  helm show bitnami/wordpress
  231  helm show chart bitnami/wordpress
  232  helm show readme bitnami/wordpress
  233  helm show values bitnami/wordpress
  234  helm --help
  235  helm repo --help
  236  helm repo update
  237  helm repo list
  238  kubectl version
  239  kubectl config current-context
  240  helm search repo wordpress
  241  helm install --help
  242  helm search repo wordpress
  243  helm install local-wp bitnami/wordpress --version=27.1.8
  245  kubectl get pod
  246  kubectl get svc
  247  kubectl get secret
  248  kubectl describe secret local-wp-wordpress
  249  kubectl describe secret sh.helm.release.v1.local-wp.v1
  250  kubectl get pod
  251  kubectl describe pod local-wp-wordpress-c76c778fc-nvjgq
  252  kubectl get deploy
  253  kubectl expose deploy local-wp-wordpress --type=NodePort
  254  kubectl expose deploy local-wp-wordpress --type=NodePort --name=local-wp
  255  kubectl get svc
  256  minikube service local-wp
  259  ls -l intall-docker-ubuntu-wsl-env.sh
  260  cd /mnt/c/pjs/k8s-minikube/
  261  ls -l intall-docker-ubuntu-wsl-env.sh
  262  cat intall-docker-ubuntu-wsl-env.sh
  263  minikube start --driver=docker
  288  ls helm-course/
  289  mv helm-course/ repos/
  305  history | egrep 'helm|kubectl'
  306  history | egrep 'minikube|docker'
  308  ls -l /mnt/c/pjs/k8s-minikube/
  313  ls -l helm-course/
  314  mkdir helm-fbte
  315  cp -p /mnt/c/pjs/k8s-minikube/ helm-fbte/
  316  cd helm-
  317  rmdir helm-course/
  318  cd helm-fbte/
  320  cp -p /mnt/c/pjs/k8s-minikube/* helm-fbte/
  321  cp -p /mnt/c/pjs/k8s-minikube/* .
  323  history | egrep 'helm|kubectl|minikube|docker'
  324  history | egrep 'helm|kubectl|minikube|docker' > helm-commands-history.txt

pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$
```

```code
# Retrieve used commands - WSL Ubuntu on Windows 11
#
pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$ history | egrep 'helm|kubectl|minikube|docker' > helm-commands-history.txt

   10  docker run -d -p 80:8080 swaggerapi/swagger-editor
  108  cd k8s-minikube/
  110  vi intall-docker-ubuntu-wsl-env.sh
  111  helm get notes local-wp | grep VERSION
  113  cd /mnt/c/pjs/k8s-minikube/
  115  helm install local-wp bitnami/wordpress --version=27.1.8         -- set "mariadb.auth.roorPassword=myawesomepassword"         -- set "mariadb.auth.password=myuserpassword"
  116  helm install local-wp bitnami/wordpress --version=27.1.8         -- set "mariadb.auth.roorPassword=myawesomepassword"         -- set "mariadb.auth.password=myuserpassword"
  117  helm install local-wp bitnami/wordpress --version=27.1.8         -- set "mariadb.auth.roorPassword=myawesomepassword"         -- set "mariadb.auth.password=myuserpassword"
  119  helm install local-wp bitnami/wordpress --version=27.1.8 -- set "mariadb.auth.rootPassword=myawesomepassword" -- set "mariadb.auth.password=myuserpassword"
  120  kubectl get secret local-wp-wordpress -o jsonpath='{.data.wordpress-password}' | base64 -d
  121  helm show values
  122  helm show values bitnami/wordpress
  125  helm get values local-wp
  126  helm get values local-wp --all
  127  helm get metadata local-wp
  128  kubectl pod --watch
  129  kubectl get pod --watch
  130  kubectl get secrets
  131  kubectl get secret local-wp-mariadb
  132  kubectl describe secret local-wp-mariadb
  142  mkdir helm-course
  143  cd helm-course/
  145  cd /mnt/c/pjs/k8s-minikube/
  147  kubectl get secret local-wp-mariadb
  148  kubectl get pod --watch
  149  kubectl describe secret local-wp-mariadb
  150  history | grep kubectl
  151  helm get notes
  152  helm get meta-data local-wp
  153  helm -?
  154  helm help
  155  kubectl help
  156  history | grep helm
  157  helm get meta-data local-wp
  158  kubectl
  159  kubectl get pos -A
  160  kubectl get pod -A
  162  kubectl describe secret local-wp-mariadb
  163  helm help
  164  helm list
  165  history | grep 'helm install
  166  history | grep 'helm install'
  167  history | grep helm
  170  kubectl config current-context
  171  helm search repo wordpress
  172  helm get notes
  173  helm get notes wordpress
  174  history | grep helm
  175  helm get notes
  176  helm get notes local-wp
  178  vi helm-install-local-wp.sh
  182  cd k8s-minikube/
  184  vi intall-docker-ubuntu-wsl-env.sh 
  185  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
  186  chmod +x kubectl
  187  sudo mv kubectl /usr/local/bin/
  188  vi intall-docker-ubuntu-wsl-env.sh 
  189  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  190  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  191  vi intall-docker-ubuntu-wsl-env.sh 
  192  minikube start --driver=docker
  193  minikube status
  194  kubectl version
  195  kubectl get pod -a
  196  kubectl get pod -A
  197  vi intall-docker-ubuntu-wsl-env.sh 
  198  $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  199  $ chmod 700 get_helm.sh
  200  $ ./get_helm.sh
  202  $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  203  curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  205  $ chmod 700 get_helm.sh
  206  chmod 700 get_helm.sh
  207  $ ./get_helm.sh
  208  ./get_helm.sh
  209  vi intall-docker-ubuntu-wsl-env.sh 
  210  helm version
  211  helm repo add bitnami https://charts.bitnami.com/bitnami
  212  helm repo update
  213  helm search repo wordpress
  214  helm search repo prometheus
  215  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  216  helm search repo prometheus
  217  helm repo list
  218  helm search repo prometheus
  219  helm search repo prometheus --max-col-width 20
  221  helm show chart bitnami/wordpress
  222  helm show chart bitnami/wordpress --versions
  223  helm serch repo wordpress --versions
  224  helm search repo wordpress
  225  helm search repo wordpress --versions
  226  helm search repo cms
  227  helm serch repo wordpress --versions
  228  helm serch repo bitnami/wordpress
  229  helm show repo bitnami/wordpress
  230  helm show bitnami/wordpress
  231  helm show chart bitnami/wordpress
  232  helm show readme bitnami/wordpress
  233  helm show values bitnami/wordpress
  234  helm --help
  235  helm repo --help
  236  helm repo update
  237  helm repo list
  238  kubectl version
  239  kubectl config current-context
  240  helm search repo wordpress
  241  helm install --help
  242  helm search repo wordpress
  243  helm install local-wp bitnami/wordpress --version=27.1.8
  245  kubectl get pod
  246  kubectl get svc
  247  kubectl get secret
  248  kubectl describe secret local-wp-wordpress
  249  kubectl describe secret sh.helm.release.v1.local-wp.v1
  250  kubectl get pod
  251  kubectl describe pod local-wp-wordpress-c76c778fc-nvjgq
  252  kubectl get deploy
  253  kubectl expose deploy local-wp-wordpress --type=NodePort
  254  kubectl expose deploy local-wp-wordpress --type=NodePort --name=local-wp
  255  kubectl get svc
  256  minikube service local-wp
  259  ls -l intall-docker-ubuntu-wsl-env.sh
  260  cd /mnt/c/pjs/k8s-minikube/
  261  ls -l intall-docker-ubuntu-wsl-env.sh
  262  cat intall-docker-ubuntu-wsl-env.sh
  263  minikube start --driver=docker
  288  ls helm-course/
  289  mv helm-course/ repos/
  305  history | egrep 'helm|kubectl'
  306  history | egrep 'minikube|docker'
  308  ls -l /mnt/c/pjs/k8s-minikube/
  313  ls -l helm-course/
  314  mkdir helm-fbte
  315  cp -p /mnt/c/pjs/k8s-minikube/ helm-fbte/
  316  cd helm-
  317  rmdir helm-course/
  318  cd helm-fbte/
  320  cp -p /mnt/c/pjs/k8s-minikube/* helm-fbte/
  321  cp -p /mnt/c/pjs/k8s-minikube/* .
  323  history | egrep 'helm|kubectl|minikube|docker'
  324  history | egrep 'helm|kubectl|minikube|docker' > helm-commands-history.txt

pl@NYC-WI-902H3J3:~/pjs/repos/helm-fbte$
```




# Uninstall local-wp-2 and reinstall

```code
#uninstall
  633  help uninstall local-wp-2
# DON"T delete pv and pvc..
  635  kubectl get pod
  636  kubectl get deploy
  637  kubectl get secrets
  638  kubectl get pv,pvc
  639  vi install-helm-setpwds-local-wp-2.sh
  640  ./install-helm-setpwds-local-wp-2.sh
  641  kubectl get pod
  642  kubectl logs local-wp-2-wordpress-5ccdd7b7db-ftcwv

# Reinstall


```