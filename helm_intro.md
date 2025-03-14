# Helm: End-to-End Guide

## 1️⃣ Introduction to Helm
Helm is a package manager for Kubernetes that simplifies application deployment using pre-configured templates called **Charts**.

---

## 2️⃣ Installing Helm
### **On Linux & macOS:**
```sh
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

### **On Windows (Using Chocolatey):**
```sh
choco install kubernetes-helm
```

### **Verify Installation:**
```sh
helm version
```

---

## 3️⃣ Helm Repositories
### **Add a Repository (Example: Bitnami Repo)**
```sh
helm repo add bitnami https://charts.bitnami.com/bitnami
```

### **List Added Repositories**
```sh
helm repo list
```

### **Update All Repositories**
```sh
helm repo update
```

### **Search for Charts in a Repository**
```sh
helm search repo bitnami
```

---

## 4️⃣ Installing Helm Charts
### **Basic Installation (Example: Nginx)**
```sh
helm install my-nginx bitnami/nginx
```

### **Install with Custom Values**
```sh
helm install my-nginx bitnami/nginx --set service.type=LoadBalancer
```

### **Install Using a Values File**
Create `values.yaml`:
```yaml
service:
  type: LoadBalancer
  ports:
    http: 80
```
Deploy using the file:
```sh
helm install my-nginx bitnami/nginx -f values.yaml
```

---

## 5️⃣ Managing Helm Releases
### **List Installed Helm Releases**
```sh
helm list
```

### **Get Details of a Release**
```sh
helm status my-nginx
```

### **Upgrade an Existing Release**
```sh
helm upgrade my-nginx bitnami/nginx --set service.type=NodePort
```

### **Rollback to a Previous Version**
```sh
helm rollback my-nginx 1
```

### **Uninstall a Release**
```sh
helm uninstall my-nginx
```

---

## 6️⃣ Helm Template Rendering & Debugging
### **Dry Run Before Applying Changes**
```sh
helm install my-nginx bitnami/nginx --dry-run --debug
```

### **Render Templates Without Deploying**
```sh
helm template my-nginx bitnami/nginx
```

### **Lint a Chart for Errors**
```sh
helm lint my-chart/
```

---

## 7️⃣ Helm Chart Development
### **Create a New Chart**
```sh
helm create my-chart
```

### **Modify Chart Values**
Edit `values.yaml` inside the `my-chart/` directory.

### **Package a Custom Chart**
```sh
helm package my-chart/
```

### **Deploy a Local Chart**
```sh
helm install my-release ./my-chart
```

---

## 8️⃣ Helm and Kubernetes Integration
### **Check Helm-Managed Kubernetes Resources**
```sh
kubectl get all -l app.kubernetes.io/instance=my-nginx
```

### **Get Logs of a Helm-Deployed Pod**
```sh
kubectl logs -l app.kubernetes.io/name=nginx
```

---

## 9️⃣ Uninstalling Helm
### **Remove Helm Completely**
```sh
rm -rf ~/.helm
kubectl delete crd -l app.kubernetes.io/name=helm
```

---


