# AWS

- Amazon Web Services
- [Lucidchart](https://www.lucidchart.com/pages/) is good for drawing AWS architecture diagram.

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
- When uploading files with aws cli:
  - use `file://<filepath>` for text file
  - use `fileb://<filepath>` for binary file

## AWS SDK

They are used to connect AWS services from the programming written in various languages.

### Python - Boto3

- [Click](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) to see documents for boto3.
- AWS services can be accessed in three ways.
  - Client: `boto3.client('service_name')` low-level AWS service access. All AWS service operations are supported by clients.
    - `region_name` can be set during initialization
  - Resource: `boto3.resource('service_name')` higher-level, object-oriented API.
  - Session: `my_west_session = boto3.Session(region_name = 'us-west-2')` then `backup_s3 = my_west_session.resource('s3')`
    - stores configuration information (primarily credentials and selected region)
    - allows developer to create service clients and resources
    - `boto3` creates a default session if not specified.

## IAM

Identity and Access Management - used to create user and group with specific permissions.

- Follow the steps to create the users and group.
- For each user the keys can be found and created in the `Security credentials tab`
- Policy can be either predefined policies(managed policy) or created in the `Create Policy` page by using a visual editor or importing JSON policy file.

## S3

Provide Persistent Storage

- All buckets(global) are shown in the `S3` console. However, each bucket belong to a certain region and can be replicated across multiple regions.
- A file name is called key.
- Object lifecycle management, it has two types:
  - Transition actions — Define when objects transition to another storage class.
    - There are costs associated with the lifecycle transition requests.
  - Expiration actions — Define when objects expire. Amazon S3 deletes expired objects on your behalf.
- The public object URL can be in many forms.
  - When the region is in the default region `us-east-1`.
    - `https://s3.amazonaws.com/bucket/key`
    - `https://bucket.s3.amazonaws.com/key`
  - When the bucket is not in `us-east-1`:
    - `https://s3-region.amazonaws.com/bucket/key`
    - `https://s3.region.amazonaws.com/bucket/key`
    - `https://bucket.s3.amazonaws.com/key`
    - `https://bucket.s3.region.amazonaws.com/key`
    - `https://bucket.s3-region.amazonaws.com/key`

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

- This service does not require region selection, all settings are global.
- There is a 50 cents charge per month per host zone.
- DNS Records are added in the hostzones.
- Some domain register has free DNS services.
- TTL for the name server can be set to a lower value for a faster update. Then set it to the longest value for a better performance.
- Alias records(A or AAAA) and CNAME records are used to redirects queries. They have the following difference:
  - Alias records can only be used for selected AWS services. It is free.
  - CNAME records can be used for any domain. Can't redirect hostzone top level domain. It is not free.

## EC2

It provide computing services.

- A private key will be generated for instance connection upon creation.
- click connect in the instance menu for connection guide.
- For Mac/Linux using SSH connection, move file to ~/.ssh and use command chmod 400 to hide the file first.
- A load balancer helps a group of EC2 instances works together. There are three types of them:
  - Classic Load Balancer
  - Application Load Balancer
    - It can redirect HTTP to HTTPS
    - It will ping a certain URL for health check, if it don't get 200 response, the loab balancer will be marked as unhealth.
  - Network Load Balancer
  - A target group will be associated with load balancer, health check is configured here.
- Load balancer can assign Security Policies to certain SSL Certificates
  - A security policy is a combination of protocols and ciphers, The `ELBSecurityPolicy-2016-08` security policy has the highest compatibility.
- For some instance types AWS sets a limit of 0 which prevent the user from running, a limit increase request should be sent in these cases.
- Snapshots are the backup of the data on EBS volumes, whereas AMIs(image)are bootable copy of the whole EC2 instances.
  - A snapshot is required for creating an image, when creating an image from an instance directly(select instance and create image), a snapshot will be auto created. Snapshots cannot be deleted when it is used by the corresponding image.
    - There is a no reboot option, when creating images. It prevent the running server from rebooting. This is not recommanded for making production images
  - An AMI image can be copy from one region to another
  - An AMI image can be used to launch instance directly
- Launch template is a copy of the entire launch configuration
- `Launch more like this` for a instance in the console, will use the selected instance launch config to launch a new instance
- Each snapshot can have the Fast Snapshot Restore Service
  - enable it for new and existing snapshots on a per-AZ (Availability Zone) basis, and then create new EBS volumes that deliver their maximum performance and do not need to be initialized.
  - It costs `$0.75` per hour per zone.
- A CloudWatch Agent can be setup and installed on a EC2 instance to send logs to the cloudwatch, This can be achieved by completing the following steps:
  - For Ubuntu:
    - run `sudo curl -o /root/amazon-cloudwatch-agent.deb https://s3.amazonaws.com/amazoncloudwatch-agent/debian/amd64/latest/amazon-cloudwatch-agent.deb` to download
    - run `sudo dpkg -i -E /root/amazon-cloudwatch-agent.deb` to install
    - run `sudo usermod -aG adm cwagent` to add the installer created user `cwagent` to the `adm` group for system logs access
    - create and attach the EC2 Role with `CloudWatchAgentServerPolicy` policy
    - run the setup wizard `/opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard` add additional logs to publish in the wizard
      - `StatsD` or `collectd` daemon is used to publish metrics
        - If select `collectd`, run `sudo apt-get update && sudo apt-get install collectd` to install
      - Optionally, the config file can be stored in the AWS Systems Manager Parameter Store (SSM)
      - Check the config file at `/opt/aws/amazon-cloudwatch-agent/bin/config.json`
      - In the config files the `collect_list` stores all logs that will be set to the cloudwatch, each with its corresponding log group
      - Whenever making changes, run `service amazon-cloudwatch-agent restart` to restart the service
      - view the cloudwatch agent log to troubleshoot at `/opt/aws/amazon-cloudwatch-agent/logs/amazon-cloudwatch-agent.log`, config file validation file is stored at `/opt/aws/amazon-cloudwatch-agent/logs/configuration-validation.log`
    - move the generated the config file to `/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json`
    - run `systemctl enable amazon-cloudwatch-agent.service`, `service amazon-cloudwatch-agent start` to enable and start the service
  - If server is not hosted on AWS, `credentials` and AWS's `config` files need to be setup on the server in the `/home/cwagent/.aws/` folder, then link the files to `/opt/aws/amazon-cloudwatch-agent/etc/common-config.toml` by running `echo "[credentials]" >> /opt/aws/amazon-cloudwatch-agent/etc/common-config.toml && echo ' shared_credential_file = "/home/cwagent/.aws/credentials"' >> /opt/aws/amazon-cloudwatch-agent/etc/common-config.toml`
    - for `credentials` add
      ```
      [AmazonCloudWatchAgent]
      aws_access_key_id = 123
      aws_secret_access_key = 123
      ```
    - for `config` add
      ```
      [AmazonCloudWatchAgent]
      output = text
      region = aa-bbbb-n
      ```

## Elastic Beanstalk

It deploys app on EC2 and will do capacity provisioning, load balancing, scaling, and application health monitoring automatically.

- It has its own command line tool called `EB CLI`
- An EB App can have multiple Environment, each deployed environment has an URL which is an alias(A record) to its corresponding load balancer.
  - Once the environment is created the load balancer type cannot be changed.
- EB Worker App host a EB worker to handle periodical tasks with AmazonSQS.

### EB Configuration Files

- Configuration files are YAML- or JSON-formatted documents with a `.config` file extension that you place in a folder named `.ebextensions` and deploy in your application source bundle.
  - YAML format is widely used and the it is recommanded format for the config files.
- [Click Here](https://github.com/awsdocs/elastic-beanstalk-samples) to see some official config samples

##### Config Sections

- A config file can contain the following sections.
- [Click](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/customize-containers-ec2.html) to see full examples from the official documents.
- `option_settings` it defines values for configuration options for an EB environment
  - The following example set the EB CLI command timeout length.
    ```yaml
    option_settings:
    aws:elasticbeanstalk:command:
    Timeout: 1200
    ```
- `Resources` it defines the setting for AWS resources used by the EB environment.
  - The following example instruct the active Application Load Balancer for the EB environment to auto redirect HTTP to HTTPs
    ```yaml
    Resources:
    AWSEBV2LoadBalancerListener:
      Type: AWS::ElasticLoadBalancingV2::Listener
      Properties:
        LoadBalancerArn:
          Ref: AWSEBV2LoadBalancer
        Port: 80
        Protocol: HTTP
        DefaultActions:
          - Type: redirect
            RedirectConfig:
              Host: "#{host}"
              Path: "/#{path}"
              Port: "443"
              Protocol: "HTTPS"
              Query: "#{query}"
              StatusCode: "HTTP_301"
    ```
- `packages` it install defined packages upon deployment
  ```yaml
  packages:
    yum:
      libmemcached: []
      ruby-devel: []
      gcc: []
    rpm:
      epel: http://download.fedoraproject.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm
    rubygems:
      chef: "0.10.2"
  ```
- `files` create files on the EC2 instance
- `groups` create Linux server user groups
- `user` create Linux server users
- `sources` download an archive file from a public URL and unpack it in a target directory on the EC2 instance.
- `command` execute commands on the EC2 instance.
  - `ignoreErrors` when true, ignore error during deployment.
- `container_commands` run command in the project folder after initial environment setup.
  - `leader_only` When true, the command are only executed during environment creation and deployments
- `services` define which services should be started or stopped when the instance is launched.

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
  - `eb status <env-name>` check details.
  - `eb health <env-name>` check env health.
  - add app domain name in the `ALLOWED_HOSTS` in the `settings.py` file.
  - `eb deploy` to update the app.
    - Whenever changes are made to the local file, run deploy again to update.
    - When the project is under version control, only commited changes will be deployed.
    - or run `eb deploy --stage` to deploy staged changed instead of committing it first.
  - `eb open` open the website.
  - `eb logs` see error logs.
  - `eb use env-name` associate a default environment with a certain branch.
  - add the following `.config` content in the `.ebextensions` allows auto migration while deploying.
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
  - Follow the step to run shell command on server:
    ```bash
    eb ssh
    source /opt/python/run/venv/bin/activate
    source /opt/python/current/env
    cd /opt/python/current/app
    python manage.py shell
    ```

### Working with Crontab

- Add Cron jobs using to EB worker app.
  1.  In the root project folder add file `cron.yaml`
  2.  add schedule info to the file
      ```yaml
      version: 1
      cron:
       — name: "test"
         url: "/postapi"
         schedule: "* * * * *"
      ```
  3.  After deployment, a post request will be sent to the `url` periodically.
- Add cron jobs to all instance of the EB web app environment by putting the following config content into the `.ebextensions` foloder.
  ```conf
  files:
      "/etc/cron.d/mycron":
          mode: "000644"
          owner: root
          group: root
          content: |
              0 3 * * * root /usr/local/bin/myscript.sh
      "/usr/local/bin/myscript.sh":
          mode: "000755"
          owner: root
          group: root
          content: |
              #!/bin/bash
              date > /tmp/date
              # Your actual script content
              source /opt/python/run/venv/bin/activate
              source /opt/python/current/env
              cd /opt/python/current/app
              python manage.py shell --command="import iport.tasks; iport.tasks.daily_report()"
              exit 0
  commands:
      remove_old_cron:
          command: "rm -f /etc/cron.d/mycron.bak"
  ```

## DynamoDB

A NoSQL database that stores JSON data.

- Whenever the database is updated, new record or updated record will be sent to the DynamoDB Stream.

## RDS

It hosts and maintain SQL Database server.

- When a new database is registered, be default it is set to private. It can be set to public by modifying the instance.
- Double check VPC and SG for database created in a new region.
- Database settings are done through `Parameter groups`. by default, The default group is used when a database is created. To use cutomized groups, create a new one and apply it to the database.
  - `log_min_duration_statement` the minimum time for a query to be logged.
  - `log_statement` how the queries are logged.

## CloudWatch

It generates metrics for other services.

- By default it generates metrics for every 5 mins for free. For a enhanced plan, it will generate metrics everything with a fee.
- Enhanced plan will provides more metrics.
- It can be used to set rules for auto scaling policy when the values from a certain metric reach certain value.
- Alarms can be set based on Metrics' states and values.
- Custom Log Group can be created and log stream can be pushed to the log group.
- Data from the log stream can be filter, collected and push to metrics based on the a predefined pattern.
  - Pattern to match log event, `127.0.0.1 - frank [10/Oct/2000:13:25:15 -0700] "GET /apache_pb.gif HTTP/1.0" 200 1534` can be `[ip, user, username, timestamp, request, status_code = 4*, bytes]`
  - `>`, `<` can be used on numerical values.
  - text surrounded by `""` or `[]` are treated as one entry.
  - Once a pattern is set cloudwatch can be generated based on it using AWS console, `CloudWatch` -> `Log Groups` -> `Create metric filter`.
  - [Click Here](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/FilterAndPatternSyntax.html) to learn more about the syntax
- When exporting logs in log group to s3, each AWS can run one exporting task at a time.
  - Multiple log groups can be exported by using regex pattern for `logGroupName` parameter
- When publish log through `Lambda`, log stream are encoded as `base64` and compressed by `gzip`.
- CloudWatch Logs Insights allows one to query log groups
  - [Click Here](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CWL_QuerySyntax.html) to learn more about the query syntax
  - [Click Here](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CWL_QuerySyntax-examples.html) for more examples
  - The time span for the logs are set in the top menu
  - The concurrent queries limit is set to `10` when using AWS SDKs

## Lambda

It runs scripts and codes without the need to set up the server.

- `Lambda` uses `UTC` as instance local time
- Click the Test tab to generate test cases with specific input.
- Add proper Lambda Execution Role to allow Lambda instance to be triggered by other AWS services.
- When SQS is the trigger, the batch means the number of SQS messages the lambda wants to receive and process during one invocation.
- The online editor console display limited lines of output, go to CloudWatch log group to view complete logs
- A layer is a ZIP archive that contains libraries, a custom runtime, or other dependencies which will be deployed in to the `/opt` folder of your Lambda container
  - If the zipped image size is over 50MB upload to S3 and use link to add layer.
  - The Lambda Develop package cannot be over 250MB after unzipping
  - The layer should obey the following file structure
    - For `Python 2.7`, the full path is `/opt/python` . For `Python 3.6` and `3.7`, that full path is `/opt/python/lib/python3.6/site-packages` and `/opt/python/lib/python3.7/site-packages` respectively.
    - only the reqired package folders are needed.`*.dist-info`, `bin` and `__pycache__` are not required. run `rm -r *.dist-info __pycache__ */__pycache__` for clean up.
    - Amazon Linux supports specific Linux version for certain packages.
      - If running `pip install` locally and the package doesn't work, build Amazon Linux container using Docker or use EC2 run `pip install` and get the package for Amazon Linux.
    - In environment variable add the folder path to key `PYTHONPATH` if anything goes wrong.
- DynamoDB can trigger Lambda function using DynamoDB stream. All records will be sent to lambda when one or more records are edited.
- Versioning
  - Create a version will create a snapshot of the current function.
  - An Alias can point to one version at a time.
  - Lambda function can now be identified by other resources as `Function:Alias`
  - By default when only use the function name, it means the lastest version(the one without any version number and alias).
  - Updating alias to point to a new version by `aws lambda update-alias --function-name <FunctionName> --name <AliasName> --function-version <VersionNumber>`
  - A Lambda version is a readonly snapshot that is saved for other resources to trigger.
- Updating a function with additional dependencies using AWS CLI
  1. Run `pip install --target ./package <pkgName>` to install the package to the `package` folder inside the project foloder.
  2. Run `zip -r9 ${OLDPWD}/function.zip .` to create a ZIP archive of the dependencies in the project folder.
     - all the dependency directories are at the top level of the zip file
  3. Run `cd $OLDPWD && zip -g function.zip lambda_function.py` to add lambda function code to the archive.
  4. Run `aws lambda update-function-code --function-name <LambdaName> --zip-file fileb://function.zip` to update the function code from the project folder

## SQS

It store messages as a cache for other services to fetch, then delete processed messages.

- Any triggered lambda function will delete messages after its done.
- Delivery means the client side delivery a new message to the SQS.
- Receive means any services starts to process the message from SQS.
- `Receive Message Wait Time` - The number of seconds of the interval for other services fetch messages from SQS. By default it is 0 second.
  - 0 second means short polling, other services fetch messages contantly.
  - Any value assigned other greater than 0 second make it long polling.
- `Message Retention Period` - the length of the period that the messages are available to other services.
- `Default Visibility Timeout` - the length of the period that the messages become invisible for other services, once a service has started processing it.
- `Delivery Delay` - the time it takes for the SQS to show new messages.
- `Dead Letter Queue` - It is a Queue in SQS that designated to receive data that cannot be processed by the services.
  - When a service receive a message from SQS and failed to process. The message will be available in the queue again and again.
  - `Maximum Receives` the number of failure for message to reach before it is moved to Dead Letter Queue.

## SNS

It is used to send notifications to user emails or other resources.

- A topic is an object that recevice notifications.
- A topic can have many subscribers with differenct protocols(Email, SQS, Lambda) to receive the message.
- Each topic has a `Publish message` button that can be used to test a message with all subscribers.
- Each subscription can have a unique filter for all messages.
- Selecting `Enable raw message delivery` for SQS subscription allow SNS topic send raw message which is the same format as sending SQS message directly.

## SES

It can be used to send formatted emails from registered email addresses.

- The email that will be used to send messages should be verified first.
- The email can also be sent by cutomized SMTP Service by adding Domain.
- By default email are sent throught AWS mailbox simulator. The message trigger spoof warning or treated as spam sometimes. Request sending limit increase will move SES out of the sandbox mode.
- SES template is a `json` file with the following format.
  ```json
  {
    "Template": {
      "TemplateName": "orangeville_limit_exceeded",
      "SubjectPart": "THRESHOLD LIMIT EXCEEDED",
      "TextPart": "THRESHOLD LIMIT EXCEEDED",
      "HtmlPart": "HTML_CONTENT"
    }
  }
  ```
  - `HtmlPart` - It takes a escaped json string. [Click here](https://www.freeformatter.com/json-escape.html) to use the json escape tool to convert it to string.
  - run `aws ses create-template --cli-input-json fileb://<filePath> --region <regionCode> --profile <profileName>` to create the template.
  - run `aws ses update-template --cli-input-json fileb://<filePath> --region <regionCode> --profile <profileName>` to update the template.
- Use other SDK to send the email using html template or plain text.

## API Gateway

It provides support for generating serverless APIs.

- All API methods are defined as resources.
- Resources need to be deploy as stages before using.
- Custom Domain Names
  - Custom Domain Names will attach user's own certificate to the URL and map the domain to the staged resources.
  - Custom Domain Names will need an Alias in Route 53 for the API Gateway domain name found in the Endpoint configuration panel after creating setup the new API Gateway domain name
  - It takes some time for the new domain name to work
- CORS can be enabled for each individual method in the `Actions` menu.
  - `CORS` header setting will be stored in the `OPTIONS` method of the same resource.
  - Can allow more headers in the `Access-Control-Allow-Headers` field when edit CORS setting
- If integrated with Lambda, response header can be added in the return statement in the following format.
  ```py
  'headers': {
      'Access-Control-Allow-Headers': 'Content-Type, Cache-Control',
      'Access-Control-Allow-Origin': '*',
      'Access-Control-Allow-Methods': 'OPTIONS,POST,GET'
  },
  ```
- The execution log can be enalbed in the stage setting `Logs/Tracing` Tab.
  - The `ARN` of an `IAM` role with `AmazonAPIGatewayPushToCloudWatchLogs` Permission is required in the setting page, opened from the left pannel.
  - It can log full requests/responses data.
  - It can enable detailed CloudWatch metrics.
- The access log is the custom log that can be used to store cutomized formatted log.
  - It support log with `CLF`, `JSON`, `CSV`, and `XML` format.
  - only the `$context` variable can be used to access requrest info.

## Amplify

- It is used for hosting frontend apps and backend services

### Amplify Console

- It can be used to host Web Apps using source code from online repo provider like GitHub
- Whenever a change is pushed the app will be auto built and updated
- Preview can be setup, so whenever a pull request is made, one can preview the changes in a browser
- Each GitHub branch can connect to one server
- The Domain management setting page can create and manage domain with SSL certificate

### Amplify CLI

- It can be use to host both frontend and backend apps
- setup
  1. run `sudo npm install -g @aws-amplify/cli` to install
  2. run `amplify configure` to create new aws crendentials for amplify CLI
  3. run `amplify init` from the root directory of the frontend app to create new amplify project
- run `amplify hosting add` to host frontend web app, there are two options:
  - hosting of static website using Amazon S3 and Amazon Cloudfront directly
  - hosting with AWS Amplify Console, there are two more options:
    - Continuous deployment - auto built and update when every a `git push` is made
    - Manual deployment - run `amplify publish` to deploy app from local machine
- run `amplify console` to open Amplify Console
- run `amplify status` check the status of running services
- run `amplify delete` delete all the environments of the project from the cloud and wipe out all the local files created by Amplify CLI
- run `amplify help` to see more options

## Amazon Certificate Manager

- Certificates from ACM cannot be downloaded used to on the server unless it is private CAs generated from ACM.

## Sagemaker

Fully managed Cloud based machine learning service

#### Notebook

- A Notebook instance can be used to develop and build model code in a Jupyter notebook using designated instances.
- It have many pre-configured popular ML algorithm
- Import model code from github
- In a note book instance select open instance, new -> terminal, cd to sagemaker folder then git clone the project.

  - The sagemaker folder in the terminal will be the root folder of the Jupyter notebook

- support data type CSV recordIO Int32 Float32 Float64
- Training result(artifact) will be stored in s3
  - Two training data input mode pipe mode(streaming) and file mode(batch)
  - Training will be fully managed and done on one or many instances. and supports Petabyte datasets.
- Deploy for Realtime prediction can be done by Sagemaker endpoint. It supports auto scaling.
- Deploy for non-interactive use cases can be done by Sagemaker Batch Transform. Fully managed.
- Sagemaker Ground Truth helps with data labeling.
  - Auto labeling
  - Manual labeling
- Sagemaker Neo uses edge locations to reduce lantency in training and use custmized hardwares.

## AI Services

- They are high-level(ready-to-use) Machine Learning services provided by AWS

### Rekognition

It provides an endpoint service for image and video analysis. It is the AWS's top level AI service for computer vision.

- The endpoint is available from CLI, SDKs as long as the credential role has access to the service.

### Transcribe

It provides speech to text services

- It supports both realtime and batch translation.
- Call the service endpoint for realtime translation.
- For batch translation, use AWS console to create a job and Upload audio file to S3 and run the service.
- Amazon Transcribe Medical is specialized in transcribing medical speech into text
- Adding words that are hard to recongize to custom vocabulary to improve accuracy
  - For a phrase add hypens `-` in between.
  - For acronyms add dots in betweens.
  - It can be a list format or a table format
    - Words can be provided in a `txt` file that has a word in each line, then it can be uploaded from local machine.
    - Table format is tab delimited and must have the following columns, columns can be entered in any order. The file can be `txt` and it must be uploaded to S3 first.
      - `Phrase` same as the words in list formats
      - `SoundsLike` break a word or phrase down into smaller pieces using the standard orthography of the language, then connect them in hypens. Ex, `loss-ann-gel-es` for `Los-Angeles`
      - `IPA` To specify the pronunciation of your word or phrase, include characters in the International Phonetic Alphabet (IPA) in this field.
        - one word cannot have both `IPA` and `SoundsLike` defined.
      - `DisplayAs` Defines the how the word or phrase looks when it's output.
- A word filter can be added with a list of unwanted words in the list format.

### Translate

It is a neural network based translation service.

- It takes into account the entire context of the source sentence as well as translation it has generated so far, to create a more accurate and fluent translation
- It supports both realtime and batch translation.

### Polly

It provides text to speech services

- It can generate audio stream for realtime use cases.
- It can create a audio file for batch use cases.
- It supports a wide range of voices and languages.
- The voice can be customized using SSML(Speech Synthesis Markup Language)

### Textract

It can extract content from text image.

- Upload the text file in JPEG, PNG, or PDF format to the endpoint, it will return processed text in raw text, form and table format.

### Comprehend

Amazon Comprehend is a natural language processing (NLP) service that uses machine learning to discover insights from text.

- Amazon Comprehend provides Keyphrase Extraction, Sentiment Analysis, Entity Recognition, Topic Modeling, and Language Detection APIs
  - Keyphrase Extraction - The Keyphrase Extraction API returns the key phrases or talking points and a confidence score to support that this is a key phrase.
  - Sentiment Analysis - The Sentiment Analysis API returns the overall sentiment of a text (Positive, Negative, Neutral, or Mixed).
  - Syntax Analysis - The Amazon Comprehend Syntax API enables customers to analyze text using tokenization and Parts of Speech (PoS), and identify word boundaries and labels like nouns and adjectives within the text.
  - Entity Recognition - The Entity Recognition API returns the named entities ("People," "Places," "Locations," etc.) that are automatically categorized based on the provided text.
  - Medical Named Entity and Relationship Extraction (NERe) - The Medical NERe API returns the medical information such as medication, medical condition, test, treatment and procedures (TTP), anatomy, and Protected Health Information (PHI).
  - Medical Ontology Linking - The Medical Ontology Linking APIs identifies medical information and links them to codes and concepts in standard medical ontologies.
  - Custom Entities - Custom Entities allows you to customize Amazon Comprehend to identify terms that are specific to your domain.
  - Language Detection - The Language Detection API automatically identifies text written in over 100 languages and returns the dominant language with a confidence score to support that a language is dominant.
  - Custom Classification - The Custom Classification API enables you to easily build custom text classification models using your business-specific labels.
  - Topic Modeling - Topic Modeling identifies relevant terms or topics from a collection of documents stored in Amazon S3. It will identify the most common topics in the collection and organize them in groups and then map which documents belong to which topic.
  - Multiple language support - Amazon Comprehend can perform text analysis on English, French, German, Italian, Portuguese, and Spanish texts.

### Lex

Conversational interfaces for your applications powered by the same deep learning technologies as Alexa

- Defining Lex model is similar with creating a skill for Alexa.

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

- Register a product from the developer console in order to get crendentials required by the customized Alexa Device.

## Cognito

- It provides authentication, authorization, and user management for your web and mobile apps. Your users can sign in directly with a user name and password, or through a third party such as Facebook, Amazon, or Google.
- The two main components of Amazon Cognito are user pools and identity pools.
  - User pools are user directories that provide sign-up and sign-in options for your app users.
  - Identity pools enable you to grant your users access to other AWS services. You can use identity pools and user pools separately or together.
