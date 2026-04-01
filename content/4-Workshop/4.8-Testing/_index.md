---
title: "End-to-End Testing"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

After completing all deployment steps, perform the following smoke tests to verify the entire system is working correctly.

---

## Smoke Test Checklist

| # | Test | Expected Result |
|---|---|---|
| 1 | Access Frontend URL (Amplify) | Login page renders correctly |
| 2 | Register a new account | Receive OTP email; account created successfully |
| 3 | Log in with credentials | Access Dashboard |
| 4 | Upload an invoice image/PDF | Status changes from **Processing** → **Draft** |
| 5 | View invoice details | Key fields (Tax ID, Date, Amount) are filled correctly |
| 6 | Check RiskLevel | Risk warning badge appears (if applicable) |

---

## Step-by-Step Verification

### 1. Frontend Access

- Open the Amplify app URL in a browser.
- The login form should appear. No console errors.

### 2. Register & Login

- Click **Register**, fill in your email and password.
- Check your email for the OTP/verification code.
- Complete registration and log in.

### 3. Invoice Upload

- From the Dashboard, click **Upload Invoice**.
- Select a sample invoice PDF or image.
- The invoice should appear in the list with status **Processing**.
- After ~30–90 seconds, status should change to **Draft** with extracted data pre-filled.

### 4. Invoice Details

- Click on the invoice to open the detail view.
- Verify that the following fields are populated:
  - Tax ID (Mã số thuế)
  - Invoice date
  - Total amount
  - Seller/Buyer names

### 5. Merge Invoice

- From the `Draft` invoice, click **Merge / Confirm**.
- Verify the invoice status changes to `Confirmed` or `Merged`.

---

## Backend Health Check

You can also verify the backend directly via CloudFront:

```bash
curl https://<CLOUDFRONT_DOMAIN>/api/health
# Expected: {"status":"Healthy"}
```

And the OCR internal health check (via ECS Exec or test from Backend):

```bash
curl http://<ALB_OCR_DNS>/api/v1/health
# Expected: {"status":"ok"}
```

---

## Troubleshooting Common Issues

| Issue | Likely Cause | Solution |
|---|---|---|
| Invoice stuck in `Processing` | OCR ECS tasks not running | Check ECS service → Tasks; check CloudWatch logs |
| 502 Bad Gateway from CloudFront | Backend EB environment unhealthy | Check EB environment health page |
| Login fails | Cognito configuration mismatch | Verify `COGNITO_CLIENT_ID` and `COGNITO_CLIENT_SECRET` in SSM |
| Invoice data empty after OCR | Model path issue or missing env vars | Check `/ecs/smartinvoice-ocr-task` logs in CloudWatch |
