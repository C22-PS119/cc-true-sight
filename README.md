Table of Contents
=================

  * [Resource](#resource)
    * [Resource Plan](#resource-plan)
    * [Resource Story](#resource-story)
    * [Resource Diagram](#resource-diagram)
  * [Organization Setup](#organization-setup)
    * [General](#general)
    * [Billing Cost](#billing-cost)
    * [Role IAM](#role-iam)
  * [API Development](#api-development)
  * [References](#references)

# Resource

## Resource Plan
- Cloud Build
- Cloud Storage
- Cloud Run
- Cloud SQL

## Resource Story
```bash
inside Cloud Storage upload machine learning model

then

inside Cloud SQL import MySQL Structure and initial data

then

from Cloud Run load model from Cloud Storage, connect to Cloud SQL, serve REST API, do predict request
```

## Resource Diagram
![Diagram](https://raw.githubusercontent.com/C22-PS119/api-true-sight/main/GCP.png)

# Organization Setup

## General
1. Organization name => C22-PS119
2. Project name => TRUE SIGHT
3. Project ID => advance-branch-351506
4. Prefered location => US Lowcost/Asia/Jakarta/Singapore

## Billing Cost
We estimate based on GCP calculator

[See our GCP Calculator details](https://cloud.google.com/products/calculator/#id=98cce779-e7d3-4d5b-b340-d9c99eb8fe9c)

- Cloud Build
- Cloud Storage $0.23
- Cloud SQL $66
- Cloud Run $0

Why cloud run price is $0 ??
=> https://cloud.google.com/run/pricing#billable_time

Some of this service have [free tier starter](https://cloud.google.com/free/docs/gcp-free-tier#free-tier-usage-limits)

```
TLDR
Cloud Build free 120hour build time/month we think is enough since it only used when pushing new container/revision

If API/web traffic is not exceed specific amount we won't charged, that's why we choose cloud run

Why cloud SQL have highest cost ??
=> Of course it run 24/7
```


Total cost $66.55 / month

Total cost Rp959,217.58 / month

GCP Bangkit credit is $250 we can keep all service running around 3 month++

## Role IAM
We think everyone can join in this GCP and explore all things here with owner role, we can invite everyone with team email addresses

# API Development
[Flask REST Service Repository](https://github.com/C22-PS119/flask_true_sight)

# References

Free Tier Limit - https://cloud.google.com/free/docs/gcp-free-tier#free-tier-usage-limits

GCP Calculator - https://cloud.google.com/products/calculator

