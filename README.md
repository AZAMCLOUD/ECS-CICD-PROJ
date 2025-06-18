# CI/CD Pipeline for Containerized Application on Amazon ECS (Fargate)

##  Project Overview

This project is using a fully automated Continuous Integration and Continuous Deployment (CI/CD) pipeline using AWS managed services. The pipeline builds, containerizes, and deploys a web application into Amazon ECS (Fargate), using CodePipeline, CodeBuild.

---

##  Project Objective

- Create a container image and pushed it to Amazon ECR.
- Deploy containers on Amazon ECS (Fargate).
- Integrate CodePipeline with CodeBuild for CI/CD.
- Use CloudWatch for logging and ECS task monitoring.



---

## 👤 My Role

- Built Docker container image for the application and pushed to Amazon ECR.
- Deployed containerized application on Amazon ECS (Fargate) with proper task definition and service configuration.
- Integrated CodePipeline, CodeBuild, and CodeDeploy to automate builds and deployments.
- Configured CloudWatch for container log monitoring and service health monitoring.

---

## 🧰 AWS Services Used

| AWS Service | Description |
|-------------|-------------|
| **Amazon ECS (Fargate)** | Container orchestration |
| **Amazon ECR** | Docker image repository |
| **AWS CodePipeline** | CI/CD orchestration |
| **AWS CodeBuild** | Docker image build automation |
| **AWS CodeDeploy** | Blue/Green deployment management |
| **Amazon CloudWatch** | Logging and monitoring |
| **AWS IAM** | Access control for build and deployment roles |

---

## 🔧 Pipeline Workflow

### Source Stage (GitHub)
- Monitors source repository for changes.
- Includes `Dockerfile`, `buildspec.yml`, and `appspec.yaml`.

### Build Stage (CodeBuild)
- Builds Docker image from application source code.
- Tags image with commit-based version.
- Pushes image to Amazon ECR.
- Dynamically generates `imagedefinitions.json`.
- Packages `imagedefinitions.json` and `appspec.yaml` as build artifact.

### Deploy Stage (CodeDeploy with ECS)
- Uses `imagedefinitions.json` and `appspec.yaml` from build artifact.
- Registers new ECS task definition revision.
- Performs Blue/Green deployment updating the ECS service.

---

## 📂 Key Files

| File | Purpose |
|------|---------|
| `Dockerfile` | Docker build instructions |
| `buildspec.yml` | CodeBuild build configuration |
| `imagedefinitions.json` | Image version information (generated in build) |
| `appspec.yaml` | CodeDeploy deployment configuration |

---

## 🔍 Monitoring

- CloudWatch Logs configured for ECS container logs.
- CloudWatch metrics used to monitor ECS service health and deployment status.

---

## 🚀 Outcome

- Achieved fully automated container deployments.
- Successfully implemented Blue/Green deployments ensuring zero downtime.
- Full build → deploy → monitor pipeline using fully managed AWS services.

---

