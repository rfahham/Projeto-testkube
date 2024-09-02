# Install

As execuções de testes são sempre realizadas dentro do seu cluster K8s

No local (painel)
Quero configurar tudo sozinho no meu cluster

Comece com 1 ambiente + 3 usuários grátis para sempre
Pague somente conforme você dimensiona ambientes + usuários
Núcleo de código aberto

Implantado e gerenciado por você:

- Agente de execução de teste
- Plano de controle/Painel
- Banco de dados + Armazenamento de artefatos

## Instalar com CLI

Seguir este tutorial de início rápido fornece uma instalação On Prem simplificada que implanta o plano de controle e o agente dentro do mesmo namespace. Ele não cria a configuração do Ingress, pois é projetado principalmente para instalações locais que permitem que você experimente e avalie a solução rapidamente. Ele vem com um administrador, organização e ambiente pré-configurados.

Antes de começar nossa implantação de início rápido, você deve instalar:

- Acesso a um cluster Kubernetes - Se você não tiver um Avaliando o Testkube sem acesso ao Kubernetes
- A CLI do helm para gerar a configuração YAML do Kubernetes.
- O kubectl CLI para executar comandos em clusters Kubernetes
- O Testkube CLI para o quickstarter. Para instruções, veja a próxima seção.

Para a experiência completa do Testkube, incluindo o Dashboard e todas as funcionalidades relacionadas, você precisará solicitar sua licença de teste gratuita que será necessária durante o processo de instalação. Como alternativa, você pode começar apenas com o agente autônomo, que é totalmente de código aberto e não requer uma licença.

> Informação
Por que uma licença é necessária? Obter uma licença gratuita nos ajuda a garantir que você tenha uma instalação e experiência de produto ideais com o Testkube. Não se preocupe - você não terá que falar com um representante de vendas ou inserir detalhes de cartão de crédito para começar - mas se precisar de nossa ajuda, estaremos muito mais bem preparados!

```bash
testkube version

Context:  (2.1.3)   Namespace: testkube
---------------------------------------

████████ ███████ ███████ ████████ ██   ██ ██    ██ ██████  ███████ 
   ██    ██      ██         ██    ██  ██  ██    ██ ██   ██ ██      
   ██    █████   ███████    ██    █████   ██    ██ ██████  █████   
   ██    ██           ██    ██    ██  ██  ██    ██ ██   ██ ██      
   ██    ███████ ███████    ██    ██   ██  ██████  ██████  ███████ 
                                           /tɛst kjub/ by Kubeshop


Client Version 2.1.3
Server Version 2.1.2
Commit 64a8049fc93613922a6be7d6de62a9d80a28fdd5
Built by goreleaser
Build date 2024-08-26T12:48:25Z
```


testkube init

http://localhost:8088/


```bash
testkube init demo

testkube init

████████ ███████ ███████ ████████ ██   ██ ██    ██ ██████  ███████ 
   ██    ██      ██         ██    ██  ██  ██    ██ ██   ██ ██      
   ██    █████   ███████    ██    █████   ██    ██ ██████  █████   
   ██    ██           ██    ██    ██  ██  ██    ██ ██   ██ ██      
   ██    ███████ ███████    ██    ██   ██  ██████  ██████  ███████ 
                                           /tɛst kjub/ by Kubeshop


Welcome to the installer for Testkube On-Prem demo.

Enter namespace for this installation: testkube
Enter license key: XXXXXX-XXXXXX-XXXXXX-XXXXXX-XXXXXX

Installation is about to start and may take a several minutes:

- Testkube will be installed in the k3d-mycluster context.
- Testkube services will be applied to the testkube namespace.
- Testkube CRDs and cluster roles will be applied to your cluster.

Do you want to continue [Y/n]: Yes

 ⠦  Installing Testkube On-Prem Demo... (19s)

 ✅  Installing Testkube On-Prem Demo...                                             
The default admin credentials are: admin@example.com / password
Make sure to copy these credentials now as you will not be able to see this again.

```

Uma vez instalado, você será perguntado se deseja testkube dashboardacessar convenientemente todos os serviços relevantes no seu localhost. Você sempre pode executar isso você mesmo depois, caso feche este terminal após a instalação. O administrador nesta demonstração tem o seguinte e-mail e senha: admin@example.com/password.

Bons testes!

Próximos passo...[Configurando o primeiro teste com Testkube](config.md)