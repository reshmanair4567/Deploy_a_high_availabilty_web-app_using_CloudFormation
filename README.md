This projects aims to deploy Infrastructure as a Code


To create a new stack, run create. sh followed by the the stack name and template body


aws cloudformation create-stack --stack-name infrastack --region us-west-2 --template-body file://server.yml --parameters file://server-params.json --capabilities CAPABILITY_IAM


Example : ./create.sh infrastack server.yml server-params.json


The template body is a parameter file with default values

To update an exisiting stack :
aws cloudformation update-stack --stack-name infrastack --region us-west-2 --template-body file://ourinfra.yml --parameters ourinfra-params.json --capabilities CAPABILITY_IAM


./update.sh infrastack server.yml server-params.json


To delete a stack:
aws cloudformation delete-stack --stack-name $1 --region=us-west-2



./delete.sh infrastack

Resources :

Bastion Host:
If you do need to connect directly to instances, it's best (and for instances in a private subnets, a requirement) to use a bastion host, otherwise known as a jump box. A bastion host is an EC2 instance that is publicly accessible, and also has access to private resources, allowing it to function as a secure go-between. You configure your EC2 instances to only accept ssh traffic from the bastion host, then you can ssh into the bastion host, and from there connect to your private resources.

NAT Gateway:
You can use a network address translation (NAT) gateway to enable instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating a connection with those instances. 
NAT gateways are not supported for IPv6 traffic—use an egress-only internet gateway instead.

Application Load Balancer :
A load balancer serves as the single point of contact for clients. The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones. This increases the availability of your application. You add one or more listeners to your load balancer.
A listener checks for connection requests from clients, using the protocol and port that you configure, and forwards requests to one or more target groups, based on the rules that you define. Each rule specifies a target group, condition, and priority. When the condition is met, the traffic is forwarded to the target group. You must define a default rule for each listener, and you can add rules that specify different target groups based on the content of the request (also known as content-based routing).
Each target group routes requests to one or more registered targets, such as EC2 instances, using the protocol and port number that you specify. You can register a target with multiple target groups. You can configure health checks on a per target group basis. Health checks are performed on all targets registered to a target group that is specified in a listener rule for your load balancer.

S3:
Amazon Simple Storage Service is storage for the Internet. It is designed to make web-scale computing easier for developers.Amazon S3 has a simple web services interface that you can use to store and retrieve any amount of data, at any time, from anywhere on the web. It gives any developer access to the same highly scalable, reliable, fast, inexpensive data storage infrastructure that Amazon uses to run its own global network of web sites. The service aims to maximize benefits of scale and to pass those benefits on to developers.

EC2 instance:
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.
Amazon EC2’s simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change. Amazon EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. Amazon EC2 provides developers the tools to build failure resilient applications and isolate them from common failure scenarios.

VPC:
Amazon Virtual Private Cloud (Amazon VPC) enables you to launch AWS resources into a virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

