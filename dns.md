# DNS

## Exam Tips:
	- ELB's do not have pre-defined IPv4 addresses, you resolve to them using a DNS name.
		○ Always given a dns endpoint only
		○ Thus we use Alias records
	- Understand the difference between Alias Records and a CNAME
		○ Alias records allow you to resolve a naked domain name/zone apex record to an ELBs DNS address.
		○ Alias records can map directly to AWS resources
		○ When making a request to Route53 for a DNS record;
			§ Charged for request if you are using a CNAME
			§ Will not be charged if you are using an Alias Record
		○ Given a choice, always choose an alias record over a cname.
	- Routing Policies (There are 5):
		○ Simple
		○ Weighted
		○ Latency
		○ Failover
		○ Geolocation

