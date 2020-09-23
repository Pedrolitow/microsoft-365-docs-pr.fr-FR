---
title: Affecter et effectuer des actions d’amélioration dans le gestionnaire de conformité Microsoft
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
description: Découvrez comment effectuer une implémentation et des tests sur les contrôles dans le gestionnaire de conformité Microsoft. Affecter le travail, stocker la documentation et exporter des rapports.
ms.openlocfilehash: 99b08ca1336c3f347764230896af47fe1486d4b2
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48204351"
---
# <a name="assign-and-complete-improvement-actions-in-compliance-manager"></a>Affecter et effectuer des actions d’amélioration dans le gestionnaire de conformité

**Dans cet article :** Cet article explique comment **gérer votre flux de travail de conformité** avec des actions d’amélioration. Découvrez comment **attribuer des actions d’amélioration** pour l’implémentation et le test, gérer les **mises à jour**et exporter des **rapports**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Gérer les flux de travail de conformité avec des actions d’amélioration

Les actions d’amélioration centralisent vos activités de conformité. Chaque action d’amélioration fournit des conseils détaillés sur la mise en œuvre pour vous aider à vous aligner sur les normes et réglementations sur la protection des données. Des actions peuvent être attribuées à des utilisateurs de votre organisation pour effectuer le travail d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements au sein de l’action.

