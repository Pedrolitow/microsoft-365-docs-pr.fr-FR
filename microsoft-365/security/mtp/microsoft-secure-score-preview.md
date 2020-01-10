---
title: Microsoft Secure score (aperçu)
description: Décrit Microsoft Secure score dans le centre de sécurité Microsoft 365, la façon dont les détails sont calculés et les administrateurs de sécurité qui peuvent s’y attendre.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Secure score, centre de sécurité, actions d’amélioration
ms.prod: w10
ms.mktglfcycl: deploy
ms.localizationpriority: medium
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
ms.openlocfilehash: 0f54ee771f4358c5c99c3338366eb277013c15e3
ms.sourcegitcommit: a2e9ab69f99f2069372ccfffd9ef2ffbd8568826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "41012177"
---
# <a name="microsoft-secure-score-preview"></a>Microsoft Secure score (aperçu)

>[!IMPORTANT]
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft Secure score est une mesure de la position de sécurité d’une organisation, avec un nombre supérieur indiquant d’autres actions d’amélioration. Le suivi des recommandations de score de sécurité peut protéger votre organisation contre les menaces. À partir d’un tableau de bord centralisé dans le centre de sécurité Microsoft 365, les organisations peuvent surveiller et gérer la sécurité des identités, des données, des applications, des périphériques et de l’infrastructure de Microsoft 365.

Le score de sécurité aide les organisations :  

* Rapport sur l’état actuel de l’état de sécurité de l’organisation.
* Améliorez la position de la sécurité en fournissant des possibilités de détectabilité, de visibilité, de conseils et de contrôle.  
* Comparez avec des benchmarks et établissez des indicateurs de performance clés (KPI).

Les organisations ont accès à des visualisations robustes de mesures et tendances, à une intégration à d’autres produits Microsoft, à une comparaison de scores avec des organisations similaires, et bien plus encore. Le score peut également indiquer quand les solutions tierces ont résolu les actions recommandées.

En outre, vous pouvez accéder à vos recommandations et à votre score via l' [API Microsoft Graph](https://www.microsoft.com/security/partnerships/graph-security-api). En savoir plus sur le [type de ressource de score sécurisé](https://go.microsoft.com/fwlink/?linkid=2092996).

## <a name="how-it-works"></a>Mode de fonctionnement

Vous disposez de points pour configurer les fonctionnalités de sécurité recommandées, effectuer des tâches liées à la sécurité ou traiter l’action d’amélioration avec une application ou un logiciel tiers. Certaines actions d’amélioration donnent uniquement des points lorsqu’ils sont complètement terminés, et d’autres les déposent si elles sont terminées pour certains périphériques ou utilisateurs. Si vous ne pouvez pas ou ne souhaitez pas arrêter une des actions d’amélioration, vous pouvez choisir d’accepter le risque ou le risque restant.

Nous vous montrons l’ensemble complet des améliorations possibles, quelle que soit la licence, afin que vous puissiez comprendre les meilleures pratiques en matière de sécurité et améliorer votre score. Votre posture de sécurité absolue est représentée par la fonction de chiffrement sécurisé, qui reste la même quelle que soit la licence de produit que possède votre organisation. N’oubliez pas que la sécurité doit être équilibrée avec la convivialité et que toutes les recommandations ne peuvent pas fonctionner pour votre environnement.

Votre score est mis à jour en temps réel afin de refléter les informations présentées dans les pages de l’action visualisations et amélioration. Le score sécurisé est également synchronisé quotidiennement pour recevoir les données système relatives aux points obtenus pour chaque action.

### <a name="how-improvement-actions-are-scored"></a>Comment les actions d’amélioration sont évaluées

Chaque action d’amélioration vaut 10 points maximum. La plupart sont évaluées de manière binaire : Si vous implémentez l’action d’amélioration, par exemple créer une nouvelle stratégie ou activer un paramètre spécifique, vous obtenez 100% des points. Pour les autres actions d’amélioration, les points sont fournis sous la forme d’un pourcentage de la configuration totale. Par exemple, si l’action d’amélioration indique que vous obtenez 30 points en protégeant tous vos utilisateurs à l’aide de l’authentification multifacteur et que vous ne disposez que de 5 de 100 total d’utilisateurs protégés, vous disposez d’un score partiel d’environ 2 points (5 protected/100 Total * 30 max pts = 2 pts de score partiel).

