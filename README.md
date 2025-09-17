# 🌐 -AWS-public-subnet-route-table-security-group-and-network-ACL-Hands-On-Lab

This project guides you through creating a secure VPC on AWS with a public subnet, route table, security group, and network ACL. By the end, your VPC will be ready to host EC2 instances for web applications! 🖥️☁️

This project assumes that you have done the [previous project](https://github.com/1suleyman/-AWS-VPC-Subnet-and-Internet-Gateway-Hands-On-Lab-/tree/main) in the networking series where the VPC and subnet had already been created

part 2 in the networking series

---

## 📋 Project Steps

### Step 1: Add a Route Table and Security Group

**Goal:** Configure traffic flow and basic security for your subnet.

**Instructions:**

#### Route Table

1. Navigate to **Route Tables** > **Create route table**.
2. Name it `Networking series part 2` Route Table` and attach to `Suleyman VPC`.
3. Select the route table, then go to **Subnet associations**.
4. Associate it with your **Public 1 subnet**.

<img width="359" height="38" alt="Screenshot 2025-09-17 at 15 09 04" src="https://github.com/user-attachments/assets/ce68bce5-c093-4672-9326-940de3f75c6e" />

💡 **Tip:** The route table directs traffic inside and outside your VPC.

#### Security Group

1. Navigate to **Security Groups** > **Create security group**.
2. Name it `Networking series part 2 Security Group`, attach to `Suleyman VPC`.
3. Add a description `A Security Group for the Suleyman VPC`
4. Add an **Inbound rule**:

   * Type: HTTP
   * Protocol: TCP
   * Port: 80
   * Source: 0.0.0.0/0

<img width="1239" height="218" alt="Screenshot 2025-09-17 at 15 12 27" src="https://github.com/user-attachments/assets/462888b7-7959-4a85-9890-6b09e7440163" />

5. Add an **Outbound rule**:

   * Type: All traffic
   * Destination: 0.0.0.0/0

<img width="1232" height="211" alt="Screenshot 2025-09-17 at 15 12 47" src="https://github.com/user-attachments/assets/4c006d37-64ef-4b98-8397-44f73dc7395f" />

💡 **Tip:** Security groups act as virtual firewalls for EC2 instances.

✅ **Checkpoint:** Route table and security group configured!

<img width="447" height="35" alt="Screenshot 2025-09-17 at 15 15 01" src="https://github.com/user-attachments/assets/3c13b354-0fa4-477b-b402-e3cbe005881f" />

---

### Step 2: Create a Network ACL

**Goal:** Add a second layer of security at the subnet level.

**Instructions:**

1. Navigate to **Network ACLs** > **Create network ACL**.
2. Name it `Networking series part 2 ACL` and attach to `Suleyman VPC`.

<img width="215" height="37" alt="Screenshot 2025-09-17 at 15 19 36" src="https://github.com/user-attachments/assets/ac5c86bf-79f1-4e4e-a9cc-5ffb7a2de8ac" />

4. Select the new ACL and go to **Inbound rules** > **Edit inbound rules** > **Add rule**:

   * Rule number: 100
   * Type: All traffic
   * Source: 0.0.0.0/0
   
<img width="1017" height="178" alt="Screenshot 2025-09-17 at 15 21 47" src="https://github.com/user-attachments/assets/b1497c1c-e191-4ddb-bcdd-e29229bf56d7" />

5. Repeat for **Outbound rules**:

   * Rule number: 100
   * Type: All traffic
   * Destination: 0.0.0.0/0

<img width="1015" height="176" alt="Screenshot 2025-09-17 at 15 22 28" src="https://github.com/user-attachments/assets/246991ff-addf-4e81-9242-71f35fd27939" />

6. Go to **Subnet associations** > **Edit subnet associations**.
7. Select your **Public 1 subnet** and save.

<img width="419" height="62" alt="Screenshot 2025-09-17 at 15 22 47" src="https://github.com/user-attachments/assets/6a7b01e9-db55-4876-912c-4a298f4a77d6" />

💡 **Tip:**

* **Network ACLs** act like traffic cops for subnets.
* **Security groups** protect individual resources; ACLs protect subnets.
* Both together provide layered security.

✅ **Checkpoint:** Network ACL created and associated with Public 1 subnet.

---

## 📌 Project Summary

| Step                             | Status | Key Notes                                            |
| -------------------------------- | ------ | ---------------------------------------------------- |
| Create VPC                       | ✅      | CIDR block 10.0.0.0/16                               |
| Create Public Subnet             | ✅      | CIDR block 10.0.1.0/24                               |
| Add Route Table & Security Group | ✅      | HTTP allowed; all outbound traffic allowed           |
| Create Network ACL               | ✅      | Inbound & outbound allow all; associated with subnet |

---

## 📸 Screenshots

Include screenshots at each checkpoint for reference:

* VPC created
* Public subnet created
* Route table associated with subnet
* Security group rules
* Network ACL inbound/outbound rules and subnet association

---

## 💡 Notes / Tips

* **Route Tables:** Direct traffic inside your VPC.
* **Security Groups vs. ACLs:** Security groups = resource-level; ACLs = subnet-level.
* **Subnet Associations:** ACL rules only work when associated with a subnet.
* **Testing:** Launch an EC2 instance in Public 1 subnet and try accessing it via HTTP to test your setup.

---

## ✅ References

* [Amazon VPC Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
* [Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
* [Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
