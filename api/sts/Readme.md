## Create a user with no permission

aws iam create-user \
    --user-name Thao

## generate out access key

aws iam create-access-key \
    --user-name Thao \
    --output table

# get sts get-caller-identity
aws sts get-caller-identity  (iam aws-example account)
aws sts get-caller-identity --profile thaobeo  (iam aws thaobeo account)

## display aws s3 bucket using iam thaobeo from main account
aws s3 ls --profile thaobeo
this iam dont have access to s3 YETTTTTT
aws: [ERROR]: An error occurred (AccessDenied) when calling the ListBuckets operation: User: 

## add iam thao with policy to access allow assume
aws iam put-user-policy \
  --user-name Thao \
  --policy-name allow-assume-sts-role \
  --policy-document '{
    "Version": "2012-10-17",
    "Statement": [{
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "arn:aws:iam::743673022279:role/sts-learning-cloudformation-deploy-StsRole-A6Kuo8ZbAMt4"
    }]
  }'



## use new user credentials and assume role
aws sts assume-role \
    --role-arn arn:aws:iam::743673022279:role/sts-learning-cloudformation-deploy-StsRole-A6Kuo8ZbAMt4 \
    --role-session-name s3-access-via-sts
    --profile sts 


## Return 

  --role-arn arn:aws:iam::743673022279:role/sts-learning-cloudformation-deploy-StsRole-A6Kuo8ZbAMt4 \
  --role-session-name s3-access-via-sts \
  --profile thaobeo
{
    "Credentials": {
        "AccessKeyId": "",
        "SecretAccessKey": "",
        "SessionToken": "",
        "Expiration": "2026-05-07T20:50:46+00:00"
    },
    "AssumedRoleUser": {
        "AssumedRoleId": "AROA22JS5Y5DWBCJAYTXW:s3-access-via-sts",
        "Arn": "arn:aws:sts::743673022279:assumed-role/sts-learning-cloudformation-deploy-StsRole-A6Kuo8ZbAMt4/s3-access-via-sts"
    }
}

## Export to CLI using previous temp cred return 
export AWS_ACCESS_KEY_ID=
export AWS_SECRET_ACCESS_KEY=
export AWS_SESSION_TOKEN=

## Create data.txt file
echo "data" > data.txt

## Upload to s3
aws s3 cp data.txt s3://api-sts-testing-cloudform

## List object in bucket
aws s3 ls s3://api-sts-testing-cloudform

## Caller Identity 
aws sts get-caller-identity

return 
{
    "UserId": "AROA22JS5Y5DWBCJAYTXW:s3-access-via-sts",
    "Account": "743673022279",
    "Arn": "arn:aws:sts::743673022279:assumed-role/sts-learning-cloudformation-deploy-StsRole-A6Kuo8ZbAMt4/s3-access-via-sts"
}
