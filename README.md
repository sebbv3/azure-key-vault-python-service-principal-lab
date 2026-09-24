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

<img width="1006" height="206" alt="Screenshot 2026-09-24 181740" src="https://github.com/user-attachments/assets/2f975c44-c352-4856-bbfb-65342307a682" />
<img width="1452" height="555" alt="Screenshot 2026-09-24 181617" src="https://github.com/user-attachments/assets/b115690f-1e7b-4f18-8a56-efd973db6415" />
<img width="1532" height="812" alt="Screenshot 2026-09-24 181324" src="https://github.com/user-attachments/assets/68a23df2-5b06-4624-a6b3-3c39d24ae2a5" />
<img width="1535" height="816" alt="Screenshot 2026-09-24 175848" src="https://github.com/user-attachments/assets/ba6371d3-b4a1-4274-870d-0d85e5d9586f" />
<img width="1535" height="812" alt="Screenshot 2026-09-24 174842" src="https://github.com/user-attachments/assets/fd32a617-d726-4e95-b018-7b9a9bb27525" />
<img width="1535" height="816" alt="Screenshot 2026-09-24 174343" src="https://github.com/user-attachments/assets/448e84ea-746b-4724-a751-eb6616db50d8" />
<img width="1535" height="812" alt="Screenshot 2026-09-24 174127" src="https://github.com/user-attachments/assets/234e42f8-4bdf-487d-a1c3-933cd5eb06cc" />
<img width="1535" height="812" alt="Screenshot 2026-09-24 173658" src="https://github.com/user-attachments/assets/d8221695-6a2e-4906-86fa-2cadc9b45c5d" />
<img width="1535" height="812" alt="Screenshot 2026-09-24 173525" src="https://github.com/user-attachments/assets/ce661285-3976-4a1a-8f5a-ad8b93d7eaed" />
<img width="1535" height="815" alt="Screenshot 2026-09-24 173456" src="https://github.com/user-attachments/assets/1f43d408-0cf0-4b05-af95-b67c847d8e0c" />
<img width="1532" height="816" alt="Screenshot 2026-09-24 173240" src="https://github.com/user-attachments/assets/f59e0a2a-4b07-4b62-946f-4c2901369c85" />
<img width="1535" height="816" alt="Screenshot 2026-09-24 172941" src="https://github.com/user-attachments/assets/dfe3de48-f0e0-4e66-91ea-31936670126c" />

