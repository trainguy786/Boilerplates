if you want to expose something 
1) apply a label:
    
```shell
k label pod -n monitoring grafana-69594fb486-cxlkp app=grafana
```

2) create a service.yaml file
----

```yaml
apiVersion: v1
kind: Service
metadata:
  name: grafana
  namespace: monitoring  # Adjust if Grafana is in a different namespace
  labels:
    app: grafana
spec:
  type: LoadBalancer
  selector:
    app: grafana
  ports:
    - port: 80           # External port for the LoadBalancer
      targetPort: 3000   # Internal port Grafana listens on
      protocol: TCP
      name: http
```
3) apply the file and enjoy!!!