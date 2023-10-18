# Danswer monitor

This is a simple monitoring software used to monitor Danswer pods inside a Kubernetes cluster.

![enter image description here](https://raw.githubusercontent.com/meherhendi/danswer-monitoring/main/img/grafana-screen.png)


# Prerequisite
* Deploy Danswer (https://github.com/danswer-ai/danswer/tree/main/deployment/kubernetes)
* Helm
* Kubectl


# Quick start
1- Install Prometheus:
```bash
helm install prometheus prometheus-community/prometheus
```
2- Install Grafana:
```bash
helm install grafana grafana/grafana
```
3- forward Grafana port for access on local device
```bash
kubectl port-forward service/grafana 3001:80 -n monitoring
```
4- Get Grafana password
```
kubectl get secret --namespace monitoring my-grafana -o jsonpath="{.data.admin-password}"  | base64 --decode ;  echo
```
5- Connect to Grafana using admin:""password-from-previous-step""\
6- Add Prometheus as a data source to Grafana\
7- import Grafana dashboard from "danswer-grafana-dashboard.json" file\
8- congrats, you have monitoring for the Danswer
