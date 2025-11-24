# ArgoCD Demo

Dieses Repository enthält eine Demo für die Verwendung von ArgoCD mit Helm-Charts und verschiedenen Umgebungen (Dev und Prod).

## Projektstruktur

```
argocd-demo/
├── argocd/
│   ├── app-app.yaml       # ArgoCD Application für die App
│   ├── cnpg-app.yaml      # ArgoCD Application für CNPG
├── charts/
│   ├── app/               # Helm-Chart für die App
│   │   ├── Chart.yaml     # Chart-Metadaten
│   │   ├── values.yaml    # Standardwerte für das Chart
│   │   └── templates/     # Kubernetes-Templates
│   │       └── deployment.yaml
│   ├── cnpg/              # Helm-Chart für CNPG
│   │   ├── Chart.yaml     # Chart-Metadaten
│   │   ├── values.yaml    # Standardwerte für das Chart
│   │   └── templates/     # Kubernetes-Templates
│   │       └── cluster.yaml
├── environments/
│   ├── dev/               # Entwicklungsumgebung
│   │   ├── app-values.yaml
│   │   └── cnpg-values.yaml
│   ├── prod/              # Produktionsumgebung
│   │   ├── app-values.yaml
│   │   └── cnpg-values.yaml
└── README.md              # Projektbeschreibung
```

## Voraussetzungen

- Kubernetes-Cluster
- ArgoCD

## Deployment mit ArgoCD

### 1. ArgoCD-Anwendungen erstellen

Wechsle in das Verzeichnis `argocd/` und wende die Konfigurationsdateien an:

```bash
kubectl apply -f app-app.yaml
kubectl apply -f cnpg-app.yaml
```

### 2. Synchronisation starten

Nach dem Erstellen der Anwendungen kannst du die Synchronisation in der ArgoCD-Benutzeroberfläche starten oder den folgenden Befehl verwenden:

```bash
argocd app sync <app-name>
```

Ersetze `<app-name>` durch den Namen der Anwendung, z. B. `app` oder `cnpg`.

## Umgebungen

- **Dev**: Entwicklungsumgebung mit spezifischen Werten in `environments/dev/`
- **Prod**: Produktionsumgebung mit spezifischen Werten in `environments/prod/`

## Lizenz

Dieses Projekt steht unter keiner spezifischen Lizenz. Es dient ausschließlich zu Demonstrationszwecken.