**Day 6**

## VPC
* VPC(Virtual Private Cloud) is the networking layer for Amazon EC2.
* Virtual Private Cloud enables to launch AWS resources into a virtual network using customer-defined IP address ranges.
* VPC provides customers with several options for connecting their AWS virtual networks with other remote networks.
* VPC enables developer to create security groups to set limits on inbound and outbound traffic to instances.
* The VPC contains subnets, route tables and internet gateways.

## Subnet :
* A subnet is a range of IP addresses in the VPC.
* VPC routers enable communication between instances in different subnets.
* VPC spans all of the Availability Zones in the Region. One or more subnets can be added in each Availability Zone.
* If a subnet's traffic is routed to an internet gateway, the subnet is known as a *public subnet*.
* If a subnet doesn't have a route to the internet gateway, the subnet is known as a *private subnet*.

## Route Tables:
* A route table contains a set of rules called routes. 
* Routes are used to determine where the network traffic is directed.
* Each subnet in VPC must be associated with a route table which controls the routing for the subnet.

## Internet Gateway:
* An internet gateway is a horizontally scaled, redundant and highly available VPC component that allows communication between the VPC and the internet.
* Internet gateway serves two purposes: to provide a target in the VPC route tables for internet-routable traffic, and to perform network address translation (NAT) for instances that have been assigned public IPv4 addresses.
* An internet gateway supports IPv4 and IPv6 traffic. It does not cause availability risks or bandwidth constraints on the network traffic.

## CloudWatch:
* CloudWatch monitors AWS resources and applications running on AWS.
* CloudWatch is used to collect and track metrics, which are variables that can measured for the resources and applications.
* System-wide visibility into resource utilization, application performance, and operational health can be gained using CloudWatch.

## CloudTrail:
* CloudTrail helps to enable governance, compliance, and operational and risk auditing of the AWS account.
* Actions taken by a user, role, or an AWS service are recorded as events in CloudTrail. Events include actions taken in the AWS Management Console, AWS CLI, AWS SDKs and APIs.
* A CloudTrail trail can be created to archive, analyze, and respond to changes in the AWS resources.
* A trail is a configuration that enables delivery of events to an Amazon S3 bucket that is specified.