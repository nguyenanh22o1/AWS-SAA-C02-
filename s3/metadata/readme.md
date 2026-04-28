aws s3 mb s3://meta-example-tutorial

echo "thaobeo" > thaoratbeo.txt

aws s3api put-object --bucket meta-example-tutorial --key thaorat.txt --metadata NguoiYeu=Thao

aws s3api put-object --bucket meta-example-tutorial --key thaoratbeo.txt --metadata NguoiYeu=Thao

aws s3api head-object --bucket meta-example-tutorial --key thaoratbeo.txt