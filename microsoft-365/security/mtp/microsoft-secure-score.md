---
title: Degré de sécurisation Microsoft
description: Décrit Microsoft Secure score dans le centre de sécurité Microsoft 365, la façon dont les détails sont calculés et les administrateurs de la sécurité qui peuvent s’y attendre.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Secure score, centre de sécurité, actions d’amélioration
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: ec659a939064d34d3e0cc078a90cd343e495ae58
ms.sourcegitcommit: 4986032867b8664a215178b5e095cbda021f3450
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2020
ms.locfileid: "41957369"
---
# <a name="microsoft-secure-score"></a>Degré de sécurisation Microsoft

Microsoft Secure score est une mesure de la position de sécurité d’une organisation, avec un nombre supérieur indiquant d’autres actions d’amélioration. Le suivi des recommandations de score de sécurité peut protéger votre organisation contre les menaces. À partir d’un tableau de bord centralisé dans le centre de sécurité Microsoft 365, les organisations peuvent surveiller et gérer la sécurité des identités, des données, des applications, des périphériques et de l’infrastructure de Microsoft 365.

Le score de sécurité aide les organisations :

* Rapport sur l’état actuel de l’état de sécurité de l’organisation.
* Améliorez la position de la sécurité en fournissant des possibilités de détectabilité, de visibilité, de conseils et de contrôle.  
* Comparez avec des benchmarks et établissez des indicateurs de performance clés (KPI).

Les organisations ont accès à des visualisations robustes de mesures et tendances, à une intégration à d’autres produits Microsoft, à une comparaison de scores avec des organisations similaires, et bien plus encore. Le score peut également indiquer quand les solutions tierces ont résolu les actions recommandées.

En outre, vous pouvez accéder à vos recommandations et à votre score via l' [API Microsoft Graph](https://www.microsoft.com/security/partnerships/graph-security-api). En savoir plus sur le [type de ressource de score sécurisé](https://go.microsoft.com/fwlink/?linkid=2092996).

## <a name="how-it-works"></a>Mode de fonctionnement

Vous disposez de points pour configurer les fonctionnalités de sécurité recommandées, effectuer des tâches liées à la sécurité (telles que l’affichage des rapports) ou traiter l’action d’amélioration avec une application ou un logiciel tiers. Certaines actions d’amélioration donnent uniquement des points lorsqu’ils sont complètement terminés, et d’autres les déposent si elles sont terminées pour certains périphériques ou utilisateurs.

Nous vous montrons l’ensemble complet des améliorations possibles, quelle que soit la licence, afin que vous puissiez comprendre les meilleures pratiques en matière de sécurité et améliorer votre score. Votre posture de sécurité absolue est représentée par la fonction de chiffrement sécurisé, qui reste la même quelle que soit la licence de produit que possède votre organisation. N’oubliez pas que la sécurité doit être équilibrée avec la convivialité et que toutes les recommandations ne peuvent pas fonctionner pour votre environnement.

Votre score est mis à jour en temps réel afin de refléter les informations présentées dans les pages de l’action visualisations et amélioration. Le score sécurisé est également synchronisé quotidiennement pour recevoir les données système relatives aux points obtenus pour chaque action.

### <a name="how-improvement-actions-are-scored"></a>Comment les actions d’amélioration sont évaluées

La plupart sont évaluées de manière binaire : Si vous implémentez l’action d’amélioration, par exemple créer une nouvelle stratégie ou activer un paramètre spécifique, vous obtenez 100% des points. Pour les autres actions d’amélioration, les points sont fournis sous la forme d’un pourcentage de la configuration totale. Par exemple, si l’action d’amélioration indique que vous obtenez 30 points en protégeant tous vos utilisateurs à l’aide de l’authentification multifacteur et que vous ne disposez que de 5 de 100 total d’utilisateurs protégés, vous disposez d’un score partiel d’environ 2 points (5 protected/100 Total * 30 max pts = 2 pts de score partiel).

### <a name="products-included-in-secure-score"></a>Produits inclus dans le score de sécurité

Il existe actuellement des recommandations pour Office 365 (notamment SharePoint Online, Exchange Online, OneDrive entreprise, la protection des informations Microsoft, etc.), Azure AD et la sécurité des applications Cloud. Des recommandations pour d’autres produits de sécurité, tels que Azure ATP et Microsoft Defender ATP, sont bientôt disponibles. Les recommandations ne couvrent pas toutes les surfaces d’attaque associées à chaque produit, mais il s’agit d’une base de référence correcte. Vous pouvez également marquer les actions d’amélioration telles qu’elles sont couvertes par un tiers.

## <a name="required-permissions"></a>Autorisations requises

