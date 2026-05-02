# create a bucket

aws s3api create-bucket --bucket cors-learing-aws --region us-east-1

# update block public access
aws s3api put-public-access-block \
    --bucket cors-learing-aws \
    --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"

# turn on static website hosting

aws s3api put-bucket-policy --bucket cors-learing-aws --policy file://policy.json

aws s3api put-bucket-website --bucket cors-learing-aws --website-configuration file://website.json
# upload index.html file 
aws s3 cp index.html s3://cors-learing-aws
aws s3api get-bucket-website --bucket cors-learing-aws 
# apply cors policy

# create api gateway with mock response and set the endpoint 

curl -X POST -H "Content-Type: application/json" https://l0prro3mr3.execute-api.us-east-1.amazonaws.com/prod/example