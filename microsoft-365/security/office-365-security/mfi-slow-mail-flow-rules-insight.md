---
title: Résoudre les règles de flux de messagerie lent
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: m365-security
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’insight de résolution des règles de flux de courrier lent dans le Centre de sécurité & conformité pour identifier et corriger les règles de flux de courrier inefficaces ou rompues (également appelées règles de transport) dans leur organisation.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 66db21eadb7578b0d20272dcdf35101122991573
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68063857"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Correction de l’insight sur les règles de flux de courrier lent dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Des règles de flux de courrier inefficaces (également appelées règles de transport) peuvent entraîner des retards de flux de courrier pour votre organisation. Cet aperçu signale les règles de flux de courrier qui ont un impact sur le flux de messagerie de votre organisation. Voici quelques exemples de ces types de règles :

- Conditions dont l’utilisation **est membre pour les** grands groupes.
- Conditions qui utilisent la correspondance de modèle d’expression régulière complexe (expression régulière).
- Conditions qui utilisent la vérification du contenu dans les pièces jointes.

L’insight **sur les règles de flux de courrier lents de correction** dans la zone **Recommandée pour vous** du [tableau de bord](mail-flow-insights-v2.md) flux de courrier dans le [Centre de sécurité & conformité](https://protection.office.com) vous avertit lorsqu’une règle de flux de courrier prend trop de temps.

Cet aperçu apparaît uniquement après la détection de la condition (si vous n’avez pas de boucles de messagerie, vous ne verrez pas l’insight).

Vous pouvez utiliser cette notification pour vous aider à identifier et à affiner les règles de flux de courrier afin de réduire les retards de flux de courrier.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules.png" alt-text="Informations sur les règles de flux de courrier lents dans la zone Recommandée pour vous du tableau de bord flux de courrier" lightbox="../../media/mfi-fix-slow-mail-flow-rules.png":::

Lorsque vous cliquez sur **Afficher les détails** du widget, un menu volant s’affiche avec plus d’informations :

- **Règle** : vous pouvez pointer sur le résumé pour voir toutes les conditions, exceptions et actions de la règle. Vous pouvez cliquer sur le résumé pour modifier la règle dans le Centre d’administration Exchange (EAC) à l’adresse <https://admin.exchange.microsoft.com/#/transportrules>.
- **Nombre de messages évalués** : vous pouvez cliquer sur **Afficher les exemples de messages** pour afficher les résultats de [suivi des messages](message-trace-scc.md) pour un exemple de messages qui ont été affectés par la règle.
- **Temps moyen passé sur chaque message**
- **Temps médian passé sur un message** : valeur intermédiaire qui sépare la moitié supérieure de la moitié inférieure des données de temps.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules-details.png" alt-text="Menu volant Détails qui s’affiche après avoir cliqué sur Afficher les détails du correctif des règles de flux de courrier lent" lightbox="../../media/mfi-fix-slow-mail-flow-rules-details.png":::

Pour plus d’informations sur les conditions et les exceptions dans les règles de flux de messagerie, consultez [conditions et exceptions de règle de flux de courrier (prédicats) dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
