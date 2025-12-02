#flashcards #aws 
status:: 
count:: 27
[[Flashcards]]

<!-- Card Start -->

### Front  

Which of the following are benefits of migrating to the AWS Cloud? (Choose two.)  

- A. Operational resilience
- B. Discounts for products on Amazon.com
- C. Business agility
- D. Business excellence
- E. Increased staff retention

### Back

**A** and **C**

<!-- Card End --> 

<!-- Card Start -->

### Front  

What is AWS CloudFront?

### Back

**AWS CloudFront** is a **Content Delivery Network (CDN)** service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds. It integrates with other AWS services to provide a seamless content distribution experience.

<!-- Card End -->
<!-- Card Start -->

### Front

What are the two types of CloudFront distributions?

### Back

1. **Web Distributions**: Used for serving static and dynamic content over HTTP and HTTPS.
2. **RTMP Distributions**: Used for streaming media files using the RTMP protocol. _(Note: RTMP distributions are being deprecated in favor of newer streaming technologies.)_

<!-- Card End -->
<!-- Card Start -->

### Front 

Define an Origin in AWS CloudFront.
### Back

An **Origin** is the source of the content that CloudFront will distribute. It can be an **AWS S3 bucket**, an **Elastic Load Balancer**, an **EC2 instance**, or any **custom HTTP server**.

<!-- Card End -->
<!-- Card Start -->
### Front 

What are Edge Locations in CloudFront?

### Back

**Edge Locations** are data centers located globally where CloudFront caches copies of your content. They are used to deliver content to end-users with low latency by serving requests from the nearest Edge Location.

<!-- Card End -->
<!-- Card Start -->
### Front 

Explain Regional Edge Caches in CloudFront.
### Back

**Regional Edge Caches** are larger caching layers located between the Edge Locations and the origin. They help reduce the load on the origin by serving content to multiple Edge Locations from a single Regional Edge Cache, improving cache hit ratios and reducing latency.

<!-- Card End -->
<!-- Card Start -->
### Front

What are Cache Behaviors in CloudFront?
### Back

**Cache Behaviors** define how CloudFront handles requests for specific paths within your distribution. They allow you to configure settings such as caching policies, origin selection, viewer protocols, and more for different parts of your website or application.

<!-- Card End -->
<!-- Card Start -->
### Front 

What is Lambda@Edge in CloudFront?
### Back

**Lambda@Edge** allows you to run **AWS Lambda functions** at CloudFront Edge Locations. This enables you to execute custom code to modify requests and responses, personalize content, perform authentication, and more, closer to the end-user for reduced latency.

<!-- Card End -->
<!-- Card Start -->
### Front  

How is AWS CloudFront priced?
### Back

CloudFront pricing is based on:

- **Data Transfer Out** to the internet.
- **Requests** made to your distribution.
- **Invalidation Requests** beyond the free tier.
- **Additional features** like Lambda@Edge and Field-Level Encryption.

Pricing varies by **region** and usage levels. There are no upfront fees, and you pay only for what you use.
<!-- Card End -->
<!-- Card Start -->
### Front 

List security features of AWS CloudFront.
### Back

- **HTTPS Support**: Secure content delivery.
- **AWS Shield Integration**: Protection against DDoS attacks.
- **AWS WAF Integration**: Web application firewall for filtering malicious traffic.
- **Origin Access Identity (OAI)**: Restricts access to S3 origins.
- **Signed URLs and Cookies**: Control access to content.

<!-- Card End --> <!-- Card Start -->

### Front 

What is an Origin Access Identity (OAI) in CloudFront?

### Back

An **Origin Access Identity (OAI)** is a special CloudFront user that you associate with your distribution to securely serve private content from an **Amazon S3 bucket**. It ensures that only CloudFront can access the S3 content, preventing direct access from the internet.

<!-- Card End -->
<!-- Card Start -->

### Front 

How does CloudFront handle caching?
### Back

CloudFront caches content at Edge Locations based on **cache behaviors** and **TTL (Time to Live)** settings. When a user requests content, CloudFront checks the cache:

- **Cache Hit**: Delivers content from the Edge Location.
- **Cache Miss**: Fetches content from the origin, caches it, and then delivers it to the user.

You can configure caching policies to control what is cached and for how long.

<!-- Card End --> 

<!-- Card Start -->

### Front 

What is an invalidation in CloudFront?

### Back

An **invalidation** is a request to remove one or more objects from CloudFront's cache before they expire. This ensures that subsequent requests for the invalidated objects are fetched from the origin, allowing you to update or delete content as needed.

<!-- Card End --> 
<!-- Card Start -->

### Front

How does CloudFront handle SSL/TLS?

### Back

CloudFront supports **HTTPS** to encrypt data between viewers and Edge Locations. You can use **default CloudFront certificates** or **custom SSL certificates** via **AWS Certificate Manager (ACM)** for your own domain names. It also supports **TLS 1.2** for enhanced security.

