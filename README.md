# Azure
Microsoft Azure

# Microsoft Azure: Zero to Advanced — Complete Study Notes

**Instructor:** Azure Teacher / Cloud Architect / Interview Mentor  
**Version:** Current as of 2025 — always verify against official Microsoft Learn docs for latest limits, SKUs, and prices.

---

## How to Use These Notes

| Symbol | Meaning |
|--------|---------|
| **Prerequisite** | Study this first |
| 💡 | Key insight |
| ⚠️ | Common mistake |
| 🔒 | Security note |
| 💰 | Cost note |
| 🎯 | Interview focus |
| 📝 | Exam focus |

**Learning path:** Read module → do the practical → answer interview questions → take MCQs → revise with "Module Revision."

---

# MODULE 1: Cloud Computing Fundamentals

**Prerequisite:** None

## 1. Definition

**Cloud computing** = renting computing resources (servers, storage, databases, networking, software) over the internet, paying only for what you use, instead of buying and maintaining your own physical data center.

**Simple analogy:** Instead of buying a generator, you buy electricity from the grid. You don't own the power plant; you just pay for usage.

## 2. Why It Exists

Before cloud:
- Companies bought servers (capital expense), waited weeks for delivery, guessed capacity.
- If traffic spiked, servers crashed. If traffic dropped, expensive hardware sat idle.
- Needed teams to maintain hardware, cooling, power, security.

Cloud solves:
- **No upfront cost** → operational expense
- **Elasticity** → scale up/down in minutes
- **Global reach** → deploy in dozens of regions
- **Focus on code**, not hardware

## 3. How It Works

```
Traditional IT                    Cloud
─────────────                     ─────
You buy server                    Provider owns hardware
You install OS                    You pick OS image
You manage everything             Provider manages physical layer
You pay upfront                   You pay per hour/second
```

**Shared Responsibility Model** — the single most important cloud concept:

| Layer | On-Prem | IaaS | PaaS | SaaS |
|-------|---------|------|------|------|
| Data & access | You | You | You | You |
| Applications | You | You | You | Provider |
| Runtime | You | You | Provider | Provider |
| OS | You | You | Provider | Provider |
| Virtualization | You | Provider | Provider | Provider |
| Servers/Storage | You | Provider | Provider | Provider |
| Network | You | Provider | Provider | Provider |
| Physical | You | Provider | Provider | Provider |

💡 **IaaS** = Infrastructure as a Service (VMs)  
**PaaS** = Platform as a Service (App Service, SQL Database)  
**SaaS** = Software as a Service (Microsoft 365, Dynamics)

## 4. Important Components

- **Compute** — CPU/RAM to run code
- **Storage** — disks, blobs, files
- **Network** — connectivity, firewalls, load balancing
- **Identity** — who can access what
- **Monitoring** — logs, metrics, alerts
- **Governance** — policies, budgets, compliance

## 5. Cloud Service Models Compared

| Model | You manage | Provider manages | Example | Use when |
|-------|-----------|------------------|---------|----------|
| On-prem | Everything | Nothing | Your data center | Regulatory, legacy |
| IaaS | OS, runtime, apps, data | Hardware, network | Azure VM | Full control needed |
| PaaS | Apps, data | OS, runtime, hardware | Azure App Service | Focus on code |
| SaaS | Data & access | Everything else | Microsoft 365 | Standard software |

## 6. Cloud Deployment Models

- **Public cloud** — Azure, AWS, GCP (shared, multi-tenant)
- **Private cloud** — dedicated to one org (Azure Stack)
- **Hybrid cloud** — mix of on-prem + public (most enterprises)
- **Multi-cloud** — using 2+ providers

## 7. Key Architectural Concepts

| Concept | Meaning | Example |
|---------|---------|---------|
| **Scalability** | Ability to handle growth | Add more VMs |
| **Elasticity** | Auto scale up/down | Auto-scale on CPU >70% |
| **Availability** | Uptime | 99.9% SLA |
| **Reliability** | Consistent correct operation | Retries, redundancy |
| **Fault tolerance** | Survive component failure | Availability Zones |
| **High Availability (HA)** | Minimal downtime | Load-balanced VMs in 2 zones |
| **Disaster Recovery (DR)** | Recover from region failure | Geo-replicated backups |
| **Performance** | Speed/latency | SSD, CDN, caching |
| **Cost optimization** | Spend efficiently | Reserved instances, right-sizing |
| **Least privilege** | Minimum needed access | RBAC scoped roles |

## 8. Real-World Use Case

A startup launches a web app:
- Week 1: 100 users → 1 small VM
- Week 4: viral → auto-scale to 20 VMs
- Week 8: traffic drops → scale back to 2 VMs
- Total cost tracks usage; no wasted hardware.

## 9. Interview Questions

**Beginner:** What is cloud computing?
**Intermediate:** Explain shared responsibility model.
**Advanced:** When would you choose IaaS over PaaS?

## 10. Revision Notes

- Cloud = rent, don't buy
- IaaS/PaaS/SaaS = who manages what
- Shared responsibility shifts with model
- Scalability ≠ elasticity (capacity vs automatic adjustment)
- HA ≠ DR (uptime vs recovery)

### Module 1 Revision

**Key concepts:** Cloud models, shared responsibility, IaaS/PaaS/SaaS, HA/DR/scalability.
**MCQs:**
1. In PaaS, who manages the OS? (Provider)
2. Which model gives most control? (IaaS)
3. 99.9% uptime = how much downtime/year? (~8.76 hours)
4. Auto-scaling is an example of? (Elasticity)
5. Least privilege means? (Minimum access needed)

---

# MODULE 2: Microsoft Azure Fundamentals

**Prerequisite:** Module 1

## 1. Definition

**Microsoft Azure** = Microsoft's public cloud platform offering 200+ services: compute, storage, networking, databases, AI, IoT, security, DevOps.

## 2. Why It Exists

Microsoft needed to compete with AWS; enterprises already used Windows Server, Active Directory, SQL Server, .NET → Azure integrates natively.

## 3. How It Works

```
User/App
   │
   ▼
Azure Portal / CLI / SDK / API
   │
   ▼
Azure Resource Manager (ARM)  ← control plane
   │
   ▼
Resource Providers (Compute, Network, Storage...)
   │
   ▼
Physical datacenters (regions)
```

## 4. Important Components

- **Management groups** → subscriptions → resource groups → resources
- **Resource providers** — APIs for each service
- **Azure Portal** — web UI
- **Azure CLI / PowerShell** — command line
- **SDKs** — .NET, Python, Java, JS, Go
- **ARM templates / Bicep** — IaC

## 5. Azure Example

Deploy a web app:
```bash
az group create --name rg-web --location eastus
az appservice plan create --name plan1 --resource-group rg-web --sku B1 --is-linux
az webapp create --name myapp123 --resource-group rg-web --plan plan1 --runtime "NODE:18-lts"
```

## 6. Real-World Use Cases

- Lift-and-shift SAP to Azure VMs
- Modernize .NET apps to App Service
- Global SaaS on Azure Front Door + AKS

## 7. Important Terminology

| Term | Meaning |
|------|---------|
| Tenant | Your organization's Azure AD instance |
| Subscription | Billing + access boundary |
| Resource Group | Logical container for resources |
| Resource | Individual service instance |
| Region | Geographic datacenter cluster |
| ARM | Azure Resource Manager (control plane) |

## 8. Configuration

**Portal:** portal.azure.com → Create a resource → search service → fill wizard → Review + create.

**CLI:**
```bash
az login
az account show
az account list --output table
az group list --output table
```

**PowerShell:**
```powershell
Connect-AzAccount
Get-AzSubscription
Get-AzResourceGroup
```

## 9. Architecture

```
Tenant (contoso.onmicrosoft.com)
 └── Management Group (Root)
      └── Subscription (Production)
           └── Resource Group (rg-web)
                ├── App Service
                ├── SQL Database
                └── Storage Account
```

## 10. Comparison: Azure vs AWS vs GCP

