# Required AWS Policies (optional)

If a user WITHOUT admin rights wants to perform a deployment, they need to add the following policies:

#### CDKBootstrapPolicy – policy for region [bootstrapping] (https://docs.aws.amazon.com/cdk/v2/guide/bootstrapping.html).

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:GetRole",
                "iam:CreateRole",
                "iam:GetRolePolicy",
                "iam:PutRolePolicy",
                "iam:DetachRolePolicy",
                "iam:DeleteRolePolicy",
                "iam:TagRole",
                "iam:AttachRolePolicy",
                "iam:DeleteRole"
            ],
            "Resource": [
                "arn:aws:iam::414675527874:role/cdk-cme-*"
            ]
        },
        {
            "Action": [
                "cloudformation:*"
            ],
            "Resource": [
                "arn:aws:cloudformation:*:414675527874:stack/CMEToolkit/*"
            ],
            "Effect": "Allow"
        },
        {
            "Sid": "S3Access",
            "Effect": "Allow",
            "Action": [
                "s3:CreateBucket",
                "s3:GetEncryptionConfiguration",
                "s3:PutEncryptionConfiguration",
                "s3:PutBucketVersioning",
                "s3:GetBucketPolicy",
                "s3:PutBucketPublicAccessBlock",
                "s3:PutBucketPolicy",
                "s3:DeleteBucketPolicy"
            ],
            "Resource": [
                "arn:aws:s3:::cdk-cme-*"
            ]
        },
        {
            "Sid": "ECRAccess",
            "Effect": "Allow",
            "Action": [
                "ecr:SetRepositoryPolicy",
                "ecr:GetLifecyclePolicy",
                "ecr:PutImageScanningConfiguration",
                "ecr:DescribeRepositories",
                "ecr:CreateRepository",
                "ecr:DeleteRepository"
            ],
            "Resource": [
                "arn:aws:ecr:*:414675527874:repository/cdk-cme-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "ssm:GetParameter*",
                "ssm:PutParameter*",
                "ssm:DeleteParameter*"
            ],
            "Resource": "arn:aws:ssm:*:414675527874:parameter/cdk-bootstrap/cme/*"
        }
    ]
}
```

#### CDKDeployPolicy – policy for CME stack deployment

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "sts:AssumeRole"
            ],
            "Resource": [
                "arn:aws:iam::414675527874:role/cdk-cme-*"
            ]
        }
    ]
}
```
