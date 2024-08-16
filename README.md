
# Fullstack App on Kubernetes

This project is a fullstack application with a frontend, backend, and MongoDB database, all deployed using Kubernetes. The backend is built with Node.js, the frontend is served by Nginx, and MongoDB is used for data storage.

## Project Structure

- **Backend (Node.js):** Handles the API logic.
- **Frontend (Nginx):** Serves the website.
- **MongoDB:** Stores data.

## How to Set It Up

### Prerequisites

- Docker
- Kubernetes (Minikube or any cluster)
- kubectl

### Steps

1. **Build and Push Images:**

   - Backend:  
     \`\`\`bash
     docker build -t <your-dockerhub-username>/node-backend .
     docker push <your-dockerhub-username>/node-backend
     \`\`\`
   - Frontend:  
     \`\`\`bash
     docker build -t <your-dockerhub-username>/nginx-frontend .
     docker push <your-dockerhub-username>/nginx-frontend
     \`\`\`

2. **Deploy on Kubernetes:**

   - Create a namespace:  
     \`\`\`bash
     kubectl create namespace fullstack-app
     \`\`\`
   - Deploy ConfigMap:  
     \`\`\`bash
     kubectl apply -f K8s/configMap.yaml -n fullstack-app
     \`\`\`
   - Deploy MongoDB:  
     \`\`\`bash
     kubectl apply -f K8s/Mongodb/ -n fullstack-app
     \`\`\`
   - Deploy Backend:  
     \`\`\`bash
     kubectl apply -f K8s/Nodejs/ -n fullstack-app
     \`\`\`
   - Deploy Frontend:  
     \`\`\`bash
     kubectl apply -f K8s/Nginx/ -n fullstack-app
     \`\`\`

3. **Check Everything:**

   - Make sure pods are running:  
     \`\`\`bash
     kubectl get pods -n fullstack-app
     \`\`\`

4. **Access the App:**

   - Get Minikube IP:  
     \`\`\`bash
     minikube ip
     \`\`\`
   - Visit the app in your browser:  
     \`\`\`bash
     http://<minikube-ip>:<node-port>
     \`\`\`

