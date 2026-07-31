---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# [AWS AMPLIFY] LIGHTWEIGHT CHOICE TO HOST WEBSITES FOR DEMOS AND WORKSHOP PRESENTATIONS

Hello everyone,

When preparing for a report or a demo, my requirement is usually to host a website as quickly as possible with simple operations, avoiding time-consuming and complex infrastructure configurations.

Normally, setting up a website using traditional methods on AWS takes a lot of time:

Creating an S3 Bucket -> Configuring Static Website Hosting -> Creating a CloudFront Distribution -> Setting up Route 53 / SSL Certificates.

However, after exploring and testing it out, I realized that **AWS Amplify Hosting** is the ideal solution to deliver clean, lightweight, and professional workshop presentations.

---

### Key Features & Benefits:

* **Deploy in Minutes:** Simply connect to a code repository (GitHub/GitLab/Bitbucket) or drag & drop the build folder directly (HTML/JS/React/Vue/Next.js) onto the console.
* **Automated CI/CD:** Every time the team pushes new code for the workshop, Amplify automatically builds and redeploys the website immediately.
* **Built-in SSL / Default Domain:** Immediately after deployment, the team receives an HTTPS link in the format `https://main.xxx.amplifyapp.com` to share with everyone for testing.

---

### New Feature: Integrated AWS WAF Protection

Previously, demo and workshop projects often avoided security setups due to tedious configuration. However, AWS Amplify now directly integrates **AWS WAF (Web Application Firewall)** right on the Amplify Console.

With just a few simple clicks, I can equip our demo with enterprise-grade protection features:

* **IP Blocking:** Allow or block specific IP ranges during testing.
* **Geographic Rate-Limiting:** Restrict access based on country/location.
* **Automated Security:** Automatically block common web vulnerabilities and malicious IPs using Amazon threat intelligence.

---

### Cost & Experience Evaluation:

* **Simplified Infrastructure:** Using Amplify helps eliminate complex networking and infrastructure configuration steps, bringing the workflow down to: **Code -> Push -> Live Demo**.
* **Cost Efficiency:** While Amplify is cost-effective and fits within the AWS Free Tier for basic usage, keep in mind that custom domain management, high bandwidth, or enabling AWS WAF rules will incur small additional charges based on usage.

---

### Conclusion:

If you are preparing for a Workshop report, presenting a course project, or building an MVP demo for clients, AWS Amplify Hosting is undoubtedly a top-tier choice to save time and effort.

Thank you for reading the post!

---

### Official AWS Blog Links:

* [Firewall Support for AWS Amplify Hosted Sites](https://aws.amazon.com/blogs/aws/firewall-support-for-aws-amplify-hosted-sites/?fbclid=IwY2xjawTPp1BleHRuA2FlbQIxMABicmlkETFNYnpiUTR6MFlXVzU0VUlwc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHo0lvAi7DyFK9RJz0yuaw3CPM4QNkT9NrC-0qEVszM-385ZdVzScGEZmy_8q_aem_MUI1FfeLVhGideiv_cVscw)  
* [AWS Amplify Hosting Adds Web Application Firewall Protection](https://aws.amazon.com/blogs/mobile/aws-amplify-hosting-adds-web-application-firewall-protection-public-preview/?fbclid=IwY2xjawTPp2ZleHRuA2FlbQIxMABicmlkETFNYnpiUTR6MFlXVzU0VUlwc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHqXhzynO67qDjqNn3iCMDAfwPy9WEXcts29g6twMNkRuNRLowpWiyHPrmMr5_aem_0IyIORQVVOYTLh5ZvFYKfw)

---

### Article Image:

![AWS Amplify Blog Post](/blog_2_final.jpg)
