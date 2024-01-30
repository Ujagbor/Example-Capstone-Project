 Create a database in RDS
DB Name: Example
DB Engine: MySQL
DB Template: Dev/Test
Deployment: Multi-AZ DB instance
Master Username: admin
Master Password: ***
DB Instance Size: db.t3.micro
Storage type: General purpose
Allocated Storage: 20GiB
Storage autoscaling: Enabled - 1000GiB
VPC- Example VPC
*** Create DB Subnet group: Example-DB-subnet
VPC Subnet - Example VPC
Subnets: us-east-1a; us-east-1b
	10.0.2.0/23; 10.0.4.0/23
VPC security group: Example-DB
Backup: Disable
Monitoring: Disable
Initial database name: Example
Create database
