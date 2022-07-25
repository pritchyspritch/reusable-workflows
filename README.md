# Reusable workflows

This repository contains multiple [reusable GitHub Actions workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) that can be injected into build workflows to run security scans against our projects.

There are four different reusable workflows in this repo, they are the:

* [Static analysis code scanning workflow](.github/workflows/reusable-codeql-workflow.yml)
* [Static analysis code scanning workflow with extended security checks](.github/workflows/reusable-extended-sec-codeql.yml)
* [Static analysis code scanning workflow with security and code quality checks](.github/workflows/reusable-sec-and-quality-codeql.yml)
* [Container vulnerability scanning workflow](.github/workflows/reusable-container-workflow.yml)
* [Terraform static analysis scanning workflow](.github/workflows/reusable-tfsec-workflow.yml)
* [Web application vulnerability scanning workflow](.github/workflows/reusable-vulnerabilityscan-workflow.yml)

Workflows will post any issues to the security tab on your repository and the examples here do not currently fail builds.

## Workflow descriptions

### Static Analysis Code Scanning
The static analysis code scanning reusable workflows use [CodeQL](https://github.com/github/codeql-action) to scan for potential security issues in your code. The standard rules are turned on for the first iteration of the standard workflow, but the security extended option will be turned on later. We have provided workflows that use extended security as well as security and code quality rules if you would like to use those straight away.

The workflows require you to pass in the language used in your repo. 

You can use the [standard static analyis template](https://github.com/pritchyspritch/workflow-templates/blob/main/templates/consumed-codeql-workflow.yml) to implement the standard CodeQL rules workflow, or reference it yourself as `pritchyspritch/reusable-workflows/.github/workflows/reusable-codeql-workflow.yml@main`.

You can use the [static analysis extended security code scanning template](https://github.com/pritchyspritch/workflow-templates/blob/main/templates/consumed-extended-sec-codeql-workflow.yml) to implement the standard CodeQL rules workflow, or reference it yourself as `pritchyspritch/reusable-workflows/.github/workflows/reusable-extended-sec-codeql.yml@main`.

You can use the [static analysis security and quality code scanning template](https://github.com/pritchyspritch/workflow-templates/blob/main/templates/consumed-sec-and-quality-codeql-workflow.yml) to implement the standard CodeQL rules workflow, or reference it yourself as `pritchyspritch/reusable-workflows/.github/workflows/reusable-sec-and-quality-codeql.yml@main`.


### Container Vulnerability Scanning
The container vulnerability scanning reusable workflow uses the [Trivy](https://github.com/aquasecurity/trivy-action) filesystem scan, [Trivy](https://github.com/aquasecurity/trivy-action) config scan, and the [Anchore Grype scan](https://github.com/anchore/scan-action). This workflow requires you to pass in the path to the Dockerfile. You can use the [container vulnerability scan template](https://github.com/pritchyspritch/workflow-templates/blob/main/templates/consumed-container-workflow.yml) to implement this workflow, or reference it yourself as `pritchyspritch/reusable-workflows/.github/workflows/reusable-container-workflow.yml@main`.

### Terraform Static Analysis Scanning
The terraform static analysis scanning reusable workflow uses [tfsec](https://github.com/aquasecurity/tfsec) to scan the terraform for potential misconfigurations in your terraform cloud deployments. This workflow requires you to pass in the path to your terraform. You can use the [terraform static analysis template](https://github.com/pritchyspritch/workflow-templates/blob/main/templates/consumed-tfsec-workflow.yml) to implement this workflow, or reference it yourself as `pritchyspritch/reusable-workflows/.github/workflows/reusable-tfsec-workflow.yml@main`.

### Web Application Vulnerabilty Scanning
The web application vulnerability scanning reusable workflow uses [Nuclei](https://github.com/projectdiscovery/nuclei-action) to scan web applications for vulnerabilities. This workflow should be run as soon as the build is deployed to check for any security issues in the application once it's running. This workflow requires you to pass in the URL of the deployed web application. You can use the [web app vulnerability scan template](https://github.com/pritchyspritch/workflow-templates/blob/main/templates/consumed-nuclei-workflow.yml) to implement this workflow, or reference it yourself as `pritchyspritch/reusable-workflows/.github/workflows/reusable-vulnerabilityscan-workflow.yml@main`.

##  Workflow Templates
There are a number of [workflow templates](https://github.com/pritchyspritch/workflow-templates) available that consume these reusable workflows as examples of how to use them. Simply copy over the code to your own workflow files to get started.

