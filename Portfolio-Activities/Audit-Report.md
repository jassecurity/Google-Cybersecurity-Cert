# Audit Findings Report 
## Botium Toys

**Audit Type**: Security Controls and Compliance Assessment  
**Auditor**: Jaspreet Kaur

---

## Scope of the Audit  
The audit covered the entire security program of Botium Toys, including:

- Employee equipment (on-premises and remote devices)
- Internal network infrastructure and internet access
- Systems and software used for operations (e-commerce, accounting, inventory)
- Data storage and retention practices
- Physical facilities (office, storefront, warehouse)

---

## Audit Objectives

- Identify existing controls and determine their effectiveness  
- Assess compliance with industry frameworks and regulations (NIST CSF, PCI DSS, GDPR, SOC 1/2)  
- Recommend remediations to strengthen Botium Toys’ security posture  

---

## Findings Summary

### Controls Assessment

| Control | Status | Findings |
|--------|--------|----------|
| **Least Privilege** | ❌ Not in place | All employees have unrestricted access to customer and internal data. No role-based access. |
| **Disaster Recovery Plans** | ❌ Not in place | No formal DR plan or backup system exists. |
| **Password Policies** | ✅ In place (**Needs remediation**) | A policy exists, but it lacks minimum complexity requirements (e.g., 8+ characters, alphanumeric, special characters). |
| **Separation of Duties** | ❌ Not in place | No formal implementation of duty separation between roles/functions. |
| **Firewall** | ✅ In place | Appropriately configured firewall is active. |
| **Intrusion Detection System (IDS)** | ❌ Not in place | No IDS deployed to detect anomalous or malicious activity. |
| **Backups** | ❌ Not in place | No automated or scheduled backups of critical data. |
| **Antivirus Software** | ✅ In place | Antivirus is installed and actively monitored by IT. |
| **Legacy System Monitoring** | ✅ In place (**Needs improvement*) | Legacy systems are monitored, but no regular schedule or documented intervention plan exists. |
| **Encryption** | ❌ Not in place | Sensitive data including credit card info is stored without encryption. |
| **Password Management System** | ❌ Not in place | No centralized password tool. Reset requests handled manually by IT. |
| **Locks (Physical Security)** | ✅ In place | Physical locks are up-to-date and functional. |
| **CCTV Surveillance** | ✅ In place | Surveillance system is functional and operational. |
| **Fire Detection/Prevention** | ✅ In place | Fire detection and suppression systems are present and operational. |

---

### 📋 Compliance Assessment

#### **PCI DSS (Payment Card Industry Data Security Standard)**

| Best Practice | Status | Findings |
|---------------|--------|----------|
| Only authorized users have access to credit card data | ❌ | Unrestricted employee access violates PCI requirements. |
| Credit card data stored/processed securely | ❌ | Credit card data is stored internally without secure protocols. |
| Encryption of credit card transaction data | ❌ | No encryption used for cardholder data. |
| Secure password policies | ❌ | Current password policy is insufficient; no enforcement or management system. |

#### **GDPR (General Data Protection Regulation)**

| Best Practice | Status | Findings |
|---------------|--------|----------|
| E.U. data kept private and secure | ❌ | No encryption or access restriction in place. |
| 72-hour breach notification plan | ✅ | Plan to notify E.U. customers exists and is documented. |
| Data classification and inventory | ❌ | Assets are not classified or inventoried. |
| Privacy policies and documentation enforced | ✅ | Internal documentation practices are followed by IT staff. |

#### **SOC 1 / SOC 2 (System and Organization Controls)**

| Best Practice | Status | Findings |
|---------------|--------|----------|
| User access policies in place | ❌ | No defined policies around user roles/access. |
| Confidentiality of sensitive data (PII/SPII) | ❌ | Data is not encrypted and is accessible to all employees. |
| Data integrity ensured | ✅ | Integrity controls are in place; data is consistent and validated. |
| Availability to authorized individuals | ✅ | Systems are accessible, but too broadly, access controls still lacking. |

---

## Risk Score: 8/10 – High

**Key Risks Identified:**

- High risk of data breaches due to lack of encryption and access controls  
- Potential regulatory fines for non-compliance with PCI DSS and GDPR  
- Lack of disaster recovery planning creates risk of prolonged downtime or data loss  

---

| Control Category       | Status                   | Notes                                                                                  |
| ------------------ | -----------------  | -------------------------------------------------------------------------------------- |
| **Administrative** | ❌ Minimal         | Lacks policy enforcement (passwords, least privilege, DR plans, separation of duties). |
| **Technical**      | ⚠️ Partial           | Firewalls and antivirus exist, but no IDS, encryption, or backup systems.              |
| **Physical**       | ✅ in place       | Physical controls like locks, CCTV, and fire systems are all functioning.              |

---

| Control Type  | Examples                    | In Place?    | 
| -------------- | --------------------------- | ------------ | 
| **Preventive** | Firewall, Least privilege, Locks, Seprartion of duties  | ⚠️ Partially        | 
| **Detective**  | CCTV, Legacy monitoring, IDS     | ⚠️ Partially | 
| **Corrective** | Backups, DR Plan            | ❌ No         | 
| **Deterrent**  | Encryption | ❌ No         | 

---

##  Recommendations

### High Priority (Immediate Implementation)

1. **Implement encryption** for all sensitive customer data and credit card transactions.  
2. **Enforce access controls** – including least privilege and separation of duties.  
3. **Establish and document a disaster recovery plan** including automated backups.  
4. **Deploy an Intrusion Detection System (IDS)** to monitor for suspicious activity.  
5. **Revise password policy** to meet current complexity standards and implement a password management system.  
6. **Classify and inventory all assets**, including legacy systems.  

### Medium Priority

- Regularize legacy system maintenance schedules.  
- Improve monitoring and alerting mechanisms for system health and activity.  

---

## Conclusion

Botium Toys has a functional IT infrastructure with some security practices in place. However, **critical gaps in data protection, compliance, and business continuity planning significantly elevate their risk profile**. The company should prioritize remediating high-risk areas to align with NIST CSF, PCI DSS, GDPR, and SOC 2 standards.

---

## Provided Reference Documents

The following documents were provided to support this audit and were reviewed as part of the assessment process:

1. [Botium Toys: Scope, goals, and risk assessment report](https://docs.google.com/document/d/1s2u_RuhRAI40JSh-eZHvaFsV1ZMxcNSWXifHDTOsgFc/template/preview)
2. [Control Categories](https://docs.google.com/document/d/1HsIw5HNDbRXzW7pmhPLsK06B7HF-KMifENO_TlccbSU/template/preview)
3. [Controls & Compliance Audit Checklist](https://docs.google.com/document/d/10NoXfyE3ZSiHFqiTE0fINL3xdPvTZq0j0VwnFEM0N3g/template/preview)

These documents provide insight into Botium Toys' current security practices, control implementations, and compliance posture.
