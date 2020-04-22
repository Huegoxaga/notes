# AWS

Amazon Web Services

## AWS CLI

AWS CLI provides full controls of AWS using command lines.

### Setup

- Installation, [click here](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) to see the command needed for installation.
  - to install on macOS for all user, run `curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg" sudo installer -pkg AWSCLIV2.pkg -target /`
- run `aws configure` and enter AWS credentials and default settings for the default user profile.
  - run `aws configure --profile username` to set up non-default user.
  - When execute commands using non-default user credentials, appending `--profile produser` to all commands.
  - profile files can be found at `~/.aws/credentials` and `~/.aws/config`.
  - json is the default output format.
- Environment variables can be set up to override user profiles setting, it is useful for one time execution in scripts.
  ```bash
  export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
  export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
  export AWS_DEFAULT_REGION=us-west-2
  ```
- Environment variables can also be stored in the `.bash_profile`.

### General Usage

- help
  - `aws help`
  - `aws <servicename> help`
- [Click here](https://docs.aws.amazon.com/cli/latest/index.html#) for complete reference.

## IAM

Identity and Access Management - used to create user and group with specific permissions.

- Follow the steps to create the users and group.
- For each user the keys can be found and created in the `Security credentials tab`
- Policy can be either predefined policies(managed policy) or created in the `Create Policy` page by using a visual editor or importing JSON policy file.

## S3

Provide Persistent Storage

### CLI Commands

- `aws s3 mb s3://bucket-name` Create new bucket.
  - bucket name has to be unique.
- `aws s3 ls` list all buckets.
  - `aws s3 ls s3://bucket-name` list certain bucket.
- `aws s3 rb s3://bucket-name` remove certain bucket.
  - append `--force` to remove a non-empty bucket.
- `aws s3 sync <from> <to>` synchronize one folder to another.
  - It only copies missing or outdated files or objects between the source and target.
  - can sync from local to s3, from s3 to local, from s3 to s3.
  - add `--delete` option is the `sync` process will cause a file to be deleted.
  - `--grant` option is available for granting permissions. Ex, `--grants Permission=Grantee_Type=Grantee_ID [Permission=Grantee_Type=Grantee_ID ...]`
- `aws s3 cp <from> <to>` copy files. usage is similar with sync.
- `aws s3 rm s3://my-bucket/path/filename` remove a file.
  - add `--recursive` to delete a path(folder) inside a bucket.

## Route 53

It provides a DNS service that translates the domain name into a designated IP address.

- There is a 50 cents charge per month per host zone.
- DNS Records are added in the hostzones.
- Some domain register has free DNS services.
- TTL for the name server can be set to a lower value for a faster update. Then set it to the longest value for a better performance.
- Alias records(A or AAAA) and CNAME records are used to redirects queries. They have the following difference:
  - Alias records can only be used for selected AWS services. It is free.
  - CNAME records can be used for any domain. Can't redirect hostzone top level domain. It is not free.

## EC2

It provide computing service.

- A private key will be generated for instance connection.
- click connect in the instance menu for connection guide.
- For Mac/Linux enter the command directly in the terminal.(move file to ~/.ssh and use command chmod 400 to hide the file first)
- For window using SHH through Git Bash.
- A load balancer helps a group of EC2 instances works together. There are three types of them:
  - Classic Load Balancer
  - Application Load Balancer
    - It can redirect HTTP to HTTPS
    - It will ping a certain URL for health check, if it don't get 200 response, the loab balancer will be marked as unhealth.
  - Network Load Balancer
  - A target group will be associated with load balancer, health check is configured here.
- Load balancer can assign Security Policies to certain SSL Certificates
  - A security policy is a combination of protocols and ciphers, The `ELBSecurityPolicy-2016-08` security policy has the highest compatibility.

## Elastic Beanstalk

It helps deploy app on EC2 and will do capacity provisioning, load balancing, scaling, and application health monitoring automatically.

- It has its own command line tool called `EB CLI`
- An EB App can have multiple Environment, each deployed environment has an URL which is an alias(A record) to its corresponding load balancer.
  - Once the environment is created the load balancer type cannot be changed.

### EB CLI

#### Installation

- run `brew update && brew install awsebcli` to install EB CLI

#### Setup

- Crendentials set in for AWS CLI can be accessed by EB CLI by using `--profile username`
- Config file can be set for EB CLI only in file `~/.elasticbeanstalk/config`
- EB CLI is configured in the project directory.
- run `eb init` to add project info and credentials for the project.
  - or `eb init --profile username` add existing user to the project.

#### Usage

- Deploy Django App
  - In project folder export `requirement.txt`, by running `pip freeze > requirements.txt`
    - `requirement.txt` needs to be updated whenever pip packages are changed in the project.
  - Create a folder `mkdir .ebextensions`
  - Add the following text in the `.ebextensions/django.config` file
    ```
    option_settings:
    aws:elasticbeanstalk:container:python:
      WSGIPath: projectname/wsgi.py
    ```
  - `eb init -p python-3.6 project-name` Initialize EB CLI repository
    - new `config.yml` will be created in the `.elasticbeanstalk` folder, customization can be added in the file. The file will only be read during environment creation process.
  - `eb use my-env-name` setup a default env for the current git branch
  - `eb create name-env` create new env and deploy project to it.
  - `eb status` check details.
  - add app domain name in the `ALLOWED_HOSTS` in the `settings.py` file.
  - `eb deploy` to update the app.
    - Whenever changes are made to the local file, run deploy again to update.
    - When the project is under version control, only commited changes will be deployed.
    - or run `eb deploy --stage` to deploy staged changed instead of committing it first.
  - `eb open` open the website.
  - `eb logs` see error logs.
  - `eb use env-name` associate a default environment with a certain branch.
  - add the following `db-migrate.config` file in the `.ebextensions` allows auto migration while deploying.
    ```
    container_commands:
      01_migrate:
        command: "django-admin.py migrate"
    option_settings:
    aws:elasticbeanstalk:application:environment:
    DJANGO_SETTINGS_MODULE: projectname.settings
    ```
  - run `eb terminate env-name` to stop the instance.
  - run `eb ssh env-name` to connect to the instance.
  - run `eb config env-name` to check configuration.
  - run `eb health env-name` to check environment health.

## DynamoDB

A NoSQL database that stores JSON data.

## RDS

It hosts and maintain SQL Database server.

- When a new database is registered, be default it is set to private. It can be set to public by modifying the instance.

## CloudWatch

It generates metrics for other services.

- By default it generates metrics for every 5 mins for free. For a enhanced plan, it will generate metrics everything with a fee.
- Enhanced plan will provides more metrics.
- It can be used to set rules for auto scaling policy when the values from a certain metric reach certain value.

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

- Alexa Skills Kit Developer Console - Alexa-Hosted

  1. [Click Here](https://developer.amazon.com/alexa/console/ask) to signup and login the console.
  2. Click on `Create Skill`, select `Alexa-Hosted` option.
     - Using `Alexa-Hosted` will enable the code editor on the console, and gain immediate access to an AWS Lambda endpoint, 5 GB of media storage with 15 GB of monthly data transfer, and a table for session persistence.
  3. Follow the steps to create a skill.
     - Invocation Name is the words that used to activate the skill, it has to have at least two words.
     - Intents are the task or action names.
     - Utterances are exact voice commands that used to invoke the corresponding intent. One intent can have many utterances.
     - Slots are words that can be recognized as variables in the voice command.
       - It can be set as mandatory, then additional prompts can be set to get its value. This is called `Auto Dialog Delegation`.
       - A type must be selected for the slots.
       - Custom types can be set for the slots.
       - Validating can be set for the slots.
     - The setting can be tested by using `Utterrance Profile` without any backend code.
  4. The result of all the skill settings will be represented as a JSON file in the JSON editor.
     - Optionally, The step by step setup can be skipped by just entering a complete JSON setting data.
  5. In the homepage of the console, click Test to test the skill or enable Beta Testing to allow selected developer account holders to test the skill.
  6. In the `Build` page, `Interface` Tab, enable `Presentation Layer` and generate display `JSON` model in the `display` tab.
  7. In code, Add an utiltity function to check if device support APL, and add the APL `json` model to the code. Edit handlers

- Alexa Skills Kit Developer Console - Custom

  - Need this additional step - Create Lambda instance as the endpoint for the skill and copy the Lambda link in the endpoint settings.
    - Use the [Code Generator](https://s3.amazonaws.com/webappvui/skillcode/v2/index.html) to generate backend code automatically.

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

#### Modification

- To change skill name, go the distribution and change the `Public Name`.
- To support a new language, add a new language in the dropdown menu, copy the JSON setting from an existing language model, translate it then paste it in the new language model. Then process the backend code using `i18next`.

#### Coding

- Backend code for Alexa skill can be written in Node.js or python.

#### Coding in Node.js

- `index.js` is the entry point.
  - It consists of one handler for each Intent.
    - Each handler has a `canhandle()` method that determine which intented is requested.
      - `canhandle()` method will return true if the correspoding intent is requested.
    - The `handle()` method will process the request.
      - It can also return another intent and it is called intent chaining.
      - It can call another handler to make code efficient.
  - The `handlerInput` is an object that contains info about the user request.
  - It has two types of Interceptors.
    - Request interceptors will run right before the all handlers process the requests.
    - Response interceptors will run right after the all handlers process the requests.
      - They use the `.process()` method to add additional info for into the `handlerInput` object.
  - Everything needs to be registered at the bottom of the file, there are two options.
    - If using `Alexa.SkillBuilders.custom()`. Everything needs to be added manually. Developer has the control of the structure.
    - If using `Alexa.SkillBuilders.standard()`. It registers many functions by default.
- `package.json` controls the dependency for the skill
  - Add records in the file and then build will automatically install the dependency for the skill project when running on AWS Lambda.
- Useful Dependencies
  - The `i18next` determines the language set on the user device, then use a helper function created in the request interceptor to get strings from the `languageStrings.js` in the corresponding language.

#### Additional Features

- To store data use the attribute manager and register a persistent adapter.
  - Session Attributes are passed along with the requests and responses while a session is open.
  - Persistent Attributes are data stored in S3.
  - When using Alexa-Hosted Template, in the code page click the S3 link to view the saved files.
- Work with DynamoDB, [Click](https://github.com/dabblelab/alexa-dynamodb-skill-template) to see the template file, edit and create DynamoDB table as required by the Lambda instance. Make sure Lambda has the permission to access the DynamoDB table.
- Work with ASK APIs
  - Needs to register the `.withApiClient(new Alexa.DefaultApiClient())` at the bottom of the `index.js` file if using custom skill builder.
  - Access permission info from `ServerClientFactory`.
  - The customer API returns the user info only when the permission is required in the build page, permission tab in the developer console, and the user permission is given after the propmt or in the Alexa App or `alexa.amazon.com`.
  - The setting API returns info like the device location.
  - Reminder API reminds the user for an event set by user earlier.
    - It also needs permissions on developer end and user end.
  - External API - It is available for the backend code.
  - Progressive Response API - Alexa request a response every 8 seconds, otherwise the session will be closed. If the device is not responding due to any reason, this API will response certain message in between.
- SSML(Speech Synthesis Markup Language ) - Is a markup language for Alexa Voices and sound effects.
  - [Click here](https://developer.amazon.com/en-US/docs/alexa/custom-skills/speech-synthesis-markup-language-ssml-reference.html) to see its docs.
  - It can be injected into output string to add tones to the voices.
  - It can be tested on the test page under `Voice & Tone` tab.

#### Debugging

- Console log will be printed to the AWS CloudWatch Log.

### Alexa Voice Service

It is used to allow devices to support Alexa.
