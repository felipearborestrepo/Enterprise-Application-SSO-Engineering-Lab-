# 🔐 Enterprise Application & SSO Engineering Lab  
**Microsoft Entra ID | Application Access Control | Conditional Access | Zero Trust IAM**

<img width="1536" height="1024" alt="ChatGPT Image Jan 20, 2026, 11_50_34 AM" src="https://github.com/user-attachments/assets/9ec8054a-b590-4ab7-859a-5370102eae78" />

---

## 📘 Project Overview

This project demonstrates real-world Identity & Access Management (IAM) engineering by onboarding an enterprise application into Microsoft Entra ID and enforcing secure, role-based access using Conditional Access and group-based authorization.

The lab simulates how organizations integrate internal business applications (e.g., HR systems, finance portals, SaaS platforms) and restrict access based on job function, applying Zero Trust principles and MFA enforcement.

---

## 🎯 Objectives

- Onboard an enterprise application into Microsoft Entra ID  
- Configure OpenID Connect (OIDC) single sign-on  
- Enforce group-based application access  
- Apply Conditional Access per application  
- Require MFA for authorized users  
- Prevent unauthorized users from accessing the application  
- Validate access enforcement through sign-in logs  

---

## 🏗️ Environment

- Platform: Microsoft Entra ID  
- App Type: Enterprise Application (OIDC)  
- Access Model: Group-based authorization  
- Security Controls: Conditional Access, MFA  
- Monitoring: Entra Sign-in Logs  

---

## 🧱 Architecture (Logical)

Microsoft Entra ID  
→ App Registration  
→ Enterprise Application  
→ Security Groups  
→ Conditional Access (Per-App)  
→ Sign-in Logs  

The integrated enterprise application (`ENT-HR-Portal`) is protected so only HR users can authenticate. IT users and guest users are intentionally not assigned, enforcing least-privilege access.

---

## 🧪 Implementation Phases

---

# 🔹 PHASE 1 — Identity & Group Foundation

### Step 1 — Create enterprise security groups

Path:  
`Microsoft Entra ID → Groups → New group`

Created:

- ENT-App-HR-Users  
- ENT-App-IT-Admins  
- ENT-App-Guests  

📸 Evidence:  

<img width="1357" height="606" alt="1" src="https://github.com/user-attachments/assets/a3f9029f-0e8c-4c17-b66a-374f91aec429" />

---

### Step 2 — Create test identities

Created cloud-only users representing business roles:

- HR user  
- IT user  
- Guest user (B2B)  

Assigned users to their corresponding groups.

📸 Evidence:  

<img width="1091" height="557" alt="1(2)" src="https://github.com/user-attachments/assets/936853b5-7527-4de5-a7da-67f20e7c8da1" />

---

# 🔹 PHASE 2 — Application Onboarding

### Step 3 — Register the application

Path:  
`Microsoft Entra ID → App registrations → New registration`

Application name:  
`ENT-HR-Portal`

📸 Evidence:  

<img width="546" height="216" alt="2" src="https://github.com/user-attachments/assets/13f21929-42f7-41df-bd9e-6abe5a51a698" />

<img width="815" height="455" alt="3" src="https://github.com/user-attachments/assets/73af1507-d63b-4db9-b96e-3fbff76cf41e" />

<img width="953" height="318" alt="4" src="https://github.com/user-attachments/assets/a2a94faa-c124-4ffc-97bb-07b4b066a42c" />

<img width="1088" height="265" alt="5" src="https://github.com/user-attachments/assets/a34b3cea-f045-40df-8038-a6711382d15c" />

---

### Step 4 — Enterprise application verification

Confirmed service principal creation.

Path:  
`Microsoft Entra ID → Enterprise applications → ENT-HR-Portal`

📸 Evidence:  

<img width="1099" height="471" alt="6" src="https://github.com/user-attachments/assets/f56f09a5-da6e-4a04-b353-a271069beb5b" />

<img width="1090" height="568" alt="7" src="https://github.com/user-attachments/assets/76bf0453-38bd-49c0-9f01-451afa08f91b" />

---

# 🔹 PHASE 3 — Authorization & App Security

### Step 5 — Enforce assignment requirement

Path:  
`Enterprise application → Properties`

- Assignment required → YES  
- Visible to users → YES  

📸 Evidence:  

