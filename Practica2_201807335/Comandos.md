# Comandos -Proyecto 1 Juan Diego Alvarado -201807335



### VPC1 

ip 192.168.121.10 255.255.255.0 192.168.121.1
save

### VPC2

ip 192.168.121.20 255.255.255.0 192.168.121.1
save

### VPC3

ip 192.168.122.10 255.255.255.0 192.168.122.1
save

### VPC4

ip 192.168.122.20 255.255.255.0 192.168.122.1
save
  
### VPC5 

ip 192.168.123.10 255.255.255.0 192.168.123.1
save

###  VPC6

ip 192.168.123.20 255.255.255.0 192.168.123.1
save

###  solo se les configura la ip
###  configurando router1 
conf t
int f0/0
ip address 192.168.123.1 255.255.255.0
no shutdown
exit
exit

###  configurando router2
### R2
conf t
int f0/0
ip address 192.168.122.1 255.255.255.0
no shutdown
exit
exit

###  configurando router3
### R3
conf t
int f0/0
ip address 192.168.121.1 255.255.255.0
no shutdown
exit
exit



# enlazando los router  
# R1-R2

conf t
int s1/1
ip address 172.121.0.1 255.255.0.0
no shutdown
exit
exit


# R1-R3

conf t
int s1/0
ip address 172.122.0.1 255.255.0.0
no shutdown
exit
exit
# R3-R2

conf t
int s1/2
ip address 172.123.0.1 255.255.0.0
no shutdown
exit
exit
# R3-R1

conf t
int s1/0
ip address 172.122.0.2 255.255.0.0
no shutdown
exit
exit
# R2-R1

conf t
int s1/1
ip address 172.121.0.2 255.255.0.0
no shutdown
exit
exit
# R2-R3

conf t
int s1/2
ip address 172.123.0.2 255.255.0.0
no shutdown
exit
exit
# Enlanzando los routers para mandar información entre ellos


# R1-R2
conf t
ip route 192.168.122.0 255.255.255.0 172.121.0.2
exit
# R1-R3
conf t
ip route 192.168.121.0 255.255.255.0 172.122.0.2
exit


# R2-R1
conf t
ip route 192.168.123.0 255.255.255.0 172.121.0.1
exit

# R2-R3
conf t
ip route 192.168.121.0 255.255.255.0 172.123.0.1
exit

# R3-R1
conf t
ip route 192.168.123.0 255.255.255.0 172.122.0.1
exit

# R3-R2
conf t
ip route 192.168.122.0 255.255.255.0 172.123.0.2
exit