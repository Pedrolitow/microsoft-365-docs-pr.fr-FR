---
title: Évaluer votre posture de sécurité via le Score de sécurité Microsoft
description: Décrit comment prendre des mesures pour améliorer votre score de sécurité Microsoft dans le Centre de sécurité Microsoft 365.
keywords: score de sécurité Microsoft, score sécurisé, score de sécurité Office 365, score de sécurité Microsoft, centre de sécurité Microsoft 365, actions d’amélioration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 8cf416e773abc6cbe1fd891fcec9f02a5011c413
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930641"
---
# <a name="assess-your-security-posture-with-microsoft-secure-score"></a>Évaluer votre posture de sécurité avec le Niveau de sécurité Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Le niveau de sécurité Microsoft est une mesure de la posture de sécurité d’une organisation, avec un nombre plus élevé indiquant d’autres actions d’amélioration. Vous pouvez le trouver dans le Centre de sécurité https://security.microsoft.com/securescore [Microsoft 365.](overview-security-center.md)

Pour vous aider à obtenir plus rapidement les informations dont vous avez besoin, les actions d’amélioration de Microsoft sont organisées en groupes :

* Identité (comptes Azure Active Directory & rôles)
* Appareil (Microsoft Defender pour point de terminaison, appelé [Score de sécurité Microsoft pour les appareils)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-microsoft-secure-score-devices)
* Application (applications de messagerie et cloud, notamment Office 365 et Microsoft Cloud App Security)

>[!NOTE]
>Dans la version récente de Microsoft Secure Score, un modèle de score amélioré a été publié, ce qui rend le Score de sécurisation Microsoft temporairement incompatible avec identity secure score et l’API Graph. [Afficher les détails](microsoft-secure-score-whats-new.md)

Dans la page vue d’ensemble du score de sécurité Microsoft, affichez la répartition des points entre ces groupes et les points disponibles. Vous pouvez également obtenir une vue globale du score total, de la tendance historique de votre score sécurisé avec des comparaisons de critères et des actions d’amélioration hiérarchisées qui peuvent être prises pour améliorer votre score.

![Page d’accueil du score de sécurisation](../../media/secure-score/secure-score-homepage-new.png)

## <a name="check-your-current-score"></a>Vérifier votre score actuel

Pour vérifier votre score actuel, consultez la page vue d’ensemble du niveau de sécurisation Microsoft et recherchez la vignette qui indique **Votre score de sécurité.** Votre score s’affiche sous la mesure d’un pourcentage, ainsi que le nombre de points que vous avez obtenus sur le nombre total de points possibles.

En outre, si vous sélectionnez le bouton **Inclure** en regard de votre score, vous pouvez choisir différentes vues de votre score. Ces différentes vues de score s’affichent dans le graphique sur la vignette de score et le graphique de répartition des points.

Voici les scores que vous pouvez ajouter à votre vue de votre score global pour vous donner une image plus complète de votre score global :

- **Score planifié**: afficher le score projeté lorsque les actions planifiées sont terminées
- **Score de licence actuel**: afficher le score qui peut être obtenu avec votre licence Microsoft actuelle
- **Score réalisable :** afficher le score qui peut être obtenu avec vos licences Microsoft et l’acceptation actuelle des risques

Cette vue ressemblera à ce à quoi elle ressemblera si vous avez inclus tous les affichages de score possibles :

![Votre score sécurisé, y compris le score planifié, le score de licence actuel et le score réalisable](../../media/secure-score/your-secure-score.png)

## <a name="take-action-to-improve-your-score"></a>Prendre des mesures pour améliorer votre score

**L’onglet Actions d’amélioration** répertorie les recommandations de sécurité qui abordent les surfaces d’attaque possibles. Il inclut également leur état (pour résoudre, planifié, risque accepté, résolu par le biais d’un tiers, résolu via une atténuation de remplacement et terminé). Vous pouvez rechercher, filtrer et grouper toutes les actions d’amélioration.  

### <a name="ranking"></a>Classement

Le classement est basé sur le nombre de points à atteindre, les difficultés de mise en œuvre, l’impact sur l’utilisateur et la complexité. Les actions d’amélioration les plus classées ont un grand nombre de points restants avec peu de difficulté, d’impact sur l’utilisateur et de complexité.

### <a name="view-improvement-action-details"></a>Afficher les détails de l’action d’amélioration

Lorsque vous sélectionnez une action d’amélioration spécifique, un volant de page complète s’affiche.  

![Exemple de volant d’action d’amélioration](../../media/secure-score/secure-score-improvement-action-details.png)

Pour effectuer l’action, vous avez plusieurs options :

