# ingress-nginx in "kind"

~~~bash
# Create a cluster using a config
kind create cluster --config kind-cluster.yaml -n kind-nginx

# Add helm repo
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update

# Install ingress-nginx using customized values
helm install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace -f values-ingress-nginx.yaml
# helm uninstall ingress-nginx -n ingress-nginx

kubectl apply -f manifests
~~~
