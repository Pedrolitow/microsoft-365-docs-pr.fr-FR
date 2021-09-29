---
title: Carte du flux de courriers
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le plan de flux de messagerie dans le tableau de bord du flux de messagerie dans le Centre de sécurité & conformité pour visualiser et suivre la façon dont les messages circulent vers et depuis leur organisation via des connecteurs et sans utiliser de connecteurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 45182b6da5a20780673f5e84aeffaa9c3e6a6fe5
ms.sourcegitcommit: 4b1bf6e4f4a0c016d148cdde7f7880dd774403d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2021
ms.locfileid: "59988582"
---
# <a name="mail-flow-map-in-the-security--compliance-center"></a>Carte de flux de messagerie dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le plan de [](mail-flow-insights-v2.md) flux de **messagerie** dans le tableau de bord de flux de messagerie du Centre de sécurité & [conformité](https://protection.office.com) donne des informations sur la façon dont les messages circulent dans votre organisation. Vous pouvez utiliser ces informations pour apprendre des modèles, identifier des anomalies et résoudre les problèmes au moment où ils se produisent.

![Widget de carte de flux de messagerie dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité.](../../media/mfi-mail-flow-map-widget.png)

Par défaut, le widget affiche le modèle de flux de messagerie du jour précédent dans un graphique appelé *diagramme Sankey.* Vous pouvez utiliser la flèche ![ gauche.](../../media/scc-left-arrow.png) et flèche droite ![ droite pour afficher les informations de différents ](../../media/scc-right-arrow.png) jours. Chaque couleur représente le flux de messagerie sur un connecteur entrant ou sortant différent (ou sans utiliser de connecteurs). Si vous pointez sur une couleur spécifique, le nombre de messages s’affiche pour ce type de connecteur.

## <a name="report-view-for-the-mail-flow-map"></a>Affichage de rapport pour le plan de flux de messagerie

Un clic sur le widget **de carte de flux** de messagerie vous permet d’accès au rapport de carte de flux **de** messagerie.

Les graphiques suivants sont disponibles dans l’affichage de rapport :

- **Afficher les données pour : Vue d’ensemble**: il s’agit essentiellement d’une vue plus grande du widget. Si vous pointez sur une couleur spécifique, le nombre de messages s’affiche pour ce type de connecteur.

  ![Vue d’ensemble dans le rapport de carte de flux de messagerie.](../../media/mfi-mail-flow-map-report-overview.png)

- **Afficher les données pour : Détail**: cet affichage affiche des détails sur les connecteurs et les domaines de destination. Les principaux domaines de l’expéditeur et du destinataire sont répertoriés et les autres sont placés dans **d’autres domaines.** Si vous pointez sur une couleur et une section spécifiques, le nombre de messages s’affiche.

  ![Affichage détaillé dans le rapport de carte de flux de messagerie.](../../media/mfi-mail-flow-map-report-detail.png)

Si vous cliquez sur **Filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec la **date de** début et la date **de fin.**

Pour envoyer par courrier électronique le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez **sur Télécharger la demande.**

Les informations associées sont affichées sous le plan de flux de messagerie si elles sont disponibles (par exemple, l’aperçu de la boucle de courrier de [correction possible).](mfi-mail-loop-insight.md)

## <a name="details-table-view-for-the-mail-flow-map"></a>Vue de table Détails pour le plan de flux de messagerie

Si vous cliquez **sur Afficher le tableau des détails** dans un affichage de rapport, les informations suivantes sont affichées :

- **Date**
- **Catégorie**
- **Connecteur / Fournisseur de services tiers**
- **Domaine de l’expéditeur/du destinataire**
- **Nombre de messages**

Si vous cliquez sur **Filtres** dans une vue de tableau de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

Si vous sélectionnez une ligne, des détails similaires sont affichés dans un volant :

![Détails du tableau détails dans le plan de flux de messagerie.](../../media/mfi-mail-flow-map-view-details-table-details.png)

Pour envoyer par courrier électronique le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez **sur Télécharger la demande.**

Pour revenir à l’affichage Rapports, cliquez **sur Afficher le rapport.**

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)
