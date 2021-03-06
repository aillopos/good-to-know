# Good To Know
*- stuff I tend to google every time I need it*


## Go

### Installation with APT
```bash
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt-get update
```

### Commands
```bash
go mod download
go mod tidy
```

### Add Go Module at Specific Commit
```bash
go get <repository>@<commithash>
```


## Bamboo
* **Artifact not found** &rarr; check if the "Clean up working directory task is there", since it also deletes any (build) artifacts


## ZSH

### Oh my ZSH
* **update** `omz update`


## Git

### Rename Branch
```bash
git checkout <old_name>
git branch -m <new_name>
git push origin -u <new_name>
git push origin --delete <old_name>
```

### Allow Dependencies from Private Repos
e.g.,
```
[url "ssh://git@scr.bsh-sdd.com:7999"]
        insteadOf = https://scr.bsh-sdd.com/scm
```

### Oh-My-ZSH Plugin
| what you get                                             | ZSH                   |
| ---                                               | ---                   |
| `git push --set-upstream origin <branch_name>`    | `gsup <branch_name>`  |

## IntelliJ / IDEA
* if something does not work anymore, e.g., dependencies not found, jump-to stops working &rarr; "Invalidate Caches / Restart ..."

### Increase Inotify Watches Limit
```bash
sudo vim /etc/sysctl.d/idea.conf
```
add `fs.inotify.max_user_watches = 524288`, then run
```bash
sudo sysctl -p --system
```
Restart IntelliJ.

## Kubectl

* **Field immutable Error** if it's a K8s Job, check if older jobs are deleted

## K8s Cluster
* increase number of nodes: AWS console -> autoscaling groups
* talk to cluster-internal endpoint
```bash
k run alpine -it --restart=Never --image=alpine -- /bin/sh
apk --no-cache add curl
curl -i -X POST 10.0.153.17:8080/heimdall/api/1.0/egw/credentials -u "egw-reu-prod:XXX" -H "Host: prod.reu.rest.homeconnectegw.com" # IP from kdp
```

### Other
* no username password prompt: use SSH repository address instead of HTTPS