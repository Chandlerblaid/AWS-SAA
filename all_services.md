# All Services
These are all of the main services in AWS as of 2017.

## AWS Global Infrastructure:
	• Region
		○ Country or location; london
	• AZ (Area Zone)
		○ A DC
		○ Usually 2 or more in a region

## Compute:
	• EC2
		○ Elastic Compute Cloud
		○ Virtual machines inside of the cloud platform
	• EC2 Container Service
		○ Manage docker containers at scale
	• Elastic Beanstalk
		○ For developers who do not understand AWS
		○ Just upload the code, and automatically provisions ec2 instances and whatever else is needed.
	• Lambda
		○ Code uploaded to cloud, you control when the code executes
		○ Just worry about your code and when to trigger
	• Lightsail
		○ VPS service (virtual private server)
		○ For people who don’t want to/know how to use aws.
		○ Provisions you a VPC and EC2s with a fixed ip address
		○ Has ssh functionality into EC2 instance.
	• Batch
		○ Batch computing in the cloud

## Storage:
	• S3 (simple storage service)
		○ One of the oldest
		○ There are buckets, you upload your files into these buckets on the cloud
	• EFS (Elastic File System)
		○ Network attached storage
		○ Store files on efs and mount it to multiple VMs
	• Glacier
		○ Data archival
		○ For data that you do not check/need very often
	• Snowball
		○ Way to bring in large amounts of data into the AWS data center
		○ Bringing in terabytes? Might be easier to write it to a disk and have AWS import it manually.
	• Storage Gateway
		○ Virtual appliances that you install in DC to replicate data into s3
		○ 4 different types

## Databases:
	• RDS
		○ Mysql, postgresql, aurora, oracle, etc.
	• DynamoDB
		○ For non-relational dbs
	• Elasticache
		○ Way of caching commonly queried things from your db server
	• Red Shift
		○ Data warehousing or Business intelligence
		○ Designed for Complex queries

## Migration:
	• AWS Migration Hub
		○ A tracking service
		○ Track your applications as you migrate them to AWS
	• Application Discovery Service
		○ Automated set of tools
		○ Detects which apps you have and their dependencies
	• Database Migration Service
		○ Easy way to migrate databases to AWS
		○ Way to visualize migrations as you're doing them
	• Server Migration Service
		○ Similar to DB Migration Service
		○ Helps to migrate virtual and physical servers to AWS cloud
	• Snowball
		○ Between storage and migration
		○ Migrating large data (tb)

## Networking & Content Delivery - NECESSARY for SAA
	• VPC (Virtual Private Cloud)
		○ Virtual DC, Must configure it
		○ MUST KNOW, Fundamental!
	• CloudFront
		○ AWS's Content Delivery Netowork
		○ Can better localize data, make it better accessible from a nearer edge server
	• Route53
		○ AWS DNS service
	• API Gateway
		○ Way of creating your own api's for your other services to talk to
	• Direct Connect
		○ Way of running a dedicated line from your DC to your VPC

## Developer Tools: - Not in DAA or SAA exam
	• CodeStar
		○ Way of getting a group of developers to work together
		○ Project management tool
	• CodeCommit
		○ Place to store your code (source control service)
	• CodeBuild
		○ Once code is ready CodeBuild will compile your code, run tests on it, and produce software packages that are ready to be deployed.
	• CodeDeploy
		○ Automates application deployment to your ec2 instances
		○ Also to lambda functions
	• CodePipeline
		○ Continuous delivery service
		○ Automate steps to release your project
	• X-Ray
		○ Debug and analyze your server-less applications
	• Cloud9
		○ IDE where you can develop inside the aws console

## Management Tools:
	• CloudWatch
	• CloudFormation - Necessary for SAA
		○ Way of scripting Infrastructure
		○ Reusable in different regions/Azs
	• CloudTrail - Necessary for SAA
		○ Everytime you do something in the console it is logged in CloudTrail
		○ Logs changes to the cloud
	• Config - Necessary for SAA
		○ Monitors config of entire AWS environment
		○ Has snapshots/backups
	• OpsWorks
		○ Similar to ElasticBeanstalk
		○ Uses shift and puppet to automate configuration of your environments
	• Service Catalog
		○ Manage a catalog of IT services approved for use
		○ For governance and compliance
	• Systems Manager
		○ Interface for managing AWS resources
	• Trusted Advisor - Necessary for SAA
		○ Vs inspector
		○ Gives advice across different disciplines (security; left your ports open)
		○ Can show you how to save money too
	• Managed Services

