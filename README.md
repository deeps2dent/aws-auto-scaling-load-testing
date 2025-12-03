
AWS Auto Scaling & Load Testing with Apache JMeter

A complete end-to-end implementation of a scalable web architecture using Amazon EC2 Auto Scaling Group (ASG), Application Load Balancer (ALB), CloudWatch monitoring, and Apache JMeter for performance & stress testing.

This project demonstrates how to build, monitor, test, and validate an automatically scaling infrastructure — similar to what real DevOps, Cloud, and SRE engineers do in production.

🚀 Project Overview

The goal of this project was to deploy a highly available and scalable AWS architecture capable of automatically handling sudden increases in web traffic. Apache JMeter was used to simulate load and verify scale-out and scale-in behavior.

🏗 Architecture Diagram

Architecture-Diagram.png

Architecture Components:

Application Load Balancer (ALB) – routes incoming traffic across instances

EC2 Auto Scaling Group (ASG) – scales instances based on CPU utilization

Launch Template – defines EC2 configuration

CloudWatch Metrics & Alarms – triggers scaling events

Apache JMeter – simulates heavy traffic load

🧰 AWS Services Used
Service	Purpose
EC2 Auto Scaling Group	Automatically adds/removes EC2 instances
Application Load Balancer	Distributes traffic evenly
Launch Template	Defines EC2 instance configuration
CloudWatch Dashboards	Real-time monitoring
CloudWatch Alarms	Trigger scaling actions
IAM Roles	Secure access for instance operations
VPC, Subnets, Security Groups	Networking setup
🔧 Project Implementation Steps
1. Create Launch Template

AMI with Apache web server installed

User-data script displaying "Gurdeep-ASG Web Server"

Instance type: t3.micro

Security group allowing HTTP (80)

2. Create Auto Scaling Group

Minimum instances: 1

Desired capacity: 1

Maximum capacity: 3

Subnets: us-east-1a & us-east-1b

Target tracking policy:

Trigger scale-out when CPU > 50%

3. Set Up Application Load Balancer

Target group: Gurdeep-TG

Listener: HTTP:80 → Forward to TG

Health checks enabled

4. Configure CloudWatch Dashboard

Widgets included:

CPU Utilization

Network In/Out

ALB RequestCount

Auto Scaling Group Total Instances

5. Perform Load Testing with Apache JMeter

Used both:

GUI-based test runs

CLI test runs (for higher accuracy)

Example CLI command:

.\jmeter.bat -n -t test-plan.jmx -l results.csv


JMeter Load Test Settings:

300 virtual users

5-second ramp-up

300-second duration

Requests sent to ALB DNS

Successfully triggered scale-out to 3 EC2 instances

After load stopped, ASG performed scale-in back to 1 instance

📊 Load Test Results

Add screenshots here:

Auto Scaling scale-out event

CloudWatch CPU spikes

RequestCount chart

ALB monitoring

JMeter results summary

📁 Repository Structure
aws-auto-scaling-load-test/
│
├── Documentation/
│   ├── Project-Report.pdf
│   └── Architecture-Diagram.png
│
├── Screenshots/
│   ├── asg-scale-out.png
│   ├── alb-dashboard.png
│   ├── cloudwatch-metrics.png
│   ├── scaling-events.png
│   └── etc...
│
├── JMeter/
│   ├── test-plan.jmx
│   ├── results.csv
│
└── README.md

🧪 How to Reproduce the Load Test

Download Apache JMeter 5.6.3+

Open the test plan (test-plan.jmx)

Replace the server name with your ALB DNS

Run using GUI or CLI

Monitor results in AWS CloudWatch

🧹 Cleanup Instructions (To Avoid Costs)

Make sure to delete:

Auto Scaling Group

Launch Template

Load Balancer (ALB) ← This costs money if left running!

Target Group

EC2 Instances

CloudWatch Dashboards

Unused Security Groups

Any leftover Elastic IPs

🏁 Project Outcome

✔ Successfully deployed a scalable infrastructure
✔ Load tested with JMeter and validated scaling behavior
✔ ASG scaled from 1 → 3 instances during high load
✔ ASG scaled back from 3 → 1 instance after load stopped
✔ Fully documented architecture & results

👤 Author

Gurdeep Singh
Cloud | AWS | DevOps | Networking
(Add your LinkedIn link here)

