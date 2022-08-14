# static website on Nginx container deployed on K8
## This repo shows how i deployed my website on a kubernetes cluster using local volume mounts 
run by using below command. 
1. git pull https://github.com/bharathkreddy/personal-website-nginx.git
2. cd personal-website-nginx
3. kubectl create ns brk
4. kubectl apply -f brksite.yaml (it would get deployed on the namespace brk)

**Requirements**
1. Your system should have git cli,kubectl cli ,docker & Kubernetes installed.

**Notes:**
I have used a local volume mount, but generally a prefered way would be to use a persistant volume claim. 
I have not used any secrets but should you use any - I would strongly advice use of secrets and configmaps to inject those.