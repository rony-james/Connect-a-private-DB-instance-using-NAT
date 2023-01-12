# Connect-a-private-DB-instance-using-NAT
We have a wordpress website which need to connect a DB server in a private instance.




![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/NAT.jpg?raw=true)



## Used Resources

- EC2
- Internet Gateway
- NAT
- VPC


In this diagram, we have 3 instances.

1. Intance which contain wordpress website
2. JUMB server for accessing other EC2
3. DB instance

![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/EC2s.png?raw=true)



A VPC and three subnet where created for these three instances. We have 2 public subets and one private subnet. DB server placed in a privet subnet for ensue the securiy. Jumb server and wordpress instance placed in public subnet. 

Jumb server is only used to access all other servers. Wordpress and DB instance only allow the SSH access from the Jumb server.


![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/VPC.png?raw=true)


We need to create an additional RT for the private subnet. Because of the privet subnet, DB server did not have any public IP. So if it needed an external communication, we need to create a NAT environment. 

![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/NAT.png?raw=true)


That NAT entry should be specified in the private RT. While creating NAT, It should be placed in a public subnet. If the DB server need to communicate outside, NAT will do that job. Also we should specify the IGW in the main Routing Table.


![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/Routing%20Tables.png?raw=true)





![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/Adding%20NAT%20into%20the%20privet%20RT.png?raw=true)







![alt text](https://github.com/rony-james/Connect-a-private-DB-instance-using-NAT/blob/main/routes.png?raw=true)



While configuring the wordpress, we should specify the private IP of DB instance.
