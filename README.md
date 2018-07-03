# lambda-sqs-sam-ple
this is a SAMple of Lambda SQS written in SAM obviously

## Please follow these steps in order to launch the sample via CloudFormation

### 1. Clone the repository

$ git clone https://github.com/davinod/lambda-sqs-sam-ple.git

### 2. From within the project folder, open the terminal and run CloudFormation package and deploy to launch the stack

$ cd lambda-sqs-sam-ple

$ aws cloudformation package --template-file sam-sqs-lambda.yml --output-template-file sam-sqs-lambda-transformed.yml --s3-bucket <S3-BUCKET-NAME>

$ aws cloudformation deploy --template-file ./sam-sqs-lambda-transformed.yml --stack-name <STACK-NAME>

Please replace <S3-BUCKET-NAME> and <STACK-NAME> by proper values.

### 3. After stack is created, push some messages to your SQS queue via AWS CLI

$ aws sqs send-message --queue-url <SQS-QUEUE-URI> --message-body "hello, world"

Replace <SQS-QUEUE-URI> by the SQS queue created by CloudFormation. You can access by opening the CFN stack, and clicking on "Resources". It should be something like: https://sqs.<REGION>.amazonaws.com/123456789/lambda-sqs-sam-ple1-MySqsQueue-1H4HVN8TNUIYU

### 4. Check on CloudWatch to check the logs of your Lambda function

Open the Lambda Web Console, access your Lambda and click on monitoring. You may see the statistics of the executions and click on "Jump to logs" to open it in CloudWatch.
