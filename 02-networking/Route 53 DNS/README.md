## Building a Complete Route 53 DNS Environment

### Setting up the public hosted zone

In this step, I'm setting up a public hosted zone in Route 53 by first understanding the DNS resolution process from the browser to the authoritative server and then examining the default NS and SOA records that Route 53 creates automatically, so that I can see how Route 53 takes ownership of a domain's DNS and serves as its authoritative name server.

## Configuring the Public Hosted Zone

![Configuring the Public Hosted Zone](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/58730017-7c44-496f-a55c-ce3b0890fe9b_t5r8fz35)

### NS records and high availability design

Route 53 assigns 'four' name servers to a hosted zone . They are spread across different TLDs (such as \`.com\`, \`.net\`, \`.org\`, and \`.co.uk\`) to \*\*avoid a single point of failure\*\*—so that an outage or issue with one Top-Level Domain's infrastructure does not take the entire hosted zone offline, effectively "not putting all your eggs in one basket" .

## Creating Every DNS Record Type

### A, CNAME, MX, TXT, and CAA records

In this step, I'm setting up an A record that maps a subdomain to an IPv4 address, creating CNAME, MX, and TXT records for routing and verification purposes, and creating a CAA record to control which certificate authorities can issue certificates for my domain, so that I can configure the complete set of DNS record types needed to route traffic, verify domain ownership, handle email, and enforce certificate security policies.

### Why alias records exist: the CNAME zone apex limitation

CNAME records cannot be used at \*\*the zone apex (the root domain, such as \`example.com\`)\*\* because the DNS protocol mandates that the zone apex must contain mandatory records like \*\*NS and SOA\*\*, and CNAME records are prohibited from coexisting with any other record type at the same name. This is why \*\*Alias records\*\* are necessary—they are a Route 53 extension that allows you to point the bare domain to AWS resources (such as CloudFront or S3) without violating DNS rules.

![Creating Every DNS Record Type](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/58730017-7c44-496f-a55c-ce3b0890fe9b_rhjzz9tg)

## Routing Traffic to AWS Resources with Alias Records

### S3 static website and EC2 instance routing

In this step, I'm creating an S3 static website with an alias record at the zone apex, launching an EC2 instance with a standard A record for it, and understanding the critical differences between alias and non-alias records, so that I can see how alias records solve the zone apex limitation and how standard records handle direct resource mapping.

![Routing Traffic to AWS Resources with Alias Records](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/58730017-7c44-496f-a55c-ce3b0890fe9b_cwfiwyk5)

### Alias records vs standard A records for EC2

I can't alias to EC2 because \*\*Route 53 alias records can only target specific AWS resources that have a fixed endpoint, such as an S3 website endpoint, a CloudFront distribution, or an Elastic Load Balancer—not an EC2 instance's IP address.\*\* Instead I would use \*\*a standard A record pointing to the instance's public IPv4 address (with a low TTL of 60 seconds), or place an Elastic Load Balancer in front of the EC2 instance and create an alias record pointing to the ELB.\*\*

## Verifying DNS Resolution with TestDNSAnswer

### Testing records without domain registration

In this step, I'm verifying DNS records using Route 53's TestDNSAnswer in the console, querying my Route 53 name servers directly using \`nslookup\` from the Command Prompt, and understanding TTL behavior and its impact on cost, propagation, and failover, so that I can confirm my record configurations are resolving correctly and grasp how TTL settings affect real-world DNS performance and AWS exam scenarios.

![Verifying DNS Resolution with TestDNSAnswer](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/58730017-7c44-496f-a55c-ce3b0890fe9b_ttxlkp0w)

### TTL strategy for zero-downtime migrations

Here is the explanation condensed into roughly 15 lines:

To migrate a website with minimal downtime using DNS, you manipulate the \*\*TTL (Time To Live)\*\*—the time resolvers cache your IP address.

1\. \*\*Lower the TTL to 60 seconds\*\* on your existing record \*before\* migrating.\
2\. \*\*Wait for the old TTL to expire.\*\* If the old TTL was 24 hours, you must wait 24 hours so every resolver worldwide updates to the new 60-second rule.\
3\. \*\*Make the change\*\* by pointing the record to your new infrastructure. Because resolvers now check every minute, the internet updates almost instantly, preventing users from hitting a dead server.\
4\. \*\*Raise the TTL back\*\* to a normal value (e.g., 300 or 3600 seconds) after the migration is stable to reduce DNS query costs and network traffic.

\*\*Note:\*\* This strategy applies to \*\*standard records\*\*. For \*\*Alias records\*\*, AWS manages the TTL automatically—you cannot change it.

## Implementing Split-View DNS with a Private Hosted Zone

### Internal DNS resolution for VPC resources

In this step, I'm setting up a private hosted zone associated with my VPC, adding internal A records for simulated services, and verifying split-view DNS and understanding NXDOMAIN behavior, so that I can resolve internal domain names privately within the VPC while keeping them invisible to the public internet, and confirm how Route 53 responds when a queried name does not exist.

![Implementing Split-View DNS with a Private Hosted Zone](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/58730017-7c44-496f-a55c-ce3b0890fe9b_zo31j9uz)

### The private zone NXDOMAIN trap

Route 53 returns an \*\*NXDOMAIN\*\* (Non-Existent Domain) error, and it \*\*does not\*\* fall through to check the public hosted zone, even if the exact same record exists there.

\*\*Why?\*\* The VPC Resolver uses a strict "first match wins" rule. Once it finds a private hosted zone associated with the VPC that matches the domain name (\`myexamprep.com\`), it \*\*commits exclusively to that zone\*\*. If the specific record (e.g., \`blog.myexamprep.com\`) is missing inside the private zone, the resolver simply reports that it doesn't exist. It will not "peek" at the public zone for a backup answer. This is often called the \*\*NXDOMAIN trap\*\* on exams.

## Mastering Route 53 Pricing and Cost Optimization

### Pricing model and exam-ready concepts

In this step, I'm reviewing the Route 53 pricing model and cost optimization strategies, studying the complete record types reference table for the exam, and memorizing 10 key exam scenarios and their answers, so that I can solidify my understanding of Route 53's cost structure, record types, and common exam pitfalls to confidently pass the certification exam.

## Subdomain Delegation with NS Records

### How enterprise DNS delegation works

In this project extension, the NS record in the parent zone tells resolvers to \*\*delegate authority for the subdomain (\`dev.myexamprep.com\`) to the specific name servers listed for the child zone.\*\*

The parent zone does not contain the A record for \`app.dev.myexamprep.com\` directly because \*\*DNS follows a hierarchical delegation model.\*\* The parent zone is only responsible for knowing \*who\* is in charge of the subdomain, not the specific IP addresses within it. By using an NS record to hand off control, the parent zone doesn't have to manage every single record for every subdomain, keeping the DNS architecture scalable and manageable.
