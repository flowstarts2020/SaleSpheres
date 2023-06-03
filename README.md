## Objective
The objective of this repository is leverage a Node.js application that is deployed on a serverless platform and developed a centralised application platform dashboard.  This dashboard is using a third-party monitoring tool SenseDeep as well as CloudWatch on monitoring the function and health on this serverless application.

## Step 1: Create a code repository in GitHub
Create via github account 
<img width="948" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/d9709a6c-1013-46f7-9fa5-1f703b4abda0">


## Step 2: Clone the code repository into local machine
Clone by the following command on visual studio code - PS C:\> git clone https://github.com/flowstarts2020/SaleSpheres.git



## Step 3: Using an index.js file
Example of an index.js file which was done via visual studio code

```
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
```
## Step 4: using a serverless.yml
Example of a serverless.yml file which was done via visual studio code
```
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
```

## Step 5: Deploy and verify that the serverless application is working
Test and execute the following commands
$ npm install
```
and then deploy with:
```
$ serverless deploy
## Step 6: Run and test with GitHub Actions
Create main.yml in .github/workflows folder. 
An example of a main.yml
```
name: CICD for Serverless Application
run-name: ${{ github.actor }} is doing CICD for Serverless Application

on:
  push:
    branches:  [ main, "*"]

jobs:
  pre-deploy:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event"
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."

  install-dependencies:
    runs-on: ubuntu-latest
    needs: pre-deploy
    steps:
      - name: Check out repository code
        uses: actions/checkout@v3
      - name: Run Installation of Dependencies Commands
        run: npm install

  scan-dependencies:
    runs-on: ubuntu-latest
    needs: install-dependencies
    steps:
      - name: Check out repository code
        uses: actions/checkout@v3
      - name: Run Scanning of Dependencies Commands
        run: npm audit

  deploy:
    name: deploy
    runs-on: ubuntu-latest
    needs: install-dependencies
    strategy:
      matrix:
        node-version: [18.x]
    steps:
    - uses: actions/checkout@v3
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
    - run: npm ci
    - name: serverless deploy
      uses: serverless/github-action@v3.2
      with:
        args: deploy
      env:
        AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
        AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

## Step 7: Add AWS_ACCESS_KEY_ID and ASW_SECRET_ACCESS_KEY to GitHub Secrets
Always keep AWS_ACCESS_KEY_ID and ASW_SECRET_ACCESS_KEY in privately. They are not meant to share or let public known for prevention of data breaches and landed to the wrong hands (hackers)

<img width="937" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/1988e2c1-64b2-48b7-975d-311a67cfac09">



## Step 8: Push changes to GitHub to start the workflow
Commit changes locally and push it to GitHub. Navigate the repo on GitHub, click on the **Actions** tab to see the workflows.
Confirm all tests passed and without errors
<img width="945" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/d2b06c16-74ae-4997-92a8-32757c41c9c5">



## Step 9: Access AWS Console to check the Lambda application (on salesphere-dev-api and SalesSphere-dev-error)
<img width="749" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/61bffb68-74dd-4ed2-963d-8628b5232c8e">


## Step 10: Test many times to Invoke the Lambda application
<img width="719" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/33662d3d-8d24-46f1-b301-811640f1f7ff">


Go to the test and click 

<img width="716" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/0a5f810d-c08c-45eb-a172-37e942359282">


Click a few times on the orange test box to invoke 

(for both on salesphere-dev-api and SalesSphere-dev-error)

## Step 11: Check any readings when monitoring the Lambda application
<img width="737" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/f002170d-cafd-4ea0-8aae-1afac018fc64">



<img width="955" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/54834832-ae06-4c4f-a877-97f8a077002a">


## Step 12: Access and login SenseDeep application
https://www.sensedeep.com/ can be register for free. For this project, we will access as a free account
Do go to this link https://www.sensedeep.com/doc/kb/starting/setup.html on how to register and setup

## Step 13: Create the widgets of graph views on SUM and Average for the related relevant monitoring Lambda application
illustrating one screenshot example of a SUM widget on salesphere-dev-api

<img width="697" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/2ce1f85b-418c-4441-bdc5-79b5bffe87b6">


## Step 14: Completion on ready to view centralize Dashboard   
This is the illustration of a detail widget based on SUM and Average hourly on salesphere-dev-api and SalesSphere-dev-error. 


SALESPHERES DASHBOARD

<img width="755" alt="image" src="https://github.com/flowstarts2020/SaleSpheres/assets/69182919/c56dac80-741c-48ed-9daf-3a47f34f664f">

## Other information - FAQ
What if Sensedeep is not available or outage?

No issue, we have the widgets dasboard created on CloudWatch updating based on salesphere-dev-api. The overall factors on ConcurrentExecutions, Duration, Errors, Invocations, Throttles and by each factor. We have an overall factors in numbers. Below is an example

![image](https://github.com/flowstarts2020/SaleSpheres/assets/69182919/fc5479d9-b61e-4768-9227-3fee03cc0fbe)

What is each of the Definition means?

Invocations -The number of times that your function code is invoked, including successful invocations and invocations that result in a function error.

Duration - The amount of time that your function code spends processing an event. The billed duration for an invocation is the value of Duration rounded up to the nearest millisecond.

Errors - The number of invocations that result in a function error.

ConcurrentExecutions - The number of function instances that are processing events. If this number reaches your concurrent executions quota for the Region, or the reserved concurrency limit on the function, then Lambda throttles additional invocation requests.

Throttles - The number of invocation requests that are throttled. 

Would like to get the logs in real-time. How would I access?

You can access on the define Dashboard name saleshere from CloudWatch. Below is an example in real-time found below the widgets

![image](https://github.com/flowstarts2020/SaleSpheres/assets/69182919/e387fe11-7f54-4746-bf20-e9a9d774d3ef)

What is the next plan?

After a period of evaluation, we are glad to propose the positive results updates to our management. Next plan version will be on the area of API Gateway integration
as well as consideration the enhancement the features on the SenseDeep application.






