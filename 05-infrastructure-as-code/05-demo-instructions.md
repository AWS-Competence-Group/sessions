## 04 Demo instructions

### Pre-Requirements

AWS Account with

  - ...

### Steps

1. Manually in the web console, create a KMS Key with an alias. Provide default values for key policy etc.

1. 


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

