# Amazon SDE-1 Industry Roadmap

## 🧭 BIG PICTURE (How Amazon SDE Work Actually Looks)

In real teams, your work is usually:

- **Designing services**, not writing standalone code
- **Reading & modifying existing large codebases**
- **Making scalable + reliable systems**
- **Deploying on Amazon Web Services**
- **Debugging production issues**
- **Writing design docs**, not just code

So roadmap = Code + Cloud + Systems + Ops + Security

## 🚀 MASTER ROADMAP (Industry-Ready)

### 1️⃣ AWS (Absolute MUST for Amazon)

You already listed good topics. Here's the industry-oriented framing 👇

**Core AWS (You must be fluent)**

- **Cloud computing fundamentals** (IaaS / PaaS / Serverless)
- **Global infra**: Regions, AZs, Edge locations
- **IAM**
  - Users vs Roles
  - AssumeRole
  - Least privilege (VERY important at Amazon)
- **EC2**
  - Launch types, AMI, autoscaling groups
- **S3**
  - Buckets, lifecycle policies, versioning
- **VPC**
  - Subnets (public/private)
  - Route tables
  - Security Groups vs NACLs
- **Load Balancers**
  - ALB vs NLB
- **Auto Scaling**
  - Scaling policies
- **Databases**
  - RDS (SQL mindset)
  - DynamoDB (Partition key, GSI, hot partitions)
- **Monitoring**
  - CloudWatch metrics, logs, alarms
- **Serverless**
  - Lambda cold start
  - API Gateway
- **CI/CD**
  - Build → Test → Deploy pipelines
- **IaC**
  - CloudFormation
  - CDK (more below)
- **High Availability**
  - Multi-AZ design
  - Failover
- **Cost Optimization**
  - Right sizing
  - On-Demand vs Reserved
  - Data transfer cost awareness

👉 **Amazon interview expectation:** They'll ask *why* you chose a service, not definitions.

### 2️⃣ System Design (THIS separates Junior vs Senior)

You don't "know" system design until you think in trade-offs.

**Core Concepts (Must-know)**

- Client–Server architecture
- REST vs gRPC
- Stateless vs Stateful services
- Horizontal vs Vertical scaling
- Load balancing strategies
- Caching (Redis / Memcached)
- Database sharding
- Read replicas
- CAP theorem
- Consistency models (eventual, strong)
- Rate limiting
- Idempotency
- Backpressure
- Message queues (SQS / Kafka concepts)

**Design Patterns used in real services**

- API Gateway pattern
- Fan-out / Fan-in
- CQRS (basic idea)
- Circuit breaker
- Retry with exponential backoff
- Saga (distributed transactions)

### 3️⃣ Real-World Application Example

👉 **"Instagram handling millions of likes/hour"**

Think in steps, not magic:

1. User clicks Like
2. Request hits Load Balancer
3. API service validates user
4. Writes to fast datastore (DynamoDB / Redis)
5. Increment counter (atomic)
6. Event pushed to queue
7. Async workers:
   - Update analytics
   - Update recommendations
8. Cache updated
9. UI reads from cache (not DB)

**Key ideas:**
- Async processing
- Eventually consistent
- Write-heavy optimization
- Hot key avoidance

If you understand this flow → you're industry ready.

### 4️⃣ ML for Senior SDE (Real, not academic)

They don't expect you to train transformers from scratch.

**What they ACTUALLY expect**
- ML system thinking
- Model lifecycle

**Core ML Concepts**
- Feature engineering
- Offline training vs online inference
- Batch vs real-time prediction
- Model versioning
- Data drift
- Concept drift
- A/B testing for ML
- Precision / Recall trade-offs
- Bias & fairness (important at Amazon)

**Tools you should recognize**
- TensorFlow / PyTorch (high level)
- Feature stores
- Model registry
- Inference endpoints
- Monitoring ML models

👉 **Interview question example:** "How do you detect your model is degrading in production?"

### 5️⃣ Authentication & Security (Very Important)

**Authentication types**
- Session-based auth
- Token-based auth (JWT)
- OAuth 2.0
- OpenID Connect

**OAuth (Must understand flow)**
- Authorization server
- Resource server
- Access token
- Refresh token
- Client ID & Secret

**Real-world auth flow**
- Signup
- Login
- Token issuance
- Token validation
- Token expiry
- Token revocation

**Also know:**
- Password hashing
- HTTPS/TLS basics
- Secrets management

### 6️⃣ AWS CDK (Modern Amazon teams use this)

**CDK concepts**
- Infrastructure as code using real programming languages
- Stacks
- Constructs
- App → Stack → Resources
- Deploy = CloudFormation underneath

**Why CDK?**
- Version controlled infra
- Reusable components
- Safer deployments

### 7️⃣ MCP Server / Internal Platforms Thinking

This is excellent senior-level thinking 👍

**Know:**
- Service ownership
- APIs as contracts
- Backward compatibility
- Versioning
- Observability (logs, metrics, traces)
- SLAs / SLOs
- On-call culture

### 8️⃣ Production Engineering (Highly Underrated)

You'll shine if you know this:

