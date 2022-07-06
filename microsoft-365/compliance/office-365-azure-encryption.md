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
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: En savoir plus sur le chiffrement disponible dans Azure, par exemple Azure Disk Encryption
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66fb4e54c0837534d6943372d84cf3a4864e4739
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632176"
---
# <a name="encryption-in-azure"></a>Chiffrement dans Azure

Les protections technologiques dans Azure, telles que les communications chiffrées et les processus opérationnels, permettent de sécuriser vos données. Vous avez également la possibilité d’implémenter des fonctionnalités de chiffrement supplémentaires et de gérer vos propres clés de chiffrement. Quelle que soit la configuration du client, Microsoft applique le chiffrement pour protéger les données client dans Azure. Microsoft vous permet également de contrôler vos données hébergées dans Azure via une gamme de technologies avancées pour chiffrer, contrôler et gérer les clés de chiffrement, ainsi que contrôler et auditer l’accès aux données. En outre, Stockage Azure fournit un ensemble complet de fonctionnalités de sécurité qui permettent aux développeurs de créer ensemble des applications sécurisées.

Azure offre de nombreux mécanismes de protection des données à mesure qu’elles passent d’un emplacement à un autre. Microsoft utilise TLS pour protéger les données lorsqu’elles transitent entre les services cloud et les clients. Les centres de données de Microsoft négocient une connexion TLS avec les systèmes clients qui se connectent aux services Azure. Perfect Forward Secrecy (PFS) protège les connexions entre les systèmes clients des clients et les services cloud de Microsoft par des clés uniques. Les connexions utilisent également des longueurs de clé de chiffrement 2 048 bits basées sur RSA. Cette combinaison rend difficile l’interception et l’accès aux données en transit.

