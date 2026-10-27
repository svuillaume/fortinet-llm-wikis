---
title: Appendix A - Amazon Policy Usage
summary: AWS IAM permissions granted to FortiCASB per service and the FortiCASB feature each one supports.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Appendix A: Amazon policy usage

FortiCASB communicates with AWS by being granted permissions to read AWS account resource configuration, through a custom JSON policy created in AWS. The tables list the permissions per service and their purpose in FortiCASB. See [AWS S3 onboarding](../onboarding/aws-s3.md) for setup. Wildcards (e.g. `Describe*`) are as printed in the guide.

[src: forticasb-admin-guide-24-4-b, p.558]

"Resource List", "profile", "Topology" and "Risk assessment" below refer to FortiCASB views for the service.

## Read permissions and their purpose

| Service | Permissions | Purpose |
|---|---|---|
| RDS | rds:Describe*, rds:DownloadDBLogFilePortion, rds:ListTagsForResource | Resource List, RDS profile, RDS Topology, RDS Risk assessment |
| EFS | elasticfilesystem:Describe* | Resource List, EFS profile, EFS Risk assessment |
| ELB | elasticloadbalancing:Describe* | Resource List, Listener/Load Balancer/Target Group profile, ELB Topology, ELB Risk assessment |
| Certificate Manager | acm:List*, acm:Describe* | Resource List, ACM Certificate profile and Risk assessment |
| CloudFront | cloudfront:List*, cloudfront:Get* | Resource List, CloudFront profile, CloudFront Risk assessment |
| EKS | eks:ListUpdates, eks:DescribeUpdate, eks:DescribeCluster, eks:ListClusters | Resource List, EKS profile, EKS Topology |
| KMS | kms:List*, kms:Describe*, kms:Get* | Resource List, KMS Key profile, KMS Risk assessment |
| Lambda | lambda:List*, lambda:GetPolicy | Resource List, Lambda profile, Lambda Risk assessment |
| SQS (read) | sqs:ReceiveMessage, GetQueueUrl, GetQueueAttributes, ListQueueTags, ListQueues, ListDeadLetterSourceQueues | Resource List, SQS profile, SQS Risk assessment |
| IAM | iam:List*, iam:Get*, iam:SimulateCustomPolicy, iam:GenerateCredentialReport, iam:SimulatePrincipalPolicy | Resource List, IAM profile, IAM Risk assessment |
| Redshift | redshift:Describe* | Resource List, Redshift profile, Redshift Risk assessment |
| ECS | ecs:Describe*, ecs:List* | Resource List, ECS profile, ECS Topology |
| EC2 | ec2:Describe*, SearchTransitGatewayRoutes, GetTransitGatewayAttachmentPropagations, GetTransitGatewayRouteTablePropagations, GetTransitGatewayRouteTableAssociations | Resource List; VPC, Route Table, Subnet, Network ACL, Security Group, AMI, EC2, EBS volume and snapshot profiles; VPC/Subnet/Network ACL/Security Group/EC2 Topology; VPC, Subnet, Security Group, AMI, EC2, EBS Risk assessment |
| CloudWatch Logs | logs:Get*, logs:Describe*, logs:FilterLogEvents | Feature "Traffic" |
| Glacier | glacier:ListVaults, glacier:GetVaultAccessPolicy | Resource List, Glacier profile, Glacier Risk assessment |
| CloudFormation | cloudformation:ListStack*, GetTemplate, DescribeStack* | Resource List, CloudFormation profile and Risk assessment |
| S3 | s3:GetBucket*, GetReplicationConfiguration, GetLifecycleConfiguration, GetInventoryConfiguration, ListBucket, ListBucketMultipartUploads, GetAccountPublicAccessBlock, ListAllMyBuckets, GetObject, GetObjectVersion, GetObjectVersionTagging, GetObjectAcl, GetObjectVersionAcl, HeadBucket, ListMultipartUploadParts, GetAnalyticsConfiguration, GetObjectVersionForReplication, ListBucketByTags, ListBucketVersions, GetAccelerateConfiguration, GetObjectVersionTorrent, GetEncryptionConfiguration, GetObjectTagging, GetMetricsConfiguration, GetObjectTorrent | Resource List, S3 bucket profile, S3 Risk assessment, feature "Buckets" |
| Pinpoint Email / SES | ses:List*, ses:Get* | Resource List, SES profile, SES Risk assessment |
| CloudTrail | cloudtrail:GetTrailStatus, LookupEvents, DescribeTrails, ListTags, GetEventSelectors | Resource List, CloudTrail profile, CloudTrail Risk assessment, feature "Activity" |
| Elasticsearch Service | es:List*, es:Describe* | Resource List, ElasticSearch profile and Risk assessment |
| Route 53 | Read-only List*/Get* actions (e.g. ListHostedZones, ListResourceRecordSets, GetHealthCheck, GetHostedZone, GetTrafficPolicy, ListQueryLoggingConfigs; about 30 actions listed) | Resource List, Route53 profile, Route53 Risk assessment |
| SNS | sns:Get* | Resource List, SQS profile, SQS Risk assessment (as printed) |
| CloudWatch | cloudwatch:Describe* | CloudWatch Risk assessment |

[src: forticasb-admin-guide-24-4-b, p.558-562]

## Write permissions: autofix of Risk assessment policies

| Service | Permissions | Autofix of policy |
|---|---|---|
| RDS | rds:ModifyDBInstance | "RDS instances should not be publicly accessible" |
| ELB | elasticloadbalancing:ModifyLoadBalancerAttributes | "ELB/ALB deletion protection should be enabled" |
| CloudFront | cloudfront:UpdateDistribution | "CloudFront should use secure ciphers for distribution" |
| KMS | kms:EnableKeyRotation | "KMS key rotation should be enabled" |
| IAM | iam:UpdateAccountPasswordPolicy | "Password requirements should be enforced" (the guide labels this under Redshift; as printed) |
| Redshift | redshift:ModifyClusterParameterGroup (with Describe*) | "Redshift database should use SSL for connections" |
| EC2 | ec2:ModifySnapshotAttribute | "EBS snapshots should not be publicly accessible" |
| EC2 | ec2:RevokeSecurityGroupEgress, ec2:RevokeSecurityGroupIngress | "Default Security Group should block all inbound traffic" |
| S3 | s3:PutBucketVersioning, PutBucketAcl, PutBucketPolicy, PutObjectAcl, PutObjectVersionAcl | "S3 buckets should not be publicly available" |
| CloudTrail | cloudtrail:StartLogging, cloudtrail:UpdateTrail | "CloudTrail bucket should not be publicly accessible" |

[src: forticasb-admin-guide-24-4-b, p.558-561]

## Notification integration permissions

| Service | Permissions | Purpose |
|---|---|---|
| SQS | sqs:TagQueue, UntagQueue, ChangeMessageVisibility, ChangeMessageVisibilityBatch, CreateQueue, DeleteMessage, DeleteMessageBatch, DeleteQueue, PurgeQueue, SendMessage, SendMessageBatch, SetQueueAttributes | FortiCASB Notification integration with AWS SQS |
| SNS | sns:* | FortiCASB Notification integration with AWS SNS |

[src: forticasb-admin-guide-24-4-b, p.559-562]

## Related
- [Appendix index](index.md)
- [AWS S3 onboarding](../onboarding/aws-s3.md)
