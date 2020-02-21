# EC2

## What is EC2?
- Amazon Elastic Compute Cloud
- A web service that provides resizable compute capacity in the cloud.
- Reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.
- Basically just Virtual machines in the cloud
- Allowing you to pay only for the capacity that you actually use, changing the economics of computing.
- Provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios

## EC2 Options
- On Demand - pay a fixed rate by the hour (or by the second) with no commitment.
	○ Users that want the low cost and flexibility w/o any up-front payment or long-term commitment.
	○ Apps with short term, spiky, or unpredictable workloads that can't be interrupted.
	○ Apps being developed or tested on Amazon EC2 for the first time
- Reserved - provide you with a capacity reservation, and offer a significant discount on the hourly charge for an instance. 1 year or 3 year terms.
	○ Apps w/ steady state or predictable usage
	○ Apps that require reserved capacity
	○ Users able to make upfront payments to reduce their total computing costs even further
	○ Three different types:
				1) Standard RI's
				2) Convertible RI's
				3) Scheduled RI's
- Spot - enable you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times.
	○ Apps that have flexible start and end times
	○ Apps that are only feasible at very low compute prices
	○ Users w/ urgent computing needs for large amounts of additional capacity
- Dedicated Hosts - Physical EC2 server dedicated for your use. Dedicated hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.
	○ Useful of regulatory requirements that may not support multitenant virtualization
	○ Great for licensing which does not support multi-tenancy or cloud deployments
	○ Can be purchased On-Demand (hourly)
	○ Can be purchased as a Reservation for up to 70% off the On-Demand price.

## EC2 Instance Types:
- |Family|Specialty|Use-case|
	|------|---------|--------|
	|D2	|Dense Storage|	Fileservers/Data Warehousing/Hadoop|
	|R4	|Memory Optimized (RAM)|	Memory Intensive Apps/DBs|
	|M4	|General Purpose|	Application Servers|
	|C4	|Compute Optimized|	CPU Intensive Apps/DBs|
	|G2	|Graphics Intensive|	Video Encoding/3D Application Streaming|
	|I2	|High Speed Storage|	NoSQL DBs Data Warehousing etc.|
	|F1	|Field Programmable Gate Array (FPGA)|	Hardware acceleration for your code|
	|T2	|Lowest cost| General Purpose	Web servers/Small DBs|
	|P2	|Graphics/General |Purpose GPU (Pics)	Machine Learning, Bit Coin Mining etc|
	|X1	|Memory Optimized	|SAP HANA/Apache Spark etc|

- T2-micro is the most commonly used
- How to remember them (corny):
	○ DR. Mc GIFT PX

## What is EBS (Elastic Block Store)?
- Allows you to create storage volumes and attach them to EC2 instances. Once attached, you can create a file system on top of these volumes, run a db, or use them in any other way you would use a block device.
- Placed in a specific Availability Zone, where they are automatically replicated to protect you from the failure of a single component.
- Block based storage
- The EBS volume must be in the same availability zone as the EC2 instance it will be mounted to.
- You can change EBS volume sizes on the fly (while the machine is running), including changing the size and storage type.
- To move an EC2 volume from one AZ to another, take a snap or an image of it, then copy it to the new AZ.
- Snapshots of root device volumes:
	○ Snapshots are saved on S3
	○ Snapshots are point in time copies of Volumes
	○ They are incremental, meaning that only the blocks that have changed since the last snapshot are moved to S3
	○ To create a snapshot for EBS volumes that serve as root devices, you should stop the instance before taking the snapshot. Although you can still take a snap while the instance is running.
	○ You can create AMI's from both Volumes and Snapshots.
	○ Snapshots of encrypted volumes are encrypted automatically.
	○ Volumes restored from encrypted snapshots are encrypted automatically..
	○ You can share snapshots, but only if they are unencrypted.
		□ Can be shared w/ other AWS accounts or made public
- Amazon Machine Image (AMI)


## Elastic Block Store (EBS) Volume Types
- SSDs:
	○ General purpose SSD (GP2)
		□ General purpose, balances both price and performance.
		□ Ration of 3 IOPs per GB w/ up to 10,000 IPS and the ability to burst up to 3,000 IOPS for extended periods of time for volumes at 3334 GiB and above
	○ Provisioned IOPS SSD (IO1)
		□ Designed for I/O intensive applications such as large relational or NoSQL databases.
		□ Use if you need more than 10,000 IOPS.
		□ Can provision up to 20,000 IOPS per volume
- Magnetic Storage:
	○ Throughput Optimized HDD (ST1)
		□ Big data
		□ Data warehouses
		□ Log processing
		□ Cannot be a boot volume
	○ Cold HDD (SC1)
		□ Lowest cost storage for infrequently accessed workloads
		□ File servers
		□ Cannot be boot volume
	○ Magnetic (Standard)
		□ Lowest cost per gigabyte of all EBS volume types that is bootable.
		□ Ideal for workloads where data is accessed infrequently, and apps where the lowest storage cost is important

## Security Groups
- A security group is a virtual firewall
- One instance can have multiple security groups
- First line of defense against hackers.
- Any change you make to a rule in a security group takes effect immediately.
- Security groups are STATEFUL.
	○ Anything that is allowed in, will be allowed out.
		□ Inbound rules automatically add an outbound rule.
	○ E.g. if you delete rule for outbound traffic, http requests will still be resolved to the host.
- Everything is denied by default, cannot deny a specific ip or type of traffic directly, you can only allow.
- You can have any number of ec2 instances within a security group.

