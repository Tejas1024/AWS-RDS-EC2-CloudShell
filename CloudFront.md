# CloudFront.md

# 🌐 AWS CloudFront – Complete Beginner Guide

## What is CloudFront?

AWS CloudFront is a Content Delivery Network (CDN) service by AWS.
It accelerates the delivery of your website content (HTML, CSS, JS, images, videos) to users worldwide by caching data at **edge locations** (Points of Presence, or POPs) geographically closer to the end users.
**Result:** Websites and apps load faster for everyone, everywhere.

---

## ⚡ Why Use CloudFront?

- **Low Latency:** Faster content loading—data comes from nearest edge.
- **Reduced Origin Load:** Fewer requests to your main/origin server, as assets are cached.
- **Cost Savings:** Less data transfer from your origin reduces AWS costs.
- **Security:** Supports HTTPS, DDoS protection, integrates with AWS Shield and WAF (Web Application Firewall).

---

## 📦 Prerequisite

- You need an **S3 bucket** with **Static Website Hosting** enabled and your website files (index.html, etc.) uploaded.

---

## 🛠️ Steps to Create a CloudFront Distribution

**1. Prepare S3 Website**
   - Have a static website running with S3 static hosting enabled.

**2. Search CloudFront in AWS Console**
   - Go to AWS Console
   - Search: "CloudFront"

**3. Create Distribution**
   - Click **Create Distribution**
   - Origin Domain: Select your S3 bucket (hosted static site)
   - Origin Type: Amazon S3
   - Ensure static website hosting is enabled on the bucket (check S3 > Properties > Static Website Hosting)
   - Click Next

**4. Configure Web Application Firewall (WAF)**
   - For testing/Basics: Set WAF to **Disable**

**5. Review & Create**
   - Review all options
   - Click **Create Distribution**
   - Wait a few minutes for global deployment

**6. Set Default Root Object**
   - After creation, go to your distribution → General tab
   - Set **Default Root Object** as `index.html`
   - Save changes

**7. Access via CloudFront URL**
   - When status = Enabled, copy CloudFront domain name (e.g., d123abcde.cloudfront.net)
   - Paste in browser to load your site via global CDN—loading will be faster than direct S3!

---

## 🧠 Summary Table

| Concept       | Description                                            |
|---------------|--------------------------------------------------------|
| Service       | AWS CloudFront                                         |
| Type          | CDN (Content Delivery Network)                         |
| Purpose       | Fast delivery of content via edge caching              |
| Prerequisite  | Static website in S3 with static website hosting       |
| Main Benefits | Speed, reduced load, cost savings, enhanced security   |
| Output        | Global CloudFront distribution URL                     |

---

## ✅ Example Flow

S3 Bucket (Static Website) → CloudFront (CDN) → Edge Locations → Global Users