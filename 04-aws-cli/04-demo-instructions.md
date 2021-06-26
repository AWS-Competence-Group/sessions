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

1. Configure AWS CLI with the credentials [profile]

```
aws configure --profile dev-account
```

1. Mention the service **AWS Secrets Manager**.

1. Google 'aws cli secretsmanager' and browse cli documentation for how to create a secret

1. Create a secret using the cli

```
aws secretsmanager create-secret --name delete-me --secret-string "Very Secret"
```

1. View secret in the web console

1. Illustrate how to configure AWS CLI for SSO on a separate profile

```
aws configure sso --profile my-sso
```

1. Demonstrate **get-caller-identity**

```
aws sts get-caller-identity

aws sts get-caller-identity --profile my-sso
```

1. Illustrate how the different profiles behaves when using the different credentials

```
aws s3 ls

aws s3 ls --profile my-sso
```

## Challenge

 - Create an MP3 file using the AWS CLI and the text to speach service **AWS Polly**
