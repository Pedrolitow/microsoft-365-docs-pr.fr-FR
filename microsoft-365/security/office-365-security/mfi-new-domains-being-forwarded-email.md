---
title: Informations sur les nouveaux domaines transmis par courrier électronique
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ''
description: Les administrateurs peuvent apprendre à utiliser les nouveaux domaines en cours de transmission de messages électroniques dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité afin de déterminer quand leurs utilisateurs transfèrent des messages à des domaines externes qui n’ont jamais été transférés.
ms.openlocfilehash: a72ffd001ea22972d9dc6c00af8a4dd7881386b7
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49356942"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Nouveaux domaines transmis par courrier électronique dans le centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Il existe des raisons professionnelles valables pour transférer des messages électroniques à des destinataires externes dans des domaines spécifiques. Toutefois, il est suspect lorsque les utilisateurs de votre organisation redirigent soudainement les messages vers un domaine où personne de votre organisation n’a transféré les messages vers (un nouveau domaine).

Cette condition peut indiquer que les comptes d’utilisateur sont compromis. Si vous pensez que les comptes ont été compromis, consultez la rubrique relative [à la réponse à un compte de courrier compromis](responding-to-a-compromised-email-account.md).

Les **nouveaux domaines transmis par courrier électronique** dans le [centre de sécurité & Compliance Center](https://protection.office.com) vous avertissent lorsque les utilisateurs de votre organisation acheminent des messages vers de nouveaux domaines.

Cette vue s’affiche uniquement lorsque le problème est détecté et qu’il apparaît sur la page [rapport de transfert](view-mail-flow-reports.md#forwarding-report) .

![Informations sur les nouveaux domaines transmis par courrier électronique](../../media/mfi-new-domains-being-forwarded.png)

Lorsque vous cliquez sur le widget, un menu volant s’affiche pour vous permettre de trouver plus d’informations sur les messages transférés, y compris un lien vers le [rapport de transfert](view-mail-flow-reports.md#forwarding-report).

![Fenêtre volante de détails qui apparaît après avoir cliqué sur les nouveaux domaines en cours de transmission de messages électroniques](../../media/mfi-new-domains-being-forwarded-details.png)

Vous pouvez également accéder à cette page de détails lorsque vous sélectionnez l’option **Afficher tout** dans la zone de **recommandations & premières Insights** (tableau de **Reports** \> **bord** rapports ou <https://protection.office.com/insightdashboard> ).

Pour empêcher le transfert automatique des messages vers des domaines externes, configurez un domaine distant pour certains ou tous les domaines externes. Pour plus d’informations, consultez la rubrique [gestion des domaines distants dans Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
