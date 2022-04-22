# Simple Golang program using AWS Lambda

This is a very simple golang program which is executed by AWS Lambda function.

Prerequisites:

- Having an AWS account
- Create a IAM Role passing as a policy the `trust-policy.json` file

Steps:

- Build the program by running `GOARCH=amd64 GOOS=linux go build main.go`
- Zip the binary `zip function.zip main`
- Create a lambda function by running `aws lambda create-function --function-name lambda-example --zip-file fileb://function.zip --handler main --runtime go1.x --role arn:aws:iam::507365993774:role/lambda-ex`
- Invoke the lambda by running `aws lambda invoke --function-name lambda-example --cli-binary-format raw-in-base64-out --payload '{"What is your name?": "Simone", "How old are you?": 39}' output.txt`
- Check the output.txt file which should contain the right answer
