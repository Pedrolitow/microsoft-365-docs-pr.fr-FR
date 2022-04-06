---
title: Exemple d’attaque par e-mail par hameçonnage
description: Analyse pas à pas d’une attaque par hameçonnage.
keywords: incidents, alertes, enquêter, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte de réception, e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 413c4fadcc6de3527643be712713d37a1e2c346c
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501132"
---
# <a name="example-of-a-phishing-email-attack"></a>Exemple d’attaque par e-mail par hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender peut vous aider à détecter les pièces jointes malveillantes remis par courrier électronique. Étant donné que le [Centre de](https://protection.office.com/) sécurité et conformité Office 365 s’intègre à Microsoft 365 Defender, les analystes de sécurité peuvent avoir une visibilité sur les menaces provenant de Office 365, par exemple par le biais de pièces jointes de courrier électronique.

Par exemple, un analyste a été affecté à un incident en plusieurs étapes.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Un incident en plusieurs étapes" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-incident.png":::

Dans **l’onglet Alertes** de l’incident, les alertes de Defender pour Office 365 et Microsoft Defender pour les applications cloud sont affichées. L’analyste peut descendre dans defender pour Office 365 alertes en sélectionnant les alertes de messages électroniques. Les détails de l’alerte sont affichés dans le volet latéral.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="Alerte par courrier électronique" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png":::
 
En faisant défiler vers le bas, plus d’informations s’affichent, montrant les fichiers malveillants et l’utilisateur qui ont été touchés.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Impact sur les utilisateurs et les fichiers d’une alerte par courrier électronique" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-impact.png":::
  
La sélection **de la page** Ouvrir une alerte vous permet d’obtenir l’alerte spécifique dans laquelle différentes informations peuvent être vues plus en détail en sélectionnant le lien. Vous pouvez afficher le message électronique réel en sélectionnant **Afficher les messages dans l’Explorateur** en bas du panneau.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Détails d’une alerte" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png"::: 

L’analyste est alors envoyé à la page Gestion des menaces dans laquelle l’objet, le destinataire, l’expéditeur et d’autres informations du courrier électronique sont affichés. **ZaP** sous **Actions spéciales** indique à l’analyste que la fonctionnalité de purge automatique heure zéro a été implémentée. ZAP détecte et supprime automatiquement les messages malveillants et de courrier indésirable des boîtes aux lettres au sein de l’organisation. Pour plus d’informations, voir [la purge automatique d’heure zéro (ZAP) dans Exchange Online](../office-365-security/zero-hour-auto-purge.md).

D’autres actions peuvent être prises sur des messages spécifiques en sélectionnant **Actions**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="Autres actions qui peuvent être prises sur les messages électroniques" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-actions.png"::: 

## <a name="next-step"></a>Étape suivante

Consultez le chemin [d’accès à l’examen des attaques](first-incident-path-identity.md) basée sur l’identité.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
