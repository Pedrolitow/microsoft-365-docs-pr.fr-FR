---
title: Utilisation du score de conformité Microsoft
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
description: Découvrez comment utiliser les outils de flux de travail dans le score de conformité Microsoft pour vous aider à gérer la conformité de votre organisation.
ms.openlocfilehash: 9dc3eb41b1ad686e1c9e1f0a4cf2df66ccb3ffbe
ms.sourcegitcommit: 544b10cc3abe04a47438085d51c4250c9238f76f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "38685708"
---
# <a name="working-with-microsoft-compliance-score-preview"></a>Utilisation du score de conformité Microsoft (aperçu)

## <a name="managing-your-workflow-with-improvement-actions"></a>Gestion de votre flux de travail avec des actions d’amélioration

L’utilisation d’actions d’amélioration dans le score de conformité centralise vos flux de travail de conformité. Les actions d’amélioration suggèrent des actions recommandées pour s’aligner sur les normes et réglementations en matière de protection des données, et fournissent des conseils détaillés. Vous pouvez les affecter aux utilisateurs pour effectuer les opérations d’implémentation et de test nécessaires. Vous pouvez également stocker la documentation et les notes, et enregistrer les mises à jour de l’État directement dans l’action d’amélioration proprement dite.

## <a name="view-your-improvement-actions"></a>Afficher vos actions d’amélioration

Le tableau de bord de score de conformité affiche vos **actions d’amélioration clés**, c’est-à-dire celles dont les points sont les plus disponibles et qui traitent des problèmes les plus importants.

Pour afficher toutes vos actions d’amélioration, sélectionnez l’onglet **actions d’amélioration** de votre tableau de bord ou sélectionnez **afficher toutes les actions d’amélioration** sous la liste des actions d’amélioration de clé dans votre tableau de bord. Cela vous amène à la page **actions d’amélioration** , qui vous permet d’afficher toutes les actions d’amélioration de votre organisation.

Si vous avez une longue liste d’actions, il peut être utile de filtrer votre vue. Pour ce faire, sélectionnez **filtre** dans le coin supérieur droit de la liste actions. Lorsque le volet flyout **filtres** apparaît, sélectionnez les critères souhaités en fonction des réglementations, des normes, de la solution et du groupe. Vous pouvez également personnaliser votre affichage en sélectionnant **groupe** dans le coin supérieur droit et, dans le menu déroulant, sélectionnez pour afficher par groupe, solution, catégorie, type d’action ou état.

L’affichage par défaut de cette page n’affiche pas les actions d’amélioration dont l’état de test est **réussite**. Pour afficher les actions qui ont été testées, activez la case à cocher **passé** dans le volet flyout **filtres** . Uniquement les actions dont l’état de test est **passé** vers votre score.

La page actions d’amélioration affiche les points de données suivants pour chaque action d’amélioration :

- **Impact sur le score**: les points par lesquels votre score global augmentera lors de l’exécution de l’action
- **Réglementation**: la réglementation ou la norme relative à l’action
- **Groupe**: groupe auquel vous avez affecté l’action.
- **Solutions**: la solution à partir de laquelle vous pouvez effectuer l’action
- **Évaluations**: l’évaluation (qui organise les contrôles afin de respecter un certain objectif de conformité) dans lequel l’action réside.
- **Catégories**: catégorie de protection des données associée (par exemple, protection des informations, gestion des appareils, etc.)
- **État du test**:
    - **None** -aucune mise à jour d’État enregistrée
    - **Non évalué** -le test n’a pas démarré
    - **Non inclus dans l’étendue** -est exclu du calcul du score de conformité et n’augmente pas votre score
    - Les tests **partiellement testés** ne sont pas encore terminés
    - Échec de test à **haut risque** : les tests de l’implémentation ont échoué et le risque de non-conformité à la norme applicable est élevé
    - **Réussite** de l’implémentation réussie
- **Pointud**: affiche les points obtenus en dehors du maximum pouvant être gagnés

### <a name="improvement-actions-details"></a>Détails des actions d’amélioration

Chaque action d’amélioration dispose d’une page de détails. Cette page contient des instructions d’implémentation détaillées, qui expliquent comment effectuer les actions recommandées pour répondre aux exigences de conformité et aux normes associées indiquées dans la rubrique **at a Glance** Header.

La page de détails est l’endroit où vous pouvez lancer l’action recommandée ou attribuer le travail à un autre utilisateur, mettre à jour l’État et joindre des notes et de la documentation.

Pour afficher la page de détails d’une action d’amélioration :

1. Accédez à votre page actions d’amélioration.
2. Cliquez ou appuyez n’importe où dans la ligne de l’action d’amélioration prévue, qui ouvre sa page de détails.

