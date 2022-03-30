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
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: Avec Office 365, certaines fonctionnalités de chiffrement sont désactivées par défaut ; d’autres fonctionnalités peuvent être configurées pour répondre à certaines exigences légales ou de conformité.
ms.openlocfilehash: 84ba80c38d6167fbd9d32fdac0288fa1ef4ac3db
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680407"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Configurer le chiffrement dans Office 365 Entreprise

Le chiffrement peut protéger votre contenu contre la lecture par des utilisateurs non autorisés. Étant [donné que le chiffrement dans Office 365](encryption.md) peut être effectué à l’aide de différentes technologies et méthodes, il n’existe pas un seul endroit où vous activer ou configurer le chiffrement. Cet article fournit des informations sur les différentes façons de configurer le chiffrement dans le cadre de votre stratégie de protection des informations.

> [!TIP]
> Si vous recherchez des détails plus techniques sur le chiffrement, voir détails de référence technique sur le chiffrement [dans Office 365](technical-reference-details-about-encryption.md).

Avec Office 365, plusieurs fonctionnalités de chiffrement sont disponibles par défaut. Des fonctionnalités de chiffrement supplémentaires peuvent être configurées pour répondre à certaines exigences légales ou de conformité. Le tableau suivant décrit plusieurs méthodes de chiffrement pour différents scénarios.

<br>

****

|Scénario|Méthodes de chiffrement|
|---|---|
|Les fichiers sont enregistrés sur Windows ordinateurs|Le chiffrement au niveau de l’ordinateur peut être effectué à l’aide de BitLocker Windows appareils. En tant qu’administrateur d’entreprise ou Pro informatique, vous pouvez le configurer à l’aide de Microsoft Deployment Shared Computer Toolkit (MDT). Voir [Configurer MDT pour BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Les fichiers sont enregistrés sur des appareils mobiles|Certains types d’appareils mobiles chiffrent les fichiers qui sont enregistrés sur ces appareils par défaut. Grâce [aux fonctionnalités des](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) Gestion des périphériques mobiles pour Office 365, vous pouvez définir des stratégies qui déterminent s’il faut autoriser les appareils mobiles à accéder aux données dans Office 365. Par exemple, vous pouvez définir une stratégie qui autorise uniquement les appareils qui chiffrent le contenu à accéder Office 365 données. Voir [Créer et déployer des stratégies de sécurité des appareils](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Pour un contrôle supplémentaire sur la façon dont les appareils mobiles interagissent Office 365, vous pouvez envisager d’ajouter des [Microsoft Intune](/mem/intune/fundamentals/setup-steps).|
|Vous devez contrôler les clés de chiffrement utilisées pour chiffrer vos données dans les centres de données de Microsoft|En tant qu’administrateur Office 365, vous pouvez contrôler les clés de chiffrement de votre organisation, puis configurer Office 365 pour les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft. <p> [Chiffrement de service avec une clé client dans Office 365](customer-key-overview.md)|
|Les personnes communiquent par courrier électronique (Exchange Online)|En tant qu Exchange Online de messagerie, vous avez plusieurs options pour configurer le chiffrement des messages électroniques. Cela inclut ce qui suit : <ul><li>Utilisation Office 365 chiffrement de [messages chiffrés (OME)](set-up-new-message-encryption-capabilities.md) avec Azure Rights Management (Azure RMS) pour permettre aux utilisateurs d’envoyer des messages chiffrés à l’intérieur ou à l’extérieur de votre organisation</li><li>Utilisation [de S/MIME pour](/exchange/security-and-compliance/smime-exo/smime-exo) chiffrer et signer numériquement des messages électroniques</li><li>Utilisation de TLS [pour configurer des connecteurs pour un flux de messagerie sécurisé avec une autre organisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)</li></ul> <p> Voir [chiffrement des messages électroniques dans Office 365](./email-encryption.md).|
|Les fichiers sont accessibles à partir de sites d’équipe ou de bibliothèques de documents (OneDrive Entreprise ou SharePoint Online)|Lorsque des personnes utilisent des fichiers enregistrés OneDrive Entreprise ou SharePoint Online, les connexions TLS sont utilisées. Il est intégré Office 365 automatiquement. Voir [Chiffrement des données dans OneDrive Entreprise et SharePoint Online](./data-encryption-in-odb-and-spo.md).|
|Les fichiers sont partagés dans les réunions en ligne et les conversations par messagerie instantanée (Skype Entreprise Online)|Lorsque des personnes utilisent des fichiers à l Skype Entreprise Online, TLS est utilisé pour la connexion. Il est intégré Office 365 automatiquement. Voir [Sécurité et archivage (Skype Entreprise Online).](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)|
|Les fichiers sont partagés dans les réunions en ligne et les conversations par messagerie instantanée (Microsoft Teams)|Lorsque des personnes utilisent des fichiers à l Microsoft Teams, TLS est utilisé pour la connexion. Il est intégré Office 365 automatiquement. Microsoft Teams ne prend actuellement pas en charge le rendu en ligne des e-mails chiffrés. Pour empêcher les messages chiffrés d’Microsoft Teams chiffrés, consultez la faq [sur le chiffrement des messages](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Informations supplémentaires

Pour en savoir plus sur les solutions de protection de fichiers qui incluent des options de chiffrement, consultez la [Office 365.](https://www.microsoft.com/download/details.aspx?id=55523)
