# ☁️ AttackTheCloud Workshop Notes

Hands-on AWS cloud security labs using LocalStack and AWS CLI.

## � Lab 1: Insecure S3 Bucket

```bash
aws --endpoint-url=http://localhost:4566/ s3 ls --no-sign-request

aws --endpoint-url=http://localhost:4566/ s3 ls s3://fsecss-bucket/ --no-sign-request

aws --endpoint-url=http://localhost:4566/ s3 cp s3://fsecss-bucket/flag.txt flag.txt --no-sign-request

## � Lab 2: S3 Bucket Versioning

```bash
s3api get-bucket-versioning
s3api list-object-versions
s3api get-object

## � Lab 3: Secrets Manager

```bash
cd creds
cat workshop.txt
aws configure
secretsmanager list-secrets
secretsmanager get-secret-value

## � Lab 4: Lambda Functions

```bash
lambda list-functions
lambda get-function
cd ..
wget lambda zip
7z x lambda-function.zip
subl lambda_function.py

<pre> ```python
import base64
encoded = 'KwwWEC0mFyEWcy0sHXVyHQ4jLwAGIw=='
key_bytes = base64.b64decode(encoded)
key = ''.join([chr(b ^ 0x42) for b in key_bytes])
print(key) ``` </pre>

lambda invoke
cat response.json

# � More Cloud Security Challenges !
https://bigiamchallenge.com/challenge/1
http://flaws.cloud
http://flaws2.cloud/
https://cloudfoxable.bishopfox.com/challenges