| Aspect | Azure | AWS | GCP |
|--------|-------|-----|-----|
| Strength | Enterprise, Microsoft stack | Broadest services | Data/AI, Kubernetes |
| Identity | Entra ID | IAM | Cloud IAM |
| Compute | VM, App Service, Functions | EC2, Elastic Beanstalk, Lambda | GCE, App Engine, Cloud Functions |
| Kubernetes | AKS | EKS | GKE |

## 11. Security

- Enable MFA on all accounts
- Use Entra ID (not local accounts)
- Apply RBAC least privilege
- Enable Azure Defender / Defender for Cloud

## 12. Cost

- Free tier + 12-month free services
- Pay-as-you-go vs Enterprise Agreement vs CSP
- Use Pricing Calculator before deploying

## 13. Common Mistakes

⚠️ Using one subscription for everything  
⚠️ No resource group naming convention  
⚠️ Leaving resources running after labs  
⚠️ Using owner role for everyone

## 14. Interview Questions

**Beginner:** What is Azure?  
**Intermediate:** Difference between subscription and resource group?  
**Advanced:** How does ARM control plane differ from data plane?

## 15. Revision Notes

- Azure = Microsoft cloud, 200+ services
- Hierarchy: MG → Sub → RG → Resource
- ARM = control plane
- Portal/CLI/PowerShell/SDK/Bicep = interfaces

### Module 2 Revision

**Key services:** Portal, CLI, ARM, Resource Groups.  
**Commands:** `az login`, `az group create`, `Connect-AzAccount`.  
**MCQs:**
1. What is the top-level container for Azure resources? (Management group / tenant)
2. Which tool is declarative IaC? (Bicep/ARM)
3. RBAC stands for? (Role-Based Access Control)
4. Which is NOT an Azure interface? (Docker CLI — unless AKS)
5. Resource group can span regions? (Yes, resources can be in different regions than RG)

---

# MODULE 3: Azure Account, Portal, Subscriptions, Resource Groups

**Prerequisite:** Module 2

## 1. Definition

- **Account** — your identity (Microsoft account or work account)
- **Tenant** — Entra ID directory for your org
- **Subscription** — billing and access boundary
- **Resource Group** — logical folder for related resources

## 2. Why It Exists

Enterprises need:
- Separate billing per department → subscriptions
- Separate environments (dev/test/prod) → subscriptions or RGs
- Delegated administration → RBAC on RG/subscription

## 3. How It Works

```
Entra ID Tenant
 ├── Subscription A (Production)
 │    ├── RG-Web
 │    └── RG-Data
 ├── Subscription B (Dev)
 │    └── RG-Dev
 └── Subscription C (Sandbox)
```

## 4. Important Components

- **Management groups** — group subscriptions for policy/RBAC
- **Subscriptions** — billing + quotas + access
- **Resource groups** — lifecycle container (delete RG = delete all inside)
- **Tags** — key/value metadata (env=prod, owner=team)

## 5. Azure Example

```bash
# Create management group hierarchy
az management-group create --name "Contoso" --display-name "Contoso Root"
az management-group create --name "Prod" --parent Contoso

# Create subscription (requires EA/MCA)
# Move subscription under MG
az management-group subscription add --management-group-id Prod --subscription <sub-id>
```

## 6. Real-World Use Cases

- **Large bank:** MG per business unit → subscription per app → RG per environment
- **Startup:** 1 subscription, RG per project, tags for cost tracking

## 7. Terminology

| Term | Meaning |
|------|---------|
| Tenant ID | GUID for Entra ID |
| Subscription ID | GUID for billing |
| RG | Resource Group |
| ARM ID | Full resource path `/subscriptions/.../resourceGroups/.../providers/...` |

## 8. Configuration

**Portal:** All Services → Resource groups → Create.  
**CLI:**
```bash
az group create -n rg-demo -l eastus --tags env=dev owner=you
az group list --query "[].{Name:name, Location:location}" -o table
az group delete -n rg-demo --yes --no-wait
```

## 9. Architecture

```
Management Group: Contoso
├── MG: Platform
│    ├── Sub: Identity
│    └── Sub: Networking
└── MG: Landing Zones
     ├── Sub: Prod
     └── Sub: NonProd
```

## 10. Comparison

| Scope | Use for |
|-------|---------|
| Management group | Policy, RBAC across many subs |
| Subscription | Billing, quotas, separation |
| Resource group | Lifecycle, RBAC, tagging |
| Resource | Individual service |

## 11. Security

- Separate prod/non-prod subscriptions
- Use PIM (Privileged Identity Management) for just-in-time roles
- Deny assignments at MG level

## 12. Cost

- Tags enable chargeback
- Cost Management + Budgets per RG/subscription
- Delete unused RGs

## 13. Common Mistakes

⚠️ Putting prod and dev in same RG  
⚠️ No tags → can't track cost  
⚠️ Deleting RG without checking contents  
⚠️ Using personal Microsoft account for enterprise

## 14. Interview Questions

**Beginner:** What is a resource group?  
**Intermediate:** Can a resource be in multiple RGs? (No)  
**Advanced:** Design subscription strategy for 500-developer org.

## 15. Revision Notes

- Tenant → MG → Sub → RG → Resource
- RG is lifecycle boundary
- Tags = metadata for cost/governance
- Subscriptions = billing + security boundary

---

# MODULE 4: Azure Regions, Availability Zones, Geography

**Prerequisite:** Module 3

## 1. Definition

- **Region** — geographic area with datacenters (e.g., East US, West Europe)
- **Availability Zone (AZ)** — physically separate datacenter within a region
- **Geography** — political boundary (US, Europe, Asia) for compliance
- **Paired region** — 300+ miles away for DR (e.g., East US ↔ West US)

## 2. Why It Exists

- **Latency** — put app near users
- **Compliance** — data must stay in country (GDPR)
- **Resilience** — survive datacenter/region failure
- **Cost** — prices vary by region

## 3. How It Works

```
Region: East US
├── AZ 1 (datacenter)
├── AZ 2 (datacenter)
└── AZ 3 (datacenter)
     │
     └── Paired: West US (300+ miles away)
```

## 4. Important Components

- **Region** — 60+ globally
- **AZ** — 3+ per enabled region
- **Region pair** — for geo-redundant services
- **Sovereign clouds** — US Gov, China (21Vianet), Germany

## 5. Azure Example

Deploy VM in Zone 1, another in Zone 2, load balance:
```bash
az vm create -n vm1 -g rg-ha --image Ubuntu2204 --zone 1
az vm create -n vm2 -g rg-ha --image Ubuntu2204 --zone 2
az network lb create -n lb1 -g rg-ha --sku Standard
```

## 6. Real-World Use Cases

- **Bank:** Data must stay in EU → West Europe region
- **Gaming:** Low latency → deploy in 10 regions + Front Door
- **Healthcare:** HIPAA → US regions + paired region DR

## 7. Terminology

| Term | Meaning |
|------|---------|
| Region | Geographic deployment target |
| AZ | Isolated datacenter group |
| Zone-redundant | Replicated across AZs |
| Locally redundant | Within one datacenter |
| Geo-redundant | Across paired regions |

## 8. Configuration

**Portal:** Create resource → select Region dropdown → check "Availability zones."  
**CLI:**
```bash
az account list-locations -o table
az vm create ... --zone 1
az aks create ... --zones 1 2 3
```

## 9. Architecture

```
Users worldwide
   │
   ▼
Azure Front Door (global)
   │
   ├── East US (AZ1, AZ2, AZ3)
   ├── West Europe (AZ1, AZ2, AZ3)
   └── Southeast Asia (AZ1, AZ2, AZ3)
```

## 10. Comparison

| Redundancy | Protects against | Example |
|------------|------------------|---------|
| LRS | Disk failure | Storage LRS |
| ZRS | Datacenter failure | Storage ZRS |
| GRS | Region failure | Storage GRS |
| GZRS | Both | Storage GZRS |

## 11. Security

- Data residency compliance
- Sovereign clouds for government
- Customer Lockbox for support access

## 12. Cost

- Same service costs differ by region (e.g., Brazil South higher)
- Cross-region egress costs money
- AZ redundancy may cost more (ZRS vs LRS)

