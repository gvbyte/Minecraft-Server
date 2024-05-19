# This configuration includes:

**Minecraft Server (itzg/minecraft-server)**: Runs a Minecraft server and persists data.

**Grafana**: A dashboard for visualizing metrics.

**Prometheus**: For collecting and storing metrics.

**Prometheus Node Exporter**: For exporting system-level metrics.

**Kibana**: For visualizing Elasticsearch data.

**Elasticsearch**: For storing and searching log data.

# Additional Configuration
## Prometheus Configuration File (prometheus.yml)

You need to create a prometheus.yml file to configure Prometheus to scrape metrics from the node exporter:

yaml file
(Copy code)
```
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node-exporter'
    static_configs:
      - targets: ['node-exporter:9100']
```
Place this prometheus.yml file in the same directory as your docker-compose.yaml file.

## Running the Setup
Ensure Docker and Docker Compose are installed on your system.
Save the docker-compose.yaml and prometheus.yml files in a directory.
Navigate to the directory containing these files and run:
```
docker-compose up -d
```
This command will start all the services in detached mode. You can access the services via the following URLs:

**Minecraft Server: minecraft-server:25565**

**Grafana: http://localhost:3000 (default login: admin/admin)**

**Prometheus: http://localhost:9090**

**Kibana: http://localhost:5601**

**Elasticsearch: http://localhost:9200**

