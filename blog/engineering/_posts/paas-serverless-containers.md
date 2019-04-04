

* Serverless and FaaS
* Cloud Agnostic?
* Cold Start Times
* Application Code Changes
    * Rest controllers vs lambda handlers
* Programming Languages Supported
* Service Limits
    * Account level concurrency limit (1000 / sec)?
    * Artifact size
* Application Design Constrains
Ex: in-memory caching, creating connection pools / other expensive object creation (also affects auto-scaled EC2, but
 problem more exaggerated in lambda)
Heavy frameworks like Spring are  not recommended
DB connection pooling - do you have to increase no. of. concurrent DB connections your DB server can handle?
https://stackoverflow.com/questions/48297735/connection-pooling-in-aws-lambda-with-rds 
* Is EB as PaaS?
* One Lambda Per User Request?
* Serverless for UI Applications
* Lambda Inside VPC
* API Gateway and CloudFront
* Auto-scaling - VM vs container startup time
* Serverless and PaaS - not mutually exclusive and can be mixed
* PaaS - VMs vs containers