## Labs
- One Subnet = One availability zone
- What happens if you delete an EC2 instance, what happens to the EBS volume attached to that EC2 instance?
	○ By default the EBS volume will be deleted unless you untick the delete on termination option when attaching the volume.
- System Status Check
	○ Checking that your hypervisor is healthy
- Instance Status Check
	○ Checking that your software setup in the VM is healthy
- Cannot encrypt default Amazon Machine Images
	○ Workaround is to provision the instance, then copy the machine image and when copying, encrypt it.
	○ Additional volumes can be encrypted though
- Deleting

## Amazon Machine Image (AMI) Types (EBS vs. Instance Store):
- All AMIs are either backed by Amazon Elastic Block Store (EBS) or by Instance store.
- You Can select your AMI based on;
	○ Region
	○ Operating system
	○ Architecture (32bit vs 64bit)
	○ Launch permissions
	○ Storage for the Root device (Root Device Volume)
		□ Instance Store (Ephemeral Storage)
		□ EBS Backed Volumes
- EBS Volumes:
	○ The root device for an instance launched from the AMI is an Amazon EBS volume created from an Amazon EBS snapshot.
- Instance Store Volumes:
	○ The root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3.
- EBS	Instance Store
		The root device for an instance launched from the AMI is an Amazon EBS volume created from an Amazon EBS snapshot.	The root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3.
		Faster provisioning time because it is created from a snapshot	Slower provisioning because it created from files on an S3 bucket.
		Can stop the instance. When taking snapshot Amazon will stop instance automatically.	Cannot stop the instance. Can only reboot or terminate.
		If root volume you can take a snapshot of the image in its stop state.	EPHEMERAL STORAGE. Less durability than EBS. Restricted instance types also.
		Stopping and starting again allows you to switch Hosts if the underlying hypervisor fails.	This is not allowed on Instance Store. If the hypervisor fails, that instance is lost.
		Can detach an image volume from ab EC2 instance and possibly attach to another EC2 instance.	This is not possible with Instance store (ephemeral storage)
		On termination you have the option to keep the root device volume	On termination the root volume is deleted

## Elastic Load Balancer - LAB
- Application Load Balancers (new)
	○ Work at layer 7 (Application Layer)
	○ Perfered LB
	○ Good for HTTP/HTTPS
- Classic Load Balancers (on exam)
	○ Layer 4 LB
	○ Makes its decisions at the TCP level
	○ Can do some layer 7 routing
	○ Make external for web-traffic serving
	○ Will cost you money if left on
- Instances monitored by ELB are reported as; InService or OutofService
- Health Checks check the instance health by talking to it
- Have their own DNS name. You are never given an IP address
	○ Amazon manages IP

## EXAM TIPS:
- Know the difference between
	○ On demand
	○ Spot
	○ Reserved
	○ Dedicated hosts
- Remember w/ spot instances
	○ If you terminate the instance, you pay for the hour
	○ If AWS terminates the spot instance, you get the hour it was terminated for free.
- Placement groups cannot be deployed across multiple AZ's
- EBS consists of;
	○ Ssd, gp2 (up to 10,000 iops)
	○ Ssd, io1 (more than 10,000 iops)
	○ Hdd, st1 (frequently accessed workloads)
	○ Hdd, sc1 (less frequently accessed data)
	○ Hdd, standard (cheap, infrequently accessed storage)
- You cannot mount 1 EBS volume to multiple EC2 instances, instead use EFS for shared storage.
- Encrypted images cannot be shared
- EBS Snapshots are backed up to S3 incrementally
	○ `aws ec2 create-snapshot`
- You cannot delete the snapshot of an EBS Volume that is used as a root device of a registered AMI
- DR. Mc GIFT PX (Acronym for EC2 Instance types)
- One subnet = One availability zone
- Cloudwatch
	○ Standard Monitoring = 5 mins
	○ Detailed Monitoring = 1 min
	○ CloudWatch is for performance monitoring
	○ CloudTrail is for auditing
	○ Dashboards - Create dashboards to see what is happening with your AWS evnironment
	○ Alarms - Allow you to set Alarms that notify you when particular thresholds are hit.
	○ Events - Helps you to respond to state changes in your AWS resources.
	○ Logs - Helps you to aggregate, monitor, and store you logs
- Roles:
	○ More secure than storing you access key and secret access key on individual EC2 instances.
	○ Easier to manage
	○ Can be assigned to an EC2 instance AFTER it has been provisioned using both the command line and the AWS console.
		□ Can update role policies as well
	○ Roles are universal, you can use from any region
- Instance Meta-data:
	○ Used to get information about an instance (such as public IP)
	○ Curl http://169.254.169.254/latest/meta-data/
- EFS (Elastic File System)
	○ Supports NFSv4
	○ You only pay for the storage you use (no pre-provisioning required)
	○ Can scale up to the petabytes
	○ Can support thousands of concurrent NFS connections
	○ Data is stored across multipole AZ's w/in a region
	○ Read After Write Consistency
- Lambda:
	○ AWS takes care of the provisioning and managing the servers that you use to run your code. You don't have to worry about OS', patching, scaling, etc. You can use Lambda in the following ways:
		□ As an event-driven compute service where AWS Lambda runs your code in response to events. These events could be changes to data in S3 or a DynamoDB table.
		□ As a compute service to run your code in response to HTTP requests using API Gateway or API calls made using AWS SDKs.
