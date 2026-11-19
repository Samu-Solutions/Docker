export ACCOUNT_ID=360754226671
---
export REPO=evergreen-quote-api-so-1234
---
export IMAGE="$ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com/$REPO:2.0"
---
aws ecr get-login-password --region us-east-1 | \
  docker login --username AWS --password-stdin "$ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com"
----
docker tag evergreen-quote-api:2.0 "$IMAGE"
----
docker push "$IMAGE"

