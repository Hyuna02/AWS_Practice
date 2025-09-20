# AWS Practice Lab: Hosting a Single-Page Application (SPA)

**Static web apps** that require only a single load in a web browser are referred to as **Single-Page Applications (SPAs)**.  
All subsequent actions by the user are handled through HTML, JavaScript, and CSS files that are preloaded in the browser.

---

## In This Practice Lab, I Will:

- ✅ Configure **Amazon S3** to host a single-page application.
- ✅ Locate the **Amazon API Gateway Invoke URL**.
- ✅ Troubleshoot **resource connections** from API Gateway.
- ✅ Troubleshoot an **AWS Lambda** function.

---

## Architecture Overview

![SPA Architecture](https://github.com/Hyuna02/AWS_Practice/blob/main/Single-PageApp.png)

---

## Key Concepts

- **Amazon S3 (Simple Storage Service)**  
  Used to host static assets like HTML, CSS, and JavaScript.

- **Amazon API Gateway**  
  Exposes backend services through a RESTful API.

- **AWS Lambda**  
  Executes backend logic triggered by API Gateway.

- **CORS (Cross-Origin Resource Sharing)**  
  Must be properly configured to allow your frontend to talk to the API.

---

## Checklist

| Task | Status |
|------|--------|
| S3 Bucket configured for static website hosting | ✅ |
| Index.html uploaded and working | ✅ |
| API Gateway created and integrated with Lambda | ✅ |
| CORS headers set in API Gateway responses | ✅ |
| API URL added to frontend JavaScript | ✅ |

---

## 🛠️ Common Troubleshooting

- `500 Internal Server Error`  
  → Check your Lambda logs in **CloudWatch**.

- `Missing Authentication Token`  
  → Confirm the **API Gateway method** and **deployment stage**.

- CORS issues (`blocked by CORS policy`)  
  → Ensure **Access-Control-Allow-Origin** header is present in **API Gateway > Method Response > Headers**.

