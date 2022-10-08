---
title: Évaluer votre posture de sécurité par le biais de Microsoft Secure Score
description: Décrit comment prendre des mesures pour améliorer votre degré de sécurisation Microsoft dans le portail Microsoft 365 Defender.
keywords: score de sécurité Microsoft, degré de sécurisation, score de sécurité Office 365, score de sécurité Microsoft, portail Microsoft 365 Defender, actions d’amélioration
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: f57144f6b27a25200423dc9d7da7fff15ff97b52
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68062053"
---
# <a name="assess-your-security-posture-with-microsoft-secure-score"></a>Évaluer votre posture de sécurité avec Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Le Niveau de sécurité Microsoft est une mesure de la posture de sécurité d'une organisation, un chiffre plus élevé indiquant que davantage de mesures d'amélioration ont été prises. Il se trouve dans https://security.microsoft.com/securescore le [portail Microsoft 365 Defender](microsoft-365-defender.md).

Pour vous aider à trouver les informations dont vous avez besoin plus rapidement, les actions d’amélioration de Microsoft sont organisées en groupes :

- Identité (comptes Azure Active Directory & rôles)
- Appareil (Microsoft Defender pour point de terminaison, appelé [Score de sécurité Microsoft pour les appareils](/windows/security/threat-protection/microsoft-defender-atp/tvm-microsoft-secure-score-devices))
- Applications (applications de messagerie et de cloud, notamment Office 365 et Microsoft Defender for Cloud Apps)

>[!NOTE]
>Dans la version récente de Microsoft Secure Score, un modèle de scoring amélioré a été publié, ce qui a rendu Microsoft Secure Score temporairement incompatible avec identity secure score et le API Graph. [Afficher les détails](microsoft-secure-score-whats-new.md)

Dans la page de vue d’ensemble du degré de sécurisation Microsoft, affichez la répartition des points entre ces groupes et les points disponibles. Vous pouvez également obtenir une vue globale du score total, la tendance historique de votre score sécurisé avec des comparaisons de benchmark et des actions d’amélioration hiérarchisées qui peuvent être prises pour améliorer votre score.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="Page d’accueil Du degré de sécurisation dans le portail Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="check-your-current-score"></a>Vérifier votre score actuel

Pour vérifier votre score actuel, accédez à la page de vue d’ensemble de Microsoft Secure Score et recherchez la vignette indiquant **votre degré de sécurisation**. Votre score s’affiche sous forme de pourcentage, ainsi que le nombre de points que vous avez atteints sur le total des points possibles.

En outre, si vous **sélectionnez** le bouton Inclure en regard de votre score, vous pouvez choisir différentes vues de votre score. Ces différents affichages de score s’affichent dans le graphique sur la vignette de score et le graphique de répartition des points.

Voici les scores que vous pouvez ajouter à votre vue de votre score global pour vous donner une image plus complète de votre score global :

- **Score planifié** : afficher le score projeté lorsque les actions planifiées sont terminées
- **Score de licence actuel** : afficher le score qui peut être obtenu avec votre licence Microsoft actuelle
- **Score réalisable** : afficher le score qui peut être obtenu avec vos licences Microsoft et l’acceptation actuelle des risques

Cette vue ressemblera à ce à quoi elle ressemble si vous avez inclus toutes les vues de score possibles :

:::image type="content" source="../../media/secure-score/secure-score-achievable.png" alt-text="Votre degré de sécurisation, y compris le score planifié, le score de licence actuel et le score réalisable dans le portail Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-achievable.png":::

## <a name="take-action-to-improve-your-score"></a>Prendre des mesures pour améliorer votre score

**L’onglet Actions d’amélioration** répertorie les recommandations de sécurité qui traitent des surfaces d’attaque possibles. Il inclut également leur état (pour traiter, planifié, risque accepté, résolu par le biais d’un tiers, résolu au moyen d’une autre atténuation et terminé). Vous pouvez rechercher, filtrer et regrouper toutes les actions d’amélioration.  

### <a name="ranking"></a>Classement

Le classement est basé sur le nombre de points restants à atteindre, la difficulté d’implémentation, l’impact sur l’utilisateur et la complexité. Les actions d’amélioration les plus élevées ont un grand nombre de points restants avec une faible difficulté, un impact utilisateur et une complexité faible.

### <a name="view-improvement-action-details"></a>Afficher les détails de l’action d’amélioration

Lorsque vous sélectionnez une action d’amélioration spécifique, un menu volant de page complète s’affiche.  

:::image type="content" source="../../media/secure-score/secure-score-improvement-action-details.png" alt-text="Menu volant d’une action d’amélioration dans le portail Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-improvement-action-details.png":::

