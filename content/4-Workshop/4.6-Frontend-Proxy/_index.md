---
title: "Frontend, Proxy & Route 53"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

This section covers Steps 16–18: configuring CloudFront as an HTTPS proxy for the Backend API, deploying the React frontend on AWS Amplify, and mapping a custom domain with Route 53.

---

## Step 16: Configure HTTPS with CloudFront (Backend Proxy)

CloudFront acts as the public HTTPS gateway for the Backend API.

### 16.1 Get Started

**Console**: CloudFront → **Create distribution**

| Field             | Value                        |
| ----------------- | ---------------------------- |
| Distribution name | `smartinvoice-backend-proxy` |
| Distribution type | **Single website or app**    |

### 16.2 Specify Origin

| Field         | Value                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------- |
| Origin type   | **Elastic Load Balancer**                                                                    |
| Origin domain | DNS Name of the **EB ALB** (e.g. `awseb-e-m-AWSEBLoa-xxxx.ap-southeast-1.elb.amazonaws.com`) |
| Protocol      | **HTTP only**, HTTP Port: `80`                                                               |

![alt text](image-3.png)

### 16.3 Default Cache Behavior

| Field                   | Value                                            |
| ----------------------- | ------------------------------------------------ |
| Viewer protocol policy  | **Redirect HTTP to HTTPS**                       |
| Allowed HTTP methods    | **GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE** |
| Cache policy            | `CachingDisabled`                                |
| Origin request policy   | `AllViewerExceptHostHeader`                      |
| Response headers policy | `CORS-With-Preflight`                            |

![alt text](image.png)

### 16.4 Security & Review

- **Rate limiting**: ✅ Enable (Recommended — protects against API spam)

→ Click **Create distribution** and wait ~5 minutes for deployment.

→ Note down the **CloudFront domain** (e.g. `https://d3xxxx.cloudfront.net`) — you will use this as the API URL for the frontend.

---

## Step 17: Deploy Frontend on Amplify

### 17.1 Connect Branch

1. **Console**: AWS Amplify → **All apps** → **New app** → **Host web app**.
2. Connect GitHub Repository `tuankiet18-dev/SMARTINVOICE-SHIELD`, select branch `main`.

![alt text](image-5.png)

### 17.2 Build Settings (amplify.yml)

Amplify auto-detects Vite. Verify under App settings → Build settings:

![alt text](image-8.png)

### 17.3 Environment Variables

**Console**: App settings → **Environment variables** → Add:

| Key            | Value                                                                     |
| -------------- | ------------------------------------------------------------------------- |
| `VITE_API_URL` | CloudFront domain from Step 16 (e.g. `https://d3xxxx.cloudfront.net/api`) |

![alt text](image-9.png)

→ After deployment, copy the **Amplify URL** and update SSM parameter `ALLOWED_ORIGINS`.

---

## Step 18: Configure Custom Domain (Route 53)

After deploying the frontend on Amplify, you can optionally map a custom domain.

1. **Console**: Route 53 → **Hosted zones**
2. Ensure you have a registered domain or create a new Hosted Zone.
3. **Console**: AWS Amplify → App settings → **Domain management** → **Add domain**
4. Enter your custom domain and click **Configure domain**.
5. Amplify will automatically generate SSL certificates and propose CNAME validation records.
6. Copy these CNAME records to your Route 53 Hosted Zone.
7. Wait for DNS propagation and SSL verification (can take up to a few hours, usually ~15 mins).
8. Once verified, your web interface will be accessible securely at your custom domain.
