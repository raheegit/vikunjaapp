# ToDo App Deployment (Vikunja) on Minikube

Vikunja is an self-hostable to-do list and task management application designed for privacy and control by being deployable on your own infrastructure.

# Technical Stack

First bullet point
Vikunja Monolith (vikunja/vikunja)
A single Docker container that includes:

Backend API (Golang)

Frontend Web UI (Vue.js)

Background Worker for recurring jobs and task reminders

PostgreSQL Database

Official PostgreSQL Helm chart

Stores all persistent Vikunja data (users, tasks, lists, reminders, etc.)
