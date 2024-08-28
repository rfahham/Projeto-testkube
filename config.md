# Configurando o primeiro teste com Testkube

## Dashboard do Testkube

<div align="center">

![Dashboard](./images/dashboard.png)

</div>

## Criando o projeto

<div align="center">

![Create Workflow](./images/create-project.png)

</div>

## Criando o teste

<div align="center">

![Create Test](./images/create-project.png)

</div>

## Criando a configuração que será utilizada no test

<div align="center">

![Create Content](./images/content.png)

</div>

Um exemplo do Content

```bash
kind: TestWorkflow
apiVersion: testworkflows.testkube.io/v1
metadata:
  name: k6-sample
  namespace: testkube
  labels:
    docs: example
spec:
  content:
    files:
      - path: /data/example.js
        content: |-
          import http from 'k6/http';
          import { sleep } from 'k6';
          export default function () {
              http.get('https://test.k6.io');
              sleep(1);
          };
  steps:
    - name: Run Tests
      workingDir: /data
      run:
        image: grafana/k6:0.49.0
        env:
          - name: K6_WEB_DASHBOARD
            value: 'true'
          - name: K6_WEB_DASHBOARD_EXPORT
            value: k6-test-report.html
        args:
          - run
          - example.js
      artifacts:
        paths:
          - k6-test-report.html

```

## Configurando a ferramenta que será utilizada no teste

- Nome
- Label
- Template
- K6 Version

<div align="center">

![K6](./images/k6.png)

</div>

## Executando o teste

<div align="center">

![Executando o teste](./images/run-test.png)

</div>


## Verificando o resultado do teste
<div align="center">

![LOG OUTPUT](./images/log-output.png)

</div>


## Verificando a execução do teste

<div align="center">

![Dashboard](./images/dashboard-2.png)

</div>

## Alterando o WORKFLOWS

Alterar o Content, inserindo mais VUs, aumentando o tempo de execução


<div align="center">

![Alterando o content di WORKFLOW](./images/change-workflows.png)

</div>


```bash
kind: TestWorkflow
apiVersion: testworkflows.testkube.io/v1
metadata:
  name: k6-sample
  namespace: testkube
  labels:
    docs: example
spec:
  content:
    files:
    - path: /data/example.js
      content: |-
        import http from 'k6/http';
        import { sleep } from 'k6';
        export const options = {
          vus: 10,
          duration: '60s',
        };
        export default function () {
          http.get('http://test.k6.io');
          sleep(1);
        }
  steps:
  - name: Run Tests
    workingDir: /data
    run:
      image: grafana/k6:0.49.0
      env:
      - name: K6_WEB_DASHBOARD
        value: "true"
      - name: K6_WEB_DASHBOARD_EXPORT
        value: k6-test-report.html
      args:
      - run
      - example.js
    artifacts:
      paths:
      - k6-test-report.html
```

## Executando novamente o teste

<div align="center">

![Reexecutando o teste](./images/run-test-2.png)

</div>

## Verificando o resultado depois da modificação

<div align="center">

![Resultado depois da alteração](./images/k6-sample-3.png)

</div>

Próximos passos... [Verificando consumo CPU/Memória dos Nodes e Pods](consumo.md)