## About

Amazon Web Services node.js module. Originally a fork of [aws-lib](https://github.com/livelycode/aws-lib/).

## Installation

Either manually clone this repository into your node_modules directory, or the recommended method:

> npm install aws2js

## Project and Design goals

 * HTTPS-only APIs communication
 * Proper error reporting
 * Simple to write clients for a specific AWS service (abstracts most of the low level plumbing)
 * Simple to use AWS API calls
 * Higher level clients for specific work flows
 * Proper documentation

## Supported services

 * Amazon EC2 (Elastic Compute Cloud)
 * Amazon RDS (Relational Database Service)
 * Amazon SES (Simple Email Service)
 * Amazon ELB (Elastic Load Balancing)
 * Amazon S3 (Simple Storage Service)
 * Amazon IAM (Identity and Access Management)
 * Amazon Auto Scaling

## Usage mode

 * [EC2 client](https://github.com/SaltwaterC/aws2js/wiki/EC2-Client)
 * [RDS client](https://github.com/SaltwaterC/aws2js/wiki/RDS-Client)
 * [SES client](https://github.com/SaltwaterC/aws2js/wiki/SES-Client)
 * [ELB client](https://github.com/SaltwaterC/aws2js/wiki/ELB-Client)
 * [S3 client](https://github.com/SaltwaterC/aws2js/wiki/S3-Client)
 * [IAM client](https://github.com/SaltwaterC/aws2js/wiki/IAM-Client)
 * [Auto Scaling client](https://github.com/SaltwaterC/aws2js/wiki/Auto-Scaling-Client)

## API versions

The clients try to use the latest available API version. This applies for the query APIs. If this breaks due to backward incompatibility (although the AWS guys should not do this), use the specific API version that applies to the case. The [client.setApiVersion()](https://github.com/SaltwaterC/aws2js/wiki/client.setApiVersion%28%29) helper should be very handy for this specific case.

## HTTP Agent setting

The clients expose the [client.setMaxSockets()](https://github.com/SaltwaterC/aws2js/wiki/client.setMaxSockets%28%29) helper for changing the https.Agent.defaultMaxSockets property.

## Gotcha

Currently the used [mime](https://github.com/bentomas/node-mime) module works by making a file extension lookup. The S3 client is affected by this issue. aws2js will eventually integrate the [mime-magic](https://github.com/SaltwaterC/mime-magic) module that provides proper mime auto-detection. Currently mime-magic doens't have binary integration with node.js while spawning file(1) commands under OS X is slower than a native integration.
