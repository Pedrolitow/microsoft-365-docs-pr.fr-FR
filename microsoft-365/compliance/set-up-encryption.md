---
title: Configurer le chiffrement dans Office 365 Entreprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: Avec Office 365, certaines fonctionnalités de chiffrement sont désactivées par défaut . d’autres fonctionnalités peuvent être configurées pour répondre à certaines exigences légales ou de conformité.
ms.openlocfilehash: e153c1e322adaea000cf686e857387d671b18a28
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51051676"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Configurer le chiffrement dans Office 365 Entreprise

Le chiffrement peut protéger votre contenu contre la lecture par des utilisateurs non autorisés. Étant donné que le chiffrement dans [Office 365](encryption.md) peut être effectué à l’aide de différentes technologies et méthodes, il n’existe pas un seul endroit où vous activer ou configurer le chiffrement. Cet article fournit des informations sur les différentes façons de configurer le chiffrement dans le cadre de votre stratégie de protection des informations.
  
> [!TIP]
> Si vous recherchez des détails techniques sur le chiffrement, voir détails de référence technique sur le chiffrement [dans Office 365.](technical-reference-details-about-encryption.md)
  
Avec Office 365, plusieurs fonctionnalités de chiffrement sont disponibles par défaut. Des fonctionnalités de chiffrement supplémentaires peuvent être configurées pour répondre à certaines exigences légales ou de conformité. Le tableau suivant décrit plusieurs méthodes de chiffrement pour différents scénarios.
  
|**Scénario**|**Méthodes de chiffrement**|
|:-----|:-----|
|Les fichiers sont enregistrés sur les ordinateurs Windows  <br/> |Le chiffrement au niveau de l’ordinateur peut être effectué à l’aide de BitLocker sur les appareils Windows. En tant qu’administrateur d’entreprise ou professionnel de l’informatique, vous pouvez le configurer à l’aide de Microsoft Deployment Shared Computer Toolkit (MDT). Voir [Configurer MDT pour BitLocker.](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker)  <br/> |
|Les fichiers sont enregistrés sur des appareils mobiles  <br/> |Certains types d’appareils mobiles chiffrent les fichiers qui sont enregistrés sur ces appareils par défaut. Avec les fonctionnalités de gestion des appareils mobiles intégrées pour [Office 365,](https://support.microsoft.com/en-us/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0)vous pouvez définir des stratégies qui déterminent si les appareils mobiles doivent autoriser ou non l’accès aux données dans Office 365. Par exemple, vous pouvez définir une stratégie qui autorise uniquement les appareils qui chiffrent le contenu à accéder aux données Office 365. Voir [Créer et déployer des stratégies de sécurité des appareils.](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6)  <br/> Pour un contrôle supplémentaire sur la façon dont les appareils mobiles interagissent avec Office 365, vous pouvez envisager d’ajouter [Microsoft Intune.](/mem/intune/fundamentals/setup-steps)  <br/> |
|Vous devez contrôler les clés de chiffrement utilisées pour chiffrer vos données dans les centres de données de Microsoft  <br/> | En tant qu’administrateur Office 365, vous pouvez contrôler les clés de chiffrement de votre organisation, puis configurer Office 365 pour les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft.  <br/> [Chiffrement de service avec une clé client dans Office 365](customer-key-overview.md) <br/> |
|Les personnes communiquent par courrier électronique (Exchange Online)  <br/> | En tant qu’administrateur Exchange Online, vous avez plusieurs options pour configurer le chiffrement du courrier électronique. Cela inclut ce qui suit :  <br/>  Utilisation du chiffrement de [messages Office 365 (OME)](set-up-new-message-encryption-capabilities.md) avec Azure Rights Management (Azure RMS) pour permettre aux utilisateurs d’envoyer des messages chiffrés à l’intérieur ou à l’extérieur de votre organisation  <br/>  Utilisation [de S/MIME pour la signature et](../security/defender-365-security/s-mime-for-message-signing-and-encryption.md) le chiffrement des messages pour chiffrer et signer numériquement les messages électroniques  <br/>  Utilisation de TLS [pour configurer des connecteurs pour un flux de messagerie sécurisé avec une autre organisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) <br/>  Voir [chiffrement de courrier électronique dans Office 365.](./email-encryption.md)  <br/> |
|Les fichiers sont accessibles à partir de sites d’équipe ou de bibliothèques de documents (OneDrive Entreprise ou SharePoint Online)  <br/> |Lorsque des personnes travaillent avec des fichiers enregistrés dans OneDrive Entreprise ou SharePoint Online, les connexions TLS sont utilisées. Il est intégré automatiquement à Office 365. Voir [chiffrement de données dans OneDrive Entreprise et SharePoint Online.](./data-encryption-in-odb-and-spo.md)  <br/> |
|Les fichiers sont partagés dans les réunions en ligne et les conversations par messagerie instantanée (Skype Entreprise Online)  <br/> |Lorsque des utilisateurs utilisent des fichiers à l’aide de Skype Entreprise Online, TLS est utilisé pour la connexion. Il est intégré automatiquement à Office 365. Voir [Sécurité et archivage (Skype Entreprise Online).](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)  <br/> |
|Les fichiers sont partagés dans les réunions en ligne et les conversations par messagerie instantanée (Microsoft Teams)  <br/> |Lorsque des personnes utilisent des fichiers à l’aide de Microsoft Teams, TLS est utilisé pour la connexion. Il est intégré automatiquement à Office 365. Microsoft Teams ne prend actuellement pas en charge le rendu inline du courrier électronique chiffré. Pour empêcher le courrier électronique chiffré d’être envoyé dans Microsoft Teams comme étant chiffré, consultez la FAQ sur le [chiffrement des messages.](./ome-faq.md?view=o365-worldwide#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail)  <br/> 

## <a name="additional-information"></a>Informations supplémentaires

Pour en savoir plus sur les solutions de protection de fichiers qui incluent des options de chiffrement, voir Solutions de protection des fichiers [dans Office 365.](https://www.microsoft.com/download/details.aspx?id=55523)
