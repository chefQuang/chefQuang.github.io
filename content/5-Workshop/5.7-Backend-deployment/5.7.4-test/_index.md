---
title: "Test the API and Alert Scheduling"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.7.4 </b> "
---

#### Test the Backend from Your Local Machine

Retrieve the current public IPv4 address of the EC2 instance. Note that this address may change if the instance is stopped and started again.

Create the `BASE_URL` variable:

```bash
BASE_URL=http://<PUBLIC_IP>:8000
```

Test the health endpoint:

```bash
curl -i "$BASE_URL/health"
```

Open the Swagger UI:

```text
http://<PUBLIC_IP>:8000/docs
```

<!-- Add screenshot: Swagger UI -->

#### Test the Forecast API

Call the API:

```bash
curl -i "$BASE_URL/forecast/station-01"
```

When the SageMaker endpoint and station data are configured correctly, the API returns:

- Source data timestamp
- Forecast timestamp
- Forecast horizon
- Predicted PM2.5 value
- AQI value

If the SageMaker endpoint or source data is not configured, the API returns HTTP `503` instead of generating mock forecast data.

<!-- Add screenshot: Forecast API response -->

#### Test Alert Subscription

Send a subscription request:

```bash
curl -i -X POST "$BASE_URL/subscribe/" \
  -H 'Content-Type: application/json' \
  -d '{
    "email": "APPROVED_TEST_EMAIL",
    "station_id": "station-01",
    "threshold_aqi": 150
  }'
```

Amazon SNS sends a confirmation email. Open the email and click **Confirm subscription**.

Use only email addresses for which you have permission to receive notifications. Do not include real email addresses in the repository, logs, or screenshots.

<!-- Add screenshot: Subscription status with email address masked -->

#### Test Alert Delivery

Submit a PM2.5 value:

```bash
curl -i -X POST "$BASE_URL/alert/" \
  -H 'Content-Type: application/json' \
  -d '{
    "station_id": "station-01",
    "pm25": 55.4
  }'
```

The Backend performs the following steps:

1. Converts the PM2.5 value to an AQI value.
2. Finds confirmed subscribers.
3. Checks the configured alert threshold.
4. Verifies the cooldown period.
5. Publishes a notification to Amazon SNS if all conditions are met.

<!-- Add screenshot: Alert email with recipient address masked -->

#### Configure Automatic Scheduling

Enable the timer only after verifying the SageMaker endpoint, station data, and IAM permissions.

Install the service and timer:

```bash
cd /opt/local-aqi-backend

sudo install -m 0644 deploy/local-aqi-forecast-cycle.service \
  /etc/systemd/system/

sudo install -m 0644 deploy/local-aqi-forecast-cycle.timer \
  /etc/systemd/system/

sudo systemctl daemon-reload
sudo systemctl enable --now local-aqi-forecast-cycle.timer
```

Check the schedule:

```bash
sudo systemctl list-timers local-aqi-forecast-cycle.timer
sudo systemctl status local-aqi-forecast-cycle.timer --no-pager
```

View the most recent execution:

```bash
sudo systemctl status local-aqi-forecast-cycle.service --no-pager
sudo journalctl -u local-aqi-forecast-cycle.service -n 100 --no-pager
```

<!-- Add screenshot: systemd timer and latest execution -->

#### Completion

You have successfully:

- Deployed the FastAPI Backend on Amazon EC2.
- Granted the Backend access to DynamoDB, SageMaker, and Amazon SNS using an IAM role.
- Started the application using `systemd`.
- Tested the health, forecast, subscribe, and alert APIs.
- Configured automatic forecasting and alert scheduling.

When the demo is no longer needed, stop the EC2 instance and the SageMaker endpoint to minimize AWS costs.