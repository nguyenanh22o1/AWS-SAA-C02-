# Create a bucket

aws s3api create-bucket --bucket acl-learning-example-asdfasfasf --region us-east-1

## Turn of block public access

aws s3api put-public-access-block \
    --bucket acl-learning-example-asdfasfasf \
    --public-access-block-configuration "BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=true,RestrictPublicBuckets=true"

# get 
aws s3api get-public-access-block --bucket acl-learning-example-asdfasfasf

# setup ownership  -> enable acl
aws s3api put-bucket-ownership-controls --bucket acl-learning-example-asdfasfasf --ownership-controls="Rules=[{ObjectOwnership=BucketOwnerPreferred}]"