Vous pouvez facilement afficher l’action d’amélioration suivante ou précédente dans la liste en sélectionnant la flèche vers le haut ou vers le bas dans le coin supérieur droit de l’écran. Si vous avez filtré votre liste dans la page actions d’amélioration, le haut ou le bas vous permet d’accéder à l’élément suivant dans la liste filtrée.

## <a name="assign-improvement-actions"></a>Affecter des actions d’amélioration

Pour commencer la mise en œuvre d’une action d’amélioration, vous pouvez effectuer le travail vous-même ou l’affecter à un autre utilisateur. La personne affectée peut être :

- Le propriétaire d’une stratégie d’entreprise
- Un ingénieur informatique
- Un autre employé responsable de l’exécution de la tâche 

Une fois que la personne appropriée est identifiée, assurez-vous qu’elle détient un [rôle](compliance-score-setup.md#set-user-permissions-and-assign-roles) suffisant dans le score de conformité (administrateur de conformité, administrateur des données de conformité, administrateur de la sécurité ou administrateur général) pour effectuer le travail, puis procédez comme suit : 

1. Dans la page Détails des actions d’amélioration, sélectionnez **modifier l’État** près de la section supérieure gauche de l’écran. 

2. Dans le volet flyout état de modification, cliquez ou appuyez sur la zone **affecté à** , qui remplit une liste de **personnes suggérées** pour les utilisateurs. Vous pouvez sélectionner l’utilisateur dans la liste ou taper l’adresse de messagerie de la personne à laquelle vous souhaitez affecter l’action.

3. Sélectionnez **enregistrer et fermer** pour terminer l’affectation. L’utilisateur affecté reçoit un message électronique indiquant que l’action d’amélioration lui a été affectée, et il peut ensuite ouvrir l’action d’amélioration à partir de son tableau de bord.

L’utilisateur affecté peut alors effectuer les actions recommandées décrites dans les instructions d’implémentation.

## <a name="perform-work-and-store-documentation"></a>Effectuer une documentation de travail et de magasin

Lorsque vous effectuez l’implémentation, vous pouvez télécharger des fichiers et des notes directement à l’aide de la section **Notes et documentation** . Cela fournit un référentiel centralisé sécurisé pour vous aider à démontrer la satisfaction des contrôles pour respecter les normes et réglementations en matière de conformité. Tout utilisateur disposant d’un accès en lecture seule peut lire le contenu de cette section. La possibilité de télécharger, de télécharger ou de supprimer des champs, ou d’entrer ou de modifier des notes, est limitée aux rôles avec des droits d’édition.

Les champs de la section **Notes et documentation sont les** suivants :

**Documents téléchargés**

- Sélectionnez **gérer les documents** pour télécharger les fichiers appropriés.
- Lorsque le volet de menu contextuel gérer les documents s’ouvre, sélectionnez **Ajouter un document**, puis sélectionnez votre fichier dans votre système. Types de fichiers acceptés : 
  - Documents (. doc,. xls,. ppt,. txt,. pdf)
  - Images (. jpg,. png)
  - Vidéo (. mkv)
  - Fichiers compressés (. zip,. rar)
- Une fois que votre fichier est résolu dans le volet, sélectionnez **Fermer,** qui enregistre automatiquement le fichier en pièce jointe. Le fichier indiqué sous **documents téléchargés** s’affiche. 
- Pour télécharger ou supprimer le document, sélectionnez **gérer les documents** sous la liste des documents. Dans le volet flyout, cliquez ou appuyez sur la ligne document pour la mettre en surbrillance, puis sélectionnez **Télécharger** ou **Supprimer.**

**Implémentation, test et notes supplémentaires**

- Pour ajouter des notes dans l’un de ces trois champs, sélectionnez **modifier les notes d’implémentation** sous l’un des champs thse.
- Lorsque le volet flyout s’ouvre, entrez des notes dans le champ texte, puis sélectionnez **enregistrer et fermer**.
- Pour modifier des notes, sélectionnez **modifier les notes d’implémentation**, apporter vos modifications, puis cliquez sur **enregistrer et fermer**.

Il n’y a pas de limite de caractères dans les champs Notes. Nous vous recommandons de conserver des notes résumées afin de pouvoir les afficher et les modifier facilement à partir de la page Détails des actions d’amélioration.

## <a name="change-improvement-action-status"></a>Modifier l’état de l’action d’amélioration

Vous pouvez enregistrer l’État et la date d’implémentation, ainsi que l’État et la date du test pour chaque action d’amélioration. Vous trouverez ci-dessous les champs et les options d’état disponibles :

- **État**de l’implémentation : sélectionnez l’une des options d’État suivantes :
    - **Non implémenté** -action pas encore implémentée
    - **Implemented** -action implémentée
    - **Autre implémentation** : sélectionnez cette option si vous avez utilisé d’autres outils tiers ou si vous avez effectué d’autres actions qui ne sont pas incluses dans les recommandations de Microsoft.
    - L’action **planifiée** est planifiée pour l’implémentation
    - **N’est pas dans l’étendue** -une option pour les actions non pertinentes pour votre organisation ; la sélection de cet État exclut l’action de l’évaluation ; Si vous désactivez cette option, vous incluez l’action dans le score.
- **Date d’implémentation**: champ disponible lorsque l’état de mise en œuvre est défini sur **implémenté** ou une **autre implémentation**; faire défiler la fenêtre de calendrier pour sélectionner la date
- **État du test**: sélectionnez l’une des options suivantes :
    - **Non évalué** -le test n’a pas démarré
    - **Réussite**de l’implémentation réussie
    - Échec du test à **faible risque** pour les tests, risque faible
    - **Risque moyen échoué** -test ayant échoué, risque moyen
    - Échec de test à **haut risque ayant** échoué, à risque élevé
- **Date du test**: afficher la fenêtre contextuelle du calendrier pour sélectionner la date

> [!NOTE]
> Les champs d’état de mise en œuvre et de test peuvent être modifiés par n’importe quel utilisateur disposant d’autorisations de modification, et pas seulement de l’utilisateur **affecté** .

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Affecter une action d’amélioration à l’évaluateur pour achèvement

Une fois le travail et le chargement des preuves terminés, l’étape suivante consiste à définir l’État et la date de l’implémentation et à affecter l’action d’amélioration à un évaluateur pour validation.

Les types d’évaluateurs sont les suivants :

- Des évaluateurs internes qui effectuent la validation des contrôles au sein de votre organisation ;
- Des évaluateurs externes qui examinent, vérifient et certifient la conformité, tels que les organisations indépendantes tierces qui auditent les services Cloud de Microsoft

L’évaluateur valide le travail et examine la documentation, puis sélectionne l’état de test approprié.

**Si le statut du test est « passé »**: l’action est terminée et les **points obtenus** indiquent le nombre total de points possibles réalisés et pris en compte dans votre score de conformité global.

**Si l’état du test est de n’importe quel degré de « échec »**: l’action ne répond pas aux exigences et l’évaluateur peut l’affecter de nouveau à l’utilisateur approprié pour un travail supplémentaire.

## <a name="solutions-page"></a>Page solutions

La **page solutions** constitue un autre point de départ pour l’utilisation des actions d’amélioration afin d’augmenter votre score. 

Pour accéder à votre page solutions, sélectionnez l’onglet **solutions** de votre tableau de bord ou sélectionnez **afficher toutes les solutions** sous **solutions qui affectent votre score** dans la section supérieure droite de votre tableau de bord.

La page solutions indique le partage des points gagnés et potentiels, tel qu’il est organisé par la solution. L’affichage de vos points restants et des actions d’amélioration à partir de cette vue vous permet de comprendre les solutions qui nécessitent une attention plus immédiate.

### <a name="filtering-your-solutions-view"></a>Filtrage de l’affichage des solutions

Pour filtrer les solutions, procédez comme suit : 

1. Sélectionnez **filtre** dans le coin supérieur gauche de votre liste évaluations.
2. Dans le volet des **filtres** de menu volant, activez les cases à cocher en regard des critères de votre choix (normes et réglementations, solution, type d’action, groupe du gestionnaire de conformité, catégorie).
3. Sélectionnez le bouton **appliquer** . Le volet de filtre se ferme et vous verrez votre affichage filtré.

Vous pouvez également modifier votre vue pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **groupe** au-dessus de votre liste d’évaluations.

### <a name="taking-actions-from-the-solutions-page"></a>Exécution d’actions à partir de la page solutions

La page solutions affiche les solutions de votre organisation qui sont connectées à des actions d’amélioration. Le tableau répertorie chaque contribution de chaque solution à votre score global, les points d’amélioration de score obtenus et possibles au sein de cette solution, ainsi que le nombre d’actions d’amélioration restantes regroupées dans cette solution qui peuvent augmenter votre score. 

Il existe deux façons d’effectuer une action à partir de cet écran :

1. Sur la ligne de la solution souhaitée, sous la colonne **actions restantes** , cliquez ou appuyez sur le numéro du lien hypertexte. Cette action vous permet d’accéder à une vue filtrée de l’écran actions d’amélioration affichant les actions d’amélioration non testées pour cette solution.

2. Sur la ligne de la solution voulue, sous la colonne **ouvrir une solution** , sélectionnez **ouvrir**. Vous accédez à la solution ou à l’emplacement dans les centres de sécurité et de conformité de Microsoft 365 et Office 365, où vous pouvez prendre l’action recommandée.

## <a name="assessments-page"></a>Page évaluations

La page évaluations répertorie les évaluations que vous choisissez de suivre pour votre organisation. Votre dénominateur de score de conformité est déterminé par toutes vos évaluations suivies. Plus vous ajoutez d’évaluations, plus les actions d’amélioration que vous voyez sur votre page actions d’amélioration et plus votre dénominateur de score est élevé.

Pour accéder à votre page évaluations, sélectionnez l’onglet **évaluations** de votre tableau de bord.

Sur cette page, vous pouvez rapidement afficher des informations importantes sur chaque évaluation :

- **État**: l’État vers la fin de toutes les actions d’amélioration dans l’évaluation est défini comme suit :
    - **Non conforme**: les actions d’amélioration dans l’évaluation n’ont pas été mises en œuvre et testées avec succès ; le travail n’a pas encore commencé
    - **En cours**: le travail est en cours lors de l’implémentation ou du test des actions d’amélioration ; Cela peut signifier, par exemple, qu’une action d’amélioration apportée à l’évaluation a été affectée au travail, qu’elle est en cours d’implémentation et de test.
- **Avancement**de l’évaluation : pourcentage du travail effectué jusqu’à la fin de l’évaluation finale, mesuré par le nombre de contrôles correctement testés.
- **Actions gérées par le client**: nombre d’actions terminées pour répondre à l’implémentation de vos contrôles gérés par le client
- **Actions gérées par Microsoft**: nombre d’actions terminées pour répondre à l’implémentation des contrôles gérés par Microsoft
- **Groupe d’évaluation**: nom du groupe que vous avez créé, dans lequel l’évaluation réside.
- **Services associés**: service Microsoft 365 associé
- **Réglementations connexes**: norme, politique ou loi réglementaire que l’évaluation cherche à respecter

### <a name="default-assessments"></a>Évaluations par défaut

Par défaut, l’évaluation de la base de données de protection des données Microsoft 365 s’affiche sur la page évaluations. Si vous souhaitez ajouter d’autres évaluations afin de traiter d’autres réglementations et normes, vous pouvez gérer les évaluations dans le gestionnaire de conformité. Le score de conformité fournit plus de 10 évaluations prédéfinies, notamment celles pour RGPD, CCPA, ISO 27001, ISO 27018, NIST 800-53, NIST 800-171, NIST CSF, CSA CCM, FFIEC, HIPAA/Hi et FedRAMP.

### <a name="managing-assessments"></a>Gestion des évaluations

Lors de la préversion publique, les fonctionnalités d’affichage, de création, d’exportation et d’archivage sont conservées dans l’outil Gestionnaire de conformité. 

Pour gérer vos évaluations, sélectionnez **gérer les évaluations dans le gestionnaire de conformité** en haut de la liste évaluations.

Le premier lien en haut de la liste des évaluations, **actions Microsoft dans le gestionnaire de conformité**, vous permet d’accéder à la page du gestionnaire de conformité affichant les contrôles Microsoft qui contribuent à votre score de conformité.

### <a name="filtering-your-assessments-view"></a>Filtrage de l’affichage des évaluations

Pour filtrer les évaluations, procédez comme suit :

1. Sélectionnez **filtre** dans le coin supérieur gauche de votre liste évaluations.
2. Dans le volet **filtres** de menu volant, activez la case à cocher en regard des critères de votre choix (standards et réglementations, groupe gestionnaire de conformité).
3. Sélectionnez le bouton **appliquer** . Le volet de filtre se ferme et vous verrez votre affichage filtré.

Vous pouvez également modifier votre vue pour afficher les évaluations par groupe, produit ou réglementation en sélectionnant le type de regroupement dans le menu déroulant **groupe** au-dessus de votre liste d’évaluations.

### <a name="managing-improvement-actions-within-an-assessment"></a>Gestion des actions d’amélioration au sein d’une évaluation

Dans la liste évaluation, sous la colonne **actions gérées par le client** , sélectionnez le texte lié sur la ligne de l’évaluation prévue. Cette opération vous permet d’accéder à une vue filtrée de la page actions d’amélioration présentant les actions de cette évaluation.

## <a name="reporting"></a>Reporting

Vous pouvez exporter un rapport de toutes vos actions d’amélioration dans le score de conformité. Dans la page **actions d’amélioration** , sélectionnez **Exporter** dans le coin supérieur gauche de votre écran, au-dessus de votre liste d’actions. Cette opération génère une feuille de calcul Excel avec toutes vos actions d’amélioration et les catégories de filtre indiquées dans la page **actions d’amélioration** , que vous pouvez afficher et enregistrer sur votre ordinateur local.

Vous pouvez également exporter un rapport à partir du gestionnaire de conformité. Dans le gestionnaire de conformité, accédez à l’onglet **paramètres** et sélectionnez **Exporter** dans la partie supérieure droite de l’écran. Cela génère une feuille de calcul Excel que vous pouvez afficher et enregistrer.
