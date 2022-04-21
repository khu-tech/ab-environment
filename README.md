# A/B environment
A/B environment is a concept to run different version of code in production which links to the same Twilio Flex account. This example uses self-hosting technology on AWS S3 in order to realize this goal. 


## S3 Setup

1. Set up an AWS account 
2. Create an S3 bucket 
3. Create two folders under this S3 bucket, one folder for environment A; and the other folder for environment B. 
4. Upload index.html, pluginConfigDialpad.json, plugin-sample.js to folder A. 

## Plugin build file setup 
In order to load custom plugins, we need to store the plugin build file to an external URL. To generate this build file, go to the plugin directory and run 
twilio flex:plugins:build, and take the *.js file (for example, plugin-sample), upload to the S3 folder, copy/paste the S3 url. 

## Service function deployment 
Flex deployment often times include Twilio function deployment. There are multiple ways to maintain two versions of the function files with two different URLs. Here in this example we use two different service. 

Go to the Twilio function CLI folder directory and run "twilio serverless:deploy --service-name environmentalpha" and "twilio serverless:deploy --service-name environmentbeta" if you don't have existing services named "environmentalpha" and "environmentbeta". If these two environments already exist, go to "package.json" file under this directory and make sure the "name" here equals the name of the service you are going to deploy to, and then run "twilio serverless:deploy"

Copy paste the full URLs of these two deployed functions. 

```

## How it works


