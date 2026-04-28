# ovia-ec2-instance-status-scheduler
# EC2 Instance Status Scheduler

## 📌 Overview

This project is a simple Python-based automation tool that periodically checks the status of Amazon EC2 instances using the AWS SDK for Python (`boto3`).

It uses the `schedule` library to run a recurring task every 5 minutes, printing the instance state along with system and instance health checks.

---

## ⚙️ Features

* Fetches EC2 instance status using AWS APIs
* Displays:

  * Instance ID
  * Instance state (running, stopped, etc.)
  * Instance status checks
  * System status checks
* Runs automatically every 5 minutes
* Lightweight and easy to extend

---

## 🛠️ Tech Stack

* Python 3.x
* boto3 (AWS SDK for Python)
* schedule (job scheduler)

---

## 📁 Project Structure

```
ec2-status-scheduler/
│── main.py
│── requirements.txt
│── README.md
```

---

## 🔧 Prerequisites

Before running this project, ensure you have:

* Python installed (>= 3.7)
* AWS account
* Configured AWS credentials

### Configure AWS Credentials

Run:

```bash
aws configure
```

Provide:

* AWS Access Key
* AWS Secret Key
* Default region (e.g., us-east-1)

---

## 📦 Installation

1. Clone the repository:

```bash
git clone https://github.com/your-username/ec2-status-scheduler.git
cd ec2-status-scheduler
```

2. Create a virtual environment (recommended):

```bash
python -m venv venv
source venv/bin/activate     # Linux/Mac
venv\Scripts\activate        # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 📜 requirements.txt

```txt
boto3
schedule
```

---

## ▶️ Usage

Run the script:

```bash
python main.py
```

The script will:

* Check EC2 instance statuses every 5 minutes
* Print results to the terminal

Example output:

```
Instance i-1234567890abcdef0 is running with instance status ok and system status ok
################################################
```

---

## 🔁 How It Works

* Uses `boto3.client("ec2")` to interact with AWS EC2
* Calls:

```python
describe_instance_status(IncludeAllInstances=True)
```

* Schedules execution using:

```python
schedule.every(5).minutes.do(check_instance_status)
```

* Runs continuously with:

```python
while True:
    schedule.run_pending()
```

---

## 🚀 Possible Enhancements

* Add logging instead of print statements
* Send alerts via email or Slack
* Store results in a database (DynamoDB, RDS)
* Convert into a cron job or systemd service
* Dockerize the application
* Integrate with monitoring tools like Prometheus

---

## ⚠️ Notes

* Ensure your IAM user/role has permission:

  * `ec2:DescribeInstanceStatus`
* Script runs indefinitely; stop with `CTRL + C`

---

## 📄 License

This project is open-source and available under the MIT License.

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## 👨‍💻 Author

Payce Nonoli
GitHub: https://github.com/paycenonoli
