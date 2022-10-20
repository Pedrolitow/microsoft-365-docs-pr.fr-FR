---
title: Configurer le chiffrement dans Office 365 Entreprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- tier1
- purview-compliance
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: Avec Office 365, certaines fonctionnalités de chiffrement sont activées par défaut ; d’autres fonctionnalités peuvent être configurées pour répondre à certaines exigences légales ou de conformité.
ms.openlocfilehash: 16b8bcd9bd0bb6ffbceec28e82111e4938ebc893
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68632995"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Configurer le chiffrement dans Office 365 Entreprise

Le chiffrement peut empêcher la lecture de votre contenu par des utilisateurs non autorisés. Étant donné que [le chiffrement dans Office 365](encryption.md) peut être effectué à l’aide de différentes technologies et méthodes, il n’existe pas un seul emplacement où vous activez ou configurez le chiffrement. Cet article fournit des informations sur les différentes façons de configurer le chiffrement dans le cadre de votre stratégie de protection des informations.

> [!TIP]
> Si vous recherchez des détails plus techniques sur le chiffrement, consultez [les informations de référence techniques sur le chiffrement dans Office 365](technical-reference-details-about-encryption.md).

Avec Office 365, plusieurs fonctionnalités de chiffrement sont disponibles par défaut. Des fonctionnalités de chiffrement supplémentaires peuvent être configurées pour répondre à certaines exigences légales ou de conformité. Le tableau suivant décrit plusieurs méthodes de chiffrement pour différents scénarios.

<br>

****

|Scénario|Méthodes de chiffrement|
|---|---|
|Les fichiers sont enregistrés sur les ordinateurs Windows|Le chiffrement au niveau de l’ordinateur peut être effectué à l’aide de BitLocker sur les appareils Windows. En tant qu’administrateur d’entreprise ou professionnel de l’informatique, vous pouvez le configurer à l’aide de Microsoft Deployment Toolkit (MDT). Voir [Configurer MDT pour BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Les fichiers sont enregistrés sur des appareils mobiles|Certains types d’appareils mobiles chiffrent les fichiers enregistrés sur ces appareils par défaut. Avec [les fonctionnalités de Gestion des périphériques mobiles pour Office 365 intégrées](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0), vous pouvez définir des stratégies qui déterminent s’il faut autoriser les appareils mobiles à accéder aux données dans Office 365. Par exemple, vous pouvez définir une stratégie qui autorise uniquement les appareils qui chiffrent le contenu à accéder à Office 365 données. Consultez [Créer et déployer des stratégies de sécurité des appareils](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Pour un contrôle supplémentaire sur la façon dont les appareils mobiles interagissent avec Office 365, vous pouvez envisager d’ajouter [des Microsoft Intune](/mem/intune/fundamentals/setup-steps).|
|Vous devez contrôler les clés de chiffrement utilisées pour chiffrer vos données dans les centres de données de Microsoft|En tant qu’administrateur Office 365, vous pouvez contrôler les clés de chiffrement de votre organisation, puis configurer Office 365 pour les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft. <p> [Chiffrement de service avec la clé client Microsoft Purview](customer-key-overview.md)|
|Personnes communiquent par e-mail (Exchange Online)|En tant qu’administrateur Exchange Online, vous disposez de plusieurs options pour configurer le chiffrement des e-mails. Cela comprend : <ul><li>Utilisation [de Office 365 chiffrement de messages (OME)](set-up-new-message-encryption-capabilities.md) avec Azure Rights Management (Azure RMS) pour permettre aux utilisateurs d’envoyer des messages chiffrés à l’intérieur ou à l’extérieur de votre organisation</li><li>Utilisation [de S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo) pour chiffrer et signer numériquement des messages électroniques</li><li>Utilisation de TLS pour [configurer des connecteurs pour un flux de messagerie sécurisé avec une autre organisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)</li></ul> <p> Consultez [Email chiffrement dans Office 365](./email-encryption.md).|
|Les fichiers sont accessibles à partir de sites d’équipe ou de bibliothèques de documents (OneDrive Entreprise ou SharePoint Online)|Lorsque des personnes travaillent avec des fichiers enregistrés dans OneDrive Entreprise ou SharePoint Online, les connexions TLS sont utilisées. Il est intégré automatiquement à Office 365. Consultez [Chiffrement des données dans OneDrive Entreprise et SharePoint Online](./data-encryption-in-odb-and-spo.md).|
|Les fichiers sont partagés dans des réunions en ligne et des conversations par messagerie instantanée (Skype Entreprise Online)|Lorsque des personnes travaillent avec des fichiers à l’aide de Skype Entreprise Online, TLS est utilisé pour la connexion. Il est intégré automatiquement à Office 365. Consultez [Sécurité et archivage (Skype Entreprise Online).](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)|
|Les fichiers sont partagés dans les réunions en ligne et les conversations par messagerie instantanée (Microsoft Teams)|Lorsque des personnes travaillent avec des fichiers à l’aide de Microsoft Teams, TLS est utilisé pour la connexion. Il est intégré automatiquement à Office 365. Microsoft Teams ne prend actuellement pas en charge le rendu inline des e-mails chiffrés. Pour empêcher l’envoi de messages chiffrés dans Microsoft Teams comme chiffré, consultez le [FAQ sur le chiffrement des messages](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="additional-information"></a>Informations supplémentaires

Pour en savoir plus sur les solutions de protection des fichiers qui incluent des options de chiffrement, consultez [Solutions de protection des fichiers dans Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