- Logging (structured logs)
- Metrics vs Logs vs Traces
- Alarms & alert fatigue
- Root cause analysis (RCA)
- Rollbacks
- Feature flags
- Blue-green deployments
- Canary releases

### 9️⃣ Amazon-Specific Culture (Hidden Curriculum)

- Write design docs
- Think in Leadership Principles
- Ownership mindset
- Bias for action
- Data-driven decisions

## 🧠 FINAL PRIORITY ORDER (If time is limited)

1. **AWS core services**
2. **System design fundamentals**
3. **Auth + security**
4. **Real-world scaling patterns**
5. **Production & ops**
6. **CDK**
7. **ML system design (if ML-inclined)**


------------------------------------------------------------------------------------------

# 90-Day Pre-Joining Roadmap (Amazon SDE-1 Ready)

## 🧭 Overview

Think of this as 3 phases:

| Phase | Goal |
|-------|------|
| **Month 1** | Become Cloud + Service aware |
| **Month 2** | Think like a System Designer |
| **Month 3** | Think like a Production Engineer / Senior SDE |

## 🔵 MONTH 1 — AWS + Backend Foundations

**Goal:** You should NOT feel scared when someone says "deploy this service"

### Week 1: AWS Core (Hands-on mindset)
**Focus on WHY, not definitions.**

- **Cloud fundamentals** (IaaS / PaaS / Serverless)
- **AWS Global Infrastructure**
- **IAM**
  - Users vs Roles
  - AssumeRole
  - Least privilege
- **EC2 basics**
- **S3 basics**

✅ **Outcome:** You can explain why IAM roles are used instead of credentials on EC2

### Week 2: Networking + Compute
- **VPC**
  - Public vs Private subnet
  - Route tables
  - Security Groups vs NACLs
- **Load Balancers** (ALB vs NLB)
- **Auto Scaling Groups**

**Mini mental exercise:** "What happens if one AZ goes down?"

### Week 3: Databases + Monitoring
- **RDS**
  - Read replicas
  - Multi-AZ
- **DynamoDB**
  - Partition key
  - Hot partition problem
- **CloudWatch**
  - Metrics
  - Logs
  - Alarms

**Important:** Learn when **NOT** to use DynamoDB

### Week 4: Serverless + CI/CD
- **Lambda**
- **API Gateway**
- **Cold start problem**
- **CI/CD pipeline basics**
- **High availability**
- **Cost optimization basics**

## 🎯 Month-1 Checkpoint
You should confidently answer: **"How would you deploy a basic backend service on AWS?"**

## 🟠 MONTH 2 — System Design (Core Differentiator)

**Goal:** Learn to design scalable systems, not just code.

### Week 5: System Design Fundamentals
- Client–Server architecture
- REST vs gRPC
- Stateless vs Stateful services
- Horizontal vs Vertical scaling
- CAP theorem
- Consistency models

**Think:** "What breaks first when traffic increases?"

### Week 6: Data & Caching
- SQL vs NoSQL trade-offs
- Sharding
- Indexing (high-level)
- **Caching**
  - Read-through
  - Write-through
  - Cache invalidation strategies

**Classic interview trap:** "Why not cache everything?"

### Week 7: Async & Distributed Systems
- Message queues (concepts)
- Event-driven architecture
- Idempotency
- Retry with backoff
- Rate limiting

**Real-world thinking:** "User clicks like 10 times — what happens?"

### Week 8: Case Studies (Very Important)
Design at high level:
- Instagram Likes
- URL Shortener
- Notification System
- Payment processing (conceptual)

## 🎯 Month-2 Checkpoint
You should explain: **"How Instagram handles millions of likes per hour"**

## 🟢 MONTH 3 — Senior SDE Mindset (Production + Security + ML)

**Goal:** Think beyond features → reliability & ownership

### Week 9: Authentication & Security
- Password hashing
- Session vs Token auth
- JWT
- **OAuth 2.0**
  - Authorization server
  - Access & refresh tokens
- HTTPS & TLS basics
- Secrets management

**Must-know:** "Why tokens expire"

### Week 10: Production Engineering
- Logs vs Metrics vs Traces
- Alert fatigue
- Root cause analysis (RCA)
- Rollbacks
- Feature flags
- Blue-green & Canary deployments

**Senior thinking:** "How do you fix prod without breaking users?"

### Week 11: AWS CDK + Infra Thinking
- Infrastructure as Code
- **CDK concepts**
  - App
  - Stack
  - Constructs
- Why CDK > manual console work
- Safe deployments

*You don't need mastery — conceptual clarity*

### Week 12: ML Systems (Senior-level, Real World)
*Not model math — system thinking*
- Offline training vs Online inference
- Feature pipelines
- Model versioning
- Data drift
- A/B testing
- Monitoring ML in production

**Interview-style thinking:** "How do you know your ML model is failing?"

## 🧠 FINAL CHECKLIST (If you can do this, you're READY)

You can:
1. **Read & modify existing backend code**
2. **Design scalable APIs**
3. **Explain AWS trade-offs**
4. **Debug production issues**
5. **Talk about auth & security confidently**
6. **Think in failure scenarios**
7. **Write clear design explanations**