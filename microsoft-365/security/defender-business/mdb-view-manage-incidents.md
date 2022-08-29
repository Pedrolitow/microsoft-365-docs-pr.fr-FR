---
title: Afficher et gérer les incidents dans Microsoft Defender pour entreprises
description: Affichez et gérez les alertes, répondez aux menaces, gérez les appareils et passez en revue les actions de correction sur les menaces détectées dans Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.date: 08/11/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2c751289c9d365d72909433fe6534f3f00ba3638
ms.sourcegitcommit: 9b10e56b9e83f3a80757fa6108bebd1d80cf4178
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67320413"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>Afficher et gérer les incidents dans Microsoft Defender pour entreprises

Lorsque des menaces sont détectées et que des alertes sont déclenchées, des incidents sont créés. L’équipe de sécurité de votre entreprise peut afficher et gérer les incidents dans le portail Microsoft 365 Defender.

**Cet article comprend les éléments suivants** :

- [Comment surveiller vos incidents et alertes](#monitor-your-incidents--alerts)
- [Gravité de l’alerte](#alert-severity)
- [Étapes suivantes](#next-steps)


## <a name="monitor-your-incidents--alerts"></a>Surveiller vos incidents & alertes

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sélectionnez **Incidents**. Tous les incidents qui ont été créés sont répertoriés sur la page.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Capture d’écran de la liste des incidents":::

2. Sélectionnez une alerte pour ouvrir son volet volant, où vous pouvez en savoir plus sur l’alerte. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Capture d’écran de l’incident sélectionné avec le menu volant ouvert":::

3. Dans le volet volant, vous pouvez voir le titre de l’alerte, afficher la liste des ressources (telles que les points de terminaison ou les comptes d’utilisateur) qui ont été affectées, prendre des mesures disponibles et utiliser des liens pour afficher plus d’informations et même ouvrir la page de détails de l’alerte sélectionnée. 

> [!TIP]
> Defender entreprise est conçu pour vous aider à résoudre les menaces détectées en proposant des actions recommandées. Lorsque vous affichez une alerte, recherchez les actions recommandées à effectuer. Prenez également note de la gravité de l’alerte, qui est déterminée non seulement sur la base de la gravité de la menace, mais aussi sur le niveau de risque pour votre entreprise. 

## <a name="alert-severity"></a>Gravité de l’alerte

Lorsque l’Antivirus Microsoft Defender attribue une gravité d’alerte en fonction de la gravité absolue d’une menace détectée (programme malveillant) et du risque potentiel pour un point de terminaison individuel (s’il est infecté). Defender entreprise affecte une gravité d’alerte en fonction de la gravité du comportement détecté, du risque réel pour un point de terminaison (appareil) et, plus important encore, du risque potentiel pour votre entreprise. Le tableau suivant répertorie quelques exemples :

| Scénario | Gravité et raison de l’alerte |
|:---|:---|
| L’Antivirus Microsoft Defender détecte et arrête une menace avant de causer des dommages. | **Information.** La menace a été arrêtée avant que des dommages n’ont été causés. |
| L’Antivirus Microsoft Defender détecte les programmes malveillants qui s’exécutaient au sein de votre entreprise. Le programme malveillant est arrêté et corrigé. | **Faible**. Bien que certains dommages aient pu être causés à un point de terminaison individuel, le programme malveillant ne représente désormais aucune menace pour votre entreprise. |
| Les programmes malveillants en cours d’exécution sont détectés par Defender entreprise. Le programme malveillant est bloqué presque immédiatement. | **Moyen** ou **élevé**. Le programme malveillant représente une menace pour les points de terminaison individuels et pour votre entreprise. |
| Un comportement suspect est détecté, mais aucune action de correction n’est encore effectuée. | **Faible**, **moyen** ou **élevé**. La gravité dépend de la mesure dans laquelle le comportement représente une menace pour votre entreprise. |

## <a name="next-steps"></a>Prochaines étapes

- [Répondre aux menaces et les atténuer dans Defender entreprise](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)
- [Afficher ou modifier des stratégies d’appareil dans Defender entreprise](mdb-view-edit-policies.md)