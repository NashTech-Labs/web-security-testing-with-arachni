# Security Testing Workflow

This repository contains a GitHub Actions workflow for performing security testing on a web application using Arachni, an open-source web application security scanner. The workflow involves running a vulnerable web application (OWASP Juice Shop) and scanning it for vulnerabilities.

## Workflow Overview

The GitHub Actions workflow is triggered on the following events:

- **Push to the master branch**
- **Pull request targeting the master branch**
- **Manual dispatch with an optional URL input**

## Workflow Steps

The workflow performs the following steps:

1. **Checkout Repository**: Checks out the code from the repository.
2. **Set up Docker Buildx**: Sets up Docker Buildx, required for building and running Docker images (only if the default URL is used).
3. **Pull Juice Shop Docker Image**: Pulls the Juice Shop Docker image from Docker Hub (only if the default URL is used).
4. **Run Juice Shop Container**: Runs the Juice Shop container (only if the default URL is used).
5. **Get Juice Shop Container IP**: Retrieves the IP address of the running Juice Shop container (only if the default URL is used).
6. **Wait for Juice Shop to be Ready**: Waits until the Juice Shop application is ready to accept connections (only if the default URL is used).
7. **Download Arachni**: Downloads and extracts Arachni.
8. **Run Arachni Scan**: Runs Arachni to scan the specified URL and generates a report.
9. **List Arachni Output Directory**: Lists the contents of the directory containing the HTML report.
10. **Upload Arachni HTML Report**: Uploads the Arachni HTML report as an artifact.

## Inputs

When manually triggering the workflow, you can provide the following input:

- **url**: The URL of the website to scan. If not specified, defaults to `http://localhost:3000`.

## Environment Variables

- **DEFAULT_URL**: The default URL for the local Juice Shop instance, set to `http://localhost:3000`.

## Artifacts

The workflow generates the following artifact:

- **Arachni HTML Report**: The Arachni report in HTML format.

## Usage

To manually trigger the workflow with an optional URL input, follow these steps:

1. Navigate to the "Actions" tab in your GitHub repository.
2. Select the "Security Testing" workflow from the list.
3. Click on the "Run workflow" button.
4. Provide the URL of the website to scan (optional). If not specified, the default URL `http://localhost:3000` will be used.
5. Click on the "Run workflow" button to start the workflow.
