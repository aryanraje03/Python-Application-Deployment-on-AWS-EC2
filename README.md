# Python Flask Application Deployment on AWS EC2

Using Python, pip, Virtual Environment, and Gunicorn

---

## Project Overview

This project walks through the deployment of a Python Flask web application on an Amazon EC2 instance running Amazon Linux 2023. The application is set up using a Python virtual environment, dependencies are installed via pip from a `requirements.txt` file, and the app is served using Gunicorn.

This project was completed as part of a Cloud and DevOps learning journey to build practical, hands-on experience with:

- AWS EC2 instance setup and configuration
- Linux server administration
- Python Flask application hosting
- Virtual environment management
- Package management using pip
- End-to-end cloud deployment of a production-style Python application

---

## Technologies Used

| Technology             | Purpose                        |
| ---------------------- | ------------------------------ |
| AWS EC2 (Amazon Linux) | Cloud Virtual Server           |
| Python                 | Programming Language / Runtime |
| pip                    | Python Package Manager         |
| Flask                  | Web Framework                  |
| Gunicorn               | WSGI HTTP Server               |
| Virtual Environment    | Isolated Python Environment    |
| Linux                  | Server Operating System        |

---

## Project Architecture

```
User
  ↓
Internet
  ↓
AWS EC2 (Amazon Linux 2023)
  ↓
Python Virtual Environment
  ↓
Flask Application (served via Gunicorn)
```

---

## Deployment Steps

### Step 1 — Launch an EC2 Instance

- Create an Amazon Linux 2023 EC2 instance (t3.micro) from the AWS Console.

> <img src="/Screenshots/EC2-Instance.jpeg" width="1000">

- Configure the Security Group with the following inbound rules:

| Type | Port |
| ---- | ---- |
| SSH  | 22   |
| HTTP | 80   |
| TCP  | 5000 |

- Connect to the instance via SSH:

```bash
ssh -i "your-key.pem" ec2-user@your-ec2-public-ip
```

---

### Step 2 — Update System Packages

```bash
sudo yum update -y
```

---

### Step 3 — Install Python 3

```bash
sudo yum install python3 -y
python3 --version
```

> <img src="/Screenshots/Python Installation.jpeg"  width="1000">

---

### Step 4 — Install pip

```bash
sudo yum install python3-pip -y
pip3 --version
```

> <img src="/Screenshots/Python Pip Installation.jpeg" width="1000">

---

### Step 5 — Create Project Directory and Virtual Environment

```bash
mkdir pythonapp
cd pythonapp
python3 -m venv myenv
ls myenv/bin/
```

---

### Step 6 — Activate the Virtual Environment

```bash
sudo bash myenv/bin/activate
```

---

### Step 7 — Install Project Dependencies

```bash
sudo pip install -r requirements.txt
```

> <img src="/Screenshots/Requirement Installation.jpeg" width="1000">

The `requirements.txt` includes:

```
click==8.0.3
colorama==0.4.4
Flask==2.0.2
itsdangerous==2.0.1
Jinja2==3.0.3
MarkupSafe==2.0.1
Werkzeug==2.0.2
gunicorn==20.1.0
setuptools>=3.0
```

---

### Step 8 — Run the Flask Application

```bash
python3 app.py
```

Or run with Gunicorn for production:

```bash
gunicorn -b 0.0.0.0:5000 app:app
```

---

## Accessing the Application

Once the application is running, open a browser and navigate to:

```
http://your-ec2-public-ip:5000
```

> <img src="/Screenshots/Output.jpeg" width="1000">

Replace `your-ec2-public-ip` with the actual public IP address of your EC2 instance.

---

## Project Outcomes

- Python Flask application deployed and running on AWS EC2
- Application accessible via EC2 public IP on port 5000
- Virtual environment created for isolated dependency management
- All dependencies installed using pip from `requirements.txt`
- Gunicorn configured as the production WSGI server
- Linux server configured and administered via SSH
- End-to-end cloud deployment completed successfully

---

## Key Learnings

- How to launch and configure an AWS EC2 instance
- How to connect to a remote Linux server using SSH
- How to install Python 3 and pip on Amazon Linux
- How to create and manage Python virtual environments
- How Flask applications run on a Linux environment
- How to use pip to install dependencies from `requirements.txt`
- How cloud servers, web frameworks, and WSGI servers work together

---

## Full Command Reference

```bash
# Update system
sudo yum update -y

# Install Python and pip
sudo yum install python3 -y
sudo yum install python3-pip -y
python3 --version
pip3 --version

# Create project directory
mkdir pythonapp
cd pythonapp

# Create and activate virtual environment
python3 -m venv myenv
ls myenv/bin/
sudo bash myenv/bin/activate

# Install dependencies
sudo pip install -r requirements.txt

# Run application
python3 app.py

# Run with Gunicorn (production)
gunicorn -b 0.0.0.0:5000 app:app
```

---

## Author

**Aryanraje Dhokale**  
Cloud and DevOps Learner
