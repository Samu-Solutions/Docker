KIT="$HOME/LabFiles/WA3870-FinalProject/LabFiles/wa3870-cap-final-review-and-capstone-project-leaders"
------------
cp "$KIT/docker/Dockerfile" api/Dockerfile
-----------
cp "$KIT/docker/.dockerignore" api/.dockerignore
----------
------------
docker build -t evergreen-quote-api:2.0 ./api
----------
docker run --rm --network host --env-file api/.env evergreen-quote-api:2.0
---------
----------
kind create cluster --name evergreen
----------
docker pull mongo:7
---------
kind load docker-image evergreen-quote-api:2.0 --name evergreen
---------
kind load docker-image mongo:7 --name evergreen
----------
kubectl apply --dry-run=client -f k8s/
----------
kubectl apply -f k8s/mongo.yaml
----------
kubectl wait --for=condition=available deploy/mongo --timeout=180s
-------
kubectl apply -f k8s/
--------
kubectl get pods
-----------
------------
kubectl port-forward svc/evergreen-quote-api 3000:80
---------
curl http://localhost:3000/
-------
--------
mkdir -p .github/workflows
-----------
cp "$KIT/workflows/ci.yml" .github/workflows/ci.yml
----------
git add .github
-----------
git commit -m "Enable CI"
----------
git push
-------------
-------------
cd ~/evergreen-quote-launch
---------
git status
----------
-------------
KIT="$HOME/LabFiles/WA3870-FinalProject/LabFiles/wa3870-cap-final-review-and-capstone-project-leaders"
--------------
ls -la "$KIT/docker"

-------------
-----------
cd ~/evergreen-quote-launch
ls
KIT="$HOME/LabFiles/WA3870-FinalProject/LabFiles/wa3870-cap-final-review-and-capstone-project-leaders"
ls -la "$KIT/k8s"
