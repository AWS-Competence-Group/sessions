## 04 Demo instructions

### Pre-Requirements

AWS Account with

  - ...

### Steps

1. Manually in the web console, create a KMS Key with an alias. Provide default values for key policy etc.

1. Show [AWS Cloudformation documentation for KMS][1]
   - Notify fields 
     - **KeyPolicy** (Required)
     - **EnableKeyRotation** (Optional)
     - **PendingWindowInDays** (Optional)

1. Create a CloudFormation template file based on KMS resources in [kms-key.yml](kms-key.yml)

1. Create a stack in web console based on the CloudFormation template.

1. Add S3 bucket that uses the KMS key for encryption.

1. Update the CloudFormation stack with the S3 bucket.

1. Verify KMS and S3 resources in web console.

1. Delete CloudFormation stack.

### Sample CLI Calls

## Encrypt and Decrypt file:

```
aws kms encrypt \
  --key-id alias/CloudFormationKeyAlias  \
  --plaintext fileb://demo-plaintext-file.txt  \
  --output text  \
  --query CiphertextBlob | base64  \
  --decode > demo-encrypted-file.txt
```

```
aws kms decrypt \
    --ciphertext-blob fileb://demo-encrypted-file.txt \
    --key-id alias/CloudFormationKeyAlias \
    --output text \
    --query Plaintext | base64 \
    --decode > demo-decrypted-file.txt
```


[1]: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-kms-key.html