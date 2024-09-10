# Aws-Daily-Mini-Projects
Welcome to my AWS daily mini-projects repository! This collection represents my journey of learning and mastering AWS through hands-on experience. Each day, I explore a new AWS service or feature by building small, practical projects that solve real-world problems.
The repository is structured with a separate folder for each day, containing:

- Code: Scripts, configuration files (e.g., Terraform, CloudFormation), or Python/Node.js code.<br/>
- Project Documentation: Each project includes a detailed README file, outlining the goal, AWS services used, step-by-step implementation, and key takeaways.<br/>
- Screenshots/Diagrams (where applicable): Visuals to help illustrate the infrastructure or key results of the project.<br/>

The goal of these mini-projects is to deepen my understanding of AWS services, from S3 and EC2 to Lambda, IAM, and beyond. I also aim to build a solid foundation in infrastructure as code (IaC), automation, and cloud security. By documenting the challenges and lessons learned, this repository serves as a knowledge base for anyone starting with AWS or looking for practical examples of cloud solutions.


# How IAM Enables Secure Access Management: A Practical Example
AWS Identity and Access Management (IAM) is a powerful service that helps organizations securely control access to their AWS resources. By creating users, groups, and policies, IAM ensures that only authorized people can perform specific actions on designated resources. This is especially important in complex cloud environments where different teams need different levels of access. Let's see how IAM can be used in a real-life example with Tech Solutions Inc. The company needs to manage access for three teams: Development, QA, and Operations, each with different needs.

# Step-by-Step Guidance for Implementing IAM at Tech Solutions Inc.

Setting up AWS Identity and Access Management (IAM) can seem complicated, but breaking it down into simple steps makes it easier. Here is a straightforward guide for Tech Solutions Inc. to set up IAM for their Development, QA, and Operations teams.

**Step 1: Access the IAM Dashboard**
* Sign in to AWS Management Console:

* Go to the AWS Management Console and log in with your AWS account credentials.
* Navigate to IAM:

* In the console, find the "Security, Identity, & Compliance" section.

* Click on "IAM" or use the search bar to locate the IAM service.

**Step 2: Create IAM Users**
**Go to the Users Section:**

* 1. In the IAM dashboard, click on "Users" in the sidebar.
* 1. Add Users:

* 1. Click on "Add user."

* 1. Enter the usernames for each team member:

* 1. Development Team:

* 1. alice.smith

* 1. bob.johnson

* 1. QA Team:

* 1. carol.white

* 1. dave.brown

* 1. Operations Team:

* 1. [eve.green](http://eve.green/)

* 1. frank.lee

* 1. Select Access Types:

* 1. For each user, select both "Programmatic access" and "AWS Management Console access."
* 1. Set Permissions:

* 1. Choose to attach existing policies directly or create custom policies later.
* 1. Review and Create:

* 1. Review the user details and click "Create user."


Step 3: Create IAM Groups
Go to the Groups Section:

In the IAM dashboard, click on "Groups."
Create New Groups:

Click on "Create New Group."

Enter the group names and attach appropriate policies:

Developers Group:

Users: alice.smith, bob.johnson

Policies: Attach AmazonEC2FullAccess and AmazonS3FullAccess.

QA Group:

Users: carol.white, dave.brown

Policies: Attach AmazonS3ReadOnlyAccess and AmazonEC2ReadOnlyAccess.

Operations Group:

Users: [eve.green](http://eve.green/), frank.lee

Policies: Attach CloudWatchFullAccess and IAMFullAccess.

Review and Create Groups:

Review the group details and click "Create group."



Step 4: Create Custom Policies (if needed)
Go to the Policies Section:

Click on "Policies" in the IAM dashboard.
Create Policy:

Click on "Create Policy."

Choose the "JSON" tab to define a custom policy. For example, to allow write access to a specific S3 bucket, use the following policy:


Copy

Copy
        json{
          "Version": "2012-10-17",
          "Statement": [
            {
              "Effect": "Allow",
              "Action": [
                "s3:PutObject",
                "s3:DeleteObject"
              ],
              "Resource": [
                "arn:aws:s3:::my-development-bucket/*"
              ]
            }
          ]
        }
Review and Create Policy:

Name the policy (e.g., CustomS3WriteAccess) and click "Create policy."



Step 5: Assign IAM Users to Groups
Go to the Users Section:

Click on "Users" in the IAM dashboard.
Select Users:

For each user, select them and navigate to the "Groups" tab.
Add Users to Groups:

Click "Add user to groups."

Assign users to their respective groups:

alice.smith and bob.johnson to Developers

carol.white and dave.brown to QA

[eve.green](http://eve.green/) and frank.lee to Operations

Click "Add to groups."



Step 6: Test User Access
Log in as Each User:

Each user should log in using their credentials.
Perform Access Tests:

alice.smith: Attempt to launch an EC2 instance and upload a file to S3.

carol.white: Try listing objects in S3 and describing EC2 instances.

[eve.green](http://eve.green/): Verify access to CloudWatch logs and IAM policies.

Address Access Issues:

If any user encounters access issues, revisit the policies and adjust them as necessary.
Step 7: Enable Multi-Factor Authentication (MFA)
Go to the Users Section:

Click on "Users" in the IAM dashboard.
Select a User:

Choose a user (e.g., alice.smith) and go to the "Security credentials" tab.
Manage MFA Device:

Click on "Manage MFA Device."

Choose "Virtual MFA device" and follow the setup instructions:

Use an authenticator app (like Google Authenticator) to scan the QR code.

Enter the verification codes from the MFA device.

Verify and Save:

Confirm the MFA setup and save the settings.
Step 8: Cross-Check the Project
Verify User Creation:

Ensure all users (alice.smith, bob.johnson, carol.white, dave.brown, [eve.green](http://eve.green/), and frank.lee) are created with the correct access types.
Verify Group Creation:

Confirm that the Developers, QA, and Operations groups exist and have the correct policies attached.
Verify Policy Attachment:

Check that custom policies are attached to the appropriate groups and that users inherit these policies.
Test Access:

Verify that each user has the correct level of access to resources according to their group's permissions.
Verify MFA Setup:

Ensure that MFA is enabled for users as required and that they can successfully log in using MFA.
In conclusion, AWS Identity and Access Management (IAM) is an essential tool for any organization leveraging AWS services. It provides a comprehensive framework for managing user access and permissions, ensuring that only authorized individuals can interact with specific resources. By implementing IAM, organizations can enhance their security posture, maintain compliance, and streamline user management. The practical example of Tech Solutions Inc. demonstrates how IAM can be effectively used to manage access for different teams, ensuring that each team has the appropriate level of access to perform their tasks efficiently. With features like users, groups, roles, and policies, IAM offers the flexibility and control needed to build a secure and efficient cloud infrastructure.
