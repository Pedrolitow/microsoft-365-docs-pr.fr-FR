---
title: Affecter et effectuer des actions d’amélioration dans le Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment effectuer l’implémentation et les tests sur les contrôles dans le Gestionnaire de conformité Microsoft. Affecter des rapports de travail, stocker de la documentation et exporter des rapports.
ms.openlocfilehash: f2674e24ed38362c5c7563a574e0dba9c81f2584
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181396"
---
# <a name="assign-and-complete-improvement-actions-in-compliance-manager"></a>Affecter et effectuer des actions d’amélioration dans le Gestionnaire de conformité

**Dans cet article :** Cet article explique comment gérer votre flux **de travail** de conformité avec des actions d’amélioration. Découvrez comment affecter des **actions d’amélioration pour** l’implémentation et le test, gérer les **mises à jour** et exporter des **rapports.**

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Gérer les flux de travail de conformité avec des actions d’amélioration

Les actions d’amélioration centralisent vos activités de conformité. Chaque action d’amélioration fournit des instructions de mise en œuvre détaillées pour vous aider à vous aligner sur les réglementations et normes en matière de protection des données. Des actions peuvent être affectées aux utilisateurs de votre organisation pour effectuer des tâches d’implémentation et de test. Vous pouvez également stocker de la documentation, des notes et enregistrer des mises à jour d’état au sein de l’action.

