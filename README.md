# Prometheus & Grafana Setup

This guide will help you set up Prometheus and Grafana using Docker, configure Prometheus to scrape metrics, and create a Grafana dashboard.

Prometheus Configuration
The prometheus.yml file is configured to scrape metrics from Prometheus itself and an additional application

Configuration Details
- scrape_interval: The interval between each scrape of metrics by Prometheus.
- scrape_configs:
    - prometheus: Scrapes metrics from the Prometheus server running on prometheus:9090.
    - your_application: Scrapes metrics from an application running on your_app:8000.
