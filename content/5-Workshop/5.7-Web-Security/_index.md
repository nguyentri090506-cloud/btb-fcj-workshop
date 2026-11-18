---
title: "Web Delivery & Security"
weight: 7
chapter: false
pre: "<b> 5.7. </b> "
---

# 5.7. Web Delivery & Security

This phase documents the actual reported BTB resources. Read each service lab; fill out outcomes and screenshots from the real environment.

- [5.7.1. AWS Certificate Manager (ACM)](5.7.1-aws-certificate-manager/) — TLS certificates for frontend CloudFront domain and backend ALB API domain.
- [5.7.2. Amazon CloudFront](5.7.2-amazon-cloudfront/) — Delivers the React SPA from S3 with HTTPS, caching and WAF integration.
- [5.7.3. Amazon Route 53](5.7.3-amazon-route-53/) — DNS records direct frontend and API hostnames to CloudFront and ALB.
- [5.7.4. AWS WAF (Frontend & Backend)](5.7.4-aws-waf/) — Web ACLs filter or count frontend CloudFront and backend ALB requests.
