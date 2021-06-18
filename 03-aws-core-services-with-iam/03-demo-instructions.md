## 03 Demo instructions

### Pre-Requirements

AWS Account with

  - Default VPC
  - Instance profile with access policies **AmazonSSMManagedInstanceCore** and **AmazonS3FullAccess**
  - Route53 zone
  - S3 bucket with static website hosting enabled

### Steps

1. Manually create a EC2 Linux 2 machine:
  - Assign public IP
  - Using instance profile **GovSessionManagerInstanceProfile**
  - Allow HTTP (port 80) for 0.0.0.0/0
  - Attach additional EBS volume

1. Connect to the machine using Session Manager

1. Run these commands as to install web server on machine
```
sudo -s
```
```
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo "<h1 style=\"color: green; text-align: center; padding: 100px 0;\">Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```

1. Browse to the Public IPv4 DNS for the machine to verify web server returns response.

1. Create a 'www' **A-record** pointing to EC2 server public IP in Route53.

1. Browse to the www-record in web browser.

1. Connect to instance using Session Manager

1. Put object into S3 bucket from the server using its instance profile and AWS CLI
```
aws s3api put-object --bucket tretton37-static-site-bucket --body /var/www/html/index.html --key index.html --content-type text/html
```

1. Browse to the index.html via its S3 url.

## 10.000$ question

What was the reason for allowing the AWS CLI call to put objects in the S3 bucket?

