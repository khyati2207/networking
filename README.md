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

AWS Take-Home Assignment - My Notes
Assignment: Building a Two-Tier Web Application Infrastructure
This is a simple record of what I did, the commands I used, why I used them, and the problems I ran into while building the VPC, security groups, and EC2 instances. Add your screenshots below each part.

Part 1 and 2 - VPC, Subnets, and Security Groups
I set up the VPC (two-tier-vpc), the public and private subnets, the internet gateway, and the two security groups (webapp-sg and database-sg) as asked in the assignment.
Problem: None to report here yet 
<img width="1920" height="1080" alt="Screenshot (492)" src="https://github.com/user-attachments/assets/88389ec0-8253-4b93-8e90-4e6a67cbb22f" />


Part 3 - Launching the Instances
What I had to do: Launch Web-Server in the public subnet (with a public IP) and DB-Server in the private subnet (with no public IP).
Problem: None. Both instances came up fine.
Checked the result in the EC2 instances list:
●	DB-Server - Running, t3.micro, private IP 10.10.2.195, no public IPv4 address - exactly what was needed since it should not be reachable from the internet.
●	Web-Server - Running, t3.micro, in the public subnet.
Why this matters:
●	DB-Server having no public IP is the whole point of this design - it keeps the database completely unreachable from the internet, and it can only be reached from inside the VPC (like from Web-Server).
<img width="1920" height="1080" alt="Screenshot (490)" src="https://github.com/user-attachments/assets/ee6da9e4-f721-4250-9cb8-87ae196f7ad0" />


Part 4, Task 1 - Access Web-Server from the browser
What I had to do: Open the Web-Server's public IP in a browser and confirm the web server is working.
Problem: None, worked right away.
Opened http://34.226.248.220 in the browser and it showed "Welcome to Web Server" - confirming the User Data script installed and started the web server correctly, and that the security group is allowing inbound HTTP (port 80) from anywhere like it should.
<img width="1920" height="965" alt="Screenshot (494)" src="https://github.com/user-attachments/assets/be8de972-cba2-4f0a-af5f-f28076f41ce3" />


Part 4, Task 2 - SSH into the Web-Server
What I had to do: SSH into the Web-Server using its key pair.
ssh -i "C:\Users\KHYATIS\Downloads\my-web-key.pem" ec2-user@34.226.248.220
Problem I faced:
●	The connection failed with Permission denied (publickey,gssapi-keyex,gssapi-with-mic). The terminal showed a warning: UNPROTECTED PRIVATE KEY FILE, saying the .pem file's permissions were too open, so SSH refused to use the key at all.
●	This happens because on Windows, a downloaded .pem file is often readable by more than just the current user by default, and SSH requires the private key file to not be accessible by others, for security reasons.
Why this matters:
●	The .pem file permissions need to be locked down (so only your own Windows user account can read it) before SSH will accept it - otherwise it treats the key as unsafe and blocks the login attempt completely, even if the key itself is correct.


Part 4, Task 3 - Ping DB-Server's private IP from Web-Server
What I had to do: From inside the Web-Server (after SSHing in), ping the private IP of DB-Server and confirm it succeeds.
ping 10.10.2.195
Problem I faced:
●	The ping timed out completely - 4 packets sent, 0 received, 100% loss.
●	Looking at it again, this ping was run directly from my own Windows machine's Command Prompt, not from inside the Web-Server. Since 10.10.2.195 is a private IP inside the AWS VPC, it can only be reached from devices inside that same VPC (like the Web-Server itself) - it is not reachable at all from my home/local network over the internet, so the timeout was expected.
●	This step still needs to be redone properly: first SSH successfully into Web-Server (after fixing the key permission problem above), and then run the ping command from inside that SSH session, not from the local machine.
Why this matters:
●	Private IPs only work within the VPC's internal network. This is exactly what keeps the DB-Server isolated from the public internet, but it also means any testing of that connection has to happen from another instance inside the same VPC, not from outside it.
<img width="1920" height="1024" alt="Screenshot (493)" src="https://github.com/user-attachments/assets/290a51d7-7b41-40d9-bb71-4ae0c55b09c7" />


Deliverable - database-sg inbound rules
What I had to check: Make sure database-sg only allows MySQL/Aurora (port 3306) traffic, and only from webapp-sg.
Problem: None - checked the console and the rule was already set up correctly.
The Inbound rules tab for database-sg showed exactly 1 rule: Type MYSQL/Aurora, Protocol TCP, Port range 3306, Source set to the webapp-sg security group (not an IP address or 0.0.0.0/0).
Why this matters:
●	Using another security group as the source (instead of an IP range) means only instances that belong to webapp-sg can reach the database on port 3306 - nothing else, including the open internet, can get in. This is exactly the kind of tight, least-access firewall rule the assignment wanted.
<img width="1920" height="1080" alt="Screenshot (492)" src="https://github.com/user-attachments/assets/2584ffd1-08ee-4997-bacb-cce9cbcca222" />


Overall - What went wrong the most
●	SSH key permissions - the downloaded .pem file on Windows had permissions that were too open, so SSH refused to use it and blocked the login. Needs to be fixed (locking down file permissions) before SSH will work.
●	Tested the private-IP ping from the wrong place - ran it from my own local machine instead of from inside the Web-Server over SSH, so it timed out as expected. Need to SSH in first, then run the ping from there.
●	Everything else (VPC setup, instance launch, web server test, security group rule for the database) worked correctly without issues.


