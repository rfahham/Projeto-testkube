# Helm

O gerenciador de pacotes para Kubernetes
O Helm é a melhor maneira de encontrar, compartilhar e usar software criado para Kubernetes.

O Helm agora tem um script de instalação que automaticamente pegará a versão mais recente do Helm e a instalará localmente.

- https://helm.sh/docs/intro/install/

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
Verificando a versão

```bash
helm version

version.BuildInfo{Version:"v3.15.4", GitCommit:"fa9efb07d9d8debbb4306d72af76a383895aa8c4", GitTreeState:"clean", GoVersion:"go1.22.6"}
```

Próximo passo...[Instalar o Testkube](testkube.md)