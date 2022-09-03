---
title: Résoudre les problèmes de boucles de courrier possibles
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: cb801985-3c89-4979-9c18-17829a4cb563
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’aperçu de la boucle de messagerie possible dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour identifier et corriger les boucles de messagerie dans leur organisation.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 488d992727ba01a4b050ddc0af6dff951898b833
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67597457"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>Correction des insights de boucle de messagerie possibles dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les boucles de messagerie sont incorrectes car :

- Ils gaspillent les ressources système.
- Ils consomment le quota de volume de courrier de votre organisation.
- Ils envoient des rapports de non-remise déroutants (également appelés DNR ou messages de rebond) aux expéditeurs de messages d’origine.

L’aperçu **de la boucle de messagerie possible** dans la zone **Recommandée pour vous** du [tableau de bord de flux](mail-flow-insights-v2.md) de messagerie dans le [Centre de sécurité & conformité](https://protection.office.com) vous avertit lorsqu’une boucle de messagerie est détectée dans votre organisation.

Cet aperçu apparaît uniquement après la détection de la condition (si vous n’avez pas de boucles de messagerie, vous ne verrez pas l’insight).

:::image type="content" source="../../media/mfi-fix-possible-mail-loop.png" alt-text="Informations sur les règles de flux de courrier lents dans la zone Recommandée pour vous du tableau de bord flux de courrier" lightbox="../../media/mfi-fix-possible-mail-loop.png":::

Lorsque vous cliquez sur **Afficher les détails** du widget, un menu volant s’affiche avec plus d’informations :

- **Domaine**
- **Nombre de messages** : vous pouvez cliquer sur **Afficher les exemples de messages** pour afficher les résultats de [la trace des messages](message-trace-scc.md) pour un exemple de messages qui ont été affectés par la boucle.
- **Type de domaine** » Par exemple, Faisant autorité ou Non faisant autorité.
- **Enregistrement MX** : valeurs d’hôte (**serveur de messagerie**) et de **priorité** de l’enregistrement MX pour le domaine.
- **Raison** de la boucle et **comment corriger** : nous allons identifier les scénarios de boucle de messagerie les plus courants et fournir des actions recommandées pour corriger la boucle.

:::image type="content" source="../../media/mfi-fix-possible-mail-loop-details.png" alt-text="Menu volant Détails qui s’affiche après avoir cliqué sur Afficher les détails de l’aperçu de la boucle de messagerie possible" lightbox="../../media/mfi-fix-possible-mail-loop-details.png":::

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
