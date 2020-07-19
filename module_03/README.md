## Deploy

1. Create a key pair named cf in the cloud console.

2. Deploy the stack with :

```bash

aws cloudformation deploy \
  --template-file ./hbfl.start.template \
  --stack-name hbfl-stack \
  --parameter-overrides \
    ImageIdParameter=ami-xxxxxx \
    VPCIdParameter=vpc-xxxxx \
    SubnetListParameter=subnet-xxxx,subnet-xxxx \
  --capabilities CAPABILITY_IAM

```

## Dry run update

```bash

aws cloudformation deploy \
  --template-file ./hbfl.start.template \
  --stack-name hbfl-stack \
  --parameter-overrides \
    InstanceTypeParameter=t2.nano
  --capabilities CAPABILITY_IAM
  --no-execute-changeset

```

## Update

```bash

aws cloudformation deploy \
  --template-file ./hbfl.start.template \
  --stack-name hbfl-stack \
  --parameter-overrides \
    InstanceTypeParameter=t2.nano
  --capabilities CAPABILITY_IAM

```

Or

```bash

aws cloudformation execute-change-set \
  --change-set-name arn:aws:cloudformation ...

```