## 13. Common Mistakes

⚠️ Assuming all services available in all regions  
⚠️ Not using paired region for DR  
⚠️ Ignoring data sovereignty  
⚠️ Cross-region traffic costs

## 14. Interview Questions

**Beginner:** What is a region?  
**Intermediate:** Difference between AZ and region pair?  
**Advanced:** Design multi-region active-active for 99.99% SLA.

## 15. Revision Notes

- Region = geographic cluster
- AZ = isolated datacenter in region
- Paired region = DR target
- LRS/ZRS/GRS/GZRS = redundancy levels

---

# MODULE 5: Azure Resource Manager (ARM)

**Prerequisite:** Module 3

## 1. Definition

**ARM** = the deployment and management layer for Azure. Every request (Portal, CLI, SDK) goes through ARM, which authenticates, authorizes, and routes to resource providers.

## 2. Why It Exists

Before ARM (classic/ASM), resources were managed individually, no grouping, no RBAC, no templates. ARM introduced:
- Declarative templates
- RBAC
- Tags
- Locks
- Consistent API

## 3. How It Works

```
Client (Portal/CLI/SDK)
   │ HTTPS + Entra token
   ▼
ARM (control plane)
   │ validate + authorize
   ▼
Resource Provider (e.g., Microsoft.Compute)
   │
   ▼
Resource created
```

## 4. Important Components

- **Resource providers** — `Microsoft.Compute`, `Microsoft.Network`, `Microsoft.Storage`
- **ARM templates** — JSON declarative
- **Bicep** — DSL that compiles to ARM JSON
- **Deployment modes** — Incremental (default), Complete (deletes extra)
- **Template specs** — shareable templates
- **Deployment stacks** — manage lifecycle of a collection

## 5. Azure Example

`main.bicep`:
```bicep
param location string = resourceGroup().location
param storageName string

resource stg 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: storageName
  location: location
  sku: { name: 'Standard_LRS' }
  kind: 'StorageV2'
}
```

Deploy:
```bash
az deployment group create -g rg-demo -f main.bicep -p storageName=mystg123
```

## 6. Real-World Use Cases

- CI/CD pipelines deploy Bicep to dev/test/prod
- Template specs for company-wide standards
- Deployment stacks to prevent manual deletion

## 7. Terminology

| Term | Meaning |
|------|---------|
| Idempotent | Re-running same template = same result |
| Incremental | Add/update, don't delete |
| Complete | Delete resources not in template |
| What-if | Preview changes |

## 8. Configuration

**CLI:**
```bash
az deployment group what-if -g rg-demo -f main.bicep
az deployment group create -g rg-demo -f main.bicep
az deployment sub create -l eastus -f sub.bicep
az deployment mg create -m Contoso -f mg.bicep
```

**PowerShell:**
```powershell
New-AzResourceGroupDeployment -ResourceGroupName rg-demo -TemplateFile main.bicep
```

## 9. Architecture

```
main.bicep
 ├── module network.bicep
 ├── module compute.bicep
 └── module data.bicep
```

## 10. Comparison: ARM vs Bicep vs Terraform

| Feature | ARM JSON | Bicep | Terraform |
|---------|----------|-------|-----------|
| Syntax | Verbose JSON | Clean DSL | HCL |
| State | Azure-managed | Azure-managed | Local/remote state |
| Multi-cloud | No | No | Yes |
| Azure support | Native | Native | Strong |
| Learning curve | High | Low | Medium |

## 11. Security

- Store secrets in Key Vault, reference in template
- Use managed identity for deployment
- Scope deployments to RG, not subscription, where possible

## 12. Cost

- ARM itself is free
- Bad templates can create expensive resources → use what-if

## 13. Common Mistakes

⚠️ Using Complete mode accidentally → deletes resources  
⚠️ Hardcoding secrets in templates  
⚠️ No parameter files per environment  
⚠️ Not using modules → giant templates

## 14. Interview Questions

**Beginner:** What is ARM?  
**Intermediate:** Incremental vs Complete mode?  
**Advanced:** How does ARM handle idempotency and dependencies?

## 15. Revision Notes

- ARM = control plane for all Azure
- Bicep = cleaner ARM
- What-if before deploy
- Modules for reuse

---

# MODULE 6: Azure Compute

**Prerequisite:** Modules 1–5

## 6.1 Virtual Machines

### 1. Definition
**Azure VM** = IaaS virtual server you fully control (OS, software, config).

### 2. Why It Exists
Lift-and-shift legacy apps, custom OS, full control, GPU workloads.

### 3. How It Works
```
Image (OS) + Size (CPU/RAM) + Disk + Network → VM
```

### 4. Components
- **Size** — B, D, E, F, M, N series (general, compute, memory, GPU)
- **Disk** — OS disk, data disks (Premium SSD, Ultra)
- **NIC** — network interface
- **Extensions** — agents (monitoring, custom script)

### 5. Example
```bash
az vm create -n web01 -g rg-web --image Ubuntu2204 --size Standard_B2s \
  --admin-username azureuser --generate-ssh-keys --public-ip-sku Standard
```

### 6. Use Cases
- SAP, Oracle DB, legacy .NET Framework
- Dev/test environments
- GPU rendering, ML training

### 7. Terminology
| Term | Meaning |
|------|---------|
| vCPU | Virtual CPU |
| Premium SSD | High-performance disk |
| Spot VM | Cheap, evictable |
| Reserved Instance | 1–3 yr discount |

### 8. Configuration
**Portal:** Create VM → pick image, size, network, disk → Review.  
**CLI:** above.  
**IaC:** Bicep `Microsoft.Compute/virtualMachines`.

### 9. Architecture
```
Internet → Public IP → NIC → VM (OS + Data Disk)
```

### 10. Comparison
| | VM | App Service | Functions |
|--|----|-------------|-----------|
| Control | Full | Medium | Low |
| Manage OS | Yes | No | No |
| Scale | Manual/VMSS | Auto | Auto |
| Cost model | Per hour | Per plan | Per execution |
| Use | Legacy, custom | Web apps | Event-driven |

### 11. Security
- NSG on subnet/NIC
- Just-in-time VM access
- Disk encryption (ADE or SSE)
- Patch management via Update Manager

### 12. Cost
- Spot VMs up to 90% off
- Reserved 1–3 yr ~40–72% off
- Deallocate to stop compute billing
- 💰 Stopped (not deallocated) VM still bills compute!

### 13. Common Mistakes
⚠️ Forgetting to deallocate  
⚠️ Using Basic public IP (no SLA)  
⚠️ No backup  
⚠️ Opening RDP/SSH to internet

### 14. Interview Questions
**Beginner:** What is a VM?  
**Intermediate:** Spot vs Reserved vs Pay-as-you-go?  
**Advanced:** Design HA VM architecture across AZs.

### 15. Revision Notes
- VM = IaaS, full control
- Deallocate to save cost
- NSG + JIT + encryption for security

---

## 6.2 VM Scale Sets (VMSS)

### 1. Definition
**VMSS** = group of identical VMs that auto-scale.

### 2. Why It Exists
Manual VM scaling is slow; VMSS adds/removes VMs based on metrics.

### 3. How It Works
```
Template (image, size, config) + Autoscale rules → N VMs
```

### 4. Components
- **Orchestration:** Uniform (same model) or Flexible (mix)
- **Autoscale:** CPU, memory, custom metrics, schedule
- **Load balancer** in front

### 5. Example
```bash
az vmss create -n webss -g rg-web --image Ubuntu2204 \
  --instance-count 2 --vm-sku Standard_B2s \
  --load-balancer lb-web --upgrade-policy-mode automatic
```

### 6. Use Cases
- Web frontends, batch processing, AKS node pools

### 7. Terminology
| Term | Meaning |
|------|---------|
| Min/Max/Default | Autoscale bounds |
| Scale-out | Add VMs |
| Scale-in | Remove VMs |
| Cool-down | Wait after scaling |

### 8. Configuration
Autoscale rule: CPU > 70% for 5 min → +1 VM (max 10).

