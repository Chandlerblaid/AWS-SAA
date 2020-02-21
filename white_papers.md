# White Papers

Security Processes (75 pages, 20% of exam):
	- Shared Security Model
		○ AWS is responsible for securing the underlying infrastructure that supports the cloud, and you're responsible for anything you put on the cloud or connect to the cloud.
	- AWS Security Responsibilities
		○ AWS is responsible for protecting the global infrastructure that runs all of the services offered in the AWS cloud. This infra is comprised of the hardware, software, networking, and facilities that run AWS services.
		○ AWS is responsible for the security configuration of its products that are considered managed service; DynamoDB, RDS, Redshift, Elastic MapReduce, Workspaces.
	- Customer Security Responsibilities
		○ IAAS - such as EC2, VPC, and S3 are completely under your control and require you to perform all of the necessary security configuration and management tasks.
		○ Managed Services, AWS is responsible for patching, antivirus, etc., however you are responsible for account management and user access. It's recommended that MFA be implemented, communicate to these services using SSL/TLS and that API/user activity logging be setup with CloudTrail.
	- Storage Decommissioning
		○ When a storage device has reached the end of its useful life, AWS procedures include a decommissioning process that is designed to prevent customer data from being exposed to unauthorized individuals.
		○ AWS uses the techniques detailed in DoD 5220.22-M or NIST 800-88 to destroy data as part of the decommissioning process.
		○ All decommissioned magnetic storage devices are degaussed and physically destroyed in accordance with industry-standard practices.
	- Network Security
		○ Transmission Protection
			§ You can connect to an AWS access point via HTTP(S) using SSL.
		○ For customers who need more network security, AWS offers VPCs which provide a private subnet within the AWS cloud, and the ability to use an Ipsec VPN device to provide an encrypted tunnel between the VPC and your DC.
		○ Amazon Corporate Segregation
			§ Logically, the AWS Production network is segregated from the Amazon Corporate network by means of a complex set of network security/segregation devices.
		○ Network Monitoring & protection
			§ DDoS (Distributed Denial of Service)
			§ Man in the middle attacks
			§ IP Spoofing:
				□ The AWS-controlled, host-based firewall infrastructure will not permit an instance to send traffic with a source IP or MAC address other than its own.
			§ Port Scanning
				□ Unauthorized port scans by EC2 customers are a violation of the AWS Acceptable Use policy. You can request permission to conduct vulnerability scans as required to meet your specific compliance requirements.
				□ These scans must be limited to your own instances and must not violate the AWS Acceptable Use Policy. You must request a vulnerability scan in advance.
			§ Packet Sniffing by other tenants
	- AWS Credentials
		○
	- AWS Trusted Advisor
		○ Inspects your AWS environment and makes recommendation when opportunities may exist to save money, improve system performance, or close security gaps.
		○ Provides alerts on several of the most common security misconfigurations that can occur; leaving certain ports open that make you vulnerable to hacking, neglecting to create IAM accounts for your internal users, allowing public access to S3 buckets, not turning on user activity logging (CloudTrail), or not using MFA on your root AWS account.
	- Instance Isolation
		○ Different instances running on the same physical machine are isolated from each other via the Xen hypervisor. In addition, the AWS firewall resides within the hypervisor layer, between the physical network interface and the instance's virtual interface.
		○ All packets must pass through this layer, thus an instance's neighbors have no more access to that instance than any other host on the internet and can be treated as if they are on separate physical hosts. The physical RAM is separated using similar mechanisms.
		○ Customer instances have no access to raw disk devices, but instead are presented with virtualized disks. The AWS proprietary disk virtualization layer automatically resets every block of storage used by the customer, so that one customer's data is never unintentionally exposed to another.
		○ In addition, memory allocated to guests is scrubbed by the hypervisor when it is unallocated to a guest. The memory is not returned to the pool of free memory available for new allocations until the memory scrubbing is complete.
	- Other Considerations
		○ Guest OS
			§ Virtual instances are completely controlled by the customer. You have full root access or admin control over accounts, services and apps. AWS does not have any access rights to your instances or the guest OS.
			§ Encryption of sensitive data is generally a good security practice, and AWS provides the ability to encrypt EBS volumes and their snapshots w/ AES-256. The encryption occurs on the servers that host the EC2 instances, providing encryption of data as it moves between EC2 instances and EBS storage.
			§ To do this efficiently and with low latency, the EBS encryption feature is only available on EC2's more powerful instance types.
		○ Firewall
			§ EC2 provides a complete firewall solution; this mandatory inbound firewall is configured in a default deny-all mode and EC2 customers must explicitly open the ports needed to allow inbound traffic.
		○ Elastic Load Balancing
			§ SSL Termination on the load balancer is supported.
			§ Allows you to identify the originating IP address of a client connecting to your servers, whether you're using HTTPS or TCP load balancing.
		○ Direct Connect
			§ Bypass internet service providers in your network path. You can procure rack space within the facility housing the Direct Connect location and deploy your equipment nearby. Once deployed, you can connect the equipment to AWS Direct Connect using a cross-connect.
			§ Using industry standard 802.1q VLANs, the dedicated connection can be partitioned into multiple virtual interfaces. This allows you to use the same connection to access public resources such as objects stored in S3 using public IP address space, and private resources such as EC2 instances running within and Amazon VPC using private IP space, while maintaining network separation between the public and private environments.
			§ Essentially extends you private IP range to use the AWS rack, connecting through MPLS (Multiprotocol Label Switching).

Storage Options in the Cloud:
	-
	- AWS Import/Export
		○ AWS Import/Export accelerates moving large amounts of data into and out of AWS using portable storage devices for transport. AWS transfers your data directly onto and off of storage devices using Amazon's high-speed internal network and bypassing the internet. For significant datasets, AWS import/export is often faster than internet transfer and more cost effective than upgrading your connectivity.
		○ You pay for only what you use. Three pricing components:
			§ Per-device fee
			§ Data load time charge (per data-loading-hour)
			§ Possible return shipping charges (expedited shipping, or shipping to destinations not local to that AWS import/export region).
	- Storage Gateway
		○ Connects an on-premises software appliance w/ cloud-based storage to provide seamless and secure integration between an organization's on-premises IT environment and AWS's storage infra. The service enables you to securely store data to the AWS cloud for scalable and cost-effective storage.
		○ Available for download as a VM.
		○ Pay for what you use. Four pricing components:
			§ Gateway usage (per gateway per month)
			§ Snapshot storage usage (per GB per month)
			§ Volume storage usage (per GB per month)
			§ Data transfer out (per GB per month)


