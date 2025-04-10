---
title: Refactoring Recall's Terraform code / Recall on the Cloud
date: "2025-04-10T18:12:03.284Z"
description: "How obtaining the Hashicorp Terraform Associate certification changed the way I look at my IaC."
---

Welcome to my blog.

Most of Recall's infrastructure is hosted on AWS: The front-end is deployed in S3 and is served via CloudFront, memories are
stored in DynamoDB tables, Cognito (with the help of Lambda) forms the backbone of authentication. Route 53 manages my domain
and Bedrock powers LLM integration. From a cloud perspective, this is definitely an AWS project.

# Why AWS?

In general, AWS, Azure and GCP offer very similar sets of features. Instead of S3, Azure has Blob Storage. Instead of
EKS, GCP has GKE _(which I'm quite jealous of)_. The fundamentals exist in all providers' ecosystems.

Where those cloud providers attract developers is with their cutting-edge services. When I started Recall, AWS offered the simplest
way of interacting with all major LLM models. Google's Vertex AI might have had an edge in training models, but Bedrock 
offered me a way of interacting with the latest Claude/GPT/Llama models in a simple, scalable, and infra-free way. The 
monthly price being based solely on tokens used also meant that my costs remained low and will scale linearly with users.
Not needing to pay for a server being available 24/7 provides significant cost advantages, especially before mass user
adoption. This serverless model scales better during peak usage times, where users shouldn't notice any added latency 
or drop in availability.

Also, my experience with Cognito has been fantastic. Cognito manages user pools, sign-ups (including SSO), 
logins, email confirmations, and even the layout of the sign-in page. It abstracts authentication to just token management, 
vastly simplifying what is usually a complicated and error-prone procedure. As far as I know, GCP and Azure don't offer 
anything quite as comprehensive, so this is a big plus for AWS.

Besides, my job at HSBC exposes me to GCP on a daily basis. I thought it'd be a fun and educational experience to
try something different.

# Deploying infrastructure

[//]: # (Talk about how you deploy most of your destroyable infrastructure with Terraform, and introduce the next
article, which will go over how you refactored your terraform after completing Terraform Associate)

# FinOps on a micro scale
[//]: # (Talk about building and destroying ECS/EKS to save money. Only have the backend running when necessary. Perhaps
leave for terraform article)