# static website on Nginx container deployed on K8
## This repo shows how i deployed my website on a kubernetes cluster using local volume mounts 
run by using below command. 
1. git pull https://github.com/bharathkreddy/personal-website-nginx.git
2. cd personal-website-nginx
3. kubectl create ns brk
4. kubectl apply -f brksite.yaml (it would get deployed on the namespace brk)
5. kubectl describe service brkwebsite-service -n brk # to see the service endpoints, which would be the pod IPs if pods are replicated.
6. kubectl -n brk exec pod/brkwebsite-pod -- nslookup brkwebsite-service.brk.svc.cluster.local #virtual permanent ip address of service which is exposed to users.
7. kubectl --namespace brk exec pod/brkwebsite-pod -- wget --spider -q -S http://brkwebsite-service:8080 <- exec into pod, hear the service and get responce.
8. kubectl --namespace brk exec pod/brkwebsite-pod -- wget --spider -q -S http://{ IP OF POD }:80  <- exec into pod and see the site.
9. kubectl apply --filename brksite.yaml --namespace brk to redeploy the yaml file.
10. kubectl describe replicationcontroller {rc name} -n {namespace}
11. 

**Requirements**
1. Your system should have git cli,kubectl cli ,docker & Kubernetes installed.

**Notes:**

I have used a local volume mount, but generally a prefered way would be to use a persistant volume claim. 

I have not used any secrets but should you use any - I would strongly advice use of secrets and configmaps to inject those.