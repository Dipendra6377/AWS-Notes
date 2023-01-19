## Network Load Balancing
- Network Load Balancer is best suited for use-cases involving low latency and high throughput workloads that involve scaling to millions of requests per second.
-  Network Load Balancer operates at the connection level (Layer 4), routing connections to targets - Amazon EC2 instances, microservices, and containers – within Amazon Virtual Private Cloud (Amazon VPC) based on IP protocol data.
- <mark style="background: #ABF7F7A6;">Network Load Balancers expose a fixed IP to the public web, therefore allowing your application to be predictably reached using these IPs,</mark>

## Application Load Balancing
- Application Load Balancer operates at the request level (layer 7), routing traffic to targets – EC2 instances, containers, IP addresses and Lambda functions based on the content of the request.
- Ideal for advanced load balancing of HTTP and HTTPS traffic
-  Application Load Balancer provides advanced request routing targeted at the delivery of modern application architectures, <mark style="background: #FFF3A3A6;">including microservices and container-based applications.</mark>
- <mark style="background: #BBFABBA6;">Application and Classic Load Balancers expose a fixed DNS (=URL) rather than the IP address.</mark>

# Auto Scaling Group

-  <mark style="background: #ABF7F7A6;">ASG does not have a dynamic Elastic IPs attachment feature.</mark>
- An Auto Scaling group also enables you to use Amazon EC2 Auto Scaling features such as health check replacements and scaling policies.
- Both maintaining the number of instances in an Auto Scaling group and automatic scaling are the core functionality of the Amazon EC2 Auto Scaling service
- You configure the size of your Auto Scaling group by setting the minimum, maximum, and desired capacity.
- If you do not define your desired capacity upfront, it defaults to your minimum capacity.