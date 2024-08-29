# Consumo

É muito importante verificar o consumo de CPU e memória durantes os testes para garantir que a ferramenta não seja gargalo durante os testes.

## Verificando os Pods

```bash
kubectl get pods -n testkube

NAME                                                    READY   STATUS    RESTARTS        AGE
testkube-api-server-7db54b85f-fsdnq                     1/1     Running   4 (4h14m ago)   4h15m
testkube-enterprise-api-5587986864-zjkr2                1/1     Running   0               4h15m
testkube-enterprise-dex-ff97f8c96-64xfl                 1/1     Running   0               4h15m
testkube-enterprise-minio-6bbbdb64fb-s95h7              1/1     Running   0               4h15m
testkube-enterprise-mongodb-585bdf9bfc-5l2gz            1/1     Running   0               4h15m
testkube-enterprise-nats-0                              3/3     Running   0               4h15m
testkube-enterprise-ui-6b9747c664-9x4rn                 1/1     Running   0               4h15m
testkube-enterprise-worker-service-694ccdb8b-rp7vp      1/1     Running   0               4h15m
testkube-minio-testkube-68947fcb4-6f2c6                 1/1     Running   0               4h15m
testkube-nats-0                                         2/2     Running   0               4h15m
testkube-operator-controller-manager-5bfb69557d-t5zqc   2/2     Running   0               4h15m  
```

## Verificando CPU e Memória

NODES

```bash
kubectl top node -n testkube

NAME                     CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%
k3d-mycluster-server-0   236m         2%     1969Mi          25%
```

PODS

```bash
kubectl top pod -n testkube

NAME                                                    CPU(cores)   MEMORY(bytes)
testkube-api-server-7db54b85f-fsdnq                     4m           194Mi
testkube-enterprise-api-5587986864-zjkr2                9m           58Mi
testkube-enterprise-dex-ff97f8c96-64xfl                 1m           12Mi
testkube-enterprise-minio-6bbbdb64fb-s95h7              2m           105Mi
testkube-enterprise-mongodb-585bdf9bfc-5l2gz            178m         86Mi
testkube-enterprise-nats-0                              2m           29Mi
testkube-enterprise-ui-6b9747c664-9x4rn                 1m           7Mi
testkube-enterprise-worker-service-694ccdb8b-rp7vp      1m           19Mi
testkube-minio-testkube-68947fcb4-6f2c6                 2m           88Mi
testkube-nats-0                                         2m           15Mi
testkube-operator-controller-manager-5bfb69557d-t5zqc   3m           32Mi
```

## Consumo pré execução do teste

<div align="center">

![Resultado depois da alteração](./images/kubernetes/pre-teste.png)

</div>

## Consumo durante execução do teste

<div align="center">

![Resultado depois da alteração](./images/kubernetes/durante-teste.png)

</div>

Próximos passos... [Métricas com Prometheus e Grafana](../prometheus-grafana-eks/README.md)