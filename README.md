Project Charter: The Fortress Pipeline 

Title: Automated DevSecOps Pipeline & Cloud-Native SOC Integration
Version: 1.0
Authors: BOUZIENE Nacef
Objective: End-to-End Secure Software Delivery and Runtime Monitoring

1. Executive Summary
The goal of this project is to build a high-performance DevSecOps Lifecycle and a Security Operations Center (SOC). It focuses on the "Shift-Left" security philosophy, ensuring that security is integrated into the development process from the first line of code until it runs on a Kubernetes (Minikube) cluster. The project uses Wazuh for threat detection and n8n for automated incident response.

2. Technical Architecture & Infrastructure:




2.2 Software Stack

Orchestration: Jenkins (CI/CD)

Containerization: Docker & Kubernetes (Minikube)

Security Scanners: Gitleaks, SonarQube, Trivy

SIEM/XDR: Wazuh Manager & Wazuh Agent

Automation/SOAR: n8n

Monitoring Extensions: Falco (Runtime Security)

3. Functional Requirements (The Pipeline):

The system must successfully execute the following stages in order:
Code Commit: Trigger Jenkins job on GitHub push event.
Secret Scanning: Execute Gitleaks to detect hardcoded credentials. If secrets are found, fail the build.
Static Analysis (SAST): Run SonarQube to scan for vulnerabilities (SQLi, XSS) and Code Quality.
Container Security: Build Docker image and scan with Trivy. Block push to Registry if CRITICAL vulnerabilities exist.
Deployment: Deploy the secure image to Minikube using Kubernetes Manifests.

4. Security Operations (The SOC):

The project must provide real-time visibility and response:

Log Collection: Wazuh Agent must collect system and container logs from VM 2.

Threat Detection: Detect unauthorized access, brute force attacks, or suspicious commands inside containers.

SOAR Workflow: * Wazuh detects a threat.

n8n receives the alert via Webhook.

n8n sends a notification to Slack/Telegram and triggers a defensive action (e.g., isolating a pod).

5. Project Roadmap & Milestones:

Milestone 1: Infrastructure setup (VMware, Networking, and Docker installation).

Milestone 2: Development of the CI/CD Pipeline with Security Gates (Jenkinsfile).

Milestone 3: Kubernetes Cluster (Minikube) configuration and Deployment.

Milestone 4: SIEM Integration (Wazuh Manager/Agent) and Falco rules.

Milestone 5: Automation of Incident Response (n8n Workflows) and Final Documentation.


