---
sidebar_position: 6
title: Smart Contract
---

# Smart Contract

The design of KAYP's smart contracts is meticulously crafted to ensure security, scalability, and trust in managing electronic Bills of Lading (eBL). This section outlines the key components of the smart contracts, emphasizing their interactions and functionalities.

## Overview

KAYP's smart contracts consist of two primary components:

- **EBL Contract**: Manages the storage and certification of cryptographically secured electronic Bills of Lading (eBL).
- **Escrow Contract**: Facilitates secure transactions between buyers, sellers, and delivery agents.

These contracts work together to secure the exchange of sensitive shipping data while ensuring compliance with industry standards.

---

## Components Breakdown

### 1. EBL Contract

The **EBL Contract** is designed to store a cryptographically secured version of an electronic Bill of Lading on the blockchain, guaranteeing that the information is authenticated and tamper-proof.

#### Key Features:
- **Data Storage**: Stores the crypted version of the eBL, ensuring only authorized access.

#### Entrypoints:
- `eblUpdate(id)`: Allows the owner to update the crypted eBL, with strict access controls to prevent unauthorized modifications.

#### Example Flow:
- **Contract Initialization**:  
  The owner's address and the crypted eBL ID are set during contract deployment.
- **Update Functionality**:  
  The owner can update the eBL as needed, ensuring that only the authorized individual can make changes.

[](./img/ebl.png)

---

### 2. Escrow Contract

The **Escrow Contract** is built to ensure secure transactions between parties involved in shipping—namely buyers, sellers, and delivery agents. It releases funds only when all parties fulfill their obligations, enhancing trust in the transaction process.

#### Key Features:
- **Transaction Management**: Ensures that funds are only released upon confirmation of delivery.

#### Entrypoints:
- `deposit`: Buyer deposits funds, changing the contract state to `PAYMENT_RECEIVED`.
- `dispatch_items`: Seller confirms dispatching items.
- `confirm_delivery`: Delivery agent confirms receipt, triggering the release of funds to the seller.
- `reclaim_fund`: Allows the buyer to reclaim funds if items are not dispatched.

#### Example Flow:
- **Deposit Phase**:  
  Buyer deposits the agreed amount, changing the state to `PAYMENT_RECEIVED`.
- **Item Dispatch**:  
  Seller marks the items as dispatched, updating the state to `ITEMS_DISPATCHED`.
- **Delivery Confirmation**:  
  Upon confirmation, the contract releases the payment to the seller.
- **Funds Reclamation**:  
  If items are not dispatched, the buyer can reclaim the funds, changing the state to `CANCELED`.

[](./img/escrow.png)

---

## What's Next?

Looking forward, KAYP plans to integrate oracles to enhance the smart contracts' functionality. Oracles will enable the smart contracts to access external data feeds, allowing for automated updates and interactions based on real-world events.

Additionally, a connection to a **Maritime Delivery API** will be established. This API will facilitate communication with shipping companies and logistics providers, enabling automatic updates to the escrow contract based on key delivery milestones. For example, once a shipment is dispatched, the Maritime Delivery API can notify the smart contract, triggering subsequent actions like confirming delivery and releasing funds.

This integration will not only enhance the efficiency of the shipping process but also provide increased transparency and accountability, further solidifying KAYP's position as a leader in digitalizing maritime trade.

---

## Conclusion

The KAYP smart contracts offer a secure, scalable, and compliant solution for managing electronic Bills of Lading and facilitating escrow transactions. By leveraging cryptographic techniques and strict access controls, these contracts ensure the integrity and confidentiality of sensitive shipping data while enabling seamless transactions between parties.

For further insights into deploying and interacting with the smart contracts, please consult our [developer documentation](https://https://developer.dcsa.org/implementing-bill-of-lading-si-td) or reach out to our support team.
