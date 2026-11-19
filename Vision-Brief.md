aws sts get-caller-identity
------------
aws eks list-clusters --region us-east-1
-------
kubectl config current-context
----------
kubectl delete -f k8s/
---------
eksctl delete cluster --name YOUR-EXACT-EKS-CLUSTER-NAME --region us-east-1
------
aws ecr delete-repository \
  --repository-name evergreen-quote-api-so-1234 \
  --region us-east-1 \
  --force
-----------
cd ~/evergreen-quote-launch
-----
git checkout -- k8s/deployment.yaml
----------
kubectl config use-context kind-evergreen
------------
kubectl config current-context
---------
kubectl get pods
----------
git status
------------
eksctl get cluster --region us-east-1
--------


