# infotrixs
WordPress site over AWS using RDS


# WordPress on AWS

This project shows how to deploy a WordPress site on AWS using EC2, RDS, and Apache.
Sure, I'll add instructions for launching a t2.micro instance in your GitHub report. Here's the updated section:

## Prerequisites

Before you begin, ensure you have met the following requirements:

- An AWS account with appropriate permissions.
- A security group for EC2 with SSH (port 22) and HTTP (port 80) access from anywhere.
- A security group for RDS with MySQL/Aurora (port 3306) access from the EC2 security group.
- An RDS instance running MySQL or Aurora.
- An EC2 instance running Ubuntu 20.04 or a t2.micro instance running Amazon Linux.

## Launching a t2.micro Instance (Amazon Linux)

1. Log in to your AWS Management Console.

2. Navigate to the EC2 dashboard.

3. Click on the "Launch Instance" button.

4. In the "Choose an Amazon Machine Image (AMI)" step, select "Amazon Linux 2 AMI (HVM), SSD Volume Type."

5. In the "Choose an Instance Type" step, select "t2.micro" (or another instance type if you prefer).

6. Follow the rest of the instance creation wizard, configuring instance details, adding storage, configuring security groups (remember to allow SSH and HTTP), and launching the instance.

7. Once the instance is launched, note its public IP address or DNS name.

8. SSH into the t2.micro instance using your key pair and the public IP address.
   ```bash
   ssh -i your-key.pem ec2-user@your-ec2-ip
   ```

Now, you can proceed with the installation steps for Apache, PHP, and WordPress on your t2.micro instance as mentioned in the previous README.

Please replace "your-key.pem" and "your-ec2-ip" with your actual key pair and EC2 instance information.

This addition provides guidance for launching a t2.micro instance with Amazon Linux, which is a cost-effective option for running your WordPress site on AWS.




