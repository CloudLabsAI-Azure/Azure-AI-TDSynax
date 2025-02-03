# Lab 6: Getting Started with Building a Chat Application

### Estimated Duration: 30 minutes

Building a chat application involves designing the user interface for seamless communication, implementing backend services for real-time message handling, and integrating with databases for storing chat histories, while ensuring robust security and scalability to handle user interactions effectively.In this lab, you will be setting up the Open AI resource and installing the application locally.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1: Building a ChatGPT-like application on Streamlit with streaming

### Task 1: Create an OpenAI resource and model

**Azure OpenAI**: Azure OpenAI Service is a cloud-based platform that provides access to OpenAI’s powerful language models, including GPT-4, GPT-3.5, Codex, and DALL-E12. This service allows developers to integrate these models into their applications for tasks such as content generation, summarization, semantic search, and natural language to code translation3.

Refer to the link for more information. [Azure OpenAI](https://learn.microsoft.com/en-us/azure/ai-services/openai/overview)

In this task, you will learn to create an Azure OpenAI resource in the Azure portal, configure its settings, and deploy the GPT-4 model in Azure AI Studio. This involves setting up the resource, navigating to Azure AI Studio, and specifying model deployment details.

1. In the Azure portal, search for **OpenAI (1)** in the top search box, then select **Azure OpenAI (2)** under services.

   ![](../media/openai8.png "Azure OpenAI")

1. From the **Azure AI Services | Azure OpenAI** pane, select **OpenAI-Lab01-<inject key="Deployment ID" enableCopy="false"/>**.

   ![](../media/openai12.png "Azure OpenAI")
   
1. In the Azure OpenAI resource pane, click on **Go to Azure AI Foundry portal** to navigate to the Azure AI Studio, where you can further configure and use your OpenAI models.

   ![](../media/azureaifoundryportal.png "Azure OpenAI")

1. In the left navigation pane, click on **Deployments (1)**, then click on **+ Deploy model** **(2)**. Select **Deploy base Model (3)** from the options presented.

   ![](../media/deploybasemodel.png)

1. In the **Select a model** window, choose **gpt-4 (1)** from the available options, and then click on **Confirm (2)** to proceed with the model selection.

   ![](../media/new11.png)
   
1. On the **Deploy Model** tab, input the required details such as Deployment name, Model version, Deployment type, Tokens per Minute Rate Limit, and enable dynamic quota. Once all fields are filled, Click on **Deploy** (6).

   | Setting  | Value |
   -----------|---------
   | Deployment name | **copilot-gpt (1)** |
   | Model version | **turbo-2024-04-09 (2)** |
   | Deployment type | **Standard (3)** |
   | Tokens per Minute Rate Limit (thousands) | **15K (4)** |
   | Enable dynamic quota | **Enabled (5)** |

   ![](../media/new99.png)

1. In the left navigation pane, click on **Deployments (1)**, then click on **+ Deploy model** **(2)**. Select **Deploy base Model (3)** from the options presented.

   ![](../media/deploybasemodel.png)

1. In the **Select a model** window, choose **text-embedding-ada-002 (1)** from the available options, and then click on **Confirm (2)** to proceed with the model selection.

1. On the **Deploy Model** tab, input the required details such as Deployment name, Model version, Deployment type, Tokens per Minute Rate Limit, and enable dynamic quota. Once all fields are filled, Click on **Deploy**.

   | Setting  | Value |
   -----------|---------
   | Deployment name | **CompletionModel** |
   | Model version | **2 (Default)** |
   | Deployment type | **Standard** |
   | Tokens per Minute Rate Limit (thousands) | **15K (4)** |
   | Enable dynamic quota | **Enabled (5)** |
   
### Task 2: Building a ChatGPT-like application on Streamlit with streaming  

In this task, you will set up an Azure OpenAI resource, deploy models like GPT-4, and integrate the required API keys. After configuring the application with these details, you will run and test a ChatGPT-like app to verify its functionality, demonstrating how to use Azure OpenAI models in a practical application.

1. In the **Azure AI Foundry** portal, select **Deployments (1)** under **Shared resources** and verify that the **gpt-4** and **text-embedding-ada-002** models are present with the deployment names as **copilot-gpt** and **CompletionModel**. Review that the model's capacity is set to **15K TPM**.
   
   ![](../media/deploymentsmodel.png)

1. Navigate back to the Azure OpenAI resource on the **Azure portal**, select **Key & Endpoint (1)** from the left menu under **Resource Managemant**, and click on **Show Keys (2)**. Note the **KEY 1 (3)** and **Endpoint (4)**.

   ![](../media/keysandendpoint.png "Azure OpenAI")
   
   > **Note**: Steps 5 through 8 demonstrate where to obtain the values used in the configuration.

1. Navigate back to **Azure OpenAI**, select **AI search (1)** from the left menu, and click on **aiinaday-cog-<inject key="Deployment ID" enableCopy="false"/> (2)**.

   ![](../media/aiinaday.png "Azure OpenAI")

1. From the Overview tab of Cognitive Search, Note the **URL**.

   ![](../media/aiinaday-01.png "Azure OpenAI")

1. From the left menu, select **Key (1)** under **Settings**, Note the **Primary admin key (2)**.

   ![](../media/keys.png "Azure OpenAI")

1. In the LabVM, open File Explorer, navigate to the below-mentioned path, right-click on the `secrets.env` file, and select open with  **Visual Studio Code**.

   ```
   C:\LabFiles\OpenAIWorkshop\scenarios\incubations\copilot\ChatGPT
   ```

    ![](../media/img67.png)

1. In the `secrets.env` file, replace the following values. Press **CTRL+S** to save the file.

      | **Variables**                     | **Values**                                                    |
      | --------------------------------- |---------------------------------------------------------------|
      | **AZURE_OPENAI_API_KEY**          | Paste the key that you copied in the previous step.              |
      | **AZURE_OPENAI_CHAT_DEPLOYMENT**        | Replace the value with your **YOUR_GPT_MODEL** name that is  **copilot-gpt**          |
      | **AZURE_OPENAI_ENDPOINT** | Paste the endpoint that you copied in the previous step.        |

      ![](../media/img68.png)

      > **Note :** If you're unable to see the full **Values** section in the table, click on the three dots (ellipsis) in the top right corner of your browser and try reducing the zoom level for better visibility.
         
      ![](../media/zoom.png)

1. Navigate back to File Explorer and open `chatgpt.py` with **Visual Studio Code** to view the code to build a ChatGPT-like app.

    ![](../media/img70.png) 
 
1. Next, click on the **Eclipse Button** at the top of the screen, then select **Terminal** from the dropdown menu and click on **New Terminal** to open a new terminal window.

    ![](../media/img69.png) 


1. Run the following command in the terminal to change the directory:

      ```
      cd C:\LabFiles\OpenAIWorkshop\scenarios\incubations\copilot\ChatGPT
      ```
   
1. To run the application from the command line, enter the following command in the terminal:

      > **Note**: You can enter your email address below to get notifications. If not, please leave this field blank and click on **Enter**.

      ```
      streamlit run chatgpt.py
      ```
   
1. Once the command `streamlit run chatgpt.py` has executed, a demo application will be launched and opened in your web browser, hosted locally on your machine.

      ![](../media/img71.png "Azure OpenAI")
      
      ![](../media/img72.png "Azure OpenAI")

1. Explore the app by running a few queries. Congratulations! You've built your own ChatGPT-like application in 50 lines of code.

      ![](../media/img73.png "Azure OpenAI")

   > **Note**: You may get a different response. please note chatgpt uses LLM and responses may vary everytime.
  
1. Navigate back to **VS Code** and stop the terminal by typing **ctrl + C**.

1. Click the **Next** button located in the bottom right corner of this lab guide to continue with the next exercise.

## Summary

In this lab, you set up an Azure OpenAI resource and model, and built a ChatGPT-like application using Streamlit. You navigated the Azure portal to create and configure your OpenAI resource, verified model deployments, and gathered the necessary API keys and endpoints. After configuring your application with these details, you ran and tested it locally, successfully creating a functional ChatGPT-like app. This process demonstrated the integration of Azure OpenAI models into a practical application, showcasing the steps to build and deploy AI-driven chat functionalities.

### You have successfully completed the lab. Click Next >> to move on to the next set of exercises.