## 02 Demo instructions

### Pre-Requirements

  - AWS Account with IAM user login

### Steps

1. Creation of **Demo IAM user** and attached **ReadOnlyAccess** policy

1. Sign in with **Demo IAM user** in incognito window

1. Simulate write access by creating an S3 bucket

1. Attach **AmazonS3FullAccess** to **Demo IAM user**

1. Verify **Demo IAM user** now can create a bucket

1. Attach an inline policy that deny *s3:DeleteBucket* action.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "DenyDeleteBucket",
            "Effect": "Deny",
            "Action": "s3:DeleteBucket",
            "Resource": "*"
        }
    ]
}
```

1. Try to delete the bucket

1. Remove the inline deny *s3:DeleteBucket* action.

1. Verify **Demo IAM user** now can delete the bucket.


