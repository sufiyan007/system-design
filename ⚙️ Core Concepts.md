## 1️⃣ Scalability

Scalability means a system's ability to handle increasing number of
users, requests, or traffic without slowing down or crashing. When a
system is small, like serving 100 users, one server is enough. But when
the system grows to 10 lakh users or 1 crore users, the same server
cannot handle all requests because CPU, RAM, and database connections
have limits. Scalability ensures the system can expand its capacity
smoothly as traffic increases. For example, when you open Instagram at
night, millions of users are also opening it at the same time. Instagram
cannot depend on a single server, so they use thousands of servers to
distribute the load. This ensures every user gets fast response and the
app does not crash. Without scalability, apps would become slow,
timeout, or completely fail when traffic increases.

There are two main ways systems scale in real production environments.

# Vertical Scaling (Scaling Up): 
means increasing power of the same server
by adding more RAM, CPU, or storage. For example, upgrading server from
8GB RAM to 64GB RAM allows it to handle more users. This is simple but
has a limit because a single machine cannot be upgraded infinitely. This
approach is used in early-stage startups or small internal tools where
traffic is moderate.

# Horizontal Scaling (Scaling Out):
means adding more servers instead of
upgrading one server. For example, instead of 1 server handling 10,000
users, you use 10 servers handling 1,000 users each. This is the most
common approach in companies like Google, Uber, WhatsApp, and Amazon.
When traffic increases, new servers are added behind a load balancer,
which distributes requests across servers. This approach has no
practical limit and supports millions or billions of users.

Example request flow in scalable system:

-   User opens WhatsApp\
-   → Request goes to Load Balancer\
-   → Load Balancer selects one server from 100 servers\
-   → Server processes request\
-   → Response sent back to user

If traffic increases, WhatsApp adds more servers. Load balancer
automatically distributes traffic. This ensures system remains fast.

Scalability is used in almost every modern production system,
especially:

-   Instagram → millions of feed requests per second\
-   YouTube → millions of video streaming requests\
-   Uber → real-time ride requests and driver tracking\
-   Banking systems → transaction processing\
-   Trading systems → order execution

---

## 2️⃣ Availability

Explanation

Availability means the system is always up, running, and accessible
whenever users try to use it. When a user opens an application and it
responds successfully without errors or delay, the system is considered
available. If the user opens the application and it shows errors, does
not load, or cannot connect to the server, the system is unavailable. In
real production environments, servers, databases, or network components
can fail anytime due to hardware crash, software bugs, memory overflow,
disk failure, power outage, or network disruption. Availability ensures
that even if one or more components fail, the system continues serving
users without interruption. For example, when you send a message on
WhatsApp, your request goes through load balancers to one of many
servers. If one server crashes, another healthy server immediately
handles the request, and the message is delivered without you noticing
any failure. This is achieved by running multiple servers instead of
relying on a single server, ensuring continuous service.

Example request flow showing availability in action:

User opens WhatsApp\
→ Request goes to Load Balancer\
→ Load Balancer selects Server-1\
→ Server-1 is down due to failure\
→ Load Balancer redirects request to Server-2\
→ Server-2 processes request successfully\
→ User receives response without downtime

This ensures uninterrupted service experience.

Causes / Purpose

The main purpose of availability is to prevent downtime and ensure
continuous business operations. Downtime means the system becomes
unusable, which directly impacts revenue, customer trust, and business
reputation. If systems are unavailable, users cannot perform critical
operations such as payments, messaging, trading, or booking services.
For example, if UPI platforms like PhonePe or Google Pay become
unavailable even for a few minutes, millions of users cannot complete
transactions, causing financial and operational disruption. Similarly,
if trading platforms like Zerodha become unavailable during stock market
hours, users cannot buy or sell stocks, resulting in financial loss and
user dissatisfaction. Availability ensures that failures in individual
components do not stop the entire system by using redundancy, failover
mechanisms, and multiple servers. This guarantees that the system
continues functioning even when failures occur.

Availability is used in all critical production systems such as:

Banking systems to ensure transactions work anytime

WhatsApp to ensure messages are delivered without interruption

Netflix to ensure videos are always accessible

Uber to ensure ride booking works continuously

Trading platforms to ensure uninterrupted order execution

Without availability, users experience downtime, failures, and service
disruption, making the system unreliable for real-world usage.

---

