Creating and Working with an EC2 Instance

# Introduction

Elastic Compute Cloud (EC2) is AWS's Infrastructure as a Service product. It provides a huge range of virtual machines suitable for general purpose and specialized on-demand compute tasks. In this hands-on lab, you will gain experience creating and interacting with an EC2 instance. The lab covers EC2 requirements, the choices available with creating EC2 instances, and the provisioning process itself. By the end of the lab, you will have gained the experience needed to be confident using EC2 in smaller deployments, such as blogs or lower-volume websites. Solution

Log in to the live AWS environment using the credentials provided. Make sure you're in the N. Virginia (us-east-1) region throughout the lab.

Here are the instructions on how to connect to EC2 using PuTTY on Windows.

Windows users can also use WSL2 on how to connect to EC2 using WSL2 on Windows (Recommended)

## Create a Default VPC

```
1\. Navigate to VPC > Your VPCs.
2\. Select Actions > Create default VPC.
3\. Click Create default VPC.
```

## Create an EC2 Instance

```
1\. Navigate to EC2 > Instances.
2\. Click Launch instance.
3\. On the AMI page, select the Amazon Linux 2 AMI.
4\. Leave t2.micro selected, and click Next: Configure Instance Details.
5\. On the Configure Instance Details page:
    5.1 Network: default
    5.2 Subnet: No preference
    5.3 Auto-assign Public IP: Enable

6\. Expand Advanced details, and paste the following into the user data box:

        #!/bin/bash
        yum update -y
        yum install -y httpd
        yum install -y wget
        chkconfig httpd on
        cd /var/www/html
        service httpd start
7\. Click Next: Add Storage, and then click Next: Add Tags.
8\. On the Add Tags page, select Add Tag then add the following:
        Key: Name
        Value: Webserver
9\. Click Next: Configure Security Group.
10\. On the Configure Security Group page, click Create a new security group, and set the following values:
        Security group name: LabSG
        Description: LabSG
11\. Click Add Rule, and set the following values (leave the default SSH rule):
        Type: HTTP
        Source: My IP
12\. Click Review and Launch, and then Launch.
13\. In the key pair dialog, select Create a new key pair.
14\. Give it a Key pair name of "Lab".
15\. Click Download Key Pair, and then Launch Instances.
16\. Click View Instances.
```

## Manage the EC2 Instance

```
1\. Wait for the instance to enter a running state and show 2/2 status checks complete.
2\. Ensure the instance is selected.
3\. In the Description section, copy its public DNS (IPv4).
4\. Paste it into a new browser tab to preview it, which should result in the Apache test page.
```

## Connect to the EC2 Instance

```
1\. Open a terminal session and change to your downloads directory where the key pair file should be saved (e.g., cd Downloads).

2\. In the terminal, change the permissions on the key pair:

chmod 400 Lab.pem

3\. On the EC2 instances page, with the EC2 instance still selected, click Connect.
4\. Copy the ssh connection string, listed under Example, and paste it into the terminal window to connect to the instance.
5\. Enter yes at the prompt.
6\. In the AWS console, note the IPv4 public IP of the instance.
7\. Click Actions > Instance State > Reboot.
8\. In the dialog, click Yes, Reboot.
9\. Note if the IPv4 public IP changes.
    (It should stay the same.)
10\. Click Actions > Instance State > Stop.
11\. In the dialog, click Yes, Stop. Give it a minute to fully stop.
12\. Note the IP.
    (Once it's fully stopped, the IP will disappear.)
13\. Click Actions > Instance State > Start.
14\. In the dialog, click Yes, Start. Give it a minute to enter a running status.
15\. Note the IP.
    (A new IP should appear.)
16\. Click Actions > Instance State > Stop.
17\. In the dialog, click Yes, Stop. Give it a minute to fully stop.
18\. Click Actions > Instance Settings > Change Instance Type.
19\. Change the instance type to t3.small, and click Apply.
```

Conclusion
