# Realtime-News-Insights

This project is designed to deliver a real-time news insights pipeline that constantly gathers and processes news data, extracts pertinent information, and stores it for subsequent analysis. The entire project is containerized using Docker and orchestrated with Kubernetes. Prometheus and Grafana are integrated to monitor and visualize the system's performance.

## Features

- Retrieve news data in real-time from a news API.
- Conduct sentiment analysis on news articles.
- Extract relevant hashtags and keywords from articles.
- Deploy with Kubernetes using Docker containers.
- Monitor application performance with Prometheus and visualize using Grafana.

## Configuration

1) Run the setup script.sh, which:

- Installs Minikube and Helm.
- Installs Docker (assumes an APT-based Linux distribution).
- Starts Minikube.
- Installs Prometheus using Helm.
- Installs Grafana using Helm.
- Creates the config.json files with the provided JSON content in the data_ingestion/ and data_processing/ directories.

```sh
sudo chmod +x setup.sh
./setup.sh
```

2) Fill in the configuration files and build the two dockerfiles in the directories data_ingestion/ and data_processing/.
```sh
   docker build data_ingestion/Dockerfile -t ingest_data:latest
   docker build data_processing/Dockerfile -t analyse_data:latest
```
4) Either push to dockerhub or push to minikube registry locally.
5) Run the minikube cluster, apply the news_injest_cronjob.yaml and news_analysis_store.yaml files.
```sh
   kubectl apply -f news_injest_cronjob.yaml
   kubectl apply -f news_analysis_store.yaml
```
