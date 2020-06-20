---
title: Utiliser le gestionnaire de conformité Microsoft (aperçu)
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
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment utiliser le gestionnaire de conformité pour suivre, affecter et vérifier les activités de conformité aux réglementations relatives aux produits Microsoft.
ms.openlocfilehash: fe7b04fe7687bc91e6f96fb2c3994a6536cec314
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817081"
---
# <a name="working-with-microsoft-compliance-manager-preview"></a>Utilisation du gestionnaire de conformité Microsoft (aperçu)

> [!IMPORTANT]
> Le gestionnaire de conformité Microsoft est un tableau de bord et un outil de gestion qui fournit un résumé de votre stature de protection et de conformité des données afin d’améliorer la protection et la conformité des données. Les actions client fournies dans le gestionnaire de conformité sont des recommandations. Il revient à votre organisation d’évaluer l’efficacité de ces recommandations dans son environnement réglementaire respectif avant la mise en œuvre. Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme des garanties de conformité.

## <a name="access-compliance-manager"></a>Gestionnaire de conformité des accès

Le gestionnaire de conformité est accessible à partir du portail d’approbation de service Microsoft. Tout utilisateur disposant d’un compte Microsoft ou d’un compte d’organisation Azure Active Directory peut accéder au gestionnaire de conformité.

