## Objective
The objective of this repository is to set up a continuous integration and continuous deployment (CI/CD) pipeline for a Node.js application that is deployed on a serverless platform. Next, using a third-party monitoring tool SenseDeep on monitoring the function and health on this serverless
application.

## Step 1: Create a code repository in GitHub
Create via github account 
<img width="948" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/d9709a6c-1013-46f7-9fa5-1f703b4abda0">


## Step 2: Clone the code repository into local machine
Clone by the following command on visual studio code - PS C:\> git clone https://github.com/flowstarts2020/SaleSpheres.git



## Step 3: Create index.js file
Example of an index.js file which was done via visual studio code


module.exports.handler = async (event) => {
  const respose = {
    "timestamp": Date.now().toString(),
    "status_code": 200,
    "body": "body"
  }
  console.log(respose)
  return {
    statusCode: 200,
    body: JSON.stringify(
      {
        message: "Go Serverless v3.0! Your function executed successfully!",
        input: respose,
      },
      null,
      2
    ),
  };
};

module.exports.error = async (event) => {
  const respose = {
    "timestamp": Date.now().toString(),
    "status_code": 400,
    "body": "body error"
  }

  const err = new Error(respose)
  
  return {
    statusCode: 400,
    body: JSON.stringify(
      {
        message: "error",
        input: err.message.body,
      },
      null,
      2
    ),
  };
};

## Step 4: Create serverless.yml
Example of a serverless.yml file which was done via visual studio code

 salesphere
service: salesphere
frameworkVersion: '3'

provider:
  name: aws
  runtime: nodejs18.x
  region: ap-southeast-1

functions:
  api:
    handler: index.handler
    events:
      - httpApi:
          path: /
          method: get

  error:
    handler: index.error
    events:
      - httpApi:
          path: /error
          method: get

plugins:
  - serverless-offline


## Step 5: Deploy and verify that the serverless application is working
Test and execute the following commands
$ npm install
```
and then deploy with:
```
$ serverless deploy
## Step 6: Create CI/CD pipeline with GitHub Actions
Create main.yml in .github/workflows folder. 
## Step 7: Add AWS_ACCESS_KEY_ID and ASW_SECRET_ACCESS_KEY to GitHub Secrets
Always keep AWS_ACCESS_KEY_ID and ASW_SECRET_ACCESS_KEY in privately. They are not meant to share or let public known for prevention of data breaches and landed to the wrong hands (hackers)

<img width="937" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/1988e2c1-64b2-48b7-975d-311a67cfac09">



## Step 8: Push changes to GitHub to start the workflow
Commit changes locally and push it to GitHub. Navigate the repo on GitHub, click on the **Actions** tab to see the workflows.
Confirm all tests passed and without errors
<img width="945" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/d2b06c16-74ae-4997-92a8-32757c41c9c5">



## Step 9: Access AWS Console to check the Lambda application (on salesphere-dev-api and SalesSphere-dev-error)
<img width="929" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/dba74c5d-a2a1-4d9f-937a-d9bf41634116">

## Step 10: Test many times to Invoke the Lambda application
<img width="947" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/f2f2dd6f-4c7d-4bcd-aa2c-ec9fea658d7f">

Go to the test and click 

<img width="942" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/110de353-198f-4ec4-83a2-6843a56ba173">

Click a few times on the orange test box to invoke 

(for both on salesphere-dev-api and SalesSphere-dev-error)

## Step 11: Check any readings when monitoring the Lambda application
<img width="950" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/7c712c84-de40-4beb-b0b2-3eb59d22b04d">


<img width="938" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/2ded59e6-8665-443c-8ade-a3aea91eabe7">

## Step 12: Access and login SenseDeep application
https://www.sensedeep.com/ can be register for free. For this project, we will access as a free account
Do go to this link https://www.sensedeep.com/doc/kb/starting/setup.html on how to register and setup

## Step 13: Create the widgets of graph views on SUM and Average for the related relevant monitoring Lambda application
illustrating one screenshot example of a SUM widget on salesphere-dev-api
<img width="949" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/72a9ae95-8587-4a95-a85e-7074d849ec03">



## Step 14: Completion on ready to view centralize Dashboard   
This is the illustration of a detail widget based on SUM and Average hourly on salesphere-dev-api and SalesSphere-dev-error. SALESPHERES DASHBOARD
<img width="950" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/178e7d30-f880-4a03-9fed-0bd36e3df256">


