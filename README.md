# Portfolio Deployment on S3 using GitHub Actions

This guide provides step-by-step instructions to deploy a portfolio website on AWS S3 using GitHub Actions.

🚀 Steps to Deploy

1. Create an S3 Bucket Accessible Publicly

To host your portfolio on S3, follow these steps:

🔹 Set AWS Secrets in GitHub

Create Access Keys in your AWS account.

Go to GitHub Repository Settings:

Navigate to Security → Secrets and Variables.

Go to Actions → New Repository Secret.

Add the following secrets:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

Click Add Secret for each.

2. Update the Bucket Name in the Code

Ensure that your GitHub Actions workflow or deployment script has the correct S3 bucket name.

3. Run the Pipeline

Once the pipeline is executed, it will sync your GitHub repository code to the S3 bucket.

4. Deploy S3 Bucket Code

🌐 Enable Static Website Hosting

Go to S3 Console → Bucket → Properties.

Scroll to Static Website Hosting and enable it.

Set Index Document to index.html.

Click Save.

🔓 Update Bucket Policy for Public Access

Go to S3 Console → Bucket → Permissions → Bucket Policy.

Add the following policy to make all objects publicly accessible:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::<bucket-name>/*"
    }
  ]
}
```
Replace <bucket-name> with your actual S3 bucket name.

🎉 Your Portfolio is Live!

Once configured, your portfolio will be accessible publicly via the S3 static website URL.

💡 Tip: You can find the S3 website endpoint in the Static Website Hosting section of your S3 bucket settings.

