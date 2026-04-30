# create a bucket
aws s3 mb s3://bucket-policy-learning-example

aws s3api put-bucket-policy --bucket bucket-policy-learning-example --policy file://policy.json

# in other account
-- list bucket
-- create new txt file
-- upload new txt file to bucket-policy-learning-example bucket

