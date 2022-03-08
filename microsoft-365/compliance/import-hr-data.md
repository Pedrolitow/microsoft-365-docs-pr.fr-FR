---
title: Configurer un connecteur pour importer des données RH
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: Les administrateurs peuvent configurer un connecteur de données pour importer les données des employés à partir du système des ressources humaines (RH) de leur organisation Microsoft 365. Cela vous permet d’utiliser des données RH dans les stratégies de gestion des risques internes pour vous aider à détecter les activités de certains utilisateurs qui peuvent poser une menace interne à votre organisation.
ms.openlocfilehash: 64822b8ea5952f4fb6787dfd7832879c2e84c2d4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320954"
---
# <a name="set-up-a-connector-to-import-hr-data"></a>Configurer un connecteur pour importer des données RH

Vous pouvez configurer un connecteur de données dans le Centre de conformité Microsoft 365 pour importer des données de ressources humaines (RH) liées à des événements tels que la merci de l’utilisateur ou un changement dans le niveau de travail d’un utilisateur. Les données RH peuvent ensuite être utilisées par la [solution](insider-risk-management.md) de gestion des risques internes pour générer des indicateurs de risque qui peuvent vous aider à identifier les activités malveillantes possibles ou le vol de données par les utilisateurs au sein de votre organisation.

La configuration d’un connecteur pour les données RH que les stratégies de gestion des risques internes peuvent utiliser pour générer des indicateurs de risque consiste à créer un fichier CSV qui contient les données RH, à créer une application dans Azure Active Directory utilisée pour l’authentification, à créer un connecteur de données RH dans le Centre de conformité Microsoft 365 et exécutez ensuite un script (sur une base programmée) qui inséra les données RH dans les fichiers CSV dans le cloud Microsoft afin qu’il soit disponible pour la solution de gestion des risques internes.

