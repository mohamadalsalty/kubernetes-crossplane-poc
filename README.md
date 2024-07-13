# Crossplane PoC Installation and Configuration

This guide provides a Proof of Concept (PoC) for installing and configuring Crossplane with GCP on your Kubernetes cluster.

## Prerequisites

- Helm installed
- Kubernetes cluster
- GCP service account credentials

## Installation

1. Add the Crossplane Helm repository:

   ```shell
   helm repo add crossplane-stable https://charts.crossplane.io/stable
   ```

2. Update your Helm repositories:

   ```shell
   helm repo update
   ```

3. Install Crossplane into your Kubernetes cluster:

   ```shell
   helm install crossplane crossplane-stable/crossplane --namespace crossplane-system --create-namespace
   ```

## Configuration

1. Apply the provider configuration:

   ```shell
   kubectl apply -f provider.yaml
   ```

2. Create a Kubernetes secret with your GCP credentials:

   ```shell
   kubectl create secret generic gcp-secret -n crossplane-system --from-file=creds=/home/mohamad/Downloads/formidable-bank-427016-h1-1f3dd31a3384.json
   ```

3. Apply the configuration file:

   ```shell
   kubectl apply -f config.yaml
   ```

4. Create a GCP bucket resource:

   ```shell
   kubectl create -f bucket.yaml
   ```

5. Apply the firewall configuration:

   ```shell
   kubectl apply -f firewall.yaml
   ```

## YAML Files

- **provider.yaml**: Configures the GCP provider.
- **config.yaml**: Sets up provider configuration using GCP credentials.
- **bucket.yaml**: Defines a GCP storage bucket.
- **firewall.yaml**: Configures a GCP vpc and firewall rule.
