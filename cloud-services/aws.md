# AWS

Amazon Web Services

## IAM

Identity and Access Management - used to create user and group with specific permissions.

- Follow the steps to create the users and group.
- for each user the keys can be found and created in the `Security credentials tab`
- policy can be either predefined policies(managed policy) or created in the `Create Policy` page by using a visual editor or importing JSON policy file.

## AWS CLI

AWS CLI provides full controls of AWS using command lines.

### Setup

1. Installation, [click here](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) to see the command needed for installation.

- to install on macOS for all user, run `curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg" sudo installer -pkg AWSCLIV2.pkg -target /`

2. run `aws configure` and enter AWS credentials and default settings for the default user profile.

### IAM

Identity and Access Management - used to create user and group with specific permissions.

- Follow the steps to create the users and group.
- for each user the keys can be found and created in the `Security credentials tab`
- policy can be either predefined policies(managed policy) or created in the `Create Policy` page by using a visual editor or importing JSON policy file.

## Route 53

It provides a DNS service that translate the domain name into a designated IP address.

- There is a 50 cents charge per month.
- DNS Records are added in the hostzones.
- Some domain register has free DNS services.
- TTL for the name server can be set to a lower value for a faster update. Then set it to the longest value for a better performance.

## EC2

It provide computing service.

- A private key will be generated for instance connection.
- click connect in the instance menu for connection guide.
- For Mac/Linux enter the command directly in the terminal.(move file to ~/.ssh and use command chmod 400 to hide the file first)
- For window using SHH through Git Bash.

## DynamoDB

A NoSQL database that stores JSON data.

## Lambda

It runs scripts and codes without the need to set up the server.

- Click the Test tab to generate test cases with specific input.
- Add proper Execution Role with specific permission to allow Lambda instance to have access to other AWS services.

## Alexa

### Alexa Skills Kit

It is used to build Alexa skills for Alexa supported products.

- A skill is a set of predefined voice commands and reactions.
- It can be tested in the console or on any Alexa device that logged in with the developers' account.

#### Implementation

Create a Skill - a skill can be created by using the following ways.

- Alexa Skills Kit Developer Console
  1. [Click Here](https://developer.amazon.com/alexa/console/ask) to signup and login the console.
  2. Follow the steps to create a skill.
  - Invocation Name is the words that used to activate the skill, it has to have at least two words.
  - Intents are the task or action names.
  - Utterances are exact voice commands that used to invoke the corresponding intent. One intent can have many utterances.
  - Slot Types are words that can be recognized as variable in the voice command.
  3. The result of all the skill setting will be represented as a JSON file in the JSON editor.
  - Optionally, The step be step setting can be skipped by just entering a complete JSON setting data.
  4. Create Lambda instance as the endpoint for the skill and copy the Lambda link in the endpoint setting.
  - Use the [Code Generator](https://s3.amazonaws.com/webappvui/skillcode/v2/index.html) to generate backend code automatically.
  5. In the homepage of the console, click Test to test the skill or enable Beta Testing to allow selected developer account holder to test the skill.
- Alexa Skills Kit CLI
  1. Install Node.js 4.5>=
  2. [Click Here](https://developer.amazon.com/alexa/console/ask) to signup an Amazon developer account.
  3. run `sudo npm i -g ask-cli`.
  4. run `ask init`, to sign in with the AWS developer account.
  5. run `ask init --aws-setup`, to update the AWS account credentials if AWS default user profile's credentials has not been set up for the AWS CLI, fill in the AWS account keys.
  6. run `ask new -n <folderName>`, to create a skill in a new folder.
  - run `ask clone -s <link>`, to clone an existing skill.
  7. run `ask deploy`, to deploy the skill by uploading skills in the project folder to the Alexa Developer Console and Creating AWS Lambda instance.
  8. run `ask simulate -l en-US -t "voice command for testing"`, to test the skill.

#### Additional Features

- Work with DynamoDB, [Click](https://github.com/dabblelab/alexa-dynamodb-skill-template) to see the template file, edit and create DynamoDB table as required by the Lambda instance. Make sure Lambda has the permission to access the DynamoDB table.

### Alexa Voice Service

It is used to allow devices to support Alexa.