### <a name="products-included-in-secure-score"></a>Produits inclus dans le score de sécurité

Il existe actuellement des recommandations pour Office 365 (notamment SharePoint Online, Exchange Online, OneDrive entreprise, la protection des informations Microsoft, etc.), Azure AD, Intune, Microsoft Defender ATP et la sécurité des applications Cloud. Des recommandations pour d’autres produits de sécurité seront bientôt disponibles. Les recommandations ne couvrent pas toutes les surfaces d’attaque associées à chaque produit, mais il s’agit d’une base de référence correcte. Vous pouvez également marquer les actions d’amélioration telles qu’elles sont couvertes par un tiers.

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
* User administrator
* Administrateur de service
* Lecteur Sécurité
* Opérateur de sécurité
* Lecteur global

### <a name="graph-api"></a>API Graph

Pour accéder à l’API Graph, vous devez disposer de l’une des étendues suivantes en plus d’un rôle :

* Étendue securityevents. Read. All (pour les rôles en lecture seule)
* Étendue securityevents. ReadWrite. All (pour les rôles lecture et écriture)

## <a name="gain-visibility-into-your-security-posture"></a>Obtenir une visibilité sur la position de la sécurité

Pour vous aider à trouver plus rapidement les informations dont vous avez besoin, les actions d’amélioration de Microsoft sont organisées en groupes :

* Identity (comptes Azure AD & rôles, avec Azure ATP bientôt disponible)
* Data (protection des informations Microsoft)
* Appareil (appareils Microsoft Defender ATP)
* Application (applications de messagerie et de Cloud, y compris Office 365 et Microsoft Cloud App Security)
* Infrastructure (ressources Azure)

Dans la page de présentation de Microsoft Secure score, vous pouvez voir la répartition des points entre ces groupes et les points disponibles. La page de vue d’ensemble est également l’endroit où vous pouvez obtenir une vue d’ensemble du score total, de la tendance historique de votre score de sécurité avec comparaisons de référence et des actions d’amélioration hiérarchisée qui peuvent être prises pour améliorer votre score.

![](../media/secure-score/secure-score-homepage.png)
*Page d’accueil du score sécurisé figure 1 : page de présentation de Microsoft Secure score*

## <a name="take-action-to-improve-your-score"></a>Prendre des mesures pour améliorer votre score

L’onglet actions d’amélioration répertorie les recommandations de sécurité qui concernent les surfaces d’attaque possibles, ainsi que leur état (terminé, planifié, risque accepté, tiers et adresse). Vous pouvez rechercher, filtrer et regrouper toutes les actions d’amélioration.  

### <a name="ranking"></a>Placé

Le classement repose sur le nombre de points restants à atteindre, les difficultés d’implémentation, l’impact de l’utilisateur et la complexité. Les actions d’amélioration les plus élevées ont un grand nombre de points restants, avec une faible Difficulté, un impact sur l’utilisateur et une complexité.

### <a name="actions"></a>Actions

Lorsque vous sélectionnez une action d’amélioration spécifique, un menu volant de page entière s’affiche.  

![Exemple](../media/secure-score/secure-score-improvement-action.png)
de menu contextuel d’action d’amélioration*figure 2 : exemple de menu contextuel d’action d’amélioration*

Pour terminer l’action, vous disposez de plusieurs options :

* Sélectionnez **gérer** pour accéder à l’écran de configuration et effectuer la modification. Vous obtiendrez ensuite les points que l’action vaut, visible dans le survol. Les points prennent généralement environ 24 heures à mettre à jour.

* Sélectionnez **partager** pour copier le lien direct vers l’action d’amélioration ou choisissez la plateforme pour partager le lien, comme courrier électronique, Microsoft Teams, planificateur Microsoft ou ServiceNow. La sélection de ServiceNow vous permettra de créer un ticket de modification qui sera visible dans ServiceNow et le centre de sécurité Microsoft 365. Pour en savoir plus, consultez la rubrique [Microsoft 365 Security Center and ServiceNow Integration](tickets.md).

