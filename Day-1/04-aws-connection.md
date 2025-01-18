# Setup Terraform for AWS

To configure AWS credentials and set up Terraform to work with AWS, you'll need to follow these steps:

1. **Install AWS CLI (Command Line Interface)**:

Make sure you have the AWS CLI installed on your machine. You can download and install it from the [AWS CLI download page](https://aws.amazon.com/cli/).

Installing AWS CLI Using snap (easy process)
Install snap
If you don't already have snap installed, you can install it by using the instructions Canonical Snapcraft provides. Run snap version to see if your version of Linux already includes snap.

Install Snapcraft on your platform. For information on installing Snapcraft, see Installing the daemon in the Snap documentation.

Restart your system so that your PATH variables are updated correctly. If you are having installation issues, follow steps in Fix common issues in the Snap documentation.

To verify that snap is installed correctly, run the following command.


$ snap version
Install and update the AWS CLI version 1 using snap
Run the following snap install command for the AWS CLI version 1.


$ snap install aws-cli --channel=v1/stable --classic
Depending on your permissions, you may need to add sudo to your command.


$ sudo snap install aws-cli --channel=v1/stable --classic
Verify that the AWS CLI installed correctly.


$ aws --version
aws-cli/1.35.20 Python/3.11.6 Linux/5.10.205-195.807.amzn2.x86_64 botocore/1.18.6
If you get an error, see Troubleshooting errors for the AWS CLI.

Uninstall the AWS CLI using snap
If you installed the AWS CLI version 1 using snap, you must also uninstall using snap.


$ snap remove aws-cli
You might need to restart your command prompt window or your computer to remove all files.

(Optional) Remove the shared AWS SDK and AWS CLI settings information in the .aws folder.

2. **Create an AWS IAM User**:

To interact with AWS programmatically, you should create an IAM (Identity and Access Management) user with appropriate permissions. Here's how to create one:

a. Log in to the AWS Management Console with an account that has administrative privileges.

b. Navigate to the IAM service.

c. Click on "Users" in the left navigation pane and then click "Add user."

- Choose a username, select "Programmatic access" as the access type, and click "Next: Permissions."

- Attach policies to this user based on your requirements. At a minimum, you should attach the "AmazonEC2FullAccess" policy for basic EC2 operations. If you need access to other AWS services, attach the relevant policies accordingly.

- Review the user's configuration and create the user. Be sure to save the Access Key ID and Secret Access Key that are displayed after user creation; you'll need these for Terraform.

3. **Configure AWS CLI Credentials**:

Use the AWS CLI to configure your credentials. Open a terminal and run:

```
aws configure
```

It will prompt you to enter your AWS Access Key ID, Secret Access Key, default region, and default output format. Enter the credentials you obtained in the previous step.
