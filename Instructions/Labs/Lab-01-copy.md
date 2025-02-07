# Lab 1: Get started with Azure OpenAI Service

## Lab Scenario
Azure OpenAI Service brings the generative AI models developed by OpenAI to the Azure platform, enabling you to develop powerful AI solutions that benefit from the security, scalability, and integration of services provided by the Azure cloud platform. In this exercise, you'll learn how to get started with Azure OpenAI by provisioning the service as an Azure resource and using Azure OpenAI Studio to deploy and explore OpenAI models.

## Lab Objectives
In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Explore a model in the Completions playground
- Task 4: Use the Chat playground
- Task 5: Explore prompts and parameters 
- Task 6: Explore code-generation

## Estimated time: 60 minutes

## Task 1: Provision an Azure OpenAI resource

In this task , you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/tel-11.png)

2. On **Azure AI Services | Azure OpenAI** blade, click on **Create**.

   ![](../media/tel-10.png)

3. Create an **Azure OpenAI** resource with the following settings:
   
    - **Subscription (1)**: Default - Pre-assigned subscription.
    - **Resource group (2)**: AzureAIrg
    - **Region (3)**: Keep it as default
    - **Name (4)**: OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Pricing tier (5)**: Standard S0
  
      ![](../media/azureopenai.png "Create Azure OpenAI resource")

4. Click on **Next (6)** by keeping others default and click on **Create**.

      >**Note:** Wait for the deployment to complete. 

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Click on the **Validate** button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at **cloudlabs-support@spektrasystems.com**. We are available 24/7 to help you out.

<validation step="5c3a40bc-ff54-4936-a729-e6248b25a8e1" />

## Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/tel-11.png)

2. On **Azure AI Services | Azure OpenAI** blade, select **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/tel-1.png)

3. In the Azure OpenAI resource pane, click on **Go to Azure AI Foundry portal** it will navaigate to **Azure AI Foundry portal**.

   ![](../media/azureaifoundry.png)


5. From the left navigation pane, select the **Deployments (1)**, click on **+ Deploy model** , Choose **Deploy base Model (2)**.

      ![](../media/ui1.png "Create a new deployment")

6. Search for **gpt-35-turbo**, click on **Confirm**

   ![](../media/pg-09.jpg)
   
7. Within the **Deploy model** pop-up interface, enter the following details:
      - **Deployment name**: my-gpt-model (1)
      - **Deployment type**: Standard (2)
      - Select **Customize**
      - **Model version**: 0301 (3)
      - **Tokens per Minute Rate Limit (thousands)**: 10K (4)
      - **Enable dynamic quota**: Enabled (5)
      - Click on **Deploy** (6)
  
         ![](../media/gpt-35-turbo.png)

         >**Note** : gpt-35-turbo-16k is supported only for chat completions and it is not supported for completions API.

8. This will deploy a model which you will be playing around with as you proceed.

      > **Note**: You can ignore any error related to assignment of roles to view the quota limits. 
   
      > **Note**: Azure OpenAI includes multiple models, each optimized for a different balance of capabilities and performance. In this exercise, you'll use the **GPT-35-Turbo** model, which is a good general model for summarizing and generating natural language and code. For more information about the available models in Azure OpenAI, see [Models](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) in the Azure OpenAI documentation.

   
> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Click on the **Validate** button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at **cloudlabs-support@spektrasystems.com**. We are available 24/7 to help you out.

<validation step="a9d5d237-cf45-4f57-9738-7c69af5faad5" />


## Task 3: Explore a model in the Completions playground

In this task ,You'll Explore a model in the Completions playground involves interacting with the AI model to test and refine its responses using real-time input and output examples.

1. In Azure AI Foundry Studio, in the left pane under **Playground**, select **Completions**.

1. In the **Completions (1)** page, ensure your **my-gpt-model (2)** deployment is selected , Type `Generate a quiz of 5 questions  For each question, provide me the answer options and the correct answer` **(3)** in the prompt.

      >**Note:** The summarize text sample consists of a *prompt* that provides some text to tell the model what kind of response is required and include some contextual information.

1. At the bottom of the page, note the number of *tokens* detected in the text. Tokens are the basic units of a prompt - essentially words or word-parts in the text.

1. Use the **Generate (4)** button to submit the prompt to the model and retrieve a response (you may need to scroll down). The response consists of a quiz based on the example in the prompt.

      ![](../media/prompt.png)

      ![](../media/generateaquiz.png)

      >**Note**: The output you receive might differ on your system, but it must follow this format for the subsequent steps to proceed.

1. Use the **View Code** button to view the code that a client application would use to submit the prompt. You can select your preferred programming language. The prompt contains the text you submitted to the model. The request is submitted to the *Completions* API for your Azure OpenAI service.

      ![](../media/viewcode1.png)

      ![](../media/openaicode.png)
    
