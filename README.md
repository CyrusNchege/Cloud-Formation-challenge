# Cloud-Formation-challenge
This is a challenge to Create a Cloud Formation template that provisions a VPC with its necessary components and an EC2 instance within the VPC.

## Getting Started
These instructions will get you a copy of the project up and running on your own

### Prerequisites
Aws account

Aws CLI and configured in your machine

### Installing
1. Clone the repo
```
git clone https://github.com/CyrusNchege/Cloud-Formation-challenge 

cd Cloud-Formation-challenge
```

In this directory you will find `challenge.yml` file which is the cloud formation template

2. Deploy the template
```
aws cloudformation deploy --template-file challenge.yml --stack-name challenge 


```
![deployterm](/images/term-deploy.png)

3. Check the status of the stack
```
aws cloudformation describe-stacks --stack-name challenge --query 'Stacks[0].StackStatus'

```

## Thing to note

When Creating the stack, you have to check the aws region you are in and change the region in the `challenge.yml` file to match your region

Also the keypair name should be changed to match your keypair name in your aws account.

The AMI used is for the `us-west-2` region, if you are in a different region, you have to change the AMI to match your region.

When you run to any problem, you can delete the stack and try again.

```
 aws cloudformation delete-stack --stack-name challenge
 ```

 Or Describe the stack to see what went wrong

 ```
aws cloudformation describe-stack-events --stack-name challenge
```

## Results
After the stack is created, you can check the output of the stack to get the public IP of the EC2 instance

```
aws cloudformation describe-stacks --stack-name challenge --query 'Stacks[0].Outputs'

```
You can see stack on the aws console

![stack](/images/stack-created.png)

And the stack resources

![resources](/images/stack-resources.png)

You can also check the EC2 instance in the aws console

![ec2](/images/instance-created.png)

You can ssh into the EC2 instance using the public IP and the keypair you used to create the stack

```
ssh -i <keypair> ec2-user@<public-ip>
```


## Destroying the stack

If you are doing this for testing purposes, you can delete the stack to avoid charges

```
aws cloudformation delete-stack --stack-name challenge
```

Congratulations, you have successfully created a cloud formation template that provisions a VPC with its necessary components and an EC2 instance within the VPC.

## Author
Cyrus Chege


If you have any questions or improvements, feel free to create an issue or reach out to me on [Email](cyruschegecc@gmail.com)