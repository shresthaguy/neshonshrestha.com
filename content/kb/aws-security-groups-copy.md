---
title: "Copying AWS Security Groups Across VPCs"
date: 2026-08-02
lastmod: 2026-08-02
description: "How to import/export security groups between VPCs, regions, and accounts using AWS CLI."
category: "AWS"
tags: ["aws", "security-groups", "vpc", "shell-scripting"]
type: "solution"
---

## The Problem

Customers often need to replicate security group configurations when migrating workloads across VPCs, regions, or AWS accounts. This comes up during disaster recovery setup, multi-region deployments, or account migrations.

## Why This Isn't Straightforward

AWS doesn't provide a native one-click way to copy a security group to a different VPC. The console only lets you copy within the same VPC/region. If you're moving across regions or accounts, you're stuck manually recreating rules — which is error-prone when a security group has dozens of rules.

## The Approach

I built a shell script that uses AWS CLI + jq to automate the full process:

1. Export ingress and egress rules from the source security group
2. Create a new security group in the destination VPC
3. Revoke the default "allow all outbound" egress rule
4. Apply the exported rules to the new group

```bash
# Same account, different region
./copy-security-group -s us-east-1 -g sg-0abc1234 -d us-west-2 -v vpc-0xyz5678 -n my-sg-copy

# Cross-account using AWS CLI profiles
./copy-security-group -s us-east-1 -g sg-0abc1234 -d eu-west-1 -v vpc-0xyz5678 -n my-sg-copy \
    --source-profile account-a --dest-profile account-b
```

**Prerequisites:** AWS CLI configured, jq installed, and IAM permissions for `ec2:DescribeSecurityGroups`, `ec2:CreateSecurityGroup`, `ec2:AuthorizeSecurityGroupIngress`, `ec2:AuthorizeSecurityGroupEgress`, `ec2:RevokeSecurityGroupEgress`.

Source: [GitHub - copy-security-group](https://github.com/shresthaguy/copy-security-group)

## Verification

Tested across:
- Same account, different region (us-east-1 → us-west-2)
- Cross-account with separate AWS CLI profiles
- Security groups with empty rule sets (script handles gracefully)
- Script validates prerequisites (aws, jq) before running and cleans up temp files on exit

## Limitations

- Rules that reference other security group IDs (e.g., `sg-xxxxx`) won't be valid in a different VPC — those need manual adjustment
- Copies rules only, not tags or descriptions beyond the group name
- If the source SG references a prefix list that doesn't exist in the destination region, the rule will fail to apply
