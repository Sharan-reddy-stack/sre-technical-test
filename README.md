# sre-technical-test

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
```bash
chmod +x provision.sh
./provision.sh deploy
