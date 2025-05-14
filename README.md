☁️ Cloud Honeypot Trap + Alert System
Author: Satyam Pandey
An AWS-based intrusion detection project that deploys a Cowrie honeypot in a cloud environment, monitors attacker behavior, and triggers real-time alerts using Lambda and SNS.

🔥 Project Objective
Create a cloud-native trap (honeypot) that:

Simulates a vulnerable SSH server (for attackers to target)

Monitors attacker behavior using logging & CloudWatch

Sends real-time alerts to the admin when threats are detected

🧠 How It Works
👨‍💻 A public-facing EC2 instance (honeypot) with open SSH port is deployed.

🕵️ Cowrie honeypot is installed to mimic a real Linux system.

📊 Logs are sent to AWS CloudWatch.

🚨 A Lambda function is triggered on suspicious patterns (brute-force, login attempts).

📧 SNS sends an email alert to the system admin with the attack details.

🛠 Tech Stack
AWS EC2 (Ubuntu-based Honeypot server)

Cowrie SSH Honeypot

AWS CloudWatch Logs + Metric Filter

AWS Lambda (Python)

AWS SNS (Simple Notification Service)

Terraform for full Infrastructure-as-Code (IaC)

📦 Folder Structure
perl
Copy
Edit
cloud-honeypot-alert-system/
│
├── terraform/              # EC2, CloudWatch, IAM, Lambda setup
│   └── main.tf
│
├── scripts/
│   └── setup_honeypot.sh   # Cowrie installation script
│
├── lambda/
│   └── alert_function.py   # Python Lambda function
│
├── README.md
└── report.pdf              # Project architecture & test results
⚙️ Installation Guide
Step 1: Clone the repo
bash
Copy
Edit
git clone https://github.com/yourusername/cloud-honeypot-alert-system.git
cd cloud-honeypot-alert-system
Step 2: Deploy Infrastructure via Terraform
bash
Copy
Edit
cd terraform/
terraform init
terraform apply
This creates:

EC2 instance

CloudWatch group

Lambda + IAM Role

SNS Topic

Step 3: SSH into EC2 and run Honeypot setup
bash
Copy
Edit
chmod +x scripts/setup_honeypot.sh
./scripts/setup_honeypot.sh
Step 4: Set up Lambda Trigger (via console or Terraform)
Ensure that:

CloudWatch metric filter matches "login attempt"

Lambda has SNS publish permissions

✅ Features
Logs attacker username/password attempts

Sends email alerts with IP address & timestamp

Cowrie logs available at /var/cowrie/log

Fake file system to fool attackers

📷 Screenshots (Add later in your repo)
EC2 public IP showing open SSH port

Cowrie logging attacker inputs

Lambda CloudWatch log trigger

Email alert with attacker IP

💡 Use Cases
Educational & lab simulation

Detect botnet scanners or brute-force attempts

Honeynet setup for red-teaming

🔒 Security Tips
Never allow this EC2 to connect to production servers

Use VPC and Security Groups to isolate traffic

Rotate IAM credentials after setup

🧩 Future Enhancements
Store alerts in DynamoDB with timestamp

Visual dashboard (using Grafana or Quicksight)

Add more honeypots (e.g., HTTP, FTP, MySQL)

📜 License
MIT License

