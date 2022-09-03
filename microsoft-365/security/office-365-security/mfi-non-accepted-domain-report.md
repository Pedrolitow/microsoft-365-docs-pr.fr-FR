---
title: Rapport de domaine non accepté dans le tableau de bord de flux de courrier
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
description: Les administrateurs peuvent apprendre à utiliser le rapport de domaine non accepté dans le tableau de bord de flux de courrier du Centre de sécurité & conformité pour surveiller les messages de votre organisation locale où le domaine de l’expéditeur n’est pas configuré dans Microsoft 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: a27f5c62af885bb777f60a012a6822fa54816a39
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67597799"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Rapport de domaine non accepté dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le rapport de **domaine non accepté** dans le [tableau de bord de flux](mail-flow-insights-v2.md) de courrier du [Centre de sécurité & conformité](https://protection.office.com) affiche des informations sur les messages de votre organisation de messagerie locale où le domaine de l’expéditeur n’est pas configuré en tant que domaine accepté dans votre organisation Microsoft 365.

Microsoft 365 peut limiter ces messages si nous avons des données pour prouver que l’intention de ces messages est malveillante. Par conséquent, il est important pour vous de comprendre ce qui se passe et de résoudre le problème.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-widget.png" alt-text="Widget de domaine non accepté dans le tableau de bord flux de courrier du Centre de sécurité & conformité" lightbox="../../media/mfi-non-accepted-domain-report-widget.png":::

## <a name="report-view-for-the-non-accepted-domain-report"></a>Vue Rapport pour le rapport de domaine non accepté

Si vous cliquez sur le graphique sur le widget de **domaine non accepté** , vous accédez au rapport de **domaine non accepté** .

Par défaut, l’activité de tous les connecteurs affectés est affichée. Si vous cliquez sur **Afficher les données,** vous pouvez sélectionner un connecteur spécifique dans la liste déroulante.

Si vous pointez sur un point de données (jour) dans le graphique, vous verrez le nombre total de messages pour le connecteur.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-overview-view.png" alt-text="Vue Rapport dans le rapport de domaine non accepté" lightbox="../../media/mfi-non-accepted-domain-report-overview-view.png":::

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Vue de table détails pour le rapport de domaine non accepté

Si vous cliquez sur **Afficher la table de détails** dans un affichage rapport, les informations suivantes s’affichent :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages** : ID de message d’un exemple de messages affectés.

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Pour envoyer par e-mail le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez sur **Télécharger la demande**.

Lorsque vous sélectionnez une ligne dans le tableau, un menu volant s’affiche avec les informations suivantes :

- **Date**
- **Nom du connecteur entrant**
- **Domaine de l’expéditeur**
- **Nombre de messages**
- **Exemples de messages** : vous pouvez cliquer sur **Afficher les exemples de messages** pour afficher les résultats de suivi des [messages](message-trace-scc.md) pour un exemple de messages affectés.

:::image type="content" source="../../media/mfi-non-accepted-domain-report-details-flyout.png" alt-text="Menu volant Détails après la sélection d’une ligne dans la vue De table Détails dans le rapport de domaine non accepté" lightbox="../../media/mfi-non-accepted-domain-report-details-flyout.png":::

Pour revenir à la vue Rapports, cliquez sur **Afficher le rapport**.

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
