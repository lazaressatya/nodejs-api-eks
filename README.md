nodejs-api-eks/
│
└── k8s/ ( Helm Chart )
    ├── deployment.yaml
    ├── service.yaml
    ├── ingress.yaml
    ├── namespace.yaml
│
└── node-api/ ( Helm Chart )
    ├── Chart.yaml
    ├── values.yaml
│
└── templates/
|    ├── deployment.yaml
|    ├── service.yaml
|    ├── ingress.yaml
|    ├── hpa.yaml
|    ├── servicemonitor.yaml
|    ├── networkpolicy.yaml
|    └── _helpers.tpl
├── Dockerfile
├── Jenkinsfile
├── README.md
├── .gitignore
├── package-lock.json
├── package.json
├── app.js
