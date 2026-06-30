# Day 08 – AWS Lambda (Manual Trigger)

## CloudBridge Startup Simulation

**Project:** CloudBridge | **Service:** AWS Lambda | **Region:** ap-south-1 (Mumbai)

---

## What I Built

Deployed a serverless function for the CloudBridge startup that runs Python code in the cloud — no server required. The function returns a JSON response confirming the service is live, and logs every execution automatically to CloudWatch.

---

## Architecture

```
[Manual Test Event]
        │
        ▼
  AWS Lambda Function
  (cloudbridge-hello-function2)
  Runtime: Python 3.12
        │
        ▼
  JSON Response (statusCode 200)
        │
        ▼
  CloudWatch Logs (auto-generated)
```

---

## AWS Services Used

| Service | Purpose |
|---|---|
| AWS Lambda | Runs Python code without provisioning a server |
| CloudWatch Logs | Captures execution logs automatically |
| IAM | Execution role granting Lambda permission to write logs |

---

## What I Did (Step by Step)

1. Navigated to AWS Lambda → Created new function `cloudbridge-hello-function2`
2. Selected **Python 3.12** runtime
3. Wrote the function code in the inline editor (`lambda_function.py`)
4. Deployed the code
5. Created a test event and invoked the function manually
6. Verified the JSON response (statusCode 200)
7. Checked CloudWatch Logs to confirm execution was captured

---

## Lambda Function Code

```python
import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": json.dumps({
            "message": "Hello from CloudBridge!",
            "project": "CloudBridge Startup Simulation",
            "service": "AWS Lambda"
        })
    }
```

---

## Test Result

```json
{
  "statusCode": 200,
  "body": "{\"message\": \"Hello from CloudBridge!\", \"project\": \"CloudBridge Startup Simulation\", \"service\": \"AWS Lambda\"}"
}
```

| Metric | Value |
|---|---|
| Status | ✅ Success |
| Duration | 1.52 ms |
| Billed Duration | 66 ms |
| Memory Configured | 128 MB |
| Max Memory Used | 36 MB |
| Init Duration (cold start) | 63.62 ms |
| Runtime | Python 3.12 |

---

## CloudWatch Logs

Execution was automatically logged to `/aws/lambda/cloudbridge-hello-function2`.

Log events captured:
- `INIT_START` — cold start, runtime initialised
- `START` — function invocation began
- `END` — function completed
- `REPORT` — duration, billed time, and memory usage summary

---

## Key Concepts Learned

**Serverless computing** — Lambda runs code without managing any servers. AWS handles provisioning, scaling, and availability automatically.

**Cold start** — The first invocation initialises the runtime environment (Init Duration: 63.62 ms). Subsequent calls are faster as the environment stays warm.

**Event-driven execution** — Lambda functions are triggered by events (manual test here; S3, API Gateway, or other services in production).

**Automatic logging** — Every Lambda execution writes logs to CloudWatch without any configuration needed.

**Billed duration vs actual duration** — AWS rounds up to the nearest 1ms for billing. Actual execution was 1.52 ms; billed was 66 ms due to cold start overhead being included.

---

## IAM Configuration

Lambda used an auto-created **execution role** with the `AWSLambdaBasicExecutionRole` managed policy, which grants permission to write logs to CloudWatch.

---

## Function Details

| Parameter | Value |
|---|---|
| Function Name | cloudbridge-hello-function2 |
| Runtime | Python 3.12 |
| Region | ap-south-1 (Mumbai) |
| ARN | arn:aws:lambda:ap-south-1:502309351126:function:cloudbridge-hello-function2 |
| Memory | 128 MB |
| Trigger | Manual (test event) |

---

## Screenshots

| Screenshot | Description |
|---|---|
| `01-function-created.png` | Lambda function successfully created |
| `02-code-deployed.png` | Python code written and deployed |
| `03-function-overview.png` | Function overview after deployment |
| `04-test-success.png` | Test execution result — statusCode 200 |
| `05-cloudwatch-loggroup.png` | CloudWatch log group created automatically |
| `06-cloudwatch-logevents.png` | Log events: INIT_START, START, END, REPORT |

---
