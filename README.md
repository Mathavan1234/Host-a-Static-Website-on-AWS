---

# Host a Static Website on AWS

## Project Overview
This project demonstrates hosting a static HTML web application on AWS by utilizing multiple AWS services to create a scalable, reliable, and secure infrastructure. The architecture ensures fault tolerance, high availability, and efficient resource utilization. Below is an overview of the infrastructure and deployment process.

---

## Key Features
1.**Virtual Private Cloud (VPC)**: Configured a VPC with public and private subnets across two Availability Zones for enhanced security and fault tolerance.
2.**Internet Gateway**: Facilitates connectivity between the VPC and the internet.
🚀  **Security Groups**: Acts as a firewall to control inbound and outbound traffic.
🚀  **Public Subnets**: Used for the NAT Gateway and Application Load Balancer.
🚀  **Private Subnets**: Hosts EC2 instances for enhanced security.
🚀  **Multi-AZ Architecture**: Ensures fault tolerance by deploying resources across multiple Availability Zones.
🚀  **Application Load Balancer (ALB)**: Evenly distributes web traffic to an Auto Scaling Group.
🚀  **Auto Scaling Group**: Automatically manages EC2 instances to maintain availability, scalability, and elasticity.
🚀  **NAT Gateway**: Provides internet access for instances in private subnets.
🚀  **SSL/TLS Security**: Secured communications using AWS Certificate Manager.
🚀  **Monitoring and Notifications**: Configured Amazon SNS for alert notifications related to the Auto Scaling Group.
🚀  **Domain Management**: Registered a domain and configured DNS using Route 53.
**Version Control**: Stored project files on GitHub for easy collaboration.

---

## Architecture Diagram
Refer to the [GitHub repository](https://github.com/Mathavan1234/Host-a-Static-Website-on-AWS/blob/main/Host-a-Static-Website-on-AWS.png) for the complete architecture diagram.

---

## Prerequisites
1. An AWS account.
2. A registered domain name (configured in Route 53).
3. A GitHub repository containing the static HTML files and deployment scripts.
4. Basic knowledge of AWS services such as VPC, EC2, ALB, and Route 53.

---

## Deployment Steps

### 1. **VPC Setup**
- Create a VPC with public and private subnets distributed across two Availability Zones.
- Attach an Internet Gateway to the VPC.

### 2. **Security Configuration**
- Define Security Groups to control inbound and outbound traffic.
- Allow HTTP (port 80) and HTTPS (port 443) access for public-facing resources.

### 3. **NAT Gateway**
- Deploy a NAT Gateway in the public subnet to enable internet access for instances in private subnets.

### 4. **EC2 Instances**
- Launch EC2 instances in private subnets and configure them to host the static web application.

### 5. **Application Load Balancer**
- Create an ALB in public subnets to distribute traffic to the EC2 instances.
- Configure target groups for routing and health checks.

### 6. **Auto Scaling**
- Set up an Auto Scaling Group to manage EC2 instances based on traffic patterns.

### 7. **DNS and SSL Configuration**
- Register the domain name and configure Route 53 DNS records to route traffic to the ALB.
- Use AWS Certificate Manager to secure communications via SSL/TLS.

### 8. **Monitoring and Alerts**
- Enable monitoring for the Auto Scaling Group and set up SNS to receive notifications about scaling activities.

### 9. **Deploy Application**
Run the following Bash script on each EC2 instance to set up the static website:

```bash
#!/bin/bash
# Switch to root user
sudo su

# Update installed packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change to the Apache web root directory
cd /var/www/html

# Install Git
yum install git -y

# Clone the GitHub repository
git clone https://github.com/Mathavan1234/Host-a-Static-Website-on-AWS.git

# Copy files to the Apache web root
cp -R Host-a-Static-Website-on-AWS/. /var/www/html/

# Clean up unnecessary files
rm -rf Host-a-Static-Website-on-AWS

# Enable and start Apache
systemctl enable httpd
systemctl start httpd
```

---

## Repository Structure
- **Reference Diagram**: Contains the architecture diagram of the project.
- **Deployment Scripts**: Includes the Bash script to set up EC2 instances.
- **Static Website Files**: HTML, CSS, and JavaScript files for the web application.

---

## Benefits of This Setup
- **Scalability**: Auto Scaling adjusts resources based on traffic demands.
- **High Availability**: Multi-AZ architecture ensures uptime.
- **Security**: Private subnets and Security Groups enhance protection.
- **Automation**: Simplifies deployment with version-controlled GitHub files and automated scaling.

---

## Future Enhancements
- Implement a CI/CD pipeline for automated deployment.
- Use S3 and CloudFront for hosting static content to further enhance scalability and performance.

For more details, refer to the [GitHub repository](https://github.com/Mathavan1234/Host-a-Static-Website-on-AWS).
