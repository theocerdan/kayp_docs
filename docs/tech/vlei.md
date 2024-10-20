---
sidebar_position: 7
title: VLei Integration
---

# vLEI

**vLEI (verifiable Legal Entity Identifiers)** are verifiable digital identifiers that enable automatic authentication of legal entities and their authorized representatives. In the context of KAYP, integrating vLEI enhances the security and transparency of transactions, especially for eB/L (Electronic Bill of Lading) and **trade finance** solutions.

### **Why Integrate vLEI in KAYP?**

1. **Security and Compliance**:
    - **vLEI** ensures that all entities and individuals involved in a transaction are verified through an internationally recognized standard ([ISO 17442](https://www.gleif.org/en/about-lei/iso-17442-the-lei-code-structure/)).
    - Ensures that KAYP complies with global standards for **KYC** and fraud prevention.
2. **Process Automation**:
    - **vLEI** automates identity and role verification in transactions without manual intervention, speeding up document validation and signing processes (eB/L, financial contracts).
3. **Global Interoperability**:
    - **vLEI** works seamlessly with various digital trade platforms and DLT (such as blockchain), ensuring full interoperability for cross-border transactions.

### **Steps to Integrate vLEI in KAYP**

### **1. Basic vLEI Integration**

- **Obtain a vLEI for the Company**:
    - During the company’s registration on KAYP, the organization must obtain a **vLEI** from a **qualified issuer** (see [GLEIF](https://www.gleif.org/en/vlei/get-a-vlei-list-of-qualified-vlei-issuing-organizations)).
    - Use the **GLEIF API** to verify that the entity is legitimate and its LEI or vLEI is valid.
- **Store the vLEI**:
    - Associate the **vLEI** with each company's account in KAYP's database. This vLEI will serve to verify the entity's authenticity for every transaction or interaction on the platform.

### **2. vLEI for Authorized Representatives**

- **Issue vLEI for Representatives**:
    - After issuing a **vLEI for the organization**, it can request **additional vLEIs** for its key representatives (e.g., shipping manager or finance officer).
- **Role Verification**:
    - The **vLEIs** of representatives must include information about their official role within the organization. Use the GLEIF API to verify that these roles are valid and align with the company’s public records.

### **3. Using vLEI in Smart Contracts**

- **eB/L Smart Contracts**:
    - Link the company's **vLEI** and those of its representatives to **eB/L** transactions. When an eB/L is signed or exchanged, the smart contract automatically verifies the identities of the parties using their **vLEIs**.
- **Trade Finance Smart Contracts**:
    - Use **vLEIs** for finance contracts to ensure that only authorized entities and individuals participate in financial transactions. This includes automatic approval of financing documents by verified representatives.

### **4. Revocation and Updating of vLEI**

- **Dynamic vLEI Management**:
    - When a representative leaves the company or changes roles, the **vLEI** must be revoked and updated through the **vLEI reissuance process**. This ensures that only active and verified individuals hold signing or approval rights.

### **Technical Implementation**

### **1. GLEIF API for vLEI Management**

- **Verification and Management**: Use the API calls provided by GLEIF to:
    - Verify the validity of the LEI/vLEI of companies.
    - Ensure the status of vLEIs is up-to-date.
    - Integrate automatic verification into KAYP's smart contracts.

### **2. Smart Contracts with vLEI Verification**

- In **smart contracts**, include checkpoints to validate the **vLEI** of entities involved in the transaction.
- When a transaction is initiated, the smart contract calls the GLEIF API to verify the **vLEI** and proceeds only if the identifier is valid.

### **Integration Flow Example:**

1. **Company Account Creation**:
    - The user submits their **LEI/vLEI** during registration → KAYP verifies with the GLEIF API.
2. **Adding Representatives**:
    - The company administrator adds users (representatives) and assigns **vLEIs** based on their role.
3. **Document Exchange via Smart Contract**:
    - During an **eB/L** exchange, the smart contract verifies the **vLEI** of the shipper and consignee → validates the exchange after verification.
4. **Access to Trade Finance Services**:
    - When a company requests financing, its **vLEI** and that of its representatives are verified before allowing access to funds.
