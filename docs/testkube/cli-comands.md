# CLI commands

Run test workflow

```bash
kubectl testkube run tw distributed-k6 
```
Get test workflow

```bash
kubectl testkube get tw distributed-k6 
```

List executions

```bash
kubectl testkube get twe -w distributed-k6 
```

Delete test workflow

```bash
kubectl testkube delete tw distributed-k6 
```