# 🚀 Autodep - Static Website with Auto Deployment to AWS EKS

This project hosts a simple static HTML/CSS/JS website served using Nginx. It is deployed to an AWS EKS cluster using Docker, ECR, and GitHub Actions.

---

## 📦 Project Structure

```
autodep/
├── index.html
├── style.css
├── coffee2.jpg
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── .github/workflows/deploy.yml
```

---

## 🔧 Prerequisites

1. An EKS Cluster is running.
2. An ECR repository is created: `autodep`
3. IAM user with permissions to EKS, ECR, and CodeDeploy.
4. GitHub repo with these **Secrets** added:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_REGION`
   - `AWS_ACCOUNT_ID`
   - `ECR_REPOSITORY` (e.g., `autodep`)
   - `EKS_CLUSTER_NAME`

---

## 🚀 Deployment Process (Automated)

Every time you push to the `main` branch:
1. GitHub Action builds the Docker image.
2. Pushes it to ECR.
3. Updates your deployment on AWS EKS using `kubectl`.

---

## 🐳 Local Build (Optional)

```bash
docker build -t autodep .
docker run -p 8080:80 autodep
```

---

## ☁️ EKS Access (Optional Manual Apply)

```bash
aws eks update-kubeconfig --name your-cluster-name --region your-region
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

---

## 🌐 Output

Use `kubectl get svc` to find the external LoadBalancer URL.

Enjoy your coffee-themed deployment ☕!