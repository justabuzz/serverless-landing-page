# AWS-based Serverless Landing Page
An AWS CloudFormation template for creating a serverless landing page website.

Author: [@justabuzz] | http://www.onclouds.com.au/

## Overview
Create a landing page in a snap! How many times did you have to create a landing page with a Contact Us form? It's one of those tasks that tend to repeat themselves. And how can you guage what sort of server to provision for this page? If your client plans promoting it at some point then you need to ensure you provision the right server for the time job.

Enter Serverless Landing Page! By utilising serverless infrastructure you avoid the provisioning part and focus solely on your business problem. And by using this AWS CloudFormation template you also avoid the initial setup of your serverless landing page. Leaving yourself with the most important task - design the actual landing page. That's it! The rest is ready! :)

## Features
The CloudFormation template provisions the following AWS resources:
* S3 Bucket to store static content
* AWS API Gateway to receive submitted Contact Us form data and pass it to AWS Lambda
* AWS Lambda to publish the submitted data via AWS SNS
* AWS SNS to send the form data to the designated email address

The repository includes an initial version for the landing page HTML, which includes:
* index.html: a basic landing page with a Contact form and all the code to submit it to the API Gateway
* error.html: an error page if users accidentally reach the wrong URL on the site

## Infrastructure design
IMAGE HERE

## Requirements
Make sure the AWS region you deploy this on supports the following AWS resources:
* AWS Lambda
* AWS API Gateway

You can check that in the [AWS Region Table].

## How To Use
* Run the CloudFormation template to provision all necessary AWS resources. In the process the system will ask you for:
    * Stack Name
    * Hosted Zone - domain (or sub-domain) for the landing page - this is important in order to enable S3-based hosting
    * Email Receipient - recipient of the submitted form data
* Grab the API Gateway 'prod' endpoint URL - you can do this by accessing the prod stage in API Gateway console
* Replace the URL place holder in index.html with the endpoint URL
* Upload to the S3 bucket the two files index.html and error.html

You will find your new serverless landing page site URL under the CloudFormation template's Outputs tab.

That's it! You have a fully functional serverless landing page!

## What To Do Next
You probably want to customise the site's URL. Here's how you can do that using [Route53]. Remember that you have to use the HostedZone value you have entered.

You may also configure AWS CloudFront to CDN your landing page. I didn't include that as part of the CloudFormation as it may incur unecessary costs to some users. Here's how to [configure CloudFront with S3].

That's it! Enjoy!

   [@justabuzz]: <https://github.com/justabuzz/>
   [AWS Region Table]: <https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/>
   [Route53]: <http://docs.aws.amazon.com/gettingstarted/latest/swh/getting-started-configure-route53.html>
   [configure CloudFront with S3]: <http://docs.aws.amazon.com/gettingstarted/latest/swh/getting-started-create-cfdist.html>