Pour terminer l’action, vous disposez de quelques options :

- Sélectionnez **Gérer dans Microsoft 365 Defender** pour accéder à l’écran de configuration et apporter la modification. Vous obtiendrez ensuite les points que l’action vaut, visibles dans le menu volant. La mise à jour des points prend généralement environ 24 heures.

- Sélectionnez **Partager** pour copier le lien direct vers l’action d’amélioration. Vous pouvez également choisir la plateforme pour partager le lien, tel que l’e-mail, Microsoft Teams ou Planificateur Microsoft.

Ajoutez **des notes** pour suivre la progression ou tout autre élément sur lequel vous souhaitez effectuer des commentaires. Si vous ajoutez vos propres **balises** à l’action d’amélioration, vous pouvez filtrer en fonction de ces balises.

### <a name="choose-an-improvement-action-status"></a>Choisir un état d’action d’amélioration

Choisissez les états et les notes d’enregistrement spécifiques à l’action d’amélioration.

- **Pour y remédier** - Vous reconnaissez que l’action d’amélioration est nécessaire et prévoyez de la traiter à un moment donné à l’avenir. Cet état s’applique également aux actions détectées comme partiellement, mais pas entièrement terminées.
- **Planifié** : des plans concrets sont en place pour mener à bien l’action d’amélioration.
- **Risque accepté** : la sécurité doit toujours être équilibrée avec la facilité d’utilisation, et toutes les recommandations ne fonctionnent pas pour votre environnement. Lorsque c’est le cas, vous pouvez choisir d’accepter le risque, ou le risque restant, et non d’adopter l’action d’amélioration. Vous ne recevrez aucun point, mais l’action ne sera plus visible dans la liste des actions d’amélioration. Vous pouvez afficher cette action dans l’historique ou l’annuler à tout moment.
- **Résolu par le biais d’un tiers** et **résolu via une autre atténuation** : l’action d’amélioration a déjà été traitée par une application ou un logiciel tiers, ou un outil interne. Vous gagnerez les points que l’action vaut, afin que votre score reflète mieux votre posture de sécurité globale. Si un outil tiers ou interne ne couvre plus le contrôle, vous pouvez choisir un autre état. N’oubliez pas que Microsoft n’aura aucune visibilité sur l’exhaustivité de l’implémentation si l’action d’amélioration est marquée comme l’un de ces états.

#### <a name="microsoft-defender-vulnerability-management-improvement-actions"></a>actions d’amélioration Gestion des vulnérabilités Microsoft Defender

Pour les actions d’amélioration dans la catégorie « Appareil », vous ne pouvez pas choisir les états. Au lieu de cela, vous êtes dirigé vers la [recommandation de sécurité Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) associée dans le Microsoft 365 Defender pour prendre des mesures. L’exception que vous choisissez et la justification que vous écrivez sont spécifiques à ce portail. Il ne sera pas présent dans le portail Microsoft Secure Score.

#### <a name="completed-improvement-actions"></a>Actions d’amélioration terminées

Les actions d’amélioration ont un état « terminé » une fois que tous les points possibles pour l’action d’amélioration ont été atteints. Les actions d’amélioration terminées sont confirmées par les données Microsoft, et vous ne pouvez pas modifier l’état.

### <a name="assess-information-and-review-user-impact"></a>Évaluer les informations et examiner l’impact de l’utilisateur

La section appelée **En un coup d’œil** vous indique la catégorie, les attaques contre laquelle elle peut se protéger et le produit.

**L’impact** utilisateur est ce que les utilisateurs rencontreront si l’action d’amélioration est adoptée, et les **utilisateurs concernés** sont les personnes qui seront affectées.

### <a name="implement-the-improvement-action"></a>Implémenter l’action d’amélioration

La section **Implémentation** présente les prérequis, les étapes suivantes pas à pas pour effectuer l’action d’amélioration, l’état d’implémentation actuel de l’action d’amélioration et tous les liens d’informations supplémentaires.

Les prérequis incluent toutes les licences nécessaires ou les actions à effectuer avant que l’action d’amélioration ne soit traitée. Assurez-vous que vous disposez de suffisamment de sièges dans votre licence pour effectuer l’action d’amélioration et que ces licences sont appliquées aux utilisateurs nécessaires.  

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous rencontrez des problèmes, faites-le nous savoir en publiant dans la communauté [Sécurité, confidentialité et conformité](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous supervisons la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Vue d’ensemble de Microsoft Secure Score](microsoft-secure-score.md)
- [Suivez votre historique de score de sécurité Microsoft et répondez aux objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Ce qui est à venir](microsoft-secure-score-whats-coming.md)
- [Nouveautés](microsoft-secure-score-whats-new.md)
