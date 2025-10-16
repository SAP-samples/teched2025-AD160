# Exercise 2 - Exercise 2 Description

BACKUP not needed anymore

## Exercise 2.1 Github Copilot setup

Install Github Copilot?
In Github Copilot install MCP server.
Configure your MCP:
·         Open Copilot Chat from the chat icon at the top.
·         Go to “Configure Tools” and enter your MCP details:

![configureTools](images/configureTools.png) 

Select the MCP server type **NPM Package**

![MCPtype](images/MCPtype.jpg) 

Insert the NPM Package Name **@cap-js/mcp-server** 

![NPMpackage](images/NPMpackage.jpg) 

Allow the installation by selecting **Allow**

![allowInstall](images/allowInstall.jpg) 

Provide the server ID **cap-mcp**

![serverID](images/serverID.jpg) 

Select **Workspace** as MCP sever install location.

![MCPLocation](images/MCPLocation.jpg) 


## Exercise 0.3 Installation of an AI Agent

In this exercise we will use Cline, an Autonomous coding agent, which can be added to your IDE. If you want to find out more information about Cline, click here [Cline Github](https://github.com/cline/cline)

To save some time in this hands-on, we already set up Cline with an SAP AI Core integration in SAP Build Code. If you want to set it up after this hands-on on your maschine, you will find the documentation here: [Cline + SAP AI Core](https://architecture.learning.sap.com/docs/ref-arch/e5eb3b9b1d/10)


## Exercise 0.3 Add instructions to the AI agents
To ensure that the AI produces correct results, we propose rules that guide the LLM’s behavior. For example for in the CAP MCP server, we define that the mcp server is always used when it searches for CDS definitions.
We are now defining rules to help the LLM use the server correctly. In Github Copilot these rules are called instructions:

On the top right side in the AI chat panel, open the seetings by clicking the gearwheel icon and select instructions.

![addInstruction](images/addInstruction.jpg) 

Select new instructions file.

![newInstructionFile](images/newInstructionFile.jpg) 

Select .github/instructions as instruction folder.

![instructionFolder](images/instructionFolder.jpg) 

Name it **rules**.

![instructionName](images/instructionName.jpg) 

Replace line 4 with the following text:
- You MUST search for CDS definitions, like entities, fields and services (which include HTTP endpoints) with cds-mcp, only if it fails you MAY read \*.cds files in the project.
- You MUST search for CAP docs with cds-mcp EVERY TIME you create, modify CDS models or when using APIs or the `cds` CLI from CAP. Do NOT propose, suggest or make any changes without first checking it.

Your file should look like this:

![instructionFile](images/instructionFile.jpg) 


Now we have completed the setup for CAP, but we also want to have a specialized agent for SAP Fiori Elements.
Try to add the fiori-mcp-server in the same way like the cap mcp server.
You can find the necessary details here: https://www.npmjs.com/package/@sap-ux/fiori-mcp-server
If you want to learn more  after the workshop, have a look here [SAP Fiori Elements MCP server](https://community.sap.com/t5/technology-blog-posts-by-sap/sap-fiori-tools-update-first-release-of-the-sap-fiori-mcp-server-for/ba-p/14204694)


## Exercise 1.1

**Aditional allinoneprompt DELETE IF NOT NEEDED**
 Application Details: Application will be used to manage incidents. Each incident will have priority and status to indicate importance of it. Incident can also be updated with comments to indicate progress. afterwards generate the UI. I don't want to deploy it to sap hana, for now only want to test it locally.

At first, the project will be empty. Next step is to create a CAP (Cloud Application Programming) data model and a service for the incidents. This can either be done manually or with the help of Joule, the digital assistant. 


Open the Terminal and run **cds init** in the beginning manually. It initializes a new project in folder ./<project>, with the current working directory as default.

Open the business partner API: https://api.sap.com/api/API_BUSINESS_PARTNER/overview

Click on **API Specification** and download odata.edmx. 

copy&paste the file in the folder. Afterwards run the following command in the Terminal:

```
cds import API_BUSINESS_PARTNER.edmx --as cds
```

Now the Business Partner is added as external service. Your project should look like this:

![Business Partner](images/businesspartner.jpg) 


**Necessary? Need to be checked**
We have a destination defined in our SAP BTP acoount with already access to the S4HC and exposed the business partner scenario. I would like to test locally by using this destination and my new project. Let’s then correct and add new information with my prompt.

```I would like you check the package.json and prepare the project for deploy and test locally. I have a BTP destination ready and connected with name API_BUSINESS_PARTNER_CC7
```

**Necessary? Need to be checked**
Step 5 — Prep for local testing with a Destination
The BTP Destination named API_BUSINESS_PARTNER_CC7 that points to the S/4HANA Business Partner API.

Add the MTA file and the destination configuration (to connect to the system). **Should we do that with AI?**

```
cds add mta;cds add xsuaa,destination,connectivity;
```


**old remove**
```
create a CAP application for managing customer support incidents:

•               Incidents are reported by Customers and contain details like title, urgency, status, and a conversation log (messages with timestamps and authors).              
•               Customers have personal/contact information and a list of their incidents and addresses.
•               Addresses are related to Customers and store location details.
•               Status and Urgency are code lists, enumerating possible incident states (new, assigned, etc.) and urgency levels (high, medium, low).
Create only the data model, sample data and service. use cds-mcp. use cds init incients to create the project.
```

## Optional BAS Config
for Cline


{
  "mcpServers": {
    "cds-mcp": {
      "disabled": false,
      "timeout": 60,
      "type": "stdio",
      "command": "node",
      "args": [
        "/home/user/.node_modules_global/lib/node_modules/@cap-js/mcp-server/index.js"
      ],
      "env": {
        "PATH": "/home/user/.asdf/bin:"
      }
    },
    "fiori-mcp": {
      "disabled": false,
      "timeout": 60,
      "type": "stdio",
      "command": "node",
      "args": [
        "/home/user/.node_modules_global/lib/node_modules/@sap-ux/fiori-mcp-server/dist/index.js"
      ],
      "env": {
        "PATH": "/home/user/.asdf/bin:"
      }
    },
    "ui5-mcp": {
      "disabled": false,
      "timeout": 60,
      "type": "stdio",
      "command": "node",
      "args": [
        "/home/user/.node_modules_global/lib/node_modules/@ui5/mcp-server/bin/ui5mcp.js"
      ],
      "env": {
        "PATH": "/home/user/.asdf/bin:"
      }
    }
  }
}


1.    Open a new terminal by pressing the hamburger icon on the left side pane
2.    Select *Terminal*
3.    Select *New terminal*

![Terminal](images/terminal.png)

4. enter **cds watch** and press enter to start a preview of the service:
```
cds watch
```

2. Click on **http://localhost:4004** in the terminal to open the preview


## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)


    - [Exercise 1.1 - Exercise 1 Sub Exercise 1 Description](exercises/ex1#exercise-11-sub-exercise-1-description)
    - [Exercise 1.2 - Exercise 1 Sub Exercise 2 Description](exercises/ex1#exercise-12-sub-exercise-2-description)
- [Exercise 2 - Second Exercise Description](exercises/ex2/)
    - [Exercise 2.1 - Exercise 2 Sub Exercise 1 Description](exercises/ex2#exercise-21-sub-exercise-1-description)
    - [Exercise 2.2 - Exercise 2 Sub Exercise 2 Description](exercises/ex2#exercise-22-sub-exercise-2-description)