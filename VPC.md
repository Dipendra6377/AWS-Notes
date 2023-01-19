- Amazon VPC provides the facility to create an IPsec VPN connection (also known as site-to-site VPN) between remote customer networks and their Amazon VPC over the internet.
-  The following are the key concepts for a site-to-site VPN:
	- Virtual private gateway: A Virtual Private Gateway (also known as a VPN Gateway)<mark style="background: #FFB86CA6;"> is the endpoint on the AWS VPC side of your VPN connection.</mark>
	- VPN connection: A secure connection between your on-premises equipment and your VPCs.
	- VPN tunnel: An encrypted link where<mark style="background: #FFB86CA6;"> data can pass from the customer network to or from AWS.</mark>
	- Customer Gateway: An AWS resource that provides <mark style="background: #FFB86CA6;">information to AWS about your Customer Gateway device.</mark>
	- Customer Gateway device: A physical device or software application <mark style="background: #FFB86CA6;">on the customer side of the Site-to-Site VPN connection.</mark>

## Internet Gateway
- An Internet Gateway is a horizontally scaled, redundant, and highly available VPC component that allows communication between your VPC and the internet.
- An Internet Gateway serves two purposes:
	- to provide a target in your VPC route tables for internet-routable traffic
	- <mark style="background: #BBFABBA6;">to perform network address translation (NAT) for instances that have been assigned public IPv4 addresses</mark>
- an Internet Gateway supports IPv4 and IPv6 traffic. It does not cause availability risks or bandwidth constraints on your network traffic.
- <mark style="background: #FFB86CA6;"> To enable access to or from the internet for instances in a subnet in a VPC, you must do the following:</mark>
	- Attach an Internet gateway to your VPC.
	- Add a route to your subnet's route table that directs internet-bound traffic to the internet gateway.
	- If a subnet is associated with a route table that has a route to an internet gateway, it's known as a public subnet.
	- if a subnet is associated with a route table that does not have a route to an internet gateway, it's known as a private subnet.
	- Ensure that instances in your subnet have a globally unique IP address (public IPv4 address, Elastic IP address, or IPv6 address).
	- <mark style="background: #D2B3FFA6;">Ensure that your network access control lists and security group rules allow the relevant traffic to flow to and from your instance.</mark>

## NAT Instance
- <mark style="background: #ADCCFFA6;">You can use a network address translation (NAT) instance in a public subnet in your VPC to enable instances in the private subnet to initiate outbound IPv4 traffic to the Internet or other AWS services,</mark>
- It prevent the instances from receiving inbound traffic initiated by someone on the Internet As the instance E1 is in a public subnet, therefore this is not good to use.
- <mark style="background: #ADCCFFA6;">NAT instance supports port forwarding</mark>
- <mark style="background: #ABF7F7A6;">NAT instance can be used as a bastion server</mark>
- <mark style="background: #ABF7F7A6;">Security Groups can be associated with a NAT instance</mark>

## NAT Gateway

- You can use a network address translation (NAT) gateway to enable instances in a private subnet to connect to the internet or other AWS services, <mark style="background: #D2B3FFA6;">but prevent the internet from initiating a connection with those instances.</mark>
- NAT gateways need to be set up in public subnets.
- What to do to create a NAT Gateway
	-  you must specify the public subnet in which the NAT gateway should reside.
	- You must also specify an Elastic IP address to associate with the NAT gateway when you create it.
	-  The Elastic IP address cannot be changed after you associate it with the NAT Gateway.
	-  After you've created a NAT gateway, you must update the route table associated with one or more of your private subnets to point internet-bound traffic to the NAT gateway.
	- This enables instances in your private subnets to communicate with the internet.
### High Availability for NAT Gateway
- If you have resources in multiple Availability Zones and they share one NAT gateway.
- if the NAT gateway’s Availability Zone is down, resources in the other Availability Zones lose internet access.
- <mark style="background: #ADCCFFA6;">To create an Availability Zone-independent architecture, create a NAT gateway in each Availability Zone and configure your routing to ensure that resources use the NAT gateway in the same Availability Zone.</mark>


## API Gateway
- Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.
- APIs act as the "front door" for applications to access data, business logic, or functionality from your backend services.
- sing API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications.
-  API Gateway supports containerized and serverless workloads, as well as web applications.
- <mark style="background: #ADCCFFA6;">You can enable API caching in Amazon API Gateway to cache your endpoint's responses.</mark>
	- With caching, you can reduce the number of calls made to your endpoint and also improve the latency of requests to your API.
	- When you enable caching for a stage, API Gateway caches responses from your endpoint for a specified time-to-live (TTL) period, in seconds.
	- API Gateway then responds to the request by looking up the endpoint response from the cache instead of requesting your endpoint.
	- <mark style="background: #ABF7F7A6;">The default TTL value for API caching is 300 seconds. The maximum TTL value is 3600 seconds. TTL=0 means caching is disabled</mark>

## Transit GateWay
- Ruote Table: limiy VPN can talk with other VPC
- <mark style="background: #ABF7F7A6;">Support IP Multi cast(not supportes by other AWS service)</mark>
- VPN connection is a secure connection between your on-premises equipment and your VPCs.
- <mark style="background: #ADCCFFA6;">Each VPN connection has two VPN tunnels which you can use for high availability.</mark>
-  A VPN tunnel is an encrypted link where data can pass from the customer network to or from AWS.
- With AWS Transit Gateway, you can simplify the connectivity between multiple VPCs and also connect to any VPC attached to AWS Transit Gateway with a single VPN connection.

### Transit Gateway: Site to Site VPC ECMP
-  AWS Transit Gateway also enables you to scale the IPsec VPN throughput with equal cost multi-path (ECMP) routing support over multiple VPN tunnels.
- A single VPN tunnel still has a maximum throughput of 1.25 Gbps
- If you establish multiple VPN tunnels to an ECMP-enabled transit gateway, it can scale beyond the default maximum limit of 1.25 Gbps.
- You also must enable the dynamic routing option on your transit gateway to be able to take advantage of ECMP for scalability.
![[Pasted image 20230119164347.png]]

### Transit Gateway - Share Direct Connect between multiple accounts
![[Pasted image 20230119164451.png]]

 