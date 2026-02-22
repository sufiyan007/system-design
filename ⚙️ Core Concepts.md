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

→ User opens WhatsApp\
→ Request goes to Load Balancer\
→ Load Balancer selects Server-1\
→ Server-1 is down due to failure\
→ Load Balancer redirects request to Server-2\
→ Server-2 processes request successfully\
→ User receives response without downtime

This ensures uninterrupted service experience.

# Causes / Purpose

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

-   Banking systems to ensure transactions work anytime
-   WhatsApp to ensure messages are delivered without interruption
-   Netflix to ensure videos are always accessible
-   Uber to ensure ride booking works continuously
-   Trading platforms to ensure uninterrupted order execution

Without availability, users experience downtime, failures, and service
disruption, making the system unreliable for real-world usage.

---

## 3️⃣ Reliability

Reliability means the system always works correctly and does not lose or
corrupt data, even if failures happen. When a user performs an action,
the system must complete it properly and safely. Failures like server
crash, database crash, or network issue can happen anytime, but a
reliable system protects the data and completes the operation correctly.
For example, when you send a WhatsApp message, reliability ensures the
message is not lost, even if a server crashes. WhatsApp stores the
message safely in its database before confirming success, so the message
can still be delivered even if one server fails.

The main purpose of reliability is to protect data and ensure correct
system behavior because data is the most critical asset in any system.
For example, when you transfer money using Google Pay, reliability
ensures the money is deducted from your account and credited to the
receiver correctly. The system stores the transaction in the database
and also keeps backup copies. If one database fails, another backup
database still has the correct data, so no money is lost. Without
reliability, systems may lose messages, lose payments, or show incorrect
data, which makes them unsafe.

Example request flow showing reliability:

User sends message on WhatsApp\
→ Request goes to Server\
→ Server saves message in Database\
→ Database also stores backup copy\
→ Server confirms success\
→ Even if one server crashes, message is safe\
→ Message is delivered successfully

Reliability is used in systems where data must never be lost, such as:

-   WhatsApp → messages must not be lost
-   Banking systems → money must be safe
-   Trading apps → orders must be correct
-   Amazon → order details must be correct
-   Uber → ride and payment data must be correct

If reliability is not implemented, data can be lost during failures,
causing serious problems for users and companies.

---

## 4️⃣ SPOF (Single Point of Failure)

SPOF means a single component in the system which, if it fails, will
cause the entire system to stop working. This happens when the system
depends on only one server, one database, or one load balancer without
any backup. If that single component crashes, users cannot access the
system anymore. For example, imagine a system with only one server
handling all requests. If that server crashes due to hardware failure or
overload, the entire application becomes unavailable because there is no
backup server to take over. This makes the system unreliable and
unavailable.

The main purpose of identifying and removing SPOF is to ensure the
system continues working even when failures happen. Companies solve this
by adding redundancy, which means having multiple servers, multiple
databases, and backup components. For example, WhatsApp does not use
only one server. It uses thousands of servers. When you send a message,
the load balancer selects one available server. If one server crashes,
another server immediately handles the request. This ensures the system
continues working without interruption and users do not notice any
failure.

Example showing SPOF problem:

User opens application\
→ Request goes to only one Server\
→ Server crashes\
→ No backup server available\
→ Application becomes unavailable

This server was SPOF because its failure stopped the entire system.

Example showing SPOF solution:

User opens application\
→ Request goes to Load Balancer\
→ Load Balancer selects Server-1\
→ Server-1 crashes\
→ Load Balancer redirects to Server-2\
→ Application continues working

Now there is no SPOF because backup servers exist.

SPOF can exist in different parts of system such as:

-   Single server → if it crashes, system stops
-   Single database → if it fails, data cannot be accessed
-   Single load balancer → if it fails, requests cannot be routed
-   Single data center → if power/network fails, system goes down

Real-world example: If Instagram had only one database server and it
crashed, users would not be able to see posts, login, or refresh feeds.
To prevent this, Instagram uses database replication, where multiple
database copies exist. If one fails, another takes over.

Removing SPOF is critical for high availability and reliability because
production systems must handle failures without downtime. All large
systems like WhatsApp, Netflix, Uber, and banking systems are designed
to eliminate SPOF by using multiple servers, database replicas, backup
systems, and failover mechanisms.

---

## 5️⃣ Latency

Latency is the time taken for one request to travel from user to server
and back with a response. It is measured in milliseconds (ms). Lower
latency means faster response, higher latency means slower response. For
example, when you open Instagram and click refresh, the time between
clicking refresh and seeing new posts is latency. If it takes 50 ms, the
system feels fast. If it takes 3 seconds, the system feels slow. Latency
is critical in real-time systems like trading apps, WhatsApp messaging,
and Uber ride requests because users expect instant response.

Example request flow showing latency:

User opens WhatsApp\
→ Request goes to Server\
→ Server processes request\
→ Server sends response\
→ Total time taken = Latency

Purpose is to make system respond faster so user experience is smooth.
Companies reduce latency using cache, CDN, and servers closer to users.

------------------------------------------------------------------------

## 6️⃣ Throughput

Throughput is the number of requests the system can handle per second.
It measures system capacity. Higher throughput means system can handle
more users at the same time. For example, if a server handles 1,000
requests per second, its throughput is 1,000 requests/sec. Instagram
handles millions of requests per second because millions of users scroll
feeds at the same time. To increase throughput, companies add more
servers (horizontal scaling) and use load balancers to distribute
traffic.

Example:

Server handles\
User 1 request\
User 2 request\
User 3 request\
User 4 request

Number of requests handled per second = Throughput

Purpose is to support large number of users without system crash.

------------------------------------------------------------------------

## 7️⃣ Bandwidth

Bandwidth is the maximum amount of data that can be transferred per
second over network. It is measured in Mbps or Gbps. Higher bandwidth
means more data can travel at once. For example, when you watch YouTube
videos in 4K, large amount of video data must transfer from server to
your phone. This requires high bandwidth. Netflix and YouTube use high
bandwidth networks and CDNs to deliver video smoothly.

Example:

Watching YouTube video\
→ Video data transfers from server to phone\
→ Amount of data transferred per second = Bandwidth

Purpose is to support large data transfer like videos, images, and
files.

---
