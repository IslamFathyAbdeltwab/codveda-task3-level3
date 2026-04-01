# companyCodveda - Cloud Integration with Azure (.NET Project)

## 📌 Project Overview

This project demonstrates how to **deploy and manage .NET applications on Microsoft Azure** using modern cloud practices. It covers web hosting, file storage, serverless computing, and CI/CD automation.

The goal is to build a scalable and secure cloud-based application using Azure services.

---

## 🚀 Features

* 🌐 Deploy ASP.NET Core Web App using Azure App Services
* 📦 Store and manage files using Azure Blob Storage
* ⚡ Implement serverless logic using Azure Functions
* 🔄 Automate deployment with CI/CD using Azure DevOps

---

## 🏗️ Technologies Used

* ASP.NET Core Web API / MVC
* Microsoft Azure App Services
* Azure Blob Storage
* Azure Functions
* Azure DevOps (CI/CD Pipelines)
* Git & GitHub

---

## 📂 Project Structure

```
/CloudProject
│── /WebApp                # ASP.NET Core Application
│── /AzureFunctions       # Serverless Functions
│── /Services             # Blob Storage Service Logic
│── /Models               # Data Models
│── /Controllers          # API Controllers
│── appsettings.json      # Configuration
│── README.md
```

---

## ⚙️ Setup & Installation

### 1️⃣ Clone Repository

```bash
git clone https://github.com/your-username/companyCodveda.git
cd companyCodveda
```

### 2️⃣ Configure App Settings

Update `appsettings.json`:

```json
"AzureStorage": {
  "ConnectionString": "your_blob_storage_connection"
}
```

---

## ☁️ Azure Deployment Steps

### 🔹 1. Deploy to Azure App Services

1. Create App Service in Azure Portal
2. Publish project from Visual Studio or CLI:

```bash
dotnet publish -c Release
```

3. Deploy using:

```bash
az webapp deploy
```

---

### 🔹 2. Azure Blob Storage Integration

* Create Storage Account
* Create Blob Container
* Use SDK to upload/download files

Example:

```csharp
BlobContainerClient container = new BlobContainerClient(connectionString, "files");
await container.UploadBlobAsync(fileName, stream);
```

---

### 🔹 3. Azure Functions (Serverless)

* Create Function App
* Add HTTP Trigger Function

Example:

```csharp
[FunctionName("HelloFunction")]
public IActionResult Run(
    [HttpTrigger(AuthorizationLevel.Function, "get")] HttpRequest req)
{
    return new OkObjectResult("Hello from Azure Function");
}
```

---

### 🔹 4. CI/CD with Azure DevOps

1. Create a new Pipeline
2. Connect GitHub repository
3. Use YAML pipeline:

```yaml
trigger:
- main

pool:
  vmImage: 'windows-latest'

steps:
- task: UseDotNet@2
  inputs:
    packageType: 'sdk'
    version: '7.0.x'

- script: dotnet build --configuration Release
- script: dotnet publish -c Release -o publish

- task: AzureWebApp@1
  inputs:
    azureSubscription: 'your-subscription'
    appName: 'your-app-name'
    package: 'publish'
```

---

## 🔐 Security Considerations

* Use Azure Key Vault for secrets
* Never store connection strings in code
* Enable HTTPS for App Services
* Use Managed Identity when possible

---

## 📸 Demo (Optional)

* Upload/download files via API
* Trigger Azure Function endpoint
* Auto deployment via pipeline

---

## 🎯 Objectives Achieved

✔ Cloud deployment using Azure
✔ File storage with Blob Storage
✔ Serverless architecture using Azure Functions
✔ Automated CI/CD pipeline

---

## 👨‍💻 Author

**Islam Fathy**
Final Year Computer Science Student
Front-End & .NET Developer

---

## 📄 License

This project is for educational purposes (Codveda Internship Task).
