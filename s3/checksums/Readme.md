### create a new s3 bucket

``` md
aws s3 mb s3://checksums-bucketexmaple
```

### create a file to do checksum

```
echo "Hello Mars" > myfile.txt
````

### get a check sum of a file

```
aws s3 cp myfile.txt s3://checksums-bucketexmaple
aws s3api head-object --bucket checksums-bucketexmaple -key myfile.txt
```