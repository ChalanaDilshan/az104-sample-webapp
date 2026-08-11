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

## 📋 Pre-requisites & Setup Guide

Follow these step-by-step instructions to try out this deployment on your own Azure account:

### 1. Pre-requisites
* An active **Microsoft Azure Account** (Azure for Students, Free Trial, or Pay-As-You-Go).
* A **GitHub Account**.

---

### 2. Step-by-Step Deployment Instructions

#### Step 1: Fork or Clone this Repository
Click the **Fork** button at the top right of this page to create a copy of this repository under your own GitHub account.

---

#### Step 2: Create an Azure Web App
1. Log in to the [Azure Portal](https://portal.azure.com).
2. Search for **App Services** and click **+ Create** -> **Web App**.
3. Fill in the required details:
   * **Resource Group:** Select existing or click *Create new* (e.g., `rg-webapp`).
   * **Name:** Choose a unique Web App name (e.g., `my-demo-webapp-123`).
   * **Publish:** Select `Code`.
   * **Runtime stack:** Select `.NET 10 (LTS)` or `.NET 8 (LTS)`.
   * **Operating System:** `Linux`.
   * **Region:** Choose a region close to you (e.g., `East Asia`).
   * **Pricing Plan:** Select `Free (F1)` or `Basic (B1)` for testing.
4. Click **Review + Create**, then click **Create**.

---

#### Step 3: Enable Basic Auth & Download Publish Profile
1. Once the Web App is created, navigate to your Web App resource in Azure Portal.
2. Go to **Settings** -> **Configuration** -> **General settings** tab.
3. Scroll down and set **SCM Basic Auth Publishing Credentials** to **On** (Enabled).
4. Click **Save** at the top.
5. Go back to the **Overview** tab and click **Download publish profile** to download the `.PublishSettings` file.

---

#### Step 4: Configure GitHub Secrets
1. Open your forked GitHub Repository.
2. Go to **Settings** -> **Secrets and variables** -> **Actions**.
3. Click **New repository secret**.
4. Set the details:
   * **Name:** `AZURE_WEBAPP_PUBLISH_PROFILE`
   * **Secret:** Open the downloaded `.PublishSettings` file in Notepad/VS Code, copy **all** XML content, and paste it here.
5. Click **Add secret**.

---

#### Step 5: Update the Workflow File
1. Open the `.github/workflows/deploy.yml` file in your repository.
2. Update the `AZURE_WEBAPP_NAME` environment variable with your actual Azure Web App name created in **Step 2**:
   ```yaml
   env:
     AZURE_WEBAPP_NAME: 'your-actual-azure-webapp-name'