### 9. Architecture
```
LB → VMSS (VM1, VM2, VM3...) → Backend
```

### 10. Comparison
| | VMSS | App Service | AKS |
|--|------|-------------|-----|
| Control | High | Medium | Highest |
| K8s | No | No | Yes |
| Best for | IaaS scale | Web apps | Microservices |

### 11. Security
- Same as VM
- Use managed identity
- Patch orchestration

### 12. Cost
- Scale in to min at night
- Spot instances in VMSS for batch

### 13. Common Mistakes
⚠️ No min instances → cold start  
⚠️ Aggressive scale-in → flapping  
⚠️ Not using Flexible for mixed SKUs

### 14. Interview Questions
**Beginner:** What is VMSS?  
**Intermediate:** Uniform vs Flexible?  
**Advanced:** Design autoscale for spiky traffic.

### 15. Revision Notes
- VMSS = auto-scaling identical VMs
- Rules based on metrics/schedule
- Flexible = newer, supports mix

---

## 6.3 App Service

### 1. Definition
**PaaS** for hosting web apps, REST APIs, mobile backends.

### 2. Why It Exists
No OS management; built-in scaling, SSL, deployment slots, CI/CD.

### 3. How It Works
```
Code → App Service Plan (compute) → App Service (your app)
```

### 4. Components
- **App Service Plan** — SKU (Free, Basic, Standard, Premium, Isolated)
- **Deployment slots** — staging/prod swap
- **Custom domains + SSL**
- **Auto-scale**
- **WebJobs** — background tasks

### 5. Example
```bash
az appservice plan create -n plan1 -g rg-web --sku P1v3 --is-linux
az webapp create -n myapp123 -g rg-web -p plan1 --runtime "NODE:18-lts"
az webapp deployment slot create -n myapp123 -g rg-web --slot staging
az webapp deployment slot swap -n myapp123 -g rg-web --slot staging --target-slot production
```

### 6. Use Cases
- .NET, Java, Node, Python, PHP web apps
- Internal APIs
- Mobile backends

### 7. Terminology
| Term | Meaning |
|------|---------|
| ASE | App Service Environment (isolated) |
| Slot | Staging copy |
| Swap | Promote staging → prod |
| Kudu | Debug console |

### 8. Configuration
**Portal:** Create Web App → runtime → plan → deploy via GitHub.  
**IaC:** `Microsoft.Web/sites`.

### 9. Architecture
```
Users → Front Door → App Service (slot: prod) → SQL DB
                         │ swap
                    slot: staging
```

### 10. Comparison
| | App Service | VM | Functions |
|--|-------------|-----|-----------|
| Manage OS | No | Yes | No |
| Always-on | Yes | Yes | Optional |
| Scale | Auto | VMSS | Auto |
| Best | Web apps | Custom | Events |

### 11. Security
- Managed identity → Key Vault
- Access restrictions (IP allowlist)
- HTTPS only, TLS 1.2+
- Private endpoints

### 12. Cost
- Free/Basic for dev
- Premium for production + slots
- Scale in at night

### 13. Common Mistakes
⚠️ Using Free tier for prod  
⚠️ No slots → downtime on deploy  
⚠️ Secrets in app settings (use Key Vault)

### 14. Interview Questions
**Beginner:** What is App Service?  
**Intermediate:** Deployment slots?  
**Advanced:** Design zero-downtime deploy with slots + traffic routing.

### 15. Revision Notes
- App Service = PaaS web hosting
- Plan = compute; App = code
- Slots = zero-downtime deploys

---

## 6.4 Azure Functions

### 1. Definition
**Serverless** compute: run code on events, pay per execution.

### 2. Why It Exists
No server management, scale to zero, event-driven.

### 3. How It Works
```
Trigger (HTTP, timer, blob, queue) → Function executes → Output binding
```

### 4. Components
- **Triggers** — HTTP, Timer, Blob, Queue, Event Hub, Cosmos
- **Bindings** — declarative input/output
- **Hosting plans** — Consumption, Premium, Dedicated (App Service), Container Apps
- **Durable Functions** — stateful workflows

### 5. Example
```bash
az functionapp create -n fn-demo -g rg-fn --consumption-plan-location eastus \
  --runtime node --functions-version 4 --storage-account mystg123
```

### 6. Use Cases
- Image resize on blob upload
- Scheduled cleanup
- API backend
- IoT telemetry processing

### 7. Terminology
| Term | Meaning |
|------|---------|
| Cold start | Delay on first invocation |
| Consumption | Pay per execution |
| Premium | Pre-warmed, VNet |
| Durable | Stateful orchestration |

### 8. Configuration
**Portal:** Create Function App → pick plan → add function.  
**IaC:** `Microsoft.Web/sites` with `kind: functionapp`.

### 9. Architecture
```
Blob upload → Event Grid → Function → Cosmos DB
```

### 10. Comparison
| | Functions | App Service | Logic Apps |
|--|-----------|-------------|------------|
| Code | Yes | Yes | No-code |
| Scale | Auto to 0 | Auto | Auto |
| Best | Events | Web apps | Workflows |

### 11. Security
- Function keys / Entra auth
- Managed identity for downstream
- VNet integration (Premium)

### 12. Cost
- Consumption: 1M free exec + 400k GB-s/month
- Premium: pre-warmed, higher cost
- Watch out for runaway loops

### 13. Common Mistakes
⚠️ Long-running functions on Consumption (5 min max)  
⚠️ No timeout handling  
⚠️ Secrets in app settings

### 14. Interview Questions
**Beginner:** What is serverless?  
**Intermediate:** Consumption vs Premium?  
**Advanced:** Design event-driven image pipeline.

### 15. Revision Notes
- Functions = event-driven serverless
- Triggers + bindings
- Consumption = scale to zero

---

## 6.5 Containers

### 1. Definition
**Container** = lightweight, portable package of app + dependencies.

### 2. Why It Exists
"Works on my machine" problem; consistency across dev/test/prod.

### 3. How It Works
```
Dockerfile → Image → Container Registry → Container instance/app
```

### 4. Components
- **Docker** — build/run
- **Azure Container Registry (ACR)** — private registry
- **Azure Container Instances (ACI)** — simplest run
- **Azure Container Apps (ACA)** — serverless containers + K8s
- **AKS** — full K8s

### 5. Example
```bash
az acr create -n myacr123 -g rg-containers --sku Basic
az acr build -r myacr123 -t myapp:v1 .
az container create -n myaci -g rg-containers --image myacr123.azurecr.io/myapp:v1 --cpu 1 --memory 1
```

### 6. Use Cases
- Microservices
- CI/CD artifacts
- Batch jobs
- Bursting

### 7. Terminology
| Term | Meaning |
|------|---------|
| Image | Read-only template |
| Container | Running instance |
| Registry | Image store |
| Pod | K8s smallest unit |

### 8. Configuration
**Portal:** Create container app → image source → ingress.  
**IaC:** `Microsoft.App/containerApps`.

### 9. Architecture
```
Dev → ACR → Container Apps → VNet → DB
```

### 10. Comparison
| | ACI | ACA | AKS |
|--|-----|-----|-----|
| K8s | No | Partial | Full |
| Scale | Manual | Auto | Auto |
| Best | Simple jobs | Microservices | Complex K8s |

### 11. Security
- Scan images (Defender for Containers)
- Non-root user
- Private ACR + managed identity

### 12. Cost
- ACI per second
- ACA per vCPU-s + requests
- AKS = node VMs + control plane (free tier available)

### 13. Common Mistakes
⚠️ Large images → slow pulls  
⚠️ Secrets in image  
⚠️ No resource limits

### 14. Interview Questions
**Beginner:** Container vs VM?  
**Intermediate:** ACI vs ACA vs AKS?  
**Advanced:** Design multi-region container platform.

### 15. Revision Notes
- Container = portable app package
- ACR = registry
- ACI/ACA/AKS = run options

---

## 6.6 Azure Kubernetes Service (AKS)

### 1. Definition
**Managed Kubernetes** — Azure manages control plane; you manage node pools.

