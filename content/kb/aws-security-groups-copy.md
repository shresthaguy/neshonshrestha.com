---
title: "Copying AWS Security Groups Across VPCs"
date: 2026-08-02
lastmod: 2026-08-02
description: "How to import/export security groups between VPCs, regions, and accounts using AWS CLI."
category: "AWS"
tags: ["aws", "security-groups", "vpc", "shell-scripting"]
---

## The Problem

AWS doesn't provide a native one-click way to copy a security group from one VPC to another — especially across regions or accounts.

## The Solution

I built a shell script that uses AWS CLI + jq to:

1. Export an existing security group's rules from a source VPC
2. Create a new security group in the destination VPC
3. Revoke default egress rules
4. Apply the original ingress and egress rules to the new group

## Prerequisites

- AWS CLI configured (with profiles for cross-account)
- jq installed

## Source

[View on GitHub](https://github.com/shresthaguy/copy-security-group)

## Key AWS CLI Commands Used

- `aws ec2 describe-security-groups` — read existing rules
- `aws ec2 create-security-group` — create in target VPC
- `aws ec2 authorize-security-group-ingress` — apply inbound rules
- `aws ec2 authorize-security-group-egress` — apply outbound rules

## Notes

- For cross-account usage, AWS CLI must be configured with multiple profiles
- Security group IDs referenced in rules won't be valid in a different VPC — those rules need manual adjustment
