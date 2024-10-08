# Prometheus & Grafana Setup

This guide will help you set up Prometheus and Grafana using Docker, configure Prometheus to scrape metrics, and create a Grafana dashboard.

Prometheus Configuration
The prometheus.yml file is configured to scrape metrics from Prometheus itself and an additional application

Configuration Details
- scrape_interval: The interval between each scrape of metrics by Prometheus.
- scrape_configs:
    - prometheus: Scrapes metrics from the Prometheus server running on prometheus:9090.
    - your_application: Scrapes metrics from an application running on your_app:8000.

# Running Prometheus and Grafana with Docker
1. Start Prometheus:
   ```
      docker run -d \
      --name=prometheus \
      --network=monitoring \
      -p 9090:9090 \
      -v $(pwd)/prometheus.yml:/etc/prometheus/prometheus.yml \
      prom/prometheus
   ```
2. Start Grafana:
   ```
      docker run -d \
      --name=grafana \
      --network=monitoring \
      -p 3000:3000 \
      grafana/grafana
   ```
    
# Accessing the Services
 - Prometheus: http://localhost:9090
 - Grafana: http://localhost:3000
    - Default Login:
        - Username: admin
        - Password: admin
     
# Creating a Grafana Dashboard
1. Add Prometheus as a Data Source:
 - Navigate to Configuration -> Data Sources.
 - Select Prometheus and set the URL to http://prometheus:9090.
 - Click Save & Test.

2. Create a Dashboard:
 - Go to Dashboards -> Manage -> New Dashboard.
 - Add a new panel and configure it to visualize the metrics from Prometheus.
 - Save the dashboard for future use.

# Conclusion
You have now set up Prometheus and Grafana with Docker, configured Prometheus to scrape metrics, and created a basic Grafana dashboard.
