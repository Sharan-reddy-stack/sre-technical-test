# SRE Technical Test - Rails Monitoring Stack

A production-ready monitoring stack for a Rails application with PostgreSQL and Redis, demonstrating enterprise-level SRE practices.

## Overview

This project implements a comprehensive observability stack including metrics collection, monitoring dashboards, and alerting for a Rails application. The solution demonstrates infrastructure automation, service reliability engineering best practices, and production-ready monitoring.

## Architecture

### Application Stack
- **Rails Application**: Hello World application with custom Prometheus metrics endpoint
- **PostgreSQL Database**: Primary data store with connection monitoring
- **Redis Cache**: Caching layer with connectivity health checks

### Monitoring Stack
- **Prometheus**: Metrics collection and storage with alerting rules
- **Grafana**: Visualization dashboards and monitoring panels
- **Alertmanager**: Alert routing and notification management
- **Node Exporter**: System-level metrics collection
- **PostgreSQL Exporter**: Database-specific metrics
- **Redis Exporter**: Cache-specific metrics

## Quick Start

### Prerequisites
- Docker and Docker Compose installed
- Ports 3000, 3001, 9090, 9093 available

### Deploy the Stack

chmod +x provision.sh
./provision.sh deploy

Access URLs

Rails Application: http://localhost:3000
Grafana Dashboard: http://localhost:3001 (admin/admin)
Prometheus UI: http://localhost:9090
Alertmanager: http://localhost:9093
Health Check API: http://localhost:3000/health
Metrics Endpoint: http://localhost:3000/metrics

Key Metrics Monitored
Application Layer Metrics

rails_up: Application availability status (0/1)
rails_response_time_seconds: Application response time
rails_memory_usage_bytes: Memory consumption
rails_uptime_seconds: Application uptime
http_requests_total: Request volume by endpoint
rails_active_connections: Database connection pool usage
rails_thread_count: Active Ruby thread count

Infrastructure Layer Metrics

database_up: PostgreSQL connectivity status (0/1)
redis_up: Redis connectivity status (0/1)
node_cpu_seconds_total: CPU utilization
node_memory_MemTotal_bytes: System memory metrics
node_filesystem_avail_bytes: Disk space availability

Alerting Strategy
Critical Alerts (Immediate Response Required)

Application Down: rails_up == 0 for >1 minute
Database Down: database_up == 0 for >1 minute

Warning Alerts (Investigation Required)

Redis Down: redis_up == 0 for >2 minutes
High Memory Usage: rails_memory_usage_bytes > 200MB for >5 minutes
High Response Time: rails_response_time_seconds > 1 second for >5 minutes

SRE Best Practices Implemented
Observability

Comprehensive metrics collection at all stack layers
Service health monitoring with proper SLI/SLO methodology
Request tracing and performance monitoring
Real-time dashboards with alerting integration

Reliability

Health checks at container, application, and dependency levels
Automatic restart policies for service recovery
Dependency management with proper startup sequencing
Error handling and graceful degradation

Infrastructure as Code

Complete stack provisioning through single script
Version-controlled configuration management
Reproducible deployment process
Environment consistency validation

Commands Reference
bash# Deploy complete stack
./provision.sh deploy

# Check system status
./provision.sh status

# Test metrics collection
./provision.sh test-metrics

# Generate additional traffic for metrics visibility
./provision.sh generate-traffic

# Clean up environment
./provision.sh cleanup
Validation Steps
1. Verify Rails Application

Open http://localhost:3000
Confirm application loads with service status display
Check live metrics preview section

2. Verify Prometheus Metrics

Open http://localhost:9090
Navigate to Graph tab
Execute queries: rails_up, database_up, redis_up
Confirm Status > Targets shows all endpoints as UP

3. Verify Grafana Dashboard

Open http://localhost:3001
Login with admin/admin
Navigate to Dashboards > Rails SRE Monitoring Dashboard
Confirm status panels show UP and graphs display data

Technical Implementation Details
Metrics Collection

Custom Rails controller exposing Prometheus format metrics
5-second scraping intervals for real-time visibility
Counter and gauge metrics for different data types
Proper metric labeling for filtering and aggregation

Alert Configuration

Production-ready alert thresholds based on SRE best practices
Severity-based routing with appropriate response times
Webhook integration for external notification systems
Alert suppression and inhibition rules

Dashboard Design

Status overview panels with color-coded health indicators
Time-series graphs for trend analysis
Resource utilization monitoring
Request rate and performance tracking

Development Process
This solution was developed using AI-assisted methodologies including:

Architecture design consultation for SRE best practices
Code generation and debugging for Rails metrics implementation
Configuration optimization for monitoring stack components
Documentation structure following industry standards

The AI tooling enhanced development efficiency while ensuring alignment with Google SRE principles and production-ready monitoring practices.
Production Considerations

Metrics retention configured for 200 hours
Restart policies enabled for service recovery
Health check timeouts optimized for container environments
Resource limits and monitoring thresholds based on typical application usage
Security considerations with proper network isolation and access controls
