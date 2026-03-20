# Enterprise Identity & Access Management (IAM) Infrastructure Deployment.

The objectives of this project remains as follows:

## 1. Secure Directory Architecture (The Foundation)

The first objective is to move away from a "flat" network where everyone is in one folder.

- **Goal:** Design a multi-level **Organizational Unit (OU)** hierarchy.
- **Why:** This allows for "Granular Administration"—meaning you can apply different rules to HR than you do to Finance without them interfering with each other.
- **Success Metric:** A structured tree that separates Users, Computers, and Administrative accounts.

## 2. Principle of Least Privilege (Security)

In modern IT, users should only have the bare minimum access they need to do their jobs.

- **Goal:** Implement **RBAC (Role-Based Access Control)** using the **AGDLP** (Account, Global, Domain Local, Permissions) method.
- **Why:** To prevent "Privilege Escalation." If a Marketing intern's account is hacked, the attacker shouldn't be able to see the CEO's files.
- **Success Metric:** Creating specific Security Groups with distinct "Read-Only" vs "Full Control" permissions.

## 3. Policy-Driven Hardening (The Rules)

An objective of any Admin is to ensure the computers are safe even when users aren't looking.

- **Goal:** Deploy **Group Policy Objects (GPOs)** to enforce a "Security Baseline."
- **Why:** To automate security. You don't want to manually disable USB ports on 100 computers; you want a GPO to do it for you.
- **Success Metric:** Enforced password complexity, automated screen locks, and restricted access to the Windows Registry/CMD for non-admins.

## 4. Automation & Scalability (Efficiency)

A "Senior" level objective is proving you don't do things manually.

- **Goal:** Use **PowerShell** for User Lifecycle Management (Onboarding/Offboarding).
- **Why:** If a company hires 50 people at once, a manual process takes all day. A script takes 5 seconds.
- **Success Metric:** A functioning PowerShell script that creates users from a CSV file and places them in the correct OUs.

## 5. Service Continuity & Health (Monitoring)

The final objective is ensuring the "Brain" (Active Directory) stays healthy.

- **Goal:** Configure and monitor **Active Directory Health & DNS.**
- **Why:** AD literally cannot function without DNS. If DNS fails, no one can log in, and the company stops.
- **Success Metric:** Successful resolution of internal names and error-free "DCDIAG" (Domain Controller Diagnostic) reports.

# Aim of the project.

The primary aim of this project is to **architect and deploy a functional Enterprise Identity and Access Management (IAM) environment** using Active Directory.

<aside>
👉🏻

How the theory of this project works?

</aside>

<aside>
👉🏻

Think of this as building a digital city.

</aside>

Say there are 10000 people in a city and to manage these people you need a database. AD is that database storing objects(people), computers(machines) and groups(clubs).

## Secure Directory Architecture (The Foundation)

To build an Active Directory City, you need the **Tools** (the hammers and saws). In the Windows world, these are called 

**RSAT** (Remote Server Administration Tools)

> WINDOWS BY DEFAULT HIDES THE PROFESSIONAL TOOLS.
> 

## INSTALLING **RSAT** (Remote Server Administration Tools)

## 📋 The Lab Blueprint (Our City Map)

 "Architectural Plan."

- **[CORP.LOCAL]**
    - 📂 **CORP-Production** (The Main Parent OU)
        - 📂 **Admins** (For your high-privilege accounts)
        - 📂 **Departments** (Where the magic happens)
            - 📂 **HR**
            - 📂 **IT**
            - 📂 **Finance**
            - 📂 **Sales**
        - 📂 **Resources**
            - 📂 **Computers** (Workstations)
            - 📂 **Servers**
            - 📂 **Groups** (Security Clubs)
            
        
        | **Level** | **Name in Your Lab** | **Purpose** |
        | --- | --- | --- |
        | **Forest** | `CORP.LOCAL` | The entire security boundary. |
        | **Tree** | `CORP.LOCAL` | A collection of domains sharing a contiguous namespace. |
        | **Domain** | `CORP.LOCAL` | The central database for your "City." |
        | **Parent OU** | `CORP-Production` | The "Container" for all your custom company work. |
        | **Sub-OU** | `Departments` | Breaks down the company by job function. |
        | **Object** | `Admin-Royan` | A specific identity (User) inside the `Admins` OU. |

# Troubleshooting Log

| Issue | Root Cause | Resolution |
| --- | --- | --- |
| ISO not loading. | Architecture Mismatch | DOwnloaded windows 11 from vmware auto downloader. |
|  |  |  |