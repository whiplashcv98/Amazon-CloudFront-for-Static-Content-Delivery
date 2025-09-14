# Amazon-CloudFront-for-Static-Content-Delivery
This project outlines the process of setting up an Amazon CloudFront distribution to securely deliver static website content stored in an S3 bucket. By using CloudFront, we can improve website performance by caching content at AWS Edge Locations and enhance security by restricting direct access to the S3 bucket.

# Project Objective
The main objective is to configure a CloudFront distribution for a static website hosted on S3, ensuring content is delivered with low latency and is not publicly accessible from the source bucket.

# Step 1: Upload Content to S3
Create a new S3 bucket.

Upload your static content (e.g., an image or HTML file) to this bucket.

Note that by default, the content is private and cannot be accessed directly via its S3 URL.

# Step 2: Create a CloudFront Distribution
Navigate to the CloudFront console.

Choose Create Distribution.

For the Origin Domain, select the S3 bucket you created.

Under Origin Access, choose Origin Access Control (OAC) and create a new OAC. This is a more secure method to restrict access.

# Step 3: Configure S3 Bucket Policy
After creating the OAC, a bucket policy will be generated for you. Copy this policy.

Go back to your S3 bucket's Permissions tab.

Edit the Bucket Policy and paste the copied policy.

Save the changes. This policy grants CloudFront permission to access your private S3 content.

# Step 4: Wait for Distribution to Deploy
CloudFront will begin deploying your distribution. The status will change from In Progress to Enabled when it is complete.

A unique domain name will be assigned to your distribution.

# Step 5: Access Content via CloudFront
Copy the CloudFront distribution's domain name.

In a new browser tab, paste the domain name and add the path to your content in the S3 bucket.

The content is now accessible via CloudFront's secure, low-latency URL.

# Key Concepts
Origin Access Control (OAC): This is the modern, recommended way to secure your S3 bucket. It prevents users from bypassing CloudFront and accessing your original content directly.

Edge Locations: CloudFront caches your content in edge locations around the world, so when a user requests content, it is served from the location closest to them.

Public vs. Private Buckets: For security, it is best practice to keep your S3 bucket private and use a service like CloudFront to manage content delivery.
