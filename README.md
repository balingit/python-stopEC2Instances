# python-stopEC2Instances
This is a very simple lambda function written in python that stops all running EC2 instances.  It is intended to be scheduled using Cloudwatch Events when the instances are no longer in use.

# Permissions
The following example files will create an IAM role with an inline policy.

## create-role-inline
The main script that runs AWS commands to create a role and create an inline policy.  The policy documents are on separate JSON files.

## lambda_trustpolicy.json
This is the trust relationship to give the lambda function the assumed role.

## ec2Stop_permission.json
An inline policy granted to the role.  The lambda function requires describe-instances and stop-instances permissions.

## Scheduling
Cloudwatch Events can use cron-like scheduling expressed in UTC timezone. To schedule to run every day at 12:00 UTC (00:00 NZST):

  0 12 * * ? *
