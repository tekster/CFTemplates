
# Demo SimpleVPC AWS CDK template.  Creates VPC and related dependencies

This creates a VPC in the region specified by AWS_PROFILE or AWS_REGION 
vpc-demo-audit-teksterDemo bucket is required for logging (pre-created)
adopted from https://stories.fylehq.com/p/creating-aws-vpc-using-cdk-with-python
As this template includes an EC2 Internet Gateway, recurring fees occur.
**a pre-created S3 Bucket named: "vpc-demo-audit-teksterDemo"**
is required for logging purposes.
Additionally, a NAT Gateway (EC2 Instance) is created, incurring
monthly fees.  Delete when no longer required.

The `cdk.json` file tells the CDK Toolkit how to execute your app.

This project is set up like a standard Python project.  The initialization
process also creates a virtualenv within this project, stored under the `.venv`
directory.  To create the virtualenv it assumes that there is a `python3`
executable in your path with access to the `venv`
package. If for any reason the automatic creation of the virtualenv fails,
you can create the virtualenv manually.

To manually create a virtualenv on MacOS and Linux:

```
$ python3 -m venv .venv
```

After the init process completes and the virtualenv is created, you can use the following
step to activate your virtualenv.

```
$ source .venv/bin/activate
```

Once the virtualenv is activated, you can install the required dependencies.

```
$ pip install -r requirements.txt
```

At this point you can now synthesize the CloudFormation template for this code.

```
$ cdk synth
```

To add additional dependencies, for example other CDK libraries, just add
them to your `setup.py` file and rerun the `pip install -r requirements.txt`
command.

## Useful commands

 * `cdk ls`          list all stacks in the app
 * `cdk synth`       emits the synthesized CloudFormation template
 * `cdk deploy`      deploy this stack to your default AWS account/region
 * `cdk diff`        compare deployed stack with current state
 * `cdk docs`        open CDK documentation
 * `cdk destroy`     remove Cloudformation Template and dependencies

Enjoy!
