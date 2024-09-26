# Boost Your API Development Speed the Cloud-native Way

Demo repository for my talk at the InfoDays API-Design 2024.

## Kusk Gateway Demo

```bash
brew install 

kusk cluster install
kusk deploy -i examples/simple/hello-api-mock.yaml
kusk get api simple-api -o yaml
kusk dashboard

# call the mocked API
kusk ip
http get `kusk ip`/hello

# deploy backend
kubectl create deployment hello-world --image=kubeshop/kusk-hello-world:v1.0.0
kubectl expose deployment hello-world --name hello-world-svc --port=8080
kusk deploy -i examples/simple/hello-api-upstream.yaml
http get `kusk ip`/hello
```

```bash
# for local development
docker run -p 8585:8080 -it --rm quay.io/microcks/microcks-uber:latest-native
open http://localhost:8585

kubectl create deployment quarkus-api-pastry --image=quay.io/microcks/quarkus-api-pastry:latest
kubectl expose deployment quarkus-api-pastry --name quarkus-api-pastry-svc --port=8282 --load-balancer-ip=''
kubectl edit service quarkus-api-pastry-svc
http get 35.228.36.101:8282/pastry

# make sure we have an ingress controller installed
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.2/deploy/static/provider/cloud/deploy.yaml

# install Microcks on cluster
kubectl create namespace microcks
helm repo add microcks https://microcks.io/helm
helm install microcks microcks/microcks --namespace microcks --set microcks.url=microcks.34.88.24.76.nip.io --set keycloak.url=keycloak.34.88.24.76.nip.io --set keycloak.privateUrl=http://microcks-keycloak.microcks.svc.cluster.local:8080
```

## Maintainer

M.-Leander Reimer (@lreimer), <mario-leander.reimer@qaware.de>

## License

This software is provided under the MIT open source license, read the `LICENSE` file for details.
