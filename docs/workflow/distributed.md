## Create a K6 Distributed Test Workflow

Neste teste o Testekube irá executar 5 testes simultâneos (Workers)

Criar um teste a partir de um exemplo

<div align="center">

![Parallel Executions](./images/parallel.png)

</div>

Selecionar `Create`

Spec*

```bash
kind: TestWorkflow
apiVersion: testworkflows.testkube.io/v1
metadata:
  name: distributed-k6
  namespace: testkube
  labels:
    docs: example
spec:
  config:
    duration:
      type: string
      default: 5s
    vus:
      type: integer
      default: 10
    workers:
      type: integer
      default: 3
  content:
    git:
      uri: https://github.com/kubeshop/testkube
      paths:
        - test/k6/executor-tests/k6-smoke-test.js
  steps:
    - name: Run test
      parallel:
        count: config.workers
        transfer:
          - from: /data/repo
        use:
          - name: distribute/evenly
        container:
          workingDir: /data/repo/test/k6/executor-tests
          env:
            - name: K6_SYSTEM_ENV
              value: K6_SYSTEM_ENV_value
            - name: K6_WEB_DASHBOARD
              value: 'true'
            - name: K6_WEB_DASHBOARD_EXPORT
              value: /data/k6-test-report.html
          resources:
            requests:
              cpu: 128m
              memory: 128Mi
        paused: true
        run:
          image: grafana/k6:0.49.0
          shell: |
            k6 run k6-smoke-test.js \
              -e K6_ENV_FROM_PARAM=K6_ENV_FROM_PARAM_value \
              --vus {{ config.vus }} \
              --duration {{ shellquote(config.duration) }} \
              --execution-segment {{ index }}/{{ count }}:{{ index + 1 }}/{{ count }}
        artifacts:
          workingDir: /data
          paths:
            - '*.html'
```



<div align="center">

![Parallel Definitions](./images/trigger.png)

</div>

# Configuração

- Duration: Tempo de execução do teste 
- VUs: Quantidade de Usuários
- Workers: Quantidade de Workers

<div align="center">

![Parallel Definitions](./images/parallel-definitions.png)

</div>

Teste Executado

<div align="center">

![Workers](./images/workers.png)

</div>
