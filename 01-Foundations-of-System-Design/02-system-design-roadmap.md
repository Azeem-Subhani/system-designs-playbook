# System Design Roadmap

## What is it?

System design is the process of turning a broad problem into a practical architecture. In an interview, it is less about memorizing patterns and more about showing clear reasoning, communication, and awareness of trade-offs.

## Why do we need it?

Real design questions are intentionally incomplete. For example, "Design Twitter" could mean a small internal tool or a global social network. A structured approach helps you choose the right scope before choosing technologies.

## How does it work?

Use this order to guide a system design interview.

```mermaid
flowchart LR
    R[Clarify requirements] --> H[Draw a simple high-level design]
    H --> B[Find bottlenecks]
    B --> T[Choose trade-offs]
    T --> D[Deep dive into key components]
```

### 1. Clarify requirements

Ask a small number of questions that define what you are building:

- What is the core user action?
- Who are the users?
- What matters most: latency, correctness, availability, or cost?
- What scale should the design support now and later?
- Which features are required, and which are out of scope?

Do not spend the entire interview asking questions. Get enough clarity to make reasonable assumptions, state those assumptions, and move on.

### 2. Start with a simple high-level design

Draw the smallest architecture that can support the core requirement. For many web products, begin with a client, an application server, and a database. Explain the request flow before adding more components.

### 3. Identify bottlenecks

Ask what fails or slows down as usage grows:

- Is the database receiving too many reads or writes?
- Is one server becoming overloaded?
- Is a slow external dependency delaying requests?
- Is data growing beyond one machine?

Add a component only because it addresses a specific problem. For example, add a cache when repeated reads are overloading the database—not simply because caches are common.

### 4. Explain trade-offs

Every design choice has benefits and costs.

| Choice | Benefit | Trade-off to discuss |
| --- | --- | --- |
| Cache | Faster reads and less database load | Stale data and cache invalidation |
| More application servers | Higher capacity and availability | Load balancing and shared state |
| NoSQL database | Flexible schema or high horizontal scale, depending on the database | Different query, transaction, and consistency guarantees |

Avoid absolute statements such as "NoSQL is eventually consistent." Database guarantees vary by product and configuration.

### 5. Deep dive where it matters

Expect to explain one or two important components in more detail. Depending on the design, this could be a message queue, cache, database replication strategy, feed-generation service, or API.

You do not need to implement every component from scratch. You do need a solid understanding of the components you choose and their failure modes.

## Example

For a URL-shortening service, first define the core flow: create a short URL and redirect users. Start with an API and database. If redirects become read-heavy, add a cache in front of the database. Then explain the trade-off: a cached mapping can be briefly stale after an update or deletion.

## Important Points

- Solve the core requirement before edge cases.
- State assumptions when requirements are unclear.
- Build from a simple design toward a scalable one.
- Introduce technologies as solutions to named bottlenecks.
- Name both the benefit and the downside of major choices.
- Be ready to go deeper on the components that carry the most risk or traffic.

## Interview Questions

### What do interviewers evaluate in a system design interview?

They commonly evaluate how you clarify ambiguity, structure a problem, communicate, make trade-offs, and reason about scale and failures.

### When should you add a cache?

Add one when data is read repeatedly and the database or another source of truth is becoming a performance bottleneck. Also explain how the cache is populated and invalidated.

### How deep should a design go?

Cover the full high-level flow first. Then deep dive into one or two major components that are central to the system's scale, correctness, or reliability.

## Recap

Strong system design starts with clear requirements, a simple architecture, and evidence-based additions. Show how each component solves a problem, then explain the trade-off it creates.
