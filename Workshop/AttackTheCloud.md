# ☁️ AttackTheCloud Notes

Hands-on AWS cloud security labs using LocalStack and AWS CLI.


## Lab 1: Insecure S3 Bucket

<pre>
aws --endpoint-url=http://localhost:4566/ s3 ls --no-sign-request

aws --endpoint-url=http://localhost:4566/ s3 ls s3://fsecss-bucket/ --no-sign-request

aws --endpoint-url=http://localhost:4566/ s3 cp s3://fsecss-bucket/flag.txt flag.txt --no-sign-request </pre>

## Lab 2: S3 Bucket Versioning

<pre>
s3api get-bucket-versioning
  
s3api list-object-versions

s3api get-object </pre>

## Lab 3: Secrets Manager

<pre>
cd creds
cat workshop.txt
aws configure
secretsmanager list-secrets
secretsmanager get-secret-value </pre>

## Lab 4: Lambda Functions

- Step 1: Inspect Lambda
<pre>
lambda list-functions
lambda get-function
cd ..
wget lambda zip
7z x lambda-function.zip
subl lambda_function.py </pre>

- Step 2: Reverse and Solve (create solve.py to decode a hidden key used in the Lambda logic)
<pre>
import base64
encoded = 'KwwWEC0mFyEWcy0sHXVyHQ4jLwAGIw=='
key_bytes = base64.b64decode(encoded)
key = ''.join([chr(b ^ 0x42) for b in key_bytes])
print(key) </pre>

- Step 3: Run and invoke the Lambda function
<pre>
python solve.py
lambda invoke
cat response.json</pre>

## 🎯 More Cloud Security Challenges!

- [Big IAM Challenge](https://bigiamchallenge.com/challenge/1)
- [Flaws.cloud](http://flaws.cloud)
- [Flaws2.cloud](http://flaws2.cloud/)
- [CloudFoxable](https://cloudfoxable.bishopfox.com/challenges)
