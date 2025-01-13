# CloudFormation Templates for AWS Sample Deployment:
Content sourced from various locations, including:<br>
**Dependencies:** my-key-pair.pem (pre-created) <br>
  AWS-CLIv2 Installation with aws-config properly configured

# == VPC Creation == #
Filename: CodeBuildVPC.yaml 

> cd /Users/robertescamilla/Documents/Source/CFTemplates<br>

> export AWS_REGION=us-west-1<br>

> aws cloudformation create-stack --stack-name CodebuildVPC --template-body file://CodeBuildVPC.yaml --parameters ParameterKey=EnvironmentName,ParameterValue=CodebuildVPC <br>

> aws cloudformation delete-stack --stack-name CodebuildVPC

# == EC2 Deployment == #
**ec24.yaml:** creates Ec2 instance with latest AMI + Elastic IP <br>
**ec2.yaml:** requires distinct AMI as parameter, to be updated each deployment<br>

> aws cloudformation create-stack --stack-name ec2-demo --template-body file://ec24.yaml \
> --parameters ParameterKey=AvailabilityZone,ParameterValue=us-west-1b \
> ParameterKey=EnvironmentType,ParameterValue=dev \
> ParameterKey=KeyPairName,ParameterValue=my-key-pair

> aws cloudformation delete-stack --stack-name ec2-demo

> ssh -i "my-key-pair.pem" ec2-user@ec2-50-18-154-177.us-west-1.compute.amazonaws.com<br>
> *get actual EC2 hostname from AWS console or EC2 Query*
