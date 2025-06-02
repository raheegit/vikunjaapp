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

# Kubernetes Resources

To deploy and manage this application effectively, we leverage Kubernetes and a variety of its resources:

* Namespace: Kubernetes namespaces are utilized to create isolated environments for different components of the application, ensuring separation and organization.

* Secret: Kubernetes secrets store sensitive information, such as API keys or credentials, required by the application securely.

* Deployment: Kubernetes deployments define how many instances of the application should run and provide instructions for updates and scaling.

* Service: Kubernetes services ensure that users can access the application by directing incoming traffic to the appropriate instances.

* StatefulSet: For components requiring statefulness, such as the MongoDB replica set, Kubernetes StatefulSets are employed to maintain order and unique identities.

* PersistentVolume and PersistentVolumeClaim: These Kubernetes resources manage the storage required for the application, ensuring data persistence and scalability.
