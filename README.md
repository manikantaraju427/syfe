#  Run a Production grade Wordpress app on Kubernetes

# Prerequisites

Before diving into the installation, ensure that our environment meets the following prerequisites:

Ensure we have an AWS account.

An Ubuntu 22.04 -Ec2 Instance

Privileged access to the system (root or sudo user).

Active internet connection.

Minimum 2GB RAM or more.

Minimum 2 CPU cores (or 2 vCPUs).

20 GB of free disk space on /var (or more).

# Step 1: Set Up EC2 Instances

Use the AWS Management Console to launch at least EC2 instances with Ubuntu Server 20.04.

![Screenshot (450)](https://github.com/manikantaraju427/syfe/assets/125948783/82f44a52-4661-4203-919a-894327e43097)

Select an instance type (e.g., t2.medium).

![Screenshot (451)](https://github.com/manikantaraju427/syfe/assets/125948783/aa6cbb49-cbb8-4122-930e-24e3b2a059d4)

Configure the instance details, storage, tags, and security group. Ensure the security group allows the required traffic.

![Screenshot (454)](https://github.com/manikantaraju427/syfe/assets/125948783/2276e3a8-adf7-4d29-8044-6e161f5ee2c6)
![Screenshot (452)](https://github.com/manikantaraju427/syfe/assets/125948783/4de8308d-1e02-4329-a311-0f1cee435fb8)

Use SSH to connect to each instance:

ssh -i my-key.pem ubuntu@my-ec2-instance-public-IP

![Screenshot (453)](https://github.com/manikantaraju427/syfe/assets/125948783/2041fd33-a4e8-4f62-b4bf-7c69c47182ab)

# Installing Kubernetes:-

Update the Package Index:

sudo apt update

![Screenshot (455)](https://github.com/manikantaraju427/syfe/assets/125948783/580b6dfc-144f-4bfd-b37b-b104ee7e9308)

Install Docker:

sudo apt install -y docker.io

sudo systemctl enable docker

sudo systemctl start docker

![Screenshot (456)](https://github.com/manikantaraju427/syfe/assets/125948783/7bccb47c-1cb9-44bb-865d-d132cf3f7216)

Check the status of docker with $systemctl status docker

![Screenshot (457)](https://github.com/manikantaraju427/syfe/assets/125948783/1fd56e3d-4d94-4abb-a376-59e9efc9f573)

Kubectl Installation on EC2

Using curl command to download kubectl

curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl

Use the below command to add executable permission for kubectl.

chmod +x ./kubectl

Next move our kubectl into bin directory for access kubectl from anywhere.

sudo mv ./kubectl /usr/local/bin

Check the kubectl client version

kubectl version - short - client

![Screenshot (458)](https://github.com/manikantaraju427/syfe/assets/125948783/397d8107-2c23-44a9-8389-a8425f523e61)

EKSctl Installation on EC2

Using curl command to download eksctl

curl - silent - location"https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

Next move our kubectl into bin directory for access eksctl from anywhere.

sudo mv /tmp/eksctl /usr/local/bin

Check the eksctl version

eksctl version


AWS cli Installation on EC2

First we need to install zip utility for unzip aws cli file.

sudo apt install zip

