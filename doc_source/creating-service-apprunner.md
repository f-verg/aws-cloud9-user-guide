# Creating App Runner services<a name="creating-service-apprunner"></a>

You can create an App Runner service in AWS Toolkit by using the **AWS Explorer**\. After you choose to create a service in a specific AWS Region, numbered steps provided by the AWS Toolkit's command pane guide you through the process of configuring the service instance where your application runs\. 

Before creating an App Runner service, make sure that you've completed the [prerequisites](using-apprunner.md#apprunner-prereqs)\. This includes providing the relevant IAM permissions and confirming the specific source repository that you want to deploy\.<a name="create-service"></a>

# To create an App Runner service<a name="create-service"></a>

1. Open AWS Explorer, if it isn't already open\.

1. Right\-click the **App Runner** node and choose **Create Service**\.

   The AWS Toolkit command pane displays\.

1. For **Select a source code location type**, choose **ECR** or **Repository**\. 

   If you choose **ECR**, you specify a container image in a repository maintained by Amazon Elastic Container Registry\. If you choose **Repository**, you specify a source code repository that's maintained by a supported repository provider\. Currently, App Runner supports [GitHub](https://github.com/) as a source code repository provider\. 

## Deploying from ECR<a name="deploying-from-ECR"></a>

1. For **Select or enter an image repository**, choose or enter the URL of the image repository that's maintained by your Amazon ECR private registry or the Amazon ECR Public Gallery\.
**Note**  
If you specify a repository from the Amazon ECR Public Gallery, make sure that automatic deployments are turned off because App Runner doesn't support automatic deployments for an image in an ECR Public repository\.  
Automatic deployments are switched off by default, and this is indicated when the icon on the command pane header features a diagonal line through it\. If you chose to switch on automatic deployments, a message informs you that this option can incur additional costs\. 

1. If the step in the command pane reports that **No tags found**, you need to go back a step to select a repository that contains a tagged container image\.

1. If you're using an Amazon ECR private registry, you require the ECR access role, **AppRunnerECRAccessRole**, that allows App Runner to access Amazon Elastic Container Registry \(Amazon ECR\) images in your account\. Choose the "\+" icon on the command pane header to automatically create this role\. \(An access role isn't required if your image is stored in Amazon ECR Public, where images are publicly available\.\) 

1. For **Port**, enter the IP port that's used by the service \(Port `8000`, for example\)\.

1. For **Configure environment variables**, you can specify a file that contains environment variables that are used to customize behavior in your service instance\. Or you can skip this step\.

1. For **Name your service**, enter a unique name without spaces and press **Enter**\.

1. For **Select instance configuration**, choose a combination of CPU units and memory in GB for your service instance\.

   When your service is being created, its status changes from **Creating** to **Running**\.

1.  After your service starts running, right\-click it and choose **Copy Service URL**\. 

1. To access your deployed application, paste the copied URL into the address bar of your web browser\. 

## Deploying from a remote repository<a name="deploying-from-repository"></a>

1.  For **Select a connection**, choose a connection that links GitHub to AWS\. The connections that are available for selection are listed on the **GitHub connections** page on the App Runner console\. 

1.  For **Select a remote GitHub repository**, choose or enter a URL for the remote repository\.

    Remote repositories that are already configured with AWS Cloud9 source control management are available for selection\. You can also paste a link to the repository if it's not listed\.

1. For **Select a branch**, choose which Git branch of your source code that you want to deploy\.

1. For **Choose configuration source**, specify how you want to define your runtime configuration\.

   If you choose **Use configuration file**, your service instance is configured by settings that are defined by the `apprunner.yaml` configuration file\. This file is in the root directory of your application’s repository\.

   If you choose **Configure all settings here**, use the command pane to specify the following:
   + **Runtime**: Choose **Python 3** or **Nodejs 12**\.
   + **Build command**: Enter the command to build your application in the runtime environment of your service instance\.
   + **Start command**: Enter the command to start your application in the runtime environment of your service instance\.

1. For **Port**, enter the IP port that's used by the service \(Port `8000`, for example\)\.

1. For **Configure environment variables**, you can specify a file that contains environment variables that are used to customize behavior in your service instance\. Or you can skip this step\.

1. For **Name your service**, enter a unique name without spaces and press **Enter**\.

1. For **Select instance configuration**, choose a combination of CPU units and memory in GB for your service instance\.

   When your service is being created, its status changes from **Creating** to **Running**\.

1. After your service starts running, right\-click it and choose **Copy Service URL**\.

1. To access your deployed application, paste the copied URL into the address bar of your web browser\.

**Note**  
If your attempt to create an App Runner service fails, the service shows a status of **Create failed** in **AWS Explorer**\. For troubleshooting tips, see [When service creation fails](https://docs.aws.amazon.com/apprunner/latest/dg/manage-create.html#manage-create.failure) in the *App Runner Developer Guide*\.