* Sélectionnez **modifier le statut et les notes** pour modifier tous les États manuels ou enregistrer des notes propres à l’action d’amélioration. Vous pouvez filtrer ou regrouper selon les statuts dans l’onglet actions d’amélioration. Les statues que vous pouvez sélectionner sont les suivants :

    * **À résoudre** : vous reconnaissez que l’action d’amélioration est nécessaire et que vous envisagez d’y remédier à un moment donné. Cet État s’applique également aux actions détectées comme partielles, mais pas complètement terminées.
    * **Planifié** : des plans concrets sont en place pour effectuer l’action d’amélioration.
    * **Risque accepté** : la sécurité doit toujours être équilibrée avec la convivialité et toutes les recommandations ne fonctionnent pas pour votre environnement. Lorsque c’est le cas, vous pouvez choisir d’accepter le risque ou le risque restant et de ne pas appliquer l’action d’amélioration. Vous n’aurez pas de points, mais l’action ne sera plus visible dans la liste des actions d’amélioration. Vous pouvez afficher cette action dans l’historique ou l’annuler à tout moment.
    * **Résoudre** par le biais d’un tiers : l’action d’amélioration a déjà été traitée par une application ou un logiciel tiers. Vous obtiendrez les points que l’action vaut, afin que votre score reflète mieux votre position de sécurité globale. Si un tiers ne couvre plus le contrôle, vous pouvez choisir un autre État. N’oubliez pas que Microsoft n’aura aucune visibilité sur l’intégralité de la mise en œuvre si l’action d’amélioration est marquée comme résolue par un tiers.

### <a name="prerequisites"></a>Conditions requises

Les conditions préalables dans la section implémentation répertorient toutes les licences qui doivent être obtenues ou les actions qui doivent être effectuées avant que l’action d’amélioration ne soit traitée. Assurez-vous que votre licence comporte suffisamment de sièges pour effectuer l’action d’amélioration et que ces licences sont appliquées aux utilisateurs nécessaires.  

## <a name="track-your-score-history-and-meet-goals"></a>Suivre l’historique des résultats et atteindre les objectifs

Vous pouvez afficher un graphique du score de votre organisation au fil du temps sous l’onglet **historique** . sous le graphique se trouve une liste de toutes les actions effectuées dans la plage de temps sélectionnée et leurs attributs, tels que les points et la catégorie obtenus. Vous pouvez personnaliser une plage de dates et filtrer par catégorie.

Dans l’onglet **mesures & tendances** , il existe plusieurs graphiques et graphiques qui vous permettent de mieux comprendre les tendances et de définir les objectifs. Vous pouvez définir la plage de dates pour la page entière des visualisations. Les visualisations sont les suivantes :

* **Votre zone de score sécurisée** , personnalisée en fonction des objectifs de votre organisation et des définitions des plages de scores correctes, correctes et incorrectes.
* **Tendance de régression** : chronologie de points qui ont régressé en raison de modifications apportées à la configuration, à l’utilisateur ou au périphérique.  
* **Tendance de comparaison** — le score de sécurité de votre organisation est comparé à d’autres utilisateurs. Cet affichage peut inclure des lignes représentant le score moyen des organisations avec un nombre de sièges similaires et un affichage de comparaison personnalisé que vous pouvez définir.
* **Tendance d’acceptation des risques** — chronologie des actions d’amélioration marquées comme « risque accepté ».
* **Noter les modifications** : nombre de points obtenus, de régression ou de nouvelles actions ajoutées, ainsi que le changement de score suivant, dans la plage de dates spécifiée.

## <a name="risk-awareness"></a>Sensibilisation aux risques

