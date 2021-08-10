# Azure_Logic_Apps

Azure logic apps is a cloud service that helps us schedule, automate, and orchestrate tasks, business processes, and workflows when we need to integrate apps, data, systems, and services across enterprises and organizations.

**Scenarios for using Azure Logic Apps:-**

**Sending:-**
Sending E-mail notifications with an event happens.

**Monitoring:-**
Monitoring tweets with specific subjects, hashtags and creating alerts, tasks based on that.

**Moving:-**
Moving files uploaded to SFTP to Azure Storage.

**Building:-**
Building workflows and business processes.

**Data:-**
Perform data operations.

## Ways of controlling the flow:-

- Parallel Execution.

- Conditional Execution.
    - Conditions
    - Switches.

- Loops(Iterations).
    - For-each.
    - Until.

- Terminate.

- Scope.

### Parallel Execution:-

Split execution of our workflows into completely separate branches, each executed in parallel.

### Conditional Execution:-

- Conditions also split execution of our workflow into separate branches but only choose one of them depending on evaluation of specific conditions.

- While conditions split workflow into two branches, switch action can create multiple branches and choose one of them depending on condition.

### Loops (Iterations):-

When executing series of repeating actions, we can use:-
- For-each action which executes action for each time in a collection.
- Until action which runs until condition is met for scenarios when we can’t determine the amount of loops.

### Terminate:-

Terminate ends execution of the logic app on demand. Think of it like return in programming languages.

### Scope:-

Scope encapsulates execution of a set of workflows actions into a single block. This is our way of error handling in logic apps, think of it like try and catch block.



## Integration Account:-

An integration account is the Azure resource we create when we want to define and store B2B artifacts for use in our workflows. After we create and link an integration account to our logic app, our workflows can use these B2B artifacts. Our workflows can also exchange messages that follow Electronic Data Interchange (EDI) and Enterprise Application Integration (EAI) standards. For example, we can define trading partners, agreements, schemas, maps, and other B2B artifacts. We can create workflows that use these artifacts and exchange messages over protocols such as AS2, EDIFACT, X12, and RosettaNet.

## How Logic app works?

In a logic app, each workflow always starts with a single trigger. A trigger fires when a condition is met, for example, when a specific event happens or when data meets specific criteria. Many triggers include scheduling capabilities that control how often your workflow runs. Following the trigger, one or more actions run operations that, for example, process, handle, or convert data that travels through the workflow, or that advance the workflow to the next step. The following screenshot shows part of an example enterprise workflow. This workflow uses conditions and switches to determine the next action. Let's say we have an order system, and our workflow processes incoming orders. We want to review orders above a certain cost manually. Our workflow already has previous steps that determine how much an incoming order costs. So, we create an initial condition based on that cost value. For example:

- If the order is below a certain amount, the condition is false. So, the workflow processes the order.
- If the condition is true, the workflow sends an email for manual review. A switch determines the next step.
    - If the reviewer approves, the workflow continues to process the order.
    - If the reviewer escalates, the workflow sends an escalation email to get more information about the order.
        - If the escalation requirements are met, the response condition is true. So, the order is processed.
        - If the response condition is false, an email is sent regarding the problem.

We can visually create workflows using the Logic Apps designer in the Azure portal, Visual Studio Code, or Visual Studio. Each workflow also has an underlying definition that's described using JavaScript Object Notation (JSON). If we prefer, we can edit workflows by changing this JSON definition. For some creation and management tasks, Logic Apps provides Azure PowerShell and Azure CLI command support. For automated deployment, Logic Apps supports Azure Resource Manager templates.
 
## Why use logic apps?

The Logic Apps integration platform provides prebuilt Microsoft-managed API connectors and built-in operations so we can connect and integrate apps, data, services, and systems more easily and quickly. We can focus more on designing and implementing our solution's business logic and functionality, not on figuring out how to access your resources.

We usually won't have to write any code. However, if we do need to write code, we can create code snippets using Azure Functions and run that code from our workflow. We can also create code snippets that run in our workflow by using the Inline Code action. If our workflow needs to interact with events from Azure services, custom apps, or other solutions, we can monitor, route, and publish events using Azure Event Grid.

Logic Apps is fully managed by Microsoft Azure, which frees us from worrying about hosting, scaling, managing, monitoring, and maintaining solutions built with these services. When we use these capabilities to create "serverless" apps and solutions, we can just focus on the business logic and functionality. These services automatically scale to meet our needs, make integrations faster, and help us build robust cloud apps using little to no code.

## Twitter Sentiment Analysis using Logic Apps:-
### Pre requisites:-
- A Twitter Account.
- A microsoft azure account.
- A Resource group.
- A cognitive service.
- Text Analytics.
- Google Sheets.
- Cosmos DB.
- Blob Storage.
- Logic Apps.

So, to perform this task, the most important feature is a cognitive service and inside that, we need text analytics and it’s credentials such as keys and URLs to login into the account.
 
Azure cognitive service is the comprehensive family of AI services that helps us build intelligent apps. Cognitive services bring AI within the reach of every developer without requiring machine learning expertise.
 