<!-- Card End --> 
<!-- Card Start -->

### Front 

What is Geo-Restriction in CloudFront?

### Back

**Geo-Restriction** allows you to **allow** or **block** content delivery to users based on their geographic locations (countries). This is useful for complying with licensing agreements, regional regulations, or content distribution policies.

<!-- Card End --> <!-- Card Start -->

### Front 

What are CloudFront Access Logs?

### Back

**CloudFront Access Logs** provide detailed records of every request made to your distribution. Logs include information such as the **viewer’s IP address**, **request time**, **HTTP status code**, **bytes served**, and more. They are useful for monitoring, analyzing traffic, and troubleshooting.

<!-- Card End --> 
<!-- Card Start -->

### Front 

Describe CloudFront Functions.

### Back

**CloudFront Functions** are lightweight JavaScript functions that run at Edge Locations. They allow you to **modify HTTP requests and responses** quickly and efficiently, enabling tasks like URL rewrites, header manipulations, and simple authentication without the overhead of Lambda@Edge.

<!-- Card End -->

<!-- Card Start -->

### Front 

How do Signed URLs and Cookies work in CloudFront?

### Back

**Signed URLs** and **Signed Cookies** are used to restrict access to your content:

- **Signed URLs**: Provide time-limited access to specific files.
- **Signed Cookies**: Allow access to multiple restricted files within a set time period.

They ensure that only authorized users can access your private content.

<!-- Card End --> <!-- Card Start -->

### Front 

How does CloudFront integrate with Amazon S3?

### Back

CloudFront can use an **Amazon S3 bucket** as an origin. When configured with an **Origin Access Identity (OAI)**, CloudFront securely serves private content from the S3 bucket, ensuring that content is accessible only through CloudFront and not directly from S3.

<!-- Card End --> <!-- Card Start -->

### Front


What are CNAMEs in CloudFront?

### Back

**CNAMEs (Canonical Names)** allow you to use your own domain names with CloudFront distributions. By adding **alternate domain names (CNAMEs)** to your distribution and configuring DNS records, you can serve content using custom URLs like `cdn.yourdomain.com`.

<!-- Card End --> <!-- Card Start -->

### Front

Explain Field-Level Encryption in CloudFront.

### Back

**Field-Level Encryption** allows you to encrypt specific data fields within HTTPS requests, protecting sensitive information like credit card numbers or personal data. CloudFront decrypts these fields before forwarding the request to the origin, ensuring data security end-to-end.

<!-- Card End -->

<!-- Card Start -->

### Front 

How does CloudFront handle compression?

### Back

CloudFront can automatically **compress** certain types of files (e.g., HTML, CSS, JavaScript) before delivering them to viewers. This reduces the amount of data transmitted, improving load times and reducing bandwidth usage. Compression settings can be enabled in cache behaviors.

<!-- Card End -->

<!-- Card Start -->

### Front 

What monitoring options does CloudFront provide?

### Back

CloudFront offers **real-time metrics and logs** through **Amazon CloudWatch**. You can monitor key performance indicators like **cache hit ratios**, **latency**, **request counts**, and **error rates**. Additionally, **access logs** provide detailed request information for in-depth analysis.

<!-- Card End --> 
<!-- Card Start -->

### Front 

What is Origin Shield in CloudFront?

### Back

**Origin Shield** is an additional caching layer that acts as a central point for all requests to your origin. It reduces the number of direct requests to the origin by consolidating requests from multiple Edge Locations, improving cache efficiency and reducing origin load.

<!-- Card End --> 
<!-- Card Start -->

### Front 

How can you customize error responses in CloudFront?

### Back

CloudFront allows you to define **custom error responses** for specific HTTP status codes (e.g., 404, 500). You can specify custom error pages, response codes, and caching durations, enhancing the user experience by providing branded or more informative error messages.

<!-- Card End --> 
<!-- Card Start -->

### Front  

Does CloudFront support HTTP/2?

### Back

Yes, **AWS CloudFront** fully supports **HTTP/2**, allowing for improved performance through features like multiplexing, header compression, and server push, enhancing the efficiency of content delivery to compatible clients.

<!-- Card End -->
<!-- Card Start -->

### Front

How does CloudFront manage access control?

### Back

CloudFront manages access control through:

- **Origin Access Identity (OAI)** for S3 buckets.
- **Signed URLs and Cookies** for restricting content access.
- **AWS IAM Policies** to control who can create and manage distributions.
- **AWS WAF** for filtering and blocking malicious requests.

<!-- Card End --> <!-- Card Start -->

### Front

How does CloudFront integrate with AWS Shield?

### Back

CloudFront integrates with **AWS Shield**, providing built-in protection against DDoS attacks. **AWS Shield Standard** is automatically enabled with CloudFront distributions, offering protection without additional costs, while **AWS Shield Advanced** provides enhanced protections and support for larger, more sophisticated attacks.

<!-- Card End -->