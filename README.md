# Ubuntu
Open your .bashrc file.
```
nano .bashrc
```

and copy this:

```
unset KUBECONFIG

# k8s default context:
[ -e ~/.kube/config ] && export KUBECONFIG=$HOME/.kube/config

# If we have microk8s; generate a context for it
which microk8s.config 2>/dev/null > /dev/null && microk8s.config > ~/.kube/contexts/microk8s.yaml

# We put other contexts in ~/.kube/contexts
for c in $(IFS=$'\n' find ~/.kube/contexts -type f -name "*.yaml")
do
export KUBECONFIG=$c:$KUBECONFIG
done

```
```
source .bashrc
```
```
kubectl config get-contexts
```


On $HOME/.kube/context we cant create a new folder with other kubernetes cluster config
