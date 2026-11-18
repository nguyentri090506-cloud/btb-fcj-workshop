---
title: "Testing & Live Demo"
weight: 11
chapter: false
pre: "<b> 5.11. </b> "
---

# 5.11. End-to-End Testing, Validation & Live Demo

**This is a reproducible test plan, not a statement that all tests passed.** Use real test accounts, test records, safe read-only APIs and sanitized screenshots. Replace TODO with the actual result, timestamp, environment and evidence file.

| ID | Scenario | Expected result | Actual evidence |
|---|---|---|---|
| T01 | Open frontend via HTTPS | React loads through CloudFront | TODO |
| T02 | Refresh nested React route | SPA route resolves as designed | TODO |
| T03 | HTTPS API request | ALB responds; ECS target healthy | TODO |
| T04 | Guest lists catalog/prices | Public data per API policy | TODO |
| T05 | Customer account activation via Admin + Gmail OTP | Only approved and verified Customer can log in | TODO |
| T06 | Unauthorized role submits Staff Quote approval | Backend denies operation | TODO |
| T07 | Volume Pricing and Quote approval | Price rules enforced by backend | TODO |
| T08 | Confirm order with a missing SKU | No Order, no partial stock reservation | TODO |
| T09 | Valid test SePay webhook | Backend confirms one event once | TODO |
| T10 | Invalid/duplicate SePay webhook | No fraudulent/double paid transition | TODO |
| T11 | Delivery Staff completes assigned trip | Order status changes only when business conditions hold | TODO |
| T12 | Backend AI endpoint → Bedrock | Valid schema/permission after test; currently pending | TODO |
| T13 | WAF frontend and BE rule samples | FE/BE associations correct; BE limit **Count** only | TODO |
| T14 | CloudWatch Logs/Alarms → SNS | Logs visible; documented alarm notification if observed | TODO |
| T15 | CloudWatch RUM/Cognito | Live browser events reach app monitor; currently pending | TODO |
| T16 | GitHub Actions FE/BE release | SHA/digest/build verified across deploy targets | TODO |
| T17 | Cloudinary/Vietmap | Images and map/address route work | TODO |

## Safe commands (replace placeholders)

```powershell
curl.exe -I https://<FRONTEND_DOMAIN>/
curl.exe -i https://<API_DOMAIN>/<ACTUAL_PUBLIC_API_PATH>
Resolve-DnsName <FRONTEND_DOMAIN>
Resolve-DnsName <API_DOMAIN>
```

Avoid destructive load tests, real bank transfers, real addresses or sensitive account screenshots. Do not assume `/actuator/health` or any particular path is public; consult Swagger/OpenAPI first.

## Live demonstration

- Frontend URL: `[TODO]`
- API domain (not credentials): `[TODO]`
- GitHub Actions FE/BE run: `[TODO]`
- Test date and deployed commit/image digest: `[TODO]`
- Screenshot/video evidence: `[TODO]`
- Known limitations and failed cases: `Bedrock production endpoint pending; RUM ingestion pending; BE WAF Count mode` (update only after verified changes).
