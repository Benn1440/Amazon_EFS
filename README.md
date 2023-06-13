# Amazon Elastic File System

In this project, three web servers were created and distributed across separate availability zones. The web servers need to share the same unstructured data.

The data can consists of PHP files, config files, plugins, and images etc.

EFS Is used as a shared file system, with EFS you can share file data without provisioning or managing servers.

Amazon EFS automatically grows and shrinks as you add or remove files. This removes the need for capacity management

After creating the EFS file system, you can create mount tragets on each subnet.The mount target enables communication from Amazon EC2 instances on the subnet.
It uses the Network File system (NFSV4) protocol

![Create different subnets within EFS to allow connection with EC2](https://github.com/Benn1440/Amazon_EFS/assets/67696393/191407cd-8c88-46f1-af2d-7fd864ec0ed6)

Amazon EFS security Group once created, you can prepare to create the file system

![NFS](https://github.com/Benn1440/Amazon_EFS/assets/67696393/b9d5fc24-8406-4e7d-b918-2e89887e06ed)

In general, Create the EC2 instance then the EFS, and within the network session of the EFS you create security group for each EC2 instance, 

![EFS](https://github.com/Benn1440/Amazon_EFS/assets/67696393/22799df4-6d93-42e0-bdc5-1aed5dcf725b)

Then click attach to attach the EFS and EC2 instance copy out the EFS mount helper provided code 
# sudo mount -t efs -o tls fs-08ed9db97402b6ab1:/ efs

![EFS Attach](https://github.com/Benn1440/Amazon_EFS/assets/67696393/18411b60-2a68-4222-938c-ade663e6e3c3)

Connect to the instance 

Login as root user: sudo -i
Install the amazon EFS Util tool

sudo yum install -y amazon-efs-utils 

![EFS Util tool](https://github.com/Benn1440/Amazon_EFS/assets/67696393/953f6f09-ae18-4e5f-a78c-fa89e5786210)

Amazon EFS client Is available in the Amazon Linux package repositories, to build install and package on linux repositories

1. In the terminal, run:

sudo -i

2. In the terminal, run:

sudo yum install -y amazon-efs-utils

3. Go to the next step.
1. In the terminal, run: 

mkdir data

- If you receive a Permission Denied message, run:

cd ~/

2. In the terminal, run:

ls

3. In the terminal, paste the sudo mount command that you copied from the Amazon EFS console in an earlier step. At the end of the command, replace the "efs" folder name with "data" (without quotes) and press Enter.
sudo mount -t efs -o tls fs-08ed9db97402b6ab1:/ efs
- The command should look similar to what is displayed in the screenshot example.

4. In the terminal, run:

cd data

5. To create a log file, run:

sudo bash -c "cat >> efs-1-setup.log"

- No output will appear. Instead, the cursor will move to a new line and wait for your next input.

6. In the terminal, run: 

efs-1 mounted in site A

7. To end the cat session, on your keyboard, press Ctrl+C.
8. To view the log file contents, run:

cat efs-1-setup.log

You should see all the File system mounted to the different instances.

![Files Monted in three EFS](https://github.com/Benn1440/Amazon_EFS/assets/67696393/f84a0d3c-a288-487e-b90a-b2163a7457b2)

# Reference Use Amazon EFS with Amazon EC2: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEFS.html

