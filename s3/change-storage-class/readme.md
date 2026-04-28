aws s3 mb s3://changestoragebucketlearning
echo "thaobeo" > thaoratbeo.txt
aws s3api put-object --bucket changestoragebucketlearning --key thaoratbeo.txt
echo "helloearth" > hiii.txt
aws s3api put-object --bucket changestoragebucketlearning --key hiii.txt --storage-class STANDARD_IA


