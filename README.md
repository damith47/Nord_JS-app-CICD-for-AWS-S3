**Documentation for AWS S3 Deployment via GitHub Actions**


**1. Create AWS IAM User with S3 Full Access**
   
1.	Sign in to the AWS Management Console and open the IAM console.
2.	In the navigation pane, choose Users and then choose Add user.
3.	Enter the user details:
  o	User name: your-username
  o	Select Programmatic access for Access type.
4.	Permissions:
o	Select Attach existing policies directly.
o	Search for AmazonS3FullAccess and check the box next to it.
5.	Review and create the user. Note down the Access key ID and Secret access key.

   
**2. Create an S3 Bucket and Give Public Access Permission**
   
1.	Open the Amazon S3 console.
2.	Choose Create bucket.
3.	Enter a Bucket name and select a Region.
4.	Uncheck the box for "Block all public access" under "Bucket settings for Block Public Access".
5.	Create the bucket.

   
**3. Edit Bucket Policy**
   
1.	Go to the S3 console and select your bucket.
2.	Choose the Permissions tab.
3.	Scroll down to Bucket policy and click Edit.
4.	Paste the following policy (replace bucket_name with your bucket name)

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowPublicReadAccess",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::bucket_name/*"
        }
    ]
}


**4. Add AWS Credentials to GitHub Secrets**

1.	Go to your GitHub repository.
2.	Navigate to Settings > Secrets and variables > Actions.
3.	Add a new repository secret for the Access key:
  o	Name: AWS_ACCESS_KEY_ID
  o	Value: Your AWS Access key ID


**5.	Add another new repository secret for the Secret key:**
   
  o	Name: AWS_SECRET_ACCESS_KEY
  o	Value: Your AWS Secret access key


**5. Create a New Branch for Staging**
   
1.	Go to your repository in GitHub.
2.	Click on the branch dropdown, type stage and press Enter to create a new branch from the current branch.

   
**6. Set Up GitHub Actions Workflow**
   
1.	Create a folder named .github in your repository.
2.	Inside .github, create another folder named workflows.
3.	Create a file named main.yml inside the workflows folder.

**   
7. Add the Deployment Workflow**
   
Paste the main.yml code into main.yml:

