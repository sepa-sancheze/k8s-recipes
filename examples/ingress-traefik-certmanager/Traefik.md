# Ingress with Traefik and Cert Manager

Hello!

In order to Deploy a Site using HTTPS, we need to to the following.

1. Add Traefik Helm repo

        helm repo add traefik https://traefik.github.io/charts

        helm repo update

        helm install traefik traefik/traefik -n traefik --create-namespace

2. Add CertManager Helm repo

        helm repo add jetstack https://charts.jetstack.io --force-update

        helm repo update

        helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.15.1 --set crds.enabled=true

3. Create Cluster Issuer

        kubectl apply -f clusterissuer.yaml

4. Create Certificate

        kubectl apply -f certificate.yaml

5. Create Deployment and Service

        kubectl apply -f application.yaml

6. Create Ingress associated with Certificate

        kubectl apply -f ingress.yaml

