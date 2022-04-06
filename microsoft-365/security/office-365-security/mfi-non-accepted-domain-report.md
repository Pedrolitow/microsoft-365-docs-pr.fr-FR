---
title: Rapport de domaine non accepté dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le rapport de domaine non accepté dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour surveiller les messages provenant de votre organisation sur site où le domaine de l’expéditeur n’est pas configuré dans Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8f16dfbafa12080058cd1784120e4bc2157e0cff
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470832"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Rapport de domaine non accepté dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le  rapport de domaine non accepté dans le tableau [](mail-flow-insights-v2.md) de bord de flux de messagerie du Centre de sécurité [&](https://protection.office.com) conformité affiche des informations sur les messages provenant de votre organisation de messagerie sur site où le domaine de l’expéditeur n’est pas configuré en tant que domaine accepté dans votre organisation Microsoft 365.

Microsoft 365 limiter ces messages si nous avons des données pour prouver que l’intention de ces messages est malveillante. Par conséquent, il est important que vous compreniez ce qui se passe et que vous corrigez le problème.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-widget.png" alt-text="Widget de domaine non accepté dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité" lightbox="../../media/mfi-non-accepted-domain-report-widget.png":::

## <a name="report-view-for-the-non-accepted-domain-report"></a>Affichage de rapport pour le rapport de domaine non accepté

Cliquez sur le graphique sur **le widget de** domaine non accepté pour vous rendre dans le **rapport de domaine** non accepté.

Par défaut, l’activité de tous les connecteurs affectés est affichée. Si vous cliquez **sur Afficher les données** pour, vous pouvez sélectionner un connecteur spécifique dans ladown.

Si vous pointez sur un point de données (jour) dans le graphique, vous verrez le nombre total de messages pour le connecteur.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-overview-view.png" alt-text="Affichage Rapport dans le rapport de domaine non accepté" lightbox="../../media/mfi-non-accepted-domain-report-overview-view.png":::

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Vue de table Détails pour le rapport de domaine non accepté

Si vous cliquez **sur Afficher le tableau des détails** dans un affichage de rapport, les informations suivantes sont affichées :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages** : ID de message d’un échantillon de messages affectés.

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin**.

Pour envoyer par courrier électronique le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez **sur Demander le téléchargement**.

Lorsque vous sélectionnez une ligne dans le tableau, un flyout s’affiche avec les informations suivantes :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages** : vous pouvez cliquer **sur Afficher les exemples de messages** pour afficher les résultats du [suivi](message-trace-scc.md) des messages pour un échantillon des messages concernés.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-details-flyout.png" alt-text="Le flyout Détails après la sélection d’une ligne dans l’affichage De la table Détails dans le rapport de domaine non accepté" lightbox="../../media/mfi-non-accepted-domain-report-details-flyout.png":::

Pour revenir à l’affichage Rapports, cliquez **sur Afficher le rapport**.

## <a name="related-topics"></a>Sujets associés

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité](mail-flow-insights-v2.md).