Pour avoir l’autorisation d’accéder à la note de sécurité Microsoft, vous devez disposer de l’un des rôles suivants dans Azure Active Directory.

### <a name="read-and-write-roles"></a>Rôles de lecture et d’écriture

Avec l’accès en lecture et en écriture, vous pouvez effectuer des modifications et interagir directement avec le score de sécurité. Vous pouvez également attribuer un accès en lecture seule aux autres utilisateurs.

* Administrateur général
* Administrateur de sécurité
* Administrateur Exchange
* Administrateur SharePoint

### <a name="read-only-roles"></a>Rôles en lecture seule

Avec un accès en lecture seule, vous n’êtes pas en mesure de modifier l’État ou les notes pour une action d’amélioration, de modifier des zones de score ou de modifier des comparaisons personnalisées.

* Administrateur du support technique
* Administrateur d’utilisateurs
* Administrateur de service
* Lecteur Sécurité
* Opérateur de sécurité
* Lecteur général

### <a name="graph-api"></a>API Graph

Pour accéder à l’API Graph, vous devez disposer de l’une des étendues suivantes en plus d’un rôle :

* Étendue securityevents. Read. All (pour le rôle en lecture seule)
* Étendue securityevents. ReadWrite. All (pour le rôle de lecture et d’écriture)

## <a name="gain-visibility-into-your-security-posture"></a>Obtenir une visibilité sur la position de la sécurité

Pour vous aider à trouver plus rapidement les informations dont vous avez besoin, les actions d’amélioration de Microsoft sont organisées en groupes :

* Identity (comptes Azure AD & rôles, avec Azure ATP bientôt disponible)
* Data (protection des informations Microsoft)
* Appareil (appareils Microsoft Defender ATP, bientôt disponible)
* Application (applications de messagerie et de Cloud, y compris Office 365 et Microsoft Cloud App Security)
* Infrastructure (ressources Azure)

Dans la page de présentation de Microsoft Secure score, vous pouvez voir la répartition des points entre ces groupes et les points disponibles. La page de vue d’ensemble est également l’endroit où vous pouvez obtenir une vue d’ensemble du score total, de la tendance historique de votre score de sécurité avec comparaisons de référence et des actions d’amélioration hiérarchisée qui peuvent être prises pour améliorer votre score.

![](../media/secure-score/homepage-original.png)
*Page d’accueil du score sécurisé figure 1 : page de présentation de Microsoft Secure score*

## <a name="take-action-to-improve-your-score"></a>Prendre des mesures pour améliorer votre score

L’onglet actions d’amélioration répertorie les recommandations de sécurité qui concernent les surfaces d’attaque possibles, ainsi que leur état (terminé, non terminé, résolu par un tiers et ignoré). Vous pouvez rechercher, filtrer et regrouper toutes les actions d’amélioration.

### <a name="ranking"></a>Placé

Le classement repose sur le nombre de points restants à atteindre, les difficultés d’implémentation, l’impact de l’utilisateur et la complexité. Les actions d’amélioration les plus élevées ont un grand nombre de points restants, avec une faible Difficulté, un impact sur l’utilisateur et une complexité.

### <a name="actions"></a>Actions

Les actions étiquetées [non notées] ne sont pas suivies par le score de sécurité Microsoft. Vous pouvez toujours prendre des mesures, mais ces dernières n’affecteront pas votre score. Si une action est suivie par le score de sécurité Microsoft à l’avenir et que vous l’avez déjà effectuée, votre score de sécurité reflète automatiquement le changement.

Lorsque vous sélectionnez une action d’amélioration spécifique, un survol s’affiche. Pour terminer l’action, vous disposez de plusieurs options :

1. Sélectionnez **afficher les paramètres** pour accéder à l’écran de configuration et effectuer les modifications. Vous pouvez ensuite obtenir les points que l’action est utile, visible en haut du volant. La mise à jour des points peut prendre jusqu’à 24 heures.

2. Sélectionnez **résoudre via un tiers** , car l’action d’amélioration a déjà été traitée par une application ou un logiciel tiers. Vous obtenez les points que l’action vaut, afin que votre score sécurisé reflète mieux votre position de sécurité globale. Si un tiers ne couvre plus le contrôle, vous pouvez marquer l’action d’amélioration comme non terminée. N’oubliez pas que Microsoft n’a aucune visibilité sur le respect des exigences de score si l’action d’amélioration est marquée comme résolue via un tiers.

3. Sélectionnez **Ignorer** , car vous avez décidé d’accepter le risque et de ne pas appliquer l’action d’amélioration. Une fois que vous ignorez une action d’amélioration, le nombre total de points de score sécurisé que vous pouvez atteindre est réduit. Vous pouvez afficher cette action dans l’historique ou l’annuler à tout moment.

