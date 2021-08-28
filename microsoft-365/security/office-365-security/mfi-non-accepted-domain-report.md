---
title: Rapport de domaine non accepté dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le rapport de domaine non accepté dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour surveiller les messages provenant de votre organisation sur site où le domaine de l’expéditeur n’est pas configuré dans Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b2ddbc6215ebbc3b1a2b2ccff4a5bc8ad7118c3
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58574543"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Rapport de domaine non accepté dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le  rapport de domaine non [](mail-flow-insights-v2.md) accepté dans le tableau de bord de flux de messagerie du Centre de sécurité [&](https://protection.office.com) conformité affiche des informations sur les messages provenant de votre organisation de messagerie sur site où le domaine de l’expéditeur n’est pas configuré en tant que domaine accepté dans votre organisation Microsoft 365.

Microsoft 365 peuvent limiter ces messages si nous avons des données pour prouver que l’intention de ces messages est malveillante. Par conséquent, il est important que vous compreniez ce qui se passe et que vous corrigez le problème.

![Widget de domaine non accepté dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité.](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a>Affichage de rapport pour le rapport de domaine non accepté

Le fait de cliquer sur le graphique sur le widget **de** domaine non accepté vous permet d’avoir accès au **rapport de domaine** non accepté.

Par défaut, l’activité de tous les connecteurs affectés est affichée. Si vous cliquez **sur Afficher les données pour**, vous pouvez sélectionner un connecteur spécifique dans ladown.

Si vous pointez sur un point de données (jour) dans le graphique, vous verrez le nombre total de messages pour le connecteur.

![Affichage du rapport dans le rapport de domaine non accepté.](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Vue de table Détails pour le rapport de domaine non accepté

Si vous cliquez **sur Afficher le tableau des détails** dans un affichage de rapport, les informations suivantes sont affichées :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages**: ID de message d’un échantillon de messages affectés.

Si vous cliquez sur **Filtres** dans une vue de tableau de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

Pour envoyer par courrier électronique le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez **sur Télécharger la demande.**

Lorsque vous sélectionnez une ligne dans le tableau, un flyout s’affiche avec les informations suivantes :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages**: vous pouvez cliquer sur Afficher les **exemples de messages** pour afficher les résultats du [suivi](message-trace-scc.md) des messages pour un échantillon des messages concernés.

![Détails volants après la sélection d’une ligne dans l’affichage Tableau Détails dans le rapport de domaine non accepté.](../../media/mfi-non-accepted-domain-report-details-flyout.png)

Pour revenir à l’affichage Rapports, cliquez **sur Afficher le rapport.**

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)
