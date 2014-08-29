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
S3 access keys should be configured under `~/.m2/settings.xml`.
