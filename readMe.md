# Commands

### Create client

    mkdir client
    cd client
    npx create-react-app client
    npm i axios


    docker build -t ozerdur/client .
    docker push ozerdur/client
    kubectl apply -f client-depl.yaml
    kubectl rollout restart deployment client-depl

### Create posts

    mkdir posts
    cd posts
    npm init -y
    npm install express cors axios nodemon

    docker build -t ozerdur/posts .
    docker push ozerdur/posts
    kubectl apply -f posts.yaml // For manually creating Pod
    kubectl apply -f posts-depl.yaml
    kubectl rollout restart deployment posts-depl //to update deployment

### Create comments

    mkdir comments
    cd comments
    npm init -y
    npm install express cors axios nodemon


    docker build -t ozerdur/comments .
    docker push ozerdur/comments
    kubectl apply -f comments-depl.yaml
    kubectl rollout restart deployment comments-depl

### Event Bus

     docker build -t ozerdur/event-bus .
     docker push ozerdur/event-bus
     kubectl rollout restart deployment event-bus-depl

### Type Of Ports

    ClusterIP: expose pods in the cluster. Sets up an easy-to-remember URL to access a pod.(Default Option)
    NodePort: makes pod accessible from outside the cluster  only for dev purposes
    LoadBalancer: expose port to outside cluster
    External Name: Redirects an in-cluster request to a CNAME url.... don't worry about this one...

### ingress-nginx

    https://kubernetes.github.io/ingress-nginx/deploy/
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.46.0/deploy/static/provider/cloud/deploy.yaml

### To Find what is running on port 80

    Mac:
        sudo lsof -i tcp:80
    Windows:
        netstat -aon | findstr :80

add 127.0.0.1 posts.com to /etc/hosts file

## Skaffold

- Used to automate kubectl tasks
- brew install skaffold
- skaffold dev
