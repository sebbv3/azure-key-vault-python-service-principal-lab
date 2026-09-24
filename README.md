# Azure Key Vault with Python and Service Principal

## Overview

This project documents a hands-on Microsoft Azure lab where I configured a Python application to securely access Azure Key Vault using a Microsoft Entra ID Service Principal.

The application authenticates to Azure without using a personal user account and can securely create and retrieve secrets stored inside Azure Key Vault.

This project provided hands-on experience with cloud identity, authentication, authorization, secret management, Python SDKs, Azure Cloud Shell, and troubleshooting.

---

## Technologies Used

- Microsoft Azure
- Azure Key Vault
- Microsoft Entra ID
- Service Principal
- Azure Cloud Shell
- Python
- Azure SDK for Python
- Git
- Linux / Bash
- pip

---

## Project Architecture

```text
Python Application
        |
        v
Service Principal
        |
        v
Microsoft Entra ID
        |
        v
Azure Key Vault
        |
        v
Create / Retrieve Secrets
```

The Service Principal acts as the application's identity.

The application authenticates using a Tenant ID, Client ID, and Client Secret. After authentication, the Service Principal's permissions determine what the application is authorized to do inside Azure Key Vault.

---

# Implementation

## 1. Create the Azure Key Vault

I first created a new Azure Key Vault using the existing lab subscription and resource group.

The vault was configured in the **West US** region using the **Standard** pricing tier.

![Create Azure Key Vault](screenshots/01-create-key-vault.png)

---

## 2. Configure the Access Policy

I configured the Key Vault to use the **Vault access policy** permission model.

The **Key, Secret, & Certificate Management** template was selected to define the permissions available to the application.

![Configure Access Policy Permissions](screenshots/02-access-policy-permissions.png)

This step defines what actions the authenticated identity is authorized to perform inside the Key Vault.

---

## 3. Assign the Service Principal

I selected the Service Principal that would be used by the Python application.

A Service Principal acts as an identity for an application instead of a human user.

![Select Service Principal](screenshots/03-select-service-principal.png)

---

## 4. Review the Access Policy

Before creating the policy, I reviewed the selected permissions and confirmed that the correct Service Principal had been assigned.

![Review Access Policy](screenshots/04-review-access-policy.png)

This demonstrates the difference between:

- **Authentication** – verifying the identity of the application.
- **Authorization** – determining what the application is allowed to access.

---

## 5. Review and Create the Key Vault

After configuring the vault and access policy, I reviewed the final settings before deployment.

![Review Key Vault](screenshots/05-review-key-vault.png)

The Key Vault was then deployed successfully.

---

## 6. Configure Azure Cloud Shell

Azure Cloud Shell was used as the Linux development environment for this project.

A storage account and file share were configured so Cloud Shell could maintain persistent storage.

![Configure Azure Cloud Shell](screenshots/06-cloud-shell-storage.png)

Cloud Shell allowed me to work directly with tools such as:

```bash
git
python
pip
cd
ls
az
```

without installing the Azure CLI environment locally.

---

## 7. Configure the Python Application

The provided Python application was opened inside Azure Cloud Shell.

The application uses the Azure Python SDK:

```python
from azure.identity import ClientSecretCredential
from azure.keyvault.secrets import SecretClient
```

The application authenticates using:

```text
Tenant ID
Client ID
Client Secret
```

and connects to the Azure Key Vault.

![Python Application Setup](screenshots/07-python-application-setup.png)

Sensitive credentials are intentionally not included in this repository.

---

## 8. Install the Required Python Packages

The application required the Azure Identity and Key Vault Secrets libraries.

The required packages were installed using pip:

```bash
python -m pip install --user azure-identity azure-keyvault-secrets
```

These packages allow the application to authenticate with Microsoft Azure and interact with Azure Key Vault.

---

## 9. Create a Secret Using Python

After configuring the application, I ran the Python script:

```bash
python pyappregkeyvault.py
```

The application successfully connected to Azure Key Vault and created a new test secret.

![Secret Created with Python](screenshots/08-secret-created.png)

This confirmed that the Service Principal was successfully authenticated and authorized to write secrets to the vault.

---

## 10. Verify the Secret in Azure Key Vault

After refreshing the Secrets page in Azure Portal, the secret created by the Python application appeared inside the Key Vault.

![Secret Visible in Azure Key Vault](screenshots/09-secret-in-key-vault.png)

This confirmed that the Python application had successfully written data to Azure Key Vault.

---

## 11. Retrieve the Secret Using Python

The application was run again to retrieve the existing secret.

```bash
python pyappregkeyvault.py
```

The application successfully retrieved the secret and returned its stored value.

![Retrieve Secret with Python](screenshots/10-secret-retrieved.png)

This confirmed that the Python application could successfully perform both write and read operations against Azure Key Vault.

---

# Troubleshooting

During the lab, I encountered and resolved several issues.

## Incorrect Working Directory

When I initially attempted to run the application, Python returned:

```text
No such file or directory
```

I verified the current directory and project files using:

```bash
ls
```

and navigated to the correct project directory using:

```bash
cd content-develop-a-python-app-to-access-key-vault-using-a-service-principal
```

After changing to the correct directory, Python was able to locate the application.

---

## Missing Azure Python Module

After locating the script, Python returned:

```text
ModuleNotFoundError: No module named 'azure'
```

I identified that the required Azure SDK libraries were missing and installed them with:

```bash
python -m pip install --user azure-identity azure-keyvault-secrets
```

After installing the dependencies, the Python application executed successfully.

---

# What I Learned

This project gave me hands-on experience with:

- Creating and configuring an Azure Key Vault
- Working with Microsoft Entra ID identities
- Understanding Service Principals
- Configuring Azure access policies
- Understanding authentication vs. authorization
- Secure secret management
- Using Azure Cloud Shell
- Working with Linux terminal commands
- Installing Python packages with pip
- Using the Azure SDK for Python
- Creating secrets programmatically
- Retrieving secrets programmatically
- Troubleshooting Python and Linux errors

---

# Security Notes

No real credentials are stored in this repository.

Sensitive values such as Client Secrets should never be committed to GitHub or stored directly inside application source code.

In production environments, credentials should be securely managed using services such as Azure Key Vault, Managed Identities, or environment variables.

---

## Result

The Python application successfully authenticated to Microsoft Azure using a Service Principal and was able to:

- Connect to Azure Key Vault
- Create a secret
- Store a secret securely
- Retrieve an existing secret
- Verify the returned secret value

This project demonstrates practical experience with Azure identity management, cloud security, secret management, Python, and troubleshooting.
