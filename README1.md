# Pile Driving Monitoring Platform (Industry Project)

Industry software engineering project developed for  
**Van Dijk Heitoezicht & Funderingsexpertise BV**.

⚠️ The source code cannot be published due to a non-disclosure agreement (NDA).  
This repository contains a high-level overview of the system and the full project report.

---

# Overview

Construction site supervision still relies heavily on manual data collection and fragmented documentation.  
This project aimed to digitize and automate the monitoring of pile-driving operations by building a scalable, real-time monitoring platform.

The system integrates sensor data, document processing, and live dashboards to improve data reliability, accessibility, and decision-making.

---

# My Role

Part of a 5-student development team working with a real industry client.

Main contributions included:
- Backend & system design decisions
- Data processing and architecture discussions
- Integration of multiple services and APIs
- Testing and deployment workflow
- Sensor data integration

---

# System Highlights

## Real-time monitoring dashboard
Live WebSocket dashboards provide updates on:
- Hammer blows and pile progress
- Incident tracking
- Project status and analytics

## OCR document processing
Automated extraction of delivery notes and receipts using:
- Image preprocessing
- Tesseract OCR
- Configurable parsing pipeline

## CAD / DWG pile plan parsing
Automatic extraction of pile IDs, coordinates and types from engineering drawings.

## Sensor data integration
Proof-of-concept integration with ESP32 sensors to detect pile hits and vibrations.

## Automated report generation
Generation of structured PDF reports summarizing daily site activity.

---

# Architecture

The platform follows a **microservices architecture**:

- React frontend
- Node.js backend services
- PostgreSQL database
- Docker containerization
- Terraform infrastructure provisioning

The system supports real-time updates, horizontal scaling and zero-downtime deployment.

---

# Tech Stack

- React
- Node.js / Express
- PostgreSQL
- Docker
- Terraform
- WebSockets
- Tesseract OCR
- ESP32 sensor integration

---

# Report

Full project documentation:
`report/Pile_Driving_Monitoring_System.pdf`

---

# Note

Due to confidentiality agreements, the source code cannot be shared publicly.  
This repository serves as a portfolio showcase of the system design and engineering process.
