# Blocking-web-traffic-with-WAF-in-AWS
Hands-on AWS security lab demonstrating how to use AWS WAF with an Application Load Balancer to inspect, filter, and block malicious web traffic before it reaches backend EC2 web servers.
# Blocking Web Traffic with WAF in AWS

## Overview
This lab demonstrates how to protect a web application in AWS by placing AWS WAF in front of an Application Load Balancer (ALB). The solution filters incoming HTTP/HTTPS traffic before requests are forwarded to backend EC2 web servers.

The environment includes:
- AWS WAF
- Application Load Balancer (ALB)
- Target Group
- Two EC2 web servers in private subnets
- Security Groups allowing traffic only from the ALB to the web servers

This lab shows how AWS WAF can be used to block malicious or unwanted traffic patterns and improve the security posture of web-facing applications.

---

## What is AWS WAF?
AWS WAF is a web application firewall that helps protect web applications from common web exploits and malicious traffic.

It allows you to create rules that inspect incoming requests and decide whether to:
- Allow
- Block
- Monitor

AWS WAF can help defend applications against threats such as:
- SQL injection
- Cross-site scripting (XSS)
- Bad or suspicious request patterns
- Requests matching custom strings or conditions

AWS WAF gives security teams more control over how traffic reaches an application.

---

## What is an Application Load Balancer?
An Application Load Balancer (ALB) distributes incoming HTTP and HTTPS traffic across multiple targets, such as EC2 instances, based on routing rules.

In this lab, the ALB:
- Receives incoming web traffic
- Routes requests to the target group
- Distributes traffic across two backend web servers
- Works with AWS WAF to ensure only approved traffic reaches the application layer

---

## Why This Lab Matters
Web applications are common attack targets. If malicious requests are not filtered early, they can reach backend systems and create security, availability, and operational risks.

This lab matters because it demonstrates how to:
- Add a protective inspection layer in front of a public-facing application
- Reduce exposure to common web attacks
- Improve defense-in-depth in AWS
- Control traffic before it reaches private web servers

---

## Problem Solved
The problem addressed in this lab is simple:

How do we stop suspicious or malicious web traffic before it reaches backend servers?

Without a filtering layer, requests sent through the load balancer could reach the application servers directly if they match network and listener rules. This increases the risk of application abuse, malicious payloads, and unnecessary load on backend resources.

By using AWS WAF with ALB, incoming traffic is evaluated against security rules first. Requests that match malicious patterns can be blocked before they ever reach the web servers.

---

## Why This Solution Makes Sense
This solution makes sense because it applies security controls at the web entry point.

Benefits include:
- Early traffic inspection
- Reduced attack surface
- Less unnecessary traffic reaching backend servers
- Better visibility into web request behavior
- Flexible rule creation based on application needs

Instead of relying only on server-side protections, AWS WAF adds a filtering layer before traffic reaches the application instances.

---

## Architecture
- Client sends HTTP request
- Request reaches the Application Load Balancer
- AWS WAF inspects the request based on configured rules
- Allowed traffic is forwarded to the target group
- ALB distributes traffic to Web Server 1 or Web Server 2
- Blocked traffic is stopped before reaching the backend

---

## Lab Components

### 1. AWS WAF
Configured with rules to inspect and filter incoming requests.

### 2. Application Load Balancer
Receives external web traffic and routes it to registered targets.

### 3. Target Group
Contains the EC2 web servers that receive traffic from the ALB.

### 4. EC2 Web Servers
Two web servers deployed in private subnets.
Each server serves a simple test page:
- RESPONSE COMING FROM SERVER 1
- RESPONSE COMING FROM SERVER 2

### 5. Security Groups
Configured to allow:
- Public traffic to the ALB on port 80
- Traffic from the ALB to the EC2 instances on port 80

---

## How It Works
1. A user sends a request to the web application through the ALB.
2. AWS WAF evaluates the request against the configured rules.
3. If the request is legitimate, it is allowed through.
4. The ALB forwards the request to the target group.
5. One of the registered EC2 web servers responds.
6. If the request matches a blocked condition, AWS WAF denies it before it reaches the backend.

This gives the application an additional security layer without changing the application code itself.

---

## Security Insight
This lab highlights an important cloud security principle:

**Protect applications as close to the entry point as possible.**

AWS WAF is valuable because it allows defenders to stop harmful traffic before it consumes backend resources or interacts with the application logic.

Key security takeaways:
- WAF improves protection against Layer 7 web threats
- ALB + WAF provides centralized traffic inspection
- Private subnet web servers reduce direct exposure
- Security groups and WAF together support layered defense
- Monitoring and tuning WAF rules helps adapt to evolving attack patterns

In real-world cloud environments, this kind of layered design helps improve resilience, reduce risk, and support secure application delivery.

---

## Skills Demonstrated
- AWS WAF configuration
- Application Load Balancer setup
- Target Group configuration
- EC2 web application hosting
- Security group design
- Layered defense in AWS
- Basic web application protection

---

## Security insights
This lab shows that cloud security is not only about securing servers. It is also about controlling and inspecting the traffic that reaches them.

Using AWS WAF with an ALB is a practical way to improve web application security, reduce risk, and build stronger cloud-native defenses.

