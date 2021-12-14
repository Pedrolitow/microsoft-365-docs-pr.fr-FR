---
title: Configurer des notifications par courrier électronique pour votre équipe de sécurité
description: Configurer des notifications par courrier électronique pour indiquer aux personnes les alertes et les vulnérabilités avec Microsoft Defender pour les entreprises
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/10/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: 60d0c58edba42b8a32062c2f7adaf417fd8c7203
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61421077"
---
# <a name="set-up-email-notifications"></a>Configurer les notifications par courrier électronique

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Vous pouvez configurer des notifications par courrier électronique pour votre équipe de sécurité. Ensuite, à mesure que des alertes sont générées ou que de nouvelles vulnérabilités sont découvertes, les membres de votre équipe de sécurité sont avertis automatiquement. 

## <a name="what-to-do"></a>Procédure

1. [Découvrez les types de notifications par courrier électronique.](#types-of-email-notifications)

2. [Afficher et modifier les paramètres de notification par courrier électronique.](#view-and-edit-email-notifications)

3. [Procédez comme vous le faire pour les étapes suivantes.](#next-steps)


## <a name="types-of-email-notifications"></a>Types de notifications par courrier électronique

Lorsque vous définissez des notifications par courrier électronique, vous pouvez choisir entre deux types, comme décrit dans le tableau suivant : <br/><br/>

| Type de notification  | Description  |
|---------|---------|
| Vulnérabilités  | Chaque fois que de nouvelles failles ou événements de vulnérabilité sont détectés, les destinataires reçoivent un e-mail. |
| Alertes & vulnérabilités  | Lorsque des alertes sont générées parce que des menaces sont détectées sur les appareils ou lorsque de nouvelles attaques ou événements de vulnérabilité sont détectés, les destinataires reçoivent un e-mail. |

> [!TIP]
> Les notifications par courrier électronique ne sont pas le seul moyen pour votre équipe de sécurité de découvrir les nouvelles **alertes ou vulnérabilités.**
> 
> Les notifications par courrier électronique sont un moyen pratique pour aider votre équipe de sécurité à rester informée, en temps réel. Mais il en existe d’autres ! Par exemple, chaque fois que votre équipe de sécurité se Microsoft 365 Defender portail ( ), des cartes mettant en évidence les nouvelles [https://security.microsoft.com](https://security.microsoft.com) menaces, alertes et vulnérabilités s’afficheront. Defender for Business (prévisualisation) est conçu pour mettre en évidence les informations importantes qui intéressent votre équipe de sécurité dès qu’elle se connecte.
> 
> Votre équipe de sécurité peut également choisir **Incidents** dans le volet de navigation pour afficher des informations. Pour plus d’informations, voir [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation).](mdb-view-manage-incidents.md)

## <a name="view-and-edit-email-notifications"></a>Afficher et modifier les notifications par courrier électronique

Pour afficher ou modifier les paramètres de notification par courrier électronique pour votre entreprise, suivez les étapes suivantes :

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Dans le volet de navigation, **sélectionnez Paramètres,** puis les **points de terminaison.** Ensuite, sous **Général,** sélectionnez **Notifications par courrier électronique.** 

3. Examinez les informations sous les **onglets Alertes** **et** vulnérabilités.

   - Si vous ne voyez aucun des éléments répertoriés sous l’onglet **Alertes,** vous pouvez créer une règle pour que les personnes soient averties lorsque des alertes sont générées. Pour obtenir de l’aide sur cette tâche, voir [Créer des règles pour les notifications d’alerte.](../defender-endpoint/configure-email-notifications.md)

   - Si vous ne voyez aucun des éléments répertoriés sous l’onglet **Vulnérabilités,** vous pouvez créer une règle pour que les personnes soient averties chaque fois qu’une nouvelle vulnérabilité est découverte. Pour obtenir de l’aide sur cette tâche, voir [Créer des règles pour les événements de vulnérabilité.](../defender-endpoint/configure-vulnerability-email-notifications.md)

   - Si des règles sont créées, sélectionnez une règle pour la modifier. Vous pouvez également supprimer une règle. 

## <a name="next-steps"></a>Prochaines étapes

Procédez comme il se doit pour :

- [Étape 4 : Intégrer des appareils à Microsoft Defender pour Entreprises (prévisualisation)](mdb-onboard-devices.md)
