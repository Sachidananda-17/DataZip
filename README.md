
# DataZip

Tak on connecting the clickhouse database with the superset using docker, kubernets.


## Prerequisites

- **Kubernetes knowledge**: Understanding of Kubernetes concepts and basic operations.
- **Minikube**: Installed on your local machine to run Kubernetes clusters locally.
- **Docker knowledge**: Familiarity with Docker for containerization.
- **ClickHouse**: Understanding of ClickHouse as an open-source data warehouse.
- **Superset**: Familiarity with Superset, a BI tool for data visualization.


## Installation

### Install Minikube

Follow the official [Minikube installation guide](https://minikube.sigs.k8s.io/docs/start/) for your operating system.

### Install kubectl

Follow the official [kubectl installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/) for your operating system.

### Install Docker

Follow the official [Docker installation guide](https://docs.docker.com/get-docker/) for your operating system.

## Steps

### Step 1: Create ClickHouse StatefulSet with Persistent Storage

Create a StatefulSet for ClickHouse with persistent storage of 10GB.

```bash
kubectl apply -f clickhouse-statefulset.yaml

```
#### Reason: Ensures data persistence for ClickHouse. 
### Step 2 : Create Superset Deployment and Service
Deploy Superset using a Kubernetes Deployment and expose it via a NodePort service.

```
kubectl apply -f superset-deployment.yaml
```
#### Reason: Provides access to Superset's UI and APIs.


### Step 3 : Access Superset UI
Retrieve the URL to access Superset's UI using Minikube.

```
minikube service superset --url

```
#### Reason: Access the Superset UI for configuration.


Login to the superset portal using the credentials




## Screenshots

![Sueper Set UI](https://github.com/Sachidananda-17/DataZip/blob/main/images/datazip%201.png)






### Step 4 : Create Superset Admin User

Open a shell inside the Superset pod and create an admin user.

```bash
kubectl exec -it <superset-pod-name> -- /bin/bash
superset fab create-admin --username admin --firstname Admin --lastname User --email admin@admin.com --password admin


```
#### Reason: Allows login and configuration of Superset.

### Step 5: Initialize Superset Database
Run commands inside the Superset pod to initialize the database.

```
kubectl exec -it <superset-pod-name> -- superset db upgrade

```
#### Reason: Sets up Superset's database schema.


### Step 6: Connect ClickHouse to Superset
In Superset UI, add a new database connection for ClickHouse using SQLAlchemy URI.

```
clickhousedb://{username}:{password}@{hostname}:{port}/{database}


```
#### Reason: Enables data visualization from ClickHouse in Superset.


## Screenshots

![ClickHouse and Superset connection](http.....)






Click the test connection in the superset to get connect the database to the superset.




## Authors

- [Sachidananda Manideep ](https://github.com/Sachidananda-17)

