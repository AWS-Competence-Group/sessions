## 04 Demo instructions

### Pre-Requirements

AWS Account with

  - An IAM User with following permission: **arn:aws:iam::aws:policy/SecretsManagerReadWrite**

  - Make sure demo computer has no [default] AWS CLI profile configured

### Steps

1. In the web console, create long term access keys for demo user

1. Configure AWS CLI with the credentials [default]

```
aws configure
```

1. Mention the service **AWS Secrets Manager**.

1. Create a secret manually in web console.

1. Google 'aws cli secretsmanager' and browse cli documentation for how to create a secret

1. Create a secret using the cli

```
aws secretsmanager create-secret --name delete-me --secret-string "Very Secret"
```

1. View secret in the web console

1. Describe secrets with cli

```
aws secretsmanager describe-secrets
```

#### AWS CLI for SSO

1. Illustrate how to configure AWS CLI for SSO on a separate profile

```
aws configure sso --profile my-sso
```

1. Demonstrate **get-caller-identity**

```
aws sts get-caller-identity

aws sts get-caller-identity --profile my-sso
```

1. Why do we get an access denied when running the first command?

```
aws s3 ls

aws s3 ls --profile my-sso
```

1. Delete the access keys on the demo IAM User.

## Bonus

1. Demonstrate AWS CloudShell and run ```aws sts get-caller-identity```

## Challenge

 - Create an MP3 file using the AWS CLI and the text to speech service **AWS Polly**. 

 - Post the message on our community channel.
