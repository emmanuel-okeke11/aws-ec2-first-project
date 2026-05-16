# my-cloud-project (EC2 + Nginx)

## screenshots

### Browser-webpage
![Webpage](./screenshots/browser-webpage.png)

### EC2 Dashboard
![EC2 Dashboard](./screenshots/ec2-dashdoard.png)

### Nginx Running
![Nginx Running](./screenshots/nginx-running.png)

### Security Group Rules
![security Group](./screenshots/security-group-rules.png)


# aws-ec2-first-project
my first AWS EC2 website project using Nginx
<!DOCTYPE html>
<html>
<head>  
  <title>My First Cloud Project</title>
</head>  
<body>
  <h1>Welcome to MY AWS EC2 Wedsite</h1>
  <p>Built by Emmanuel</p>
  <p>hosted on AWS EC2 using Nginx</p>
</body>  
</html>  
# my-cloud-project (EC2 + Nginx)

I deployed a linux server on aws EC2 using Nginx. configure SSH access, HTTP traffic, security groups, and trobleshooting procedure.
THE ARCHITECTURE EXPLANATION
user browser
- EC2 public IP
- security Gruop allows port 80
- Nginx serves webpage
## screenshots

EC2 + NGINX SETUP STEPS
1) Launch EC2 instance
### Browser-webpage
![Webpage](./screenshots/browser-webpage.png)

1. Go to AWS Console → EC2 → Instances → Launch instances.
### EC2 Dashboard
![EC2 Dashboard](./screenshots/ec2-dashdoard.png)

2. Choose an AMI (example: Ubuntu Server).
### Nginx Running
![Nginx Running](./screenshots/nginx-running.png)

3. Select instance type (example: t2.micro if eligible).

4. Create/select:

• Key pair (for SSH access)

• Network settings (VPC/subnet)

5. Launch the instance.

2) Connect to the instance using SSH

1. In EC2 → Instances, select your instance.

2. Copy the public IP (or use the instance public DNS).

3. From your computer terminal (example command):

bash
ssh -i/path/to/your-key.pem ubuntu@<EC2_public_ip
Copy

• Use the correct username (e.g., ubuntu for Ubuntu, ec2-user for Amazon Linux).

4. Confirm you can log in successfully.

3) Install Nginx on EC2

1. Update package lists:

bash
sudo apt upbate
Copy

 (For non-Ubuntu, use the appropriate package manager.)

2. Install nginx:

bash
sudo apt install -y nginx
Copy

3. Start and enable it:
bash
sudo systemctl status start nginx
sudo systemctl status enable nginx
Copy

5. Verify service status:
bash
sudo syetemctl status nginx --no-pager
Copy

4) Configure the Security Group (allow web traffic)

1. Go to EC2 → Instances → Security (or open the instance’s Security group).

2. Edit inbound rules for the attached security group:

• Add rule: HTTP (port 80) from your preferred source

• Example: 0.0.0.0/0 (public) for testing

• Or better: restrict to your IP for security

3. (Optional) Add HTTPS (port 443) if you set up TLS later.

4. Save changes.
   
5) Test browser access

1. Open a browser and go to:

http://<EC2_PUBLIC_IP>

2. Confirm you see the nginx default page (or your configured page).

3. (Optional) If it doesn’t load, check:

• Nginx running: sudo systemctl status nginx

• Listening on port 80:

bash
sudo ss -tuinp | grep:80
Copy

• Security group inbound rule for port 80.
http://<EC2_PUBLIC_IP>

6) (Optional) Link to CloudWatch monitoring (high level)

If you want to connect this to AWS monitoring (CloudWatch) after setup:

1. Ensure the instance has the correct IAM role for CloudWatch (CloudWatch Agent / monitoring permissions).

2. In CloudWatch, verify metrics are showing for the EC2 instance.

3. (Optional) Create an Alarm (e.g., CPU utilization) to practice monitoring.

* TROBLESHOOTING SECTION
1 PROBLEM:
* wedsite was not loading
2 INVESTIGATION:
* checked nginx service status and security group rule.
3 CAUSE:
* port 80 was not properly accessible
4 FIX:
* updated sucrity group and restarted nginx.
### Security Group Rules
![security Group](./screenshots/security-group-rules.png)

SKILLS USED
1) AWS EC2
2) linux
3) nginx
4) SSH
5) Networking
6) Troubleshooting
