# Azure Key Vault with Python and Service Principal

## Overview

This project documents a hands-on Azure lab where I configured a Python application to securely access Azure Key Vault using a Microsoft Entra ID Service Principal.

The application authenticates to Azure without using a personal user account and is able to create and retrieve secrets stored inside Azure Key Vault.

## What I Learned

During this lab, I worked with:

- Microsoft Azure
- Azure Key Vault
- Microsoft Entra ID (Azure Active Directory)
- Service Principals
- Authentication and authorization
- Azure Access Policies
- Azure Cloud Shell
- Python
- Azure Python SDK
- Git and GitHub
- Python package management with pip
- Basic Linux terminal navigation and troubleshooting

## Project Workflow

The project followed this general architecture:

Python Application  
↓  
Service Principal Authentication  
↓  
Microsoft Entra ID  
↓  
Azure Key Vault  
↓  
Create / Retrieve Secrets

## Azure Key Vault

I created an Azure Key Vault that acts as a secure location for sensitive information such as:

- Passwords
- API keys
- Tokens
- Application secrets
- Certificates

Instead of storing sensitive information directly inside application code, an application can retrieve it securely from Azure Key Vault.

## Service Principal

A Service Principal was used as the identity of the Python application.

The application authenticated using:

- Tenant ID
- Client ID
- Client Secret

The Service Principal was then granted permission to access the Key Vault.

This demonstrated the difference between:

**Authentication** – verifying the identity of the application.

**Authorization** – determining what the application is allowed to access.

## Python Application

The application used the Azure Python SDK, including:

```bash
azure-identity
azure-keyvault-secrets
