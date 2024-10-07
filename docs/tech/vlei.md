---
sidebar_position: 7
title: VLei Integration
---

# Intégration des vLEI dans KAYP

### **Introduction**

Les **vLEI (verifiable Legal Entity Identifier)** sont des identifiants numériques vérifiables qui permettent une authentification automatique des entités juridiques et de leurs représentants autorisés. Dans le contexte de KAYP, l’intégration des vLEI permet de renforcer la sécurité et la transparence des transactions, notamment pour les eB/L (Electronic Bill of Lading) et les solutions de **trade finance**.

### **Pourquoi intégrer les vLEI dans KAYP ?**

1. **Sécurité et conformité** :
    - Les **vLEI** garantissent que toutes les entités et individus participant à une transaction sont vérifiés via un standard reconnu internationalement ([ISO 17442](https://www.gleif.org/fr/about-lei/iso-17442-the-lei-code-structure/)).
    - Assure que KAYP est conforme aux standards globaux en matière de **KYC** et de lutte contre la fraude.
2. **Automatisation des processus** :
    - Le **vLEI** permet d’automatiser la vérification des identités et des rôles dans les transactions sans intervention manuelle, ce qui accélère les processus de validation et de signature des documents (eB/L, contrats financiers).
3. **Interopérabilité globale** :
    - Le **vLEI** fonctionne de manière transparente avec les différentes plateformes de commerce numérique et DLT (comme la blockchain), assurant une interopérabilité totale pour les transactions transfrontalières.

### **Étapes pour intégrer les vLEI dans KAYP**

### **1. Intégration de base du vLEI**

- **Obtenir un vLEI pour l'entreprise** :
    - Lors de l’inscription d’une entreprise sur KAYP, l’organisation doit obtenir un **vLEI** auprès d’un **émetteur qualifié** (voir [GLEIF](https://www.gleif.org/en/vlei/get-a-vlei-list-of-qualified-vlei-issuing-organizations)).
    - Utiliser l'**API GLEIF** pour vérifier que l'entité est légitime et que son LEI ou vLEI est valide.
- **Stocker le vLEI** :
    - Associer le **vLEI** à chaque compte entreprise dans la base de données KAYP. Ce vLEI servira à vérifier l’authenticité de l’entité pour chaque transaction ou interaction sur la plateforme.

### **2. vLEI pour les représentants autorisés**

- **Émettre des vLEI pour les représentants** :
    - Après avoir émis un **vLEI pour l’organisation**, elle peut demander des **vLEI supplémentaires** pour ses représentants clés (par exemple, le responsable des expéditions ou le gestionnaire de finance).
- **Vérification des rôles** :
    - Les **vLEI** des représentants doivent inclure des informations sur leur rôle officiel dans l’organisation. Utiliser l'API GLEIF pour vérifier que ces rôles sont valides et en ligne avec les statuts publics de l'entreprise.

### **3. Utilisation des vLEI dans les smart contracts**

- **Smart contracts eB/L** :
    - Associer le **vLEI de l’entreprise** et des représentants aux transactions de **eB/L**. Lorsqu’un eB/L est signé ou échangé, le smart contract vérifie automatiquement les identités des parties grâce à leur **vLEI**.
- **Smart contracts de trade finance** :
    - Utiliser les **vLEI** pour les contrats de financement, afin de valider que seules des entités et des individus autorisés participent aux transactions financières. Cela inclut l’approbation automatique de documents de financement par des représentants vérifiés.

### **4. Revocation et mise à jour des vLEI**

- **Gestion dynamique des vLEI** :
    - Lorsqu’un représentant quitte l’entreprise ou change de rôle, le **vLEI** doit être révoqué et mis à jour via le processus de réémission de **vLEI**. Cela garantit que seules les personnes actives et vérifiées détiennent des droits de signature ou d’approbation.

### **Implémentation technique**

### **1. API GLEIF pour la gestion des vLEI**

- **Vérification et gestion** : Utiliser les appels d’API fournis par GLEIF pour :
    - Vérifier la validité des LEI/vLEI des entreprises.
    - Assurer la mise à jour des statuts des vLEI.
    - Intégrer la vérification automatique dans les smart contracts KAYP.

### **2. Smart contracts avec vérification des vLEI**

- Dans les **smart contracts**, inclure des points de contrôle pour valider les **vLEI** des entités impliquées dans la transaction.
- Lorsqu’une transaction est initiée, le smart contract appelle l’API GLEIF pour vérifier le **vLEI**, puis continue seulement si l’identifiant est valide.

### **Exemple de flux d'intégration :**

1. **Création du compte d’entreprise** :
    - L’utilisateur soumet son **LEI/vLEI** lors de l'inscription → KAYP vérifie avec l'API GLEIF.
2. **Ajout des représentants** :
    - L’administrateur de l’entreprise ajoute des utilisateurs (représentants) et leur assigne des **vLEI** en fonction de leur rôle.
3. **Échange de documents via smart contract** :
    - Lors d’un échange de **eB/L**, le smart contract vérifie le **vLEI** de l'expéditeur et du destinataire → valide l’échange après vérification.
4. **Accès aux services de trade finance** :
    - Lorsqu’une entreprise demande un financement, son **vLEI** et celui de ses représentants sont vérifiés avant d'autoriser l’accès aux fonds.