---
title: Chiffrement dans Microsoft Cloud
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
description: Dans cet article, lisez une vue d’ensemble des différentes formes de chiffrement utilisées pour assurer la sécurité des données client dans le cloud Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 20236e67432ad5bc7e837b91590387355022ccb5
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727575"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Chiffrement dans Microsoft Cloud

Les données client dans les services cloud d’entreprise de Microsoft sont protégées par plusieurs technologies et processus, y compris diverses formes de chiffrement. (Les données client de ce document incluent le contenu de la boîte aux lettres Exchange Online, le corps du courrier électronique, les entrées de calendrier et le contenu des pièces jointes, et le cas échéant, le contenu skype entreprise), le contenu du site SharePoint Online et les fichiers stockés dans les sites, ainsi que les fichiers téléchargés vers OneDrive Entreprise ou Skype Entreprise.) Microsoft utilise plusieurs méthodes, protocoles et chiffrements de chiffrement dans ses produits et services pour fournir un chemin d’accès sécurisé aux données client pour les déplacer dans nos services cloud et protéger la confidentialité des données client stockées dans nos services cloud. Microsoft utilise certains des protocoles de chiffrement les plus forts et les plus sécurisés disponibles pour empêcher tout accès non autorisé aux données client. Une gestion appropriée des clés est également un élément essentiel des meilleures pratiques de chiffrement, et Microsoft s’assure que toutes les clés de chiffrement gérées par Microsoft sont correctement sécurisées.

Les données client stockées dans les services cloud d’entreprise de Microsoft sont protégées à l’aide d’une ou plusieurs formes de chiffrement. (La validation de notre stratégie de chiffrement et de son application est vérifiée indépendamment par plusieurs auditeurs tiers et des rapports de ces audits sont disponibles sur le portail d’approbation de [services.)](https://aka.ms/stp)

Microsoft fournit des technologies côté service qui chiffrent les données client au repos et en transit. Par exemple, pour les données client au repos, Microsoft Azure utilise [BitLocker](https://docs.microsoft.com/windows/device-security/bitlocker/bitlocker-overview) et [DM-Crypt,](https://en.wikipedia.org/wiki/Dm-crypt)et Microsoft 365 utilise BitLocker, le chiffrement du service de stockage [Azure,](https://docs.microsoft.com/azure/)le gestionnaire de clés distribuées [](https://docs.microsoft.com/microsoft-365/compliance/exchange-online-secures-email-secrets) (DKM) et le chiffrement du service Microsoft 365. Pour les données client en transit, Azure, Office 365, le Support commercial Microsoft, Microsoft Dynamics 365, Microsoft Power BI et Visual Studio Team Services utilisent des protocoles de transport sécurisés standard, tels que IPsec (Internet Protocol Security) et TLS (Transport Layer Security), entre les centres de données Microsoft et entre les appareils utilisateur et les centres de données Microsoft.

En plus du niveau de base de sécurité de chiffrement fourni par Microsoft, nos services cloud incluent également des options de chiffrement que vous pouvez gérer. Par exemple, vous pouvez activer le chiffrement pour le trafic entre leurs machines virtuelles Azure et leurs utilisateurs. Avec [Azure Virtual Networks,](https://azure.microsoft.com/services/virtual-network/)vous pouvez utiliser le protocole IPsec standard pour chiffrer le trafic entre votre passerelle VPN d’entreprise et Azure. Vous pouvez également chiffrer le trafic entre les VM de votre réseau virtuel. En outre, les nouvelles fonctionnalités de chiffrement de messages [Office 365](set-up-new-message-encryption-capabilities.md) vous permettent d’envoyer des messages chiffrés à tout le monde.

En suivant la norme de sécurité opérationnelle de l’infrastructure à clé publique, qui est un composant de la stratégie de sécurité [Microsoft,](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers)Microsoft utilise les fonctionnalités de chiffrement incluses dans le système d’exploitation Windows pour les certificats et les mécanismes d’authentification. Ces mécanismes incluent l’utilisation de modules de chiffrement qui répondent à la norme FIPS [(Federal Information Processing Standards)](https://csrc.nist.gov/publications/PubsFIPS.html) 140-2 du gouvernement américain. Vous pouvez rechercher les numéros de certificat NIST pertinents pour Microsoft à l’aide du CMVP du programme de validation de module de [chiffrement.](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search)

> [REMARQUE] Pour accéder à la stratégie de sécurité Microsoft en tant que ressource, vous devez vous inscrire à l’aide de votre compte scolaire ou scolaire. Si vous n’avez pas encore d’abonnement, vous pouvez vous [inscrire à un essai gratuit.](https://servicetrust.microsoft.com/Home/TrialSubscriptions)

FIPS 140-2 est une norme conçue spécifiquement pour valider les modules de produit qui implémentent le chiffrement plutôt que les produits qui les utilisent. Les modules de chiffrement implémentés au sein d’un service peuvent être certifiés pour répondre aux exigences de force de hachage, de gestion des clés, etc. Les modules et chiffrements de chiffrement utilisés pour protéger la confidentialité, l’intégrité ou la disponibilité des données dans les services cloud de Microsoft respectent la norme FIPS 140-2.

Microsoft certifie les modules de chiffrement sous-jacents utilisés dans nos services cloud à chaque nouvelle version du système d’exploitation Windows :

- Azure et Azure U.S. Government
- Dynamics 365 et Dynamics 365 U.S. Governement
- Office 365, Office 365 U.S. Government, Office 365 U.S. Government Defense

Le chiffrement des données client au repos est fourni par plusieurs technologies côté service, notamment BitLocker, DKM, le chiffrement du service de stockage Azure et le chiffrement de service dans Exchange Online, Skype Entreprise, OneDrive Entreprise et SharePoint Online. Le chiffrement du service Office 365 inclut une option d’utilisation des clés de chiffrement gérées par le client qui sont stockées dans Azure Key Vault. Cette option de clé gérée par le client, appelée Clé [client,](https://docs.microsoft.com/microsoft-365/compliance/customer-key-overview)est disponible pour Exchange Online, SharePoint Online, Skype Entreprise et OneDrive Entreprise.

Pour les données client en transit, tous les serveurs Office 365 négocient des sessions sécurisées à l’aide de TLS par défaut avec les ordinateurs clients pour sécuriser les données client. Par exemple, Office 365 négociera des sessions sécurisées vers Skype Entreprise, Outlook et Outlook sur le web, les clients mobiles et les navigateurs web.

(Tous les serveurs clients négocient par défaut vers TLS 1.2.)

## <a name="related-links"></a>Liens connexes

- [Chiffrement dans Azure](office-365-azure-encryption.md)
- [BitLocker et Distributed Key Manager (DKM) pour le chiffrement](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Chiffrement du service Office 365](office-365-service-encryption.md)
- [Chiffrement Office 365 pour Skype Entreprise, OneDrive Entreprise, SharePoint Online et Exchange Online](office-365-encryption-for-skype-onedrive-sharepoint-and-exchange.md)
- [Chiffrement des données en transit](office-365-encryption-for-data-in-transit.md)
- [Fonctionnalités de chiffrement gérées par le client](office-365-customer-managed-encryption-features.md)
- [Protections et les risques de chiffrement](office-365-encryption-risks-and-protections.md)
- [Chiffrement dans Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)
