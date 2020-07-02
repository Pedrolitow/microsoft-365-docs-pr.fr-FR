---
title: Utiliser les actions d’amélioration dans le score de conformité Microsoft (aperçu)
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment gérer vos activités de conformité dans le score de conformité Microsoft en utilisant des actions d’amélioration.
ms.openlocfilehash: d10e04f144595e1976f4b20e894ccbc299aade7b
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016577"
---
# <a name="work-with-improvement-actions-in-compliance-score-preview"></a>Utiliser les actions d’amélioration dans le score de conformité (aperçu)

**Dans cet article :** Cet article explique comment **gérer votre flux de travail de conformité** avec des actions d’amélioration. Découvrez comment **attribuer des actions d’amélioration** pour l’implémentation et les tests, les affecter à des évaluateurs pour terminer et exporter des **rapports**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Gérer les flux de travail de conformité avec des actions d’amélioration

Les actions d’amélioration centralisent vos activités de conformité. Chaque action d’amélioration fournit des conseils détaillés sur la mise en œuvre pour vous aider à vous aligner sur les normes et réglementations sur la protection des données. Des actions peuvent être attribuées à des utilisateurs de votre organisation pour effectuer le travail d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements au cours de l’action d’amélioration.

Toutes vos améliorations sont répertoriées dans la page actions d’amélioration. En savoir plus sur [la façon de filtrer votre vue de vos actions d’amélioration et d’interpréter les États d’État](compliance-score-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Page des détails des actions d’amélioration

Chaque action d’amélioration dispose d’une page de détails indiquant son état actuel et les normes et exigences réglementaires associées. Des conseils détaillés sur l’implémentation incluent un lien **lancer maintenant** qui vous place dans la solution appropriée pour l’implémentation. Vous pouvez attacher la documentation d’implémentation et de test directement à la page de détails d’une action d’amélioration.

Pour afficher la page de détails d’une action d’amélioration :

1. Accédez à votre page actions d’amélioration.
2. Sélectionnez la ligne de l’action d’amélioration prévue, qui ouvre sa page de détails.

Vous pouvez facilement afficher l’action d’amélioration suivante ou précédente dans la liste en sélectionnant la flèche vers le haut ou vers le bas dans le coin supérieur droit de l’écran. Si vous avez filtré votre liste dans la page actions d’amélioration, le fait de remonter ou de descendre vous amène à l’élément suivant dans cette liste filtrée.

## <a name="assign-improvement-actions"></a>Affecter des actions d’amélioration

Pour commencer la mise en œuvre d’une action d’amélioration, vous pouvez effectuer le travail vous-même ou l’affecter à un autre utilisateur. La personne affectée peut être :

- Le propriétaire d’une stratégie d’entreprise
- Un ingénieur informatique
- Un autre employé responsable de l’exécution de la tâche

Une fois que vous avez identifié le cessionnaire approprié, assurez-vous qu’il dispose d’un [rôle suffisant dans le score de conformité](compliance-score-setup.md#set-user-permissions-and-assign-roles) (administrateur de conformité, administrateur de données de conformité, administrateur de sécurité ou administrateur général) pour effectuer le travail, puis procédez comme suit :

1. Dans la page Détails des actions d’amélioration, sélectionnez **modifier l’État** près de la section supérieure gauche de l’écran.

2. Dans le volet flyout état de modification, activez la case à cocher **affecté à** pour afficher une liste de **personnes suggérées** pour les utilisateurs. Vous pouvez sélectionner l’utilisateur dans la liste ou taper l’adresse de messagerie de la personne à laquelle vous souhaitez l’attribuer.

3. Sélectionnez **enregistrer et fermer**. L’utilisateur affecté reçoit un message électronique indiquant que l’action d’amélioration lui a été affectée, et il peut ensuite ouvrir l’action d’amélioration à partir de son tableau de bord.

L’utilisateur affecté peut ensuite effectuer les actions recommandées.

## <a name="perform-work-and-store-documentation"></a>Effectuer une documentation de travail et de magasin

Vous pouvez télécharger des fichiers et des notes relatifs à l’implémentation et au test directement dans la section **Notes et documentation** . Cet environnement est un référentiel centralisé sécurisé qui vous permet de démontrer la satisfaction des contrôles pour répondre aux normes et réglementations en matière de conformité. Tout utilisateur disposant d’un accès en lecture seule peut lire le contenu de cette section. Seuls les utilisateurs disposant de droits de modification peuvent télécharger et télécharger des fichiers et entrer ou modifier des notes.

Les champs de la section **Notes et documentation sont les** suivants :

### <a name="uploaded-documents"></a>Documents téléchargés

- Sélectionnez **gérer les documents** pour télécharger les fichiers appropriés.
- Lorsque le volet de menu contextuel gérer les documents s’ouvre, sélectionnez **Ajouter un document**, puis sélectionnez votre fichier dans votre système. Types de fichiers acceptés :
    - Documents (. doc,. xls,. ppt,. txt,. pdf)
    - Images (. jpg,. png)
    - Vidéo (. mkv)
    - Fichiers compressés (. zip,. rar)
- Une fois que votre fichier est résolu dans le volet, sélectionnez **Fermer**, ce qui enregistre automatiquement le fichier en pièce jointe. Vous verrez ensuite le fichier indiqué sous **documents téléchargés**.
- Pour télécharger ou supprimer le document, sélectionnez **gérer les documents** sous la liste des documents. Dans le volet flyout, cliquez ou appuyez sur la ligne document pour la mettre en surbrillance, puis sélectionnez **Télécharger** ou **supprimer**.

### <a name="implementation-notes-test-notes-and-additional-notes"></a>Notes de mise en œuvre, notes de test et notes supplémentaires

- Pour ajouter des notes dans l’un de ces champs, sélectionnez **modifier les notes de mise en œuvre** sous l’un de ces champs.
- Lorsque le volet flyout s’ouvre, entrez des notes dans le champ texte, puis sélectionnez **enregistrer et fermer**.
- Pour modifier des notes, sélectionnez **modifier les notes d’implémentation**, apporter vos modifications, puis cliquez sur **enregistrer et fermer**.

Il n’y a pas de limite de caractères dans les champs Notes. Nous vous recommandons de conserver des notes résumées afin de pouvoir les afficher et les modifier facilement à partir de la page Détails des actions d’amélioration.

## <a name="change-improvement-action-status"></a>Modifier l’état de l’action d’amélioration

Vous pouvez enregistrer l’État et la date d’implémentation, ainsi que l’État et la date du test pour chaque action d’amélioration. Les champs d' **État** de **mise en œuvre** et de test peuvent être modifiés par tout utilisateur disposant d’autorisations de modification, et non simplement par la personne affectée.

Pour modifier l’état d’une action d’amélioration, sélectionnez **modifier l’État** dans la section supérieure gauche de la page de détails. Vous trouverez ci-dessous les champs et les options d’état disponibles :

- **État de l’implémentation**
    - **Non implémenté** -action pas encore implémentée
    - **Implemented** -action implémentée
    - **Autre implémentation** : sélectionnez cette option si vous avez utilisé d’autres outils tiers ou si vous avez effectué d’autres actions qui ne sont pas incluses dans les recommandations de Microsoft.
    - L’action **planifiée** est planifiée pour l’implémentation
    - **Hors de portée** : l’action n’est pas pertinente pour votre organisation et ne contribue pas à votre score
- **Date d’implémentation**: disponible pour sélection lorsque l’état de mise en œuvre est « implémenté » ou « autre implémentation »
- **État du test**: disponible pour sélection lorsque l’état de mise en œuvre est « implémenté » ou « autre implémentation » :
    - **Non évalué** : l’action n’a pas été testée
    - L’implémentation **passée**a été vérifiée par un évaluateur
    - Échec du test à **faible risque** pour les tests, risque faible
    - **Risque moyen échoué** -test ayant échoué, risque moyen
    - **Échec à haut risque** – tests échoués, à risque élevé
    - **Non inclus dans l’étendue** : l’action est hors de portée pour l’évaluation et ne contribue pas à votre score
- **Date du test**: afficher la fenêtre contextuelle du calendrier pour sélectionner la date

Les actions courantes sont synchronisées entre les groupes. Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration gérées par vous-même, toutes les mises à jour apportées aux détails de l’implémentation ou à l’état d’une action sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences dans plusieurs réglementations.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Affecter une action d’amélioration à l’évaluateur pour achèvement

Une fois le travail terminé, de tester et de charger des preuves, l’étape suivante consiste à affecter l’action d’amélioration à un évaluateur pour validation.

Les types d’évaluateurs sont les suivants :

- Des évaluateurs internes qui effectuent la validation des contrôles au sein de votre organisation ;
- Des évaluateurs externes qui examinent, vérifient et certifient la conformité, tels que les organisations indépendantes tierces qui auditent les services Cloud de Microsoft

L’évaluateur valide le travail et examine la documentation, puis sélectionne l’état de test approprié.

**Si le statut du test est défini sur « passé »**: l’action est terminée et les points obtenus indiquent le nombre maximal de points atteints. Les points sont ensuite pris en compte dans le score de conformité global.

**Si le statut du test est défini sur « échec »**: l’action ne remplit pas les conditions requises et l’évaluateur peut l’attribuer à nouveau à l’utilisateur approprié pour un travail supplémentaire.

## <a name="export-a-report"></a>Exporter un rapport

Sélectionnez **Exporter** dans le coin supérieur gauche de votre écran pour télécharger une feuille de calcul Excel contenant toutes vos actions d’amélioration et les catégories de filtre affichées dans la page actions d’amélioration.