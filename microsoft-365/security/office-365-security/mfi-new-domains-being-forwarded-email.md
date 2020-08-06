---
title: Nouveaux domaines transmis par courrier électronique
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ''
description: Les administrateurs peuvent apprendre à utiliser les nouveaux domaines en cours de transmission de courriers électroniques dans le centre d’administration Exchange moderne pour rechercher les utilisateurs de leur organisation qui transfèrent des messages vers des domaines externes qui n’ont jamais été transférés.
ms.openlocfilehash: 81a596d48696f28d62d68594f27081435487d17f
ms.sourcegitcommit: c04f1207cfaddac2a9abef38967c17d689756a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "46578393"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Nouveaux domaines transmis par courrier électronique dans le centre de sécurité & conformité

Même si vous avez des raisons professionnelles valables pour transférer des messages électroniques à des destinataires externes dans des domaines spécifiques, il est suspect lorsque les utilisateurs de votre organisation redirigent soudainement les messages vers des domaines externes et que personne de l’organisation n’a transféré les messages vers ces domaines avant (nouveaux domaines). Cette condition peut indiquer que les comptes d’utilisateur sont compromis. Si vous pensez que les comptes ont été compromis, consultez la rubrique relative [à la réponse à un compte de courrier compromis](https://docs.microsoft.com/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account).

Les **nouveaux domaines transmis par courrier électronique** vous avertissent lorsque les utilisateurs de votre organisation acheminent les messages vers de nouveaux domaines.

Cette vue s’affiche uniquement lorsque le problème est détecté et qu’il apparaît sur la page [rapport de transfert](view-mail-flow-reports.md#forwarding-report) .

![Nouveaux domaines transmis par courrier électronique](../../media/mfi-new-domains-being-forwarded.png)

Lorsque vous cliquez sur le widget, un menu volant s’affiche pour vous permettre de trouver plus d’informations sur les messages transférés, y compris un lien vers le [rapport de transfert](view-mail-flow-reports.md#forwarding-report).

![Fenêtre volante de détails qui apparaît après avoir cliqué sur les nouveaux domaines en cours de transmission de messages électroniques](../../media/mfi-new-domains-being-forwarded-details.png)

Vous pouvez également accéder à cette page de détails lorsque vous sélectionnez l’option **Afficher tout** dans la zone de **recommandations & premières Insights** (tableau de**Reports** \> **bord** rapports ou <https://protection.office.com/insightdashboard> ).

Pour empêcher le transfert automatique des messages vers des domaines externes, configurez un domaine distant pour certains ou tous les domaines externes. Pour plus d’informations, consultez la rubrique [gestion des domaines distants dans Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>Sujets associés

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
