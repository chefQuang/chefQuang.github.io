---
title: "Backend Installation and Configuration"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.7.2 </b> "
---

#### Connect to the EC2 Instance

1. Open the **Amazon EC2** service.
2. Select the `local-aqi-dev-ec2-backend` instance.
3. Click **Connect**.
4. Select the **Session Manager** tab.
5. Click **Connect**.


Verify the Python version:

```bash
python3 --version
```

Install the required tools:

```bash
sudo dnf install -y python3-pip git rsync
```

#### Download the Source Code

Navigate to the EC2 user's home directory:

```bash
cd /home/ec2-user
```

Clone the repository:

```bash
git clone <REPOSITORY_URL> AWS-FCJ-local_aqi_forecast
cd AWS-FCJ-local_aqi_forecast
```

Run the bootstrap script to create the application directory and the `systemd` service:

```bash
sudo bash backend/deploy/ec2-user-data.sh
```

Synchronize the Backend source code to `/opt/local-aqi-backend`:

```bash
sudo rsync -a --delete \
  --exclude '.env' \
  --exclude '.venv' \
  backend/ /opt/local-aqi-backend/

sudo chown -R ec2-user:ec2-user /opt/local-aqi-backend
```

#### Install Dependencies

Navigate to the Backend directory:

```bash
cd /opt/local-aqi-backend
```

Create a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

#### Configure Environment Variables

Create the `.env` file:

```bash
cp .env.example .env
chmod 600 .env
```

Open the file:

```bash
nano .env
```

Update the file with the following content:

```dotenv
AWS_REGION=ap-southeast-1
SUBSCRIBERS_TABLE=local-aqi-subscribers-dev
ALERTS_TOPIC_ARN=arn:aws:sns:ap-southeast-1:ACCOUNT_ID:local-aqi-alerts-dev

SAGEMAKER_ENDPOINT_NAME=ENDPOINT_NAME
SAGEMAKER_CONTENT_TYPE=application/json
SAGEMAKER_TIMEOUT_SECONDS=5
SAGEMAKER_MAX_ATTEMPTS=3
FORECAST_HORIZON_HOURS=24

STATION_DATA_FILE=/opt/local-aqi-backend/runtime/stations.json
ALLOW_SAMPLE_STATION_DATA=false
ALERT_COOLDOWN_SECONDS=3600
```

Replace `ACCOUNT_ID` and `ENDPOINT_NAME` with the actual values.

Configure `SAGEMAKER_ENDPOINT_NAME` only after the endpoint reaches the `InService` state and the request/response format has been finalized with the ML team.

Do not store your AWS Access Key, Secret Access Key, or personal email address in the `.env` file.


#### Verify the Source Code

Run the test suite:

```bash
python -m unittest discover -s tests -v
```

Check the Python syntax:

```bash
python -m compileall -q app tests
```

Validate the OpenAPI specification:

```bash
python scripts/validate_openapi.py
```

If all commands complete successfully, proceed to the Backend startup step.