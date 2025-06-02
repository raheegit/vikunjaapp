# ToDo App Deployment (Vikunja) on Minikube

Vikunja is an self-hostable to-do list and task management application designed for privacy and control by being deployable on your own infrastructure.

# Technical Stack

1. Vikunja Monolith (vikunja/vikunja)
A single Docker container that includes:
* Backend API (Golang)
* Frontend Web UI (Vue.js)
* Background Worker for recurring jobs and task reminders

2. PostgreSQL Database
Official PostgreSQL Service
Stores all persistent Vikunja data (users, tasks, lists, reminders, etc.)

 # Kubernetes Minikube Setup and Resources
 
* Minikube (local single-node Kubernetes cluster)
1. Used for local development and testing
2. Provides services like kubectl, ingress controller, persistent volumes

* Kubernetes Resources
1. vikunja/: Deploys the monolithic Vikunja container
2. postgresql/: Deploys PostgreSQL with PVC and resource limits

*Services:
1. PostgreSQL: ClusterIP (internal communication)
2. Vikunja: NodePort (exposed for ingress)

* Ingress:
1. Routes HTTP traffic to the Vikunja web interface via domain like vikunja.local