<img width="805" height="545" alt="8" src="https://github.com/user-attachments/assets/1e2c14f8-3cb1-4a39-a9bc-4d1018486436" />

<img width="1090" height="561" alt="9" src="https://github.com/user-attachments/assets/5ef6e120-926a-40c9-b302-f5c712f8ca32" />

<img width="1085" height="563" alt="10" src="https://github.com/user-attachments/assets/daffd721-5284-4789-9210-4426d31be395" />

---

### Step 6 — Group-based application access

Path:  
`Enterprise application → Users and groups → Add user/group`

Assigned:

- ENT-App-HR-Users  

📸 Evidence:  

<img width="537" height="381" alt="11" src="https://github.com/user-attachments/assets/fc4ba3f7-96f1-4036-a75f-0d5f2ddf759a" />

<img width="990" height="548" alt="12" src="https://github.com/user-attachments/assets/09163491-34c4-459b-964f-a415b9bd4d7d" />

---

# 🔹 PHASE 4 — Conditional Access Enforcement

### Step 7 — Per-application MFA policy

Path:  
`Microsoft Entra ID → Protection → Conditional Access → New policy`

Policy:

`CA-ENT-HR-Portal-MFA`

Configuration:

- Users: ENT-App-HR-Users  
- Cloud apps: ENT-HR-Portal  
- Grant: Require multi-factor authentication  

📸 Evidence:  

<img width="917" height="192" alt="13" src="https://github.com/user-attachments/assets/87ceb221-c5ae-4085-a0df-074946f57167" />

<img width="1110" height="579" alt="14" src="https://github.com/user-attachments/assets/377560d1-0ac0-4f5d-b040-051c43f0ad8e" />

<img width="780" height="508" alt="15" src="https://github.com/user-attachments/assets/ef77a4f2-c9bd-490d-81b6-e27288ecfa05" />

<img width="1102" height="614" alt="16" src="https://github.com/user-attachments/assets/54204a74-05dd-40ce-8ee3-2850a1016cd5" />

<img width="1078" height="235" alt="17" src="https://github.com/user-attachments/assets/dbde0dd1-8880-480a-8269-b2096c09092f" />

---

# 🔹 PHASE 5 — Validation & Testing

Testing was performed using the Microsoft My Apps portal.

Path:  
`https://myapps.microsoft.com`

Results:

- HR user could access the enterprise application and was prompted for MFA.  
- IT and guest users could authenticate but did not see or have access to the ENT-HR-Portal application.

📸 Evidence:  

<img width="502" height="391" alt="18" src="https://github.com/user-attachments/assets/5a6c31b9-4173-4f59-814c-58da4f6d35b2" />

<img width="506" height="397" alt="19" src="https://github.com/user-attachments/assets/73a8bf55-9c25-47e1-9b88-57299a2f11fa" />

<img width="1360" height="602" alt="20" src="https://github.com/user-attachments/assets/54c0dda1-92cf-4d48-acb9-c63b04703260" />

<img width="1387" height="601" alt="21" src="https://github.com/user-attachments/assets/a351f066-83b2-4c7f-953a-7ff15acedbf7" />

---

# 🔹 PHASE 6 — IAM Operational Evidence

### Authorized sign-in log analysis

Path:  
`Microsoft Entra ID → Monitoring → Sign-in logs`

Reviewed HR authentication event:

- Application: ENT-HR-Portal  
- Conditional Access policy applied  
- MFA enforced  
- Authentication details confirmed  

📸 Evidence:  

<img width="910" height="391" alt="22" src="https://github.com/user-attachments/assets/05c3f122-29e4-4131-b58a-6c0b142194fe" />

<img width="1102" height="561" alt="23" src="https://github.com/user-attachments/assets/601f9136-f613-4b70-b9aa-1de44fb39c0b" />

---

## 🏆 Skills Demonstrated

- Enterprise application onboarding  
- OpenID Connect SSO integration  
- Group-based authorization  
- Least-privilege access design  
- Per-application Conditional Access  
- MFA enforcement  
- IAM monitoring and log analysis  
- Zero Trust access control  

---

## 📌 Key Takeaway

This project demonstrates how enterprise IAM teams securely onboard applications, scope access based on business roles, enforce strong authentication, and validate access decisions using Conditional Access and sign-in logs.
