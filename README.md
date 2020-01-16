# opa-demo
# OPA template
OPA (**OPA-Istio**) that allows you to enforce OPA policies at the Istio Proxy layer.

  
## Table of contents
1. [Getting Started](#Getting Started)
2. [Configuring](#Configuring)
3. [Running](#Running)
4. [Example](#Example)

## Getting Started
Requirements -
To run this example you will need **minikube**, **kubectl**, **Docker**, **istio**.

## Configuring
To get case class objects from Kafka topic will need to make deserilaizer 


## Running
Steps to run this templete-
1> Start minikube
**minikube start --vm-driver=none**
2> Install istio on minikube cluster
**istioctl manifest apply --set profile=demo**
3> Ensure all pods are running
**kubectl get pods -n istio-system**
4> Now apply quick_start.yaml 
**kubectl apply -f quick_start.yaml**
5> Enable the opa and istio injection for service pods
**kubectl label namespace default opa-istio-injection="enabled"
kubectl label namespace default istio-injection="enabled"**
6> Now apply bookinfo.yaml 
**kubectl apply -f bookinfo.yaml**
7> Create a gateway for your service mesh by applying bookinfo-gateway.yaml
**kubectl apply -f bookinfo-gateway.yaml**
8> Node Port
**export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')
export INGRESS_HOST=$(minikube ip)
export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
echo $GATEWAY_URL**


curl --user alice:password -i http://$GATEWAY_URL/productpage
curl --user alice:password -i http://$GATEWAY_URL/api/v1/products

curl --user bob:password -i http://$GATEWAY_URL/productpage
curl --user bob:password -i http://$GATEWAY_URL/api/v1/products





## Example



