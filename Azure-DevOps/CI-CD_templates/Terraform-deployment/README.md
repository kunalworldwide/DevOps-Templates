# Terraform Azure Pipeline Guide

## Overview

This guide provides a comprehensive overview of using the Terraform Azure Pipeline for applying and destroying infrastructure. The pipeline is designed to automate the provisioning and de-provisioning of resources in Azure using Terraform, adhering to best practices.

## Prerequisites

*   Azure DevOps account
*   Access to an Azure subscription
*   Basic understanding of Terraform and Azure

## Pipeline Configuration

The pipeline is configured using a YAML file which includes steps for initializing Terraform, validating Terraform files, planning, and applying or destroying infrastructure based on the provided parameters.

### Key Parameters

*   `Action`: Can be either `apply` or `destroy`. This determines whether the pipeline will create or remove resources.

## Usage

### For Applying Infrastructure

1.  Set the Action Parameter: Ensure the `Action` parameter in the pipeline is set to `apply`. This will provision the resources defined in your Terraform scripts.
2.  Push to Main Branch: Trigger the pipeline by pushing your changes to the `main` branch. This is necessary as the `apply` action is conditioned to run only when changes are pushed to the `main` branch.
3.  Review Plan: Before the application, review the Terraform plan to ensure the correct resources are being provisioned.
4.  Apply Changes: The pipeline will automatically apply the changes if everything is as expected.

### For Destroying Infrastructure

1.  Set the Action Parameter: Change the `Action` parameter in the pipeline to `destroy` when you need to de-provision resources.
2.  Trigger Pipeline: Run the pipeline manually since the destroy action is not conditioned to any branch.
3.  Review Plan: The pipeline will generate a plan showing what resources will be destroyed. Review this carefully.
4.  Destroy Resources: Confirm the destruction of resources. The pipeline will then de-provision the resources as per the Terraform scripts.

## Best Practices

*   Version Control: Always keep your Terraform scripts in version control and use branches for managing different environments.
*   Code Review: Implement a code review process for all changes to the Terraform scripts.
*   State Management: Ensure remote state is used for managing the Terraform state and it's backed up appropriately.
*   Secrets Management: Use Azure Key Vault or similar for managing secrets, rather than hard-coding in Terraform scripts.
*   Modular Approach: Write modular Terraform code for reusability and maintainability.
*   Logging and Monitoring: Implement logging and monitoring for your pipeline to track deployments and changes.

## Troubleshooting

*   If the pipeline fails, check the logs provided by Azure DevOps for detailed error messages.
*   Ensure that the service connections and permissions in Azure DevOps and Azure are correctly configured.

## Conclusion

This pipeline simplifies the process of managing infrastructure in Azure using Terraform. By following the best practices outlined in this guide, you can ensure efficient and safe management of your cloud resources.