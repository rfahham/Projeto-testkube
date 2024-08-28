# Monitorando o CLuster

Utilizando o Prometheus e o Grafana

```bash
git clone https://github.com/prometheus-operator/kube-prometheus

cd kube-prometheus
```

Instalação do CRDS (Custom Resource Definition)

```bash
kubectl create -f manifests/setup

customresourcedefinition.apiextensions.k8s.io/alertmanagerconfigs.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/alertmanagers.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/podmonitors.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/probes.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/prometheuses.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/prometheusagents.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/prometheusrules.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/scrapeconfigs.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/servicemonitors.monitoring.coreos.com created
customresourcedefinition.apiextensions.k8s.io/thanosrulers.monitoring.coreos.com created
namespace/monitoring created
```

Verificando os CDRs criados

```bash
kubectl get customresourcedefinition.apiextensions.k8s.io -n monitoring
```

Verificando os pods

```bash
kubectl get pods -n monitoring
No resources found in monitoring namespace.
```

Criando os pods com todas as aplicações necessárias para o monitoramento

```bash
kubectl apply -f manifests
```

Verificando os pods

```bash
kubectl get pods -n monitoring
NAME                                   READY   STATUS    RESTARTS   AGE
alertmanager-main-0                    2/2     Running   0          52s
alertmanager-main-1                    2/2     Running   0          52s
alertmanager-main-2                    2/2     Running   0          52s
blackbox-exporter-597d86cf5c-l9cmb     3/3     Running   0          60s
grafana-58f5f5f869-k4slr               1/1     Running   0          59s
kube-state-metrics-789f4b647d-mrvlb    3/3     Running   0          59s
node-exporter-wlhjk                    2/2     Running   0          59s
prometheus-adapter-5794d7d9f5-b7vng    1/1     Running   0          58s
prometheus-adapter-5794d7d9f5-tl8sp    1/1     Running   0          58s
prometheus-k8s-0                       2/2     Running   0          51s
prometheus-k8s-1                       2/2     Running   0          51s
prometheus-operator-7545b58fd7-sq9pp   2/2     Running   0          58s
```


```bash
kubectl get svc -n monitoring
NAME                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                      AGE
alertmanager-main       ClusterIP   10.43.145.234   <none>        9093/TCP,8080/TCP            3m
alertmanager-operated   ClusterIP   None            <none>        9093/TCP,9094/TCP,9094/UDP   2m52s
blackbox-exporter       ClusterIP   10.43.129.174   <none>        9115/TCP,19115/TCP           3m
grafana                 ClusterIP   10.43.211.108   <none>        3000/TCP                     2m59s
kube-state-metrics      ClusterIP   None            <none>        8443/TCP,9443/TCP            2m59s
node-exporter           ClusterIP   None            <none>        9100/TCP                     2m59s
prometheus-adapter      ClusterIP   10.43.11.32     <none>        443/TCP                      2m58s
prometheus-k8s          ClusterIP   10.43.139.143   <none>        9090/TCP,8080/TCP            2m59s
prometheus-operated     ClusterIP   None            <none>        9090/TCP                     2m51s
prometheus-operator     ClusterIP   None            <none>        8443/TCP                     2m58s
```

Acessando o Prometheus pelo Browser

```bash
kubectl port-forward -n monitoring svc/prometheus-k8s 9090:9090
```

Acessando o Grafana pelo Browser

```bash
kubectl port-forward -n monitoring svc/grafana 3000:3000
```

admin/admin

http://prometheus-k8s.monitoring.svc:9090

Post "http://prometheus-k8s.monitoring.svc:9090/api/v1/query": dial tcp 10.43.146.56:9090: i/o timeout - There was an error returned querying the Prometheus API.

```shell
$ kubectl --namespace monitoring port-forward svc/prometheus-k8s 9090
```

```shell
$ kubectl --namespace monitoring port-forward svc/grafana 3000
```