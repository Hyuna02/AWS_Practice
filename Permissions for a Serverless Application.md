# Serverless Application Lab with AWS

## 🧠 Key Concepts

This practice lab demonstrates how to build a **secure**, **scalable**, and **cost-effective** serverless architecture using the following AWS services:

- **AWS Lambda**: Run backend code without provisioning or managing servers.
- **Amazon S3**: Object storage service for storing files, logs, and static content.
- **Amazon DynamoDB**: Fully managed NoSQL database service for key-value and document data.
- **IAM (Identity and Access Management)**: Securely manage access to AWS services and resources using roles and policies.

---

## 🔧 Practice Steps

### 1) Create an Amazon S3 Bucket

- **Bucket Name**: `my-diy-lab-bucket`

#### Bucket Policy Example

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::<account-id>:role/diy_lambda_role"
      },
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::my-diy-lab-bucket/*"
    }
  ]
}
```

---

### 2) Create a DynamoDB Table

- **Table Name**: `DiyItems`
- **Primary Key**: `itemId` (String)

---

### 3) Create an AWS Lambda Function

- **Function Name**: `diy_function`
- **IAM Execution Role**: `diy_lambda_role`
- **Permissions Needed**:
  - `s3:PutObject` on the S3 bucket
  - `dynamodb:PutItem` on the DynamoDB table
- **Environment Variable**:
  - `BUCKET_NAME = my-diy-lab-bucket`

#### Lambda Function Code (Python)

```python
import boto3
import os

s3 = boto3.client('s3')
dynamodb = boto3.resource('dynamodb')

def lambda_handler(event, context):
    bucket_name = os.environ['BUCKET_NAME']
    key = 'test-upload.txt'
    content = 'This is a test file from Lambda.'

    # Upload file to S3
    s3.put_object(Bucket=bucket_name, Key=key, Body=content)

    # Write item to DynamoDB
    table = dynamodb.Table('DiyItems')
    table.put_item(Item={'itemId': 'test1', 'value': 'Lambda write success'})

    return {
        'statusCode': 200,
        'body': f'File uploaded to {bucket_name}/{key} and DynamoDB write complete.'
    }
```

---

### 4) Invoke the Lambda Function

- Invoke manually from the Lambda console or via a test event.

**Expected Results**

- ✅ `test-upload.txt` is uploaded to S3 bucket `my-diy-lab-bucket`.
- ✅ An item with `itemId='test1'` is written to DynamoDB table `DiyItems`.

---

## 🖼️ Permissions Diagram

![Permissions for a Serverless Application](https://github.com/Hyuna02/AWS_Practice/blob/main/ExploretheAmazonBedrockPlaygrounds.png)
