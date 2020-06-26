kubectl create namespace nginx-ingress 
kubectl create namespace cert-manager
kubectl create namespace chartmuseum
kubectl label namespace cert-manager certmanager.k8s.io/disable-validation="true"
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v0.15.1/cert-manager.crds.yaml

helm upgrade --install nginx-ingress stable/nginx-ingress --wait --namespace=nginx-ingress --version=1.11.1 
helm upgrade --install cert-manager jetstack/cert-manager --namespace cert-manager --version v0.15.1 --wait
helm upgrade --install chartmuseum stable/chartmuseum --wait --namespace=chartmuseum --version=2.3.2 -f values.yaml

kubectl appy -f kubernetes-templating//cert-manager/cert-manager-clusterissue.yaml

chartmuseum
1. Install Helm plugin to push chart package to ChartMuseum helm plugin install "https://github.com/chartmuseum/helm-push.git"
2. Add helm repo "helm repo add chartmuseum "helm repo add chartmuseum https://chartmuseum.35.188.146.9.nip.io/"
3. Push chart to chartmuseum "helm push my-firat-chart/ chartmuseum"
4. Install chart from chartmuseum repo "helm upgrade --install my-first-chart chartmuseum/my-first-chart --wait"


