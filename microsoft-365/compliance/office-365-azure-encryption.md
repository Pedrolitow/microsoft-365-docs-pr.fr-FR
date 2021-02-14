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
ms.openlocfilehash: a90f66ed7288d84785becbb4cd25c803ccf4fdbe
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48198327"
---
# <a name="encryption-in-azure"></a>Chiffrement dans Azure

Les protections technologiques dans Azure, telles que les communications chiffrées et les processus opérationnels, contribuent à sécuriser vos données. Vous avez également la possibilité d’implémenter des fonctionnalités de chiffrement supplémentaires et de gérer vos propres clés de chiffrement. Quelle que soit la configuration du client, Microsoft applique le chiffrement pour protéger les données client dans Azure. Microsoft vous permet également de contrôler vos données hébergées dans Azure via une gamme de technologies avancées pour chiffrer, contrôler et gérer les clés de chiffrement, ainsi que contrôler et auditer l’accès aux données. En outre, Le stockage Azure fournit un ensemble complet de fonctionnalités de sécurité qui permettent aux développeurs de créer des applications sécurisées.

Azure offre de nombreux mécanismes de protection des données lors de son déplacement d’un emplacement à un autre. Microsoft utilise TLS pour protéger les données lorsqu’il se déplace entre les services cloud et les clients. Les centres de données de Microsoft négocient une connexion TLS avec les systèmes clients qui se connectent aux services Azure. Perfect Forward Secrecy (PFS) protège les connexions entre les systèmes clients des clients et les services cloud de Microsoft par des clés uniques. Les connexions utilisent également des longueurs de clé de chiffrement 2 048 bits basées sur RSA. Cette combinaison complique l’interception et l’accès aux données en transit.

