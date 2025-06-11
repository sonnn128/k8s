```
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: car-serv-deployment
  name: car-serv-deployment
  namespace: car-serv
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25% 
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: car-serv-deployment
  template:
    metadata:
      labels:
        app: car-serv-deployment
      namespace: car-serv
    spec:
      containers:
        # - image: elroydevops/car-serv
        - image: nginx
          imagePullPolicy: Always
          name: car-serv
          ports:
            - containerPort: 80
              name: tcp
              protocol: TCP
```

