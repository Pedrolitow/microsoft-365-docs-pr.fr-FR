---
title: Rapport de non-remise dans le tableau de bord de flux de messagerie
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
description: Les administrateurs peuvent apprendre à utiliser le rapport de non-remise dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour surveiller les codes d’erreur les plus fréquemment rencontrés dans les rapports de non-remise (également appelés rapports de non-remise ou de non-remise) des expéditeurs de votre organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bc408f6bb28b11e77c49755b888c44e0ea4d9f57
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473736"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Rapport de non-remise dans le Centre de conformité & sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le  rapport d’absence de remise [](mail-flow-insights-v2.md) dans le tableau de bord de flux de messagerie du Centre de sécurité [&](https://protection.office.com) conformité affiche les codes d’erreur les plus rencontrés dans les rapports d’in-remise (également appelés messages de non-remise) pour les utilisateurs de votre organisation. Ce rapport présente les détails des rapports de non-remise pour vous aider à résoudre les problèmes de remise des e-mails.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="Widget de rapport de non-remise dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>Affichage du rapport de non-remise

Un clic sur le widget de rapport de **non-remise** vous permet d’avoir accès à la **rapport d’absence de remise**.

Par défaut, l’activité de tous les codes d’erreur s’affiche. Si vous cliquez **sur Afficher les données** pour, vous pouvez sélectionner un code d’erreur spécifique dans ladown.

Si vous pointez sur une couleur spécifique (code d’erreur) un jour spécifique dans le graphique, vous verrez le nombre total de messages pour l’erreur.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="Affichage Rapport dans le rapport de domaine non accepté" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>Affichage de table détails pour le rapport de non-remise

Si vous cliquez **sur Afficher le tableau des détails** dans un affichage de rapport, les informations suivantes sont affichées :

- **Date**
- **Code de rapport de non-remise**
- **Count**
- **Exemples de messages** : ID de message d’un échantillon de messages affectés.

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin**.

Pour envoyer par courrier électronique le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez **sur Demander le téléchargement**.

Lorsque vous sélectionnez une ligne dans le tableau, un flyout s’affiche avec les informations suivantes :

- **Date**
- **Code de rapport de non-remise** : vous pouvez cliquer sur le lien pour obtenir plus d’informations sur les causes et solutions du code d’erreur spécifique.
- **Count**
- **Exemples de messages** : vous pouvez cliquer **sur Afficher les exemples de messages** pour afficher les résultats du [suivi](message-trace-scc.md) des messages pour un échantillon des messages concernés.


:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="Le flyout Détails après la sélection d’une ligne dans l’affichage De la table Détails dans le rapport de non-remise" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>Sujets associés

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité](mail-flow-insights-v2.md).
