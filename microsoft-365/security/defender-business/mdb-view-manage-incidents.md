---
title: Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)
description: Découvrez comment afficher les & gérer les alertes, répondre aux menaces, gérer les appareils et passer en revue les actions de correction
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 01/06/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 62036779aec92b08679d1213c1605b42388760af
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61940577"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business-preview"></a>Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Lorsque des menaces sont détectées et que des alertes sont déclenchées, des incidents sont créés. L’équipe de sécurité de votre entreprise peut afficher et gérer les incidents dans le portail Microsoft 365 Defender entreprise.

**Cet article inclut** les articles suivants :

- [Comment surveiller vos incidents et alertes](#monitor-your-incidents--alerts)
- [Gravité de l’alerte](#alert-severity)
- [Étapes suivantes](#next-steps)

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise.</a> Vos commentaires sont les bienvenus.
>

## <a name="monitor-your-incidents--alerts"></a>Surveiller vos incidents et & alertes

1. Dans le Microsoft 365 Defender de navigation ( ), dans le volet [https://security.microsoft.com](https://security.microsoft.com) de navigation, sélectionnez **Incidents**. Tous les incidents qui ont été créés sont répertoriés sur la page.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Capture d’écran de la liste Incidents":::

2. Sélectionnez une alerte pour ouvrir son volet volant, où vous pouvez en savoir plus sur l’alerte. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Capture d’écran de l’incident sélectionné avec le volant ouvert":::

3. Dans le volet volant, vous pouvez voir le titre de l’alerte, afficher la liste des biens (tels que les points de terminaison ou les comptes d’utilisateur) qui ont été affectés, prendre des mesures disponibles et utiliser des liens pour afficher plus d’informations et même ouvrir la page de détails de l’alerte sélectionnée. 

> [!TIP]
> Microsoft Defender pour Entreprise (prévisualisation) est conçu pour vous aider à résoudre les menaces détectées en proposant des actions recommandées. Lorsque vous affichez une alerte, recherchez les actions recommandées à prendre. Notez également la gravité de l’alerte, qui est déterminée non seulement sur la base de la gravité de la menace, mais également sur le niveau de risque pour votre entreprise. 

## <a name="alert-severity"></a>Gravité de l’alerte

Lorsque Antivirus Microsoft Defender affecte une gravité d’alerte en fonction de la gravité absolue d’une menace détectée (programme malveillant) et du risque potentiel pour un point de terminaison individuel (s’il est infecté).
Microsoft Defender pour Entreprise (prévisualisation) affecte une gravité d’alerte en fonction de la gravité du comportement détecté, du risque réel pour un point de terminaison (appareil) et, plus important encore, du risque potentiel pour votre entreprise. Le tableau suivant répertorie quelques exemples : <br/><br/>

| Scénario | Gravité de l’alerte | Reason |
|:---|:---|:---|
| Antivirus Microsoft Defender détecte et arrête une menace avant qu’elle ne soit endommagée. | Informatif | La menace a été arrêtée avant d’être endommagée. |
| Antivirus Microsoft Defender détecte les programmes malveillants qui s’exécutaient au sein de votre entreprise. Le programme malveillant est arrêté et corrigé. | Faible | Bien que certains dommages ont pu être causés à un point de terminaison individuel, le programme malveillant ne pose désormais aucune menace pour votre entreprise. |
| Les programmes malveillants en exécution sont détectés par Microsoft Defender entreprise (prévisualisation). Le programme malveillant est bloqué presque immédiatement. | Moyenne ou élevée | Le programme malveillant représente une menace pour les points de terminaison individuels et pour votre entreprise. |
| Un comportement suspect est détecté, mais aucune action de correction n’est encore prise. | Faible, Moyen ou Élevé | La gravité dépend du degré auquel le comportement pose une menace pour votre entreprise. |

## <a name="next-steps"></a>Prochaines étapes

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Afficher ou modifier des stratégies d’appareil dans Microsoft Defender entreprise (prévisualisation)](mdb-view-edit-policies.md)