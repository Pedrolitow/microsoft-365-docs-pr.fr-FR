---
title: Chiffrement dans Azure
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
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: En savoir plus sur le chiffrement disponible dans Azure, tel que le chiffrement de disque Azure
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 72a6560d6d3fdb12489b5b2cc988c469277c81c425ca4117b728039ca0de1ff2
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53855910"
---
# <a name="encryption-in-azure"></a>Chiffrement dans Azure

Les protections technologiques dans Azure, telles que les communications chiffrées et les processus opérationnels, contribuent à sécuriser vos données. Vous avez également la possibilité d’implémenter des fonctionnalités de chiffrement supplémentaires et de gérer vos propres clés de chiffrement. Quelle que soit la configuration du client, Microsoft applique le chiffrement pour protéger les données client dans Azure. Microsoft vous permet également de contrôler vos données hébergées dans Azure via une gamme de technologies avancées pour chiffrer, contrôler et gérer les clés de chiffrement, ainsi que contrôler et auditer l’accès aux données. En outre, stockage Azure fournit un ensemble complet de fonctionnalités de sécurité qui permettent aux développeurs de créer des applications sécurisées.

Azure offre de nombreux mécanismes de protection des données lors de son déplacement d’un emplacement à un autre. Microsoft utilise TLS pour protéger les données lorsqu’il se déplace entre les services cloud et les clients. Les centres de données de Microsoft négocient une connexion TLS avec les systèmes clients qui se connectent aux services Azure. Perfect Forward Secrecy (PFS) protège les connexions entre les systèmes clients des clients et les services cloud de Microsoft par des clés uniques. Les connexions utilisent également des longueurs de clé de chiffrement 2 048 bits basées sur RSA. Cette combinaison complique l’interception et l’accès aux données en transit.

