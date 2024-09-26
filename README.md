# Boost Your API Development Speed the Cloud-native Way

Demo repository for my talk at the InfoDays API-Design 2024.

## Kusk Gateway Demo

```bash
brew install 

kusk cluster install
kusk deploy -i examples/simple/hello-api-mock.yaml
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

## Maintainer

M.-Leander Reimer (@lreimer), <mario-leander.reimer@qaware.de>

## License

This software is provided under the MIT open source license, read the `LICENSE` file for details.