Toutes vos actions d’amélioration sont répertoriées dans la page actions d’amélioration. En savoir plus sur [l’affichage de vos actions d’amélioration](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Page des détails des actions d’amélioration

Chaque action d’amélioration dispose d’une page de détails indiquant son état actuel, les normes associées et les exigences réglementaires, ainsi que les conseils en matière d’implémentation recommandés. Les [actions techniques](compliance-score-calculation.md#technical-and-non-technical-actions) incluent un lien **lancer maintenant** qui vous permet d’accéder à la solution appropriée pour l’implémentation. Vous pouvez attacher la documentation d’implémentation et de test directement à la page de détails d’une action d’amélioration.

Pour afficher la page de détails d’une action d’amélioration :

1. Accédez à votre page actions d’amélioration.
2. Sélectionnez la ligne de l’action d’amélioration prévue, qui ouvre sa page de détails.

Vous pouvez facilement afficher l’action d’amélioration suivante ou précédente dans la liste en sélectionnant la flèche vers le haut ou vers le bas dans le coin supérieur droit de l’écran. Si vous avez filtré votre liste dans la page actions d’amélioration, le fait de remonter ou de descendre vous amène à l’élément suivant dans cette liste filtrée.

## <a name="assign-improvement-actions"></a>Affecter des actions d’amélioration

Pour commencer la mise en œuvre d’une action d’amélioration, vous pouvez effectuer le travail vous-même ou l’affecter à un autre utilisateur. La personne affectée peut être :

- Le propriétaire d’une stratégie d’entreprise
- Un ingénieur informatique
- Un autre employé responsable de l’exécution de la tâche

Une fois que vous avez identifié le cessionnaire approprié, assurez-vous qu’il détient un [rôle de gestionnaire de conformité](compliance-manager-setup.md#set-user-permissions-and-assign-roles) suffisant pour effectuer le travail. Ensuite, suivez les étapes ci-dessous pour affecter l’action d’amélioration :

1. Dans la page Détails des actions d’amélioration, sélectionnez **modifier l’État** près de la section supérieure gauche de l’écran.

2. Dans le volet flyout état de modification, activez la case à cocher **affecté à** pour afficher une liste de **personnes suggérées** pour les utilisateurs. Vous pouvez sélectionner l’utilisateur dans la liste ou taper l’adresse de messagerie de la personne à laquelle vous souhaitez l’attribuer.

3. Sélectionnez **enregistrer et fermer**. L’utilisateur affecté reçoit un message électronique expliquant que l’action d’amélioration lui a été affectée, avec un lien direct vers l’action d’amélioration.

L’utilisateur affecté peut ensuite effectuer les actions recommandées.

## <a name="perform-work-and-store-documentation"></a>Effectuer une documentation de travail et de magasin

Vous pouvez télécharger des fichiers et des notes relatifs à l’implémentation et au test directement dans la section **Notes et documentation** . Cet environnement est un référentiel centralisé sécurisé qui vous permet de démontrer la satisfaction des contrôles pour répondre aux normes et réglementations en matière de conformité. Tout utilisateur disposant d’un accès en lecture seule peut lire le contenu de cette section. Seuls les utilisateurs disposant de droits de modification peuvent télécharger et télécharger des fichiers et entrer ou modifier des notes.

La section **Notes et documentation** contient des champs pour les documents téléchargés, des notes de mise en œuvre, des notes de test et des notes supplémentaires.

#### <a name="uploaded-documents"></a>Documents téléchargés

- Sélectionnez **gérer les documents** pour télécharger les fichiers appropriés.
- Lorsque le volet de menu contextuel gérer les documents s’ouvre, sélectionnez **Ajouter un document**, puis sélectionnez votre fichier dans votre système. Types de fichiers acceptés :
    - Documents (. doc,. xls,. ppt,. txt,. pdf)
    - Images (. jpg,. png)
    - Vidéo (. mkv)
    - Fichiers compressés (. zip,. rar)
- Une fois que votre fichier est résolu dans le volet, sélectionnez **Fermer**, ce qui enregistre automatiquement le fichier en pièce jointe. Vous verrez ensuite le fichier indiqué sous **documents téléchargés**.
- Pour télécharger ou supprimer le document, sélectionnez **gérer les documents** sous la liste des documents. Dans le volet flyout, sélectionnez la ligne document pour la mettre en surbrillance, puis sélectionnez **Télécharger** ou **supprimer**.

#### <a name="implementation-notes-test-notes-and-additional-notes"></a>Notes de mise en œuvre, notes de test et notes supplémentaires

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
    - L’implémentation **passée** a été vérifiée par un évaluateur
    - Échec du test à **faible risque** pour les tests, risque faible
    - **Risque moyen échoué** -test ayant échoué, risque moyen
    - **Échec à haut risque** – tests échoués, à risque élevé
    - **Hors de portée** – l’action est hors de portée pour l’évaluation et ne contribue pas à votre score
- **Date du test**: afficher la fenêtre contextuelle du calendrier pour sélectionner la date

Les actions courantes sont synchronisées entre les groupes. Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration gérées par vous-même, toutes les mises à jour apportées aux détails de l’implémentation ou à l’état d’une action sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences dans plusieurs réglementations.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Affecter une action d’amélioration à l’évaluateur pour achèvement

Une fois le travail terminé, de tester et de charger des preuves, l’étape suivante consiste à affecter l’action d’amélioration à un évaluateur pour validation. L’évaluateur valide le travail et examine la documentation, puis sélectionne l’état de test approprié.

**Si le statut du test est défini sur « passé »**: l’action est terminée et les points obtenus indiquent le nombre maximal de points atteints. Les points sont ensuite pris en compte dans le score de conformité global.

**Si le statut du test est défini sur « échec »**: l’action ne répond pas à la configuration requise et l’évaluateur peut l’attribuer à nouveau à l’utilisateur approprié pour un travail supplémentaire.

## <a name="accepting-updates-to-improvement-actions"></a>Acceptation de mises à jour pour les actions d’amélioration

Lorsqu’une mise à jour est disponible pour une action d’amélioration, une notification s’affiche en regard de son nom. Vous pouvez accepter la mise à jour ou la reporter pour une date ultérieure.

#### <a name="what-causes-an-update"></a>Qu’est-ce qui provoque une mise à jour ?

Une mise à jour est effectuée lorsqu’il y a des modifications liées au score, à l’automatisation ou à l’étendue. Les modifications peuvent impliquer de nouvelles instructions pour les actions d’amélioration en fonction des changements de réglementation, ou peuvent être liées à des modifications de produit. Seules les actions d’amélioration gérées par vos organisations reçoivent des notifications de mise à jour.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où se trouvent les notifications de mise à jour de l’évaluation

Lorsqu’une action d’amélioration est mise à jour, une étiquette **mise à jour en attente** apparaît en regard de son nom dans la page actions d’amélioration, puis sur la page Détails de ses évaluations connexes.

Accédez à la page des détails de l’action d’amélioration, puis sélectionnez le bouton **examiner la mise à jour** dans la bannière supérieure pour examiner les détails des modifications et accepter ou différer la mise à jour.

#### <a name="review-update-to-accept-or-defer"></a>Examiner la mise à jour pour accepter ou reporter

Après avoir sélectionné **examiner la mise à jour** à partir de la page Détails de l’action d’amélioration, un volet flyout apparaît sur le côté droit de l’écran. Le volet flyout fournit des détails clés sur la mise à jour, tels que les évaluations impactées et les modifications du score et de l’étendue.

Sélectionnez **accepter la mise à jour** pour accepter toutes les modifications apportées à l’action d’amélioration. **Les modifications acceptées sont permanentes**.

> [!NOTE]
> Lorsque vous acceptez une mise à jour d’une action, vous acceptez également les mises à jour de toutes les autres versions ou instances de cette action. Les mises à jour vont propager les actions techniques à l’échelle du client et vont propager les groupes pour les actions non techniques.

Si vous sélectionnez **Annuler**, la mise à jour ne sera pas appliquée à l’action d’amélioration. Toutefois, vous continuerez de voir la notification de **mise à jour en attente** jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi est-il recommandé d’accepter les mises à jour ?**

En acceptant les mises à jour, vous disposez des instructions les plus à jour sur l’utilisation des solutions et l’exécution des actions d’amélioration appropriées pour vous aider à répondre aux exigences de la certification à la main.

**Pourquoi reporter une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation qui inclut l’action d’amélioration, vous souhaiterez peut-être vous assurer que vous avez terminé de travailler dessus avant d’accepter la mise à jour. Vous pouvez reporter la mise à jour ultérieurement en sélectionnant **Annuler** dans le volet de sélection de mise à jour de révision.

## <a name="export-a-report"></a>Exporter un rapport

Sélectionnez **Exporter** dans le coin supérieur gauche de votre écran pour télécharger une feuille de calcul Excel contenant toutes vos actions d’amélioration et les catégories de filtre affichées dans la page actions d’amélioration.