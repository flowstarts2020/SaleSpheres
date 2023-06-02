## Objective
The objective of this repository is to set up a continuous integration and continuous deployment (CI/CD) pipeline for a Node.js application that is deployed on a serverless platform. Next, using a third-party monitoring tool SenseDeep on monitoring the function and health on this serverless
application.

## Step 1: Create a code repository in GitHub
## Step 2: Clone the code repository into local machine
## Step 3: Create index.js file
## Step 4: Create serverless.yml
## Step 5: Deploy and verify that the serverless application is working
## Step 6: Test and execute the following commands
$ npm install
```
and then deploy with:
```
$ serverless deploy
## Step 7: Create CI/CD pipeline with GitHub Actions
Create main.yml in .github/workflows folder. 
## Step 8: Add AWS_ACCESS_KEY_ID and ASW_SECRET_ACCESS_KEY to GitHub Secrets
## Step 9: Push changes to GitHub to start the workflow
Commit changes locally and push it to GitHub. Navigate the repo on GitHub, click on the **Actions** tab to see the workflows.
## Step 10: Access AWS Console to check the Lambda application (on salesphere-dev-api and SalesSphere-dev-error)
<img width="929" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/dba74c5d-a2a1-4d9f-937a-d9bf41634116">

## Step 11: Test many times to Invoke the Lambda application
<img width="947" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/f2f2dd6f-4c7d-4bcd-aa2c-ec9fea658d7f">
Go to the test button 

<img width="942" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/110de353-198f-4ec4-83a2-6843a56ba173">



(for both on salesphere-dev-api and SalesSphere-dev-error)

## Step 12: Check any readings when monitoring the Lambda application
<img width="950" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/7c712c84-de40-4beb-b0b2-3eb59d22b04d">

<img width="938" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/2ded59e6-8665-443c-8ade-a3aea91eabe7">

## Step 13: Access and login SenseDeep application
https://www.sensedeep.com/ can be register for free. For this project, we will access as a free account
Do go to this link https://www.sensedeep.com/doc/kb/starting/setup.html on how to register and setup

## Step 14: Create the widgets of graph views on SUM and Average for the related relevant monitoring Lambda application
illustrating one screenshot example of a SUM widget on salesphere-dev-api
<img width="949" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/72a9ae95-8587-4a95-a85e-7074d849ec03">



## Step 15: Completion on ready to view centralize Dashboard   
This is the illustration of a detail widget based on SUM and Average hourly on salesphere-dev-api and SalesSphere-dev-error. SALESPHERES DASHBOARD
<img width="950" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/178e7d30-f880-4a03-9fed-0bd36e3df256">