Les données peuvent être sécurisées en transit entre une application et Azure à l’aide du chiffrement côté [client,](/azure/storage/storage-client-side-encryption)HTTPS ou SMB 3.0. Vous pouvez activer le chiffrement pour le trafic entre vos propres machines virtuelles (VM) et vos utilisateurs. Avec [Azure Virtual Networks,](https://azure.microsoft.com/services/virtual-network/)vous pouvez utiliser le protocole IPsec standard pour chiffrer le trafic entre votre passerelle VPN d’entreprise et Azure, ainsi qu’entre les VM situées sur votre réseau virtuel.

Pour les données au repos, Azure offre de nombreuses options de chiffrement, telles que la prise en charge d’AES-256, ce qui vous permet de choisir le scénario de stockage de données qui répond le mieux à vos besoins. Les données peuvent être automatiquement chiffrées lorsqu’elles sont écrites sur stockage Azure à l’aide du chiffrement [Stockage Service,](/azure/storage/storage-service-encryption)et le système d’exploitation et les disques de données utilisés par les ordinateurs virtuels peuvent être chiffrés. Pour plus d’informations, voir recommandations en matière de [sécurité Windows machines virtuelles dans Azure.](/azure/security/azure-security-disk-encryption) En outre, l’accès délégué aux objets de données dans stockage Azure peut être accordé à l’aide de [signatures d’accès partagé.](/azure/storage/storage-dotnet-shared-access-signature-part-1) Azure fournit également le chiffrement des données au repos à l’Transparent Data Encryption [pour Azure SQL Database et Data Warehouse](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Pour plus d’informations sur le chiffrement dans Azure, voir [Azure Encryption overview](/azure/security/security-azure-encryption-overview) et Azure Data [Encryption-at-Rest](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Chiffrement de disque Azure

Le chiffrement de disque Azure vous permet de chiffrer vos Windows et votre infrastructure Linux en tant que disques IaaS (VM Disk Encryption). Le chiffrement de disque Azure tire parti de la fonctionnalité BitLocker de Windows et de la fonctionnalité DM-Crypt de Linux pour fournir un chiffrement au niveau du volume pour le système d’exploitation et les disques de données. Il garantit également que toutes les données sur les disques des ordinateurs virtuels sont chiffrées au repos dans votre stockage Azure. Le chiffrement de disque Azure est intégré à Azure Key Vault pour vous aider à contrôler, gérer et auditer l’utilisation des clés de chiffrement et des clés secrètes.

Pour plus d’informations, voir recommandations en matière de [sécurité Windows machines virtuelles dans Azure.](/azure/virtual-machines/windows/security-recommendations)

## <a name="azure-storage-service-encryption"></a>stockage Azure Chiffrement de service

Avec [stockage Azure service de](/azure/storage/storage-service-encryption)chiffrement, stockage Azure chiffre automatiquement les données avant de les rendre persistantes dans le stockage et déchiffre les données avant la récupération. Les processus de chiffrement, de déchiffrement et de gestion des clés sont totalement transparents pour les utilisateurs. stockage Azure Le chiffrement de service peut être utilisé pour les objets [blob Azure Stockage](https://azure.microsoft.com/services/storage/blobs/) [et les fichiers Azure.](https://azure.microsoft.com/services/storage/files/) Vous pouvez également utiliser des clés de chiffrement gérées par Microsoft avec stockage Azure service de chiffrement, ou vous pouvez utiliser vos propres clés de chiffrement. (Pour plus d’informations sur l’utilisation de vos propres clés, voir [chiffrement Stockage service](/azure/storage/common/storage-service-encryption-customer-managed-keys)à l’aide de clés gérées par le client dans Azure Key Vault . Pour plus d’informations sur l’utilisation des clés gérées par Microsoft, voir [Stockage Service encryption for Data at Rest](/azure/storage/storage-service-encryption).) En outre, vous pouvez automatiser l’utilisation du chiffrement. Par exemple, vous pouvez activer ou désactiver le chiffrement de service Stockage par programme sur un compte de stockage à l’aide de l’API REST du fournisseur de ressources [stockage Azure,](/rest/api/storagerp/)de la bibliothèque cliente du fournisseur de ressources Stockage pour [.NET,](/dotnet/api/overview/azure/storage) [Azure PowerShell](/powershell/azureps-cmdlets-docs)ou de l’interface de ligne de base de données [Azure.](/azure/storage/storage-azure-cli)

Certains Microsoft 365 utilisent Azure pour stocker des données. Par exemple, SharePoint Online et OneDrive Entreprise stocker des données dans le stockage Blob Azure et Microsoft Teams stocke les données de son service de conversation dans des tables, des objets blob et des files d’attente. En outre, la fonctionnalité Gestionnaire de conformité dans le Centre de conformité Microsoft 365 stocke les données entrées par le client qui sont stockées sous forme chiffrée dans [Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest), une base de données PaaS (Platform as a Service), distribuée globalement et à modèles multiples. stockage Azure Le chiffrement de service chiffre les données stockées dans le stockage Blob Azure et dans les tables, et le chiffrement de disque Azure chiffre les données dans les files d’attente, ainsi que les disques de machine virtuelle Windows et IaaS pour fournir le chiffrement de volume pour le système d’exploitation et le disque de données. La solution garantit que toutes les données des disques de l’ordinateur virtuel sont chiffrées au repos dans votre stockage Azure. [Le chiffrement au repos dans Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest) est implémenté à l’aide de plusieurs technologies de sécurité, notamment les systèmes de stockage de clés sécurisées, les réseaux chiffrés et les API de chiffrement.

## <a name="azure-key-vault"></a>Azure Key Vault

La gestion des clés sécurisées n’est pas seulement essentielle aux meilleures pratiques de chiffrement . il est également essentiel pour la protection des données dans le cloud. [Azure Key Vault vous](/azure/key-vault/key-vault-whatis) permet de chiffrer des clés et de petites clés secrètes, telles que des mots de passe qui utilisent des clés stockées dans des modules de sécurité matérielle (HSM). Azure Key Vault est la solution recommandée par Microsoft pour gérer et contrôler l’accès aux clés de chiffrement utilisées par les services cloud. Les autorisations d’accès aux clés peuvent être attribuées à des services ou à des utilisateurs Azure Active Directory comptes. Azure Key Vault décharge les organisations de la nécessité de configurer, de mettre à jour et de gérer des HSM et des logiciels de gestion des clés. Avec Azure Key Vault, Microsoft ne voit jamais vos clés et les applications n’y ont pas un accès direct ; vous maintenez le contrôle. Vous pouvez également importer ou générer des clés dans des HSM. Les organisations qui ont un abonnement qui inclut Azure Information Protection peuvent configurer leur client Azure Information Protection pour utiliser une clé gérée par le client [Apportez](/information-protection/plan-design/byok-price-restrictions) votre propre clé (BYOK) et enregistrer [son utilisation.](/information-protection/deploy-use/log-analyze-usage)