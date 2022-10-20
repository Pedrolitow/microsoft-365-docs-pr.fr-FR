---
title: Exemple de repérage avancé pour Microsoft Defender pour Office 365
description: Prise en main de la recherche des menaces par e-mail à l’aide de la chasse avancée
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.openlocfilehash: 29212f30cfb0628a8fc51bd5acdeea60ec9aac55
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631455"
---
# <a name="advanced-hunting-example-for-microsoft-defender-for-office-365"></a>Exemple de repérage avancé pour Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Souhaitez-vous commencer à rechercher des menaces d’e-mail à l’aide de la fonctionnalité de repérage avancé ? Essayez ceci :

La section [Prise en main](/microsoft-365/security/office-365-security/defender-for-office-365#getting-started) de [l’article Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) présente des blocs de configuration initiale logiques qui ressemblent à ceci :

1. Configurez tout avec « Anti » dans le nom.
   - Ant-programme malveillant
   - Anti-hameçonnage
   - Anti-courrier indésirable
2. Configurez tout avec « Safe » dans le nom.
   - Liens sûrs
   - Pièces jointes fiables
3. Protégez les charges de travail (par exemple, SharePoint Online, OneDrive et Teams).
4. Protégez avec le vidage automatique de zéro heure.

Vous pouvez également utiliser un [Lien](../office-365-security/protect-against-threats.md) pour vous aider à vous lancer directement dans la configuration dès le premier jour.

La dernière étape de la **Prise en main** consiste à protéger les utilisateurs grâce à la **Purge automatique à zéro heure**, également appelée ZAP. Le fait de savoir si la purge automatique zéro heure d’un courrier malveillant, après la remise, est effective peut être très important.

La navigation rapide dans la langue de la requête Kusto pour repérer des problèmes est un avantage de la convergence de ces deux centres de sécurité. Les équipes de sécurité peuvent surveiller les échecs ZAP en effectuant les étapes suivantes [ici](https://security.microsoft.com/advanced-hunting), sous **Repérage** \> **avancé**.

1. Dans la page Repérage avancé, cliquez sur **Requête**.
1. Copiez la requête ci-dessous dans la fenêtre de requête.
1. Sélectionnez **Exécuter la requête**.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfullyconverge-2-endpoints-new.png
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

:::image type="content" source="../../media/ah-query-example-new.png" alt-text="Page De chasse avancée (sous Chasse) avec requête sélectionnée en haut du panneau de requête et exécution d’une requête Kusto pour capturer les actions ZAP au cours des 7 derniers jours." lightbox="../../media/ah-query-example-new.png":::

Les données de cette requête s’affichent dans le panneau de résultats sous la requête elle-même. Les résultats incluent des informations telles que « DeviceName », « AccountDisplayName », et « ZapTime » dans un jeu de résultats personnalisable. Les résultats peuvent également être exportés pour vos enregistrements. Si vous avez encore besoin de la requête, sélectionnez **Enregistrer** > **Enregistrer sous** et ajoutez la requête à votre liste de requêtes, vos partages, ou vos requêtes de la communauté.

## <a name="related-information"></a>Informations connexes
- [Meilleures pratiques de chasse avancées](advanced-hunting-best-practices.md)
- [Vue d’ensemble - Repérage avancé](advanced-hunting-overview.md)
