# k3s-pi-vault
HashiCorp Vault on K3s on RPi4 


## Objective

To learn Kubernetes with a Raspberry Pi 4 and K3s.
 

## Download `k3sup` 

I copied this section from the [k3sup README](https://github.com/alexellis/k3sup/blob/master/README.md) go check it out.

`k3sup` is distributed as a static Go binary. You can use the installer on MacOS and Linux, or visit the [Releases page](https://github.com/alexellis/k3sup/releases) to download the executable for Windows.

```sh
curl -sLS https://get.k3sup.dev | sh
sudo install k3sup /usr/local/bin/

k3sup --help
```
`k3sup` is made available free-of-charge, but you can support its ongoing development through [GitHub Sponsors](https://insiders.openfaas.io/) 💪

I would also suggest you check out [Alex Ellis on Twitter](https://twitter.com/alexellisuk)

His Twitter account has inspired me to learn lots of fune stuff with Kubernetes FaaS and RPIs.


### Setup K3s with `k3sup` but do not deploy Traefik

> Note: You can copy ssh keys to a remote VM with `ssh-copy-id user@IP`.

Imagine the IP was `192.168.161.104` and the username was `pi`, then you would run this:

* Run `k3sup`:

```sh
export IP=192.168.161.104
k3sup install --ip $IP --user pi --k3s-extra-args --no-deploy traefik
```

Use the optional argument to not deploy Traefik as the http port will overlap.

* `--k3s-extra-args` - Optional extra arguments to pass to k3s installer, wrapped in quotes, i.e. `--k3s-extra-args '--no-deploy traefik'`.

## Kubernetes Objects



## Service

I made a NodePort [Service](https://github.com/colin-mccarthy/k3s-pi-vault/blob/master/manifests/svc-vault-tcp-nodeport.yml)
for port 30007

```
kubectl apply -f svc-vault-tcp-nodeport.yml 
```

## ConfigMap

I made a [ConfigMap](https://github.com/colin-mccarthy/k3s-pi-vault/blob/master/manifests/configmap-vault-vars.yml)
to hold the Env vars.

```
kubectl apply -f configmap-vault-vars.yml 
```

## Pod

I made a [Pod](https://github.com/colin-mccarthy/k3s-pi-vault/blob/master/manifests/pod-vault.yml)
to stand up Vault with the littlest amount of complexity.

```
kubectl apply -f pod-vault.yml 
```

## Deployment

I made a [Deployment](https://github.com/colin-mccarthy/k3s-pi-vault/blob/master/manifests/deployment-vault.yml)
to stand up Vault with replicas and an update strategy.

```
kubectl apply -f deployment-vault.yml
```


## Secret

Coming soon







