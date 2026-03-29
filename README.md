# Static FacebookApp


Project Overview


This project demonstrates a complete CI/CD pipeline setup for deploying a Static Facebook Application, integrating modern tools like Jenkins, SonarQube, Nexus, Docker, Kubernetes (EKS), and Prometheus for monitoring. This repository showcases the automation of code quality checks, artifact management, application deployment, and monitoring in a production-like environment.

Key Technologies & Tools
Jenkins: Continuous Integration and Continuous Deployment.
SonarQube: Static code analysis for quality and security checks.
Nexus: Artifact repository manager.
Docker: Containerization of the application.
Kubernetes (EKS): Orchestration of containerized applications.
Prometheus & Grafana: Monitoring and visualization of application performance.
Blackbox Exporter: Probing application availability and uptime monitoring.
Objectives
Automate the CI/CD pipeline: Automate building, testing, and deploying the blogging app.
Enhance code quality and security: Use SonarQube for static code analysis and Trivy for vulnerability scans.
Deploy to Kubernetes (EKS): Use Terraform to deploy and manage Kubernetes infrastructure on AWS.
Monitor the application: Use Prometheus, Blackbox Exporter, and Grafana for real-time monitoring and alerting.
Repository Structure
/ci-scripts: Shell scripts for installing Jenkins, Docker, Prometheus, Grafana, and Blackbox Exporter.
/kubernetes: Kubernetes manifests for deploying the app and setting up roles and access.
/terraform: Infrastructure as Code (IaC) files to provision an EKS cluster.
/src: The source code and Dockerfile for the SocialMedia application.
CI/CD Pipeline Overview
GitHub Integration: Jenkins pulls the latest changes from the GitHub repository and triggers the pipeline.
Build & Test:
The code is compiled and built using Maven.
Code analysis is done using SonarQube.
Trivy scans for vulnerabilities.
Docker & Nexus:
Jenkins builds a Docker image for the application.
Artifacts are pushed to Nexus.
Kubernetes Deployment:
The app is deployed to an EKS cluster.
Kubernetes handles scaling and service management.
Monitoring:
Prometheus scrapes metrics from the Blackbox Exporter.
Grafana visualizes application uptime, health, and other critical metrics.
Steps to Reproduce the Project
1. Clone the Repository
git clone https://github.com/LokeshPonthala/FacebookApp.git

cd FacebookApp

######## I used an Existing Static FB app and Implemented a complete CI/CD Pipeline ########

<img width="1882" height="913" alt="Screenshot 2026-29-03 104349" src="https://github.com/user-attachments/assets/6ab2da86-c985-4b74-8629-7e240567c884" />

