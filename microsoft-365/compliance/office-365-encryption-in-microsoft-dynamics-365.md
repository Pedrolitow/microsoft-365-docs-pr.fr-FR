---
title: Chiffrement dans Microsoft Dynamics 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Découvrez comment Microsoft utilise la technologie de chiffrement pour protéger les données client dans Microsoft Dynamics 365 au repos dans une base de données Microsoft et en transit.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 22ac316240b0bf299351c48eef876d456662b23e4a856905ebdd92829c41a182
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53885542"
---
# <a name="encryption-in-microsoft-dynamics-365"></a>Chiffrement dans Microsoft Dynamics 365

Microsoft utilise la technologie de chiffrement pour protéger les données client dans Dynamics 365 pendant qu’elles sont au repos dans une base de données Microsoft et pendant qu’elles sont en transit entre les appareils des utilisateurs et nos centres de données. Les connexions établies entre les clients et les centres de données Microsoft sont chiffrées, et tous les points de terminaison publics sont sécurisés à l’aide de TLS standard. TLS établit efficacement une connexion de navigateur à serveur améliorée pour garantir la confidentialité et l’intégrité des données entre les bureaux et les centres de données. Une fois le chiffrement des données activé, il ne peut pas être désactivé. Pour plus d’informations, voir [Chiffrement des données au](/previous-versions/dynamicscrm-2016/developers-guide/dn481562(v=crm.8))niveau du champ.

Dynamics 365 utilise le chiffrement au niveau Microsoft SQL Server cellule standard pour un ensemble d’attributs d’entité par défaut qui contiennent des informations sensibles, telles que des noms d’utilisateur et des mots de passe de messagerie. Cette fonctionnalité peut aider les organisations à respecter les exigences de conformité associées à LA FIPS 140-2. Le chiffrement des données au niveau du champ est particulièrement important dans les scénarios qui exploitent le routeur de messagerie [Microsoft Dynamics CRM,](/previous-versions/dynamicscrm-2016/administering-dynamics-365/hh699800(v=crm.8))qui doit stocker les noms d’utilisateur et les mots de passe pour permettre l’intégration entre une instance Dynamics 365 et un service de messagerie.

Toutes les instances de Dynamics 365 utilisent [Microsoft SQL Server Transparent Data Encryption](/sql/relational-databases/security/encryption/transparent-data-encryption) (TDE) pour effectuer le chiffrement en temps réel des données lorsqu’elles sont écrites sur disque (au repos). TDE chiffre les fichiers SQL Server, Azure SQL Database et Azure SQL Data Warehouse. Par défaut, Microsoft stocke et gère les clés de chiffrement de base de données pour vos instances de Dynamics 365. (Les clés utilisées par Dynamics 365 for Financials sont générées par l’API .NET Framework protection des données.)

La fonctionnalité gérer les clés dans le Centre d’administration Dynamics 365 permet aux administrateurs de gérer eux-mêmes les clés de chiffrement de base de données associées à des instances de Dynamics 365. (Les clés de chiffrement de base de données auto-gérées sont disponibles uniquement dans la mise à jour de janvier 2017 pour Microsoft Dynamics 365 et peuvent ne pas être disponibles pour les versions ultérieures. Pour plus d’informations, voir Gérer les clés de chiffrement pour votre [instance Dynamics 365 (en ligne).](/dynamics365/customer-engagement/admin/manage-encryption-keys-instance) La fonctionnalité de gestion des clés prend en charge les fichiers de clés de chiffrement PFX et BYOK, tels que ceux stockés dans un HSM. (Pour plus d’informations sur la génération et le transfert d’une clé protégée par HSM sur Internet, voir Comment générer et transférer des clés protégées par [HSM](/azure/key-vault/key-vault-hsm-protected-keys)pour Azure Key Vault.)

Pour utiliser l’option de clé de chiffrement de téléchargement, vous avez besoin de la clé de chiffrement publique et privée.

La fonctionnalité de gestion des clés met la complexité de la gestion des clés de chiffrement à l’aide d’Azure Key Vault pour stocker en toute sécurité les clés de chiffrement. Azure Key Vault permet de protéger les clés de chiffrement et les secrets utilisés par les applications et services cloud. La fonctionnalité de gestion des clés ne nécessite pas que vous disposez d’un abonnement Azure Key Vault et, dans la plupart des cas, il n’est pas nécessaire d’accéder aux clés de chiffrement utilisées pour Dynamics 365 dans le coffre.