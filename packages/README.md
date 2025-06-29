# 🌱 EcoGuardian: Your AI-Powered Carbon Footprint Tracker & Sustainability Coach

## 🚀 Project Overview

EcoGuardian is a cutting-edge, serverless application designed to empower individuals to understand, track, and actively reduce their personal carbon footprint. By leveraging the latest advancements in Artificial Intelligence and cloud computing on Azure, EcoGuardian provides a personalized, interactive, and data-driven experience. It acts as both a diligent tracker of your environmental impact and a knowledgeable coach, offering tailored advice and answering your questions about sustainability.

This project is built upon the foundation of Azure Developer CLI (azd) AI templates, specifically integrating:

*   **Serverless GenAI Assistant with LangChain.js:** For intelligent, conversational coaching and personalized recommendations.
*   **RAG (Retrieval Augmented Generation) with Azure AI Search:** To provide accurate, context-aware answers by referencing curated climate data, research papers, and local sustainability policies.
*   **JavaScript/TypeScript Frontend:** For a dynamic and user-friendly interface, likely using a framework like React or Next.js for rich data visualization.

## 🎯 The Problem We're Solving

Climate change is a pressing global issue, yet many individuals find it challenging to:

*   **Quantify their personal impact:** Accurately measure their daily carbon emissions from various activities (commute, diet, energy consumption, purchases).
*   **Receive actionable, personalized advice:** Generic tips are often insufficient; users need guidance tailored to their lifestyle, location, and specific habits.
*   **Access reliable information:** Navigating the vast amount of climate data, research, and local regulations can be overwhelming.
*   **Stay motivated:** Maintaining sustainable habits requires ongoing engagement and a sense of progress.

EcoGuardian aims to bridge these gaps by providing an accessible, intelligent, and engaging platform.

## ✨ Key Features

EcoGuardian offers a suite of features designed for comprehensive sustainability management:

*   **Intelligent Carbon Footprint Tracking:**
    *   **Manual Input:** Users can easily log daily activities (e.g., travel modes, meals, home energy usage).
    *   **Potential IoT Integration (Future):** Seamlessly connect with smart home devices or wearables to automate data capture.
    *   **Data Visualization:** Clear charts and graphs illustrate emission sources and trends over time.

*   **AI-Powered Sustainability Coaching:**
    *   **Personalized Recommendations:** Based on tracked data, the GenAI assistant suggests specific, achievable actions (e.g., "Switching to a plant-based meal twice a week could reduce your dietary emissions by X kg CO₂e per month").
    *   **Goal Setting & Progress Monitoring:** Users can set personal reduction targets, and the AI helps track progress towards them.
    *   **Motivational Feedback:** Encouraging messages and achievement badges for reaching milestones.

*   **RAG-Enhanced Knowledge Base:**
    *   **Question Answering:** Ask natural language questions about climate science, local recycling rules, energy efficiency tips, or government incentives.
    *   **Data Sources:** Leverages curated datasets, including excerpts from IPCC reports, local municipal guidelines, and reputable climate research, indexed in Azure AI Search.

*   **Community & Gamification:**
    *   **Leaderboards:** Compare progress anonymously with other users.
    *   **Challenges:** Participate in community-wide sustainability challenges.
    *   **Sharing:** Option to share achievements and tips on social media.

## 🛠️ Technology Stack

This project is architected for scalability, efficiency, and ease of development using Azure services and modern JavaScript frameworks:

*   **Cloud Platform:** Microsoft Azure
*   **Orchestration & Deployment:** Azure Developer CLI (`azd`)
*   **Compute:**
    *   Azure Functions (for serverless backend logic, API endpoints)
    *   Azure Static Web Apps (for hosting the frontend and integrating with Azure Functions)
*   **AI Services:**
    *   **Azure OpenAI Service:** For the Generative AI capabilities (e.g., GPT-3.5-turbo, GPT-4) powering the coaching assistant.
    *   **Azure AI Search (formerly Cognitive Search):** For indexing and retrieving data for the RAG system.
*   **AI Orchestration Frameworks:**
    *   **LangChain.js:** To build and manage the AI agent, connect LLMs, and implement prompt engineering for coaching.
    *   **LlamaIndex.TS:** To efficiently load, index, and query diverse data sources for RAG.
*   **Frontend:**
    *   **JavaScript/TypeScript:** Core programming languages.
    *   **React / Next.js (or similar):** For building a responsive and interactive user interface.
    *   **D3.js / Chart.js:** For creating insightful data visualizations of carbon footprints and progress.
*   **Data Storage:**
    *   Azure AI Search for the RAG knowledge base.
    *   Potentially Azure Cosmos DB or Azure Table Storage for user data and tracking logs.

## 🚀 Getting Started with Deployment

This project is designed for streamlined deployment using the Azure Developer CLI (`azd`).

### 1. Prerequisites

Before you begin, ensure you have the following installed:

*   **Azure Subscription:** An active Azure subscription is required. If you don't have one, you can create a free account.
*   **Azure Developer CLI (`azd`):** Install the latest version from the [official installation guide](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/install-azd).
*   **Node.js and npm/yarn:** Ensure you have Node.js (v18 or later recommended) and a package manager (npm or yarn) installed.
*   **Azure OpenAI / Azure AI Services Resource:** You must provision an Azure OpenAI Service resource or an Azure AI Services resource with a deployed language model (e.g., `gpt-35-turbo`, `gpt-4`). You'll also need an Azure AI Search resource.