### 2. Why It Exists
K8s is powerful but complex; AKS simplifies control plane, upgrades, integration.

### 3. How It Works
```
Control plane (Azure-managed)
   │
   ├── Node pool 1 (system)
   └── Node pool 2 (user)
        └── Pods
```

### 4. Components
- **Cluster** — control plane + nodes
- **Node pool** — group of VMs
- **Pod** — smallest deployable unit
- **Deployment** — manages pods
- **Service** — stable IP
- **Ingress** — HTTP routing
- **Namespace** — logical isolation

### 5. Example
```bash
az aks create -n aks1 -g rg-aks --node-count 2 --enable-managed-identity --generate-ssh-keys
az aks get-credentials -n aks1 -g rg-aks
kubectl get nodes
kubectl create deployment nginx --image=nginx
kubectl expose deployment nginx --port=80 --type=LoadBalancer
```

### 6. Use Cases
- Microservices at scale
- CI/CD with GitOps
- Multi-tenant platforms

### 7. Terminology
| Term | Meaning |
|------|---------|
| kubelet | Node agent |
| kubectl | CLI |
| Helm | Package manager |
| Ingress | HTTP router |
| ConfigMap/Secret | Config |

### 8. Configuration
**Portal:** Create AKS → node size/count → networking → Review.  
**IaC:** `Microsoft.ContainerService/managedClusters`.

### 9. Architecture
```
Users → App Gateway/Front Door → AKS Ingress → Services → Pods → DB
```

### 10. Comparison
| | AKS | ACA | App Service |
|--|-----|-----|-------------|
| K8s API | Yes | No | No |
| Control | Full | Medium | Low |
| Best | Complex microservices | Simple containers | Web apps |

### 11. Security
- Managed identity
- Azure Policy for AKS
- Network policies
- Private cluster
- Defender for Containers

### 12. Cost
- Control plane free (or uptime SLA tier)
- Node VMs = main cost
- Spot node pools for batch
- Cluster autoscaler

### 13. Common Mistakes
⚠️ No resource requests/limits  
⚠️ Single node pool  
⚠️ Public API server  
⚠️ No monitoring

### 14. Interview Questions
**Beginner:** What is AKS?  
**Intermediate:** Node pool vs pod?  
**Advanced:** Design multi-region AKS with GitOps.

### 15. Revision Notes
- AKS = managed K8s
- Control plane free/managed
- Node pools = VMs
- Ingress + services expose apps

---

# MODULE 7: Azure Networking

**Prerequisite:** Module 6

## 7.1 Virtual Network (VNet)

### 1. Definition
**VNet** = isolated network in Azure (like your own datacenter network).

### 2. Why It Exists
Resources need private communication, isolation, control.

### 3. How It Works
```
VNet (10.0.0.0/16)
 ├── Subnet web (10.0.1.0/24)
 ├── Subnet app (10.0.2.0/24)
 └── Subnet data (10.0.3.0/24)
```

### 4. Components
- **Address space** — CIDR
- **Subnets** — segments
- **NSG** — firewall
- **Route table** — custom routes
- **Peering** — connect VNets

### 5. Example
```bash
az network vnet create -n vnet1 -g rg-net --address-prefix 10.0.0.0/16 \
  --subnet-name web --subnet-prefix 10.0.1.0/24
```

### 6. Use Cases
- 3-tier apps
- Hybrid connectivity
- Hub-spoke topology

### 7. Terminology
| Term | Meaning |
|------|---------|
| CIDR | IP range notation |
| Peering | VNet-to-VNet |
| Hub-spoke | Central hub + spokes |
| UDR | User-defined route |

### 8. Configuration
**Portal:** Create VNet → subnets → NSG.  
**IaC:** `Microsoft.Network/virtualNetworks`.

### 9. Architecture
```
Hub VNet (firewall, VPN)
 ├── Spoke 1 (web)
 ├── Spoke 2 (app)
 └── Spoke 3 (data)
```

### 10. Comparison
| | VNet | Subnet | NSG |
|--|------|--------|-----|
| Scope | Network | Segment | Firewall |
| Contains | Subnets | Resources | Rules |

### 11. Security
- NSG on subnets
- Private endpoints
- DDoS Protection

### 12. Cost
- VNet free
- Peering egress costs
- VPN/ER costs

### 13. Common Mistakes
⚠️ Overlapping CIDRs  
⚠️ No NSG  
⚠️ Too few subnets

### 14. Interview Questions
**Beginner:** What is VNet?  
**Intermediate:** Peering vs VPN?  
**Advanced:** Design hub-spoke for 50 apps.

### 15. Revision Notes
- VNet = isolated network
- Subnets = segments
- NSG = firewall
- Peering = connect VNets

---

## 7.2 Subnets

**Definition:** Logical subdivision of VNet.  
**Why:** Isolation, NSG per tier, delegation.  
**Example:** web/app/data subnets.  
**Reserved IPs:** 5 per subnet (x.x.x.0 network, .1 gateway, .2-.3 DNS, last broadcast).

---

## 7.3 Network Security Groups (NSG)

**Definition:** Stateful firewall with allow/deny rules.  
**Priority:** 100–4096 (lower = higher priority).  
**Default rules:** Allow VNet, Allow LB, Deny all inbound.  
**Example:**
```bash
az network nsg create -n nsg-web -g rg-net
az network nsg rule create -n allow-https -g rg-net --nsg-name nsg-web \
  --priority 100 --direction Inbound --protocol Tcp --destination-port-ranges 443 --access Allow
```

---

## 7.4 Public vs Private IP

| | Public IP | Private IP |
|--|-----------|------------|
| Reachable | Internet | VNet only |
| SKU | Basic/Standard | N/A |
| Use | LB, VPN, Bastion | VMs, DB |

💡 Basic public IP has no SLA; use Standard.

---

## 7.5 DNS

- **Azure DNS** — host public zones
- **Private DNS** — internal name resolution
- **Azure-provided DNS** — 168.63.129.16

---

## 7.6 Load Balancer

**Definition:** Layer 4 (TCP/UDP) load balancer.  
**Types:** Public, Internal.  
**SKUs:** Basic, Standard, Gateway.  
**Example:**
```bash
az network lb create -n lb1 -g rg-net --sku Standard --public-ip-address pip1
```

---

## 7.7 Application Gateway

**Definition:** Layer 7 (HTTP/HTTPS) load balancer with WAF.  
**Features:** URL routing, SSL termination, WAF, cookie affinity.  
**Use:** Web apps needing path-based routing.

---

## 7.8 Azure Front Door

**Definition:** Global Layer 7 load balancer + CDN + WAF.  
**Use:** Multi-region apps, global acceleration.  
**vs App Gateway:** Front Door = global; App Gateway = regional.

---

## 7.9 VPN Gateway

**Definition:** Encrypted tunnel between on-prem and Azure.  
**Types:** Site-to-Site, Point-to-Site, VNet-to-VNet.  
**Use:** Hybrid connectivity.

---

## 7.10 ExpressRoute

**Definition:** Private dedicated connection (not internet).  
**Use:** High bandwidth, low latency, compliance.  
**vs VPN:** ER faster, more expensive, no internet.

---

## 7.11 Private Endpoint

**Definition:** Private IP for Azure PaaS (Storage, SQL).  
**Use:** Keep traffic on Microsoft backbone.  
**Example:**
```bash
az network private-endpoint create -n pe-sql -g rg-net --vnet-name vnet1 \
  --subnet data --private-connection-resource-id /subscriptions/.../servers/sql1 \
  --group-id sqlServer --connection-name sqlconn
```

---

## Module 7 Revision

**Key services:** VNet, Subnet, NSG, LB, App Gateway, Front Door, VPN, ER, Private Endpoint.  
**Comparison:**
| Service | Layer | Scope | Use |
|---------|-------|-------|-----|
| LB | 4 | Regional | TCP/UDP |
| App Gateway | 7 | Regional | HTTP + WAF |
| Front Door | 7 | Global | Multi-region + CDN |
| Traffic Manager | DNS | Global | DNS routing |

