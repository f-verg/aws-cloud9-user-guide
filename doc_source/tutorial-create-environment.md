# Step 1: Create an environment<a name="tutorial-create-environment"></a>

\(First step of [Tutorial: Hello AWS Cloud9 \(console\)](tutorial.md)\)

In this step, you use the AWS Cloud9 console to create and then open an AWS Cloud9 development environment\.

**Note**  
If you have already created the environment that you want to use for this tutorial, open that environment and skip ahead to [Step 2: Basic tour of the IDE](tutorial-tour-ide.md)\.

In AWS Cloud9, a *development environment* \(or only an *environment*\) is a place where you store your development project's files and where you run the tools to develop your applications\. In this tutorial, you create a special kind of environment called an *EC2 environment*, and then work with the files and tools in that environment\.

## Create an EC2 Environment with the console<a name="tutorial-create-environment-console"></a>

1. Sign in to the AWS Cloud9 console:
   + If you're the only one that using your AWS account or you're an IAM user in a single AWS account, go to [https://console\.aws\.amazon\.com/cloud9/](https://console.aws.amazon.com/cloud9/)\.
   + If your organization uses AWS Single Sign\-On \(AWS SSO\), ask your AWS account administrator for sign\-in instructions\.
   + If you're using an AWS Educate Starter Account, see [Use an AWS Educate Starter Account to sign in to the AWS Cloud9 console](setup-student.md#setup-student-sign-in-ide) in *Individual Student Signup*\.
   + If you're a student in a classroom, ask your instructor for sign\-in instructions\.

1. After you sign in to the AWS Cloud9 console, in the top navigation bar, choose an AWS Region to create the environment in\. For a list of available AWS Regions, see [AWS Cloud9](https://docs.aws.amazon.com/general/latest/gr/rande.html#cloud9_region) in the *AWS General Reference*\.  
![\[AWS Region selector in the AWS Cloud9 console\]](http://docs.aws.amazon.com/cloud9/latest/user-guide/images/console-region.png)

1. Choose the large **Create environment** button in one of the locations shown\.

   If you have no AWS Cloud9 environments yet, the button is shown on a welcome page\.  
![\[Welcome page in the AWS Cloud9 console\]](http://docs.aws.amazon.com/cloud9/latest/user-guide/images/console-welcome-new-env.png)

   If you already have AWS Cloud9 environments, the button is shown as follows\.  
![\[Create environment button in the AWS Cloud9 console\]](http://docs.aws.amazon.com/cloud9/latest/user-guide/images/console-new-env.png)

1. On the **Name environment** page, for **Name**, enter a name for your environment\. For this tutorial, use `my-demo-environment`\.

1. For **Description**, enter something about your environment\. For this tutorial, use `This environment is for the AWS Cloud9 tutorial.`

1. Choose **Next step**\.

1. On the **Configure settings** page, for **Environment type**, choose one of the following options to create an EC2 backed environment:
   + **Create a new EC2 instance for environment \(direct access\)** – Launches an Amazon EC2 instance that AWS Cloud9 can connect to directly over SSH\.
   + **Create a new no\-ingress EC2 instance for environment \(access via Systems Manager\)** – Launches an Amazon EC2 instance that doesn't require any open inbound ports\. AWS Cloud9 connects to the instance through [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html)\.
     + If you select the **access via Systems Manager** option, a service role and an IAM instance profile are automatically created to allow Systems Manager to interact with the EC2 instance on your behalf\. You can view the names of both in the **Service role and instance profile for Systems Manager access** section further down the interface\. For more information, see [Accessing no\-ingress EC2 instances with AWS Systems Manager](ec2-ssm.md)\. 
**Warning**  
Creating an EC2 instance for your environment might result in possible charges to your AWS account for Amazon EC2\. There is no additional cost to use Systems Manager to manage connections to your EC2 instance\.

1. For **Instance type**, leave the default choice\. This choice has relatively low RAM and vCPUs, which is sufficient for this tutorial\.
**Warning**  
Choosing instance types with more RAM and vCPUs might result in additional charges to your AWS account for Amazon EC2\.

1. For **Platform**, choose the type of Amazon EC2 instance that you want: **Amazon Linux 2**, **Amazon Linux**, or **Ubuntu**\. AWS Cloud9 creates the instance and then connects the environment to it\.
**Important**  
We recommend that you choose the **Amazon Linux 2** option for your EC2 environment\. As well as providing a secure, stable, and high\-performance runtime environment, Amazon Linux 2 AMI includes long\-term support through 2023\.  
Standard support for the previous version of Amazon Linux AMI discontinued on December 31, 2020\. Now this version only receives maintenance support\. For more information, see the [Amazon Linux 2 page](https://aws.amazon.com/amazon-linux-2/)\.

1. Choose a value for **Cost\-saving setting**\. When all web browser instances that are connected to the IDE for the environment are closed, AWS Cloud9 waits the amount of time specified and then shuts down the Amazon EC2 instance for the environment\. 
**Warning**  
Choosing a longer time period might result in more charges to your AWS account\.

1. Expand **Network settings \(advanced\)**\.

   AWS Cloud9 uses Amazon Virtual Private Cloud \(Amazon VPC\) to communicate with the newly created Amazon EC2 instance\. For this tutorial, we recommend that you don't change the preselected default settings\. With the default settings, AWS Cloud9 attempts to automatically use the default VPC with its single subnet in the same AWS account and AWS Region as the new environment\.

   You can find more information about Amazon VPC choices in [Create an EC2 Environment with the Console](create-environment-main.md#create-environment-vpc-step), and in [VPC settings for AWS Cloud9 Development Environments](vpc-settings.md)\.

1. Add up to 50 tags by supplying a **Key** and a **Value** for each tag\. The tags are attached to the AWS Cloud9 environment as resource tags, and are propagated to the following underlying resources: the AWS CloudFormation stack, the Amazon EC2 instance, and Amazon EC2 security groups\. You can find information about tags in [Control Access Using AWS Resource Tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *[IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/)*\. Also see the [advanced information](tags.md) about tags\.
**Warning**  
If you update these tags after you create them, the changes are not automatically propagated to the underlying resources\. For more information, see [Propagating tag updates to underlying resources](tags.md#tags-propagate) in the advanced information about [tags](tags.md)\.

1. Choose **Next step**\.

1. On the **Review** page, choose **Create environment**\. Wait while AWS Cloud9 creates your environment\. This can take several minutes\.
**Note**  
If account creation fails, a banner is displayed at the top of the console page\. Additionally, the card for the environment, if it exists, indicates that environment creation failed\.

After AWS Cloud9 creates your environment, it displays the AWS Cloud9 IDE for the environment\.

If AWS Cloud9 doesn't display the IDE after at least five minutes, there might be a problem with your web browser, your AWS access permissions, the instance, or the associated virtual private cloud \(VPC\)\. For possible fixes, see [Cannot open an environment](troubleshooting.md#troubleshooting-env-loading) in *Troubleshooting*\.

## Next step<a name="tutorial-create-env-next"></a>

[Step 2: Basic tour of the IDE](tutorial-tour-ide.md)