### Create a logic app
1. From the top search box, search for and select Logic Apps.
2. Select Add.
3. Select Consumption and enter the following values.
4. Accept default values for all other settings.
5. Select Review + create.
6. Select Create.
7. Once the deployment is complete, select Go to Resource.
8. Select the Blank Logic App button.
9. Select the Save button on the toolbar to save our progress.

We can now use the Logic Apps Designer to add services and triggers to our application.

### Connect to Twitter
Create a connection to Twitter so our app can poll for new tweets.
1. Search for Twitter in the top search box.
2. Select the Twitter icon.
3. Select the When a new tweet is posted trigger.
4. Enter the values.
5. Select Sign in.
6. Follow the prompts in the popup window to complete signing in to Twitter. Next, enter the following values in the When a new tweet is posted box.
7. Select the Save button on the toolbar to save your progress.

Next, connect to text analytics to detect the sentiment of collected tweets.

### Add Text Analytics sentiment detection
1. Select New step.
2. Search for Text Analytics in the search box.
3. Select the Text Analytics icon.
4. Select Detect Sentiment and enter the values.
5. Select Create.
6. Click inside the Add new parameter box, and check the box next to documents that appear in the pop-up.
7. Click inside the documents Id - 1 textbox to open the dynamic content pop-up.
8. In the dynamic content search box, search for id, and click on Tweet id.
9. Click inside the documents Text - 1 textbox to open the dynamic content pop-up.
10. In the dynamic content search box, search for text, and click on Tweet text.
11. In Choose an action, type Text Analytics, and then click the Detect sentiment action.
12. Select the Save button on the toolbar to save your progress.

### Connect sentiment output to function endpoint
1. Select New step.
2. Search for Azure Functions in the search box.
3. Select the Azure Functions icon.
4. Search for your function name in the search box. If we follow the guidance above, our function name begins with TweetSentimentAPI.
5. Select the function icon.
6. Select the TweetSentimentFunction item.
7. Click inside the Request Body box, and select the Detect Sentiment score item from the pop-up window.Select the Save button.

### Add conditional step
1. Select the Add an action button.
2. Click inside the Control box, and search for and select Control in the pop-up window.
3. Select Condition.
4. Click inside the Choose a value box, and select the TweetSentimentFunction Body item from the pop-up window.
5. Enter Positive in the Choose a value box.
6. Select the Save button on the toolbar to save your progress.


## Implement RSS Feed:-

A workflow always starts with a single trigger, which specifies the condition to meet before running any actions in the workflow. Each time the trigger fires, the Logic Apps service creates and runs a workflow instance. If the trigger doesn't fire, no instance is created nor run. We can start a workflow by choosing from many different triggers.

This example uses an RSS trigger that checks an RSS feed, based on a schedule. If a new item exists in the feed, the trigger fires, and a new workflow instance starts to run. If multiple new items exist between checks, the trigger fires for each item, and a separate new workflow instance runs for each item.

1. In the Logic Apps Designer, under the search box, select All.
2. To find the RSS trigger, in the search box, enter rss. From the Triggers list, select the RSS trigger, When a feed item is published.
3. In the trigger details, provide the required informations.
4. Collapse the trigger's details for now by clicking inside its title bar.
5. When we're done, save your logic app, which instantly goes live in the Azure portal. On the designer toolbar, select Save.

The trigger won't do anything other than check the RSS feed. So, we need to add an action that defines what happens when the trigger fires.

### Add an action

Following a trigger, an action is a subsequent step that runs some operation in the workflow. Any action can use the outputs from the previous step, which can be the trigger or another action. We can choose from many different actions, add multiple actions up to the limit per workflow, and even create different action paths.
This example uses an Office 365 Outlook action that sends an email each time that the trigger fires for a new RSS feed item. If multiple new items exist between checks, we receive multiple emails.

1. Under the When a feed item is published trigger, select New step.
2. Under Choose an operation and the search box, select All.
3. In the search box, enter send an email so that we can find connectors that offer this action. To filter the Actions list to a specific app or service, select that app or service first.

For example, if we have a Microsoft work or school account and want to use Office 365 Outlook, select Office 365 Outlook. Or, if we have a personal Microsoft account, select Outlook.com. This example continues with Office 365 Outlook.

4. We can now more easily find and select the action that we want, for example, Send an email.
5. If our selected email service prompts us to sign in and authenticate your identity, complete that step now.

Many connectors require that we first create a connection and authenticate our identity before we can continue.

### Run our workflow

To check that the workflow runs correctly, we can wait for the trigger to check the RSS feed based on the set schedule. Or, we can manually run the workflow by selecting Run on the Logic Apps Designer toolbar.

If the RSS feed has new items, our workflow sends an email for each new item. Otherwise, our workflow waits until the next interval to check the RSS feed again.

##### Links for Twitter Sentiment Analysis:-
1. https://www.youtube.com/watch?v=x5p6x9lpuYc
2. https://www.youtube.com/watch?v=NdemMu5kr-o

##### Links for RSS Feed:-
https://www.youtube.com/watch?v=gTePawo6xok
		








