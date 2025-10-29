# Exercise 2 - Optional Parts: Adding further capabilities to the application

## Exercise 2.1 Use the attachments plugin


In this optional part of the tutorial, another feature of the CAP framework will be added to the application: With each incident, the user should have an option to add an attachment, for example, a photo the problem description. For this, additional logic and an additional UI section is needed to maintain and show attachments for each notification. 

SAP Build Code via CAP and SAP Fiori elements makes it easy to add this functionality:

1.    Open a new terminal by pressing the hamburger icon on the left side pane
2.    Select *Terminal*
3.    Select *New terminal*

![Terminal](images/terminal.png)

4.    In the terminal, add the statement

`npm add @cap-js/attachments`

5.    Press *return*.

![Npm](images/npm.png)

This will add a so-called *CAP plugin*, in this case one for attachment-handling. Behind the scenes, a dependency to this plugin will be added into the *package.json* file of the application and the plugin will be loaded.


6. Open Cline again and now the AI agent should extend the incidents entity with the following prompt:

```
Each Incidents should also be able to have several attachments. Use the installed plugin for that. Only update the schema.
```

7. What happened here? The Attachments plugin has been added to the file. As a last step, a new property needs to be created, called *attachments* here, which is a *Composition of Attachments.*

Your new schema.cds file should contain now these two line:

![schemaattachments](images/schemaattachments.jpg) 



Let’s have a look at the result:

8. If you have stopped the preview, press the green arrow on the upper right of the Storyboard again. If the preview is still running, the application should have refreshed itself.

9.    On the *Application Development Project Preview* page, press the tile *Incidents* again.

10. Create a new notification in your app by clicking *create* which you can find at the top right. You should now see a new attachment section in the application.

![attachmentsaddon](images/attachmentsaddon.jpg) 

New attachments can now be uploaded that will then appear in the list. You can also view them from that list. Each time creating a new incidents with a description, the attachments will be stored alongside the incdents.



## Exercise 2.2 Freestyle SAPUI5 Application

In addition to the SAP Fiori Elements to maintain the incidents, we would like to get some analytics on top of our incidents data. For example a freesytle SAPUI5 page that contains a chart that visualises the status of the incidents.

Of course you don't need to implement that manually. Try to ask Cline to perform that task for you.

But before extend the AI agents rules in Cline, with rules for UI5. Copy&paste the following rules into the Clines Global rules file called sap.md.

Maybe you remember that part from the first part of the exercise, what we have prepared already for you for CAP and Fiori Elements. 

```
## Guidelines for UI5

Use the `get_guidelines` tool of the UI5 MCP server to retrieve the latest coding standards and best practices for UI5 development.
```

</details>
<details>
<summary><b>Spoiler for an example prompt</b></summary>
```
Create a freestyle SAP ui5 application on top for the incidents for analytical purposes. Create a pie chart that visualises the sum of incidents per status.
```

</details>

## Summary

You've now extended the application with the capability to store attachments for the incidents.
