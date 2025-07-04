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


##  AWS Services Used

 - **Amazon ECS (Fargate)** :  Container orchestration 
 - **Amazon ECR** : Docker image repository 
 - **AWS CodePipeline** : CI/CD orchestration 
 - **AWS CodeBuild** : Docker image build automation 
 - **Amazon CloudWatch** : Logging and monitoring 
 - **AWS IAM** : Access control for build and deployment roles 

---
## ECS Deployment
### Created Amazon ECR To Store my Images

![ECS DEPLOYMENT](/screenshots/Screenshots(3).png)


### Deployed containers on Amazon ECS (Fargate)

- Configured an ECS Cluster on Fargate.

- Managed ECS task definitions and revisions.

- Deployed the application containers using ECS Services and Load Balancers.

![ECS DEPLOYMENT](/screenshots/Screenshots(1).png)

![ECS DEPLOYMENT](/screenshots/Screenshots(2).png)
  
---

## CI/CD Setup

- Integrated CodePipeline with CodeBuild for CI/CD

- Configured CodePipeline to trigger on GitHub commits.

- Used CodeBuild to build Docker images and generate deployment artifacts.

- Implemented ECS deployments using imagedefinitions.json.

  ![CICD SETUP](/screenshots/Screenshots(5).png)

---



##  Pipeline Workflow

### Source Stage (GitHub)
- Monitors source repository for changes.
- Includes `Dockerfile`, `buildspec.yml`, and `index.html`.

  ### Key Files
| File | Purpose |
|------|---------|
| `Dockerfile` | Docker build instructions |
| `buildspec.yml` | CodeBuild build configuration |
| `imagedefinitions.json` | Image version information (generated in build) |
| `index.html` | Application code used in Dockerfile |

![Pipeline Workflow](/screenshots/Screenshots(12).png)

![Pipeline Workflow](/screenshots/Screenshots(11).png)

![Pipeline Workflow](/screenshots/Screenshots(10).png)


### Build Stage (CodeBuild)
- Builds Docker image from application source code.
- Tags image with commit-based version.
- Pushes image to Amazon ECR.
- Dynamically generates `imagedefinitions.json`.
- Packages `imagedefinitions.json` as build artifact.

![Pipeline Workflow](/screenshots/Screenshots(9).png)
  
![Pipeline Workflow](/screenshots/Screenshots(8).png)


### Deploy Stage 
- Uses `imagedefinitions.json` from build artifact.
- Registers new ECS task definition revision.
- Performs deployment updating the ECS service.

![Pipeline Workflow](/screenshots/Screenshots(6).png)

![Pipeline Workflow](/screenshots/Screenshots(7).png)

![Pipeline Workflow](/screenshots/Screenshots(4).png)

---

## Monitoring

- CloudWatch Logs configured for ECS container logs.
- CloudWatch metrics used to monitor ECS service health and deployment status.

![Monitoring](/screenshots/Screenshots(15).png)

![Monitoring](/screenshots/Screenshots(14).png)

![Monitoring](/screenshots/Screenshots(13).png)


---

## Outcome

- Achieved fully automated container deployments.
- Full build → deploy → monitor pipeline using fully managed AWS services.

---

