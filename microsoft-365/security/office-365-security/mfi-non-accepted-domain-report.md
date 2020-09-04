---
title: Rapport de domaine non accepté dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le rapport de domaine non accepté dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité pour surveiller les messages provenant de votre organisation locale où le domaine de l’expéditeur n’est pas configuré dans Microsoft 365.
ms.openlocfilehash: 02692fbded20aa5062ce8add83925fb65c116630
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358577"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Rapport de domaine non accepté dans le centre de sécurité & conformité

Le rapport de **domaine non accepté** dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le [Centre de sécurité & conformité](https://protection.office.com) affiche des informations sur les messages provenant de votre organisation de messagerie locale où le domaine de l’expéditeur n’est pas configuré en tant que domaine accepté dans votre organisation 365 Microsoft.

Microsoft 365 peut limiter ces messages si nous disposons de données pour prouver que l’objectif de ces messages est malveillant. Par conséquent, il est important de comprendre ce qui se passe et de résoudre le problème.

![Widget domaine non accepté dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a>Affichage de rapport pour le rapport de domaine non accepté

Si vous cliquez sur le graphique sur le widget de **domaine non accepté** , vous accédez au rapport de **domaine non accepté** .

Par défaut, l’activité de tous les connecteurs concernés est affichée. Si vous cliquez sur **afficher les données pour**, vous pouvez sélectionner un connecteur spécifique dans la liste déroulante.

Si vous placez le curseur de la souris sur un point de données (jour) dans le graphique, vous verrez le nombre total de messages pour le connecteur.

![Affichage de rapport dans le rapport de domaine non accepté](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Vue de la table Détails pour le rapport de domaine non accepté

Si vous cliquez sur **afficher la table des détails** dans un affichage de rapport, les informations suivantes s’affichent :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages**: ID de message d’un exemple de messages concernés.

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

Pour envoyer par courrier électronique le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez sur **demander un téléchargement**.

Lorsque vous sélectionnez une ligne dans le tableau, une fenêtre mobile apparaît avec les informations suivantes :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages**: vous pouvez cliquer sur **afficher les exemples de messages** pour afficher les résultats du [suivi](message-trace-scc.md) des messages pour un exemple des messages concernés.

![Menu volant des détails après la sélection d’une ligne dans la vue du tableau de détails dans le rapport de domaine non accepté](../../media/mfi-non-accepted-domain-report-details-flyout.png)

Pour revenir à l’affichage rapports, cliquez sur **afficher le rapport**.

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
