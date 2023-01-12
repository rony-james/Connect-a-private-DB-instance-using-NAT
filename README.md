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

A VPC and three subnet where created for these three instances. We have 2 public subets and one privet subnet. DB server placed in a privet subnet for ensue the securiy. Jumb server and wordpress instance placed in public subnet. 

We need to reate an additional RT for the privet subnet. Because of the privet subnet, DB server did not have any public IP. So if it needed an external communication, we need to create a NAT environment. That NAT entry should be specified in the privet RT. NAT should be placed in a public subnet. If the DB server need to communicate outside, NAT will do that job. Also we should specify the IGW in the main Routing Table.
