# VPC-to-VPC-Peering

1. What is VPC?
VPC is virtual private cloud where we create our own network which is isolated from internet. In VPC we decide which which traffic should come and go.

2. subnet
subnet is sub network where we divide our network in different parts using ip address

3. Internet Gateway
Internet Gateway use to give public access to subnet

4. NAT(Network Address Translation) Gateway
NAT Gateway is used to give internet access of Private Subnet using Public Subnet

# Architecture
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/9cc29a5e-e995-45f0-9470-47bc521cab2b)


# Hands on with AWS

# First VPC

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

# Second VPC

1. Create Second VPC With different IP ranges
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/c03e81c4-bd4d-4097-ac61-4fc20cac0471)

2. Also Create subnet for second VPC
3. Create Internet Gateway and attach to VPC
4. Create Route Table also same as first vpc
5. communicate That RT with vpc using subnet association
6. Also communicate that RT with Internet gateway using routes


# what is vpc peering 
when one ec2 instace send request to another ec2 instance which present in another vpc and one ec2 instance accept request this called as vpc peering

1. Now goto peering network present in VPC and add both vpc's for peering
2. Now we need to accept request hence select peering network and click on actions and click on accept request

3. Then also connection is not possible
4. So connection is possible by route table
5. so do test route table peer for production route table using Routes as add prod ip address to routes and target as peering connection

![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/e3a60370-c6c0-4e0e-aa85-5565f9fe09aa)

6. Same do for production route table
![image](https://github.com/shubhamkale119/VPC-to-VPC-Peering/assets/128287182/2fbb9adc-912e-4c44-b396-d0d7ed63ffed)

7. Then also peering is not possible due to security groups
8. to peer add security group as All ICMP-IPv4 protocol and add ip as opposite vpc means if you are adding protocol to test vpc the add ip address of prod vpc in test vpc and vice versa
9. After ping using instances


# How to go public subnet to private subnet

1. goto subnet and create subnet using or without overlap of ip address
2. Now create NAT Gateway(NAT gateway is between public to private subnet) and select subnet public for NAT gateway
3. Now this nat gateway add through route table as Routes and add ip adress whichever you want to access private subnet in vpc
4. and save it now private subnet is accessable to specific address





