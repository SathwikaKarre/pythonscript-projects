## AWS Cloud Cost Optimization – Automating the Cleanup of Unused EBS Snapshots
### Introduction
Amazon Elastic Block Store (EBS) snapshots provide a way to back up your EC2 volumes, but over time, unused snapshots can accumulate and increase storage costs. This guide details how to automate the detection and deletion of stale EBS snapshots using an AWS Lambda function.

## Objective
The goal is to identify and remove EBS snapshots that are no longer associated with active EC2 instances, reducing storage costs.

## Solution Approach

1️. Understanding Stale Snapshots
EBS snapshots are incremental backups of EC2 volumes.
When an EC2 instance is terminated, its associated EBS volume may also be deleted, but snapshots remain in AWS indefinitely.
Unused snapshots can lead to unnecessary storage costs.

2️. Steps to Automate Snapshot Cleanup
Retrieve all snapshots owned by the AWS account.
Fetch all active EC2 instances (running or stopped).
Compare each snapshot to determine if its associated volume still exists.
Delete snapshots that are no longer linked to any active instance.

## Implementation Using AWS Lambda
### Prerequisites
An AWS Lambda function with a role that has permissions to manage EBS snapshots and EC2 instances.
IAM Role Permissions required:
    ec2:DescribeSnapshots
    ec2:DescribeInstances
    ec2:DeleteSnapshot

## How It Works
Fetches all snapshots in the AWS account.
Identifies active EC2 instances and collects volume IDs in use.
Compares snapshot volume IDs against active volume IDs.
Deletes snapshots that are not linked to any active instance.

## Conclusion
By automating stale snapshot removal, you can significantly reduce AWS storage costs while keeping essential backups. Deploy this solution and monitor cost savings over time. 
