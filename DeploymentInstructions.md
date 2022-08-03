# Story STRY0858959 Deployment Instructions

## Pre-Deployment Steps

1. Open VS Code
2. Run the following command in the terminal to download the source code to a local repository:

        git clone https://github.com/jdrussett/flood_sub_route_project.git [directory location]

    > Where `directory location` is an optional location you can specify where you want the project to install

3. You should now see the project appear in your file explorer/directory in VS Code. Confirm that the folder structure contains the force-app folder with several subfolders, as well as the data folder which contains several json files
4. Ensure that your terminal directory is based within the project folder that was just installed.
5. Run the following command in the terminal to authenticate FNBO's salesforce production org if you haven't done so previously:

        sfdx force:auth:web:login --instanceurl https://fnni.my.salesforce.com --setalias production

    > Supply your production org credentials to log in when the browser window launches. If you are asked to change your password, try closing the tab, signing into production with Okta in a different tab to instantiate a session within the browser, then re-run the command in VS Code and it should skip the login verification page. Click "Allow" at the next screen asking you to allow VS Code and the Salesforce CLI to access org data and metadata.

6. You should see a success message in the terminal after running the command if the authentication command was successful

## Deployment Steps

1. In VS Code, with the terminal location at the root folder of the project you downloaded locally in the pre-deployment steps section, run the following command:

        sfdx force:data:tree:import --targetusername production --plan data/datamapping-plan.json

2. If the command executes successfully, you should see about two dozen import result records populate in the terminal window.
3. In Salesforce, check the loan compliance route on the loan UI for a booked and open loan, and verify that the flood questionnaire sub-route was added to the end of the route. Confirm that the questions render appropriately depending on the answers you select and no errors result in the UI.