4. Sélectionnez **Review** , car l’action d’amélioration vous oblige à examiner régulièrement une partie de votre environnement pour gagner et conserver des points. Par exemple, les règles de transfert de boîtes aux lettres doivent être vérifiées chaque semaine afin de s’assurer que les données ne sont pas exportées à partir de votre réseau. Vous n’avez pas besoin d’effectuer des modifications, mais une action doit être effectuée. Si vous examinez régulièrement les règles, vous recevrez les points. Si ce n’est pas le cas, le score est réduit.

![Exemple d’action d’amélioration du score sécurisé](../media/secure-score/secure-score1x450.png) ![Exemple d’action d’amélioration de la vérification du score sécurisé](../media/secure-score/secure-score2x450.png)

*Figures 2 & 3 : lanceurs d’actions d’amélioration*

## <a name="monitor-improvements-over-time"></a>Surveiller les améliorations au fil du temps

Vous pouvez afficher un graphique du score de votre organisation au fil du temps sous l’onglet **historique** . sous le graphique se trouve une liste de toutes les actions effectuées dans la plage de temps sélectionnée et leurs attributs, tels que les points et la catégorie obtenus. Vous pouvez personnaliser une plage de dates et filtrer par catégorie.

## <a name="risk-awareness"></a>Sensibilisation aux risques

Microsoft Secure score est un résumé numérique de votre position de sécurité basée sur les configurations système, le comportement de l’utilisateur et d’autres mesures liées à la sécurité ; il ne s’agit pas d’une mesure absolue de la probabilité de violation de votre système ou de vos données. Il représente plutôt la mesure dans laquelle vous avez adopté des contrôles de sécurité dans votre environnement Microsoft, ce qui peut vous aider à compenser le risque d’être compromis. Aucun service en ligne n’est totalement immunisé contre les violations de sécurité et le score sécurisé ne doit pas être interprété comme une garantie d’une violation de sécurité.

## <a name="whats-new"></a>Nouveautés

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité, nous avons apporté des modifications.

### <a name="removed-not-scored-improvement-actions"></a>Suppression des actions d’amélioration « non notées »

L’un des principes du score de sécurité est que le score doit être standardisé et facile à mettre en relation. Les actions d’amélioration qui ne sont pas mesurables ou exploitables provoquent des confusions. Un score de sécurité Microsoft n’a de sens que si chaque recommandation peut avoir un effet clair sur le score. Les actions d’amélioration ne sont pas évaluées.  

Pour ces raisons, toutes les actions d’amélioration qui n’ont pas été évaluées ont été supprimées. Aucune action n’est nécessaire de votre part.

## <a name="whats-coming"></a>Qu’est-ce qui arrive ?

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité et améliore la convivialité, nous apportons des modifications dans le futur proche. Votre score et le score maximal possible seront modifiés. Toutefois, cela n’implique pas de modification de votre position de sécurité.

### <a name="removing-improvement-actions-from-intune"></a>Suppression des actions d’amélioration d’Intune

Après une évaluation des actions de Microsoft Secure scores improved fournies par Intune, il a été décidé de ne pas fournir une représentation utile de la position de sécurité des appareils dans les organisations. Au lieu de se concentrer sur les stratégies, nous nous efforcerons de mettre en place des contrôles de sécurité qui évaluent directement l’état de configuration des appareils.

Les actions d’amélioration d’Intune suivantes seront supprimées :

- Activer la gestion des appareils mobiles Microsoft Intune
- Créer une stratégie de conformité Microsoft Intune pour Android
- Créer une stratégie de conformité Microsoft Intune pour Android pour le travail
- Créer une stratégie de protection des applications Microsoft Intune pour Android
- Créer une stratégie de protection des applications Microsoft Intune pour iOS
- Marquer les appareils sans aucune stratégie de conformité Microsoft Intune attribuée comme non conforme
- Créer une stratégie de conformité Microsoft Intune pour iOS
- Créer une stratégie de conformité Microsoft Intune pour macOS
- Créer une stratégie de conformité Microsoft Intune pour Windows
- Créer un profil de configuration Microsoft Intune pour Android
- Créer un profil de configuration Microsoft Intune pour Android pour le travail
- Créer un profil de configuration Microsoft Intune pour macOS
- Créer un profil de configuration Microsoft Intune pour iOS
- Créer un profil de configuration Microsoft Intune pour Windows
- Activer la détection jailbreak améliorée dans Microsoft Intune
- Exiger l’application des correctifs sur tous les appareils, les antivirus et les pare-feu activés
- Activer l’intégration de Windows Defender ATP dans Microsoft Intune
- Créer une stratégie de protection des informations Windows Microsoft Intune
- Exiger que tous les appareils disposent de configurations de sécurité avancées
- Vérifier toutes les semaines les périphériques bloqués