### 2. Authentication

Log in to your Azure account using the Azure Developer CLI:

```bash
azd auth login
```
Follow the prompts to authenticate through your browser.

### 3. Project Setup & Configuration

1.  **Clone the Repository:**
    ```bash
    git clone <repository-url>
    cd <project-directory>
    ```
    *(Note: If you are starting from an existing `azd` template, you'll adapt this step.)*

2.  **Environment Configuration:**
    Create a `.env` file in the root of your project by copying the `.env.example` file:
    ```bash
    cp .env.example .env
    ```
    Open the `.env` file and fill in your Azure and AI service credentials:
    ```env
    # .env file example
    AZURE_SUBSCRIPTION_ID=<your-azure-subscription-id>
    AZURE_LOCATION=<your-preferred-azure-region> # e.g., eastus, westeurope
    AZURE_TENANT_ID=<your-azure-tenant-id> # Optional, if not using default tenant

    # Azure OpenAI / AI Services Configuration
    OPENAI_API_KEY=<your-openai-api-key>
    OPENAI_ENDPOINT=<your-openai-endpoint>
    OPENAI_DEPLOYMENT_NAME=<your-openai-deployment-name> # e.g., gpt-35-turbo, my-custom-model

    # Azure AI Search Configuration
    SEARCH_ENDPOINT=<your-search-endpoint>
    SEARCH_API_KEY=<your-search-api-key>
    SEARCH_INDEX_NAME=<your-desired-search-index-name> # e.g., ecoguardian-data
    ```
    *   **`AZURE_LOCATION`**: Choose a region that supports the Azure services you intend to use.
    *   **`OPENAI_DEPLOYMENT_NAME`**: This is the specific name you gave your model deployment within Azure OpenAI.

### 4. Provision Azure Resources

This command will provision all necessary Azure infrastructure based on the `azure.yaml` file in the project (e.g., Azure Static Web App, Azure Functions App, Azure AI Search index).

```bash
azd provision
```
You will be prompted to provide a name for your project and potentially other resource-specific names.

### 5. Deploy the Application

After provisioning, deploy your application code to the created Azure resources:

```bash
azd deploy
```
This command builds your frontend and backend code and deploys it to Azure Static Web Apps and Azure Functions.

### 6. Run and Interact

Once the deployment is complete, `azd` will output the URL for your deployed EcoGuardian application. Open this URL in your web browser to start tracking your carbon footprint and interacting with your AI sustainability coach!

## 💡 Customization and Extension

EcoGuardian is designed to be a flexible platform. Here are several ways you can customize and extend its functionality:

*   **Data Ingestion:**
    *   **Expand Knowledge Base:** Add more datasets to Azure AI Search, such as detailed life cycle assessments of products, regional energy mix data, or specific company sustainability reports.
    *   **Curate Content:** Refine the prompts and data sources used by the RAG system for more accurate and relevant answers.
    *   **API Integrations:** Connect to external APIs for real-time data (e.g., public transport schedules, local recycling center updates, weather data for energy consumption estimates).

*   **AI Model & Logic:**
    *   **Fine-tuning:** If you have a large dataset of user interactions, consider fine-tuning an Azure OpenAI model for even more specialized coaching.
    *   **Agentic Behavior:** Enhance the LangChain agent to perform multi-step reasoning, such as planning a week's worth of low-carbon meals based on user preferences and available ingredients.
    *   **Different Models:** Experiment with different Azure OpenAI models (e.g., GPT-4 for more complex reasoning) or other LLM providers.

*   **User Interface & Experience:**
    *   **Advanced Visualizations:** Implement more sophisticated charts for tracking progress, comparing emissions across categories, and visualizing the impact of adopted habits.
    *   **Gamification Enhancements:** Develop a more robust points system, badges, and leaderboards. Introduce team-based challenges.
    *   **Personalization Options:** Allow users to set specific goals (e.g., "reduce commute emissions by 50%"), dietary preferences, or preferred communication styles for the AI coach.

*   **Backend Enhancements:**
    *   **User Authentication:** Integrate Azure AD B2C or other authentication providers for secure user accounts.
    *   **Database Optimization:** Use Azure Cosmos DB for more complex user data management and historical tracking.
    *   **Alerting:** Implement Azure Logic Apps or Azure Functions to send push notifications or emails for reminders, goal achievements, or new sustainability tips.

## 🤝 Contributing

We encourage contributions to EcoGuardian! Whether it's improving the AI's coaching capabilities, adding new data sources, enhancing the UI, or fixing bugs, your input is valuable.

Please refer to the `CONTRIBUTING.md` file for detailed guidelines on how to contribute, including:
*   Code of Conduct
*   How to report bugs
*   How to suggest features
*   Guidelines for submitting pull requests

## 📜 License

This project is licensed under the **MIT License**. See the `LICENSE` file for more details. This means you are free to use, modify, and distribute the code for both personal and commercial purposes, provided you include the original license and copyright notice.

---
