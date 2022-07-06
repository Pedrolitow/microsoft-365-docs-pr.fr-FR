---
title: Utilisation des actions d’amélioration dans le Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment implémenter et tester des contrôles en travaillant avec des actions d’amélioration dans le Gestionnaire de conformité Microsoft Purview. Attribuez des rapports de travail, de stockage de documentation et d’exportation.
ms.openlocfilehash: ca6855c544451661f9a8bd3cc9f59a111eeed360
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625498"
---
# <a name="working-with-improvement-actions-in-compliance-manager"></a>Utilisation des actions d’amélioration dans le Gestionnaire de conformité

**Dans cet article :** Cet article explique comment **gérer votre flux de travail de conformité** avec des actions d’amélioration. Découvrez comment **affecter des actions d’amélioration** pour l’implémentation et les tests, **gérer les mises à jour** et exporter **des rapports**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Gérer les flux de travail de conformité avec des actions d’amélioration

Les actions d’amélioration centralisent vos activités de conformité. Chaque action d’amélioration fournit des conseils d’implémentation détaillés pour vous aider à vous aligner sur les réglementations et normes de protection des données. Des actions peuvent être affectées aux utilisateurs de votre organisation pour effectuer des travaux d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements dans l’action.

Toutes vos actions d’amélioration sont répertoriées dans la page Actions d’amélioration. En savoir plus sur [l’affichage de vos actions d’amélioration](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Page détails des actions d’amélioration

Chaque action d’amélioration comporte une page de détails indiquant son état actuel, les normes connexes et les exigences réglementaires, ainsi que des conseils d’implémentation recommandés. [Les actions techniques](compliance-score-calculation.md#technical-and-non-technical-actions) incluent un lien **Launch now** qui vous dirige vers la solution appropriée pour l’implémentation. Vous pouvez joindre la documentation d’implémentation et de test directement dans la page de détails d’une action d’amélioration.

Pour afficher la page de détails d’une action d’amélioration :

1. Accédez à la page des actions d’amélioration.
2. Sélectionnez la ligne de l’action d’amélioration prévue, qui ouvre sa page de détails.

Vous pouvez facilement afficher l’action d’amélioration suivante ou précédente dans la liste en sélectionnant la flèche vers le haut ou le bas dans le coin supérieur droit de l’écran. Si vous avez filtré votre liste sur la page Actions d’amélioration, le déplacement vers le haut ou vers le bas vous amène à l’élément suivant dans cette liste filtrée.

> [!TIP]
> En savoir plus sur les différents [types d’actions d’amélioration et sur la façon dont les points sont attribués](compliance-score-calculation.md#action-types-and-points) et pris en compte dans votre score de conformité.

## <a name="assign-improvement-actions"></a>Affecter des actions d’amélioration

Pour commencer le travail d’implémentation sur une action d’amélioration, vous pouvez effectuer le travail vous-même ou l’affecter à un autre utilisateur. La personne affectée peut être :

- Le propriétaire d’une stratégie d’entreprise
- Un ingénieur informatique
- Un autre employé responsable de l’exécution de la tâche

Une fois que vous avez identifié l’assignateur approprié, assurez-vous qu’il dispose d’un [rôle de Gestionnaire de conformité](compliance-manager-setup.md#set-user-permissions-and-assign-roles) suffisant pour effectuer le travail. Suivez ensuite les étapes ci-dessous pour affecter l’action d’amélioration :

1. Dans la page détails des actions d’amélioration, sélectionnez **Affecter une action** à gauche de l’écran.

2. Le volet **Affectation au menu volant de l’utilisateur** affiche une liste de **personnes suggérées** d’utilisateurs. Vous pouvez sélectionner l’utilisateur dans la liste ou taper l’adresse e-mail de la personne à laquelle vous souhaitez l’affecter.

3. Sélectionnez **Affecter**. L’utilisateur affecté recevra un e-mail expliquant que l’action d’amélioration lui a été affectée, avec un lien direct vers l’action d’amélioration.

> [!NOTE]
> Les clients us government community (GCC) High and Department of Defense (DoD) ne reçoivent pas d’e-mail lorsque des actions d’amélioration leur sont affectées.

L’utilisateur affecté peut ensuite effectuer les actions recommandées.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Affecter plusieurs actions d’amélioration à un seul utilisateur

Vous pouvez affecter plusieurs actions d’amélioration à un utilisateur en procédant comme suit :

1. Accédez à votre page Actions d’amélioration.
2. Sélectionnez la zone à gauche du nom de l’action d’amélioration. Une icône de vérification ronde s’affiche pour indiquer que vous avez sélectionné cette action. Vérifiez toutes les actions que vous souhaitez affecter.
3. Sélectionnez le lien **Affecter à l’utilisateur** en haut de la table actions d’amélioration.
4. Une fenêtre contextuelle apparaît. Dans le champ **Affecter à** , commencez à taper le nom de la personne à laquelle vous souhaitez affecter les actions. Vous pouvez également sélectionner dans la liste des personnes suggérées.
5. Une fois que vous avez renseigné le champ **Affecter au** nom de l’assigneur, sélectionnez **Affecter**.
6. Vous verrez ensuite votre page Actions d’amélioration avec le nouveau bénéficiaire répertorié pour les actions que vous venez d’affecter.

## <a name="change-implementation-details"></a>Modifier les détails de l’implémentation

Vous pouvez enregistrer l’état et la date d’implémentation de chaque action d’amélioration et ajouter des notes pour référence interne. Ces champs peuvent être modifiés par n’importe quel utilisateur disposant d’autorisations de modification, pas seulement par la personne affectée.

Pour modifier l’état d’une action d’amélioration, **sélectionnez Modifier les détails de l’implémentation** dans la page de détails. Vous trouverez ci-dessous les champs disponibles et les options d’état :

- **État de l’implémentation**
  - **Non implémenté** : action non encore implémentée
  - **Partiellement implémentée** : pour les actions testées automatiquement, l’action est partiellement implémentée (ni réussit ni échoue) et reçoit un score partiel
  - **Implémenté** : action implémentée
  - **Autre implémentation** : sélectionnez cette option si vous avez utilisé d’autres outils tiers ou pris d’autres actions non incluses dans les recommandations Microsoft
  - **Planifié** : une action est planifiée pour l’implémentation
  - **Hors de portée** : l’action n’est pas pertinente pour votre organisation et ne contribue pas à votre score
- **Date d’implémentation** : disponible pour sélectionner quand l’état de l’implémentation est « implémenté » ou « implémentation alternative »
- **Notes d’implémentation** : champ de texte pour les notes relatives à votre implémentation.

Il n’existe aucune limite de caractères dans les champs de notes. Nous vous recommandons de garder les notes brèves afin que vous puissiez les afficher et les modifier facilement à partir de la page de détails des actions d’amélioration.

Les actions courantes se synchronisent entre les groupes. Lorsque deux évaluations différentes dans le même groupe partagent des actions d’amélioration gérées par vous, toutes les mises à jour que vous apportez aux détails ou à l’état d’implémentation d’une action sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. Cette synchronisation vous permet d’implémenter une action d’amélioration et de répondre à plusieurs exigences sur plusieurs réglementations.

## <a name="change-test-status"></a>Modifier l’état du test

Dans la section **Test** , vous pouvez afficher l’état de test de votre action d’amélioration, la date de test et toutes les notes. Un utilisateur disposant d’autorisations de modification peut sélectionner  **Modifier les détails du test** pour modifier le contenu sous l’onglet **Test** .

#### <a name="testing-status-fields"></a>Tester les champs d’état

**État du test**
 
Vous pouvez modifier l’état du test quand l’état d’implémentation d’une action d’amélioration est « implémenté » ou « implémentation alternative ».

État des tests pour les [actions testées manuellement](#manual-testing-source) :
  - **Aucun** : aucun travail n’a démarré sur l’action
  - **Non évalué** : l’action n’a pas été testée
  - **Passé** : l’implémentation a été vérifiée par un évaluateur
  - **Échec à faible risque** : échec du test, faible risque
  - **Risque moyen non réussi** : échec du test, risque moyen
  - **Risque élevé d’échec** : échec du test, risque élevé
  - **Hors de portée** : l’action est hors de portée pour l’évaluation et ne contribue pas à votre score
  - **En cours** : test en cours
  - **Corrigé** : tod

[Les actions testées automatiquement](#automatic-testing-source) peuvent également afficher l’un des états suivants dans la colonne **État du test** sur la page **Actions d’amélioration** :
   - **À détecter** : signaux en attente indiquant l’état du test
  - **Impossible de détecter** : impossible de détecter un état de test ; sera automatiquement coché à nouveau
  - **Partiellement testé** : l’action a été partiellement testée;  ni réussit, ni échoue

> [!NOTE]
> Les notes d’état et de test des actions d’amélioration automatiquement testées ne peuvent pas être modifiées manuellement. Le Gestionnaire de conformité met à jour ces champs pour vous.

**Date de test**

Basculez dans la fenêtre contextuelle du calendrier pour sélectionner la date de test.

**Notes de test** et **notes supplémentaires**

Entrez des notes pour votre propre référence interne dans ces champs de texte libre.

**Historique des tests**

L’historique des tests fournit un rapport téléchargé de tous les changements d’état de test pour l’action d’amélioration.

#### <a name="exporting-testing-history"></a>Exportation de l’historique des tests
Vous pouvez exporter un rapport qui affiche l’historique de toutes les modifications apportées à l’état du test pour une action d’amélioration. Ces rapports sont particulièrement utiles pour surveiller la progression [des actions qui sont automatiquement testées](#automatic-testing-source), car ces actions sont régulièrement ou fréquemment mises à jour en fonction des données de votre locataire.

Dans la page de détails d’une action d’amélioration, sélectionnez l’onglet **Test** . Sous **Historique des tests**, sélectionnez le bouton **Exporter l’historique des tests** . Le rapport sera téléchargé sous forme de fichier Excel.

## <a name="update-testing-source"></a>Mettre à jour la source de test

Le Gestionnaire de conformité vous propose des options pour tester les actions d’amélioration. Dans la section **Vue d’ensemble** de chaque action d’amélioration, la zone **Source de test** comporte un menu déroulant dans lequel vous pouvez choisir la façon dont vous souhaitez tester l’action : **Manuel**, **Automatique** et **Parent**. Découvrez les détails de chaque méthode de test ci-dessous.

#### <a name="manual-testing-source"></a>Source de test manuel
Les actions d’amélioration définies pour les tests manuels sont des actions que vous testez et implémentez manuellement. Vous définissez les états d’implémentation et d’état de test nécessaires, puis chargez tous les fichiers de preuve sous l’onglet **Documents** . Pour certaines actions, il s’agit de la seule méthode disponible pour tester les actions d’amélioration.

#### <a name="automatic-testing-source"></a>Source de test automatique
Certaines actions d’amélioration peuvent être automatiquement testées par le Gestionnaire de conformité. [Obtenez des détails sur les](compliance-manager-improvement-actions.md#update-testing-source) actions d’amélioration qui peuvent et ne peuvent pas être testées automatiquement.

Pour les actions d’amélioration qui peuvent être testées automatiquement, vous verrez l’option **Automatique** pour tester la source. Le Gestionnaire de conformité détecte les signaux provenant d’autres solutions de conformité que vous avez configurées dans votre environnement Microsoft 365, ainsi que toutes les actions complémentaires que Microsoft Secure Score surveille également. Le champ **Logique de test** sous l’onglet **Test** indique le type de stratégie ou de configuration requis dans une autre solution afin que l’action passe et gagne des points vers votre score de conformité.

Quand les signaux indiquent qu’une action d’amélioration a été correctement implémentée, vous recevez automatiquement les points éligibles à cette action, qui seront pris en compte dans les scores pour les contrôles et évaluations associés. En savoir plus sur [l’impact de l’évaluation continue sur votre score de conformité](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

 Le test automatique est activé par défaut pour toutes les actions d’amélioration éligibles. Vous pouvez ajuster ces paramètres pour tester automatiquement uniquement certaines actions d’amélioration, ou désactiver le test automatique pour toutes les actions. Apprenez-en davantage sur le fonctionnement des tests automatisés et sur l’ajustement de vos paramètres lors de la [configuration des tests automatisés](compliance-manager-setup.md#manage-automated-testing-settings).

#### <a name="parent-testing-source"></a>Source de test parent

Lorsque vous sélectionnez **Parent** comme source de test pour une action d’amélioration, vous choisissez une autre action à laquelle votre action sera liée. Votre action devient en effet l'« enfant » de l’action que vous désignez comme « parent ». Lorsque vous désignez un parent pour une action d’amélioration, cette action est inhérente aux détails d’implémentation et de test de l’action parente. Chaque fois que l’état de l’action parent change, l’état de l’enfant hérite de ces modifications. L’action enfant accepte également toutes les preuves de l’onglet **Documents** qui appartiennent à l’action parente, ce qui peut remplacer toutes les données qui existaient précédemment dans les **documents** de l’action enfant.

> [!NOTE]
> Le fait d’avoir une source de test de **Parent** ne signifie pas nécessairement que l’action est automatiquement testée par le Gestionnaire de conformité. Par exemple, si la source de test de l’action parente est **manuelle**, l’action enfant prend l’état de l’action parente, qui est un test manuel et une implémentation par l’organisation.

Pour configurer une source de test parent, suivez les étapes ci-dessous :

- Dans une page de détails de l’action d’amélioration, **recherchez la section Vue d’ensemble** .
- Sous l’en-tête **Source de test** , sélectionnez **Parent** dans le menu déroulant.
- Sélectionnez **Affecter un parent**.
- Dans le volet volant **Affecter l’action d’amélioration parent** , recherchez l’action d’amélioration que vous souhaitez affecter en tant que parent dans la liste, ou entrez le nom de l’action dans la barre de recherche située en haut. Lorsque vous identifiez l’action prévue, cochez la case qui apparaît à gauche du nom de l’action lorsque vous pointez dessus, puis **sélectionnez Enregistrer**.

Vous revenez à la page de détails de votre action. Sous **Source de test** dans la section **Vue d’ensemble** , la nouvelle action que vous avez désignée comme parent est répertoriée sous **l’action Parent**.

## <a name="review-standards-and-regulations"></a>Examiner les normes et réglementations

La section **Normes et réglementations** fournit une liste de normes et de réglementations pouvant faire l’objet d’une recherche et filtrables associées à votre action d’amélioration. Elles peuvent être affichées par le **contrôle** approprié, **l’ID de contrôle**, la **famille de contrôles** et le **règlement** en cause.

## <a name="perform-work-and-store-documentation"></a>Effectuer des tâches et stocker la documentation

Vous pouvez charger des fichiers et des notes liés au travail d’implémentation et de test directement dans la section **Documents** . Cet environnement est un référentiel centralisé sécurisé qui vous permet de démontrer la satisfaction des contrôles pour répondre aux normes et réglementations de conformité. Tout utilisateur disposant d’un accès en lecture seule peut lire du contenu dans cette section. Seuls les utilisateurs disposant de droits d’édition peuvent charger et télécharger des fichiers.

#### <a name="uploaded-documents"></a>Documents téléchargés

- Sélectionnez **Gérer les documents** pour charger les fichiers pertinents.
- Lorsque le volet de menu volant Gérer les documents s’ouvre, **sélectionnez Ajouter un document**, puis sélectionnez votre fichier dans votre système. Types de fichiers acceptés :
  - Documents (.doc, .xls, .ppt, .txt, .pdf)
  - Images (.jpg, .png)
  - Vidéo (.mkv)
  - Fichiers compressés (.zip, .rar)
- Une fois votre fichier résolu dans le volet, sélectionnez **Fermer**, qui enregistre automatiquement la pièce jointe du fichier. Vous verrez ensuite le fichier répertorié sous **Documents chargés**.
- Pour télécharger ou supprimer le document, sélectionnez **Gérer les documents** sous la liste des documents. Dans le volet de menu volant, sélectionnez la ligne du document pour la mettre en surbrillance, puis **sélectionnez Télécharger** ou **Supprimer**.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Affecter une action d’amélioration à l’évaluateur pour l’achèvement

Une fois que vous avez terminé le travail, effectué des tests et chargé des preuves, l’étape suivante consiste à affecter l’action d’amélioration à un évaluateur pour validation. L’évaluateur valide le travail et examine la documentation, puis sélectionne l’état de test approprié.

**Si l’état du test est défini sur « Passé »** : l’action est terminée et les points atteints indiquent le nombre maximal de points atteints. Les points sont ensuite comptabilisés dans votre score de conformité global.

**Si l’état du test est défini sur « Échec »** : l’action ne répond pas aux exigences et l’évaluateur peut l’affecter à l’utilisateur approprié pour un travail supplémentaire.

## <a name="accepting-updates-to-improvement-actions"></a>Acceptation des mises à jour des actions d’amélioration

Lorsqu’une mise à jour est disponible pour une action d’amélioration, une notification s’affiche en regard de son nom. Vous pouvez accepter la mise à jour ou la différer ultérieurement.

#### <a name="what-causes-an-update"></a>Causes d’une mise à jour

Une mise à jour se produit en cas de modifications liées au scoring, à l’automatisation ou à l’étendue. Les modifications peuvent impliquer de nouveaux conseils pour les actions d’amélioration basées sur les modifications réglementaires, ou peuvent être dues à des modifications apportées aux produits. Seules les actions d’amélioration gérées par vos organisations reçoivent des notifications de mise à jour.

#### <a name="where-youll-see-assessment-update-notifications"></a>Où vous verrez les notifications de mise à jour d’évaluation

Lorsqu’une action d’amélioration est mise à jour, une étiquette de **mise à jour en attente** s’affiche en regard de son nom dans la page actions d’amélioration et dans la page de détails de ses évaluations associées.

Accédez à la page des détails de l’action d’amélioration, puis **sélectionnez le bouton Vérifier la mise à jour** dans la bannière supérieure pour passer en revue les détails des modifications et accepter ou différer la mise à jour.

#### <a name="review-update-to-accept-or-defer"></a>Passer en revue la mise à jour pour accepter ou différer

Après avoir sélectionné **Vérifier la mise à jour dans** la page détails de l’action d’amélioration, un volet volant s’affiche sur le côté droit de votre écran. Le volet volant fournit des détails clés sur la mise à jour, tels que les évaluations impactées et les modifications du score et de l’étendue.

Sélectionnez **Accepter la mise à jour** pour accepter toutes les modifications apportées à l’action d’amélioration. **Les modifications acceptées sont permanentes**.

> [!NOTE]
> Quand vous acceptez une mise à jour d’une action, vous acceptez également les mises à jour d’autres versions ou instances de cette action. Mises à jour propagera les actions techniques à l’échelle du locataire et propagera les actions non techniques à l’échelle du groupe.

Si vous sélectionnez **Annuler**, la mise à jour ne sera pas appliquée à l’action d’amélioration. Toutefois, vous continuerez à voir la notification de **mise à jour en attente** jusqu’à ce que vous acceptiez la mise à jour.

**Pourquoi nous vous recommandons d’accepter les mises à jour**

L’acceptation des mises à jour vous permet de disposer des conseils les plus mis à jour sur l’utilisation des solutions et de prendre les mesures d’amélioration appropriées pour vous aider à répondre aux exigences de la certification en cours.

**Pourquoi voulez-vous différer une mise à jour ?**

Si vous êtes en train d’effectuer une évaluation qui inclut l’action d’amélioration, vous pouvez vous assurer que vous avez terminé de travailler dessus avant d’accepter la mise à jour. Vous pouvez différer la mise à jour pour une date ultérieure en sélectionnant **Annuler** dans le volet de menu volant de la mise à jour de révision.

#### <a name="accept-all-updates-at-once"></a>Accepter toutes les mises à jour à la fois

Si vous avez plusieurs mises à jour et que vous souhaitez les accepter toutes en même temps, sélectionnez le lien **Accepter toutes les mises à jour** en haut de la table des actions d’amélioration. Un volet volant s’affiche, qui répertorie le nombre d’actions à mettre à jour. Sélectionnez le bouton **Accepter les mises à jour** pour appliquer toutes les mises à jour.

Notez que lorsque vous revenez à votre page d’actions d’amélioration, vous pouvez voir un message en haut de la page vous demandant d’actualiser la page pour que les mises à jour soient terminées.

## <a name="set-up-alerts-for-improvement-action-changes"></a>Configurer des alertes pour les modifications apportées aux actions d’amélioration

Vous pouvez configurer des alertes pour vous avertir immédiatement lorsque certaines modifications apportées aux actions d’amélioration se produisent, telles qu’une modification de l’implémentation ou de l’état de test, ou une augmentation ou une diminution du score. L’obtention de notifications rapides de ces modifications peut vous aider à rester informé des risques de conformité possibles. Visitez [les alertes et les stratégies d’alerte du Gestionnaire de conformité](compliance-manager-alert-policies.md) pour savoir comment configurer des alertes.

## <a name="export-a-report"></a>Exporter un rapport

Sélectionnez **Exporter** dans le coin supérieur gauche de votre écran pour télécharger une feuille de calcul Excel contenant toutes vos actions d’amélioration et les catégories de filtre affichées dans la page Actions d’amélioration.
