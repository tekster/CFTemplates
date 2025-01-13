# CloudFormation Templates for AWS Sample Deployment:
Content sourced from various locations, including:
  Requires: my-key-pair.pem (pre-created)

# == VPC Creation == #
######################
cd /Users/robertescamilla/Documents/Source/CFTemplates
export AWS_REGION=us-west-1
aws cloudformation create-stack --stack-name CodebuildVPC --template-body file://CodeBuildVPC.yaml --parameters ParameterKey=EnvironmentName,ParameterValue=CodebuildVPC
aws cloudformation delete-stack --stack-name CodebuildVPC

# == EC2 Deployment == #
########################
# ec24.yaml: creates Ec2 instance with latest AMI + Elastic IP
# ec2.yaml: requires distinct AMI as parameter, to be updated each deployment

aws cloudformation create-stack --stack-name ec2-demo --template-body file://ec24.yaml \
--parameters ParameterKey=AvailabilityZone,ParameterValue=us-west-1b \
ParameterKey=EnvironmentType,ParameterValue=dev \
ParameterKey=KeyPairName,ParameterValue=my-key-pair

aws cloudformation delete-stack --stack-name ec2-demo

ssh -i "my-key-pair.pem" ec2-user@ec2-50-18-154-177.us-west-1.compute.amazonaws.com
