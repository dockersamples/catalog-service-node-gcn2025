# Catalog Service - Node

> [!NOTE]
> This repo is a fork of the [Catalog Service (Node)](https://github.com/dockersamples/catalog-service-node) project specifically for Google Cloud Next 2025.
> It will be archived and not maintained after the event. Go to the original repo for the ongoing project.

This repo has had its CI pipeline updated to:

- Build images and push them to Google Artifact Registry
- Create image attestations with Binary Authorization to indicate the images were created by CI
- Deploy the new image to Google Cloud Run with a policy that ensures only images with a `gha-workflow` attestation can be run


## Google Cloud configuration

All Google Cloud resources (except for the initial project creation and state bucket) are defined in Terraform in the [./tf](./tf) directory.