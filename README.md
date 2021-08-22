# aws-cfm-iam-assume-role

# Step:
## 1.Create "master-user " account at Master aws account with Administrator Access
- [master-user.yaml](./master-user.yaml)

```bash
aws cloudformation create-stack --stack-name master-user --template-body file://master-user.yaml --profile cloudideastar-master --region ap-southeast-1 --capabilities CAPABILITY_NAMED_IAM
```

## 2.Create at dev aws account for dev assume role with administrator access then trusted the master aws account
- [dev-terraform-role.yaml](./dev-terraform-role.yaml)

```bash
aws cloudformation create-stack --stack-name dev-terraform-role --template-body file://dev-terraform-role.yaml --profile cloudideastar-dev --region ap-southeast-1 --capabilities CAPABILITY_NAMED_IAM
```

## 3.Create at prod aws account for prod assume role with administrator access then trusted the master aws account
- [prod-terraform-role.yaml](./prod-terraform-role.yaml)

```bash
aws cloudformation create-stack --stack-name prod-terraform-role --template-body file://prod-terraform-role.yaml --profile cloudideastar-prod --region ap-southeast-1 --capabilities CAPABILITY_NAMED_IAM
```

## Test
# 1. Log in to aws master account test switch role
# 2.aws iam list-roles --profile cloudideastar-dev
# 3.aws iam list-roles --profile cloudideastar-prod

![header image](assume.png)
