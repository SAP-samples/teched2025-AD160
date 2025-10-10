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


## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
