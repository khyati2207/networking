LINUX-NETWORKING
Question 1 
Problem: None.
ip addr show
It showed the IP 10.244.102.175 on the eth0 interface.
Why I used it:
●	ip addr show lists every network interface on the machine along with its IP address. The loopback one (lo) is just 127.0.0.1 and can be ignored - the real one is under eth0.
<img width="1920" height="1080" alt="Screenshot (464)" src="https://github.com/user-attachments/assets/d3797676-de9c-46ef-b4eb-e3a5df1a9a55" />


Question 2 
Problem: None,.
The answer is eth0 - it was shown right there in the same command output.
<img width="1920" height="1080" alt="Screenshot (466)" src="https://github.com/user-attachments/assets/e40f5f12-5691-4ea2-9695-47afa0e7446f" />


Question 3 
Problem: None.
ip route show
It showed: default via 169.254.1.1 dev eth0
Why I used it:
●	ip route show shows the routing table, and the line starting with default via is exactly the default gateway.
<img width="1920" height="1080" alt="Screenshot (468)" src="https://github.com/user-attachments/assets/6266ca96-b53c-4aa6-b594-cb82b80547e3" />


Question 4 
Problem: None.
ip link show eth0
The output included the word UP in the flags, confirming it's active.
<img width="1920" height="1080" alt="Screenshot (470)" src="https://github.com/user-attachments/assets/3eed1f5c-e42e-49c6-a266-df8062c6a277" />


Question 5 
Problem: None.
The answer is ip link. ip addr is for IP addresses, ip route is for routing, and netstat -i can only show info, not change anything.
<img width="1920" height="1080" alt="Screenshot (472)" src="https://github.com/user-attachments/assets/ee6c4518-f93d-4ee3-8748-16c1621100ee" />


Question 6 
Problem: None.
The answer is ip addr - it specifically shows IP addresses assigned to interfaces.
<img width="1920" height="1080" alt="Screenshot (474)" src="https://github.com/user-attachments/assets/a1b715a3-f283-47f6-b74f-dc91ed1fb1b7" />


Question 7 
Problem: None.
The answer is ip route add. Following the pattern of ip <thing> <action>, since we're adding a route, it has to be ip route add.
<img width="1920" height="1080" alt="Screenshot (476)" src="https://github.com/user-attachments/assets/ee7dccbf-a9b8-475a-bc9c-ae9160db8bad" />


Question 8 
Problem: None.
The answer is: to connect two or more different networks together. A router's whole point is joining separate networks - connecting devices on the same network is a switch's job instead, not a router's.
<img width="1920" height="1080" alt="Screenshot (478)" src="https://github.com/user-attachments/assets/a40575f3-8efc-4c70-8a3b-e6e06777c103" />


Question 9 
Problem: None
The answer is: no gateway is needed to reach that destination. This usually shows up for networks that are directly connected, so there's no need to hop through another router.
<img width="1920" height="1080" alt="Screenshot (480)" src="https://github.com/user-attachments/assets/15af32a7-4b99-4cc9-b3f5-e07a3a32905d" />


Question 10 
Problem: None.
The answer is /etc/network/interfaces. This is the standard file used on Debian/Ubuntu systems  to make network settings permanent.
<img width="1920" height="1080" alt="Screenshot (482)" src="https://github.com/user-attachments/assets/c19aed5b-4172-47c9-ac19-f980af404da2" />


Question 11
Problem: None.
The answer is: a switch can only deliver packets to hosts within the same network. Switches work inside one single network only - connecting different networks together is a router's job instead.
<img width="1920" height="1080" alt="Screenshot (484)" src="https://github.com/user-attachments/assets/b583f92d-a99d-4cfc-b69e-1feea5489597" />


Question 12 
Problem: None.
ip link
It showed only 2 interfaces total: lo (loopback) and eth0.
  <img width="1920" height="1080" alt="Screenshot (486)" src="https://github.com/user-attachments/assets/f11691f4-82eb-4577-af8c-aa46314ed2d6" />


Question 13 
Problem: None.
The answer is default - this is literally what shows up in the routing table output itself  so it was actually already visible from an earlier command.
<img width="1920" height="1080" alt="Screenshot (488)" src="https://github.com/user-attachments/assets/ed0d8384-4aba-4ed4-97fa-ab1be620fc3c" />

