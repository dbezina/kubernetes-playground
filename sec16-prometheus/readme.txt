how to configure prometheus and graphana

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

 helm install my-observability prometheus-community/kube-prometheus-stack --version 55.5.0 

 wait for 10 minuteseverything to start

  kubectl get all -A 

  kubectl port-forward service/my-observability-kube-prom-prometheus 9090:9090 
  use at localhost:9090

  kubectl port-forward service/my-observability-grafana 3000:80   
  use at localhost:3000
  user: admin
  pass: prom-operator

  goto  https://github.com/dotdc/graphana-dashboards-kubernetes 
  choose the dashboard you like and import it to your graphana by ID


  helm uninstall my-observability      

  kubectl -n kube-system delete service/my-observability-kube-prom-kubelet 