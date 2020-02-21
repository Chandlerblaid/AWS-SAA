# Cloudfront

## What is a CDN?
- A content delivery network (CDN) is a system of distributed servers (network) that deliver webpages and other web content to a user based on the geographic locations of the user, the origin of the webpage and a content delivery server.
## CloudFront - Key Terminology
- Edge Location - This is the location where content will be cached. This is separate to an AWS Region/AZ
	○ Not just Read only, you can write to them (put an object on to them) too.
		□ Once an object has been uploaded to your edge location, amazon will take care of persisting it to your s3 bucket.
	○ Objects are cached for the life of the TTL (Time To Live)
		□ TTL's are always in seconds
		□ Make sure you pay attention to the rate at which your files change when setting TTL's
	○ Clearing cached objects is a charge.
- Origin - this is the origin of all the files that the CDN will distribute. This can either be an s3 bucket, and ec2 instance, and elastic load balancer or Route 53.
- Distribution - This is the name given to a CDN, which consists of a collection of Edge Locations.
	○ Web distribution - typically used for websites
	○ RTMP - used for media streaming.
## What is CloudFront?
- Amazon CloudFront can be used to deliver your entire website, including dynamic, static, streaming, and interactive content using a global network of edge locations.
- Requests for your content are automatically routed to the nearest edge location, so content is delivered w/ the best possible performance
	○ This will cause the first users performance to suffer a bit, but once that first users request is cached in the nearest edge location, performance for everyone else will greatly increase.
## Create a CloudFront CDN
- How to secure your cloudfront; to make sure only paid users can access the content?
	○ Presigned urls and signed cookies
- WAF (Web Application Firewall)
	○ Layer7 protection
	○ Prevents SQL injection and XSS