**Interview Qs:**
- LB vs App Gateway vs Front Door?
- NSG vs Firewall?
- VPN vs ExpressRoute?
- Private Endpoint vs Service Endpoint?

---

# MODULE 8: Azure Storage

**Prerequisite:** Module 7

## 8.1 Storage Accounts

### 1. Definition
Container for all Azure Storage data services.

### 2. Why It Exists
Durable, scalable, secure storage for any data type.

### 3. How It Works
```
Storage Account
 ├── Blob (objects)
 ├── File (SMB shares)
 ├── Queue (messages)
 ├── Table (NoSQL)
 └── Disk (VM disks)
```

### 4. Components
- **Performance:** Standard, Premium
- **Replication:** LRS, ZRS, GRS, GZRS, RA-GRS
- **Access tiers:** Hot, Cool, Cold, Archive

### 5. Example
```bash
az storage account create -n mystg123 -g rg-storage --sku Standard_LRS --kind StorageV2
az storage container create -n uploads --account-name mystg123
az storage blob upload -f file.txt -c uploads -n file.txt --account-name mystg123
```

### 6. Use Cases
- Static website hosting
- Backup/archive
- Data lake
- VM disks

### 7. Terminology
| Term | Meaning |
|------|---------|
| Blob | Object |
| Container | Blob folder |
| Share | File share |
| Queue | Message queue |
| Table | NoSQL key-value |

### 8. Configuration
**Portal:** Create storage account → containers → upload.  
**IaC:** `Microsoft.Storage/storageAccounts`.

### 9. Architecture
```
App → Blob (hot) → Lifecycle → Cool → Archive
```

### 10. Comparison
| | Blob | File | Queue | Table |
|--|------|------|-------|-------|
| Type | Object | SMB | Message | NoSQL |
| Use | Files, media | Lift-shift | Async | Key-value |

### 11. Security
- SAS tokens
- Managed identity
- Private endpoints
- Encryption at rest (always)

### 12. Cost
- Hot > Cool > Cold > Archive (storage cost)
- Archive retrieval expensive
- Lifecycle policies

### 13. Common Mistakes
⚠️ Public blob access  
⚠️ No lifecycle policy  
⚠️ Using LRS for critical data

### 14. Interview Questions
**Beginner:** What is Blob storage?  
**Intermediate:** LRS vs GRS?  
**Advanced:** Design cost-optimized data lake.

### 15. Revision Notes
- Storage account = container for all storage
- Blob = object; File = SMB; Queue = messages; Table = NoSQL
- Redundancy: LRS→ZRS→GRS→GZRS
- Lifecycle: Hot→Cool→Cold→Archive

---

# MODULE 9: Azure Databases

**Prerequisite:** Module 8

## 9.1 Azure SQL Database

**Definition:** Managed SQL Server (PaaS).  
**Why:** No patching, built-in HA, backup.  
**Editions:** Basic, Standard, Premium, Hyperscale, Serverless.  
**Example:**
```bash
az sql server create -n sqlsrv123 -g rg-db --admin-user sqladmin --admin-password 'P@ssw0rd1234'
az sql db create -n db1 -g rg-db --server sqlsrv123 --service-objective S1
```

## 9.2 Cosmos DB

**Definition:** Globally distributed NoSQL (multi-model).  
**APIs:** SQL, MongoDB, Cassandra, Gremlin, Table.  
**Consistency:** Strong, Bounded Staleness, Session, Consistent Prefix, Eventual.  
**Use:** Global apps, low latency.

## 9.3 PostgreSQL / MySQL

**Definition:** Managed open-source DBs.  
**Options:** Single Server (legacy), Flexible Server (recommended).  
**Use:** LAMP, Django, Rails.

## 9.4 Comparison

| | Azure SQL | Cosmos DB | PostgreSQL |
|--|-----------|-----------|------------|
| Type | Relational | NoSQL | Relational |
| Scale | Vertical | Horizontal | Vertical |
| Global | Geo-replica | Multi-master | Read replicas |
| Best | OLTP | Global NoSQL | Open-source |

## Module 9 Revision

- Azure SQL = managed SQL Server
- Cosmos = global NoSQL
- PostgreSQL/MySQL = managed open-source
- Choose based on data model, scale, consistency

---

# MODULE 10: Azure Identity and Security

**Prerequisite:** Module 3

## 10.1 Microsoft Entra ID

**Definition:** Cloud identity provider (formerly Azure AD).  
**Features:** Users, groups, apps, SSO, MFA, Conditional Access.

## 10.2 RBAC

**Definition:** Role-Based Access Control.  
**Components:** Security principal + Role definition + Scope.  
**Built-in roles:** Owner, Contributor, Reader, User Access Administrator.  
**Example:**
```bash
az role assignment create --assignee user@contoso.com --role Reader --scope /subscriptions/<sub-id>
```

## 10.3 Managed Identity

**Definition:** Auto-managed identity for Azure resources.  
**Types:** System-assigned, User-assigned.  
**Use:** App Service → Key Vault without secrets.

## 10.4 Key Vault

**Definition:** Secrets, keys, certificates store.  
**Use:** Centralize secrets, audit access.

## 10.5 MFA & Conditional Access

**MFA:** Something you know + have.  
**Conditional Access:** If user/location/device → then require MFA/block.

## 10.6 Zero Trust

**Principle:** Never trust, always verify.  
**Pillars:** Identity, devices, apps, data, network, infrastructure.

## Module 10 Revision

- Entra ID = identity
- RBAC = authorization
- Managed identity = secretless auth
- Key Vault = secrets
- Zero Trust = verify explicitly, least privilege, assume breach

---

# MODULE 11: Azure Monitoring and Management

**Prerequisite:** Module 6

## 11.1 Azure Monitor

**Definition:** Central monitoring platform.  
**Components:** Metrics, Logs, Alerts, Dashboards, Workbooks.

## 11.2 Log Analytics

**Definition:** Store + query logs (KQL).  
**Example:**
```kusto
AzureActivity
| where OperationNameValue contains "delete"
| project TimeGenerated, Caller, ResourceGroup
```

## 11.3 Application Insights

**Definition:** APM for apps.  
**Features:** Request rates, failures, dependencies, live metrics.

## 11.4 Alerts

**Types:** Metric, Log, Activity log.  
**Actions:** Email, SMS, webhook, Logic App, Function.

## Module 11 Revision

- Monitor = metrics + logs + alerts
- Log Analytics = KQL queries
- App Insights = app performance
- Alerts = proactive notification

---

# MODULE 12: Azure Governance

**Prerequisite:** Module 3

## 12.1 Policies

**Definition:** Rules enforced on resources.  
**Example:** Require tag `env`, allowed regions.

## 12.2 Tags

**Definition:** Key/value metadata.  
**Use:** Cost tracking, automation.

## 12.3 Locks

**Types:** CanNotDelete, ReadOnly.  
**Use:** Protect critical resources.

## 12.4 Management Groups

**Definition:** Hierarchy above subscriptions.  
**Use:** Apply policy/RBAC at scale.

## 12.5 Cost Management

**Features:** Budgets, cost analysis, recommendations, exports.

## Module 12 Revision

- Policy = enforce rules
- Tags = metadata
- Locks = prevent changes
- MG = scale governance
- Cost Management = budgets + analysis

---

# MODULE 13: Infrastructure as Code

**Prerequisite:** Module 5

## 13.1 ARM Templates
JSON declarative templates.

## 13.2 Bicep
DSL → ARM JSON. Cleaner syntax.

## 13.3 Terraform
HCL, multi-cloud, state file.

## Comparison

| | ARM | Bicep | Terraform |
|--|-----|-------|-----------|
| Syntax | JSON | DSL | HCL |
| State | Azure | Azure | You manage |
| Multi-cloud | No | No | Yes |
| Learning | Hard | Easy | Medium |

## Module 13 Revision

- IaC = declarative infra
- Bicep = preferred Azure-native
- Terraform = multi-cloud
- Always use what-if/plan

---

# MODULE 14: Azure DevOps and CI/CD

**Prerequisite:** Module 13

## 14.1 Repositories
Git repos in Azure DevOps.