- Sélectionnez **Gérer** pour passer à l’écran de configuration et effectuer les changements. Vous gagnerez ensuite les points que l’action vaut, visibles dans le volant. La mise à jour des points prend généralement environ 24 heures.

- Sélectionnez **Partager** pour copier le lien direct vers l’action d’amélioration. Vous pouvez également choisir la plateforme pour partager le lien, telle que la messagerie, Microsoft Teams, Le Planificateur Microsoft ou ServiceNow. La sélection de ServiceNow vous permet de créer un ticket de modification qui sera visible dans ServiceNow et le centre de sécurité Microsoft 365. Pour en savoir plus, voir [Centre de sécurité Microsoft 365 et intégration de ServiceNow.](tickets-security-center.md)

Ajoutez **des notes** pour suivre la progression ou tout autre commentaire que vous souhaitez commenter. Si vous ajoutez vos propres **balises à** l’action d’amélioration, vous pouvez filtrer par ces balises.

### <a name="choose-an-improvement-action-status"></a>Choisir l’état d’une action d’amélioration

Choisissez les états et les notes d’enregistrement spécifiques à l’action d’amélioration.

- **To address** - You recognize that the improvement action is necessary and plan to address it at some point in the future. Cet état s’applique également aux actions détectées comme partiellement, mais pas entièrement terminées.
- **Planifié** : des plans concrets sont en place pour effectuer l’action d’amélioration.
- **Risque accepté :** la sécurité doit toujours être équilibrée avec la convivialité, et toutes les recommandations ne fonctionnent pas pour votre environnement. Lorsque c’est le cas, vous pouvez choisir d’accepter le risque, ou le risque restant, et de ne pas adopter l’action d’amélioration. Aucun point ne vous sera attribué, mais l’action ne sera plus visible dans la liste des actions d’amélioration. Vous pouvez afficher cette action dans l’historique ou l’annuler à tout moment.
- **Résolu par le**  biais d’un tiers et résolu par le biais d’une atténuation alternative : l’action d’amélioration a déjà été traitée par une application ou un logiciel tiers, ou par un outil interne. Vous gagnerez les points que l’action vaut, afin que votre score reflète mieux votre posture de sécurité globale. Si un outil tiers ou interne ne couvre plus le contrôle, vous pouvez choisir un autre état. N’oubliez pas que Microsoft n’aura aucune visibilité sur l’intégralité de l’implémentation si l’action d’amélioration est marquée comme l’un de ces états.

#### <a name="threat--vulnerability-management-improvement-actions"></a>Actions d’amélioration & la gestion des menaces et des vulnérabilités

Pour les actions d’amélioration dans la catégorie « Appareil », vous ne pouvez pas choisir les états. Au lieu de cela, vous [](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) serez dirigé vers la recommandation de sécurité associée à la gestion des menaces et des vulnérabilités dans le Centre de sécurité [Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/use) pour prendre des mesures. L’exception que vous choisissez et la justification que vous écrivez sera spécifique à ce portail. Il ne sera pas présent dans le portail Score de sécurité Microsoft.

#### <a name="completed-improvement-actions"></a>Actions d’amélioration terminées

Les actions d’amélioration ont un état « terminé » une fois que tous les points possibles pour l’action d’amélioration ont été atteints. Les actions d’amélioration terminées sont confirmées à l’aide de données Microsoft et vous ne pouvez pas modifier l’état.

### <a name="assess-information-and-review-user-impact"></a>Évaluer les informations et examiner l’impact sur l’utilisateur

La section appelée **En un coup d’œil** vous indique la catégorie, les attaques contre qui elle peut être protégée et le produit.

**L’impact** sur les utilisateurs est ce que  les utilisateurs vont faire si l’action d’amélioration est adoptée et que les utilisateurs affectés sont les personnes qui seront affectées.

### <a name="implement-the-improvement-action"></a>Implémenter l’action d’amélioration

La  section Implémentation présente les conditions préalables, les étapes suivantes pas à pas pour effectuer l’action d’amélioration, l’état d’implémentation actuel de l’action d’amélioration et d’autres liens.

Les conditions préalables incluent les licences nécessaires ou les actions à prendre avant que l’action d’amélioration ne soit traitée. Assurez-vous que vous avez suffisamment de sièges dans votre licence pour effectuer l’action d’amélioration et que ces licences sont appliquées aux utilisateurs nécessaires.  

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous avez des problèmes, faites-le nous savoir en publiant dans la communauté sécurité, confidentialité [& conformité.](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) Nous surveillons la communauté et fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Vue d’ensemble du score de sécurisation Microsoft](microsoft-secure-score.md)
- [Suivre votre historique du Score de sécurisation Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)
- [Nouveautés](microsoft-secure-score-whats-new.md)
