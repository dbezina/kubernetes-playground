1. install helm
2. install CDRs
    kubectl apply -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.5.1/standard-install.yaml
check kubectl get crds | findstr gateway
    helm repo add ngf https://nginxinc.github.io/nginx-gateway-fabric
3. install nginx-gateway
    helm install ngf oci://ghcr.io/nginx/charts/nginx-gateway-fabric --create-namespace -n nginx-gateway
check
get gatewayclass
kubectl get deployments,pods -n nginx-gateway 
kubectl get svc -n nginx-gateway
4. apply all
        kubectl apply -f ./ 
 check:
 kubectl get gateway -n nginx-gateway 
 NAME CLASS ADDRESS PROGRAMMED AGE 
 dice-gateway nginx True 68m

 kubectl describe httproute -n default
        Type: Accepted
        Status: True ✅

5. make port-forward
    kubectl port-forward -n nginx-gateway svc/dice-gateway-nginx 8080:80
6. check 
    curl.exe -H "Host: job.127.0.0.1.nip.io" http://localhost:8080 