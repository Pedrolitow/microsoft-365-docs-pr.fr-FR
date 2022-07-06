---
title: Chiffrement dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 0a322724-08ca-43db-b69a-afbfa20484cd
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365solution-mip
- m365initiative-compliance
description: Avec Office 365, votre contenu est chiffré au repos et en transit avec le chiffrement, les protocoles et les technologies les plus puissants disponibles. Obtenez une vue d’ensemble du chiffrement dans Office 365.
ms.openlocfilehash: e26ade7021434461e72e24b7aa8176888d9c21d0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629638"
---
# <a name="encryption"></a>Chiffrement

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et d’informations. Cet article fournit une vue d’ensemble du chiffrement pour Office 365. Obtenez de l’aide sur les tâches de chiffrement telles que la configuration du chiffrement pour votre organisation et la protection par mot de passe des documents Office.
  
- Pour plus d’informations sur les certificats et les technologies comme TLS, consultez [les informations de référence techniques sur le chiffrement dans Office 365](technical-reference-details-about-encryption.md).

- Pour plus d’informations sur la configuration ou la configuration du chiffrement pour votre organisation, consultez [Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Qu’est-ce que le chiffrement et comment fonctionne-t-il dans Office 365 ?

Le processus de chiffrement encode vos données (appelées texte en clair) en texte chiffré. Contrairement au texte en clair, le texte chiffré ne peut pas être utilisé par des personnes ou des ordinateurs, sauf si le texte chiffré est déchiffré. Le déchiffrement nécessite une clé de chiffrement dont disposent uniquement les utilisateurs autorisés. Le chiffrement permet de s’assurer que seuls les destinataires autorisés peuvent déchiffrer votre contenu. Le contenu inclut des fichiers, des e-mails, des entrées de calendrier, et ainsi de suite.
  
Le chiffrement en soi n’empêche pas l’interception de contenu. Le chiffrement fait partie d’une stratégie de protection des informations plus large pour votre organisation. En utilisant le chiffrement, vous vous assurez que seules les parties autorisées peuvent utiliser les données chiffrées.
  
Vous pouvez avoir plusieurs couches de chiffrement en place en même temps. Par exemple, vous pouvez chiffrer les messages électroniques ainsi que les canaux de communication par le biais desquels votre courrier électronique est transmis. Avec Office 365, vos données sont chiffrées au repos et en transit, à l’aide de plusieurs protocoles de chiffrement forts et de technologies qui incluent TLS/SSL (Transport Layer Security/Secure Sockets Layer), IPSec (Internet Protocol Security) et Advanced Encryption Standard (AES).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Chiffrement des données au repos et des données en transit

 **Les exemples de données au repos** incluent les fichiers que vous avez chargés dans une bibliothèque SharePoint, les données Project Online, les documents que vous avez chargés lors d’une réunion Skype Entreprise, les messages électroniques et les pièces jointes que vous avez stockés dans des dossiers de votre boîte aux lettres et les fichiers que vous avez chargés dans OneDrive Entreprise.
  
 **Les messages électroniques** qui sont en cours de remise ou les conversations qui ont lieu lors d’une réunion en ligne sont des exemples de données en transit. Dans Office 365, les données sont en transit chaque fois que l’appareil d’un utilisateur communique avec un serveur Microsoft ou lorsqu’un serveur Microsoft communique avec un autre serveur.
  
Avec Office 365, plusieurs couches et types de chiffrement fonctionnent ensemble pour sécuriser vos données. Le tableau suivant contient quelques exemples, avec des liens vers des informations supplémentaires.
  
|**Types de contenu**|**Technologies de chiffrement**|**Ressources pour en savoir plus**|
|:-----|:-----|:-----|
|Fichiers sur un appareil. Ces fichiers peuvent inclure des messages électroniques enregistrés dans un dossier, des documents Office enregistrés sur un ordinateur, une tablette ou un téléphone, ou des données enregistrées dans le cloud Microsoft.  <br/> |BitLocker dans les centres de données Microsoft. BitLocker peut également être utilisé sur des ordinateurs clients, tels que des ordinateurs windows et des tablettes  <br/> Gestionnaire de clés distribuées (DKM) dans les centres de données Microsoft  <br/> Clé client pour Microsoft 365  <br/> |[Windows IT Center : BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Centre de gestion de la confidentialité Microsoft : chiffrement](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Série de contrôles de sécurité cloud : Chiffrement des données au repos](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Procédure de sécurisation des informations confidentielles dans votre courrier électronique dans Exchange Online](exchange-online-secures-email-secrets.md) <br/> [Chiffrement du service avec la clé client](customer-key-overview.md) <br/> |
|Fichiers en transit entre les utilisateurs. Ces fichiers peuvent inclure des documents Office ou des éléments de liste SharePoint partagés entre les utilisateurs.  <br/> |TLS pour les fichiers en transit  <br/> |[Chiffrement de données dans OneDrive Entreprise et SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype Entreprise Online : sécurité et archivage](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|E-mail en transit entre les destinataires. Cet e-mail inclut les e-mails hébergés par Exchange Online.  <br/> |Chiffrement de messages Microsoft Purview avec Azure Rights Management, S/MIME et TLS pour les e-mails en transit  <br/> |[Chiffrement des messages](ome.md) <br/> [Chiffrement du courrier électronique dans Office 365](email-encryption.md) <br/> [Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie dans Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Conversations, messages et fichiers en transit entre les destinataires à l’aide de Microsoft Teams. <br/> |Teams utilise TLS et MTLS pour chiffrer les messages instantanés. Le trafic multimédia est chiffré à l’aide du protocole SRTP (Secure RTP). Teams utilise des algorithmes conformes FIPS (Federal Information Processing Standard) pour les échanges de clés de chiffrement. <br/> |[Chiffrement pour Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Que se passe-t-il si j’ai besoin d’un contrôle accru sur le chiffrement pour répondre aux exigences de sécurité et de conformité ?

Microsoft 365 fournit des solutions gérées par Microsoft pour le chiffrement de volume, le chiffrement de fichiers et le chiffrement de boîte aux lettres dans Office 365. En outre, Microsoft fournit des solutions de chiffrement que vous pouvez gérer et contrôler. Ces solutions de chiffrement sont basées sur Azure.
  
Pour en savoir plus, consultez les ressources suivantes :
  
- [Qu’est-ce que Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)

- [Activer Rights Management dans le Centre d’administration](../enterprise/activate-rms-in-microsoft-365.md)

- [Configurer la gestion des droits relatifs à l’information dans le centre d’administration SharePoint](set-up-irm-in-sp-admin-center.md)

- [Chiffrement de service avec la clé client Microsoft Purview](customer-key-overview.md)

- [Chiffrement à double clé](double-key-encryption.md)

## <a name="how-do-i"></a>Procédures

|**Pour effectuer cette tâche**|**Voir ces ressources**|
|:-----|:-----|
|Configurer le chiffrement pour mon organisation|[Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md)|
|Afficher des détails sur les certificats, les technologies et les suites de chiffrement TLS|[Détails techniques sur le chiffrement](technical-reference-details-about-encryption.md)|
|Utiliser des messages chiffrés sur un appareil mobile|[Afficher les messages chiffrés sur votre appareil Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)[Afficher les messages chiffrés sur votre iPhone ou iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Chiffrez un document à l’aide de la protection par mot de passe. (La protection par mot de passe n’est pas prise en charge dans un navigateur. Utilisez les versions de bureau de Word, Excel et PowerPoint pour la protection par mot de passe.) |[Ajoutez ou supprimez une protection dans votre document, classeur ou présentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Choisissez une section **Ajouter une protection** , puis consultez **Chiffrer avec mot de passe**.|
|Supprimer le chiffrement d’un document|[Ajoutez ou supprimez une protection dans votre document, classeur ou présentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Choisissez une section **Supprimer la protection** , puis consultez **Supprimer le chiffrement de mot de passe**.  |

## <a name="related-topics"></a>Rubriques connexes

[Planifier les fonctionnalités de sécurité et de protection des informations de Microsoft 365](plan-for-security-and-compliance.md)

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](/office365/admin/security-and-compliance/secure-your-business-data)

[Microsoft Stream flux de chiffrement et de lecture au niveau de la vidéo](/stream/network-overview#video-level-encryption-and-playback-flow)
