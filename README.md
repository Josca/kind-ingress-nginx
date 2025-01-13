# ingress-nginx in "kind"

~~~bash
# Create a cluster using a config
kind create cluster --config kind-cluster.yaml -n kind-nginx

# Add helm repo
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo add metallb https://metallb.github.io/metallb
helm repo update

helm install metallb metallb/metallb --version 0.14.9

helm install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx --create-namespace -f values-ingress-nginx.yaml

kubectl apply -f manifests
~~~
