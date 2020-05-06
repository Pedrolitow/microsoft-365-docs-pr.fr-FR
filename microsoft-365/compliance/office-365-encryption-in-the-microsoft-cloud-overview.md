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
description: Dans cet article, lisez une présentation des différentes formes de chiffrement utilisées pour conserver les données client en toute sécurité dans le Cloud Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 62353725073f5010db1a8681bebad18bc671d81f
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44031384"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Chiffrement dans Microsoft Cloud

Les données client dans les services Cloud d’entreprise de Microsoft sont protégées par diverses technologies et processus, y compris diverses formes de chiffrement. (Les données client dans ce document incluent le contenu de boîte aux lettres Exchange Online, le corps de courrier électronique, les entrées de calendrier, ainsi que le contenu des pièces jointes et, le cas échéant, le contenu Skype entreprise), le contenu de site SharePoint Online et les fichiers stockés dans les sites, ainsi que les fichiers téléchargés vers OneDrive entreprise ou Skype entreprise.) Microsoft utilise plusieurs méthodes de chiffrement, des protocoles et des chiffrements dans ses produits et services afin de fournir un chemin sécurisé aux données client afin de les transférer via nos services Cloud et de protéger la confidentialité des données client stockées dans nos services Cloud. Microsoft utilise certains des protocoles de chiffrement les plus sûrs et les plus sécurisés disponibles pour fournir des obstacles à l’accès non autorisé aux données client. La gestion des clés appropriée est également un élément essentiel des meilleures pratiques de chiffrement, et Microsoft travaille pour s’assurer que toutes les clés de chiffrement gérées par Microsoft sont correctement sécurisées.

Quelle que soit la configuration client, les données client stockées dans les services Cloud d’entreprise de Microsoft sont protégées à l’aide d’une ou plusieurs formes de chiffrement. (La validation de notre stratégie de chiffrement et son application sont vérifiées de manière indépendante par plusieurs auditeurs tiers, et les rapports de ces audits sont disponibles sur le [portail d’approbation de services](https://aka.ms/stp).)

Microsoft fournit des technologies côté service qui chiffrent les données client au repos et en transit. Par exemple, pour les données client au repos, Microsoft Azure utilise [BitLocker](https://docs.microsoft.com/windows/device-security/bitlocker/bitlocker-overview) et [DM-crypt](https://en.wikipedia.org/wiki/Dm-crypt), et Microsoft 365 utilise BitLocker, le [chiffrement de service de stockage Azure](https://azure.microsoft.com/documentation/articles/storage-service-encryption/), le [Gestionnaire de clés distribuées](https://support.office.com/article/989ba10c-f73f-4efb-ad1b-af3322e5f376) (DKM) et le chiffrement de service Microsoft 365. Pour les données client en transit, Azure, Office 365, le support commercial Microsoft, Microsoft Dynamics 365, Microsoft Power BI et Visual Studio Team Services utilisent des protocoles de transport sécurisé standard, tels que IPsec (Internet Protocol Security) et TLS (Transport Layer Security), entre les centres de données Microsoft et entre les appareils utilisateur et les centres de données Microsoft.

Outre le niveau de base de la sécurité de chiffrement fourni par Microsoft, nos services Cloud incluent également des options de chiffrement supplémentaires que vous pouvez gérer. Par exemple, vous pouvez activer le chiffrement pour le trafic entre ses machines virtuelles (VM) et leurs utilisateurs. Avec les [réseaux virtuels Azure](https://azure.microsoft.com/services/virtual-network/), vous pouvez utiliser le protocole IPSec standard pour chiffrer le trafic entre votre passerelle VPN d’entreprise et Azure, ainsi qu’entre les machines virtuelles situées sur votre réseau virtuel. En outre, les [nouvelles fonctionnalités de chiffrement de messages Office 365](set-up-new-message-encryption-capabilities.md) vous permettent d’envoyer des messages chiffrés à tous.

Conformément à la norme de sécurité opérationnelle de l’infrastructure à clé publique, qui est un composant de la [stratégie de sécurité Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers), Microsoft exploite les fonctionnalités de chiffrement incluses dans le système d’exploitation Windows pour les certificats et les mécanismes d’authentification, ce qui inclut l’utilisation de modules cryptographiques conformes à la norme FIPS ( [Federal Information Processing Standards](https://csrc.nist.gov/publications/PubsFIPS.html) ) 140-2. (Les numéros de certificat NIST appropriés pour Microsoft sont disponibles à l’adresse suivante :https://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401vend.htm.)

> Note Pour accéder à la stratégie de sécurité Microsoft en tant que ressource, vous devez vous connecter à l’aide de votre compte professionnel ou scolaire. Si vous n’avez pas encore d’abonnement, [vous pouvez vous inscrire pour obtenir une version d’évaluation gratuite](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 est une norme conçue spécifiquement pour la validation des modules de produit qui implémentent le chiffrement plutôt que les produits qui les utilisent. Les modules de chiffrement qui sont mis en œuvre au sein d’un service peuvent être certifiés conformes à la configuration requise pour la force de hachage, la gestion des clés et les autres. Toutes les fonctionnalités de chiffrement de temps sont utilisées pour protéger la confidentialité, l’intégrité ou la disponibilité des données dans les services Cloud de Microsoft, les modules et les chiffrements utilisés correspondent à la norme FIPS 140-2.

Microsoft certifie les modules de chiffrement sous-jacents utilisés dans nos services Cloud avec chaque nouvelle version du système d’exploitation Windows :

- Azure et le gouvernement des États-Unis Azure
- Dynamics 365 et Dynamics 365 U.S. Governement
- Office 365, Office 365 U.S. Government, Office 365 U.S. Government Defense

Le chiffrement des données client au repos est assuré par plusieurs technologies côté service, notamment BitLocker, DKM, le chiffrement du service de stockage Azure et le chiffrement de service dans Exchange Online, Skype entreprise, OneDrive entreprise et SharePoint Online. Le chiffrement de service Office 365 inclut une option permettant d’utiliser des clés de chiffrement gérées par le client qui sont stockées dans Azure Key Vault. Cette option de clé gérée par le client, appelée [clé client](https://support.office.com/article/f2cd475a-e592-46cf-80a3-1bfb0fa17697), est disponible pour Exchange Online, SharePoint Online, Skype entreprise et OneDrive entreprise.

Pour les données client en transit, tous les serveurs Office 365 négocient des sessions sécurisées à l’aide de TLS par défaut avec des ordinateurs clients pour sécuriser les données client.  Cela s’applique aux protocoles sur n’importe quel périphérique utilisé par les clients, tels que Skype entreprise, Outlook et Outlook sur le Web, les clients mobiles et les navigateurs Web.

(Tous les serveurs clients négocient avec TLS 1,2 par défaut, mais nous prenons également en charge la négociation vers une norme inférieure, si nécessaire.)

## <a name="related-links"></a>Liens connexes

- [Chiffrement dans Azure](office-365-azure-encryption.md)
- [BitLocker et Distributed Key Manager (DKM) pour le chiffrement](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Chiffrement du service Office 365](office-365-service-encryption.md)
- [Chiffrement Office 365 pour Skype entreprise, OneDrive entreprise, SharePoint Online et Exchange Online](office-365-encryption-for-skype-onedrive-sharepoint-and-exchange.md)
- [Chiffrement des données en transit](office-365-encryption-for-data-in-transit.md)
- [Fonctionnalités de chiffrement gérées par le client](office-365-customer-managed-encryption-features.md)
- [Protections et les risques de chiffrement](office-365-encryption-risks-and-protections.md)
- [Chiffrement dans Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)
