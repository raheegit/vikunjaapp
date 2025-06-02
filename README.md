# ToDo App Deployment (Vikunja) on Minikube

Vikunja is an open-source, self-hosted ToDo app that helps you stay organized with powerful task management features like hierarchical projects, team collaboration, and multiple views including Kanban, Gantt, and table layouts.

# Technical Stack

1. Vikunja Monolith (vikunja/vikunja)
A single Docker container that includes:
* Backend API (Golang)
* Frontend Web UI (Vue.js)
* Background Worker for recurring jobs and task reminders

2. PostgreSQL Database
Official PostgreSQL Service
* Stores all persistent Vikunja data (users, tasks, lists, reminders, etc.)

 # Kubernetes Minikube Setup and Resources
 
##  Minikube (local single-node Kubernetes cluster)
* Used for local development and testing
* Provides services like kubectl, ingress controller, persistent volumes

##  Kubernetes Resources
* vikunja/: Deploys the monolithic Vikunja container
* postgresql/: Deploys PostgreSQL with PVC and resource limits

##  Services:
* PostgreSQL: ClusterIP (internal communication)
* Vikunja: NodePort (exposed for ingress)

## * Ingress:
* Routes HTTP traffic to the Vikunja web interface via domain like vikunja.local

# Deployment Templating Strategy Using Helm
The deployment uses a Helm umbrella chart named vikunjaapp/ which aggregates multiple subcharts:
## Subcharts:
 * vikunja/ — for the main application
 * postgresql/ — for the database

## Templates:

* Each chart contains reusable Kubernetes manifest templates (Deployments, Services, PVCs, Ingress)
* Templates use Helm Go templating syntax to allow customization via values.yaml

## Values Management:

* values.yaml in the umbrella chart defines global settings and overrides for subcharts
* Allows dynamic configuration of:
  * Replica counts
  * Resource requests and limits
  * Storage sizes

# Detailed Deployment Resources:

* Deployment Guide - https://github.com/raheegit/vikunjaapp/wiki
* Minikube - https://minikube.sigs.k8s.io/docs/start/
* Helm - https://helm.sh/docs/intro/install/
* Vikunja - https://vikunja.io
* Ingress on Minikube - https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/
* Ingress Issue - https://stackoverflow.com/questions/70366074/ingress-not-working-from-official-kubernetes-tutorial/70382920#70382920
