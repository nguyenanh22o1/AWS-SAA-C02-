# create a bucket
aws s3 mb s3://learn-encryption-sse-s3

# create an file object
echo "dataheheh" > data.txt

# upload
aws s3 cp data.txt s3://learn-encryption-sse-s3

# chnage object to kms
aws kms list-keys
aws s3 cp s3://learn-encryption-sse-s3/data.txt s3://learn-encryption-sse-s3/data.txt \
  --sse aws:kms \
  --sse-kms-key-id yo key

# verify changed 

aws s3api head-object \
  --bucket learn-encryption-sse-s3 \
  --key data.txt