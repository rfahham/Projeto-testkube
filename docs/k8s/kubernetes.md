# Kubernetes

## Ter uma infra de Kubernetes.

- k3d - https://k3d.io/v5.7.3/#install-specific-release
- k3s - https://k3s.io/
- minikube - https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download
- kind - https://kind.sigs.k8s.io/
- Criar seu próprio ambiente kubernetes
- Usar kubernetes pública (AWS, GCP, AZURE)

## Instalando kubernetes com K3D

```bash
k3d cluster create horadoqa

INFO[0000] Prep: Network
INFO[0000] Created network 'k3d-horadoqa'
INFO[0000] Created image volume k3d-horadoqa-images
INFO[0000] Starting new tools node...
INFO[0000] Starting node 'k3d-horadoqa-tools'
INFO[0001] Creating node 'k3d-horadoqa-server-0'
INFO[0001] Creating LoadBalancer 'k3d-horadoqa-serverlb'
INFO[0001] Using the k3d-tools node to gather environment information
INFO[0001] Starting new tools node...
INFO[0001] Starting node 'k3d-horadoqa-tools'
INFO[0003] Starting cluster 'horadoqa'
INFO[0003] Starting servers...
INFO[0003] Starting node 'k3d-horadoqa-server-0'
INFO[0007] All agents already running.
INFO[0007] Starting helpers...
INFO[0007] Starting node 'k3d-horadoqa-serverlb'
INFO[0014] Injecting records for hostAliases (incl. host.k3d.internal) and for 3 network members into CoreDNS configmap...
INFO[0016] Cluster 'horadoqa' created successfully!
INFO[0016] You can now use it like this:
kubectl cluster-info
```

Podemos conferir a criação do cluster no Docker Desktop

[Cluster criado](./images/cluster-criado.png)

## Listando o Cluster

```bash
kubectx

k3d-horadoqa
```

## Listando os Namespaces

```bash
kubens

kubectl get namespace
```

## Listando os Nodes

```bash
kubectl get nodes

NAME                    STATUS   ROLES                  AGE     VERSION
k3d-horadoqa-server-0   Ready    control-plane,master   3m26s   v1.30.3+k3s1
```

## Listando os Pods

```bash
kubectl get pods

No resources found in default namespace.
```

Próximo passo... [Instalar o Helm](../helm/helm.md)

