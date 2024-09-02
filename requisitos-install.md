# Pre Requisitos para a Instalação

Preparando o ambiente para a instalação

- Kubernetes
- Helm
- Testkube

# Kubernetes

Ter uma infra de Kubernetes.

- k3d - https://k3d.io/v5.7.3/#install-specific-release
- k3s - https://k3s.io/
- minikube - https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download
- kind - https://kind.sigs.k8s.io/
- Criar seu próprio ambiente kubernetes
- Usar kubernetes pública (AWS, GCP, AZURE)

# Helm

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

# Testkube com Ubuntu

```bash
wget -qO - https://repo.testkube.io/key.pub | sudo apt-key add -
echo "deb https://repo.testkube.io/linux linux main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install -y testkube
```

# Testkube MAC OS

```bash
brew install testkube
```

# Download Manual

1. Baixe o binário para a versão e plataforma de sua escolha [aqui](https://github.com/kubeshop/testkube/releases).

2. Descompacte-o. Por exemplo, no Linux use:
```bash
tar -zxvf testkube_1.5.1_Linux_x86_64.tar.gz.
```

3. Mova-o para um local no PATH. Por exemplo:

```bash
mv  testkube_1.5.1_Linux_x86_64/kubectl-testkube /usr/local/bin/kubectl-testkube
```

O instalador concluirá estas etapas:

- Verifique se você escolheu o ambiente Kubernetes certo.
- Peça algumas informações, como a licença solicitada anteriormente.
- Instale o plano de controle e o agente do Testkube, ambos no mesmo namespace.

Todo o processo leva de 3 a 5 minutos e pode ser iniciado com o seguinte comando:

Próximos passo... [Instalação do Testkube](install.md)