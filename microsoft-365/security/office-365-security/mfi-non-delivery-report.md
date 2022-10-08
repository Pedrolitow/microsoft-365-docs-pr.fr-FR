---
title: Rapport de non-remise dans le tableau de bord flux de courrier
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
description: Les administrateurs peuvent apprendre à utiliser le rapport des détails de non-remise dans le tableau de bord de flux de courrier du Centre de sécurité & conformité pour surveiller les codes d’erreur les plus fréquemment rencontrés dans les rapports de non-remise (également appelés notifications de remise ou messages de rebond) des expéditeurs de votre organisation.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 6c2069a0896fc77191602b9df8b6c24cc2bdb007
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68091782"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Rapport de non-remise dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le **rapport de non-remise** dans le [tableau de bord](mail-flow-insights-v2.md) flux de courrier du [Centre de sécurité & conformité](https://protection.office.com) affiche les codes d’erreur les plus rencontrés dans les rapports de non-remise (également appelés notifications de remise ou messages de rebond) pour les utilisateurs de votre organisation. Ce rapport affiche les détails des DNR pour vous permettre de résoudre les problèmes de remise de courrier électronique.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="Widget de rapport de non-remise dans le tableau de bord de flux de courrier du Centre de sécurité & conformité" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>Affichage rapport pour le rapport de non-remise

Si vous cliquez sur le widget **de rapport de non-remise** , vous accédez au **rapport de non-remise**.

Par défaut, l’activité de tous les codes d’erreur est affichée. Si vous cliquez sur **Afficher les données,** vous pouvez sélectionner un code d’erreur spécifique dans la liste déroulante.

Si vous pointez sur une couleur spécifique (code d’erreur) un jour spécifique dans le graphique, vous verrez le nombre total de messages pour l’erreur.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="Vue Rapport dans le rapport de domaine non accepté" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>Vue de table Détails pour le rapport de non-remise

Si vous cliquez sur **Afficher la table de détails** dans un affichage rapport, les informations suivantes s’affichent :

- **Date**
- **Code de rapport non remis**
- **Count**
- **Exemples de messages** : ID de message d’un exemple de messages affectés.

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Pour envoyer par e-mail le rapport pour une plage de dates spécifique à un ou plusieurs destinataires, cliquez sur **Télécharger la demande**.

Lorsque vous sélectionnez une ligne dans le tableau, un menu volant s’affiche avec les informations suivantes :

- **Date**
- **Code de rapport non remis** : vous pouvez cliquer sur le lien pour trouver plus d’informations sur les causes et les solutions du code d’erreur spécifique.
- **Count**
- **Exemples de messages** : vous pouvez cliquer sur **Afficher les exemples de messages** pour afficher les résultats de suivi des [messages](message-trace-scc.md) pour un exemple de messages affectés.

:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="Menu volant Détails après la sélection d’une ligne dans l’affichage De la table Détails dans le rapport De non-remise" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
