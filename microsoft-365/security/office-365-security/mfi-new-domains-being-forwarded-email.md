---
title: Informations sur les nouveaux domaines transmis par courrier électronique
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: ''
description: Les administrateurs peuvent apprendre à utiliser les informations sur les nouveaux domaines qui sont transmis par courrier électronique dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour examiner le moment où leurs utilisateurs envoient des messages à des domaines externes qui n’ont jamais été transmis.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a4429f1657861091082fdfaedb52c85cec3a0cc1
ms.sourcegitcommit: e920e68c8d0eac8b152039b52cfc139d478a67b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50150599"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Informations sur les nouveaux domaines transmis par courrier électronique dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Il existe des raisons professionnelles valides de faire passer des messages électroniques à des destinataires externes dans des domaines spécifiques. Toutefois, il est suspect lorsque les utilisateurs de votre organisation commencent soudainement à envoyer des messages vers un domaine vers lequel aucun utilisateur de votre organisation n’a jamais transmis de messages (un nouveau domaine).

Cette condition peut indiquer que les comptes d’utilisateur sont compromis. Si vous pensez que les comptes ont été compromis, voir Répondre [à un compte de messagerie compromis.](responding-to-a-compromised-email-account.md)

**L’aperçu** des nouveaux domaines transmis par courrier électronique dans le Centre de sécurité [&](https://protection.office.com) conformité vous informe lorsque les utilisateurs de votre organisation sont en train de forwarder des messages vers de nouveaux domaines.

Cette information apparaît uniquement lorsque le problème est détecté et apparaît sur la page du rapport [de forwarding.](view-mail-flow-reports.md#forwarding-report)

![Informations sur les nouveaux domaines transmis par courrier électronique](../../media/mfi-new-domains-being-forwarded.png)

Lorsque vous cliquez sur le widget, un flyout s’affiche, dans lequel vous trouverez plus de détails sur les messages transmis, y compris un lien vers le rapport [de forwarding.](view-mail-flow-reports.md#forwarding-report)

![Volant d’informations qui s’affiche après avoir cliqué sur l’aperçu des nouveaux domaines transmis par courrier électronique](../../media/mfi-new-domains-being-forwarded-details.png)

Vous pouvez également vous rendre sur cette page de  détails lorsque vous sélectionnez l’aperçu après avoir cliqué sur Afficher tout dans la zone Recommandations & informations les plus **détaillées** **(** Tableau de bord de rapports \>  ou <https://protection.office.com/insightdashboard> ).

Pour empêcher le transmission automatique de messages à des domaines externes, configurez un domaine distant pour certains domaines externes ou tous. Pour plus d’informations, voir [Gérer les domaines distants dans Exchange Online.](https://docs.microsoft.com/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains)

## <a name="related-topics"></a>Rubriques connexes

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)
