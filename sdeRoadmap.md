# Sde Roadmap

# 🧱 LAYER 1: AWS & Cloud
**Goal:** You should be able to design + debug a production system, not just explain services.

## 1️⃣ Core AWS Concepts (Must know deeply)
> **Learn like this:** What problem does it solve? What can go wrong?

### **Compute**
- **EC2** (instance types, autoscaling, spot vs on-demand)
- **Containers:** ECS / EKS
- **Lambda** (cold start, statelessness)

### **Storage**
- **S3** (consistency, lifecycle rules, cost)
- **EBS vs EFS**
- **CDN:** CloudFront

### **Networking (VERY IMPORTANT)**
- **VPC, Subnets, Route tables**
- **Security Groups vs NACLs**
- **NAT Gateway, Internet Gateway**
- **Private vs public services**

### **IAM (Senior-level expectation)**
- **Users vs Roles vs Policies**
- **AssumeRole**
- **Least privilege**
- **Cross-account access**

### **Databases**
- **RDS** (indexes, read replicas)
- **DynamoDB** (partition key, hot partition, GSI, LSI)
- **Redis / ElastiCache** (cache patterns)

### **Observability**
- **CloudWatch metrics vs logs**
- **Alarms**
- **X-Ray / tracing**
- **Log aggregation mindset**

### **CI/CD**
- **Build → Test → Deploy → Rollback**
- **Blue-green vs Canary deployments**

### **Infrastructure as Code**
- **CloudFormation / Terraform**
- **Why manual infra is a bug**

### **Cost**
- **Cost Explorer**
- **Why over-provisioning kills teams**
- **Cost vs latency trade-off**

--------------------------------------------------------------------------------------------------

# 🧠 LAYER 2: REAL System Design (Senior Interview Level)
**This is where most people fail.**

## Core System Design Foundations
> **You must internalize these mentally, not memorise.**

### 1️⃣ Scalability
- **Vertical vs Horizontal scaling**
- **Stateless services**
- **Sharding strategies**

### 2️⃣ Data
- **SQL vs NoSQL trade-offs**
- **Indexing vs write cost**
- **Eventual consistency**
- **CAP theorem** (applied, not theory)

### 3️⃣ Performance
- **Latency budget**
- **Network calls > CPU cost**
- **Caching layers** (client, server, CDN)

### 4️⃣ Reliability
- **Single point of failure**
- **Timeouts**
- **Retries** (and retry storms!)
- **Circuit breakers**
- **Idempotency**

### 5️⃣ Messaging
- **Kafka / SQS / SNS**
- **Async vs sync**
- **Exactly-once is a lie** (almost)

### 6️⃣ APIs
- **REST vs gRPC**
- **Versioning**
- **Backward compatibility**

--------------------------------------------------------------------------------------------------

# 🏗️ LAYER 3: REAL-WORLD APPLICATION EXAMPLES (This is GOLD)

## Example: Instagram Reels – Millions of Likes / Hour

### What actually happens:
- **User taps ❤️**
- **Request hits Load Balancer**
- **Auth validated** (token)
- **Like event written asynchronously**
- **Event pushed to Kafka / SQS**
- **Counter updated in:**
  - Redis (fast read)
  - DB (eventual write)
- **Feed service reads from cache**
- **Periodic batch jobs reconcile counts**

### Key ideas you must know:
- **Never update DB synchronously**
- **Counters are approximate**
- **Cache is source of truth for reads**
- **DB is source of truth for recovery**
- **Writes are batched**

### If interviewer asks:
> **“What if Redis crashes?”**

**You answer:**
- **Rebuild from Kafka logs / DB**
- **Graceful degradation**


--------------------------------------------------------------------------------------------------

# 🤖 LAYER 4: REAL-WORLD ML for Senior SDE (Very Important)
> **This is NOT Kaggle ML.**

## What Senior SDEs Are Expected to Know

### 1️⃣ ML System Architecture
- **Training pipeline**
- **Inference pipeline**
- **Feature store**
- **Model registry**
- **Versioning**

### 2️⃣ Data
- **Data drift**
- **Concept drift**
- **Training vs inference skew**
- **Label delays**

### 3️⃣ Serving
- **Batch vs real-time inference**
- **Latency vs accuracy trade-off**
- **Shadow deployment**
- **A/B testing models**

### 4️⃣ Monitoring
- **Model accuracy in production**
- **Feature distribution shift**
- **Alerts when model degrades**

### 5️⃣ ML Ops
- **Retraining triggers**
- **Rollback models**
- **Canary models**

### 6️⃣ Tools (You don’t need mastery, but familiarity)
- **TensorFlow / PyTorch** (you know)
- **SageMaker** (very relevant for Amazon)
- **Feature stores**
- **Offline vs online pipelines**

## Interview Reality

### They ask:
- **“How would you deploy this model?”**
- **“What if data distribution changes?”**
- **“How do you debug bad predictions?”**