1. Accédez à [https://servicetrust.microsoft.com/ComplianceManager/V3](https://servicetrust.microsoft.com/ComplianceManager/V3).

2. Connectez-vous à l’aide de votre compte de service Microsoft, qui est votre compte d’utilisateur Office 365, Microsoft 365 ou Azure Active Directory (Azure AD).

> [!NOTE]
> Dans le portail d’approbation de service, sélectionnez **Gestionnaire de conformité**, version d’évaluation avec les fonctionnalités les plus récentes. Ne sélectionnez pas le **Gestionnaire de conformité (classique)**, qui contient les fonctionnalités de version préliminaire non couvertes par cette documentation.

## <a name="administration"></a>Administration

Il existe des fonctions d’administration spécifiques qui sont uniquement disponibles pour l’administrateur général et ne sont visibles que lorsque vous êtes connecté avec un compte d’administrateur général. L’administrateur général peut attribuer des autorisations utilisateur et activer les mises à jour automatiques du score de sécurité.
  
### <a name="assigning-compliance-manager-roles-to-users"></a>Affectation des rôles du Gestionnaire de conformité aux utilisateurs

Une fois que l’administrateur a attribué des rôles de gestionnaire de conformité à d’autres utilisateurs, ces derniers peuvent afficher les données dans le gestionnaire de conformité et effectuer les actions déterminées par leur rôle. L’administrateur peut également accorder un accès en lecture seule au gestionnaire de conformité en affectant à ce dernier le [rôle de lecteur global dans Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-reader).

Chaque rôle de gestionnaire de conformité a des autorisations légèrement différentes. Vous pouvez afficher les autorisations affectées à chaque rôle, voir les utilisateurs qui se trouvent dans quels rôles et ajouter ou supprimer des utilisateurs de ce rôle via le portail d’approbation de services. Sélectionnez l’option de menu **admin** , puis choisissez les **paramètres** à afficher.
  
![Menu d’administration STP : paramètres sélectionnés](../media/65a82b1b-d462-452f-988b-7e4263bd638e.png)
  
Pour ajouter ou supprimer des utilisateurs des rôles du Gestionnaire de conformité.
  
1. Accédez à [https://servicetrust.microsoft.com](https://servicetrust.microsoft.com).

2. Connectez-vous avec votre compte Administrateur général Azure Active Directory.

3. Dans la barre de menus supérieure du portail d’approbation de service, sélectionnez **administrateur** , puis **paramètres**.

4. Dans la liste déroulante **Sélectionner un rôle** , sélectionnez le rôle que vous souhaitez gérer.

5. Les utilisateurs ajoutés à chaque rôle figurent sur la page **Sélectionner un rôle**.

6. Pour ajouter des utilisateurs à ce rôle, sélectionnez **Ajouter**. Dans la boîte de dialogue **Ajouter des utilisateurs** , sélectionnez le champ utilisateur. Vous pouvez faire défiler la liste des utilisateurs disponibles ou commencer à taper le nom d’utilisateur pour filtrer la liste en fonction de votre terme de recherche. Sélectionnez l’utilisateur qui doit ajouter ce compte à la liste **Ajouter des utilisateurs** mise en service avec ce rôle. Si vous souhaitez ajouter plusieurs utilisateurs simultanément, commencez à taper un nom d’utilisateur pour filtrer la liste, puis sélectionnez l’utilisateur à ajouter à la liste. Sélectionnez **Enregistrer** pour mettre en service le rôle sélectionné pour ces utilisateurs. 

    ![Gestionnaire de conformité — ajouter des utilisateurs](../media/compliance-manager-add-users.png)
  
7. Pour supprimer des utilisateurs de ce rôle, sélectionnez les utilisateurs et sélectionnez **supprimer**.

    ![Gestionnaire de conformité — supprimer des utilisateurs](../media/compliance-manager-delete-users.png)

### <a name="controlling-automatic-secure-score-updates"></a>Contrôle des mises à jour automatiques du score de sécurité

Les mises à jour du score sécurisé peuvent être activées automatiquement pour toutes les actions, désactivées pour toutes les actions ou définies par une action individuelle en procédant comme suit.

1. Connectez-vous au [portail d’approbation de service](https://servicetrust.microsoft.com) avec votre compte d’administrateur général.

2. Dans la barre de menus supérieure du portail d’approbation de service, sous **autres**, sélectionnez **administrateur** , puis **paramètres**.

3. Sous l’onglet **score sécurisé** , sélectionnez le bouton correspondant pour **activer toutes les actions**, **désactiver pour toutes les actions**ou **définir par action.**

Si vous choisissez **définir par action,** suivez ces étapes supplémentaires pour activer les mises à jour du score de sécurité pour des actions individuelles :

4. Sélectionnez **Gestionnaire de conformité** dans le menu supérieur (Remarque : ne sélectionnez pas « gestionnaire de conformité (classique) »).

5. Sélectionnez **gestion des clients** dans le coin supérieur droit de votre écran.

6. Dans le volet **actions client** , recherchez l’action souhaitée avec des points de suspension (**...**) dans la colonne **actions affectées** . Cliquez sur les ellipses et sélectionnez **modifier.**

7. Basculez le commutateur de basculement de **mise à jour continue de score de sécurité** **sur activé.**

8. Sélectionnez **Enregistrer.** Score de sécurité la surveillance continue est maintenant activée pour cette action.

**Remarque :** Seul l’administrateur général peut activer ou désactiver les mises à jour automatiques pour toutes les actions. L’administrateur du gestionnaire de conformité peut activer les mises à jour automatiques pour des actions individuelles, mais pas pour toutes les actions de manière globale.

## <a name="groups"></a>Groupes

Les groupes sont des conteneurs qui vous permettent d’organiser des évaluations et de partager des informations communes et des tâches de flux de travail entre les évaluations qui ont le même ou les mêmes contrôles gérés par le client.

Vous pouvez regrouper les évaluations d’une manière logique pour vous, par exemple par année, standard, service ou en fonction des équipes, divisions ou régions de votre organisation. Vous trouverez ci-dessous des exemples de deux groupes et de leurs évaluations sous-jacentes :
  
- **FFIEC est une évaluation 2020**
  - Office 365 + FFIEC est
  - Intune + FFIEC est
- **Évaluations de confidentialité et de sécurité des données**
  - Office 365 + ISO 27001:2013
  - Office 365 + ISO 27018:2014

> [!NOTE]
> Nous vous recommandons de déterminer une stratégie de regroupement pour votre organisation *avant* d’ajouter de nouvelles évaluations.

Pour vous aider à démarrer, un groupe **par défaut** est configuré pour vous, qui contient la base de données de protection des données. Cette ligne de base est un ensemble de contrôles qui inclut des normes et des réglementations industrielles communes ([en savoir plus](compliance-score-methodology.md#initial-score-based-on-microsoft-365-data-protection-baseline)).

### <a name="how-to-create-a-group"></a>Procédure de création d’un groupe

Les groupes ne peuvent pas être créés en tant qu’entités autonomes. Un groupe doit toujours contenir au moins une évaluation, donc pour créer un groupe, vous devez d’abord créer une évaluation à placer dans le groupe.

Suivez les étapes ci-dessous pour créer un groupe :

1. Créez une nouvelle évaluation en sélectionnant **+ Ajouter une évaluation** dans la partie supérieure de votre tableau de bord.
2. Dans le volet flyout d' **évaluation** , entrez un titre pour votre évaluation et sélectionnez un modèle dans le menu déroulant.
3. Sur **Sélectionnez un groupe ou ajouter un nouveau groupe**, sélectionnez **Ajouter un nouveau groupe** , puis entrez le nom de votre groupe dans le champ ci-dessous.
4. Pour copier des informations à partir d’un groupe existant, faites basculer la **copie des données d’un groupe existant** vers **.** Sélectionnez le groupe à copier dans le menu déroulant, puis activez les cases à cocher de tous les champs que vous souhaitez reporter dans la nouvelle évaluation de votre nouveau groupe.
5. Sélectionnez **Enregistrer**. Une fois l’opération terminée, le volet flyout se ferme et vous verrez votre nouveau groupe sur votre tableau de bord.

Éléments à connaître lors de l’utilisation de groupes :
  
- Les noms de groupe (également appelés *ID de groupe*) doivent être uniques au sein de votre organisation.
- Les groupes n’ont pas de propriétés de sécurité. Toutes les autorisations sont associées à des évaluations.
- Une fois que vous avez ajouté une évaluation à un groupe, le regroupement ne peut pas être modifié. Vous pouvez renommer le groupe d’évaluation, ce qui modifie le nom du regroupement d’évaluation pour toutes les évaluations associées à ce groupe.
- Les contrôles d’évaluation associés dans différentes évaluations au sein du même groupe sont automatiquement mis à jour lorsque vous avez terminé.
- Si vous ajoutez une nouvelle évaluation à un groupe existant, les informations courantes des évaluations de ce groupe sont copiées dans la nouvelle évaluation.
- Les groupes peuvent contenir des évaluations pour la même certification ou la même réglementation, mais chaque groupe ne peut contenir qu’une seule évaluation pour une paire de certification de produit spécifique. Par exemple, un groupe ne peut pas contenir deux évaluations pour Office 365 et l’infrastructure NIST. Un groupe peut contenir plusieurs évaluations pour le même produit uniquement si la certification ou la réglementation correspondante est différente.
- Le masquage d’une évaluation rompt la relation entre cette évaluation et le groupe. Les autres mises à jour apportées à d’autres évaluations associées ne sont plus reflétées dans l’évaluation cachée. ([Découvrez comment masquer les évaluations.](#hide-a-template-or-an-assessment))
- Les groupes ne peuvent pas être supprimés.
- Lorsqu’une modification est apportée à un élément d’action qui apparaît dans plusieurs groupes, cette modification est reflétée dans toutes les instances de cet élément d’action.

## <a name="tenant-management-of-dimensions-owners--customer-actions"></a>Gestion des clients pour les dimensions, les propriétaires & les actions des clients

L’interface de **gestion des clients** vous permet de gérer ces paramètres à l’échelle de l’Organisation :

- **Dimensions :** Affichez les métadonnées des modèles, des évaluations et des éléments d’action qui vous permettent de créer des tableaux croisés dynamiques personnalisés pour les filtres.
- **Propriétaires :** Remplissez une liste de parties responsables pouvant être associées à des actions.
- **Actions des clients :** Gérez la liste complète des éléments actions inclus dans le gestionnaire de conformité (aperçu) et activez/désactivez la surveillance du score sécurisé pour les actions intégrées à un score sécurisé.

Sélectionnez **gestion des clients** dans le coin supérieur droit de l’écran pour ouvrir l’interface de gestion et suivez les étapes ci-dessous pour gérer les **dimensions**, les **propriétaires**et les **actions des clients**.

### <a name="dimensions"></a>Dimensions

Les dimensions sont des ensembles de métadonnées qui fournissent des informations sur un modèle, une évaluation ou un élément d’action. Les dimensions utilisent le concept de clés et de valeurs, où la clé de dimension représente une propriété et la valeur de dimension représente des valeurs valides pour la propriété. Par exemple, dans le gestionnaire de conformité, il existe trois types d’actions. Elles sont définies par une clé de dimension de l' **objectif d’action** et des valeurs de dimension de **préventive**, de **détective**et de **Correction**.

### <a name="owners"></a>Owners

Les propriétaires sont utilisés pour identifier la personne responsable de chaque contrôle. Tous les contrôles intégrés appartiennent à Microsoft, aux clients ou aux deux. Vous pouvez créer des valeurs personnalisées pour les propriétaires qui peuvent être utilisées pour spécifier des responsabilités plus granulaires au sein de votre organisation. Par exemple, vous pouvez créer des propriétaires qui représentent des groupes, des équipes ou des divisions spécifiques au sein de votre organisation.

#### <a name="add-an-owner"></a>Ajouter un propriétaire

1. Ouvrez **gestion des clients** et sélectionnez **propriétaires**.
2. Sélectionnez **+ Ajouter un propriétaire**.
3. Indiquez un nom et une description pour le propriétaire, puis sélectionnez **Enregistrer**. La description est affichée dans la colonne propriétaire.

#### <a name="edit-an-owner"></a>Modifier un propriétaire

Vous ne pouvez pas modifier un nom de propriétaire, mais vous pouvez modifier la description qui est affichée dans la colonne propriétaire.

1. Ouvrez **gestion des clients** et sélectionnez **propriétaires**.
2. Recherchez le propriétaire que vous souhaitez modifier, sélectionnez les points de suspension (...) en regard de celui-ci, puis sélectionnez **modifier**.
3. Modifiez la description si nécessaire, puis sélectionnez **Enregistrer**.

#### <a name="delete-an-owner"></a>Supprimer un propriétaire

1. Ouvrez **gestion des clients** et sélectionnez **propriétaires**.
2. Recherchez le propriétaire que vous souhaitez supprimer, sélectionnez les points de suspension (...) en regard de celui-ci, puis sélectionnez **supprimer**.
3. Lorsque le message de confirmation s’affiche, sélectionnez **supprimer**.

### <a name="customer-actions"></a>Actions client

La zone actions client affiche toutes les actions des clients pour tous les modèles et évaluations dans le gestionnaire de conformité (aperçu).

![Gestionnaire de conformité — ajouter des utilisateurs](../media/compliance-manager-customer-actions.png "Actions client du gestionnaire de conformité")

En un clin d’œil, vous pouvez voir le titre, le propriétaire, la catégorie, l’application et le score d’une action, et déterminer si elle est intégrée avec le score de sécurité. Vous pouvez développer une action et sélectionner **More** pour lire la description de l’action et accéder à tous les liens dans la description. Vous pouvez également utiliser cette interface pour activer et désactiver l’intégration de la note sécurisée en fonction de l’action et pour ajouter des actions personnalisées. Les actions qui ont des fonctions d’intégration de score sécurisé comportent des points de suspension (...) en regard de celles-ci (Notez que les actions personnalisées comportent également des points de suspension).

#### <a name="enable-or-disable-secure-score-integration"></a>Activer ou désactiver l’intégration de la note sécurisée

1. Sélectionnez les points de suspension (...) de l’action que vous souhaitez modifier, puis sélectionnez **modifier**.
2. Basculez le commutateur de la mise à jour continue du score de sécurité sur activé ou désactivé pour activer ou désactiver la surveillance continue via le score de sécurité.
3. Sélectionnez **Enregistrer**.

Lorsque les organisations déploient d’abord Microsoft 365 ou Office 365, il faut environ sept jours pour que l’évaluation complète des données et les intégrer dans votre score. Pendant ce temps, la définition du commutateur de mise à jour continue de score de sécurité sur **désactivé** et la définition manuelle d’une action sur **implémenté** compteront cette action vers votre score. Une fois les sept jours initiaux, l’activation de la mise à jour continue du score sécurisé active la surveillance continue à partir de ce moment-là.

Toutes les actions qui ne sont pas prises en charge par l’intégration de la note sécurisée peuvent être implémentées manuellement. Une implémentation manuelle concerne le score du groupe de cette action.

## <a name="assessments"></a>Évaluations

Cette section explique comment afficher et utiliser vos évaluations, notamment comment en ajouter de nouvelles, les exporter, copier des informations à partir d’évaluations existantes et les conserver mises à jour via le contrôle de version.

### <a name="view-an-assessment-and-action-details"></a>Afficher les détails de l’évaluation et de l’action
  
Dans le tableau de bord **évaluations** , sélectionnez le nom de l’évaluation pour l’ouvrir et afficher les éléments d’action et les informations de contrôle.

Voici un exemple de l’évaluation pour Office 365 et ISO 27001. La première vue illustre la nouvelle vue actions dans le gestionnaire de conformité (aperçu).

![Affichage des éléments d’action du gestionnaire de conformité](../media/compliance-manager-action-items.png)

Les actions sont répertoriées par ordre alphabétique et un score et un propriétaire sont attribués à chaque action. Sélectionnez le lien **en savoir plus** pour lire les détails de chaque action.

![Affichage des éléments d’action du gestionnaire de conformité](../media/compliance-manager-actions-read-more.png)

Sélectionnez le lien **examiner** pour gérer, affecter, mettre en œuvre et tester l’action. Vous trouverez ci-dessous un exemple d’action.

![Vue d’action du gestionnaire de conformité](../media/compliance-manager-action.png)

Utilisez les champs suivants pour gérer le flux de travail d’action :

- **Attribuer un utilisateur :** Sélectionnez ce champ pour choisir ou entrer l’utilisateur auquel cette action doit être affectée. Vous pouvez faire défiler la liste ou taper un nom pour le trouver, puis le sélectionner.
- **Gérer les documents :** Vous pouvez charger des preuves de l’implémentation sous la forme de documents Office, de fichiers image et de captures d’écran, de sorties PowerShell au format CSV ou TXT, et de fichiers PDF.
- **État de l’implémentation :** Permet d’indiquer l’état actuel de l’implémentation. Les valeurs possibles ne sont pas implémentées, implémentées, une implémentation alternative, planifiée et non dans l’étendue.
- **Date d’implémentation :** Date à laquelle l’action a été effectuée.
- **Résultat du test :** Permet d’indiquer les résultats de la validation de l’implémentation. Les valeurs possibles ne sont pas calculées, transmises, échec-faible risque, échec moyen-risque, échec à haut risque et non dans l’étendue.
- **Date du test :** Date à laquelle la validation s’est produite.
- **Remarques sur l’implémentation :** Entrez les détails d’implémentation de votre organisation, ainsi que les notes que vous souhaitez inclure.
- **Plan de test :** Entrez les détails du plan de test pour cette action, ainsi que les notes que vous souhaitez inclure.
- **Informations supplémentaires :** Entrez des informations supplémentaires sur cette action ou la manière dont elle a été implémentée dans votre organisation, ainsi que les notes que vous souhaitez inclure.

Dans le tableau de bord informations sur les **contrôles** , vous pouvez afficher des informations sur les contrôles au niveau de l’évaluation et du modèle. Vous trouverez ci-dessous un exemple de tableau de bord d’informations des contrôles pour les évaluations.

![Vue infos sur les contrôles du gestionnaire de conformité](../media/compliance-manager-controls-info.png)

Pour les évaluations, le tableau de bord informations sur les contrôles affiche les informations suivantes :

- Une liste déroulante de **groupe** pour sélectionner le groupe à afficher (en cas d’utilisation de plusieurs groupes).
- Liste déroulante d' **évaluation** permettant de sélectionner l’évaluation à afficher.
- Métadonnées relatives à l’évaluation sélectionnée, notamment :
    - Indicateur de progression pour les **contrôles évalués** illustrant le nombre de contrôles évalués sur le nombre total de contrôles.
    - Score de **conformité** actuel pour l’évaluation, affiché sous la forme d’un pourcentage.
    - Détails sur la **certification** et le **produit** utilisés dans l’évaluation.
    - **État** actuel et date de dernière **modification** de l’évaluation.
- Une liste des **services dans l’étendue** pour l’évaluation.
- Détails des contrôles, regroupés par famille de contrôle, avec des liens vers les actions client et les détails de la mise en œuvre de Microsoft :
    - **Vos actions** affichent les actions du client que vous pouvez effectuer pour satisfaire une partie ou la totalité des exigences du contrôle. De nombreux contrôles ont plusieurs actions associées et toutes les actions associées à un contrôle sont affichées ici. Les actions indiquées ici ont la même interface utilisateur que celles répertoriées dans le tableau de bord actions.
    - **Actions Microsoft** : affiche la liste des contrôles de l’infrastructure interne de Microsoft qui s’appliquent au contrôle de certification sélectionné. Pour chaque contrôle interne, sélectionnez **implémenté** pour afficher les détails de l’implémentation et du test de Microsoft, ainsi que le résultat du test et la date du test, comme indiqué ci-dessous.

![Gestionnaire de conformité-vue d’action Microsoft](../media/compliance-manager-microsoft-action.png)

### <a name="add-an-assessment"></a>Ajouter une évaluation
  
1. Dans le tableau de bord évaluations, sélectionnez **+ Ajouter une évaluation**.

2. À l’ouverture de la lame, entrez les informations suivantes :

    - **Titre (obligatoire) :** Entrer un titre pour votre évaluation
    - **Sélectionnez un modèle (obligatoire) :** Sélectionner un modèle standard ou personnalisé
    - **Sélectionnez un groupe ou ajoutez un nouveau groupe (obligatoire) :** Sélectionnez un groupe existant ou choisissez d’ajouter un nouveau groupe, et fournissez un nom de groupe unique.
    - Voulez- **vous copier les données à partir d’un groupe existant ? (facultatif) :** fait basculer le contrôle pour activer la copie de groupe, puis :
        - **Sélectionnez un groupe (facultatif) :** Si la copie de groupe est activée, sélectionnez le groupe à partir duquel effectuer la copie.
            - **Détails de l’implémentation (facultatif) :** Sélectionnez cette option pour copier les détails de l’implémentation dans le nouveau groupe.
            - **Plan de Test & des informations supplémentaires (facultatif) :** Sélectionnez cette option pour copier le plan de test et les détails des informations supplémentaires dans le nouveau groupe.
            - **Documents (facultatif) :** Sélectionnez cette option pour copier les documents vers le nouveau groupe

3. Sélectionnez **Enregistrer** pour créer l’évaluation.

 La nouvelle évaluation apparaît sur le tableau de bord d’évaluation et affiche les informations suivantes :

- Titre de l’évaluation.
- Les dimensions de l’évaluation, y compris la certification, l’environnement et le produit, appliquées à l’évaluation.
- Date de création et date de la dernière modification.
- Score d’évaluation affiché sous la forme d’un pourcentage. Ce score inclut automatiquement vos scores à partir des contrôles gérés par Microsoft et du score de sécurité.
- Indicateurs de progression indiquant le nombre de contrôles évalués gérés par Microsoft et gérés par le client.

### <a name="copying-information-from-existing-assessments"></a>Copie des informations des évaluations existantes

Lorsque vous créez une évaluation, vous avez la possibilité de copier des informations à partir d’un groupe existant. La copie vous permet d’appliquer les informations entrées dans l’évaluation copiée aux mêmes contrôles dans la nouvelle évaluation. Par exemple, si vous avez un groupe pour toutes les évaluations liées à FFIEC dans votre organisation, vous pouvez copier les informations suivantes à partir d’évaluations existantes :

- Détails de l’implémentation
- Plan de test & des informations supplémentaires
- Documents

#### <a name="copy-information-from-an-existing-assessment-to-a-new-assessment"></a>Copier des informations d’une évaluation existante vers une nouvelle évaluation
  
1. Dans le tableau de bord d’évaluation, sélectionnez **+ Ajouter une évaluation**.
    
2. Dans la fenêtre **Ajouter une évaluation** , fournissez les informations suivantes

    - **Titre (obligatoire) :** Entrez un titre pour votre évaluation.
    - **Sélectionnez un modèle (obligatoire) :** Sélectionnez un modèle standard ou personnalisé.
    - **Sélectionnez un groupe ou ajoutez un nouveau groupe (obligatoire) :** Sélectionnez **Ajouter un nouveau groupe** et indiquez un nom de groupe unique.
    - Voulez- **vous copier les données à partir d’un groupe existant ? (facultatif) :** fait basculer le contrôle sur activé pour activer la copie de groupe, puis :- **Sélectionner un groupe (facultatif) :** si la copie de groupe est activée, sélectionnez le groupe à partir duquel copier.
            - **Détails de l’implémentation (facultatif) :** Sélectionnez cette option pour copier les détails de l’implémentation dans le nouveau groupe.
            - **Plan de Test & des informations supplémentaires (facultatif) :** Sélectionnez cette option pour copier le plan de test et les détails des informations supplémentaires dans le nouveau groupe.
            - **Documents (facultatif) :** Sélectionnez cette option pour copier les documents vers le nouveau groupe.

3. Sélectionnez **Enregistrer** pour créer l’évaluation.

### <a name="versioning-alerts-for-assessment-updates"></a>Alertes de versioning pour les mises à jour d’évaluation

Lorsqu’une mise à jour est disponible pour une évaluation, une icône d’alerte vous signale qu’une mise à jour est prête. Lorsque vous cliquez sur cette icône, une fenêtre contextuelle explique la mise à jour et vous invite à accepter. Voici un exemple d’alerte de contrôle de version pour une évaluation :

![Score de conformité-alerte de contrôle de version](../media/compliance-score-assessment-version.png "Alerte de mise à jour de version d’évaluation")

La sélection de l’icône d’alerte révèle un volet flyout expliquant la mise à jour et vous invitant à accepter les éléments suivants :

![Score de conformité-menu volant de gestion des versions](../media/compliance-score-assessment-version-accept.png "Volet de confirmation de mise à jour d’évaluation")

Nous vous recommandons vivement d’accepter toutes les mises à jour lorsque vous recevez des notifications de mise à jour.

### <a name="export-an-assessment"></a>Exporter une évaluation

Vous pouvez exporter une évaluation vers un fichier Excel pour les parties prenantes en conformité dans votre organisation ou pour les auditeurs et régulateurs externes. Le rapport est une capture instantanée de l’évaluation à compter de la date et de l’heure de création du rapport. Le rapport contient les détails de tous les contrôles gérés par Microsoft et par le client pour l’évaluation, le contrôle de l’état de l’implémentation, le contrôle de la date de test, les résultats des tests et fournit des liens vers les documents de preuve téléchargés.
  
### <a name="export-an-assessment-report"></a>Exporter un rapport d’évaluation
  
1. Dans le tableau de bord du gestionnaire de conformité, sélectionnez l’onglet **contrôles et informations** .
2. Sélectionnez le **groupe** et l' **évaluation** dans les menus déroulants pour l’évaluation que vous souhaitez exporter.
3. Sélectionnez le bouton **Exporter** .

Le rapport d’évaluation est téléchargé sous la forme d’un fichier Excel dans votre session de navigateur. Le nom de fichier du fichier Excel est par défaut le titre de l’évaluation.

### <a name="hide-a-template-or-an-assessment"></a>Masquer un modèle ou une évaluation

Lorsque vous avez terminé d’utiliser un modèle ou une évaluation et que vous n’en avez plus besoin à des fins de conformité, vous pouvez le masquer à partir de votre affichage. Lorsqu’un modèle ou une évaluation est masquée, elle est supprimée de la vue par défaut et vous devez activer la case à cocher **inclure les masqués** pour l’afficher.

![Affichage du modèle masqué du gestionnaire de conformité](../media/compliance-manager-hidden-template.png "Modèle masqué du gestionnaire de conformité")

> [!IMPORTANT]
> Les évaluations masquées ne conservent pas leurs liens vers les documents de preuve téléchargés. Nous vous recommandons vivement d’exporter une évaluation avant de la masquer pour conserver des liens vers des documents de preuve dans le rapport.
  
#### <a name="hiding-a-template"></a>Masquage d’un modèle

1. Ouvrez le tableau de bord **modèles** .
2. Recherchez le modèle que vous souhaitez masquer et les ellipses de sa ligne, sélectionnez **Masquer**.
3. Lorsque le message de confirmation s’affiche, sélectionnez **Masquer**.

#### <a name="hide-an-assessment"></a>Masquer une évaluation

1. Ouvrez le tableau de bord **évaluations** .
2. Dans la liste déroulante, sélectionnez le **groupe** qui contient l’évaluation à masquer.
3. Recherchez l’évaluation que vous souhaitez masquer et, dans les ellipses, sélectionnez **Masquer**.
4. Lorsque le message de confirmation s’affiche, sélectionnez **Masquer**.

#### <a name="view-hidden-assessments"></a>Afficher les évaluations masquées
  
1. Ouvrez l’onglet de tableau de bord **évaluations** et activez la case à cocher **inclure les masqués** .
2. Les évaluations masquées apparaissent dans la section **évaluations masquées** .

#### <a name="unhide-an-assessment"></a>Afficher une évaluation

1. Sous l’onglet **évaluations** , activez la case à cocher **inclure les masqués** .
2. Les évaluations masquées apparaissent dans la section **évaluations masquées** .
3. Localisez l’évaluation que vous souhaitez afficher et les ellipses, sélectionnez **Afficher**.
4. Lorsque le message de confirmation s’affiche, sélectionnez **Afficher**.

## <a name="controls-and-actions"></a>Contrôles et actions

Les contrôles et les actions sont les principaux tableaux croisés dynamiques utilisés dans le gestionnaire de conformité (aperçu). Le tableau croisé dynamique de contrôle, qui existait dans les versions précédentes du gestionnaire de conformité, a été amélioré pour afficher les contrôles Microsoft et client dans les mêmes familles de contrôle. Cette vue consolidée facilite l’affichage du modèle de responsabilité partagé complet par contrôle. Le tableau des actions est nouveau dans le gestionnaire de conformité (Preview) et il est conçu pour offrir une vue simplifiée de toutes les actions recommandées par Microsoft.

### <a name="controls"></a>Contrôles

Les contrôles peuvent être affichés à partir du tableau de bord informations sur les contrôles. Les contrôles représentent les exigences d’une norme, d’une certification, d’une réglementation ou d’une infrastructure. Pour mapper ces exigences sur plusieurs normes, réglementations, etc., et les associer à des actions, tout est traité comme s’il s’agissait d’une infrastructure de contrôle. Par exemple, comme une infrastructure de contrôle, les réglementations, telles que HIPAA, ont été divisées par section, et les contrôles HIPAA du gestionnaire de conformité utilisent le même schéma de numérotation que ces sections, comme indiqué ci-dessous :

![Détails des contrôles Microsoft du gestionnaire de conformité](../media/compliance-manager-control-details.png)

Il existe trois types de contrôles :

1. **Contrôles gérés par Microsoft :** il s’agit de contrôles pour lesquels seul Microsoft est responsable. Ils apparaissent dans les modèles prédéfinis et sont ajoutés au gestionnaire de conformité par Microsoft.
2. **Contrôles gérés par le client :** il s’agit de contrôles dont les clients sont responsables uniquement. Ils apparaissent dans les modèles prédéfinis et sont ajoutés au gestionnaire de conformité par les clients.
3. **Contrôles de gestion partagés :** il s’agit de contrôles où la responsabilité est partagée entre Microsoft et le client. Ceux-ci apparaissent dans les modèles prédéfinis et sont ajoutés au gestionnaire de conformité par Microsoft. Le client peut également modifier ou désactiver les contrôles gérés par Microsoft.

### <a name="actions-items"></a>Éléments actions

Actions les éléments sont les tâches recommandées pour la mise en œuvre des exigences d’une norme ou d’une réglementation, ou pour tester, vérifier et documenter les exigences d’implémentation de votre organisation. Les actions sont associées à un ou plusieurs contrôles. Chaque contrôle a une ou plusieurs actions associées, et chaque action peut être associée à un ou plusieurs contrôles. Les actions font partie du flux de travail de base dans le gestionnaire de conformité (Preview), car il s’agit des objets qui sont affectés, suivis et validés par votre organisation.

#### <a name="assign-action-items"></a>Affecter des éléments d’action
  
1. Dans le tableau de bord **éléments d’action** , sélectionnez le **groupe** contenant les évaluations dont vous souhaitez affecter l’action.
2. Dans la liste déroulante **évaluation** , sélectionnez l’évaluation dont vous souhaitez affecter l’action ou sélectionnez **toutes** dans la liste déroulante pour afficher toutes les actions disponibles.
3. Localisez l’action que vous souhaitez attribuer, puis dans la colonne **propriétaire** , sélectionnez le lien à **réviser**, * * implémenté ou **test**.
4. Sélectionnez le champ **affecter un utilisateur** , et une liste d’utilisateurs de votre organisation apparaît. Faites défiler la liste et sélectionnez utilisateur ou filtrez la liste pour sélectionner un utilisateur en tapant son nom.
5. Dans le champ Remarques d’implémentation, entrez les remarques que vous souhaitez transmettre à l’utilisateur affecté.
6. Sélectionnez **Enregistrer** pour affecter l’action.

#### <a name="reassign-action-items"></a>Réaffecter des éléments d’action

Cette fonction permet à une organisation de supprimer toutes les dépendances actives ou en suspens sur le compte d’utilisateur en réaffectant une action à un nouvel utilisateur.

1. Dans le tableau de bord **éléments d’action** , sélectionnez le **groupe** contenant les évaluations dont vous souhaitez réaffecter l’action.
2. Dans la liste déroulante **évaluation** , sélectionnez l’évaluation dont vous souhaitez réaffecter l’action ou sélectionnez **toutes** dans la liste déroulante pour afficher toutes les actions disponibles.
3. Localisez l’action que vous souhaitez réaffecter, puis dans la colonne **propriétaire** , sélectionnez le lien pour **révision**, **implémenté**ou **test**.
4. Supprimez l’utilisateur existant du champ **Assign User** , puis choisissez un autre utilisateur dans la liste des utilisateurs ou filtrez la liste pour sélectionner un utilisateur en tapant son nom.
5. Dans le champ Remarques d’implémentation, entrez les remarques que vous souhaitez transmettre à l’utilisateur.
6. Sélectionnez **Enregistrer** pour réaffecter l’action.

#### <a name="common-action-items-synch-status-across-groups"></a>Éléments d’action courants synchronisés entre les groupes

Si votre organisation dispose de plusieurs groupes d’évaluations, il existe un comportement des actions techniques (c’est-à-dire, des actions affectant l’ensemble de votre organisation). Toutes les actions en double entre les groupes sont désormais regroupées en une seule action. Cette action unique contient toutes les notes téléchargées et les preuves provenant de versions déjà dupliquées. Toute modification apportée à l’action dans un groupe ou une évaluation est reflétée dans toutes les instances de cette action. Les champs **État**de l’implémentation, **Date de mise en œuvre**, **État du test**et date du **test** reflètent les mises à jour les plus récentes.

## <a name="templates"></a>Modèles

Un modèle est l’objet de base dans le gestionnaire de conformité (aperçu) qui est associé à un produit et à une certification (par exemple, standard, réglementation, infrastructure de contrôle, etc.). Les modèles peuvent être affichés et ajoutés à partir du tableau de bord **modèles** .

![Tableau de bord de modèles Microsoft du gestionnaire de conformité](../media/compliance-manager-template-dashboard.png)
 
Le tableau de bord affiche chaque modèle, ainsi que la certification et le produit associés au modèle, les dates auxquelles le modèle a été créé et modifié pour la dernière fois, le nombre de clients et les contrôles gérés par Microsoft, le score de conformité maximal pour le modèle et l’état du modèle (par exemple, approuvé, en attente d’approbation, importé).

### <a name="create-a-template"></a>Créer un modèle

Il existe trois façons de travailler avec des modèles pour créer des évaluations :

1. Utilisez l’un des modèles préconfigurés fournis par Microsoft.
2. Personnaliser un modèle préconfiguré avec vos propres actions et contrôles via le processus d’extension.
3. Créez votre propre modèle et importez-le dans le gestionnaire de conformité.

#### <a name="use-a-microsoft-pre-configured-template"></a>Utiliser un modèle préconfiguré Microsoft

Les modèles préconfigurés sont disponibles dans le tableau de bord **modèles** . Afficher la [liste actuelle des modèles](compliance-manager-overview.md#templates), qui est mise à jour chaque fois qu’un nouveau modèle est disponible.

#### <a name="customize-a-template-through-the-extension-process"></a>Personnaliser un modèle via le processus d’extension

1. Ouvrez le tableau de bord **modèles** et sélectionnez **+ Ajouter un modèle**.
2. Dans le volet flyout de modèle, activez la case à cocher **créer une extension à partir du modèle global** .
3. Dans le menu déroulant, sélectionnez le modèle que vous souhaitez étendre.
4. Si vous n’avez pas déjà mis en forme les données de votre modèle dans Excel, sélectionnez le lien dans le volet flyout pour télécharger un fichier Excel. Remplissez la feuille de calcul en fonction des instructions d' [importation de données de modèle avec Excel](#import-template-data-with-excel) ci-dessous et enregistrez-la sur votre lecteur local.
5. Importez les données de votre modèle personnalisé en sélectionnant **Parcourir** pour charger votre fichier Excel.
6. Sélectionnez **Ajouter au tableau de bord**. Votre nouveau modèle est ensuite ajouté à votre tableau de bord **modèles** .

#### <a name="create-your-own-template-and-import-it-into-compliance-manager"></a>Créez votre propre modèle et importez-le dans le gestionnaire de conformité

1. Ouvrez le tableau de bord **modèles** et sélectionnez **+ Ajouter un modèle**.
2. Dans le volet flyout de modèle, sélectionnez **créer un nouveau modèle**.
3. Importez les données de votre modèle en sélectionnant **Parcourir** pour charger votre fichier Excel contenant les données (voir [Import template Data with Excel](#import-template-data-with-excel) ci-dessous).
4. Sélectionnez **Ajouter au tableau de bord**. Votre nouveau modèle est ensuite ajouté à votre tableau de bord **modèles** .

#### <a name="import-template-data-with-excel"></a>Importer des données de modèle avec Excel

Pour modifier un modèle ou créer votre propre modèle, vous allez utiliser une [feuille de calcul Excel](https://go.microsoft.com/fwlink/?linkid=2124865) pour capturer les données nécessaires et les charger dans le gestionnaire de conformité. Ce modèle de feuille de calcul a un format et un schéma spécifiques qui doivent être utilisés ou qui ne seront pas importés dans le gestionnaire de conformité.

> [!IMPORTANT]
> Si vous avez déjà créé ou personnalisé des modèles dans le gestionnaire de conformité, **ce processus a été mis à jour** dans le cadre de la version du gestionnaire de conformité d’avril 2020 (aperçu). **Veuillez consulter attentivement cette section.**

La feuille de calcul contient quatre onglets, trois étant obligatoires :

1. Modèle (obligatoire)
2. ControlFamily (obligatoire)
3. Actions (obligatoire)
4. Dimensions (facultatif)

Votre feuille **de calcul doit inclure les onglets dans cet ordre**, sinon vos données ne peuvent pas être correctement importées dans un modèle.

##### <a name="template-tab"></a>Onglet modèle

L’onglet **modèle** est obligatoire. Les informations de cet onglet fournissent des métadonnées sur le modèle. Il y a quatre colonnes obligatoires. Les colonnes doivent conserver la commande sur la feuille Excel, comme indiqué ci-dessous. Vous pouvez ajouter votre propre colonne **après** les quatre colonnes pour fournir vos propres dimensions. Si vous procédez ainsi, veillez à les ajouter à l’onglet **dimensions** en suivant les [instructions ci-dessous](#dimensions-tab).

- **titre**: il s’agit du titre de votre modèle, qui doit être unique. Il ne peut pas partager un nom avec un autre modèle que vous avez dans le gestionnaire de conformité, qu’il s’agisse d’un modèle que vous avez déjà créé ou d’un modèle préconfiguré fourni par Microsoft.

- **Product**: il s’agit d’une dimension obligatoire. Répertoriez le produit associé au modèle.

- **certification**: il s’agit de la règle que vous utilisez pour le modèle.

- **inScopeServices**: il s’agit des services du produit que cette évaluation adresse (par exemple, si vous avez répertorié Office 365 comme produit, Microsoft teams pourrait être un service dans l’étendue). Vous pouvez répertorier plusieurs services séparés par deux points-virgules.

> [!NOTE]
> En ce qui concerne les produits et la certification : les données que vous insérez dans le **produit** et les cellules de **certification** ne peuvent pas être modifiées une fois la feuille de calcul importée pour créer ou personnaliser un modèle. De plus, un groupe ne peut pas contenir deux évaluations qui ont la même combinaison de **produit/certification** . Vous pouvez avoir plusieurs modèles qui ont la même combinaison de produit/certification.

##### <a name="controlfamily-tab"></a>Onglet ControlFamily

L’onglet **ControlFamily** est obligatoire.  Les colonnes obligatoires de cet onglet, qui doivent respecter l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivantes :

- **nomcontrôle**: nom de contrôle de la certification, de la norme ou de la réglementation, qui est généralement un type d’ID. Les noms de contrôle doivent être uniques dans un modèle. Vous ne pouvez pas avoir plusieurs contrôles portant le même nom dans la feuille de calcul.

- **controlFamily**: fournissez un mot ou une expression pour le controlFamily, qui identifie un large regroupement de contrôles. Un controlFamily ne doit pas nécessairement être unique ; elle peut être affichée plusieurs fois dans une feuille de calcul. Le même controlFamily peut également être mis en vente dans plusieurs modèles, même s’ils n’ont pas de relation les uns avec les autres. Chaque controlFamily doit être mappé à au moins un contrôle.

- **controlTitle**: fournissez un titre pour le contrôle. Alors que NomContrôle est un code de référence, le titre est un format de texte enrichi généralement visible dans les réglementations.

- **controlDescription**: fournissez une description du contrôle.

- **controlActionTitle**: il s’agit du titre d’une action que vous souhaitez associer à ce contrôle. Vous pouvez ajouter plusieurs actions en séparant par deux points-virgules sans espace. Chaque contrôle que vous répertoriez doit inclure au moins une action, et l’action doit exister (ce qui signifie que vous pouvez répertorier une action que vous répertoriez sous l’onglet **actions** de la même feuille de calcul, une action qui existe dans un autre modèle ou une action créée par Microsoft). Différents contrôles peuvent faire référence à la même action.

##### <a name="actions-tab"></a>Onglet actions

L’onglet **actions** est obligatoire.  Il désigne les actions de votre organisation et non pas les actions de Microsoft, qui existent déjà dans le gestionnaire de conformité. Les colonnes requises pour cet onglet, qui doivent respecter l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivantes :

- **actionTitle**: il s’agit du titre de votre action et est un champ obligatoire. Le titre que vous fournissez doit être unique. **Important**: Si vous faites référence à une action que vous possédez déjà (par exemple, dans un autre modèle) et que vous modifiez l’un de ses éléments dans les colonnes suivantes, ces modifications seront répercutées dans la même action dans d’autres modèles.

- **implementationType**: dans ce champ obligatoire, répertoriez l’un des trois types d’implémentation ci-dessous :
    - **Opérations-actions** mises en œuvre par des personnes et des processus pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes, des biens, des données et du personnel de l’organisation (exemple : sensibilisation et formation à la sécurité)
    - **Techniques** : actions accomplies via l’utilisation de technologies et de mécanismes contenus dans les composants matériels, logiciels ou microprogrammes du système d’information afin de protéger la confidentialité, l’intégrité et la disponibilité des systèmes et des données de l’organisation (exemple : authentification multifacteur)
    - **Documentation** -actions mises en œuvre via des stratégies et des procédures documentées qui établissent et définissent les contrôles requis pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes, des biens, des données et du personnel de l’organisation (exemple : une stratégie de sécurité des informations)

- **actionScore**: dans ce champ obligatoire, fournissez une valeur de score numérique pour votre action. Il doit être un nombre entier compris entre 1 et 99 ; il ne peut pas être égal à 0, null ou vide. Plus le nombre est élevé, plus sa valeur augmente pour améliorer la conformité. Pour obtenir des instructions, voir ci-dessous comment Microsoft note ses contrôles :

![Contrôle du gestionnaire de conformité-valeurs de points](../media/compliance-score-controls-scoring.png "Contrôle du gestionnaire de conformité-valeurs de points")

- **actionDescriptionTitle**: il s’agit du titre de la description et est obligatoire. Ce titre de description vous permet d’avoir la même action dans plusieurs modèles et de faire apparaître une description différente dans chaque modèle.  Ce champ vous permet de clarifier le modèle référencé par la description. Dans la plupart des cas, vous pouvez placer le nom du modèle que vous créez dans ce champ.

- **actionDescription**: fournissez une description de l’action. Vous pouvez appliquer une mise en forme telle que le texte gras et les liens hypertexte. Champ obligatoire.

- **dimension-action d’action**: il s’agit d’un champ facultatif. Si vous l’incluez, l’en-tête doit inclure le préfixe « dimension- ». Toutes les dimensions que vous incluez ici seront utilisées en tant que [filtres dans le score de conformité](compliance-score-setup.md#filtering-your-dashboard-view) et apparaissent sur la [page des détails des actions d’amélioration dans le score de conformité](working-with-compliance-score.md#view-your-improvement-actions).

##### <a name="dimensions-tab"></a>Onglet dimensions

L’onglet **dimensions** est facultatif. Toutefois, si vous référencez une dimension ailleurs, vous devez la spécifier ici si elle n’existe pas dans un modèle que vous avez déjà créé ou dans un modèle Microsoft. Les colonnes de cet onglet sont répertoriées ci-dessous :

- **dimensionKey**: liste en tant que « produit », « certifications », « objectif de l’action »
- **dimensionValue**: exemples : Office 365, HIPPA, préventive, détective

Vous pouvez afficher vos dimensions existantes en accédant à **gestion des clients** et en sélectionnant l’onglet **dimensions** . Par ailleurs, chaque fois que vous exportez un modèle existant, la feuille de calcul exportée aura l’onglet **dimensions** , qui répertorie toutes les dimensions utilisées dans le modèle.

### <a name="modify-an-existing-template"></a>Modifier un modèle existant

Pour modifier un modèle que vous avez créé ou personnalisé à l’aide du processus d’importation décrit ci-dessus, vous devez utiliser la même procédure pour importer ces modifications dans votre modèle.

> [!NOTE]
> Il existe plusieurs facteurs importants à prendre en compte lors de la modification des composants de modèle, c’est pourquoi nous vous recommandons de consulter attentivement cette section.

#### <a name="general-process-for-modifying-a-template"></a>Processus général de modification d’un modèle

Pour modifier l’un des modèles existants de votre organisation, le processus général est le suivant :

1. Dans votre tableau de bord **modèles** , sélectionnez le modèle que vous souhaitez modifier, qui affiche le tableau de bord **informations sur les contrôles** affichant votre onglet **modèle** .
2. À partir de là, sélectionnez **Exporter**. Une feuille Excel avec toutes vos données de modèle seront téléchargées.
3. Pour modifier, ajouter ou supprimer une action, consultez les sections ci-dessous.
4. Lorsque vous avez terminé d’apporter des modifications à votre fichier Excel, importez le fichier dans le modèle en sélectionnant le modèle dans votre tableau de bord et en sélectionnant **Importer**. Votre modèle inclut désormais les modifications que vous avez apportées.

#### <a name="to-edit-template-attributes"></a>Pour modifier les attributs de modèle

Sous l’onglet **modèles** , vous pouvez modifier n’importe quel élément dans la colonne **titre** , la colonne **inScopeServices** , ainsi que dans n’importe quelle autre colonne que vous avez peut-être ajoutée. Toutefois, vous ne pouvez rien modifier dans les colonnes de **produit** ou de **certification** .

#### <a name="to-add-an-action-to-a-template"></a>Pour ajouter une action à un modèle

1. Accédez à l’onglet **actions** et ajoutez vos informations dans les champs obligatoires de la première ligne vide sous vos actions existantes.
2. Accédez à l’onglet **ControlFamily** . Recherchez la ligne contenant le contrôle auquel votre action est mappée. Ajoutez votre nouvelle action à la colonne **controlActionTitle** de cette ligne (n’oubliez pas de séparer plusieurs actions de ce champ par deux points-virgules, sans espace entre).
3. Enregistrez votre feuille de calcul sur votre ordinateur local.

#### <a name="to-edit-an-actions-information"></a>Pour modifier les informations d’une action

Vous pouvez modifier les informations d’une action *, à l’exception de son titre*. Vous pouvez modifier une cellule à partir des colonnes B et, lorsque vous réimportez le fichier dans le modèle, les actions de ce modèle contiendront désormais les données mises à jour.

Vous ne pouvez pas modifier la **actionTitle** (colonne A) car si vous le faites, le gestionnaire de conformité considère qu’il s’agit d’une nouvelle action. Si vous souhaitez modifier le nom d’une action, consultez les instructions immédiatement en dessous.

#### <a name="to-change-the-name-of-an-action"></a>Pour modifier le nom d’une action

Si vous souhaitez modifier le nom d’une action, vous devez explicitement indiquer dans la feuille de calcul que vous remplacez un nom existant par un nouveau nom. Pour modifier le nom d’une action, procédez comme suit :

1. Dans l’onglet **actions** de votre feuille de calcul, ajoutez une nouvelle colonne à la feuille de calcul après la colonne a.
2. Dans cette nouvelle colonne, qui est maintenant la colonne B, placée en tant qu’en-tête dans la ligne 1 : **oldActionTitle**.
3. Copiez le contenu de la colonne A et collez-le dans la colonne B. Cela place les titres d’action existants, qui sont les éléments que vous souhaitez modifier, dans la colonne B.
4. Dans la colonne A, **actionTitle**, supprimez l’ancien nom et remplacez-le par le nouveau nom de l’action.

#### <a name="to-remove-an-action-from-a-template"></a>Pour supprimer une action d’un modèle

La suppression d’une action d’une ligne dans une feuille de calcul **ne supprime pas** l’action du modèle que vous modifiez. Au lieu de cela, suivez la procédure ci-dessous pour supprimer une action :

1. Sous l’onglet **actions** , insérez une nouvelle colonne en tant que colonne a **et put dans** la ligne d’en-tête, qui est le numéro de ligne 1.
2. Sur la ligne de l’action que vous souhaitez supprimer, placez **supprimer** dans la colonne A pour cette ligne.
3. Assurez-vous que cette action n’est plus référencée par un contrôle. Accédez à l’onglet **ControlFamily** et recherchez le titre de votre action dans la colonne F, qui est **controlActionTitle**.
4. Lorsque vous trouvez les actions indiquées dans la colonne **controlActionTitle** , supprimez-les.
5. Enregistrez votre feuille de calcul sur votre ordinateur local.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre action est supprimée du modèle. La suppression d’une action d’un modèle ne supprime pas complètement l’action. Cette action peut toujours être référencée par un autre modèle.

Si vous supprimez la dernière action référencée par un contrôle, vous devez supprimer le contrôle.

> [!NOTE]
> Pour supprimer un contrôle, procédez de la même manière que pour supprimer une action comme indiqué ci-dessus. Dans l’onglet **ControlFamily** , ajoutez une colonne **opération** et placez la **suppression** en regard du contrôle que vous souhaitez supprimer.

### <a name="updates-to-templates"></a>Mises à jour des modèles

Chaque fois qu’une évaluation est mise à jour via le processus de contrôle de version, votre évaluation personnalisée hérite de ces mises à jour et conserve vos contrôles personnalisés. Consultez la rubrique [gestion des versions des alertes pour les mises à jour d’évaluation](#versioning-alerts-for-assessment-updates).

### <a name="export-a-template-to-json"></a>Exporter un modèle vers JSON

Gestionnaire de conformité (aperçu) prend en charge l’exportation des modèles au format JSON (JavaScript Object Notation). Cela vous permet d’échanger des données du gestionnaire de conformité avec d’autres systèmes qui prennent en charge JSON.

## <a name="reports"></a>Rapports

Vous pouvez exporter une évaluation vers un fichier Excel pour les parties prenantes en conformité dans votre organisation ou pour les auditeurs et régulateurs externes. Le rapport est une capture instantanée de l’évaluation à compter de la date et de l’heure de l’exportation. Le rapport contient les détails de Microsoft et des contrôles gérés par le client pour l’évaluation, le contrôle de l’état de l’implémentation, le contrôle de la date de test, les résultats des tests et les liens vers les documents de preuve téléchargés. Étant donné que les évaluations masquées ne retiennent pas les liens vers les documents téléchargés, vous devez exporter l’évaluation avant de la masquer.

### <a name="export-an-assessment"></a>Exporter une évaluation

1. Dans le tableau de bord du gestionnaire de conformité, sélectionnez l’onglet **contrôles et informations** .
2. Sélectionnez le groupe et l’évaluation dans les menus déroulants pour l’évaluation que vous souhaitez exporter.
3. Sélectionnez Exporter. L’exportation de l’évaluation est téléchargée sous la forme d’un fichier Excel.

![Rapport Excel d’évaluation du gestionnaire de conformité](../media/compliance-manager-assessment-report.png "Rapport Excel d’évaluation du gestionnaire de conformité")

## <a name="permissions"></a>Autorisations

Le tableau suivant décrit chaque autorisation du gestionnaire de conformité et ce qu’il permet à l’utilisateur d’effectuer. Le tableau indique également le rôle auquel chaque autorisation est attribuée.

||**Lecteur global Azure AD**|**Lecteur du Gestionnaire de conformité**|**Contributeur du Gestionnaire de conformité**|**Évaluateur du Gestionnaire de conformité**|**Administrateur du Gestionnaire de conformité**|**Administrateur du Portail**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**Lire les données :** Les utilisateurs peuvent lire, mais pas modifier les données (à l’exception des données de modèle et de gestion des clients).  <br> | X | X | X | X | X  | X |
|**Modifier les données :** Les utilisateurs peuvent modifier tous les champs, à l’exception des champs résultat de test et date du test (sauf pour les données de modèle et la gestion des clients).  <br> ||| X | X  | X | X |
|**Modifier les résultats des tests :** Les utilisateurs peuvent modifier les champs résultat de test et date du test.  <br> |||| X | X | X |
|**Gérer les évaluations :** Les utilisateurs peuvent créer, archiver et supprimer des évaluations.  <br> ||||| X | X |
|**Gérer les données principales :** Les utilisateurs peuvent afficher, modifier et supprimer des données de modèle et des données de gestion des clients.  <br> ||||| X | X |
|**Gérer les utilisateurs :** Les utilisateurs peuvent ajouter d’autres utilisateurs au sein de leur organisation aux rôles lecteur, collaborateur, évaluateur et administrateur. Seuls les utilisateurs disposant du rôle administrateur général dans votre organisation peuvent ajouter ou supprimer des utilisateurs du rôle d’administration du portail.  <br> |||||| X |