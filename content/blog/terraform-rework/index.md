---
title: Reworking my Infrastructure as Code
date: "2025-08-02T14:13:03.284Z"
description: "A story of how I'm using Terraform to deploy Recall's infrastructure and cut costs."
---

Welcome to my blog.

# Deploying Infrastructure

As I discussed in my [previous article](https://blog.kug.la/recall-on-the-cloud/), Recall is a cloud-native project,
hosted on AWS. Arguably the simplest way to deploy resources on any Cloud is by using their online console.
With that, we can deploy our storage, compute, or networks with just a few clicks. 

This may be the right solution for a small project, where we don't need to manage complex cloud resources. Many years ago 
I wanted to build an "Internet of Things"-eqsue solution that would give me data about the environment in my house directly
on my phone. I bought an [Enviro sensor](https://learn.pimoroni.com/article/getting-started-with-enviro-plus) for monitoring
temperature, pressure, humidity and light level, and got it connected to my Raspberry Pi. It wasn't difficult to get a script
running that took a snapshot of the data every few seconds, but I needed to find a way to get that data off of my Raspberry Pi
and deliver it to my phone in real time.

It turns out that GCP's Firebase had the perfect solution for that -- and a simple one, too. I used Cloud Functions to
expose an HTTPS endpoint through which data could be sent, verify the data's integrity, and store the data in Firestore 
(this is Firebase's noSQL database solution).

It only took two resources to get my IoT project off the ground. Something this simple can plausibly be deployed without
any infrastructure as code (though even this is not always optimal, as we'll discuss later).



I coded an IoT solution that ran a service on Raspberry Pis to collect environment data 
(temperature, pressure, humidity and light level) every few seconds. I needed to store that data somewhere from where I could
later download it onto my phone and display it in my mobile app. At the time, I used Cloud Functions to expose
an HTTPS endpoint, verify the data integrity, and store the data in Firestore (Firebase's noSQL database).

As an example,
think of a simple data logger for an IoT device. All it may need is an API Gateway to provide a public HTTPS endpoint for
sending data, a quick Lambda function for processing and saving the data, and a DynamoDB table to save the data in. It's a
genuinely useful cloud application that only really utilises 3 resources.

# Deploying infrastructure

[//]: # (Talk about how you deploy most of your destroyable infrastructure with Terraform, and introduce the next
article, which will go over how you refactored your terraform after completing Terraform Associate)

# FinOps on a micro scale
[//]: # (Talk about building and destroying ECS/EKS to save money. Only have the backend running when necessary. Perhaps
leave for terraform article)