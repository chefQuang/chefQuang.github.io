---
title: "Run the Backend with systemd"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.7.3 </b> "
---

#### Verify the Service

The bootstrap script creates the following service file:

```text
/etc/systemd/system/local-aqi-backend.service
```

View the service configuration:

```bash
sudo systemctl cat local-aqi-backend
```

The service should use the following configuration:

```ini
[Unit]
Description=Local AQI FastAPI backend
After=network-online.target
Wants=network-online.target

[Service]
Type=simple
User=ec2-user
Group=ec2-user
WorkingDirectory=/opt/local-aqi-backend
EnvironmentFile=-/opt/local-aqi-backend/.env
ExecStart=/opt/local-aqi-backend/.venv/bin/uvicorn app.main:app --host 0.0.0.0 --port 8000
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

#### Start the Backend

Reload the `systemd` configuration:

```bash
sudo systemctl daemon-reload
```

Enable the service to start automatically when the EC2 instance boots:

```bash
sudo systemctl enable local-aqi-backend
```

Start the service:

```bash
sudo systemctl start local-aqi-backend
```

Check the service status:

```bash
sudo systemctl status local-aqi-backend --no-pager
```

Expected output:

```text
Active: active (running)
```


#### Check the Logs

Display the last 100 log entries:

```bash
sudo journalctl -u local-aqi-backend -n 100 --no-pager
```

Follow the logs in real time:

```bash
sudo journalctl -u local-aqi-backend -f
```

The logs should not contain email addresses, credentials, access keys, or other sensitive payloads.

#### Test the Health Endpoint

Call the API directly from the EC2 instance:

```bash
curl -i http://127.0.0.1:8000/health
```

Expected response:

```text
HTTP/1.1 200 OK
```

```json
{"status":"ok"}
```

If the API is not running, verify the following:

```bash
sudo systemctl status local-aqi-backend --no-pager
sudo journalctl -u local-aqi-backend -n 100 --no-pager
sudo ss -lntp | grep 8000
```