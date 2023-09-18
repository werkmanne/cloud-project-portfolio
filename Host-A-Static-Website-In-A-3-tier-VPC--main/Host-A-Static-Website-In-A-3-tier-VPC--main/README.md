<h1># Host-A-Static-Website-In-A-3-tier-VPC-</h1> 

<img src='Host-A-Static-Website-In-A-3-tier-VPC Reference Architecture.png' alt='Host-A-Static-Website-In-A-3-tier-VPC Reference Architecture'>

<h2>Introduction</h2>

This readme file provides an overview of the project hosted on an Amazon EC2 instance within a 3-tier VPC. The project is a website that consists of HTML files, CSS stylesheets, and JavaScript files. This document will guide you through the setup, deployment, and usage of the project.

<h2>Prerequisites</h2>
<p><b>Before getting started with the project, you'll need the following prerequisites:</b></p>

<ol type="1">
	<li>An Amazon Web Services (AWS) account</li>
	<li>Basic knowledge of AWS services, EC2 instances, VPCs, and security groups.</li>
</ol>

<h2>Architecture Design</h2>
<h3>VPC Design:</h3>
<p>Create a new VPC with three subnets: Public, Private, and Database.</p>
<ol type="1">
	<li>Public Subnet: This subnet will host the EC2 instance that serves as the web server accessible to the public internet.</li>
	<li>Private Subnet: This subnet will be used for backend application servers or services that don't require direct public access.</li>
</ol>
<h3>Security Groups:</h3>
<p>Set up appropriate security groups to control inbound and outbound traffic for each subnet and the EC2 instance.</p>
<ol type="1">
	<li>Application load balance: Allow incoming HTTP (port 80) and HTTPS (port 443) traffic from 0.0.0.0/0 .</li>
	<li>Private EC2 Instances Security Group: Allow incoming HTTP (port 80) and HTTPS (port 443) traffic from Application Load Balancer</li>      
</ol>
</ol>
<h3>Autoscaling Group:</h3>
<p>Create an autoscaling group that will automatically adjust the number of EC2 instances based on traffic load.</p>

<h3>Application Load Balancer (ALB):</h3>
<p>Set up an Application Load Balancer to distribute incoming traffic across the EC2 instances.</p>
<h3>Route 53:</h3>
<p>Use Route 53 for domain registration (if required) and DNS management to point the domain to the ALB.</p>
<h3>Amazon Certificate Manager (ACM):</h3>
<p>Obtain an SSL/TLS certificate from ACM for secure HTTPS communication.</p>


<h2>Setup</h2>
<ol type="1">
	<li>Create VPC with public and private subnets in 3 availability zones with internet gateway, nat-gateway, route-table, public and private subnet.</li>
	<li>Create Security groups to allow traffic</li>
        <li>Application Load Balancer to distribute web traffic across an Auto Scaling Group of EC2 instances in multiple AZs.</li>
        <li>Using Auto Scaling Group to dynamically create our EC2 instances to make our website highly available scalable, fault-tolerant, and elastic.</li>
        <li>Route 53 to register our Domain name and create a record set and use ACM to secure the domain</li>
        <li>We will store our Webfiles in a GitHub repository.</li>
</ol>

<h2>Implementation Steps</h2>
<h3>Step 1: Launch EC2 Instance and Create Website Files to test your launch configuration script</h3>
<p>Launch an EC2 instance in the Public Subnet with an appropriate Amazon Machine Image (AMI) that supports your web server (e.g., Apache or Nginx).</p>
<p>Connect to the EC2 instance using SSH.</p>
<p>Download the HTML, CSS, and JavaScript files to the EC2 instance from GIthub repository and configure the web server to serve them.</p>

<h3>Step 2: Create and Configure the ALB</h3>
<p>Create an Application Load Balancer in the same VPC, ensuring it has a public IP address.</p>
<p>Configure the ALB to listen on HTTP (port 80) and HTTPS (port 443). Use the SSL/TLS certificate from ACM for HTTPS configuration.</p>
<p>Set up a target group for the ALB and associate it with the EC2 instances.</p>

<h3>Step 3: Set Up Autoscaling Group</h3>
<p>Create an Autoscaling Launch Template, specifying the AMI, instance type, security groups, and add the Bash Script to User Data</p>
<p>Configure the ALB to listen on HTTP (port 80) and HTTPS (port 443). Use the SSL/TLS certificate from ACM for HTTPS configuration.</p>
<p>Configure the Autoscaling Group to use the created launch configuration and the target group associated with the ALB.</p>
<p>Set up autoscaling policies based on metrics such as CPU utilization or request count to automatically adjust the number of EC2 instances.</p>

<h3>Step 4: Register Domain in Route 53</h3>
<p>In Route 53, register your domain (if you haven't already) or configure the DNS settings for an existing domain.</p>
<p>Create an "A" record for your domain and associate it with the ALB's public IP address.</p>

<h3>Step 5: Obtain SSL/TLS Certificate from ACM</h3>
<p>In the AWS Management Console, go to Amazon Certificate Manager (ACM).</p>
<p>Request a new SSL/TLS certificate for your domain.</p>
<p>Choose the DNS validation method to prove ownership of the domain.</p>
<p>Once the certificate is issued, associate it with the Route 53 domain</p>

<h3>Step 6: Test and Monitor</h3>
<p>Test the website by accessing it through the domain name. It should be served securely over HTTPS and be accessible through the ALB.</p>
<p>Monitor the website's performance and autoscaling behavior using CloudWatch metrics and logs.</p>


<h2>Conclusion</h2>
<p>By following the steps outlined in this guide, you should have successfully deployed your website on an Amazon EC2 instance within a 3-tier VPC, using autoscaling, an Application Load Balancer, Route 53 for DNS management, and an SSL/TLS certificate from Amazon Certificate Manager. This architecture ensures high availability, scalability, and security for your website, making it well-prepared to handle varying levels of traffic and deliver a smooth user experience. Always remember to keep your infrastructure updated, secure, and properly monitored to ensure the best performance for your website.</p>
