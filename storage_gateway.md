# Storage Gateway

## What is it?
- AWS Storage Gateway is a service that connects an op-premises software appliance w/ cloud-based storage to provide seamless and secure integration between an orgs on-premises IT environment and AWS's storage infrastructure.
- The service enables you to securely store data to the AWS cloud for scalable and cost-effective storage.
- Available for download as a VM image that you install on a host in your DC.
- Supports either VMware ESXi or Microsoft Hyper-V.
- Once you've installed your gateway and associated it w/ your AWS account through the activation process, you can use the AWS Management Console to create the storage gateway option that is right for you.
## 4 Types of Storage Gateways
- File Gateway (NFS)
	○ Flat files only stored directly on S3
	○ Files are stored in s3 and accessed through Network file system (NFS) mount point. Once transferred to s3 they can be managed as regular s3 files.
	○ Can connect through
		□ Direct connect
		□ Internet
		□ Amazon VPC
- Volume Gateway (iSCSI)
	○ Block-based storage: presents your apps w/ disk volumes using the iSCSI block protocol.
		□ OS, DBs, etc.
	○ Stored volumes
		□ Virtual hard disks that sit on-premises, then you back these up on AWS asynchronously in the form of EBS snapshots.
		□ Size: from 1GB - 16TiB
	○ Cached volumes
		□ Use s3 as your primary data storage while keeping a copy of your frequently accessed data locally in your storage gateway.
		□ Size: up to 32TiB
- Tape Gateway (VTL)
	○ Allows you to leverage your existing tape-based backup app infrastructure to store data on virtual tape cartridges that you create on your tape gateway.
	○ Instead of physical tapes you have virtual tapes these are then being sent to s3.
