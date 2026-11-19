aws sts get-caller-identity
----------
aws ecr describe-repositories \
  --repository-names "$REPO" \
  --region us-east-1 \
  --query 'repositories[0].repositoryUri' \
  --output text
