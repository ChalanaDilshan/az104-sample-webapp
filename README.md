# Azure App Service CI/CD Demo (.NET 10)

This is a sample .NET 10 Web Application created for practicing **AZ-104 (Microsoft Azure Administrator)** lab scenarios, specifically focused on deploying web applications using **GitHub Actions CI/CD workflows** to **Azure App Service**.

---

## 🛠️ Tech Stack & Cloud Services
* **Framework:** .NET 10.0
* **Cloud Provider:** Microsoft Azure
* **Hosting Service:** Azure App Service (Linux)
* **CI/CD Automation:** GitHub Actions

---

## 🔄 How the CI/CD Pipeline Works
1. Any code changes or commits pushed to the `main` branch trigger the GitHub Actions workflow.
2. GitHub Actions sets up the .NET environment and builds the application.
3. The build output is packaged and published.
4. Using Azure's **Publish Profile**, the application is automatically deployed to the live Azure Web App.

---

## ⚙️ Pre-requisites & Setup
1. Download the **Publish Profile** from your Azure Web App resource in the Azure Portal.
2. Add the profile content as a Repository Secret in GitHub:
   * **Secret Name:** `AZURE_WEBAPP_PUBLISH_PROFILE`
3. Ensure the `AZURE_WEBAPP_NAME` environment variable in `.github/workflows/deploy.yml` matches your actual Azure Web App name.
