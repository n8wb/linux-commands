# General

## View documentation for a command
`man <command> `

## Search all files in a dir
`grep -H -n -r <search term> <dir>`

## Essentials

* `sed` -> https://linux.die.net/man/1/sed
* `awk` -> https://linux.die.net/man/1/awk
* `tmux` -> https://linux.die.net/man/1/tmux
* `grep` -> https://linux.die.net/man/1/grep
* `journalctl` -> https://man7.org/linux/man-pages/man1/journalctl.1.html
* `systemctl` -> https://man7.org/linux/man-pages/man1/systemctl.1.html
* `jq` -> https://manpages.ubuntu.com/manpages/focal/en/man1/jq.1.html

# Crypto

## Create new ethereum private key

`openssl rand -hex 32`

# Devops

## Forward local port to remote server

`ssh -R <remote port>:localhost:<local port> <remote ip> -N`

## expose an port on a socket

`socat tcp-listen:<new listen port>,reuseaddr,fork tcp:localhost:<forwarding port>`

# Kubectl 

[Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

## Important sub-commands

```
kubectl logs
kubectl describe <pod|deployment...> <name>
kubectl get <pods|secrets|configmap> <name> [-o yaml]
```

## All logs for an entire chart

`kubectl logs --max-log-requests 200 -f -l app.kubernetes.io/instance=<chart>`

## All logs for a deployment

`kubectl logs --max-log-requests 200 -f -l app.kubernetes.io/name=<deployment name>`

## Get all pods for a deployment

`kubectl get pods -l app.kubernetes.io/instance=<deployment name>`

## Restart all pods for a deployment

`kubectl delete pods $(kubectl get pods -l app.kubernetes.io/instance=<chart> | awk '{print $1}' | sed -e '1d')`

## Extract Secret 
```
kubectl get secrets
kubectl get secrets <secret name> -o json  | jq .data.<secret field> -r | base64 -d
```

# Helm

* [Cheat Sheet](https://helm.sh/docs/intro/cheatsheet/)
* [Intro](https://helm.sh/docs/intro/using_helm/)

## List Charts

`helm ls -a`

## See deployed yaml for a chart

`helm get manifest <chart name>`

## rollback a release

`helm rollback <release> <previous version number>`

# Gcloud CLI

## Gcloud CLI application default login [Deprecated]

```
gcloud auth application-default login 
gcloud auth application-default set-quota-project <project>
```


# GPG

## New Key
`gpg --full-generate-key`

## List your private keys
`gpg -K`

## Export public key  
`gpg --export --armour <key id>`
