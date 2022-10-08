---
title: Carte du flux de messagerie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: m365-security
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser la carte de flux de messagerie dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour visualiser et suivre la façon dont les flux de messagerie vers et depuis leur organisation sont acheminés sur des connecteurs et sans utiliser de connecteurs.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 46b9fbf868d12a92b505bd6470cee53ed53f15b7
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68077686"
---
# <a name="mail-flow-map-in-the-security--compliance-center"></a>Carte de flux de messagerie dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le **mappage de flux de** messagerie dans le [tableau de bord flux de](mail-flow-insights-v2.md) messagerie du [Centre de sécurité & conformité](https://protection.office.com) fournit des insights sur la façon dont le courrier transite par votre organisation. Vous pouvez utiliser ces informations pour apprendre les modèles, identifier les anomalies et résoudre les problèmes à mesure qu’ils se produisent.

:::image type="content" source="../../media/mfi-mail-flow-map-widget.png" alt-text="Widget de mappage de flux de messagerie dans le tableau de bord flux de courrier dans le Centre de sécurité & conformité" lightbox="../../media/mfi-mail-flow-map-widget.png":::

Par défaut, le widget affiche le modèle de flux de messagerie du jour précédent dans un graphique appelé *diagramme Sankey* . Vous pouvez utiliser la flèche ![gauche gauche.](../../media/scc-left-arrow.png) flèche droite et flèche ![](../../media/scc-right-arrow.png) droite pour afficher les informations de différents jours. Chaque couleur différente représente le flux de messagerie sur un connecteur entrant ou sortant différent (ou sans utiliser de connecteurs). Si vous pointez sur une couleur spécifique, le nombre de messages s’affiche pour ce type de connecteur.

## <a name="report-view-for-the-mail-flow-map"></a>Affichage de rapport pour la carte de flux de courrier

Si vous cliquez sur le widget de **mappage de flux** de messagerie, vous accédez au rapport de **la carte de flux de** messagerie.

Les graphiques suivants sont disponibles dans la vue rapport :

- **Afficher les données pour : Vue d’ensemble** : il s’agit essentiellement d’une vue plus grande du widget. Si vous pointez sur une couleur spécifique, le nombre de messages s’affiche pour ce type de connecteur.

    :::image type="content" source="../../media/mfi-mail-flow-map-report-overview.png" alt-text="Vue Vue d’ensemble dans le rapport de mappage de flux de messagerie" lightbox="../../media/mfi-mail-flow-map-report-overview.png":::

- **Afficher les données pour : Détail** : cette vue affiche des détails sur les connecteurs et les domaines de destination. Les domaines d’expéditeur et de destinataire supérieurs sont répertoriés, et les autres sont placés dans **Autres**. Si vous pointez sur une couleur et une section spécifiques, le nombre de messages s’affiche.

    :::image type="content" source="../../media/mfi-mail-flow-map-report-detail.png" alt-text="Vue Détails dans le rapport de mappage de flux de courrier" lightbox="../../media/mfi-mail-flow-map-report-detail.png":::

Si vous cliquez sur **Filtres** dans une vue de rapport, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Pour envoyer par e-mail le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez sur **Télécharger la demande**.

Les insights connexes sont affichés sous la carte de flux de messagerie s’ils sont disponibles (par exemple, [l’insight de boucle de messagerie possible.](mfi-mail-loop-insight.md)

## <a name="details-table-view-for-the-mail-flow-map"></a>Vue de table Détails pour la carte de flux de courrier

Si vous cliquez sur **Afficher la table de détails** dans un affichage rapport, les informations suivantes s’affichent :

- **Date**
- **Catégorie**
- **Connecteur / Fournisseur de services tiers**
- **Domaine expéditeur/destinataire**
- **Nombre de messages**

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Si vous sélectionnez une ligne, des détails similaires s’affichent dans un menu volant :

:::image type="content" source="../../media/mfi-mail-flow-map-view-details-table-details.png" alt-text="Menu volant Détails de la table de détails dans la carte de flux courrier" lightbox="../../media/mfi-mail-flow-map-view-details-table-details.png":::

Pour envoyer par e-mail le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez sur **Télécharger la demande**.

Pour revenir à la vue Rapports, cliquez sur **Afficher le rapport**.

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
