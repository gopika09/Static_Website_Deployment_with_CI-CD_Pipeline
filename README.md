# Static_Website_Deployment_with_CI_CD_Pipeline

## **Introduction**

This project demonstrates how to host a static website and integrate it with a Continuous Integration/Continuous Deployment (CI/CD) pipeline. The process involves using **GitHub**, **Amazon S3**, **AWS CodePipeline**, and **Amazon CloudFront**. The pipeline automatically deploys updates from the GitHub repository to an S3 bucket, enabling seamless updates to the website.

---

## **Features**

- **Automated Deployment:** Updates to the GitHub repository are automatically pushed to the live website.
- **Version Control:** GitHub is used for version control, ensuring easy rollback and collaboration.
- **Secure Hosting:** Hosted using Amazon S3 with CloudFront providing content delivery.
- **Scalable Infrastructure:** Amazon S3 and CloudFront enable scalability for high traffic.
- **Optimized Delivery:** CloudFront ensures low latency by caching content across edge locations.

---

## **Tools and Technologies**

- **GitHub:** Version control system for managing code and hosting the static website.
- **Amazon S3:** Storage service for hosting static files.
- **AWS CodePipeline:** CI/CD service for automated deployment.
- **Amazon CloudFront:** Content Delivery Network (CDN) for fast and secure delivery of website content.
- **HTML:** Used to create the static webpage (`index.html`).

---

## **Steps to Deploy**  

### **Step 1: Set Up GitHub Repository**  

1. Create a new repository on GitHub named `Static_website_for_CICD_pipeline`.  
2. Push your local file (`index.html`) to the GitHub repository:  
   ```bash
   # Navigate to your project directory
   git clone https://github.com/gopika09/Static_website_for_CICD_pipeline.git
   cd Static_website_for_CICD_pipeline

   # Add and commit the file
   git add index.html
   git commit -m "added a file"

   # Push changes to the main branch
   git push origin main

## Step 2: Create an S3 Bucket

1. Navigate to the **S3 Console** on AWS and create a new bucket:
    - **Bucket Name**: `cicdwebsite`
    - **ACL**: Disabled
    - **Block Public Access**: Off
2. Click **Create Bucket**.

---

## Step 3: Configure AWS CodePipeline

1. Open the **CodePipeline Console** and create a new pipeline:
    - **Pipeline Name**: Choose an appropriate name.
    - **Execution Mode**: Supersede.
    - **Service Role**: Create a new role.
2. Configure the **Source Stage**:
    - **Source Provider**: GitHub.
    - **Connection**: Connect to your GitHub account and select the repository (`Static_website_for_CICD_pipeline`).
3. Skip the **Build Stage**.
4. Configure the **Deploy Stage**:
    - **Deploy Provider**: S3.
    - **Bucket Name**: Select `cicdwebsite`.
    - Enable the **Extract file before deploy** option.
5. Click **Create Pipeline**.

---

## Step 4: Set Up Amazon CloudFront

1. Open the **CloudFront Console** and create a new distribution:
    - **Origin Domain Name**: Select the S3 bucket (`cicdwebsite`).
    - **Origin Access**: Use legacy access identities.
    - Update the **Bucket Policy** to allow CloudFront access.
2. **Viewer Settings**:
    - **Viewer Protocol Policy**: HTTP and HTTPS.
    - **Allowed HTTP Methods**: GET, HEAD.
    - **WAF**: Disabled.
    - **Supported HTTP Versions**: HTTP/2, HTTP/3.
3. Complete the setup and note the distribution domain name (e.g., `https://d1nipgr1fpacfq.cloudfront.net/index.html`).

---

## Conclusion

This setup enables automated and efficient deployment of a static website using AWS services. By integrating GitHub with AWS CodePipeline, updates are automatically pushed to the live environment. **CloudFront** ensures fast and secure delivery of the content, providing a scalable and optimized hosting solution.

### Access Your Deployed Website

You can now access your deployed website at the following URL:  
[https://d1nipgr1fpacfq.cloudfront.net/index.html](https://d1nipgr1fpacfq.cloudfront.net/index.html)
