# Example-Project-With-AWS

**Example Social Research Organization is a (fictitious) nonprofit organization** that provides a website for social science researchers to obtain global development statistics. For example, visitors to the site can look up various data, such as the life expectancy for any country in the world over the past 10 years.

**Client Brief:** The company's website was published through a commercial hosting company that provides limited support for technical issues and security. Over the past year, the website has grown in popularity. 
- As a result of increased traffic, there were complaints that the site was not as responsive as it used to be.
- The website experienced an attempted ransomware security breach.
- The security breach was unsuccessful.
The website was moved to AWS recently by the company and now, the client wants to ensure that her current design follows best practices and make sure that she has a robust and secure website.


# Design Solution Summary

Designing and deploying a robust and secure company website that returns data from the query page. This project design architecture was solely on cost optimization, high availability, autoscaling, and security by selecting and making use of the most efficient computing resources when initializing processes, which could always be scaled up in case of business growth.

![Capstone Diagram-Example drawio](https://github.com/Ujagbor/Example-Capstone-Project/assets/101636247/82883f5a-85d1-453a-8d44-e09f7552979b)

## Solution

## LAMP Web Server on Linux
Installed a LAMP web server to deliver a high-performance web application.

## EC2

- Provided anonymous access to web users.
- I opened port 80 from the security group of the Cloud9 EC2 instance to allow inbound traffic on port 80.
- This adjustment enables external access to the web server hosted on the EC2 instance, facilitating seamless communication over HTTP protocols.

## MySQL RDS Database

### Provided secure hosting of the MySQL database. 

- In creating an RDS database, I created an AWS RDS subnet group in the private subnets in zones us-east-1a and us-east-1b.
- I edited the security group by adding an inbound rule to restrict access to MySQL/aurora database.
- To enforce secure access controls for MySQL/Aurora database, adding an inbound rule within the associated security group specifies only allowed traffic sources to the database instance.
- By configuring the security group in this manner, the designated instance can communicate with MySQL/Aurora database, only the administrative users can import the database, enhancing the overall security posture of our infrastructure.

**Ran the website on a t2.micro EC2 instance, and provided Secure Shell (SSH) access to administrators.**

## Parameter Store

- Stored database connection information in the AWS Systems Manager Parameter Store.
- Configured parameter values and attached an IAM role called the Inventory-App role that permits access to the database. Information was stored successfully in the parameter store.

## Application Load Balancer

Provided high availability to the website through an application load balancer

## Automatic Scaling Group

- Provided automatic scaling that uses a launch template.
- Created an AMI for the Cloud9 instance.
- Modified the IAM role of the instance created by Cloud9 to enable queries on the website.
- Modified the launch template with the recent version of the AMI. This allowed connection to the website by entering the Load Balancer's endpoint, it queried the data from the RDS database successfully too.


