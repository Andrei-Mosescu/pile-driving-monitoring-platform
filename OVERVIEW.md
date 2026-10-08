# HeiToezicht - Pile Driving Project Management Platform

<div align="center">
  <img src="services/frontend/public/assets/logo.png" alt="HeiToezicht Logo" width="200"/>

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Node Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org)
[![Docker](https://img.shields.io/badge/docker-%3E%3D20.10-blue.svg)](https://www.docker.com/)
[![Terraform](https://img.shields.io/badge/terraform-%3E%3D1.0-purple.svg)](https://www.terraform.io/)
</div>

## 🏗️ Overview

HeiToezicht is a comprehensive web-based platform designed for managing pile driving construction projects. It provides real-time monitoring, incident tracking, and detailed reporting capabilities for construction teams and project managers.

### Key Features

- **📊 Real-time Project Dashboard** - Monitor project progress, KPIs, and daily productivity
- **🗺️ Interactive Pile Mapping** - Visual pile placement and status tracking with DXF file support
- **📱 IoT Sensor Integration** - Real-time data collection from acceleration and sound sensors
- **📸 Receipt & Document OCR** - Automatic text extraction from construction documents
- **🌤️ Weather Integration** - Real-time weather data for project locations
- **📈 Advanced Analytics** - Trend analysis, productivity charts, and progress predictions
- **📄 PDF Report Generation** - Automated daily and project reports
- **🌐 Multi-language Support** - Dutch and English interfaces
- **🔒 Role-based Access Control** - Secure user management with granular permissions

## 🛠️ Technology Stack

### Frontend
- **React 19** with functional components and hooks
- **Material-UI v7** for modern UI components
- **Socket.io** for real-time updates
- **React Router v7** for navigation
- **i18next** for internationalization
- **Recharts** for data visualization
- **jsPDF** for PDF generation

### Backend Services
- **Node.js** with Express.js
- **PostgreSQL** database
- **Socket.io** for WebSocket connections
- **JWT** authentication
- **OpenAI API** integration for OCR
- **Tesseract.js** for offline OCR

### Infrastructure
- **Docker** containers with multi-stage builds
- **Docker Compose** for orchestration
- **Terraform** for infrastructure as code
- **Traefik** reverse proxy
- **GitHub Actions** for CI/CD

## 📋 Prerequisites

- Node.js >= 18.0.0
- Docker >= 20.10
- Docker Compose >= 2.0
- Terraform >= 1.0 (for deployment)
- PostgreSQL >= 14

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/your-org/heitoezicht.git
cd heitoezicht
```

### 2. Environment Setup

Create the asked files in the env folder. There are some templates that need to be copied, remove the .template part and fill the keys.

### 3. Install Dependencies

```bash
# Install root dependencies
npm install

# Install service dependencies
cd services/frontend && npm install
cd ../query-core && npm install
cd ../data-processing && npm install
cd ../service-login && npm install
```

### 4. Development Mode

```bash
# Using Docker Compose (recommended)
docker compose --profile dev up
```

### 5. Production Mode

```bash
# Using Terraform (recommended)
cd deployment &&  terraform apply -auto-approve -var="frontend_env=prod" -var="expected_origin=https://portal.heitoezicht.net" -var="expected_rpid=portal.heitoezicht.net"
```

### 6. Database Setup - Only first time running for initializing the database

```bash
# Start PostgreSQL container
docker exec -it database bash
cd init && ./re_init.sh
```

The application will be available at:
- Frontend: http://localhost:3000

## 🏗️ Architecture

```
heitoezicht/
├── services/
│   ├── frontend/          # React application
│   ├── query-core/        # Main API service
│   ├── data-processing/   # File processing & OCR
│   └── service-login/     # Authentication service
├── shared/                # Shared utilities
├── deployment/           # Terraform configurations
├── docker/              # Docker configurations
├── hardware/            # IoT sensor code (Arduino)
└── docs/                # Documentation
```

## 📱 Features Documentation

### Pile Management
- Create and configure piles with type, subtype, and code
- Track pile status: planned → configured → in_progress → completed/failed
- Real-time status updates via WebSocket
- Batch operations for multiple piles

### Interactive Pile Map
- Import DXF drawings as base maps
- Drag-and-drop pile positioning
- Multi-select editing capabilities
- Background image overlay with scaling controls
- Real-time synchronization across users

### Sensor Integration
- WiFi-based acceleration sensors for pile driving monitoring
- Sound level monitoring during operations
- Real-time data visualization
- Historical data analysis

### Document Processing
- Receipt OCR with automatic field extraction
- Support for multiple languages (Dutch/English)
- Batch document upload
- GPT-4 powered intelligent extraction

### Reporting System
- Daily productivity reports
- Project progress summaries
- Incident tracking and reporting
- Automated PDF generation with charts

## 🧪 Testing

### Running Tests

```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run specific service tests
cd services/frontend && npm test
cd services/query-core && npm test
```

### Test Structure
- Unit tests for components and utilities
- Integration tests for API endpoints
- E2E tests for critical user flows
- WebSocket connection tests

## 🚀 Deployment

### Terraform Deployment

```bash
# Initialize Terraform
cd deployment
terraform init

# Plan deployment
terraform plan -var="frontend_env=prod" \
              -var="expected_origin=https://portal.heitoezicht.net" \
              -var="expected_rpid=portal.heitoezicht.net"

# Apply deployment
terraform apply -var="frontend_env=prod" \
               -var="expected_origin=https://portal.heitoezicht.net" \
               -var="expected_rpid=portal.heitoezicht.net"
```

## 🔧 Configuration

### ESLint Setup

```bash
# Install ESLint and plugins
npm install --save-dev eslint @eslint/eslintrc @eslint/js globals \
  eslint-plugin-react eslint-plugin-jsx-a11y

# Run linting
npm run lint
```

### Database Configuration

The application uses PostgreSQL with the following main tables:
- `users` - User authentication and profiles
- `projects` - Project information
- `piles` - Individual pile data
- `pile_tochten` - Pile driving sessions
- `incidents` - Project incidents
- `daily_records` - Daily productivity records
- `files` - Uploaded files and documents

## 🐛 Troubleshooting

### Common Issues

1. **Port conflicts**
   ```bash
   # Check if ports are in use
   lsof -i :3000
   ```

2. **Database connection issues**
   ```bash
   # Check PostgreSQL container
   docker compose ps database
   docker compose logs database
   ```

3. **WebSocket connection failures**
    - Ensure CORS is properly configured
    - Check firewall rules for WebSocket ports
    - Verify Socket.io client/server versions match

### Code Style
- Use ESLint configuration
- Follow React best practices
- Write tests for new features
- Update documentation