1. Close the **Sample Code**.

## Task 4: Use the Chat playground

In this task, you'll use the Chat playground to interact with and test the AI model's conversational abilities through a simulated chat interface.

1. In the **Playgrounds** section, select the **Chat** page, and ensure that the **my-gpt-model (1)** model is selected in the configuration pane.

2. In the **Setup** section, in the **Give the model instructions and context** box, replace the current text with the following statement: `The system is an AI teacher that helps people learn about AI` **(2)**.

3. Select the **+ Add section (3)** box, click on **Examples (4)**. enter the following message and response in the designated boxes:

      ![](../media/gpt-model.png)

4.  Enter the following message and response in the designated boxes:

      - **User**: `What are different types of artificial intelligence?`
      - **Assistant**: `There are three main types of artificial intelligence: Narrow or Weak AI (such as virtual assistants like Siri or Alexa, image recognition software, and spam filters), General or Strong AI (AI designed to be as intelligent as a human being. This type of AI does not currently exist and is purely theoretical), and Artificial Superintelligence (AI that is more intelligent than any human being and can perform tasks that are beyond human comprehension. This type of AI is also purely theoretical and has not yet been developed).`

         ![](../media/exples-ai.jpg)
   
         > **Note**: Few-shot examples are used to provide the model with examples of the types of responses that are expected. The model will attempt to reflect the tone and style of the examples in its own responses.

5. Save the changes by clicking on **Apply changes**.

   ![](../media/applychanges1.png)

   >**Note:** On the **Update system message?**, select **Continue**.
   
6. In the query box at the bottom of the page, enter the text `What is artificial intelligence?`. Use the **Send** button to submit the message and view the response.

      ![](../media/openai-12.png)
   
      > **Note**: If you receive a response that the API deployment is not yet ready, wait for a few minutes and try again.

7. Review the response and then submit the following message to continue the conversation: `How is it related to machine learning?`

8. Review the response, noting that context from the previous interaction is retained (so the model understands that "it" refers to artificial intelligence).

9. Use the **View Code** button to view the code for the interaction. The prompt consists of the *system* message, the few-shot examples of *user* and *assistant* messages, and the sequence of *user* and *assistant* messages in the chat session so far.
            
      ![](../media/viewcodes.png)

## Task 5: Explore prompts and parameters

In this task, you'll explore prompts and parameters by experimenting with different inputs and settings to fine-tune the AI model's responses and behavior.

1. In the **Chat Configuration** pane, expand **Parameters (1)**, set the following parameter values:
      
      - **Max response (2)**: 500

      - **Temperature (3)**: 0

         ![](../media/parameters.png)
      
2. Submit the following message in chat session

      ```
      Write three multiple choice questions based on the following text.

      Most computer vision solutions are based on machine learning models that can be applied to visual input from cameras, videos, or images.*

      - Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on.*

      - Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use object detection to identify the location of different classes of vehicle.*

      - Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution might overlay traffic images with "mask" layers to highlight different vehicles using specific colors.
      
      ```

3. Review the results, which should consist of multiple-choice questions that a teacher could use to test students on the computer vision topics in the prompt. The total response should be smaller than the maximum length you specified as a parameter.

      ![](../media/classification.png)

      >**Note:** The output you receive might differ on your system, but it must follow this format for the subsequent steps to proceed.
   
4. Observe the following about the prompt and parameters you used:

    - The prompt specifically states that the desired output should be three multiple choice questions.
       
    - The parameters include *Temperature*, which controls the degree to which response generation includes an element of randomness. The value of **0** used in your submission minimizes randomness, resulting in stable, predictable responses.

## Task 6: Explore code-generation

In this task, you'll explore code-generation by testing the AI model’s ability to generate and suggest code snippets based on various programming prompts and requirements.

1. In the **Setup** pane, enter the message: `You are a Python developer.` under **Give the model instructions and context** and save the changes by clicking on **Apply changes** when prompted click on **Continue**.

2. In the **Chat session** pane, select **Clear chat** to clear the chat history and start a new session.

      ![](../media/clear-chat.png)

3. Submit the following user message:

      ```
      Write a Python function named Multiply that multiplies two numeric parameters.
      ```

4. Review the response, which should include sample Python code that meets the requirement in the prompt.
   
      ![](../media/writeapython.png)

5. Close the **Azure AI Foundry Portal**.

## Summary

In this lab, you have accomplished the following:
-   Provision an Azure OpenAI resource
-   Deploy an Azure OpenAI model within the Azure OpenAI studio
-   Use the chat playground to utilize the functionalities of prompts, parameters and code-generation

#### You have successfully completed the lab. Click Next >> to move on to the next set of exercises.