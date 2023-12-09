# VPC-to-VPC-Peering

1. What is VPC?
VPC is virtual private cloud where we create our own network which is isolated from internet. In VPC we decide which which traffic should come and go.

2. subnet
subnet is sub network where we divide our network in different parts using ip address

3. Internet Gateway
Internet Gateway use to give public access to subnet

4. NAT(Network Address Translation) Gateway
NAT Gateway is used to give internet access of Private Subnet using Public Subnet

# Hands on with AWS

1. Crate VPC With 65536 IP Address:
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/94d7d7c7-489a-4daf-831c-2a6338e204e7)

2. Also Create Public subnet with IP addresses:
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/8778d542-e569-4aa8-a999-97c0c558056b)

3. Create EC2 instance in that VPC: You have to give auto IP assign to vpc without that we not able to access ec2 instace publically
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/0821f1d5-e6b9-44b6-b992-031584030832)

4. Create Internet Gateway And attach to vpc
5. Create Route Table but they don't know how to communicate with VPC goto subnet association present at route table and edit or add to public subnet
6. Now also Route Table Don't know how to communicate with Internet Gateway so  goto Routes and add to 0.0.0.0 to internet gateway

7. Now connect ec2 successfully
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/1f8f80a0-52bb-43a6-a57a-2547b0dd90e3)



