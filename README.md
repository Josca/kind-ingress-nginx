# ingress-nginx in "kind"

~~~bash
# Create a cluster using a config
kind create cluster --config kind-cluster.yaml -n kind-nginx

# Pull helm nginx-ingress
helm pull oci://ghcr.io/nginxinc/charts/nginx-ingress --untar --version 2.0.0
helm install nginx-ingress ./nginx-ingress --namespace nginx-ingress --create-namespace -f values-nginx-ingress.yaml

# Update your local /etc/hosts, add lines:
# 127.0.0.1   metrics.ingress-nginx
kubectl apply -f ingress-metrics.yaml
# curl http://metrics.ingress-nginx/metrics

# Update your local /etc/hosts, add lines:
# 127.0.0.1   web-a.com
# 127.0.0.1   web-b.com
helm install web-a ./my-web-chart --namespace web --create-namespace
helm install web-b ./my-web-chart --namespace web --create-namespace
~~~