Microsoft Secure score est un résumé numérique de votre position de sécurité basée sur les configurations système, le comportement de l’utilisateur et d’autres mesures liées à la sécurité ; il ne s’agit pas d’une mesure absolue de la probabilité de violation de votre système ou de vos données. Il représente plutôt la mesure dans laquelle vous avez adopté des contrôles de sécurité dans votre environnement Microsoft, ce qui peut vous aider à compenser le risque d’être compromis. Aucun service en ligne n’est totalement immunisé contre les violations de sécurité et le score sécurisé ne doit pas être interprété comme une garantie d’une violation de sécurité.

## <a name="whats-coming"></a>Qu’est-ce qui arrive ?

### <a name="mfa-improvement-action-updates"></a>Mises à jour de l’action d’amélioration MFA

Pour refléter la nécessité pour les entreprises de garantir la sécurité maximale lors de l’application des stratégies qui fonctionnent avec leur entreprise, le score de sécurité Microsoft supprime trois actions d’amélioration axées sur l’authentification multifacteur et en ajoutant deux.

Les trois qui seront supprimés :
- Inscrire tous les utilisateurs pour l’authentification multifacteur
- Exiger l’authentification multifacteur pour tous les utilisateurs
- Exiger l’authentification multifacteur pour les rôles privilège Azure AD

Nouvelles actions d’amélioration :
- S’assurer que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé
- Exiger MFA pour les rôles d’administration

 Ces nouvelles actions d’amélioration requièrent l’enregistrement de vos utilisateurs ou administrateurs pour l’authentification multifacteur (MFA) dans votre répertoire et l’établissement de l’ensemble approprié de stratégies répondant à vos besoins organisationnels. L’objectif principal est de la flexibilité tout en s’assurant que tous vos utilisateurs et administrateurs peuvent s’authentifier avec plusieurs facteurs ou des invites de vérification d’identité basées sur les risques. Cela peut prendre la forme de paramètres de sécurité par défaut qui permettent à Microsoft de déterminer quand il faut défier les utilisateurs à l’authentification multifacteur, ou si plusieurs stratégies appliquent des décisions délimitées.

## <a name="whats-new"></a>Nouveautés 

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité et améliore la convivialité, nous avons apporté des modifications. Votre score et le score maximal possible ont été modifiés. Toutefois, cela n’implique pas de modification de votre position de sécurité.

### <a name="updated-interface-and-functionality"></a>Interface et fonctionnalité mises à jour

* Toutes les nouvelles mesures et tendances pour les CISO et les discussions au niveau des prospects
* Nouvelles façons de suivre et d’évaluer votre score
* Meilleure approche et compréhension pour les régressions de score
* Filtrage, balisage, recherche et regroupement de vos actions d’amélioration
* Gérer vos objectifs à venir à l’aide de projections de score et des actions planifiées
* Et bien plus encore !

### <a name="removed-not-scored-and-review-improvement-actions"></a>Suppression des actions d’amélioration « non notées » et « réviser »

L’un des principes du score de sécurité est que le score doit être standardisé et facile à mettre en relation. Les actions d’amélioration qui ne sont pas mesurables ou exploitables provoquent des confusions. Un score de sécurité Microsoft n’a de sens que si chaque recommandation peut avoir un effet clair sur le score. Les actions d’amélioration non évaluées ne sont pas quantifiables, et les actions d’amélioration ne sont pas mesurées de la même manière que les autres actions d’amélioration.

Pour ces raisons, toutes les actions d’amélioration qui n’ont pas été évaluées ou nécessitaient une cadence de révision ont été temporairement supprimées. Aucune action n’est nécessaire de votre part.

### <a name="simplification-of-the-point-system"></a>Simplification du système de point

Pour standardiser les points sur plusieurs expériences, chaque point d’action d’amélioration de score sécurisé a été mis à jour pour avoir une valeur de 10 points maximum. Il est nécessaire d’être plus cohérent à travers l’allongement des contrôles de sécurité que nous avons aujourd’hui et ceux que nous allons ajouter à l’avenir. S’il s’agit d’une modification importante et que vous verrez des totaux de point de dépôt, aucune modification n’est apportée à votre position de sécurité.

## <a name="we-want-to-hear-from-you"></a>Nous souhaitons être informés

Si vous rencontrez des problèmes, indiquez-nous en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.
