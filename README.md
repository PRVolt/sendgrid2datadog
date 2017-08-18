# SendGrid2Datadog

[![Build Status](https://travis-ci.org/dtan4/sendgrid2datadog.svg?branch=master)](https://travis-ci.org/dtan4/sendgrid2datadog)
[![Docker Repository on Quay](https://quay.io/repository/dtan4/sendgrid2datadog/status "Docker Repository on Quay")](https://quay.io/repository/dtan4/sendgrid2datadog)

Send SendGrid metrics to Datadog

![sendgrid2datadog](images/sendgrid2datadog.png)

```
+----------+
|          |
| SendGrid |
|          |
+----------+
     |
     | Event Notification
     |
+====|================================+
|    |     SendGrid2Datadog           |
|    v                                |
| +------------+        +-----------+ |           +---------+
| |            |        |           | |           |         |
| | API Server | -----> | DogStatsD |-----------> | DataDog |
| |            |        |           | |           |         |
| +------------+        +-----------+ |           +---------+
|                                     |
+=====================================+
```

## Install

### Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

### Kubernetes

```bash
kubectl create -f kubernetes/namespace.yaml
kubectl create -f kubernetes/service.yaml

# Use envFrom (>= k8s 1.6)
kubectl create -f kubernetes/deployment-envFrom.yaml

# or else
kubectl create -f kubernetes/deployment.yaml
```

## Environment variables

|Key|Kubernetes Secret name|Description|Required|
|---|---|---|
|`BASIC_AUTH_USERNAME`|`sendgrid2datadog`|basic auth username||
|`BASIC_AUTH_USERNAME`|`sendgrid2datadog`|basic auth password||
|`DATADOG_API_KEY`|`dd-agent`|Datadog API key|Required|

If both `BASIC_AUTH_USERNAME` and `BASIC_AUTH_PASSWORD` are provided, basic auth will be enabled.

## License

[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)