## Media Services:
	• Elastic Transcoder
		○ Takes video recorded on mac and resizes it to look good on different devices
	• New, wont be on exams:
		○ MediaConvert
		○ MediaLive
		○ MediaPackage
		○ MediaStore
		○ MediaTailor

## Machine Learning: - NOT IN EXAM
	• SageMaker
		○ Makes it easy for develpers to use deep learning
	• Comprehend
		○ Sentiment analysis around data
	• DeepLens
		○ Artificially aware camera
		○ Physical piece of hardware
	• Lex
		○ Powers Amazon Alexa service
	• Machine Learning
		○ Throw data set in and it will analyze it and whatnot
	• Polly
		○ Text --> Speech
	• Rekognition
		○ Upload a file and tells you what is in that file
	• Amazon Translate
		○ Machine translation service
	• Transcribe
		○ CCs

## Analytics:
	• Athena
		○ Sql-Query items in your s3 bucket
	• EMR (Elastic Map Reduce) - NECESSARY FOR SAA
		○ Processing large amounts of data
		○ Many servicers and chops up data into them for analysis
	• CloudSearch & ElasticSearch Service
	• Kinesis -NECESSARY FOR SAA
		○ Ways of injecting large amounts of data into AWS
	• Kinesis Video Streams
	• QuickSight
		○ Business intelligence tool
	• Data Pipeline
		○ Way of moving data between AWS services
	• Glue
		○ Etl (extract, transform, load)

## Security & Identity & Compliance:
	• IAM (Identity Acess Management) - NECESSARY FOR SAA
	• Cognito
		○ Way of authenticating devices
		○ Can use to request temporary access to certain parts of your AWS app
	• GuardDuty - NOT IN EXAM
		○ Monitors for malicious activity on your AWS account
	• Inspector - NECESSARY FOR SAA
		○ Agent installed on your vm or ec2s, you can run tests against it
		○ Can be scheduled to run at specified times
	• Macie
		○ Scan your s3 bucket looking for things that would contain personal identifiable information (PII) and will alert you
	• Certificate Manager - NECESSARY FOR SAA
		○ SSL certs for free if using AWS and registering through route 53
	• CloudHSM
		○ Hardware Security Modules
		○ Store secret keys here
	• Directory Service - NECESSARY FOR SAA
	• WAF (Web application Firewall) - NECESSARY FOR SAA
		○ Layer 7 firewall
		○ Stops XSS, sql injection, etc. looking at application layer for vulnerabilities
	• Shield
		○ Get it by default for a lot of other services
		○ DDoS mitigation
	• Artifact
		○ Ordered and compliance
		○ Portal for downloading on-demand compliance reports

## Mobile Services: - NOT IN EXAM
	• Mobile Hub
		○ Sets up your environment for mobile apps
	• Pinpoint
		○ Location ( push near this location… )
	• AWS AppSync
		○ Automatically updates data of mobile users
	• Device Farm
		○ Way of testing your apps on real life devices
	• Mobile Analytics

## AR / VR (Sumerian):  - NOT IN EXAM
	• Sumerian

## Application Integration:
	• Step Functions
	• Amazon MQ
	• SNS (Simple Notification Service) - NECESSARY FOR SAA
		○ Notification service
	• SQS (Simple Queue Service) - NECESSARY FOR SAA
		○ Way to decoupling your infrastructure
	• SWF (Simple Workflow Service) - NECESSARY FOR SAA

## Customer Engagement:
	• Connect
	• Simple Email Service

## Business Productivity:
	• Alexa for Business
	• Chime
		○ Video conferencing, like google hangouts
	• Work Docs - NECESSARY FOR SAA
		○ Like dropbox
	• WorkMail
		○ Like Office365

## Desktop & App Streaming: - NOT IN EXAM
	• Workspaces
	• AppStream 2.0

## Internet of Things: - NOT IN EXAM
	• iOT
	• iOT Device Management
	• Amazon FreeRTOS
	• Greengrass

## GameLift: - NOT IN EXAM
	• Gaming stuffs