Toutes vos actions d’amélioration sont répertoriées sur la page Actions d’amélioration. En savoir plus sur [l’affichage de vos actions d’amélioration.](compliance-manager-setup.md#improvement-actions-page)

## <a name="improvement-actions-details-page"></a>Page détails des actions d’amélioration

Chaque action d’amélioration possède une page de détails indiquant son état actuel, les normes et exigences réglementaires associées, ainsi que les recommandations d’implémentation recommandées. [Les actions techniques](compliance-score-calculation.md#technical-and-non-technical-actions) incluent un **lien Lancer maintenant** qui vous permet d’obtenir la solution appropriée pour l’implémentation. Vous pouvez joindre la documentation d’implémentation et de test directement dans la page de détails d’une action d’amélioration.

Pour afficher la page de détails d’une action d’amélioration :

1. Go to your improvement actions page.
2. Sélectionnez la ligne de l’action d’amélioration prévue, qui ouvre sa page de détails.

Vous pouvez facilement afficher l’action d’amélioration suivante ou précédente dans la liste en sélectionnant la flèche vers le haut ou vers le bas dans le coin supérieur droit de l’écran. Si vous avez filtré votre liste sur la page Actions d’amélioration, le déplacement vers le haut ou vers le bas vous permet d’passer à l’élément suivant dans cette liste filtrée.

## <a name="assign-improvement-actions"></a>Affecter des actions d’amélioration

Pour commencer le travail d’implémentation d’une action d’amélioration, vous pouvez le faire vous-même ou l’affecter à un autre utilisateur. La personne affectée peut être :

- Le propriétaire d’une stratégie d’entreprise
- Un ingénieur informatique
- Un autre employé chargé d’effectuer la tâche

Une fois que vous avez identifié la personne appropriée, assurez-vous qu’elle a un rôle de Gestionnaire de conformité suffisant [pour](compliance-manager-setup.md#set-user-permissions-and-assign-roles) effectuer le travail. Suivez ensuite les étapes ci-dessous pour affecter l’action d’amélioration :

1. Dans la page détails des actions d’amélioration, sélectionnez **Modifier l’état** dans la section supérieure gauche de l’écran.

2. Dans le volet volant Modifier l’état, sélectionnez  la zone Affecté à pour afficher une liste de personnes suggérées d’utilisateurs.  Vous pouvez sélectionner l’utilisateur dans la liste ou taper l’adresse de messagerie de la personne à qui vous souhaitez l’affecter.

3. Sélectionnez **Enregistrer et fermer.** L’utilisateur affecté reçoit un e-mail expliquant que l’action d’amélioration lui a été affectée, avec un lien direct vers l’action d’amélioration. 
> [!NOTE]
> Les clients Community (Cloud de la communauté du secteur public) Haut et Département de la Défense (DoD) du gouvernement américain ne reçoivent pas de courrier électronique lorsque des actions d’amélioration leur sont affectées.

L’utilisateur affecté peut ensuite effectuer les actions recommandées.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Affecter plusieurs actions d’amélioration à un seul utilisateur

Vous pouvez affecter plusieurs actions d’amélioration à un utilisateur en suivant les étapes suivantes :

1. Go to your Improvement actions page.
2. Sélectionnez la zone à gauche du nom de l’action d’amélioration. Une icône de vérification arrondie s’affiche indiquant que vous avez sélectionné cette action. Vérifiez toutes les actions que vous souhaitez affecter.
3. Sélectionnez le **lien Affecter à l’utilisateur** en haut du tableau des actions d’amélioration.
4. Une fenêtre contextuelle apparaît. Dans le **champ Affecter à,** commencez à taper le nom de la personne à qui vous souhaitez affecter les actions. Vous pouvez également choisir dans la liste des personnes suggérées.
5. Une fois que vous avez rempli le **champ Affecter à** avec le nom de la personne assignée, sélectionnez **Affecter**.
6. Vous verrez ensuite votre page d’actions d’amélioration avec la nouvelle personne affectée répertoriée pour les actions que vous avez affectées.

## <a name="perform-work-and-store-documentation"></a>Effectuer des travaux et stocker de la documentation

Vous pouvez charger des fichiers et des notes relatifs à l’implémentation et au test de travail directement dans la section **Notes et documentation.** Cet environnement est un référentiel sécurisé et centralisé pour vous aider à démontrer la satisfaction des contrôles pour répondre aux normes et réglementations de conformité. Tout utilisateur ayant un accès en lecture seule peut lire le contenu de cette section. Seuls les utilisateurs ayant des droits d’édition peuvent télécharger des fichiers et entrer ou modifier des notes.

La section **Notes et documentation** contient des champs pour les documents téléchargés, les notes d’implémentation, les notes de test et les notes supplémentaires.

#### <a name="uploaded-documents"></a>Documents téléchargés

- Sélectionnez **Gérer les documents** pour télécharger les fichiers appropriés.
- Lorsque le volet volant Gérer les documents s’ouvre, sélectionnez Ajouter **un document,** puis sélectionnez votre fichier à partir de votre système. Types de fichiers acceptés :
    - Documents (.doc, .xls, .ppt, .txt, .pdf)
    - Images (.jpg, .png)
    - Vidéo (.mkv)
    - Fichiers compressés (.zip, .rar)
- Une fois votre fichier résolu dans le volet, sélectionnez **Fermer,** qui enregistre automatiquement la pièce jointe du fichier. Vous verrez ensuite le fichier répertorié sous **les documents téléchargés.**
- Pour télécharger ou supprimer le document, sélectionnez **Gérer les documents** sous la liste des documents. Dans le volet volant, sélectionnez la ligne du document pour la mettre en surbrillon, puis sélectionnez **Télécharger** ou **Supprimer.**

#### <a name="implementation-notes-test-notes-and-additional-notes"></a>Notes d’implémentation, notes de test et notes supplémentaires

- Pour ajouter des notes dans l’un de ces trois champs, sélectionnez Modifier les **notes** d’implémentation sous l’un de ces champs.
- Lorsque le volet volant s’ouvre, entrez des notes dans le champ de texte, puis **sélectionnez Enregistrer et fermer.**
- Pour modifier des notes, **sélectionnez Modifier les notes** d’implémentation, a apporter vos modifications, puis **sélectionnez Enregistrer et fermer.**

Il n’existe aucune limite de caractères dans les champs de notes. Nous vous recommandons de garder les notes brèves afin de pouvoir facilement les afficher et les modifier à partir de la page de détails des actions d’amélioration.

## <a name="change-improvement-action-status"></a>État de l’action d’amélioration des changements

Vous pouvez enregistrer l’état et la date d’implémentation, ainsi que l’état et la date du test pour chaque action d’amélioration. Les **champs d’implémentation** **et d’état** de test peuvent être modifiés par n’importe quel utilisateur ayant des autorisations de modification, pas seulement par la personne affectée.

Pour modifier l’état d’une action d’amélioration, sélectionnez **Modifier l’état** dans la section supérieure gauche de la page de détails. Vous trouverez ci-dessous les champs disponibles et les options d’état :

- **État de l’implémentation**
    - **Non implémenté** - action pas encore implémentée
    - **Implémenté** - action implémentée
    - **Implémentation alternative** : sélectionnez cette option si vous avez utilisé d’autres outils tiers ou pris d’autres actions non incluses dans les recommandations de Microsoft
    - **Planifié** : l’action est planifiée pour l’implémentation
    - **Hors de portée** : l’action n’est pas pertinente pour votre organisation et ne contribue pas à votre score
- **Date d’implémentation**: disponible pour sélectionner le moment où l’état d’implémentation est « implémenté » ou « implémentation alternative »
- **État du** test : disponible pour sélectionner le moment où l’état d’implémentation est « implémenté » ou « implémentation alternative » :
    - **Non évalué :** l’action n’a pas été testée
    - **Réussi** : l’implémentation a été vérifiée par un évaluateur
    - **Échec du risque faible :** échec du test, faible risque
    - **Échec du risque moyen :** échec du test, risque moyen
    - **Échec d’un risque élevé** : échec du test, risque élevé
    - **Hors de portée :** l’action n’est pas étendue pour l’évaluation et ne contribue pas à votre score
- **Date de test**: basculez dans la fenêtre pop-up du calendrier pour sélectionner la date

Les actions courantes sont synchronisées entre les groupes. Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration qui sont gérées par vous, les mises à jour apportées aux détails ou à l’état d’implémentation d’une action se synchronisent automatiquement avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences dans plusieurs réglementations.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Affecter une action d’amélioration à l’évaluateur pour l’achèvement

Une fois que vous avez terminé le travail, effectué des tests et chargé des preuves, l’étape suivante consiste à affecter l’action d’amélioration à un évaluateur pour validation. L’évaluateur valide le travail, examine la documentation et sélectionne l’état de test approprié.

**Si l’état du test est « Réussi**» : l’action est terminée et les points obtenus indiquent le nombre maximal de points obtenus. Les points sont ensuite comptabilisés dans votre score de conformité global.

**Si l’état** du test est « Échec » : l’action ne répond pas aux exigences et l’évaluateur peut l’affecter à l’utilisateur approprié pour un travail supplémentaire.

## <a name="accepting-updates-to-improvement-actions"></a>Acceptation des mises à jour pour les actions d’amélioration

Lorsqu’une mise à jour est disponible pour une action d’amélioration, vous verrez une notification en regard de son nom. Vous pouvez accepter la mise à jour ou la différer pour une période ultérieure.

#### <a name="what-causes-an-update"></a>Causes d’une mise à jour

Une mise à jour se produit lorsqu’il existe des modifications liées à l’score, à l’automatisation ou à l’étendue. Les modifications peuvent impliquer de nouvelles instructions pour les actions d’amélioration basées sur les modifications réglementaires, ou peuvent être dues à des modifications apportées aux produits. Seules les actions d’amélioration gérées par vos organisations reçoivent des notifications de mise à jour.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où vous verrez les notifications de mise à jour de l’évaluation

Lorsqu’une action d’amélioration est mise  à jour, vous verrez une étiquette de mise à jour en attente en regard de son nom sur la page actions d’amélioration et sur la page de détails de ses évaluations connexes.

Go to the improvement action’s details page, and select the **Review update** button in the top banner to review details about the changes and accept or defer the update.

#### <a name="review-update-to-accept-or-defer"></a>Passer en revue la mise à jour pour accepter ou différer

Après avoir sélectionné la mise à **jour de** révision dans la page détails de l’action d’amélioration, un volet volant s’affiche sur le côté droit de votre écran. Le volet volant fournit des détails clés sur la mise à jour, tels que les évaluations impactées et les modifications apportées au score et à l’étendue.

Sélectionnez **Accepter la mise à** jour pour accepter toutes les modifications apportées à l’action d’amélioration. **Les modifications acceptées sont permanentes.**

> [!NOTE]
> Lorsque vous acceptez une mise à jour d’une action, vous acceptez également les mises à jour d’autres versions ou instances de cette action. Les mises à jour propagent les actions techniques à l’échelle du client et se propagent à l’échelle du groupe pour les actions non techniques.

Si vous **sélectionnez Annuler,** la mise à jour ne sera pas appliquée à l’action d’amélioration. Toutefois, vous continuerez à voir la notification de mise à jour **en** attente jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi nous vous recommandons d’accepter les mises à jour ?**

L’acceptation des mises à jour vous permet de vous assurer que vous avez les conseils les plus mis à jour sur l’utilisation des solutions et la prise d’actions d’amélioration appropriées pour vous aider à répondre aux exigences de la certification.

**Pourquoi différer une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation qui inclut l’action d’amélioration, vous voudrez peut-être vous assurer que vous avez terminé de travailler dessus avant d’accepter la mise à jour. Vous pouvez différer la mise à jour ultérieurement en sélectionnant **Annuler** dans le volet volant de révision de la mise à jour.

#### <a name="accept-all-updates-at-once"></a>Accepter toutes les mises à jour en même temps

Si vous avez plusieurs mises à jour et que  vous souhaitez les accepter toutes en même temps, sélectionnez le lien Accepter toutes les mises à jour en haut du tableau des actions d’amélioration. Un volet volant s’affiche, qui répertorie le nombre d’actions à mettre à jour. Sélectionnez le **bouton Accepter les mises à** jour pour appliquer toutes les mises à jour.

Notez que lorsque vous revenirz à votre page d’actions d’amélioration, vous pouvez voir un message en haut de la page vous demandant d’actualiser la page pour que les mises à jour soient terminées.

## <a name="export-a-report"></a>Exporter un rapport

Sélectionnez **Exporter** dans le coin supérieur gauche de votre écran pour télécharger une feuille de calcul Excel contenant toutes vos actions d’amélioration et les catégories de filtre affichées sur la page Actions d’amélioration.