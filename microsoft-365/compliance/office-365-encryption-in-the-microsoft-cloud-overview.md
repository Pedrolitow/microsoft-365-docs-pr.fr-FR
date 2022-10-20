---
title: Chiffrement dans Microsoft Cloud
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
- purview-compliance
- tier3
- Strat_O365_Enterprise
description: Dans cet article, lisez une vue d’ensemble des différentes formes de chiffrement utilisées pour sécuriser les données client dans le cloud Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: bc28109558cd48b8d78081b73c192f84910cc9ef
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68644992"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Chiffrement dans Microsoft Cloud

Les données client dans les services cloud d’entreprise de Microsoft sont protégées par plusieurs technologies et processus, notamment diverses formes de chiffrement. (Les données client de ce document incluent Exchange Online contenu de boîte aux lettres, le corps du courrier électronique, les entrées de calendrier et le contenu des pièces jointes de messagerie, et, le cas échéant, Skype Entreprise contenu), le contenu du site SharePoint Online et les fichiers stockés dans les sites, ainsi que les fichiers chargés dans OneDrive Entreprise ou Skype Entreprise.) Microsoft utilise plusieurs méthodes de chiffrement, protocoles et chiffrements sur ses produits et services pour fournir un chemin d’accès sécurisé aux données client à parcourir nos services cloud et pour protéger la confidentialité des données client stockées dans nos services cloud. Microsoft utilise certains des protocoles de chiffrement les plus forts et les plus sécurisés disponibles pour fournir des obstacles à l’accès non autorisé aux données client. Une gestion appropriée des clés est également un élément essentiel des meilleures pratiques de chiffrement, et Microsoft s’assure que toutes les clés de chiffrement gérées par Microsoft sont correctement sécurisées.

Les données client stockées dans les services cloud d’entreprise de Microsoft sont protégées à l’aide d’une ou plusieurs formes de chiffrement. (La validation de notre stratégie de chiffrement et de son application est vérifiée indépendamment par plusieurs auditeurs tiers, et des rapports de ces audits sont disponibles sur le [portail d’approbation](https://aka.ms/stp) de services.)

Microsoft fournit des technologies côté service qui chiffrent les données client au repos et en transit. Par exemple, pour les données client au repos, Microsoft Azure utilise [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) et [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt), et Microsoft 365 utilise BitLocker, [Azure Storage Service Encryption](/azure/), [Distributed Key Manager](./exchange-online-secures-email-secrets.md) (DKM) et le chiffrement de service Microsoft 365. Pour les données client en transit, Azure, Office 365, le support commercial Microsoft, Microsoft Dynamics 365, Microsoft Power BI et Visual Studio Team Services utilisent des protocoles de transport sécurisé standard, tels que IPsec (Internet Protocol Security) et TLS (Transport Layer Security), entre les centres de données Microsoft et entre les appareils utilisateur et les centres de données Microsoft.

Outre le niveau de base de sécurité de chiffrement fourni par Microsoft, nos services cloud incluent également des options de chiffrement que vous pouvez gérer. Par exemple, vous pouvez activer le chiffrement pour le trafic entre leurs machines virtuelles Azure et leurs utilisateurs. Avec [les réseaux virtuels Azure](https://azure.microsoft.com/services/virtual-network/), vous pouvez utiliser le protocole IPsec standard pour chiffrer le trafic entre votre passerelle VPN d’entreprise et Azure. Vous pouvez également chiffrer le trafic entre les machines virtuelles de votre réseau virtuel. En outre, les [nouvelles fonctionnalités de chiffrement des messages Office 365](set-up-new-message-encryption-capabilities.md) vous permettent d’envoyer des messages chiffrés à n’importe qui.

Conformément à la norme de sécurité opérationnelle de l’infrastructure à clé publique, qui est un composant de la stratégie [de sécurité Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers), Microsoft utilise les fonctionnalités de chiffrement incluses dans le système d’exploitation Windows pour les certificats et les mécanismes d’authentification. Ces mécanismes incluent l’utilisation de modules de chiffrement conformes à la norme FIPS ( [Federal Information Processing Standards](https://csrc.nist.gov/publications/PubsFIPS.html) ) 140-2 du gouvernement des États-Unis. Vous pouvez rechercher les numéros de certificat NIST appropriés pour Microsoft à l’aide du [CMVP du programme de validation de module de chiffrement](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [REMARQUE] Pour accéder à la stratégie de sécurité Microsoft en tant que ressource, vous devez vous connecter à l’aide de votre compte professionnel ou scolaire. Si vous n’avez pas encore d’abonnement, [vous pouvez vous inscrire à un essai gratuit](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 est une norme conçue spécifiquement pour valider les modules de produit qui implémentent le chiffrement plutôt que les produits qui les utilisent. Les modules de chiffrement implémentés au sein d’un service peuvent être certifiés comme répondant aux exigences en matière de puissance de hachage, de gestion des clés, et ainsi de suite. Les modules de chiffrement et les chiffrements utilisés pour protéger la confidentialité, l’intégrité ou la disponibilité des données dans les services cloud de Microsoft répondent à la norme FIPS 140-2.

Microsoft certifie les modules de chiffrement sous-jacents utilisés dans nos services cloud avec chaque nouvelle version du système d’exploitation Windows :

- Azure et Azure U.S. Government
- Dynamics 365 et Dynamics 365 U.S. Governement
- Office 365, Office 365 U.S. Government, Office 365 U.S. Government Defense

Le chiffrement des données client au repos est fourni par plusieurs technologies côté service, notamment BitLocker, DKM, Azure Storage Service Encryption et le chiffrement des services dans Exchange Online, Skype Entreprise, OneDrive Entreprise et SharePoint Online. Office 365 chiffrement de service inclut une option permettant d’utiliser des clés de chiffrement gérées par le client stockées dans Azure Key Vault. Cette option de clé gérée par le client, appelée [Clé client](./customer-key-overview.md), est disponible pour Exchange Online, SharePoint Online, Skype Entreprise et OneDrive Entreprise.

Pour les données client en transit, tous les serveurs Office 365 négocient des sessions sécurisées à l’aide de TLS par défaut avec les machines clientes pour sécuriser les données client. Par exemple, Office 365 négocie des sessions sécurisées pour Skype Entreprise, Outlook et Outlook sur le web, les clients mobiles et les navigateurs web.

(Tous les serveurs orientés client négocient vers TLS 1.2 par défaut.)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="related-links"></a>Liens connexes

- [Chiffrement dans Azure](office-365-azure-encryption.md)
- [BitLocker et Distributed Key Manager (DKM) pour le chiffrement](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Chiffrement du service Office 365](office-365-service-encryption.md)
- [chiffrement Office 365 pour Skype Entreprise, OneDrive Entreprise, SharePoint Online et Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Chiffrement des données en transit](/compliance/assurance/assurance-encryption-in-transit)
- [Fonctionnalités de chiffrement gérées par le client](office-365-customer-managed-encryption-features.md)
- [Protections et les risques de chiffrement](office-365-encryption-risks-and-protections.md)
- [Chiffrement dans Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)