Les données peuvent être sécurisées en transit entre une application et Azure à l’aide du [chiffrement côté client](/azure/storage/storage-client-side-encryption), HTTPS ou SMB 3.0. Vous pouvez activer le chiffrement pour le trafic entre vos propres machines virtuelles et vos utilisateurs. Avec [les réseaux virtuels Azure](https://azure.microsoft.com/services/virtual-network/), vous pouvez utiliser le protocole IPsec standard pour chiffrer le trafic entre votre passerelle VPN d’entreprise et Azure, ainsi qu’entre les machines virtuelles situées sur votre Réseau virtuel.

Pour les données au repos, Azure offre de nombreuses options de chiffrement, telles que la prise en charge d’AES-256, ce qui vous donne la possibilité de choisir le scénario de stockage de données qui répond le mieux à vos besoins. Les données peuvent être chiffrées automatiquement lors de leur écriture dans Stockage Azure à l’aide [de Storage Service Encryption](/azure/storage/storage-service-encryption), et le système d’exploitation et les disques de données utilisés par les machines virtuelles peuvent être chiffrés. Pour plus d’informations, consultez [les recommandations de sécurité pour les machines virtuelles Windows dans Azure](/azure/security/azure-security-disk-encryption). En outre, l’accès délégué aux objets de données dans Stockage Azure peut être accordé à l’aide de [signatures d’accès partagé](/azure/storage/storage-dotnet-shared-access-signature-part-1). Azure fournit également le chiffrement des données au repos à l’aide de [Transparent Data Encryption pour Azure SQL Base de données et Data Warehouse](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Pour plus d’informations sur le chiffrement dans Azure, consultez [la vue d’ensemble du chiffrement Azure](/azure/security/security-azure-encryption-overview) et [Azure Data Encryption-at-Rest](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Azure Disk Encryption

Azure Disk Encryption vous permet de chiffrer vos disques de machine virtuelle IaaS (Infrastructure as a Service) Windows et Linux. Azure Disk Encryption tire parti de la fonctionnalité BitLocker de Windows et de la fonctionnalité DM-Crypt de Linux pour fournir un chiffrement au niveau du volume pour le système d’exploitation et les disques de données. Il garantit également que toutes les données sur les disques de machine virtuelle sont chiffrées au repos dans votre stockage Azure. Azure Disk Encryption est intégré à Azure Key Vault pour vous aider à contrôler, gérer et auditer l’utilisation des clés de chiffrement et des secrets.

Pour plus d’informations, consultez [les recommandations de sécurité pour les machines virtuelles Windows dans Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Azure Storage Service Encryption

Avec [Azure Storage Service Encryption](/azure/storage/storage-service-encryption), Stockage Azure chiffre automatiquement les données avant de les conserver dans le stockage et déchiffre les données avant leur récupération. Les processus de chiffrement, de déchiffrement et de gestion des clés sont totalement transparents pour les utilisateurs. Azure Storage Service Encryption peut être utilisé pour [Stockage Blob Azure](https://azure.microsoft.com/services/storage/blobs/) et [Azure Files](https://azure.microsoft.com/services/storage/files/). Vous pouvez également utiliser des clés de chiffrement gérées par Microsoft avec Azure Storage Service Encryption ou utiliser vos propres clés de chiffrement. (Pour plus d’informations sur l’utilisation de vos propres clés, consultez [Storage Service Encryption à l’aide de clés gérées par le client dans Azure Key Vault](/azure/storage/common/storage-service-encryption-customer-managed-keys). Pour plus d’informations sur l’utilisation de clés gérées par Microsoft, consultez [Storage Service Encryption pour les données au repos](/azure/storage/storage-service-encryption).) En outre, vous pouvez automatiser l’utilisation du chiffrement. Par exemple, vous pouvez activer ou désactiver programmatiquement Storage Service Encryption sur un compte de stockage à l’aide de [l’API REST du fournisseur de ressources de stockage Azure](/rest/api/storagerp/), de la [bibliothèque cliente du fournisseur de ressources de stockage pour .NET](/dotnet/api/overview/azure/storage), [Azure PowerShell](/powershell/azureps-cmdlets-docs) ou [Azure CLI](/azure/storage/storage-azure-cli).

Certains services Microsoft 365 utilisent Azure pour stocker des données. Par exemple, SharePoint Online et OneDrive Entreprise stocker des données dans le stockage Blob Azure, et Microsoft Teams stocke les données de son service de conversation dans des tables, des objets blob et des files d’attente. En outre, la fonctionnalité Gestionnaire de conformité dans le portail de conformité Microsoft Purview stocke les données entrées par le client qui sont stockées sous forme chiffrée dans [Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest), une base de données PaaS (Platform as a Service), distribuée à l’échelle mondiale et multimodal. Azure Storage Service Encryption chiffre les données stockées dans le stockage Blob Azure et dans des tables, et Azure Disk Encryption chiffre les données dans les files d’attente, ainsi que les disques de machine virtuelle Windows et IaaS pour fournir le chiffrement en volume pour le système d’exploitation et le disque de données. La solution garantit que toutes les données sur les disques de machine virtuelle sont chiffrées au repos dans votre stockage Azure. [Le chiffrement au repos dans Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest) est implémenté à l’aide de plusieurs technologies de sécurité, notamment des systèmes de stockage de clés sécurisés, des réseaux chiffrés et des API de chiffrement.

## <a name="azure-key-vault"></a>Azure Key Vault

La gestion sécurisée des clés n’est pas seulement essentielle aux meilleures pratiques de chiffrement ; il est également essentiel pour protéger les données dans le cloud. [Azure Key Vault](/azure/key-vault/key-vault-whatis) vous permet de chiffrer les clés et les petits secrets tels que les mots de passe qui utilisent des clés stockées dans des modules de sécurité matériels (HSM). Azure Key Vault est la solution recommandée par Microsoft pour gérer et contrôler l’accès aux clés de chiffrement utilisées par les services cloud. Les autorisations d’accès aux clés peuvent être attribuées aux services ou aux utilisateurs disposant de comptes Azure Active Directory. Azure Key Vault évite aux organisations de devoir configurer, corriger et gérer des modules HSM et des logiciels de gestion des clés. Avec Azure Key Vault, Microsoft ne voit jamais vos clés et vos applications n’y ont pas accès directement ; vous conservez le contrôle. Vous pouvez également importer ou générer des clés dans des modules HSM. Les organisations qui disposent d’un abonnement qui inclut Azure Information Protection peuvent configurer leur locataire Azure Information Protection pour utiliser une clé gérée par le client [ByOK (Bring Your Own Key](/information-protection/plan-design/byok-price-restrictions)) et [consigner son utilisation](/information-protection/deploy-use/log-analyze-usage).
