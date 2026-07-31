---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---


# [AWS COMPUTE BLOG] MODERNIZING LAMBDA + S3 ARCHITECTURE WITH AMAZON S3 FILES – WHAT I LEARNED FROM EXPLORING AN ALTERNATIVE SOLUTION

Hello everyone,

When working with AWS, combining AWS Lambda and Amazon S3 is an extremely familiar architectural pattern. Normally, when processing files (such as image resizing, reading CSV/Parquet files, or creating temporary storage for AI Agents), my classic workflow looks like this:

Download file from S3 to `/tmp` -> Process file -> Upload result back to S3 -> Delete temporary file in `/tmp`.

Initially, I thought this was the standard and best way. However, after reading a recent article on the AWS Compute Blog about **Amazon S3 Files**, I realized that writing code to manage downloads/uploads, monitoring `/tmp` storage limits, and cleaning up temporary files are unnecessary tasks.

---

### What is the `/tmp` Directory?

The `/tmp` directory (Ephemeral Storage) is a temporary disk area provided by AWS for each Lambda execution environment. This temporary area has limited capacity, exists only short-term, and is automatically wiped when the Lambda instance terminates.

AWS now allows Lambda to mount S3 Buckets directly as local disk drives using the **Amazon S3 Files** feature.

---

### System Architecture & Workflow

![Amazon S3 Files Architecture](/blog_3_architect.jpg)
*Figure 1: Architectural diagram of Lambda integrating with Amazon S3 Files via VPC Endpoint*

As shown in the architecture diagram above, the processing flow consists of 4 main steps:

1. **Event / Trigger:** The Client sends a request to trigger the AWS Lambda function.
2. **Direct Read/Write:** Instead of downloading files via AWS SDK, AWS Lambda performs direct local file I/O operations through the **S3 VPC Endpoint** mounted inside the VPC.
3. **Auto Sync:** Data written to the local mount path is automatically synchronized with the **Amazon S3 Bucket Storage** by the underlying file system.
4. **Read Final Files:** Users or external services can read the processed final files directly from the Amazon S3 Bucket.

---

### Key Features & Benefits:

* **Eliminate `/tmp` Storage Limits:** Process large files easily without worrying about temporary storage disk overflow.
* **Cleaner Source Code:** Reduces dozens of complex lines of code down to native file I/O operations (e.g., `open()`, `read()`, `write()`).
* **No S3 API Call Overhead:** Eliminates explicit `GET` and `PUT` object API calls, reducing overall costs and network connection issues during transfers.

---

### How AWS Combines VPC, S3 Files, and Lambda:

To implement this architecture, AWS connects these services via private networking mechanisms:

1. **S3 File System & VPC:** Create an S3 File System for the Bucket, then create Mount Targets and Access Points inside Amazon VPC.
2. **AWS Lambda in VPC:** Place the Lambda function inside the VPC and configure it to attach the File System with a local Mount Path (e.g., `/mnt/images`).
3. **IAM Permissions:** Grant `s3files:ClientMount` and `s3files:ClientWrite` permissions to the Lambda IAM Role.
4. **Performance Optimization:** For large file processing, allocate at least 512 MB RAM to Lambda to enable Direct Reads from S3.

---

### Cost & Developer Experience Evaluation:

* **Simplified Developer Experience:** From my perspective, developers can focus entirely on core business logic (resizing images, converting data, writing reports). Data synchronization, state management, and file integrity are handled automatically by the underlying file system.
* **Architectural Trade-offs:** Utilizing S3 Files requires running Lambda inside a VPC. Additionally, for workflows requiring specific S3 API features like Presigned URLs, S3 Select, or Multipart Uploads, the traditional SDK/API approach remains necessary.

---

### Conclusion:

Amazon S3 Files is not just a new feature, but a significant step forward in simplifying Serverless architectures on AWS. If your project runs large data ETL pipelines or Multi-agent AI systems on Lambda, this solution is well worth considering to clean up your codebase and reduce error-handling logic.

Thank you everyone for taking the time to read my post!

---

### Official AWS Blog Link:

👉 [Modernizing Lambda + S3 workloads with Amazon S3 Files](https://aws.amazon.com/blogs/compute/modernizing-lambda-s3-workloads-with-amazon-s3-files/)

---

### Article Image:

![Blog 3 Final](/blog_3_final.jpg)
