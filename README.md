kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml

helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/

helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard --create-namespace --namespace kubernetes-dashboard

helm delete kubernetes-dashboard --namespace kubernetes-dashboard

kubectl apply -f dashboard-adminuser.yaml

kubectl apply -f dashboard-read-only-role.yaml

kubectl get secret admin-user -n kubernetes-dashboard -o jsonpath={".data.token"} | base64 -d


kubectl -n kubernetes-dashboard delete serviceaccount dashboard-user

kubectl -n kubernetes-dashboard delete clusterrolebinding dashboard-user

kubectl delete -f <path/to/kubernetes-dashboard-manifests>