## 14.2 Pipelines
YAML or classic. Build + release.

## 14.3 Build
Compile, test, package.

## 14.4 Release
Deploy to environments.

## 14.5 Deployment Strategies

| Strategy | Description |
|----------|-------------|
| Rolling | Gradual replace |
| Blue-Green | Two environments, swap |
| Canary | Small % first |
| Ring | Staged rollout |

## Module 14 Revision

- Azure DevOps = repos + pipelines + boards + artifacts
- CI = build/test
- CD = deploy
- Strategies: rolling, blue-green, canary

---

# MODULE 15: Azure Containers and Kubernetes (Deep Dive)

Already covered in 6.5/6.6. Additional:
- **GitOps** with Flux/ArgoCD
- **Service Mesh** (Istio, Linkerd)
- **Ingress** (NGINX, App Gateway Ingress)
- **Storage** (Azure Disk, Azure Files)
- **Networking** (CNI, kubenet)

---

# MODULE 16: Azure Serverless Architecture

**Prerequisite:** Module 6.4

## Components
- Functions
- Logic Apps
- Event Grid
- Service Bus
- Event Hubs
- Durable Functions
- API Management

## Architecture
```
HTTP → API Management → Function → Cosmos DB
Event → Event Grid → Function → Queue → Function
```

## Module 16 Revision

- Serverless = no server management
- Functions = code
- Logic Apps = workflow
- Event Grid = reactive events
- Service Bus = enterprise messaging

---

# MODULE 17: Azure Backup and Disaster Recovery

**Prerequisite:** Module 8

## 17.1 Azure Backup
Backup VMs, files, SQL, SAP.

## 17.2 Azure Site Recovery (ASR)
Replicate VMs to another region.

## 17.3 RTO/RPO

| Term | Meaning |
|------|---------|
| RTO | Recovery Time Objective |
| RPO | Recovery Point Objective |

## Module 17 Revision

- Backup = data protection
- ASR = DR orchestration
- RTO = max downtime
- RPO = max data loss

---

# MODULE 18: High Availability and Scalability

**Prerequisite:** Module 4

## Concepts
- **HA** = minimize downtime
- **Scalability** = handle growth
- **Elasticity** = auto scale
- **Fault tolerance** = survive failure

## Patterns
- Load balancing
- Replication
- Auto-scaling
- Health probes
- Circuit breaker
- Retry
- Queue-based load leveling

## Module 18 Revision

- HA = uptime
- DR = recovery
- Scale up = vertical
- Scale out = horizontal
- Elasticity = auto

---

# MODULE 19: Azure Architecture Design

**Prerequisite:** All previous

## Pillars (Azure Well-Architected Framework)
1. Reliability
2. Security
3. Cost Optimization
4. Operational Excellence
5. Performance Efficiency

## Design Patterns
- N-tier
- Microservices
- Event-driven
- Big data
- Serverless

## Module 19 Revision

- WAF 5 pillars
- Design for failure
- Decouple components
- Automate everything

---

# MODULE 20: Azure AI and Machine Learning

**Prerequisite:** Module 6

## Services
- **Azure Machine Learning** — train/deploy models
- **Cognitive Services** — prebuilt AI (vision, speech, language)
- **Azure OpenAI** — GPT models
- **Bot Service** — chatbots
- **Form Recognizer** — document AI

## Module 20 Revision

- Azure ML = custom models
- Cognitive Services = prebuilt
- OpenAI = GPT
- Use case: chatbot, OCR, recommendations

---

# MODULE 21: Azure Data and Analytics

**Prerequisite:** Module 8

## Services
- **Azure Data Factory** — ETL
- **Synapse Analytics** — data warehouse
- **Databricks** — Spark
- **HDInsight** — Hadoop
- **Data Lake Storage** — big data
- **Stream Analytics** — real-time

## Module 21 Revision

- ADF = orchestration
- Synapse = warehouse + big data
- Databricks = Spark
- Stream Analytics = IoT/real-time

---

# MODULE 22: Azure Integration and Messaging

**Prerequisite:** Module 16

## 22.1 Service Bus
Enterprise messaging: queues, topics, sessions, dead-letter.

## 22.2 Event Grid
Reactive event routing (blob created, resource changed).

## 22.3 Event Hubs
Big data streaming (millions/sec).

## Comparison

| | Service Bus | Event Grid | Event Hubs |
|--|-------------|------------|------------|
| Type | Message broker | Event router | Event stream |
| Scale | Medium | High | Very high |
| Use | Orders, workflows | Reactive | Telemetry |

## Module 22 Revision

- Service Bus = reliable messaging
- Event Grid = reactive events
- Event Hubs = streaming

---

# MODULE 23: Azure Security Architecture

**Prerequisite:** Module 10

## Layers
- Identity (Entra ID)
- Network (NSG, Firewall, DDoS)
- Compute (Defender, patching)
- Data (encryption, Key Vault)
- Governance (Policy, Blueprints)
- Monitoring (Sentinel, Defender)

## Microsoft Defender for Cloud
CSPM + CWPP.

## Microsoft Sentinel
SIEM + SOAR.

## Module 23 Revision

- Defense in depth
- Zero Trust
- Defender for Cloud = posture
- Sentinel = SIEM

---

# MODULE 24: Azure Cost Optimization

**Prerequisite:** Module 12

## Strategies
- Right-sizing
- Reserved instances
- Spot VMs
- Auto-scaling
- Lifecycle policies
- Hybrid Benefit
- Budgets + alerts

## Module 24 Revision

- Pay only for what you use
- Reserved = 1–3 yr discount
- Spot = cheap, evictable
- Hybrid Benefit = use existing licenses

---

# MODULE 25: Real-World Azure Architectures

## 25.1 3-Tier Web App
```
Users → Front Door → App Gateway → App Service → SQL DB
                                      │
                                   Redis Cache
```

## 25.2 Microservices on AKS
```
Users → Front Door → App Gateway → AKS Ingress → Services → Cosmos DB
```

## 25.3 Serverless Event Pipeline
```
Blob → Event Grid → Function → Cosmos DB
```

## 25.4 Hybrid
```
On-prem → VPN/ExpressRoute → Azure VNet → VMs + SQL
```

---

# MODULE 26: Azure Interview Preparation

## Beginner Questions
1. What is Azure?
2. What is a resource group?
3. What is a VNet?
4. What is Blob storage?
5. What is RBAC?

## Intermediate Questions
1. VM vs App Service vs Functions?
2. NSG vs Firewall?
3. LRS vs GRS?
4. Managed identity vs service principal?
5. Deployment slots?

## Advanced Questions
1. Design multi-region active-active.
2. Design hub-spoke network.
3. Design zero-downtime deployment.
4. Design cost-optimized data platform.
5. Design secure hybrid architecture.

## Scenario Questions
- App slow in Europe → Front Door + regional deploy
- Data must stay in EU → region selection + policy
- 10,000 req/sec → AKS + Cosmos DB + Event Hubs

---

# MODULE 27: Azure Certification Roadmap

| Level | Certification | Focus |
|-------|--------------|-------|
| Beginner | AZ-900 | Fundamentals |
| Associate | AZ-104 | Administrator |
| Associate | AZ-204 | Developer |
| Associate | AZ-500 | Security |
| Associate | AI-900 | AI Fundamentals |
| Associate | DP-900 | Data Fundamentals |
| Expert | AZ-305 | Solutions Architect |
| Expert | AZ-400 | DevOps Engineer |
| Expert | AZ-500 | Security Engineer |

**Path:** AZ-900 → AZ-104 → AZ-204/AZ-500 → AZ-305/AZ-400.

---

# Learning Projects

## Project 1: Static Website Hosting

**Objective:** Host a static site on Azure Storage.  
**Architecture:**
```
Users → Storage Static Website ($web container) → CDN (optional)
```
**Services:** Storage Account, CDN (optional), Custom Domain.  
**Steps:**
```bash
az storage account create -n mystatic123 -g rg-static --sku Standard_LRS --kind StorageV2
az storage blob service-properties update --account-name mystatic123 --static-website --index-document index.html
az storage blob upload-batch -d '$web' -s ./site --account-name mystatic123
```
**Security:** HTTPS only, no public container.  
**Cost:** Pennies/month.  
**Testing:** Browse static website URL.  
**Troubleshooting:** 404 → check index document.  
**Learned:** Blob, static website, CDN.  
**Advanced:** Add Front Door + WAF.

