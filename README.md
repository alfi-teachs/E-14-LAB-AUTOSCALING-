# E-14-LAB-MANUAL SCALING AUTOSCALING-

AWS EC2 AMI & Instance Scaling Lab
# Step 1: Launch EC2 Instance

Go to Amazon Web Services Console → EC2

Click Launch Instance

Choose:

AMI: Amazon Linux

Instance Type: t2.micro

Create or select a Key Pair

Launch the instance

# Step 2: Connect to Instance

ssh -i your-key.pem ec2-user@<public-ip>

# Step 3: Install Apache & Create Files

sudo su

# Create directory and files

mkdir /data

cd /data

touch file{1..100}

# Update system

yum update -y

# Install Apache
yum install httpd -y

# Start and enable service
systemctl start httpd
systemctl enable httpd
systemctl status httpd

Step 4: (Optional) Change Instance Type
Stop instance → Actions → Instance Settings → Change Instance Type
Example: t2.micro → t3.micro
Step 5: Create AMI (Amazon Machine Image)
Go to EC2 → Instances
Select your instance
Click Actions → Image and Templates → Create Image
Give name → Click Create
Step 6: Check AMI Status
Go to EC2 → AMIs
Wait until status shows Available
Step 7: Launch Instance from AMI
Select your AMI → Click Launch Instance
Choose instance type (you can change here if needed)
Launch instance
Step 8: Connect to New Instance
ssh -i your-key.pem ec2-user@<new-public-ip>

Step 9: Verify Data
sudo su
ls /data


You should see:

file1 file2 file3 ... file100

Open browser:
http://<public-ip>


Apache should be running.

Step 10: Vertical Scaling (Resize Instance)
Stop instance
Go to Actions → Instance Settings → Change Instance Type
Select:
t3.micro (or any required type)
Start instance again
What this lab really shows
How to install and configure a web server
How AMI captures full instance state (data + software)
How to launch identical servers from AMI
How vertical scaling works by changing instance type

















 
  


