Les données peuvent être sécurisées en transit entre une application et Azure à l’aide du chiffrement côté [client,](https://docs.microsoft.com/azure/storage/storage-client-side-encryption)HTTPS ou SMB 3.0. Vous pouvez activer le chiffrement pour le trafic entre vos propres machines virtuelles (VM) et vos utilisateurs. Avec [Azure Virtual Networks,](https://azure.microsoft.com/services/virtual-network/)vous pouvez utiliser le protocole IPsec standard pour chiffrer le trafic entre votre passerelle VPN d’entreprise et Azure, ainsi qu’entre les VM situées sur votre réseau virtuel.

Pour les données au repos, Azure offre de nombreuses options de chiffrement, telles que la prise en charge d’AES-256, vous offrant ainsi la possibilité de choisir le scénario de stockage de données qui répond le mieux à vos besoins. Les données peuvent être automatiquement chiffrées lorsqu’elles sont écrites dans le stockage Azure à l’aide du chiffrement du [service](https://docs.microsoft.com/azure/storage/storage-service-encryption)de stockage, et les disques de système d’exploitation et de données utilisés par les ordinateurs virtuels peuvent être chiffrés. Pour plus d’informations, voir [recommandations en matière de sécurité pour les machines virtuelles Windows dans Azure.](https://docs.microsoft.com/azure/security/azure-security-disk-encryption) En outre, l’accès délégué aux objets de données dans le stockage Azure peut être accordé à l’aide de [signatures d’accès partagé.](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) Azure fournit également le chiffrement des données au repos à l’aide du chiffrement transparent des données [pour Azure SQL Database et Data Warehouse](https://docs.microsoft.com/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Pour plus d’informations sur le chiffrement dans Azure, voir [Azure Encryption overview](https://docs.microsoft.com/azure/security/security-azure-encryption-overview) et Azure Data [Encryption-at-Rest](https://docs.microsoft.com/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Chiffrement de disque Azure

Le chiffrement de disque Azure vous permet de chiffrer vos disques IaaS (Windows and Linux Infrastructure as a Service) VM. Le chiffrement de disque Azure tire parti de la fonctionnalité BitLocker de Windows et de la fonctionnalité DM-Crypt de Linux pour fournir un chiffrement au niveau du volume pour le système d’exploitation et les disques de données. Il garantit également que toutes les données sur les disques de l’ordinateur virtuel sont chiffrées au repos dans votre stockage Azure. Le chiffrement de disque Azure est intégré à Azure Key Vault pour vous aider à contrôler, gérer et auditer l’utilisation des clés de chiffrement et des clés secrètes.

Pour plus d’informations, voir recommandations en matière de sécurité pour les [machines virtuelles Windows dans Azure.](https://docs.microsoft.com/azure/virtual-machines/windows/security-recommendations)

## <a name="azure-storage-service-encryption"></a>Chiffrement du service de stockage Azure

Avec [le chiffrement](https://docs.microsoft.com/azure/storage/storage-service-encryption)du service de stockage Azure, le stockage Azure chiffre automatiquement les données avant de les rendre persistantes dans le stockage et déchiffre les données avant la récupération. Les processus de chiffrement, de déchiffrement et de gestion des clés sont totalement transparents pour les utilisateurs. Le chiffrement du service de stockage Azure peut être utilisé pour le stockage [Blob Azure](https://azure.microsoft.com/services/storage/blobs/) et [les fichiers Azure.](https://azure.microsoft.com/services/storage/files/) Vous pouvez également utiliser des clés de chiffrement gérées par Microsoft avec le chiffrement du service de stockage Azure, ou vous pouvez utiliser vos propres clés de chiffrement. (Pour plus d’informations sur l’utilisation de vos propres clés, voir [Chiffrement](https://docs.microsoft.com/azure/storage/common/storage-service-encryption-customer-managed-keys)du service de stockage à l’aide de clés gérées par le client dans Azure Key Vault . Pour plus d’informations sur l’utilisation des clés gérées par Microsoft, voir Chiffrement du service de stockage [pour les données au repos.)](https://docs.microsoft.com/azure/storage/storage-service-encryption) En outre, vous pouvez automatiser l’utilisation du chiffrement. Par exemple, vous pouvez activer ou désactiver par programme le chiffrement du service de stockage sur un compte de stockage à l’aide de l’API REST du fournisseur de ressources de stockage [Azure,](https://msdn.microsoft.com/library/azure/mt163683.aspx)de la bibliothèque cliente du fournisseur de ressources de stockage pour [.NET,](https://msdn.microsoft.com/library/azure/mt131037.aspx) [Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs)ou de l’interface de ligne de ligne de base [Azure.](https://docs.microsoft.com/azure/storage/storage-azure-cli)

Certains services Microsoft 365 utilisent Azure pour stocker des données. Par exemple, SharePoint Online et OneDrive Entreprise stockent des données dans le stockage Blob Azure, et Microsoft Teams stocke les données de son service de conversation dans des tables, des objets blob et des files d’attente. En outre, la fonctionnalité Gestionnaire de conformité dans le Centre de conformité Microsoft 365 stocke les données entrées par le client qui sont stockées sous forme chiffrée dans [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/database-encryption-at-rest), une base de données PaaS (Platform as a Service), distribuée globalement et à modèles multiples. Le chiffrement du service de stockage Azure chiffre les données stockées dans le stockage Blob Azure et dans les tables, et le chiffrement de disque Azure chiffre les données des files d’attente, ainsi que les disques des ordinateurs virtuels Windows et IaaS pour fournir le chiffrement de volume pour le système d’exploitation et le disque de données. La solution garantit que toutes les données sur les disques de l’ordinateur virtuel sont chiffrées au repos dans votre stockage Azure. [Le chiffrement au repos dans Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/database-encryption-at-rest) est implémenté à l’aide de plusieurs technologies de sécurité, notamment des systèmes de stockage de clés sécurisés, des réseaux chiffrés et des API de chiffrement.

## <a name="azure-key-vault"></a>Azure Key Vault

La gestion des clés sécurisées n’est pas seulement essentielle aux meilleures pratiques de chiffrement . il est également essentiel pour la protection des données dans le cloud. [Azure Key Vault vous](https://docs.microsoft.com/azure/key-vault/key-vault-whatis) permet de chiffrer des clés et de petites clés secrètes, telles que des mots de passe qui utilisent des clés stockées dans des modules de sécurité matérielle (HSM). Azure Key Vault est la solution recommandée par Microsoft pour gérer et contrôler l’accès aux clés de chiffrement utilisées par les services cloud. Les autorisations d’accès aux clés peuvent être attribuées à des services ou à des utilisateurs ayant des comptes Azure Active Directory. Azure Key Vault décharge les organisations de la nécessité de configurer, de mettre à jour et de gérer des HSM et des logiciels de gestion des clés. Avec Azure Key Vault, Microsoft ne voit jamais vos clés et les applications n’y ont pas un accès direct ; vous maintenez le contrôle. Vous pouvez également importer ou générer des clés dans des HSM. Les organisations qui ont un abonnement qui inclut Azure Information Protection peuvent configurer leur client Azure Information Protection pour utiliser une clé gérée par le client [Apportez](https://docs.microsoft.com/information-protection/plan-design/byok-price-restrictions) votre propre clé (BYOK) et enregistrer [son utilisation.](https://docs.microsoft.com/information-protection/deploy-use/log-analyze-usage)
