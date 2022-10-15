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
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Découvrez comment Microsoft utilise la technologie de chiffrement pour protéger les données client dans Microsoft Dynamics 365 au repos dans une base de données Microsoft et en transit.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1a11b854f9757eaf6ed7ea88c9d7254ee5f7918b
ms.sourcegitcommit: 1f4c51d022d1cfb6c194bf0f0af9c2841c781d68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2022
ms.locfileid: "68574030"
---
# <a name="encryption-in-microsoft-dynamics-365"></a>Chiffrement dans Microsoft Dynamics 365

Microsoft utilise la technologie de chiffrement pour protéger les données client dans Dynamics 365 au repos dans un centre de données Microsoft et pendant son transit entre les appareils utilisateur et nos centres de données. Les connexions établies entre les clients et les centres de données Microsoft sont chiffrées et tous les points de terminaison publics sont sécurisés à l’aide du protocole TLS standard. TLS établit efficacement une connexion de navigateur à serveur renforcée par la sécurité pour garantir la confidentialité et l’intégrité des données entre les bureaux et les centres de données. Une fois le chiffrement des données activé, il ne peut pas être désactivé. Pour plus d’informations, consultez [Chiffrement des données au niveau du champ](/previous-versions/dynamicscrm-2016/developers-guide/dn481562(v=crm.8)).

Dynamics 365 utilise le chiffrement au niveau de la cellule Microsoft SQL Server standard pour un ensemble d’attributs d’entité par défaut qui contiennent des informations sensibles, telles que les noms d’utilisateur et les mots de passe de messagerie. Cette fonctionnalité peut aider les organisations à répondre aux exigences de conformité associées à FIPS 140-2. Le chiffrement des données au niveau du champ est particulièrement important dans les scénarios qui tirent parti du [routeur Microsoft Dynamics CRM Email](/previous-versions/dynamicscrm-2016/administering-dynamics-365/hh699800(v=crm.8)), qui doit stocker les noms d’utilisateur et les mots de passe pour permettre l’intégration entre une instance Dynamics 365 et un service de messagerie.


Toutes les instances de Dynamics 365 utilisent [Microsoft SQL Server Transparent Data Encryption](/sql/relational-databases/security/encryption/transparent-data-encryption) (TDE) pour effectuer un chiffrement en temps réel des données lorsqu’elles sont écrites sur disque (au repos). TDE chiffre les fichiers de données SQL Server, Azure SQL Database et Azure SQL Data Warehouse. Par défaut, Microsoft stocke et gère les clés de chiffrement de base de données pour vos instances de Dynamics 365. (Les clés utilisées par Dynamics 365 for Financials sont générées par l’API .NET Framework Data Protection.) 

La fonctionnalité gérer les clés du Centre d’administration Power Platform permet aux administrateurs de gérer eux-mêmes les clés de chiffrement de base de données associées aux instances de Dynamics 365. Consultez [Gérer les clés de chiffrement pour votre instance Dynamics 365 (en ligne](/dynamics365/customer-engagement/admin/manage-encryption-keys-instance)). La fonctionnalité de gestion des clés prend en charge les fichiers de clé de chiffrement PFX et BYOK, tels que ceux stockés dans un HSM. (Pour plus d’informations sur la génération et le transfert d’une clé protégée par HSM sur Internet, consultez [Comment générer et transférer des clés protégées par HSM pour Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys).) 

Pour utiliser l’option de chargement de clé de chiffrement, vous avez besoin de la clé de chiffrement publique et privée.

La fonctionnalité de gestion des clés simplifie la gestion des clés de chiffrement à l’aide d’Azure Key Vault pour stocker en toute sécurité les clés de chiffrement. Azure Key Vault permet de protéger les clés de chiffrement et les secrets utilisés par les applications et services cloud. La fonctionnalité de gestion des clés ne nécessite pas que vous ayez un abonnement Azure Key Vault et, dans la plupart des cas, il n’est pas nécessaire d’accéder aux clés de chiffrement utilisées pour Dynamics 365 dans le coffre.
