<h1>Deploy a WordPress Website on AWS</h1>

<img src='1._WordPress_Project_Reference_Architecture.jpg' alt='WordPress_Project_Reference_Architecture'>

<h3>Introduction</h3>

<p>I am glad to see you here again for our next real world project! We will learn how to deploy this dynamic website on AWS. We will also learn how to use my reference architecture to host this website using various AWS services and how they work together:</p>

<ul>
<li>VPC with public and private subnets</li>
<li>Security groups</li>
<li>EC2 instances</li>
<li>NAT gateways</li>
<li>RDS</li>
<li>Application load balancer</li>
<li>Route 53</li>
<li>Auto scaling group</li>
<li>Certificate manager</li>
<li>EFS and more</li>
</ul>

<h3>Objectives</h3>
<ol>
<li>Build a three-tier AWS network VPC from scratch</li>
<li>Create NAT gateways</li>
<li>Create the security groups</li>
<li>Create the RDS instance</li>
<li>Create the elastic file system</li>
<li>Create a key pair</li>
<li>Download putty</li>
<li>Launch the setup server</li>
<li>SSH into an EC2 instance in the public subnet</li>
<li>Create an application load balancer</li>
<li>Register a new domain name in Route 53</li>
<li>Create a record set in route 53</li>
<li>Register for an SSL certificate in AWS certificate manager</li>
<li>Launch bastion host</li>
<li>SSH into an instance in the private subnet</li>
<li>Create an HTTPS listener for the application load balancer</li>
<li>Create an auto scaling group</li>
<li>Install WordPress theme and template</li>
<li>Clean up</li>
</ol>
