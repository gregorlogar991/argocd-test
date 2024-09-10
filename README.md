Application:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  annotations:
    argocd.argoproj.io/manifest-generate-paths: .
  labels:
    app.kubernetes.io/name: glogar-test
    app.kubernetes.io/version: 1.0.8
  name: glogar-test
  namespace: argo-cd
spec:
  destination:
    namespace: develop
    server: https://kubernetes.default.svc
  project: default
  source:
    helm:
      releaseName: release
      valueFiles:
      - values.yaml
    path: helm-app
    repoURL: https://github.com/gregorlogar991/argocd-test
    targetRevision: HEAD
  syncPolicy:
    automated: {}
```
