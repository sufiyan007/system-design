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

Vertical Scaling (Scaling Up) means increasing power of the same server
by adding more RAM, CPU, or storage. For example, upgrading server from
8GB RAM to 64GB RAM allows it to handle more users. This is simple but
has a limit because a single machine cannot be upgraded infinitely. This
approach is used in early-stage startups or small internal tools where
traffic is moderate.

Horizontal Scaling (Scaling Out) means adding more servers instead of
upgrading one server. For example, instead of 1 server handling 10,000
users, you use 10 servers handling 1,000 users each. This is the most
common approach in companies like Google, Uber, WhatsApp, and Amazon.
When traffic increases, new servers are added behind a load balancer,
which distributes requests across servers. This approach has no
practical limit and supports millions or billions of users.

Example request flow in scalable system:

User opens WhatsApp\
→ Request goes to Load Balancer\
→ Load Balancer selects one server from 100 servers\
→ Server processes request\
→ Response sent back to user

If traffic increases, WhatsApp adds more servers. Load balancer
automatically distributes traffic. This ensures system remains fast.

Scalability is used in almost every modern production system,
especially:

Instagram → millions of feed requests per second

YouTube → millions of video streaming requests

Uber → real-time ride requests and driver tracking

Banking systems → transaction processing

Trading systems → order execution

---
