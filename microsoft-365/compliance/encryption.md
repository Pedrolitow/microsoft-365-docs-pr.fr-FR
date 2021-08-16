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
localization_priority: Normal
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
ms.openlocfilehash: 1dcfb16c08eae1cddde10f250093df9ffc43cbc11944745c96e38e3ff0279670
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53900062"
---
# <a name="encryption"></a>Chiffrement

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et des informations. Cet article fournit une vue d’ensemble du chiffrement pour Office 365. Obtenez de l’aide sur les tâches de chiffrement, telles que la façon de configurer le chiffrement pour votre organisation et la protection par mot de passe Office documents.
  
- Pour plus d’informations sur les certificats et les technologies telles que TLS, voir [détails](technical-reference-details-about-encryption.md)de référence technique sur le chiffrement dans Office 365 .

- Pour plus d’informations sur la configuration ou la configuration du chiffrement pour votre organisation, voir Configurer le chiffrement [dans Office 365 Entreprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Qu’est-ce que le chiffrement et comment fonctionne-t-il dans Office 365 ?

Le processus de chiffrement code vos données (appelées texte brut) en texte chiffré. Contrairement au texte brut, le texte chiffré ne peut pas être utilisé par des personnes ou des ordinateurs, sauf si le texte chiffré est déchiffré. Le déchiffrement nécessite une clé de chiffrement dont seuls les utilisateurs autorisés ont besoin. Le chiffrement permet de s’assurer que seuls les destinataires autorisés peuvent déchiffrer votre contenu. Le contenu inclut des fichiers, des messages électroniques, des entrées de calendrier, etc.
  
Le chiffrement seul n’empêche pas l’interception du contenu. Le chiffrement fait partie d’une stratégie de protection des informations plus importante pour votre organisation. Le chiffrement vous permet de vous assurer que seules les parties autorisées peuvent utiliser les données chiffrées.
  
Vous pouvez avoir plusieurs couches de chiffrement en place en même temps. Par exemple, vous pouvez chiffrer les messages électroniques, ainsi que les canaux de communication via lesquels vos messages électroniques circulent. Avec Office 365, vos données sont chiffrées au repos et en transit, à l’aide de plusieurs protocoles et technologies de chiffrement forts, notamment TLS/SSL (Transport Layer Security/Secure Sockets Layer), IPSec (Internet Protocol Security) et AES (Advanced Encryption Standard).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Chiffrement des données au repos et des données en transit

  Parmi les exemples de données au repos figurent les fichiers que vous avez téléchargés dans une bibliothèque SharePoint, les données Project Online, les documents que vous avez téléchargés lors d’une réunion Skype Entreprise, les messages électroniques et les pièces jointes que vous avez stockés dans des dossiers de votre boîte aux lettres et les fichiers que vous avez téléchargés vers OneDrive Entreprise.
  
 **Les messages électroniques** en cours de livraison ou les conversations qui ont lieu dans une réunion en ligne sont des exemples de données en transit. Dans Office 365, les données sont en transit chaque fois que l’appareil d’un utilisateur communique avec un serveur Microsoft ou lorsqu’un serveur Microsoft communique avec un autre serveur.
  
Avec Office 365, plusieurs couches et types de chiffrement fonctionnent ensemble pour sécuriser vos données. Le tableau suivant inclut quelques exemples, avec des liens vers des informations supplémentaires.
  
|**Types de contenu**|**Technologies de chiffrement**|**Ressources pour en savoir plus**|
|:-----|:-----|:-----|
|Fichiers sur un appareil. Ces fichiers peuvent inclure des messages électroniques enregistrés dans un dossier, des documents Office enregistrés sur un ordinateur, une tablette ou un téléphone, ou des données enregistrées dans le cloud Microsoft.  <br/> |BitLocker dans les centres de données Microsoft. BitLocker peut également être utilisé sur des ordinateurs clients, tels que Windows ordinateurs et tablettes  <br/> Gestionnaire de clés distribuées (DKM) dans les centres de données Microsoft  <br/> Clé client pour Microsoft 365  <br/> |[Windows Centre de l’it : BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Centre de confiance Microsoft : chiffrement](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Série de contrôles de sécurité cloud : chiffrement des données au repos](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Procédure de sécurisation des informations confidentielles dans votre courrier électronique dans Exchange Online](exchange-online-secures-email-secrets.md) <br/> [Chiffrement de service avec clé client](customer-key-overview.md) <br/> |
|Fichiers en transit entre les utilisateurs. Ces fichiers peuvent inclure des documents Office ou des SharePoint de liste partagés entre les utilisateurs.  <br/> |TLS pour les fichiers en transit  <br/> |[Chiffrement de données dans OneDrive Entreprise et SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype Entreprise En ligne : sécurité et archivage](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Courrier électronique en transit entre les destinataires. Ce courrier électronique inclut les e-mails hébergés par Exchange Online.  <br/> |chiffrement de messages Office 365 avec Azure Rights Management, S/MIME et TLS pour le courrier électronique en transit  <br/> |[Chiffrement de messages Office 365 (OME)](ome.md) <br/> [Chiffrement du courrier électronique dans Office 365](email-encryption.md) <br/> [Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie dans Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Conversations, messages et fichiers en transit entre les destinataires à l’aide Microsoft Teams. <br/> |Teams utilise TLS et MTLS pour chiffrer les messages instantanés. Le trafic multimédia est chiffré à l’aide de secure RTP (SRTP). Teams utilise des algorithmes conformes FIPS (Federal Information Processing Standard) pour les échanges de clés de chiffrement. <br/> |[Chiffrement pour Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Que se passe-t-il si j’ai besoin d’un contrôle plus élevé sur le chiffrement pour répondre aux exigences de sécurité et de conformité ?

Microsoft 365 propose des solutions gérées par Microsoft pour le chiffrement en volume, le chiffrement de fichiers et le chiffrement de boîtes aux lettres dans Office 365. En outre, Microsoft fournit des solutions de chiffrement que vous pouvez gérer et contrôler. Ces solutions de chiffrement reposent sur Azure.
  
Pour en savoir plus, consultez les ressources suivantes :
  
- [Qu’est-ce que Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)

- [Activer la Gestion des droits dans le Centre d’administration](../enterprise/activate-rms-in-microsoft-365.md)

- [Configurer la gestion des droits relatifs à l’information dans le centre d’administration SharePoint](set-up-irm-in-sp-admin-center.md)

- [Chiffrement de service avec une clé client dans Office 365](customer-key-overview.md)

- [Chiffrement à double clé pour Microsoft 365](double-key-encryption.md)

## <a name="how-do-i"></a>Procédures

|**Pour ce faire,**|**Voir ces ressources**|
|:-----|:-----|
|Configurer le chiffrement pour mon organisation  <br/> |[Configurer le chiffrement dans Office 365 Entreprise](set-up-encryption.md) <br/> |
|Afficher des détails sur les certificats, les technologies et les suites de chiffrement TLS <br/> |[Détails techniques sur le chiffrement](technical-reference-details-about-encryption.md) <br/> |
|Utiliser des messages chiffrés sur un appareil mobile  <br/> |[Afficher les messages chiffrés sur votre appareil Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) <br/> [Afficher les messages chiffrés sur iPhone ou iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf) <br/> |
|Chiffrer un document à l’aide de la protection par mot de passe  <br/><br/>  La protection par mot de passe n’est pas prise en charge dans un navigateur. Utilisez les versions de bureau de Word, Excel et PowerPoint pour la protection par mot de passe. |[Ajouter ou supprimer une protection dans votre document, votre workbook ou votre présentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826) <br/> Choisissez une section **Ajouter une protection,** puis consultez **Chiffrer avec mot de passe.**  |
|Supprimer le chiffrement d’un document  <br/> |[Ajouter ou supprimer une protection dans votre document, votre workbook ou votre présentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826) <br/> Choisissez une section **Supprimer la protection,** puis consultez **Supprimer le chiffrement de mot de passe.**  |


## <a name="related-topics"></a>Sujets connexes

[Planifier les fonctionnalités Microsoft 365 sécurité et de protection des informations](plan-for-security-and-compliance.md)

[10 principales méthodes de sécurisation des Microsoft 365 pour les plans d’entreprise](/office365/admin/security-and-compliance/secure-your-business-data)

[Chiffrement et flux de lecture au niveau de Microsoft Stream Video](/stream/network-overview#video-level-encryption-and-playback-flow)