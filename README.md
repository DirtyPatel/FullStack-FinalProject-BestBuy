## Project Overview

This is a cloud-ready microservices e-commerce prototype resembling a BestBuy-style store. The system comprises multiple containerized services, deployed to Azure AKS, showcasing backend APIs, frontend UI (store & admin), and a database layer.

I used AI to help me style and restructure the store-front repo and manually modified the product-service to display product BestBuy would typically sell. 

## Architecture

- Store-Front
    - A basic Vue.js app that lets customers see products, add them to a cart, and submit an order. When the order is submitted, it’s sent to the order-service and the cart clears. No checkout or customer info.

- Store-Admin
    - A simple Vue.js admin portal where products can be managed and orders can be viewed or processed. Works with the product-service and makeline-service.

- Order-Service
    - A Fastify API that receives orders from the store-front and sends them to a RabbitMQ queue (AMQP 1.0). Very simple order intake service.

- Product-Service
    - A Rust API that provides product data. Products are kept in memory, so they reset when the service restarts. Used by both store-front and store-admin.

- Makeline-Service
    - A Go service that reads orders from RabbitMQ, processes them, and stores them in MongoDB. Simulates a basic order processing “makeline.”

## Deployment

- Created an AKS cluster on Azure.

- Authenticate to Azure (e.g. via az login).

- Get AKS credentials (az aks get-credentials …).

- Apply Kubernetes manifests from the deployment folder:
kubectl apply -f <deployment-folder>

- Verify pods/services:
kubectl get pods, kubectl get services

## lINKS : 

- https://github.com/DirtyPatel/store-front-L8
- https://github.com/DirtyPatel/makeline-service-L8
- https://github.com/DirtyPatel/store-admin-L8 
- https://github.com/DirtyPatel/order-service-L8
- https://github.com/DirtyPatel/product-service-L8

## YOUTUBE 
https://youtu.be/KsTmmjAAzyI
