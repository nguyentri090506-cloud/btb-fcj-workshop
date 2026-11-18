---
title: "Amazon VPC"
weight: 3
chapter: false
pre: "<b> 5.4.3. </b> "
---

# 5.4.3. Amazon VPC

> **Source status, as reported by the BTB team (18 November 2026):** VPC, routes and IGW configured; exact subnet placement/egress to external providers must be recorded.

## Objective and actual role

Networking for public ALB and backend ECS tasks, including subnets, routes and Internet Gateway.

## Lab: inspect, document and verify the existing production setup

1. Open VPC → Your VPCs, select the existing BTB VPC and record the actual Region, VPC ID and CIDR; do not copy example CIDRs from a diagram.
2. Use the VPC resource map and Subnets view to record actual Availability Zones, public/private mapping and route-table associations.
3. Check the Internet Gateway attachment and public routes; a public ALB normally requires internet-reachable subnets with appropriate ingress rules.
4. Verify ECS tasks' real network placement and outbound connectivity toward Supabase, Cloudinary, Vietmap, SePay, Bedrock and SMTP; do not assume an Internet Gateway alone gives private tasks internet access.
5. Check the ALB security group allows intended HTTPS ingress and the ECS security group permits the backend application port only from ALB security group.
6. Capture the VPC map, route tables, security groups and ECS task network settings; mark private-route design as unresolved if not verified.

## Expected outcome / result recording

**Expected:** ALB health checks work, ECS can reach required third parties, and backend port is not directly internet-accessible.

**Actual:** `[FILL AFTER TEST: result, date/time, Region, resource, evidence]`

## Risks and operational notes

Public subnet/private subnet and number of Availability Zones must reflect current AWS Console. NAT Gateway / VPC endpoints are not presumed deployed.

## Screenshot evidence to capture

VPC resource map, subnet routes, SG inbound/outbound, ECS task networking.

**Suggested path:** `static/images/5-workshop/5.4.3-01.png` (capture from real Console; do not create a fake screenshot).

## Official reference

<https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html>
