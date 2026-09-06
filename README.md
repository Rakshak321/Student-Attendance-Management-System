# Student Attendance Management System

A full-stack Student Attendance Management System built using the MERN stack and deployed using modern DevOps practices.

## 🚀 Project Overview

The Student Attendance Management System is a web-based application that helps manage students, teachers, classes, subjects, examinations, and attendance records.

The application consists of a React frontend and Node.js/Express backend connected with MongoDB.

The project is containerized using Docker and deployed on Kubernetes. Jenkins is used to automate the CI/CD pipeline.

## 🛠️ Technology Stack

### Application
- React.js
- Node.js
- Express.js
- MongoDB
- Mongoose

### DevOps
- Git & GitHub
- Docker
- Docker Compose
- Docker Hub
- Kubernetes
- Jenkins
- CI/CD

## 🏗️ Architecture

```text
                    GitHub
                       |
                       v
                    Jenkins
                       |
              +--------+--------+
              |                 |
        Frontend Build    Backend Build
              |                 |
              +--------+--------+
                       |
                       v
                 Docker Build
                       |
                       v
                  Docker Hub
                       |
                       v
                 Kubernetes
                /          \
               /            \
        Frontend Service   Backend Service
             |             /    |    \
          Frontend Pod   Pod    Pod    Pod
                              |
                              v
                           MongoDB