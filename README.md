# Single NODE K8s with microk8s

sudo snap install microk8s

microk8s enable dns storage ingress helm3

microk8s helm3 install postgres bitnami/postgresql

microk8s helm3 install cert-manager jetstack/cert-manager   \ 
    --namespace cert-manager --version v0.15.2   --set installCRDs=true   \ 
    --set ingressShim.defaultIssuerName=letsencrypt-production   \
    --set ingressShim.defaultIssuerKind=ClusterIssuer   \
    --set ingressShim.defaultIssuerGroup=cert-manager.iow0

k create -f  production-issuer.yml

