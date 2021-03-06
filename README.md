Table of Contents
=================

  * [Resource](#resource)
    * [Resource Plan](#resource-plan)
    * [Resource Story](#resource-story)
    * [Resource Diagram](#resource-diagram)
    * [HOW TO DEPLOY ON GOOGLE CLOUD](#HOW-TO-DEPLOY-ON-GOOGLE-CLOUD)
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

How we doploy flask rest api to Google Cloud Platform ?

We prefer to use GCP Console UI instead of command line/shell

We will use Cloud Build connected with github repostiory containing
our rest api source code to make a docker container by **Dockerfile** which it
will automatically submited to google cloud **image registry**.

For data source, we will upload model that have been trained by our ML Team to **Cloud Storage**, 
then for SQL Database, we will use Cloud SQL with MySQL 8 newest version

Finally we can create new Cloud Run service with connection to Cloud SQL through `unix_socket`, 
then in our source code we will add some feature to predict through model that was uploaded before
fortunately python can make call to `gs://` filesystem with gcs module


## Resource Diagram
![Diagram](https://raw.githubusercontent.com/C22-PS119/api-true-sight/main/GCP.png)

## HOW TO DEPLOY ON GOOGLE CLOUD
Good News! It's all just an easy step 😉

1. Clone or download [Our Flask API](https://github.com/wahyusa/flask_true_sight) repository
2. Login and use Google Cloud Console UI
3. Search for Cloud Build service and enable the Cloud Build API in case you missed it
4. Connect the clonned repo with Cloud Build
5. Now we can move to Cloud SQL Service
6. Create new Cloud SQL Instance it should be easy
7. Then we move to Cloud Run service, nake sure you enable the API (you will aksed to enable it)
8. Create new Cloud Run Instance
9. There is an option, choose **continuos integration** from cloud build
10. In Connection tab, **DON'T FORGET to connect** with SQL Instance that we've created earlier
11. Wait for build and deploy process
12. Voila! it should have URL like `https://xxxx.run.app`

# Organization Setup

## General
1. Organization name => C22-PS119
2. Project name => TRUE SIGHT
3. Project ID => advance-branch-351506
4. Prefered zone/region => US Lowcost/Asia/Jakarta/Singapore

## Billing Cost
We estimate based on GCP calculator

[See our GCP Calculator details](https://cloud.google.com/products/calculator/#id=98cce779-e7d3-4d5b-b340-d9c99eb8fe9c)

- Cloud Build - https://cloud.google.com/build/pricing
- Cloud Storage $0.23 / GB object
- Cloud SQL $66
- Cloud Run $0

Why cloud run price is $0 ??
=> https://cloud.google.com/run/pricing#billable_time

Some of this service have [free tier starter](https://cloud.google.com/free/docs/gcp-free-tier#free-tier-usage-limits)

```
TLDR
First 120 builds-minutes per day are free

If API/web traffic is not exceed specific amount we won't charged, that's why we choose cloud run

Why cloud SQL have highest cost ??
=> Of course it run 24/7
```


Total cost $66.55 / month

Total cost Rp959,217.58 / month

GCP Bangkit credit is $250 we can keep all service running around 3 month++

   > You may see our cost and usage is always $0 and got lot of discount/promotion but actually it use the bangkit credit.
   > So it can be cost $0 but bangkit credit usage is still running. 
   > To view the full information about billing you should use the 1 account that was [redeemed education token](https://cloud.google.com/edu)

## Role IAM
We think everyone can join in this GCP and explore all things here with owner role, we can invite everyone with team email addresses

# API Development
[Flask REST Service Repository](https://github.com/C22-PS119/flask_true_sight)

# References

Free Tier Limit - https://cloud.google.com/free/docs/gcp-free-tier#free-tier-usage-limits

GCP Calculator - https://cloud.google.com/products/calculator

How to connect SQL From Cloud Run - https://cloud.google.com/sql/docs/mysql/connect-run

GCP Edu program - https://cloud.google.com/edu

