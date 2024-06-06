# **EFK STACK ELASTICSEARCH FLUENTD KIBANA**

### Description:

​    The most popular centralized logging solution is the Elasticsearch, Fluentd, and Kibana (EFK) stack.
​    When running multiple services and applications on a Kubernetes cluster, a centralized, cluster-level logging stack can help you quickly sort through and analyze the heavy volume of log data produced by your Pods.

### Architecture:

Fluentd collects, transform, and ship log data to the Elasticsearch
Elasticsearch is a real-time, distributed, and scalable search engine
Kibana is a powerful data visualization frontend and dashboard for Elasticsearch



![](/home/niveus/Pictures/0_PzfG1ZvHdz3S6lYV.png)

### Prerequisites:

​    Before you begin with this guide, ensure you have the following available to you:

​    A Kubernetes 1.10+ cluster with role-based access control (RBAC) enabled

​    Ensure your cluster has enough resources available to roll out the EFK stack, and if not scale your cluster by adding worker nodes. We’ll be deploying a 1-Pod Elasticsearch cluster (you can scale it up to 3 if necessary), as well as a single Kibana Pod. Every worker node will also run a Fluentd Pod. The cluster in this guide consists of 3 worker nodes and a managed control plane.

​    The kubectl and Helm command-line tool installed on your local machine, configured to connect to your cluster.

### **Installation steps:**

Add helm Repo:
$ helm repo add efk https://sachinniveus.github.io/observability/

Create a namespace
$ kubectl create ns logging

Install the stack
$ helm install efk efk/efk -n logging --set kibana.ingress.hosts=hostname

### Accessing the Kibana:

    - Use the subdomain name configured or use the svc command to get the public IP address 
          http://<public-Ip:5601> or the https://subdomain-name.com/kibana