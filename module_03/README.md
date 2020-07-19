# Cloudformation

Cloudformation allow do define infrastructure as code. Like Terraform.

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

# Elasticbeanstalk

Elasticbeanstalk works in an Application context. It uses Cloudformation under the hood.

It allow to deploy multiple environment like staging and prod in one application.

Elasticbeanstalk works better for one application.

1. Install `eb` cli : `brew install awsebcli`

2. go to webapp root

3. Clean node_modules : `rm -rf node_modules`

4. Init elastic beanstalk run `eb init`

5. Create with `eb create`

6. Update with `eb deploy`

7. Delete with `eb terminate`