### Not:
- “Derive gradient descent”


--------------------------------------------------------------------------------------------------

# 🧩 LAYER 5: OTHER CRITICAL INDUSTRY TOPICS

### Backend Engineering
- **Concurrency**
- **Thread pools**
- **Async programming**
- **Memory leaks**
- **JVM vs Python performance**

### Security
- **Authentication vs Authorization**
- **Token expiry**
- **Rate limiting**
- **OWASP basics**

### Code Quality
- **Clean code**
- **SOLID principles**
- **Refactoring**
- **Testing** (unit, integration)

### Incident Response
- **On-call mindset**
- **Rollbacks**
- **Postmortems**
- **Blameless culture**

--------------------------------------------------------------------------------------------------

# 🗺️ FINAL ROADMAP (High-Level Order)

## Phase 1 (Before joining / First 3 months)
- **AWS fundamentals** (hands-on)
- **Basic system design**
- **One full backend service project**

## Phase 2 (6–12 months)
- **Deep distributed systems**
- **Production debugging**
- **Scaling bottlenecks**
- **Caching + messaging mastery**

## Phase 3 (Senior readiness)
- **Large-scale system design**
- **ML systems** (if ML-oriented)
- **Cost & reliability ownership**
- **Mentoring juniors**

--------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------



# “Deploy changes through CDK instead of manual AWS changes” comes under 👇

## 🧱 Infrastructure as Code (IaC)
> 👉 and more broadly under **Production Engineering / DevOps / Platform Engineering**

### Let me anchor this properly in your roadmap 👇

### 1️⃣ Primary Category (Must-know for SDEs)
**Infrastructure as Code (IaC)**
*AWS CDK, CloudFormation, Terraform all fall here.*

**What this means in industry:**
- **Infra is treated like code**
- **Version controlled** (Git)
- **Reviewed** (PRs)
- **Reproducible**
- **Rollback-able**

> 🔥 **Manual console changes = production risk**

--------------------------------------------------------------------------------------------------


# 2️⃣ Why Amazon (and big tech) CARES a lot about this

### In real companies:
- **Manual changes cause configuration drift**
- **No audit trail**
- **Hard to reproduce bugs**
- **Impossible to scale teams**

### So:
> **“If it’s not in CDK/Terraform, it doesn’t exist.”**

**This mindset is very Amazon-like.**


--------------------------------------------------------------------------------------------------
# 3️⃣ Where this fits in your BIG roadmap

### High-level map:

**Cloud Computing**
 ├── Compute / Storage / Network
 ├── Security (IAM)
 ├── Observability
 ├── CI/CD
 └── **Infrastructure as Code** ⭐⭐⭐
       ├── AWS CDK
       ├── CloudFormation
       ├── Terraform


--------------------------------------------------------------------------------------------------

# 4️⃣ What CDK knowledge signals in interviews 🚀

### If you say:
> **“We deploy infra using CDK instead of manual AWS changes”**

### Interviewer immediately infers:
- **You understand production discipline**
- **You care about reproducibility**
- **You think in systems, not UI clicks**
- **You can work in large teams**

> **That’s senior thinking, even for SDE-1.**
--------------------------------------------------------------------------------------------------

# 5️⃣ Practical Example (Very Interview-Relevant)

### ❌ Bad (junior / risky)
- **Go to AWS console**
- **Change security group manually**
- **Update EC2 config manually**
- **Forget to document**

### ✅ Good (industry-grade)
- **Update CDK stack**
- **PR → review**
- **CI/CD deploys stack**
- **Infra versioned**
- **Easy rollback**

> **You should be able to say this clearly.**
--------------------------------------------------------------------------------------------------

# 6️⃣ Deeper: What CDK actually touches
> **CDK is NOT just “infra” — it interacts with:**

| Area | Example |
| :--- | :--- |
| **Networking** | VPC, subnets |
| **Security** | IAM roles |
| **Compute** | ECS, Lambda |
| **Scaling** | Auto Scaling |
| **Deployment** | Blue/Green |
| **Cost** | Right sizing |
| **Reliability** | Multi-AZ |

> **So it sits at the intersection of many concepts.**


--------------------------------------------------------------------------------------------------

# 7️⃣ Interview framing (copy this mentally)

### If asked:
> **“How do you manage infra changes?”**

### You say:
> “We use **Infrastructure as Code (AWS CDK).**
> All infra changes go through **code reviews and CI/CD.**
> This avoids **config drift**, improves **rollback**, and ensures **reproducibility**.”

> **That answer = 🔥**
--------------------------------------------------------------------------------------------------

# 8️⃣ Where YOU should place this in your learning checklist

- [ ] Cloud Basics
- [ ] Networking
- [ ] IAM
- [x] **Infrastructure as Code (CDK) ← YOU ARE HERE**
- [ ] CI/CD
- [ ] System Design
- [ ] Production Debugging