# Application Services

## SQS:
	- A web service that gives you access to a message queue that can be used to store messages while waiting for a computer to process them.
	- Pull based (must poll for the information)
	- Messeges are 256KB in size
	- Messages can be kept in the queue from 1 minute to 14 days. Default is 4 days.
	- Visibility time out is the amount of time that the message is invisible in the SQS queue after a reader picks up that message. Provided the job is processed before the visibility time out expires, the message will then be deleted from the queue. If the job is not processed within that time, the message will become visible again and another reader will process it. This could result in the same message being delivered twice.
	- Visibility time out max is 12 hours
	- SQS guarantees that your messages will be processed at least once.
	- SQS long polling is a way to retrieve messages from your SQS queues. While the regular short polling returns immediately, even if the message queue being polled is empty, long polling doesn’t return a response until a message arrives in the message queue, or the long poll times out.
	- Queue's can either be standard or FIFO.

## SWF vs. SQS:
	- A domain refers to a collection of related workflows.
	- SQS	SWF
	Retention period; 14 days	Retention period 1 year
	Offers a message-oriented API	Offers a task-oriented API
	Need to handle duplicated messages	A task is assigned only once/never duplicated
	Need to implement your own app-level tracking, especially if your app uses multiple queues.	Keeps track of all tasks and events in an application.

## SWF Actors:
	- Workflow Starters - an app that can initiate a workflow. Could be your e-commerce website when placing an order or a mobile app searching for bus times.
	- Deciders - Control the flow of activity tasks in a workflow execution. If something has finished in a workflow (or fails) a Decider decides what to do next.
		○ If then control logic
	- Activity Workers - Carry out the activity tasks.

## SNS:
	- Types of subscribers;
		○ HTTP(S)
		○ Email
		○ Email-JSON
		○ SQS
		○ Application
		○ Lambda

## SNS vs. SQS:
	- SNS	SQS
	Push-based	Pull-based (Polls)

## Elastic Transcoder:
	- Media Transcoder in the cloud.
	- Converts media files from their original source format to different formats for smartphones, tablets, PCs etc.
	- Pay is based on the minutes that you spend transcoding and the resolution at which you transcode.

## Kinesis:
	- Streams
		○ Data producers --> Streams
		○ Split into shards
		○ 24 hour - 7 Days retention
		○ Pipe this data to consumers (ec2s)
	- Firehouse
		○ Data producers --> Firehouse
		○ Wont hold the data, can be queried using lambda
		○ Data sent straight to S3
	- Analytics
		○ Sits on top, allowing sql queries on both Streams or Firehouse.
		○ Sends data to S3/Redshift/Elastic Search