### <a name="removing-improvement-actions-that-dont-meet-expectations-for-reliable-measurement"></a>Suppression des actions d’amélioration qui ne répondent pas aux attentes en matière de mesure fiable

Pour vous assurer que le score de sécurité de Microsoft est significatif et que chaque action d’amélioration est mesurable et fiable, nous supprimons les actions d’amélioration suivantes.

- Activer l’enregistrement des données d’audit
- Découverte des applications informatiques de clichés instantanés risquées et non conformes
- Passer en revue les autorisations & bloquer les applications OAuth à risque connectées à votre environnement
- Configurer le contrôle de version sur les bibliothèques de documents SharePoint Online
- Stocker des documents utilisateur dans OneDrive entreprise
- Ne pas autoriser la délégation de boîte aux lettres
- Autoriser les liens de partage d’invités anonymes pour les sites et les documents
- Configurer des stratégies de pièces jointes approuvées ATP Office 365
- Configurer les liens fiables Office 365 pour vérifier les URL

### <a name="mfa-improvement-action-updates"></a>Mises à jour de l’action d’amélioration MFA

Pour refléter la nécessité pour les entreprises de garantir la sécurité maximale lors de l’application des stratégies qui fonctionnent avec leur entreprise, le score de sécurité Microsoft supprime trois actions d’amélioration axées sur l’authentification multifacteur et en ajoutant deux.

Les trois qui seront supprimés :

- Inscrire tous les utilisateurs pour l’authentification multifacteur
- Exiger l’authentification multifacteur pour tous les utilisateurs
- Exiger l’authentification multifacteur pour les rôles privilège Azure AD

Nouvelles actions d’amélioration ajoutées :

- S’assurer que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé
- Exiger MFA pour les rôles d’administration

 Ces nouvelles actions d’amélioration requièrent l’enregistrement de vos utilisateurs ou administrateurs pour l’authentification multifacteur (MFA) dans votre répertoire et l’établissement de l’ensemble approprié de stratégies répondant à vos besoins organisationnels. L’objectif principal est de la flexibilité tout en s’assurant que tous vos utilisateurs et administrateurs peuvent s’authentifier avec plusieurs facteurs ou des invites de vérification d’identité basées sur les risques. Cela peut prendre la forme de paramètres de sécurité par défaut qui permettent à Microsoft de déterminer quand il faut défier les utilisateurs à l’authentification multifacteur, ou si plusieurs stratégies appliquent des décisions délimitées.

### <a name="removing-review-improvement-actions"></a>Suppression des actions d’amélioration « révision »

L’un des principes du score de sécurité est que le score doit être standardisé et facile à mettre en relation. Les actions d’amélioration qui ne sont pas mesurables ou exploitables provoquent des confusions. Un score de sécurité Microsoft n’a de sens que si chaque recommandation peut avoir un effet clair sur le score. Examiner les actions d’amélioration ne sont pas mesurées de la même façon que les autres actions d’amélioration.  

Pour ces raisons, toutes les actions d’amélioration nécessitant une cadence de révision seront temporairement supprimées. Aucune action n’est nécessaire de votre part.

### <a name="simplification-of-the-point-system"></a>Simplification du système de point

Pour standardiser les points sur plusieurs expériences, chaque point d’action d’amélioration de score sécurisé est mis à jour avec une valeur de 10 points maximum. Il est nécessaire d’être plus cohérent à travers l’allongement des contrôles de sécurité que nous avons aujourd’hui et ceux que nous allons ajouter à l’avenir. S’il s’agit d’une modification importante et que vous verrez des totaux de point de dépôt, aucune modification n’est apportée à votre position de sécurité.  

### <a name="preview-features"></a>Fonctionnalités de préversion

Les fonctionnalités suivantes seront incluses dans la [version d’évaluation](microsoft-secure-score-preview.md):

* Toutes les nouvelles mesures et tendances pour les CISO et les discussions au niveau des prospects
* Nouvelles façons de suivre et d’évaluer votre score
* Suivi et surveillance améliorés des régressions de score
* Filtrage, balisage, recherche et regroupement de vos actions d’amélioration
* Gérer vos objectifs à venir à l’aide de projections de score et des actions planifiées
* Et bien plus encore !

## <a name="we-want-to-hear-from-you"></a>Nous souhaitons être informés

Si vous rencontrez des problèmes, indiquez-nous en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.