> [!IMPORTANT]
> Une nouvelle version du connecteur RH est désormais disponible en prévisualisation publique. Pour créer un connecteur RH ou importer des données pour le nouveau [](#csv-file-for-employee-profile-data-preview) scénario de profil d’employé pour le scénario de stratégie de santé pour la gestion des risques internes, allez à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365, sélectionnez l’onglet **Connecteurs**, puis cliquez sur Ajouter un connecteur **> RH (** prévisualisation) pour démarrer la mise en place. Les connecteurs RH existants continueront de fonctionner sans interruption.

## <a name="before-you-begin"></a>Avant de commencer

- Déterminez les scénarios rh et les données à importer dans Microsoft 365. Cela vous aidera à déterminer le nombre de fichiers CSV et de connecteurs RH que vous devrez créer, ainsi que la façon de générer et structurer les fichiers CSV. Les données RH que vous importez sont déterminées par les stratégies de gestion des risques internes que vous souhaitez implémenter. Pour plus d’informations, voir l’étape 1.

- Déterminez comment récupérer ou exporter les données à partir du système RH de votre organisation (et régulièrement) et ajoutez-les aux fichiers CSV que vous créez à l’étape 1. Le script que vous exécutez à l’étape 4 charge les données RH des fichiers CSV dans le cloud Microsoft.

- Le rôle d’administrateur du connecteur de données doit être attribué à l’utilisateur qui crée le connecteur RH à l’étape 3. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- L’exemple de script que vous exécutez à l’étape 4 charge vos données RH dans le cloud Microsoft afin qu’elles soient utilisées par la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

- Ce connecteur est disponible dans les environnements Cloud de la communauté du secteur public dans le cloud Microsoft 365 pour le gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP. Pour obtenir des instructions détaillées sur la configuration d’un connecteur RH dans un environnement Cloud de la communauté du secteur public, voir Configurer un connecteur pour importer des données RH dans le gouvernement des [États-Unis](import-hr-data-US-government.md).

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>Étape 1 : Préparer un fichier CSV avec vos données RH

La première étape consiste à créer un fichier CSV qui contient les données RH que le connecteur importe dans Microsoft 365. Ces données seront utilisées par la solution à risque interne pour générer des indicateurs de risque potentiels. Les données des scénarios RH suivants peuvent être importées dans Microsoft 365 :

- Employé. Informations sur les employés qui ont quitté votre organisation.

- Changements de niveau de travail. Informations sur les changements de niveau de travail pour les employés, telles que les promotions et rétrogradations.

- Révisions des performances. Informations sur les performances des employés.

- Plans d’amélioration des performances. Informations sur les plans d’amélioration des performances pour les employés.

- Profil de l’employé (aperçu). Informations générales sur un employé.

Le type de données RH à importer dépend de la stratégie de gestion des risques internes et du modèle de stratégie correspondant que vous souhaitez implémenter. Le tableau suivant indique le type de données RH requis pour chaque modèle de stratégie :

|  Modèle de stratégie |  Type de données RH |
|:------------------------------|:--------------------------------|
| Vol de données par des employés quittant votre organisation | Employé employé|
| Fuites de données générales                             | Non applicable|
| Fuites de données par des utilisateurs prioritaires                   | Non applicable |
| Fuites de données provoquées par un utilisateur mécontent                | Changements de niveau de travail, révisions des performances, plans d’amélioration des performances|
| Violations générales de la stratégie de sécurité             | Non applicable |
| Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise  | Employé employé|
| Violations de la stratégie de sécurité par des utilisateurs prioritaires   | Non applicable|
| Violations de stratégie de sécurité par des utilisateurs mécontents| Changements de niveau de travail, révisions des performances, plans d’amélioration des performances |
| Langage offensant dans les messages électroniques                    | Non applicable |
| Politique de santé| Profil de l’employé |
|||

Pour plus d’informations sur les modèles de stratégie pour la gestion des risques internes, voir [stratégies de gestion des risques internes](insider-risk-management-policies.md#policy-templates).

Pour chaque scénario RH, vous devez fournir les données RH correspondantes dans un ou plusieurs fichiers CSV. Le nombre de fichiers CSV à utiliser pour votre implémentation de la gestion des risques internes est abordé plus loin dans cette section.

Après avoir créé le fichier CSV avec les données RH requises, stockez-le sur l’ordinateur local sur qui vous exécutez le script à l’étape 4. Vous devez également implémenter une stratégie de mise à jour pour vous assurer que le fichier CSV contient toujours les informations les plus récentes afin que les données RH les plus récentes soient téléchargées vers le cloud Microsoft et accessibles à la solution de gestion des risques internes.

> [!IMPORTANT]
> Les noms de colonne décrits dans les sections suivantes ne sont pas des paramètres obligatoires, mais uniquement des exemples. Vous pouvez utiliser n’importe quel nom de colonne dans vos fichiers CSV. Toutefois, les noms de colonne que vous utilisez dans un fichier  CSV doivent être mappés au type de données lorsque vous créez le connecteur RH à l’étape 3. Notez également que les exemples de fichiers CSV des sections suivantes sont illustrés en mode Bloc-notes. Il est beaucoup plus facile d’afficher et de modifier des fichiers CSV dans Microsoft Excel.

Les sections suivantes décrivent les données CSV requises pour chaque scénario RH.

### <a name="csv-file-for-employee-resignation-data"></a>Fichier CSV pour les données d’employé

Voici un exemple de fichier CSV pour les données d’employé.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’employé.

|  Colonne   |   Description |
|:------------|:----------------|
|**EmailAddress**| Spécifie l’adresse de messagerie (UPN) de l’utilisateur licencié.|
| **Dateét** | Spécifie la date à laquelle le contrat de travail de l’utilisateur a été officiellement résilié dans votre organisation. Par exemple, il peut s’agit de la date à laquelle l’utilisateur a donné son avis de départ de votre organisation. Cette date peut être différente de la date du dernier jour de travail de la personne. Utilisez le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, qui est le format de date et d’heure [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **LastWorkingDate** | Spécifie le dernier jour de travail de l’utilisateur licencié. Utilisez le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, qui est le format de date et d’heure [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>Fichier CSV pour les données de modifications de niveau de travail

Voici un exemple de fichier CSV pour les données de modifications de niveau de travail.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 – Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 – Director,Level 60- Sr. Manager
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de modifications de niveau de travail.

|  Colonne | Description |
|:--------- |:------------- |
| **EmailAddress**  | Spécifie l’adresse de messagerie de l’utilisateur (UPN).|
| **EffectiveDate** | Spécifie la date à laquelle le niveau de travail de l’utilisateur a été officiellement modifié. Utilisez le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, qui est le format de date et d’heure [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies sur le changement de niveau de travail. Vous pouvez entrer une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
| **OldLevel**| Spécifie le niveau de travail de l’utilisateur avant qu’il ne soit modifié. Il s’agit d’un paramètre de texte libre qui peut contenir une taxonomie hiérarchique pour votre organisation. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
| **NewLevel**| Spécifie le niveau de travail de l’utilisateur après qu’il a été modifié. Il s’agit d’un paramètre de texte libre qui peut contenir une taxonomie hiérarchique pour votre organisation. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-performance-review-data"></a>Fichier CSV pour les données d’examen des performances

Voici un exemple de fichier CSV pour les données de performances.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’examen des performances.

|  Colonne | Description |
|:----------|:--------------|
| **EmailAddress**  | Spécifie l’adresse de messagerie de l’utilisateur (UPN).|
| **EffectiveDate** | Spécifie la date à laquelle l’utilisateur a été officiellement informé du résultat de son examen des performances. Il peut s’y trouver la date à laquelle le cycle de révision des performances s’est terminé. Utilisez le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, qui est le format de date et d’heure [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies à l’utilisateur pour l’examen des performances. Il s’agit d’un paramètre de texte avec une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
| **Rating**| Spécifie l’évaluation fournie pour l’examen des performances. Il s’agit d’un paramètre de texte qui peut contenir n’importe quel texte de forme libre que votre organisation utilise pour reconnaître l’évaluation. Par exemple, « 3 satisfait les attentes » ou « 2 en dessous de la moyenne ». Il s’agit d’un paramètre de texte avec une limite de 25 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>Fichier CSV pour les données du plan d’amélioration des performances

Voici un exemple de fichier CSV pour les données des données du plan d’amélioration des performances.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’examen des performances.

|  Colonne |  Description |
|:----------|:---------------|
| **EmailAddress**  | Spécifie l’adresse de messagerie de l’utilisateur (UPN).|
| **EffectiveDate** | Spécifie la date à laquelle l’utilisateur a été officiellement informé de son plan d’amélioration des performances. Vous devez utiliser le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, qui est le format de date et d’heure [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies sur le plan d’amélioration des performances. Il s’agit d’un paramètre de texte avec une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV. |
| **Rating**| Spécifie toute évaluation ou toute autre information liée à l’examen des performances. Il s’agit d’un paramètre de texte qui peut contenir n’importe quel texte de formulaire libre que votre organisation utilise pour reconnaître l’évaluation. Par exemple, « 3 satisfait les attentes » ou « 2 en dessous de la moyenne ». Il s’agit d’un paramètre de texte avec une limite de 25 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-employee-profile-data-preview"></a>Fichier CSV pour les données de profil des employés (aperçu)

> [!NOTE]
> La possibilité de créer un connecteur RH pour les données de profil d’employé est en prévisualisation publique. Pour créer un connecteur RH qui prend en charge les données de profil d’employé, rendez-vous sur la page **Connecteurs** de données dans le Centre de conformité Microsoft 365, sélectionnez l’onglet **Connecteurs**,  >  puis cliquez sur Ajouter un **connecteurHR (prévisualisation).** Suivez les étapes pour créer un connecteur à [l’étape 3 : créez le connecteur RH](#step-3-create-the-hr-connector).

Voici un exemple de fichier CSV pour les données des données de profil d’employé.

```text
EmailAddress,UserName,EmployeeFirstName,EmployeeLastName,EmployeeAddLine1,EmployeeAddLine2,EmployeeCity,EmployeeState,EmployeeZipCode,EmployeeDept,EmployeeType,EmployeeRole
jackq@contoso.com,jackq,jack,qualtz,50 Oakland Ave,#206,City,Florida,32104,Orthopaedic,Regular,Nurse
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de profil des employés.

|  Colonne |  Description |
|:----------|:---------------|
| EmailAddress<sup>*</sup>    | Nom d’utilisateur principal (UPN) ou adresse e-mail de l’employé.|
| EmployeeFirstName<sup>*</sup>   | Prénom de l’employé.|
| EmployeeLastName<sup>*</sup>   | Nom de famille de l’employé.|
| EmployeeAddressLine1<sup>*</sup>    | Adresse de rue de l’employé.|
| EmployeeAddressLine2   | Informations d’adresse secondaire, telles que le numéro du domicile, pour l’employé.|
| EmployeeCity | Ville de résidence de l’employé.|
| EmployeeState | État de résidence de l’employé.|
| EmployeeZipCode<sup>*</sup>  | Code postal de résidence de l’employé. |
| EmployeeCountry| Pays de résidence de l’employé.|
| EmployeeDepartment | Service de l’employé dans l’organisation.|
| EmployeeType |Type d’emploi pour l’employé, par exemple Normal, Exempté ou Ordinaire.|
| EmployeeRole |Rôle, désignation ou fonction des employés dans l’organisation.|
|||

> [!NOTE]
> <sup>*</sup> Cette colonne est obligatoire. Si une colonne obligatoire est manquante, le fichier CSV n’est pas validé et les autres données du fichier ne sont pas importées.

Nous vous recommandons de créer un connecteur RH qui importe uniquement les données de profil des employés. Pour ce connecteur, n’oubliez pas d’actualiser fréquemment les données de profil d’employé, de préférence tous les 15 à 20 jours. Les enregistrements de profil des employés sont supprimés s’ils ne sont pas mis à jour au cours des 30 derniers jours.

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>Détermination du nombre de fichiers CSV à utiliser pour les données RH

À l’étape 3, vous pouvez choisir de créer des connecteurs distincts pour chaque type de données RH ou de créer un connecteur unique pour tous les types de données. Vous pouvez utiliser des fichiers CSV distincts qui contiennent des données pour un scénario RH (comme les exemples de fichiers CSV décrits dans les sections précédentes). Vous pouvez également utiliser un seul fichier CSV qui contient des données pour au moins deux scénarios RH. Voici quelques conseils pour vous aider à déterminer le nombre de fichiers CSV à utiliser pour les données RH.

- Si la stratégie de gestion des risques internes que vous souhaitez implémenter nécessite plusieurs types de données RH, envisagez d’utiliser un seul fichier CSV qui contient tous les types de données requis.

- La méthode de génération ou de collecte des données RH peut déterminer le nombre de fichiers CSV. Par exemple, si les différents types de données RH utilisés pour configurer un connecteur RH se trouvent dans un système RH unique dans votre organisation, vous pouvez exporter les données dans un seul fichier CSV. Toutefois, si les données sont distribuées entre différents systèmes RH, il peut être plus facile d’exporter des données vers différents fichiers CSV. Par exemple, les données de l’employé peuvent se trouver dans un système RH différent des données de niveau de travail ou d’examen des performances. Dans ce cas, il peut être plus facile d’avoir des fichiers CSV distincts plutôt que d’avoir à combiner manuellement les données dans un seul fichier CSV. Ainsi, la façon dont vous récupérez ou exportez des données à partir de vos systèmes RH peut déterminer le nombre de fichiers CSV dont vous aurez besoin.

- En règle générale, le nombre de connecteurs RH que vous devez créer est déterminé par les types de données dans un fichier CSV. Par exemple, si un fichier CSV contient tous les types de données requis pour prendre en charge votre implémentation de gestion des risques internes, vous n’avez besoin que d’un connecteur RH. Toutefois, si vous avez deux fichiers CSV distincts qui contiennent chacun un seul type de données, vous devez créer deux connecteurs RH. Une exception à cela est que si vous ajoutez une colonne **HRScenario** à un fichier CSV (voir la section suivante), vous pouvez configurer un connecteur RH unique qui peut traiter différents fichiers CSV.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Configuration d’un fichier CSV unique pour plusieurs types de données RH

Vous pouvez ajouter plusieurs types de données RH à un seul fichier CSV. Cela est utile si la solution de gestion des risques internes que vous implémentez nécessite plusieurs types de données RH ou si les types de données se trouvent dans un système RH unique dans votre organisation. Le fait d’avoir moins de fichiers CSV vous permet toujours d’avoir moins de connecteurs RH à créer et à gérer.

Voici les conditions requises pour configurer un fichier CSV avec plusieurs types de données :

- Vous devez ajouter les colonnes requises (et facultatives si vous les utilisez) pour chaque type de données et le nom de colonne correspondant dans la ligne d’en-tête. Si un type de données ne correspond pas à une colonne, vous pouvez laisser la valeur vide.

- Pour utiliser un fichier CSV avec plusieurs types de données RH, le connecteur RH doit savoir quelles lignes du fichier CSV contiennent quel type de données RH. Pour ce faire, ajoutez une colonne **HRScenario** supplémentaire au fichier CSV. Les valeurs de cette colonne identifient le type de données RH dans chaque ligne. Par exemple, les valeurs qui correspondent aux quatre scénarios \`RH peuvent être : Scénario\`,\`\` Changement du niveau de travail, \`\`Révision des performances, \`Plan\`\` d’amélioration des performances et Profil de l’employé.\`

- Si vous avez plusieurs fichiers CSV qui contiennent une colonne HRScenario**, assurez-vous que chaque fichier utilise le même nom de colonne et les mêmes valeurs qui identifient les scénarios RH spécifiques.

L’exemple suivant montre un fichier CSV qui contient la **colonne HRScenario** . Les valeurs de la colonne HRScenario identifient le type de données dans la ligne correspondante.

```text
HRScenario,EmailAddress,ResignationDate,LastWorkingDate,EffectiveDate,Remarks,Rating,OldLevel,NewLevel
Resignation,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30,,,,
Resignation,pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540,,,,
Job level change,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 61 Sr. Manager, Level 60 Manager
Job level change,pillarp@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 62 Director,Level 60 Sr Manager
Performance review,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2 Below expectations,,
Performance review,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team,,
Performance improvement plan,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2 Below expectations,,
Performance improvement plan,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Multiple conflicts with the team,,
```

> [!NOTE]
> Vous pouvez utiliser n’importe quel nom pour la colonne qui identifie le type de données RH, car vous maprez le nom de la colonne dans votre fichier CSV en tant que colonne qui identifie le type de données RH lorsque vous configurerez le connecteur à l’étape 3. Vous allez également ma cartographier les valeurs utilisées pour la colonne de type de données lors de la mise en place du connecteur.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Ajout de la colonne HRScenario à un fichier CSV qui contient un seul type de données

En fonction des systèmes RH de votre organisation et de la façon dont vous allez exporter les données RH dans un fichier CSV, vous de devez peut-être créer plusieurs fichiers CSV qui contiennent un seul type de données RH. Dans ce cas, vous pouvez toujours créer un connecteur RH unique pour importer des données à partir de différents fichiers CSV. Pour ce faire, il vous suffit d’ajouter une colonne HRScenario au fichier CSV et de spécifier le type de données RH. Vous pouvez ensuite exécuter le script pour chaque fichier CSV, mais utiliser le même ID de travail pour le connecteur. Voir [l’étape 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>Étape 2 : Créer une application dans Azure Active Directory

L’étape suivante consiste à créer et inscrire une nouvelle application dans Azure Active Directory (Azure AD). L’application correspond au connecteur RH que vous créez à l’étape 3. La création de cette application permet Azure AD authentifier le connecteur RH lorsqu’il s’exécute et tente d’accéder à votre organisation. Cette application sera également utilisée pour authentifier le script que vous exécutez à l’étape 4 pour charger vos données RH dans le cloud Microsoft. Lors de la création de cette Azure AD, n’oubliez pas d’enregistrer les informations suivantes. Ces valeurs seront utilisées aux étapes 3 et 4.

- Azure AD’ID d’application (également appelé *ID* d’application ou *ID client*)

- Azure AD secrète de l’application (également appelée *secret client*)

- ID de client (également appelé *ID d’annuaire*)

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, voir [Enregistrer une application](/azure/active-directory/develop/quickstart-register-app) avec le Plateforme d'identités Microsoft.

## <a name="step-3-create-the-hr-connector"></a>Étape 3 : Créer le connecteur RH

L’étape suivante consiste à créer un connecteur RH dans le Centre de conformité Microsoft 365. Après avoir exécuté le script à l’étape 4, le connecteur RH que vous créez inséra les données RH du fichier CSV vers votre organisation Microsoft 365. Avant de créer un connecteur, assurez-vous que vous avez une liste des scénarios RH et les noms de colonne CSV correspondants pour chacun d’eux. Vous devez ma cartographier les données requises pour chaque scénario avec les noms de colonne réels dans votre fichier CSV lors de la configuration du connecteur. Vous pouvez également télécharger un exemple de fichier CSV lors de la configuration du connecteur et l’Assistant vous aidera à maser le nom des colonnes sur les types de données requis.

Une fois cette étape terminée, assurez-vous de copier l’ID de travail généré lors de la création du connecteur. Vous utiliserez l’ID de travail lorsque vous exécuterez le script.

1. Go to the Centre de conformité Microsoft 365, and select <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Data connectors**</a>.

2. Dans la page **Connecteurs de données**, cliquez **sur HR (aperçu).**

3. Dans la page **RESSOURCES HUMAINES (aperçu),** cliquez **sur Ajouter un connecteur**.

4. Dans la page **Configuration de la connexion** , faites ce qui suit, puis cliquez sur **Suivant** :

   1. Tapez ou collez Azure AD’ID d’application pour l’application Azure que vous avez créée à l’étape 2.

   2. Tapez un nom pour le connecteur RH.

5. Dans la page Scénarios RH, sélectionnez un ou plusieurs scénarios RH pour qui vous souhaitez importer des données, puis cliquez sur **Suivant**.

   ![Sélectionnez un ou plusieurs scénarios RH.](../media/HRConnectorScenarios.png)

6. Dans la page de méthode de mappage de fichiers, sélectionnez un type de fichier si nécessaire, puis sélectionnez l’une des options suivantes, puis cliquez sur **Suivant**.

   - **Télécharger un exemple de fichier**. Si vous sélectionnez cette option, cliquez sur **Télécharger exemple** de fichier pour télécharger le fichier CSV que vous avez préparé à l’étape 1. Cette option vous permet de sélectionner rapidement des noms de colonnes dans votre fichier CSV à partir d’une liste de listes listes afin de les ma tôt sélectionnées sur les types de données pour les scénarios RH que vous avez précédemment sélectionnés.

   OR

   - **Fournissez manuellement les détails du mappage**. Si vous sélectionnez cette option, vous devez taper le nom des colonnes dans votre fichier CSV pour les maser aux types de données pour les scénarios RH que vous avez précédemment sélectionnés.

7. Dans la page Détails du mappage de fichiers, faites l’une des choses suivantes, selon que vous avez téléchargé un exemple de fichier CSV et que vous configurez le connecteur pour un scénario RH unique ou pour plusieurs scénarios. Si vous avez chargé un exemple de fichier, vous n’avez pas besoin de taper les noms de colonne. Vous les sélectionnez dans une liste liste.

    - Si vous avez sélectionné un scénario RH unique à l’étape précédente, tapez les noms d’en-tête de colonne (également *appelés paramètres*) à partir du fichier CSV que vous avez créé à l’étape 1 dans chacune des zones appropriées. Les noms de colonne que vous tapez ne sont pas sensibles à la cas, mais assurez-vous d’inclure des espaces si les noms de colonnes dans votre fichier CSV incluent des espaces. Comme indiqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de paramètres dans votre fichier CSV. Par exemple, la capture d’écran suivante montre les noms des paramètres à partir de l’exemple de fichier CSV pour le scénario RH de l’employé, illustré à l’étape 1.

    - Si vous avez sélectionné plusieurs types de données à l’étape ci-dessus, vous devez entrer le nom de colonne d’identificateur qui identifiera le type de données RH dans votre fichier CSV. Après avoir entré le nom de la colonne d’identificateur, tapez la valeur qui identifie ce type de données RH, puis tapez les noms d’en-tête de colonne pour les types de données sélectionnés à partir des fichiers CSV que vous avez créés à l’étape 1 dans chacune des zones appropriées pour chaque type de données sélectionné. Comme indiqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de colonne dans votre fichier CSV.

8. Dans la page **Révision** , examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Une page d’état qui confirme que le connecteur a été créé s’affiche. Cette page contient deux éléments importants que vous devez effectuer à l’étape suivante pour exécuter l’exemple de script pour télécharger vos données RH.

   ![Page de révision avec ID de travail et lien vers github pour obtenir un exemple de script.](../media/HRConnector_Confirmation.png)

   1. **ID de travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez le copier à partir de cette page ou à partir de la page de flyout du connecteur.

   2. **Lien vers l’exemple de script.** Cliquez sur **le lien** ici pour accéder au site GitHub pour accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Gardez cette fenêtre ouverte afin de pouvoir copier le script à l’étape 4. Vous pouvez également réserver un signet à la destination ou copier l’URL afin de pouvoir y accéder à nouveau lorsque vous exécutez le script. Ce lien est également disponible sur la page volante du connecteur.

9. Cliquez sur **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous **l’onglet Connecteurs** .

10. Cliquez sur le connecteur RH que vous avez créé pour afficher la page de présentation, qui contient des propriétés et d’autres informations sur le connecteur.

   ![Page de flyout pour le nouveau connecteur RH.](../media/HRConnectorWizard7.png)

Si ce n’est pas déjà fait, vous pouvez copier les valeurs de **l’ID d’application Azure** et de **l’ID** de travail connecteur. Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page volante (ou le télécharger à l’aide du lien de l’étape suivante).)

Vous pouvez également cliquer sur **Modifier** pour modifier l’ID d’application Azure ou les noms d’en-tête de colonne que vous avez définis sur la page **de mappage de** fichiers.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Étape 4 : Exécuter l’exemple de script pour télécharger vos données RH

La dernière étape de la configuration d’un connecteur RH consiste à exécuter un exemple de script qui chargera les données RH dans le fichier CSV (que vous avez créé à l’étape 1) dans le cloud Microsoft. Plus précisément, le script charge les données vers le connecteur RH. Après avoir exécuté le script, le connecteur RH que vous avez créé à l’étape 3 importe les données RH dans votre organisation Microsoft 365 où elles sont accessibles par d’autres outils de conformité, tels que la solution de gestion des risques internes. Après avoir exécuté le script, envisagez de planifier une tâche pour qu’elle s’exécute automatiquement quotidiennement afin que les données les plus récentes de résiliation d’employé sont chargées dans le cloud Microsoft. Voir [Planifier l’exécuter automatiquement](#optional-step-6-schedule-the-script-to-run-automatically).

1. Accédez à la fenêtre que vous avez laissée ouverte à partir de l’étape précédente pour accéder au site GitHub avec l’exemple de script. Vous pouvez également ouvrir le site avec signet ou utiliser l’URL que vous avez copiée. Vous pouvez également accéder au script [ici](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Cliquez sur **le bouton Brut** pour afficher le script en affichage texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, si nécessaire.

5. Enregistrez le fichier texte en tant que fichier Windows PowerShell script à l’aide d’un suffixe `.ps1`de nom de fichier de ; par exemple, `HRConnector.ps1`. Vous pouvez également utiliser le nom GitHub fichier pour le script, qui est `upload_termination_records.ps1`.

6. Ouvrez une invite de commandes sur votre ordinateur local et allez dans le répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour télécharger les données RH dans le fichier CSV dans le cloud Microsoft . par exemple :

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
    ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations obtenues lors des étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   | Paramètre | Description |
   |:-----|:-----|:-----|
   |`tenantId`|Il s’agit de l’ID de votre Microsoft 365 que vous avez obtenu à l’étape 2. Vous pouvez également obtenir l’ID de locataire de votre organisation dans le panneau **Vue** d’ensemble du centre Azure AD’administration. Il est utilisé pour identifier votre organisation.|
   |`appId` |Il s’agit Azure AD’ID d’application de l’application que vous avez créée Azure AD l’étape 2. Il est utilisé par les Azure AD pour l’authentification lorsque le script tente d’accéder à Microsoft 365 organisation. | 
   |`appSecret`|Il s’agit de Azure AD’application secrète pour l’application que vous avez créée Azure AD l’étape 2. Cette fonction est également utilisée pour l’authentification.|
   |`jobId`|Il s’agit de l’ID de travail pour le connecteur RH que vous avez créé à l’étape 3. Cette fonction permet d’associer les données RH téléchargées vers le cloud Microsoft au connecteur RH.|
   |`filePath`|Il s’agit du chemin d’accès au fichier (stocké sur le même système que le script) que vous avez créé à l’étape 1. Essayez d’éviter les espaces dans le chemin d’accès du fichier . sinon, utilisez des guillemets simples.|
   |||

   Voici un exemple de syntaxe pour le script de connecteur RH utilisant des valeurs réelles pour chaque paramètre :

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Si le téléchargement réussit, le script affiche le message **Télécharger** réussite.

   > [!NOTE]
   > Si vous avez des problèmes lors de l’exécution de la commande précédente [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) en raison des stratégies d’exécution, voir À propos des stratégies d’exécution et [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des instructions sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-hr-connector"></a>Étape 5 : Surveiller le connecteur RH

Après avoir créé le connecteur RH et exécuté le script pour télécharger vos données RH, vous pouvez afficher le connecteur et l’état de chargement dans le Centre de conformité Microsoft 365. Si vous programmez l’exécuter automatiquement sur une base régulière, vous pouvez également afficher l’état actuel après la dernière fois que le script a été exécuté.

1. Go to the Centre de conformité Microsoft 365, and select <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Data connectors**</a>.

2. Cliquez sur **l’onglet Connecteurs** , puis sélectionnez le connecteur RH pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

   ![Page de flyout du connecteur RH avec les propriétés et l’état.](../media/HRConnectorFlyout1.png)

3. Sous **Progression**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données du fichier CSV dans le cloud Microsoft. 

   ![Le fichier journal du connecteur RH affiche les lignes de numéro à partir du fichier CSV qui ont été téléchargées.](../media/HRConnectorLogFile.png)

   Le `RecordsSaved` champ indique le nombre de lignes dans le fichier CSV téléchargé. Par exemple, si le fichier CSV contient quatre lignes, `RecordsSaved` la valeur des champs est 4, si le script a correctement téléchargé toutes les lignes du fichier CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes pour exécuter le script.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécuter automatiquement

Pour vous assurer que les dernières données RH de votre organisation sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécuter automatiquement de manière périodique, par exemple une fois par jour. Vous devez également mettre à jour les données RH dans le fichier CSV selon une planification similaire (si ce n’est pas la même) afin qu’elles contiennent les dernières informations sur les employés qui quittent votre organisation. L’objectif est de télécharger les données RH les plus récentes afin que le connecteur RH puisse les rendre disponibles pour la solution de gestion des risques internes.

Vous pouvez utiliser l’application De planification des tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur Windows **bouton** Démarrer, puis tapez Planification **des tâches**.

2. Cliquez sur **l’application De planification des** tâches pour l’ouvrir.

3. Dans la section **Actions** , cliquez sur **Créer une tâche**.

4. Sous **l’onglet** Général, tapez un nom descriptif pour la tâche programmée . par exemple, **SCRIPT DE CONNECTEUR RH**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité**, faites les actions suivantes :

   1. Déterminez s’il faut exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou l’exécuter lorsque vous êtes connecté ou non.

   1. Assurez-vous que la case **à cocher Exécuter avec les privilèges les plus élevés** est sélectionnée.

6. Sélectionnez **l’onglet Déclencheurs** , cliquez **sur Nouveau**, puis faites les choses suivantes :

   1. Sous **Paramètres**, sélectionnez l’option **Quotidienne**, puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script s’exécute tous les jours à la même heure spécifiée.

   1. Sous **Paramètres avancés**, vérifiez que la case **à** cocher Activée est activée.

   1. Cliquez sur **OK**.

7. Sélectionnez **l’onglet Actions** , cliquez **sur Nouveau**, puis faites les actions suivantes :

   ![Paramètres d’action pour créer une tâche programmée pour le script de connecteur RH.](../media/HRConnectorScheduleTask1.png)

   1. Dans la **liste liste de** listes d’actions, assurez-vous que **démarrer un programme** est sélectionné.

   1. Dans la **zone Programme/script**, cliquez sur **Parcourir**, puis accédez à l’emplacement suivant et sélectionnez-le afin que le chemin d’accès s’affiche dans la zone : `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

   1. Dans la **zone Ajouter des arguments (facultatif),** collez la même commande de script que celle que vous avez l’étape 4. Par exemple, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Dans la **zone Démarrer dans (facultatif),** collez l’emplacement du dossier du script que vous avez écrit à l’étape 4. Par exemple, `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Cliquez **sur OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la **fenêtre Créer une** tâche, cliquez sur **OK** pour enregistrer la tâche programmée. Vous pouvez être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du Programmeur de tâches.

   ![La nouvelle tâche s’affiche dans la bibliothèque du Programmeur de tâches.](../media/HRConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script a été exécuté et la prochaine fois qu’il est programmé pour s’exécuter, s’affiche. Vous pouvez double-cliquer sur la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script a été écrit sur la page volante du connecteur RH correspondant dans le centre de conformité.

## <a name="existing-hr-connectors"></a>Connecteurs RH existants

Le 13 décembre 2021, nous avons publié le scénario de données de profil d’employé pour les connecteurs RH. Si vous avez créé un connecteur RH avant cette date, nous migrerons les instances existantes ou les connecteurs RH de votre organisation afin que vos données RH continuent d’être importées dans le cloud Microsoft. Vous n’avez rien à faire pour maintenir cette fonctionnalité. Vous pouvez continuer à utiliser ces connecteurs sans interruption.

Si vous souhaitez implémenter le scénario de données de profil d’employé, vous créez un connecteur RH et le configurez selon les besoins. Après avoir créé un connecteur RH, exécutez le script à l’aide de l’ID de travail du nouveau connecteur et [](#csv-file-for-employee-profile-data-preview) des fichiers CSV avec les données de profil d’employé décrites précédemment dans cet article.
