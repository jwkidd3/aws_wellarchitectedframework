# Lab 2 — IAM Least Privilege Review

**Duration:** ~30 minutes
**Pillar:** Security

## Objective

Read a sample IAM policy attached to an application role, identify least-privilege violations, and rewrite it so the application can do its job — and nothing else.

## Scenario

You are reviewing the role `app-orders-processor`. The application:

- Reads order events from a single SQS queue: `arn:aws:sqs:us-east-1:111122223333:orders-incoming`
- Writes processed orders to one DynamoDB table: `arn:aws:dynamodb:us-east-1:111122223333:table/orders`
- Writes structured logs to CloudWatch Logs (its own log group only)
- Runs on EC2 in account `111122223333`, region `us-east-1`

## The Current Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AppAccess",
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    },
    {
      "Sid": "ExtraStuff",
      "Effect": "Allow",
      "Action": [
        "s3:*",
        "iam:PassRole",
        "dynamodb:*",
        "sqs:*",
        "logs:*"
      ],
      "Resource": "*"
    }
  ]
}
```

## Tasks

1. **List every violation you can find.** Aim for at least five. Consider:
   - Action wildcards
   - Resource wildcards
   - Privileges the workload does not need at all
   - Privilege escalation risks
   - Cross-region or cross-account exposure
2. **Rewrite the policy** so it grants only what the workload actually needs. Constrain by action *and* resource ARN.
3. **Bonus:** add a `Condition` that restricts the role to the `us-east-1` region.

## Hints

- DynamoDB actions you likely need: `GetItem`, `PutItem`, `UpdateItem`, `BatchWriteItem`
- SQS actions you likely need: `ReceiveMessage`, `DeleteMessage`, `GetQueueAttributes`
- CloudWatch Logs: `CreateLogStream`, `PutLogEvents` — scope to the app's log group ARN
- A condition key for region: `aws:RequestedRegion`

## Sample Solution (one possible answer)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadOrderQueue",
      "Effect": "Allow",
      "Action": [
        "sqs:ReceiveMessage",
        "sqs:DeleteMessage",
        "sqs:GetQueueAttributes"
      ],
      "Resource": "arn:aws:sqs:us-east-1:111122223333:orders-incoming"
    },
    {
      "Sid": "WriteOrdersTable",
      "Effect": "Allow",
      "Action": [
        "dynamodb:GetItem",
        "dynamodb:PutItem",
        "dynamodb:UpdateItem",
        "dynamodb:BatchWriteItem"
      ],
      "Resource": "arn:aws:dynamodb:us-east-1:111122223333:table/orders"
    },
    {
      "Sid": "WriteAppLogs",
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "arn:aws:logs:us-east-1:111122223333:log-group:/app/orders-processor:*"
    }
  ],
  "Statement_ConditionExample": {
    "Condition": {
      "StringEquals": { "aws:RequestedRegion": "us-east-1" }
    }
  }
}
```

## Discussion

- How would you detect a policy like the original *before* it reaches production?
- What AWS services help enforce or surface least-privilege issues automatically?
  (Hint: IAM Access Analyzer, Service Control Policies, Config rules.)
