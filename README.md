# Infiniti
To infiniti and beyond!

# Directions
To create the website, you will be creating a CloudFormation stack. This can be done by running the command below or clicking on the Launch Stack button. Running the command assumes the AWS CLI is installed and configured with a user that has sufficient permissions to create the necessary AWS resources.

```
aws cloudformation create-stack \
    --stack-name JoeGardner \
    --template-body file://./homework.yml \
    --capabilities "CAPABILITY_IAM" \
    --region us-east-1
```

[![launch button](https://d2908q01vomqb2.cloudfront.net/1b6453892473a467d07372d45eb05abc2031647a/2017/08/17/2-launch.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=JoeGardner&templateURL=https://s3.amazonaws.com/public-joehack3r-com/infiniti/homework.yml)

The URL for the web servers can be accessed from the CloudFormation Outputs tab or by running the following command (assumes jq is installed):
```
aws cloudformation describe-stacks \
    --stack-name JoeGardner | \
    jq .Stacks[0].Outputs[0].OutputValue
```
If jq is not installed, the following also works:
```
aws cloudformation describe-stacks \
    --stack-name JoeGardner | \
    grep OutputValue | \
    sed -e "s/.*\"OutputValue\": //g"
```
