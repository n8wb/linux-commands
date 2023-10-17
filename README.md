=== GENERAL === 

## View documentation for a command
man <command> 

## Search all files in a dir
grep -H -n -r <search term> <dir>

## Essentials
• sed -> https://linux.die.net/man/1/sed
• awk -> https://linux.die.net/man/1/awk
• tmux -> https://linux.die.net/man/1/tmux
• grep -> https://linux.die.net/man/1/grep
• journalctl -> https://man7.org/linux/man-pages/man1/journalctl.1.html
• systemctl -> https://man7.org/linux/man-pages/man1/systemctl.1.html
• jq -> https://manpages.ubuntu.com/manpages/focal/en/man1/jq.1.html

=== CRYPTO ===

## CREATE NEW ETH PRIVATE KEY 

`openssl rand -hex 32`

=== Devops === 

## FORWARD LOCAL PORT TO REMOTE SERVER 

`ssh -R <remote port>:localhost:<local port> <remote ip> -N`

## EXPOSE A PORT ON ANOTHER PORT

`socat tcp-listen:<new listen port>,reuseaddr,fork tcp:localhost:<forwarding port>`

# Kubectl 

Cheatsheet: https://kubernetes.io/docs/reference/kubectl/cheatsheet/

### Important sub-commands

```
kubectl logs
kubectl describe <pod|deployment...> <name>
kubectl get <pods|secrets|configmap> <name> [-o yaml]
```

## ALL LOGS FOR AN ENTIRE CHART

`kubectl logs --max-log-requests 200 -f -l app.kubernetes.io/instance=<chart>`

## ALL LOGS FOR A DEPLOYMENT

`kubectl logs --max-log-requests 200 -f -l app.kubernetes.io/name=<deployment name>`

## GET ALL PODS FOR A DEPLOYMENT

`kubectl get pods -l app.kubernetes.io/instance=<deployment name>`

## RESTART ALL PODS FOR A CHART

`kubectl delete pods $(kubectl get pods -l app.kubernetes.io/instance=<chart> | awk '{print $1}' | sed -e '1d')`

## Extract Secret 
```
kubectl get secrets
kubectl get secrets <secret name> -o json  | jq .data.<secret field> -r | base64 -d
```

# HELM

## LIST CHARTS

`helm ls`

## SEE DEPLOYED YAML FOR CHAT

`helm get manifest <chart name>`

## ROLLBACK

`helm rollback <release> <previous version number>`

# GCLOUD CLI

## GCLOUD CLI APPLICATION DEFAULT AUTH

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
