---
sidebar_position: 6
title: Encryption FHE
---

## Fully Homomorphic Encryption

In the context of international trade finance, multiple parties are involved in handling sensitive documents such as the Bill of Lading (B/L), which acts as a receipt of shipment, a document of title, and evidence of the contract of carriage. Typically, banks, customs authorities, transporters, buyers, and sellers must interact with the B/L to ensure that the terms of a Letter of Credit (LC) are met before payments are released.

To protect sensitive data while allowing these parties to verify and update specific elements of the B/L, Fully Homomorphic Encryption (FHE) is utilized. FHE enables computations to be performed on encrypted data, ensuring that no party gains access to unauthorized information while still allowing necessary operations, such as status updates or data verifications.

This document provides a technical breakdown of how KAYP implements FHE within a system of smart contracts to facilitate secure, verifiable, and efficient trade finance operations.

## 2. Overview of the Process

### 2.1 Key Parties Involved

- **Seller**: Ships goods (e.g., roses from Kenya).
- **Buyer**: Receives goods (e.g., Netherlands-based importer).
- **Banks**: Issue and confirm the Letter of Credit (LC), ensuring that payment is made once all conditions are satisfied.
- **Customs Authorities**: Verify the goods upon entry and exit, ensuring that they match the documentation.
- **Transporter**: Issues the Bill of Lading (B/L), which serves as proof of shipment.
- **KAYP**: Provides the digital infrastructure for securely handling eB/Ls, smart contracts, and encrypted data processing using FHE.

### 2.2 Document Flow

1. **Letter of Credit (LC) Issuance**: The buyer's bank issues an LC guaranteeing payment to the seller once certain conditions are met (such as the issuance of the B/L).
2. **eB/L Creation**: The transporter issues an electronic Bill of Lading (eB/L) after goods are shipped, storing the encrypted document on KAYP.
3. **Document Verification**: Various parties (banks, customs, etc.) verify different parts of the eB/L without accessing the entire document.
4. **Status Updates**: The status of the eB/L is updated (e.g., from "Draft" to "Issued" to "Released") based on the progress of the shipment and validation of conditions.
5. **Escrow Payment Release**: Once the conditions of the LC are satisfied, funds are released to the seller through a smart contract.

## 3. Fully Homomorphic Encryption (FHE)

### 3.1 What is FHE?

Fully Homomorphic Encryption (FHE) allows computations to be performed on encrypted data without ever needing to decrypt it. This means that parties can verify or modify specific portions of a document (such as the status of a shipment) without exposing other sensitive information, such as financial terms or contract details.

In the context of KAYP’s trade finance solution, FHE ensures that:

- Data privacy is maintained throughout the process.
- Authorized parties can perform necessary operations on encrypted data.
- Integrity and security of the document are guaranteed, as sensitive information is never exposed.

### 3.2 Key Features of FHE in KAYP

- **Granular Access Control**: Each party can interact with predefined parts of the eB/L (e.g., shipment details for customs or contract terms for banks) without seeing unrelated information.
- **Data Integrity**: Any changes or computations performed on the encrypted document (such as updating the shipment status) maintain the integrity of the original data.
- **Security**: Sensitive information, such as financial terms or contract details, remains encrypted and secure, even during verification processes.

## 4. Implementation of FHE in Smart Contracts

### 4.1 Smart Contracts Overview

KAYP utilizes two main types of smart contracts:

- **eB/L Smart Contract**: This contract handles the creation, status updates, and verification of the electronic Bill of Lading.
- **Escrow Smart Contract**: This contract manages the release of funds once all conditions of the LC are met, based on the status of the eB/L and other associated documents.

### 4.2 eB/L Smart Contract

- **Encrypted Data Storage**: The eB/L, which contains sensitive shipment details (e.g., item description, quantity, shipment date, and destination), is encrypted using FHE and stored off-chain. A hash of the encrypted eB/L is logged on-chain to guarantee its integrity.
- **Status Management**: The transporter's and other authorized parties' keys allow them to update the status of the eB/L (e.g., "Draft", "Issued", "Released") based on predefined permissions. These status updates are performed on the encrypted document using FHE.
- **Verification by Multiple Parties**: Customs, banks, and other relevant parties can verify specific portions of the encrypted eB/L, such as shipment details, while the rest of the document remains encrypted. This ensures that each party only has access to the data necessary for their role.

### 4.3 Escrow Smart Contract

- **Conditional Payment**: The smart contract managing the escrow account is triggered once the status of the eB/L reaches "Released" and the conditions of the LC are verified by the bank.
- **FHE for Verification**: Banks can verify the terms of the LC and the shipment status without decrypting the entire eB/L. FHE allows them to confirm that the shipment has met the contractual obligations, ensuring compliance before releasing funds.
- **Release of Funds**: Once the encrypted conditions are satisfied, the escrow contract releases the funds to the seller's bank.

## 5. Example Use Case

### 5.1 Scenario: Shipping Roses from Kenya to the Netherlands

- **Shipment Initiation**: The seller in Kenya ships roses to the buyer in the Netherlands. The transporter issues an encrypted eB/L using FHE, containing details of the shipment, which is logged on-chain via a hash.
- **Customs Verification**: Customs authorities at the port of origin and destination verify the shipment details (e.g., the quantity and type of goods) using their specific keys. These verifications are performed on the encrypted data without accessing the financial terms.
- **Bank Verification**: The buyer’s bank verifies that the conditions of the LC are met (e.g., shipment is on time, and the status is "Released") by interacting with the encrypted eB/L.
- **Escrow Release**: Once all parties have confirmed the necessary details, the escrow contract releases the funds to the seller, and the transaction is complete.

## 6. Security and Privacy Considerations

### 6.1 Granular Data Access

- **Role-Based Access Control**: Each party receives a key that allows them to access only the portions of the encrypted eB/L relevant to their role.
- **FHE Safeguards**: FHE ensures that no party gains unauthorized access to sensitive data, even while performing necessary verifications or status updates.

### 6.2 Data Integrity and Transparency

- **On-Chain Hashing**: The hash of the encrypted eB/L is stored on-chain, ensuring that any changes to the document are tracked and verifiable.
- **Immutable Logs**: The blockchain provides an immutable record of status updates, ensuring full transparency of the document’s life cycle.

## 7. Conclusion

In the context of trade finance, FHE provides a powerful solution for maintaining the privacy of sensitive data while allowing multiple parties to interact with a document securely. By integrating FHE into KAYP’s platform for handling eB/Ls and escrow smart contracts, trade operations are made more secure, efficient, and verifiable, while ensuring that each party only accesses the information necessary for their role.
