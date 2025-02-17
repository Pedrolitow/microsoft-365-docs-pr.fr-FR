---
title: Chiffrement des e-mails dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: c0d87cbe-6d65-4c03-88ad-5216ea5564e8
ms.collection:
- purview-compliance
- tier1
- m365solution-mip
- m365initiative-compliance
- highpri
description: Comparez les options de chiffrement Microsoft 365, notamment la fonctionnalité de chiffrement des messages Office (OME), S/MIME, la gestion des droits relatifs à l’information (IRM), et découvrez le protocole TLS.
ms.openlocfilehash: df17096146308c2f391653bc5013f66128bea91a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68634693"
---
# <a name="email-encryption"></a>Chiffrement du courrier électronique

Cet article compare les options de chiffrement dans Microsoft 365, notamment la fonctionnalité de chiffrement des messages Microsoft (OME), S/MIME, la gestion des droits relatifs à l’information (IRM), et présente le protocole TLS.
  
Microsoft 365 propose plusieurs options de chiffrement pour vous aider à répondre aux besoins de votre entreprise pour la sécurité des messages électroniques. Cet article présente les trois méthodes de chiffrement de courrier électronique dans Office 365. Si vous voulez en savoir plus sur toutes les fonctionnalités de sécurité dans Office 365, visitez le [centre de gestion de la confidentialité Office 365](https://go.microsoft.com/fwlink/p/?LinkID=282470). Cet article présente les trois types de chiffrement disponibles pour aider les administrateurs Microsoft 365 à sécuriser les messages électroniques dans Microsoft 365 :
  
- Chiffrement des messages Microsoft Purview.

- S/MIME (Secure/Multipurpose Internet Mail Extension).

- Gestion des droits relatifs à l’information (IRM).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-microsoft-365-uses-email-encryption"></a>Utilisation du chiffrement d’e-mail par Microsoft 365

Encryption is the process by which information is encoded so that only an authorized recipient can decode and consume the information. Microsoft 365 uses encryption in two ways: in the service, and as a customer control. In the service, encryption is used in Microsoft 365 by default; you don't have to configure anything. For example, Microsoft 365 uses Transport Layer Security (TLS) to encrypt the connection, or session, between two servers. 
  
Voici comment fonctionne généralement le chiffrement des messages :
  
- Un message est chiffré ou transformé de texte brut en texte chiffré illisible, soit sur l’ordinateur de l’expéditeur, soit via un serveur central lorsque le message est en transit.

- Le message reste en texte chiffré tant qu’il est en transit pour qu’il ne puisse pas être lu s’il venait à être intercepté.

- Une fois que le destinataire a reçu le message, celui-ci est de nouveau transformé en texte brut lisible de l’une des deux manières suivantes :

  - L’ordinateur du destinataire utilise une clé pour déchiffrer le message, ou

  - Un serveur central déchiffre le message pour le compte du destinataire, après avoir validé l’identité du destinataire.

Pour plus d’informations sur la façon dont Microsoft 365 sécurise les communications entre des serveurs, par exemple entre des organisations dans Microsoft 365 ou entre Microsoft 365 et un serveur de messagerie approuvé en dehors de Microsoft 365, voir la rubrique décrivant [comment Exchange Online utilise le protocole TLS pour sécuriser les connexions dans Microsoft 365](exchange-online-uses-tls-to-secure-email-connections.md).
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>Comparaison des options de chiffrement des messages électroniques disponibles dans Office 365

|Technologie de chiffrement d’e-mail|![Illustration conceptuelle qui décrit OME.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![Illustration conceptuelle qui décrit IRM](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![Illustration conceptuelle qui décrit SMIME](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|De quoi s’agit-il ?|Le chiffrement des messages est un service basé sur Azure Rights Management (Azure RMS) qui vous permet d’envoyer des messages chiffrés à des personnes internes ou externes à votre organisation, quelle que soit l’adresse e-mail de destination (Gmail, Yahoo! Mail, Outlook.com, etc.). <br/> As an admin, you can set up transport rules that define the conditions for encryption. When a user sends a message that matches a rule, encryption is applied automatically. <br/> To view encrypted messages, recipients can either get a one-time passcode, sign in with a Microsoft account, or sign in with a work or school account associated with Office 365. Recipients can also send encrypted replies. They don't need a Microsoft 365 subscription to view encrypted messages or send encrypted replies.|IRM is an encryption solution that also applies usage restrictions to email messages. It helps prevent sensitive information from being printed, forwarded, or copied by unauthorized people. <br/> Les fonctionnalités IRM dans Microsoft 365 utilisent Azure Rights Management (Azure RMS).|S/MIME is a certificate-based encryption solution that allows you to both encrypt and digitally sign a message. The message encryption helps ensure that only the intended recipient can open and read the message. A digital signature helps the recipient validate the identity of the sender. <br/> Les signatures numériques et le chiffrement des messages sont possibles grâce à l’utilisation de certificats numériques uniques qui contiennent les clés pour la vérification des signatures numériques et le chiffrement ou le déchiffrement des messages. <br/> To use S/MIME, you must have public keys on file for each recipient. Recipients have to maintain their own private keys, which must remain secure. If a recipient's private keys are compromised, the recipient needs to get a new private key and redistribute public keys to all potential senders.|
|Que fait-il ?|OME : <br/> Chiffre les messages envoyés à des destinataires internes ou externes. <br/>  Allows users to send encrypted messages to any email address, including Outlook.com, Yahoo! Mail, and Gmail. <br/>  Vous permet, en tant qu’administrateur, de personnaliser le portail d’affichage des messages électroniques pour qu’il corresponde à la marque de votre organisation. <br/> Microsoft gère et stocke les clés de manière sécurisée, vous n’avez donc pas à vous en occuper. <br/> Aucun logiciel spécial côté client n’est nécessaire tant que le message chiffré (envoyé en tant que pièce jointe HTML) peut être ouvert dans un navigateur.|IRM : <br/> Utilise le chiffrement et les restrictions d’utilisation pour fournir une protection en ligne et hors ligne pour les messages électroniques et les pièces jointes. <br/> Vous donne, en votre qualité d’administrateur, la possibilité de configurer des règles de transport ou des règles de protection Outlook pour appliquer automatiquement la gestion des droits relatifs à l’information (IRM) aux messages sélectionnés. <br/> Permet aux utilisateurs d’appliquer manuellement des modèles dans Outlook ou Outlook sur le web (auparavant Outlook Web App).|S/MIME gère l’authentification des expéditeurs par les signatures numériques et la confidentialité des messages par le chiffrement.|
|Que ne fait-il pas ?|OME doesn't let you apply usage restrictions to messages. For example, you can't use it to stop a recipient from forwarding or printing an encrypted message.|Some applications may not support IRM emails on all devices. For more information about these and other products that support IRM email, see [Client device capabilities](/azure/information-protection/requirements#BKMK_ClientCapabilities).|S/MIME ne permet pas l’analyse des messages chiffrés pour détecter les logiciels malveillants et le courrier indésirable ou y appliquer des stratégies.|
|Recommandations et exemples de scénarios|We recommend using OME when you want to send sensitive business information to people outside your organization, whether they're consumers or other businesses. For example:  <br/>  Quand un employé de banque envoie des relevés de carte de crédit aux clients ;  <br/>  Quand un cabinet médical envoie un dossier médical à un patient   <br/>  Quand un avocat envoie des informations juridiques à caractère confidentiel à un autre avocat.|We recommend using IRM when you want to apply usage restrictions as well as encryption. For example:  <br/>  Un responsable qui envoie des données confidentielles à son équipe sur un nouveau produit applique l’option « Ne pas transférer ».  <br/>  Un dirigeant doit envoyer une proposition d’appel d’offres à une autre société ; elle contient une pièce jointe d’un partenaire qui utilise Office 365 ; le message électronique et la pièce jointe doivent tous deux être protégés.|Nous vous recommandons d’utiliser S/MIME lorsque votre organisation ou l’organisation du destinataire requiert un véritable chiffrement de pair à pair.  <br/>  S/MIME est la solution utilisée le plus couramment dans les scénarios suivants :  <br/>  Des agences gouvernementales communiquant avec des agences gouvernementales  <br/>  Une entreprise communiquant avec une agence gouvernementale|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Quelles options de chiffrement sont disponibles pour mon abonnement Microsoft 365 ?

For information about email encryption options for your Microsoft 365 subscription see the [Exchange Online service description](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Here, you can find information about the following encryption features:
  
- Azure RMS, y compris les fonctionnalités IRM et le chiffrement des messages Microsoft Purview

- S/MIME

- TLS

- Chiffrement des données stockées (via BitLocker)

Vous pouvez également utiliser des outils de chiffrement tiers avec Microsoft 365 (par exemple, PGP (Pretty Good Privacy)). Microsoft 365 ne prend pas en charge PGP/MIME, et vous ne pouvez utiliser PGP/Inline que pour envoyer et recevoir des e-mails chiffrés par PGP.

## <a name="what-about-encryption-for-data-at-rest"></a>Qu’en est-il du chiffrement des données stockées ?

"Data at rest" refers to data that isn't actively in transit. In Microsoft 365, email data at rest is encrypted using BitLocker Drive Encryption. BitLocker encrypts the hard drives in Microsoft datacenters to provide enhanced protection against unauthorized access. To learn more, see [BitLocker Overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>Informations supplémentaires sur les options de chiffrement du courrier

Pour plus d’informations sur les options de chiffrement des messages électroniques dans cet article, ainsi que sur le protocole TLS, consultez les articles suivants :
  
**Chiffrement des messages Microsoft Purview**
  
[Cryptage des messages](ome.md)
  
**IRM**
  
[Gestion des droits relatifs à l'information dans Exchange Online](./information-rights-management-in-exchange-online.md)
  
[Qu’est-ce que Azure Rights Management?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[S/MIME pour la signature et le chiffrement des messages](/Exchange/policy-and-compliance/smime/smime)
  
[Présentation de S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Présentation de la cryptographie par clé publique](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Configurer un flux de courrier personnalisé à l’aide de connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
