---
title: Exemple d’attaque par e-mail de hameçonnage
description: Analyse pas à pas d’une attaque par hameçonnage.
keywords: incidents, alertes, enquêter, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte de réception, e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 41a2c73ce5e1c3060d88572f4fa7afe63e193f46
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52299987"
---
# <a name="example-of-a-phishing-email-attack"></a>Exemple d’attaque par e-mail de hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender peut vous aider à détecter les pièces jointes malveillantes remis par courrier électronique. Dans la mesure où le Centre de sécurité et conformité [Office 365](https://protection.office.com/) s’intègre à Microsoft 365 Defender, les analystes de sécurité peuvent avoir une visibilité sur les menaces provenant de Office 365, par exemple par le biais de pièces jointes de courrier électronique.

Par exemple, un analyste a été affecté à un incident à plusieurs étapes.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Exemple d’incident en plusieurs étapes"::: 

Dans **l’onglet Alertes** de l’incident, les alertes de Defender Office 365 et Microsoft Cloud App Security sont affichées. L’analyste peut descendre dans defender pour Office 365 alertes en sélectionnant les alertes de messages électroniques. Les détails de l’alerte s’affichent dans le volet latéral.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="Exemple d’alerte par courrier électronique":::
 
En faisant défiler vers le bas, plus d’informations s’affichent, montrant les fichiers malveillants et l’utilisateur qui ont été touchés.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Exemple d’impact sur les utilisateurs et les fichiers d’une alerte par courrier électronique":::
  
La sélection **de la page** Ouvrir une alerte vous permet d’obtenir l’alerte spécifique dans laquelle différentes informations peuvent être vues plus en détail en sélectionnant le lien. Le message électronique réel peut être vu en sélectionnant Afficher les messages dans **l’Explorateur** en bas du panneau.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Exemple de détails d’une alerte"::: 

L’analyste se trouve alors sur la page Gestion des menaces dans laquelle l’objet, le destinataire, l’expéditeur et d’autres informations du courrier électronique sont affichés. **ZaP** sous **Actions spéciales indique** à l’analyste que la fonctionnalité de purge automatique heure zéro a été implémentée. ZAP détecte et supprime automatiquement les messages malveillants et de courrier indésirable des boîtes aux lettres au sein de l’organisation. Pour plus d’informations, voir [la purge automatique heure zéro (ZAP) dans Exchange Online](../office-365-security/zero-hour-auto-purge.md).

D’autres actions peuvent être prises sur des messages spécifiques en sélectionnant **Actions.** 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="Exemple d’autres actions peuvent être prises sur les messages électroniques"::: 

## <a name="next-step"></a>Étape suivante

Consultez le chemin [d’accès à l’examen des attaques](first-incident-path-identity.md) basée sur l’identité.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
