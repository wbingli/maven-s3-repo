AWS S3 Maven Repository
=======================

This project demonstrates how to use AWS S3 as maven repository. [AWS Maven Wagon](https://github.com/spring-projects/aws-maven) plugin is used.

Demo Projects
=============

## s3
This project is a sample maven project. It's configured to be published to S3 based repository.

It is used to demonstrate maven artifacts publish to S3 based repository.


## s3-test
This project depends on **s3** project.

It is used to demonstrate resolving dependencies using S3 based repository with an `s3://` schema.

## s3-http-test
This project also depends on **s3** project.

It's also used to demonstrate resolving dependencies using S3 based repository, but directly with `http://` schema.

Configuration
=============

## Local AWS Account Settings
S3 access keys should be configured under `~/.m2/settings.xml`.

    <settings>
       <servers>
        <server>
          <id>aws-release</id>
          <username>AKIAIC5IC111111111</username>
          <password>ACF1111111111111111111111111111111</password>
        </server>
        <server>
          <id>aws-snapshot</id>
          <username>AKIAIC5IC111111111</username>
          <password>ACF1111111111111111111111111111111</password>
        </server>
      </servers>
    </settings>

## AWS Account Permissions
Proper AWS account permissions need to be granted to allow the account to write and read objects from S3.

They are required to publish artifacts to S3 or download artifacts via `s3://` schema.

You may use _AmazonS3FullAccess_ policy template for this permission.

## Use HTTP Schema for S3 Repository
If you want to use `http://` schema as maven repository, S3 bucket need to be configured as below:

### Enable website hosting
Only enable this, you can access S3 via HTTP.

Just go to S3 console, and enable **Static Website Hosting**.

### Configure Bucket Policy
You need to configure bucket policy so that those artifacts could be accessable. Example as below:

    {
      "Id": "Policy1397027253868",
      "Statement": [
        {
          "Sid": "Stmt1397027243665",
          "Action": [
            "s3:ListBucket"
          ],
          "Effect": "Allow",
          "Resource": "arn:aws:s3:::wbinglee-so-s3",
          "Principal": {
            "AWS": [
              "*"
            ]
          }
        },
        {
          "Sid": "Stmt1397027177153",
          "Action": [
            "s3:GetObject"
          ],
          "Effect": "Allow",
          "Resource": "arn:aws:s3:::wbinglee-so-s3/*",
          "Principal": {
            "AWS": [
              "*"
            ]
          }
        }
      ]
    }
