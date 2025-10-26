# task-3
# 🌩️ Task 3 — Create and Configure a Virtual Private Cloud (VPC) with Subnets

## 🎯 Objective
To understand how secure networking works in cloud environments by creating a **Virtual Private Cloud (VPC)** with **public and private subnets**, enabling controlled internet access using route tables and an Internet Gateway.

---

## ✅ Deliverables
- 📌 Screenshot of **VPC + Subnets** page
- 📌 Screenshot of **Route Table configuration**
- 📌 Short description containing:
  - VPC CIDR
  - Subnet CIDRs
  - Region
  - Internet access status (enabled/disabled)

---

## 🛠️ Tools Used
| Tool | Purpose |
|--------|---------|
| **AWS Free Tier** | VPC, Subnets, Routing & Internet Gateway |
| **EC2 (Optional for testing)** | To test public vs private connectivity |

---

## 🧭 Step-by-Step Guide

### **1️⃣ Create VPC**
1. Open AWS Console → Go to **VPC Dashboard**
2. Click **Create VPC**
3. Enter:
   - **Name:** `intern-vpc`
   - **IPv4 CIDR:** `10.0.0.0/16`
4. Click **Create VPC**

---

### **2️⃣ Create Subnets**

#### ✅ Public Subnet
1. VPC → Subnets → **Create subnet**
2. Choose **VPC:** `intern-vpc`
3. **Name:** `public-subnet-1`
4. **CIDR:** `10.0.1.0/24`
5. Enable **Auto-assign Public IPv4**

#### ✅ Private Subnet
1. Again click **Create subnet**
2. **Name:** `private-subnet-1`
3. **CIDR:** `10.0.2.0/24`
4. **Disable Public IPv4 Assignment**

---

### **3️⃣ Create and Attach Internet Gateway**
1. Go to **Internet Gateways**
2. Click **Create Internet Gateway**
3. **Name:** `intern-igw`
4. Click **Attach to VPC** → select `intern-vpc`

---

### **4️⃣ Configure Route Tables**

#### ✅ Public Route Table
1. Go to **Route Tables** → Create
2. **Name:** `public-rt` → VPC: `intern-vpc`
3. Edit routes → Add route:
   - **Destination:** `0.0.0.0/0`
   - **Target:** Internet Gateway (`intern-igw`)
4. Associate this Route Table with `public-subnet-1`

#### ✅ Private Route Table
1. Create another Route Table as `private-rt`
2. **Do NOT add any internet route**
3. Associate it with `private-subnet-1`

---

## ✅ Verification Checklist
| Item | Expected Result |
|---------|---------------|
| Public Subnet | Has internet (via IGW + public RT) |
| Private Subnet | No internet access |
| Route Tables | Public RT has `0.0.0.0/0 → IGW`, Private RT does not |

---

## 📝 Example Summary (for screenshot submission)