---

## Project 2: Web App Deployment

**Objective:** Deploy Node.js app to App Service.  
**Architecture:**
```
Users → App Service → SQL DB
```
**Services:** App Service, SQL DB, Key Vault.  
**Steps:**
```bash
az appservice plan create -n plan1 -g rg-web --sku B1 --is-linux
az webapp create -n myapp123 -g rg-web -p plan1 --runtime "NODE:18-lts"
az webapp deployment source config-zip -n myapp123 -g rg-web --src app.zip
```
**Security:** Managed identity → Key Vault.  
**Cost:** B1 ~$13/mo.  
**Testing:** Browse URL.  
**Learned:** PaaS deploy, connection strings.  
**Advanced:** Slots + auto-scale.

---

## Project 3: 3-Tier Application

**Objective:** Web + API + DB with private networking.  
**Architecture:**
```
Front Door → App Gateway → Web VMSS → API VMSS → SQL (private endpoint)
```
**Services:** VNet, VMSS, App Gateway, SQL, Key Vault, Monitor.  
**Steps:** Create VNet + subnets → NSGs → VMSS → App Gateway → SQL private endpoint.  
**Security:** NSG per tier, private endpoints, WAF.  
**Cost:** ~$200/mo.  
**Testing:** Load test with Apache JMeter.  
**Learned:** Networking, tiers, security.  
**Advanced:** Multi-region.

---

## Project 4: Serverless Application

**Objective:** Image resize on upload.  
**Architecture:**
```
Blob upload → Event Grid → Function → Blob (resized)
```
**Services:** Storage, Event Grid, Functions, App Insights.  
**Steps:**
```bash
az functionapp create -n fn-img -g rg-fn --consumption-plan-location eastus --runtime node --functions-version 4 --storage-account mystg123
```
Deploy function code.  
**Security:** Managed identity, private endpoint.  
**Cost:** Free tier.  
**Testing:** Upload image → check resized container.  
**Learned:** Event-driven, bindings.  
**Advanced:** Add CDN + OCR.

---

## Project 5: Containerized Application

**Objective:** Deploy container to AKS.  
**Architecture:**
```
Users → App Gateway → AKS Ingress → Pods → Cosmos DB
```
**Services:** ACR, AKS, Cosmos DB, Key Vault.  
**Steps:**
```bash
az acr create -n myacr123 -g rg-aks --sku Basic
az acr build -r myacr123 -t myapp:v1 .
az aks create -n aks1 -g rg-aks --node-count 2 --attach-acr myacr123
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```
**Security:** Private cluster, network policies.  
**Cost:** ~$150/mo.  
**Testing:** curl service IP.  
**Learned:** Containers, K8s, ACR.  
**Advanced:** GitOps + multi-region.

---

## Project 6: CI/CD Deployment

**Objective:** GitHub → Azure DevOps → App Service.  
**Architecture:**
```
GitHub → Azure Pipelines → Build → Deploy → App Service
```
**Services:** Azure DevOps, App Service, Key Vault.  
**Steps:** Create pipeline YAML → connect repo → build → deploy.  
**Security:** Service connection with managed identity.  
**Cost:** Free tier for DevOps.  
**Testing:** Push commit → auto-deploy.  
**Learned:** CI/CD, YAML, slots.  
**Advanced:** Canary + feature flags.

---

## Project 7: Secure Production Architecture

**Objective:** Zero Trust production landing zone.  
**Architecture:**
```
Entra ID → Conditional Access → Front Door (WAF) → App Gateway → Private AKS → Private SQL
```
**Services:** Entra ID, Front Door, App Gateway, AKS, SQL, Key Vault, Defender, Sentinel.  
**Steps:** Landing zone → hub-spoke → private endpoints → policies → monitoring.  
**Security:** Zero Trust, PIM, JIT, private endpoints.  
**Cost:** High (~$1000+/mo).  
**Testing:** Pen test, policy compliance.  
**Learned:** Enterprise security.  
**Advanced:** Multi-region + DR.

---

## Project 8: Highly Available Application

**Objective:** 99.99% SLA app.  
**Architecture:**
```
Front Door → App Gateway (zone-redundant) → VMSS (3 AZs) → SQL (zone-redundant) → GRS storage
```
**Services:** Front Door, App Gateway, VMSS, SQL, Storage.  
**Steps:** Deploy in 3 AZs → zone-redundant services → health probes → auto-scale.  
**Security:** WAF, NSG, encryption.  
**Cost:** High.  
**Testing:** Chaos testing (kill VM).  
**Learned:** HA, AZ, health probes.  
**Advanced:** Multi-region active-active.

---

## Project 9: Monitoring and Logging System

**Objective:** Central observability.  
**Architecture:**
```
App → App Insights → Log Analytics → Alerts → Action Groups → Teams/Email
```
**Services:** Monitor, App Insights, Log Analytics, Alerts.  
**Steps:** Enable App Insights → create workspace → alerts → dashboards.  
**Security:** RBAC on workspace.  
**Cost:** Pay per GB ingested.  
**Testing:** Trigger alert.  
**Learned:** KQL, alerts, dashboards.  
**Advanced:** Sentinel + workbooks.

---

## Project 10: Advanced Cloud Architecture

**Objective:** Global multi-region SaaS.  
**Architecture:**
```
Front Door → Regional App Gateway → AKS → Cosmos DB (multi-master) → Event Hubs → Data Lake
```
**Services:** Front Door, AKS, Cosmos DB, Event Hubs, Data Lake, Synapse, DevOps.  
**Steps:** Deploy in 3 regions → global DB → event streaming → analytics.  
**Security:** Zero Trust, private endpoints, WAF.  
**Cost:** Very high.  
**Testing:** Global load test.  
**Learned:** Global scale, data consistency.  
**Advanced:** AI/ML integration.

---

# Complete Azure Roadmap

## Beginner (Weeks 1–4)
- Cloud fundamentals
- Azure fundamentals
- Portal, CLI, subscriptions, RGs
- Regions, AZs
- Compute: VM, App Service
- Storage: Blob
- Identity: Entra ID basics
- **Cert:** AZ-900

## Intermediate (Weeks 5–12)
- Networking: VNet, NSG, LB, App Gateway
- Databases: SQL, Cosmos
- Functions, Containers
- Monitoring
- Governance
- IaC: Bicep
- DevOps
- **Cert:** AZ-104

## Advanced (Weeks 13–24)
- AKS deep dive
- Security architecture
- HA/DR
- Serverless patterns
- Integration: Service Bus, Event Grid, Event Hubs
- Data: Synapse, Databricks
- AI: Azure ML, OpenAI
- Architecture design
- **Cert:** AZ-305, AZ-400, AZ-500

## Must-Learn
- VNet, NSG, LB
- VM, App Service, Functions
- Storage, SQL, Cosmos
- Entra ID, RBAC, Key Vault
- Monitor
- Bicep
- DevOps

## Good-to-Know
- AKS
- Event Grid/Hubs
- Logic Apps
- API Management
- Front Door

## Advanced
- ExpressRoute
- Sentinel
- Synapse
- Azure ML
- Multi-region design

## Real-World Job Topics
- Landing zones
- Hub-spoke
- CI/CD
- IaC
- Security
- Cost optimization

## Certification Prep
- AZ-900 → AZ-104 → AZ-204/AZ-500 → AZ-305/AZ-400

---

# Final Notes

- **Azure changes fast** — always check Microsoft Learn for latest SKUs, limits, prices.
- **Practice** — create free account, do labs.
- **Document** — keep your own notes.
- **Build projects** — portfolio > certificates.
- **Interview prep** — focus on scenarios, not memorization.

**You now have a complete Azure curriculum. Start with Module 1, do the labs, and progress sequentially. Good luck!**
