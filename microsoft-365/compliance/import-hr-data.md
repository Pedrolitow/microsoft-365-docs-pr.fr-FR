---
title: Configurer un connecteur pour importer des données RH
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données d’employés à partir du système de ressources humaines de leur organisation vers Microsoft 365. Cela vous permet d’utiliser les données RH dans les stratégies de gestion des risques internes pour vous aider à détecter les activités d’utilisateurs spécifiques susceptibles de poser une menace interne à votre organisation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 193b45e50d76f6647d871fd84bda70f9be2b324c
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537273"
---
# <a name="set-up-a-connector-to-import-hr-data"></a>Configurer un connecteur pour importer des données RH

Vous pouvez configurer un connecteur de données dans le portail de conformité Microsoft Purview pour importer des données de ressources humaines liées à des événements tels que la démission d’un utilisateur ou une modification du niveau de travail d’un utilisateur. Les données RH peuvent ensuite être utilisées par la [solution de gestion des risques internes](insider-risk-management.md) pour générer des indicateurs de risque qui peuvent vous aider à identifier les activités malveillantes ou le vol de données possibles par les utilisateurs au sein de votre organisation.

La configuration d’un connecteur pour les données RH que les stratégies de gestion des risques internes peuvent utiliser pour générer des indicateurs de risque consiste à créer un fichier CSV contenant les données RH, à créer une application dans Azure Active Directory utilisée pour l’authentification, à créer un connecteur de données RH dans le portail de conformité, puis à exécuter un script (planifié) qui ingère les données RH dans les fichiers CSV dans le cloud Microsoft afin qu’elles soient disponibles à la solution de gestion des risques internes.

> [!IMPORTANT]
> Une nouvelle version du connecteur RH est désormais disponible pour la préversion publique. Pour créer un connecteur RH ou importer des données pour le [nouveau scénario de profil d’employé](#csv-file-for-employee-profile-data-preview) pour le scénario de stratégie de santé pour la gestion des risques **internes** , accédez à la page Connecteurs de données dans le portail de conformité, sélectionnez l’onglet **Connecteurs** , puis sélectionnez **Ajouter un connecteur > RH (préversion)** pour démarrer la configuration. Les connecteurs RH existants continueront de fonctionner sans interruption.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-begin"></a>Avant de commencer

- Déterminez les scénarios rh et les données à importer dans Microsoft 365. Cela vous aidera à déterminer le nombre de fichiers CSV et de connecteurs RH que vous devez créer, ainsi que la façon de générer et de structurer les fichiers CSV. Les données RH que vous importez sont déterminées par les stratégies de gestion des risques internes que vous souhaitez implémenter. Pour plus d’informations, consultez l’étape 1.

- Déterminez comment récupérer ou exporter les données à partir du système RH de votre organisation (et régulièrement) et ajoutez-les aux fichiers CSV que vous créez à l’étape 1. Le script que vous exécutez à l’étape 4 charge les données RH dans les fichiers CSV dans le cloud Microsoft.

- L’utilisateur qui crée le connecteur RH à l’étape 3 doit disposer du rôle Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- L’exemple de script que vous exécutez à l’étape 4 charge vos données RH dans le cloud Microsoft afin qu’elles puissent être utilisées par la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

- Ce connecteur est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP. Pour obtenir des instructions pas à pas sur la configuration d’un connecteur RH dans un environnement GCC, consultez [Configurer un connecteur pour importer des données RH dans le gouvernement des États-Unis](import-hr-data-US-government.md).

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>Étape 1 : Préparer un fichier CSV avec vos données RH

La première étape consiste à créer un fichier CSV qui contient les données RH que le connecteur va importer dans Microsoft 365. Ces données seront utilisées par la solution de risque interne pour générer des indicateurs de risque potentiels. Les données des scénarios RH suivants peuvent être importées dans Microsoft 365 :

- Démission de l’employé. Informations sur les employés qui ont quitté votre organisation.

- Modifications au niveau du travail. Informations sur les changements de niveau de travail pour les employés, telles que les promotions et rétrogradations.

- Révisions des performances. Informations sur les performances des employés.

- Plans d’amélioration des performances. Informations sur les plans d’amélioration des performances pour les employés.

- Profil d’employé (préversion). Informations générales sur un employé.

Le type de données RH à importer dépend de la stratégie de gestion des risques internes et du modèle de stratégie correspondant que vous souhaitez implémenter. Le tableau suivant indique le type de données RH requis pour chaque modèle de stratégie :

|  Modèle de stratégie |  Type de données RH |
|:------------------------------|:--------------------------------|
| Vol de données par des employés quittant votre organisation | Démissions d’employés|
| Fuites de données générales                             | Non applicable|
| Fuites de données par des utilisateurs prioritaires                   | Non applicable |
| Fuites de données provoquées par un utilisateur mécontent                | Changements au niveau du travail, révisions des performances, plans d’amélioration des performances|
| Violations générales de la stratégie de sécurité             | Non applicable |
| Violations de stratégie de sécurité par des utilisateurs quittant l’entreprise  | Démissions d’employés|
| Violations de la stratégie de sécurité par des utilisateurs prioritaires   | Non applicable|
| Violations de stratégie de sécurité par des utilisateurs mécontents| Changements au niveau du travail, révisions des performances, plans d’amélioration des performances |
| Langage offensant dans les messages électroniques                    | Non applicable |
| Politique de santé| Profil d’employé |
|||

Pour plus d’informations sur les modèles de stratégie pour la gestion des risques internes, consultez stratégies [de gestion des risques internes](insider-risk-management-policies.md#policy-templates).

Pour chaque scénario RH, vous devez fournir les données RH correspondantes dans un ou plusieurs fichiers CSV. Le nombre de fichiers CSV à utiliser pour votre implémentation de la gestion des risques internes est abordé plus loin dans cette section.

Après avoir créé le fichier CSV avec les données RH requises, stockez-le sur l’ordinateur local sur lequel vous exécutez le script à l’étape 4. Vous devez également implémenter une stratégie de mise à jour pour vous assurer que le fichier CSV contient toujours les informations les plus actuelles afin que, quelle que soit l’exécution du script, les données RH les plus actuelles soient chargées dans le cloud Microsoft et accessibles à la solution de gestion des risques internes.

> [!IMPORTANT]
> Les noms de colonnes décrits dans les sections suivantes ne sont pas des paramètres obligatoires, mais seulement des exemples. Vous pouvez utiliser n’importe quel nom de colonne dans vos fichiers CSV. Toutefois, les noms de colonnes que vous utilisez dans un fichier CSV *doivent* être mappés au type de données lorsque vous créez le connecteur RH à l’étape 3. Notez également que les exemples de fichiers CSV des sections suivantes sont affichés en mode Bloc-notes. Il est beaucoup plus facile d’afficher et de modifier des fichiers CSV dans Microsoft Excel.

Les sections suivantes décrivent les données CSV requises pour chaque scénario RH.

### <a name="csv-file-for-employee-resignation-data"></a>Fichier CSV pour les données de démission des employés

Voici un exemple de fichier CSV pour les données de démission des employés.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de démission des employés.

|  Colonne   |   Description |
|:------------|:----------------|
|**EmailAddress**| Spécifie l’adresse e-mail (UPN) de l’utilisateur arrêté.|
| **Résignation** | Spécifie la date à laquelle l’emploi de l’utilisateur a été officiellement résilié dans votre organisation. Par exemple, il peut s’agir de la date à laquelle l’utilisateur a donné son avis de quitter votre organisation. Cette date peut être différente de la date du dernier jour de travail de la personne. Utilisez le format de date et d’heure suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`il s’agit du [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **LastWorkingDate** | Spécifie le dernier jour de travail de l’utilisateur arrêté. Utilisez le format de date et d’heure suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`il s’agit du [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>Le fichier CSV pour le niveau de travail modifie les données

Voici un exemple de fichier CSV pour les données modifiées au niveau du travail.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 - Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 - Director,Level 60- Sr. Manager
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de modification au niveau du travail.

|  Colonne | Description |
|:--------- |:------------- |
| **EmailAddress**  | Spécifie l’adresse e-mail de l’utilisateur (UPN).|
| **EffectiveDate** | Spécifie la date à laquelle le niveau de travail de l’utilisateur a été officiellement modifié. Utilisez le format de date et d’heure suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`il s’agit du [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies sur la modification du niveau du travail. Vous pouvez entrer une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV.|
| **OldLevel**| Spécifie le niveau de travail de l’utilisateur avant sa modification. Il s’agit d’un paramètre de texte libre qui peut contenir une taxonomie hiérarchique pour votre organisation. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV.|
| **NewLevel**| Spécifie le niveau de travail de l’utilisateur après sa modification. Il s’agit d’un paramètre de texte libre qui peut contenir une taxonomie hiérarchique pour votre organisation. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-performance-review-data"></a>Fichier CSV pour les données d’évaluation des performances

Voici un exemple de fichier CSV pour les données de performances.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’évaluation des performances.

|  Colonne | Description |
|:----------|:--------------|
| **EmailAddress**  | Spécifie l’adresse e-mail de l’utilisateur (UPN).|
| **EffectiveDate** | Spécifie la date à laquelle l’utilisateur a été officiellement informé du résultat de son examen des performances. Il peut s’agir de la date à laquelle le cycle de révision des performances s’est terminé. Utilisez le format de date et d’heure suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`il s’agit du [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies à l’utilisateur pour la révision des performances. Il s’agit d’un paramètre de texte avec une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV.|
| **Rating**| Spécifie l’évaluation fournie pour l’évaluation des performances. Il s’agit d’un paramètre de texte qui peut contenir n’importe quel texte de forme libre que votre organisation utilise pour reconnaître l’évaluation. Par exemple, « 3 a répondu aux attentes » ou « 2 en dessous de la moyenne ». Il s’agit d’un paramètre de texte avec une limite de 25 caractères. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>Fichier CSV pour les données du plan d’amélioration des performances

Voici un exemple de fichier CSV pour les données des données du plan d’amélioration des performances.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’évaluation des performances.

|  Colonne |  Description |
|:----------|:---------------|
| **EmailAddress**  | Spécifie l’adresse e-mail de l’utilisateur (UPN).|
| **EffectiveDate** | Spécifie la date à laquelle l’utilisateur a été officiellement informé de son plan d’amélioration des performances. Vous devez utiliser le format de date et d’heure suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies au sujet du plan d’amélioration des performances. Il s’agit d’un paramètre de texte avec une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV. |
| **Rating**| Spécifie une évaluation ou d’autres informations relatives à l’évaluation des performances. Il s’agit d’un paramètre de texte qui peut contenir n’importe quel texte de forme libre utilisé par votre organisation pour reconnaître l’évaluation. Par exemple, « 3 a répondu aux attentes » ou « 2 en dessous de la moyenne ». Il s’agit d’un paramètre de texte avec une limite de 25 caractères. Ce paramètre est facultatif. Vous n’avez pas à l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-employee-profile-data-preview"></a>Fichier CSV pour les données de profil des employés (préversion)

> [!NOTE]
> La possibilité de créer un connecteur RH pour les données de profil des employés est en préversion publique. Pour créer un connecteur RH qui prend en charge les données de profil des employés, accédez à la page **Connecteurs de données** dans le portail de conformité, sélectionnez l’onglet **Connecteurs**, puis **sélectionnez Ajouter un connecteur** > **RH (préversion).** Suivez les étapes pour créer un connecteur à [l’étape 3 : Créer le connecteur RH](#step-3-create-the-hr-connector).

Voici un exemple de fichier CSV pour les données des données de profil d’employé.

```text
EmailAddress,UserName,EmployeeFirstName,EmployeeLastName,EmployeeAddLine1,EmployeeAddLine2,EmployeeCity,EmployeeState,EmployeeZipCode,EmployeeDept,EmployeeType,EmployeeRole
jackq@contoso.com,jackq,jack,qualtz,50 Oakland Ave,#206,City,Florida,32104,Orthopaedic,Regular,Nurse
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de profil des employés.

|  Colonne |  Description |
|:----------|:---------------|
| Emailaddress<sup>*</sup>    | Nom d’utilisateur principal (UPN) ou adresse e-mail de l’employé.|
| EmployeeFirstName<sup>*</sup>   | Prénom de l’employé.|
| EmployeeLastName<sup>*</sup>   | Nom de l’employé.|
| EmployeeAddressLine1<sup>*</sup>    | Adresse postale de l’employé.|
| EmployeeAddressLine2   | Informations d’adresse secondaire, telles que le numéro d’appartement, pour l’employé.|
| EmployeeCity | Ville de résidence de l’employé.|
| EmployeeState | État de résidence de l’employé.|
| EmployeeZipCode<sup>*</sup>  | Code postal de résidence pour l’employé. |
| EmployeeCountry| Pays de résidence de l’employé.|
| EmployeeDepartment | Service de l’employé dans l’organisation.|
| EmployeeType |Type d’emploi pour l’employé, tel que Régulier, Exempt ou Entrepreneur.|
| EmployeeRole |Rôle, désignation ou titre de travail des employés dans l’organisation.|
|||

> [!NOTE]
> <sup>*</sup> Cette colonne est obligatoire. Si une colonne obligatoire est manquante, le fichier CSV n’est pas validé et les autres données du fichier ne sont pas importées.

Nous vous recommandons de créer un connecteur RH qui importe uniquement les données de profil des employés. Pour ce connecteur, veillez à actualiser fréquemment les données de profil des employés, de préférence tous les 15 à 20 jours. Les enregistrements de profil d’employé seront supprimés s’ils ne sont pas mis à jour au cours des 30 derniers jours.

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>Détermination du nombre de fichiers CSV à utiliser pour les données RH

À l’étape 3, vous pouvez choisir de créer des connecteurs distincts pour chaque type de données RH ou vous pouvez choisir de créer un seul connecteur pour tous les types de données. Vous pouvez utiliser des fichiers CSV distincts qui contiennent des données pour un scénario RH (comme les exemples de fichiers CSV décrits dans les sections précédentes). Vous pouvez également utiliser un seul fichier CSV qui contient des données pour deux scénarios RH ou plus. Voici quelques instructions pour vous aider à déterminer le nombre de fichiers CSV à utiliser pour les données RH.

- Si la stratégie de gestion des risques internes que vous souhaitez implémenter nécessite plusieurs types de données RH, envisagez d’utiliser un seul fichier CSV qui contient tous les types de données requis.

- La méthode de génération ou de collecte des données RH peut déterminer le nombre de fichiers CSV. Par exemple, si les différents types de données RH utilisés pour configurer un connecteur RH se trouvent dans un seul système RH de votre organisation, vous pouvez exporter les données vers un seul fichier CSV. Toutefois, si les données sont distribuées entre différents systèmes RH, il peut être plus facile d’exporter des données vers différents fichiers CSV. Par exemple, les données sur les démissions des employés peuvent se trouver dans un autre système rhéographique que les données de niveau travail ou d’évaluation du rendement. Dans ce cas, il peut être plus facile d’avoir des fichiers CSV distincts plutôt que d’avoir à combiner manuellement les données dans un seul fichier CSV. Par conséquent, la façon dont vous récupérez ou exportez des données à partir de vos systèmes RH peut déterminer le nombre de fichiers CSV dont vous aurez besoin.

- En règle générale, le nombre de connecteurs RH que vous devez créer est déterminé par les types de données dans un fichier CSV. Par exemple, si un fichier CSV contient tous les types de données requis pour prendre en charge votre implémentation de la gestion des risques internes, vous n’avez besoin que d’un seul connecteur RH. Toutefois, si vous avez deux fichiers CSV distincts qui contiennent chacun un seul type de données, vous devez créer deux connecteurs RH. Une exception à cela est que si vous ajoutez une colonne **HRScenario** à un fichier CSV (voir la section suivante), vous pouvez configurer un seul connecteur RH qui peut traiter différents fichiers CSV.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Configuration d’un fichier CSV unique pour plusieurs types de données RH

Vous pouvez ajouter plusieurs types de données RH à un seul fichier CSV. Cela est utile si la solution de gestion des risques internes que vous implémentez nécessite plusieurs types de données RH ou si les types de données se trouvent dans un système RH unique de votre organisation. Le fait d’avoir moins de fichiers CSV vous permet toujours d’avoir moins de connecteurs RH à créer et à gérer.

Voici les conditions requises pour configurer un fichier CSV avec plusieurs types de données :

- Vous devez ajouter les colonnes requises (et facultatives si vous les utilisez) pour chaque type de données et le nom de colonne correspondant dans la ligne d’en-tête. Si un type de données ne correspond pas à une colonne, vous pouvez laisser la valeur vide.

- Pour utiliser un fichier CSV avec plusieurs types de données RH, le connecteur RH doit savoir quelles lignes du fichier CSV contiennent le type de données RH. Pour ce faire, ajoutez une colonne **HRScenario** supplémentaire au fichier CSV. Les valeurs de cette colonne identifient le type de données RH dans chaque ligne. Par exemple, les valeurs qui correspondent aux scénarios RH peuvent être Démission, Changement au niveau du travail, \`Examen\` des performances, \`Plan\` d’amélioration des performances et \`Profil\` d’employé.\`\`\`\`

- Si vous avez plusieurs fichiers CSV qui contiennent une colonne HRScenario**, assurez-vous que chaque fichier utilise le même nom de colonne et les mêmes valeurs qui identifient les scénarios RH spécifiques.

L’exemple suivant montre un fichier CSV qui contient la colonne **HRScenario** . Les valeurs de la colonne HRScenario identifient le type de données dans la ligne correspondante. L’exemple ci-dessous couvre quatre scénarios \`RH : démission\`, \`changement au niveau du\` travail, \`examen\` du rendement et \`plan\` d’amélioration du rendement.

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
> Vous pouvez utiliser n’importe quel nom pour la colonne qui identifie le type de données RH, car vous mapperez le nom de la colonne dans votre fichier CSV comme colonne qui identifie le type de données RH lorsque vous configurez le connecteur à l’étape 3. Vous allez également mapper les valeurs utilisées pour la colonne de type de données lorsque vous configurez le connecteur.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Ajout de la colonne HRScenario à un fichier CSV qui contient un seul type de données

En fonction des systèmes RH de votre organisation et de la façon dont vous allez exporter des données RH vers un fichier CSV, vous devrez peut-être créer plusieurs fichiers CSV qui contiennent un seul type de données RH. Dans ce cas, vous pouvez toujours créer un seul connecteur RH pour importer des données à partir de différents fichiers CSV. Pour ce faire, vous devez simplement ajouter une colonne HRScenario au fichier CSV et spécifier le type de données RH. Vous pouvez ensuite exécuter le script pour chaque fichier CSV, mais utiliser le même ID de travail pour le connecteur. Voir [l'étape 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>Étape 2 : Créer une application dans Azure Active Directory

L’étape suivante consiste à créer et à inscrire une application dans Azure Active Directory (Azure AD). L’application correspond au connecteur RH que vous créez à l’étape 3. La création de cette application permet à Azure AD d’authentifier le connecteur RH lorsqu’il s’exécute et tente d’accéder à votre organisation. Cette application sera également utilisée pour authentifier le script que vous exécutez à l’étape 4 pour charger vos données RH dans le cloud Microsoft. Lors de la création de cette application Azure AD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées à l’étape 3 et à l’étape 4.

- ID d’application Azure AD (également appelé *ID d’application* ou *ID client*)

- Secret d’application Azure AD (également appelé *clé secrète client*)

- ID de locataire (également appelé *ID de répertoire*)

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, consultez [Inscrire une application auprès du Plateforme d'identités Microsoft](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-3-create-the-hr-connector"></a>Étape 3 : Créer le connecteur RH

L’étape suivante consiste à créer un connecteur RH dans le portail de conformité. Après avoir exécuté le script à l’étape 4, le connecteur RH que vous créez ingère les données RH du fichier CSV à votre organisation Microsoft 365. Avant de créer un connecteur, veillez à disposer d’une liste des scénarios RH et des noms de colonneS CSV correspondants pour chacun d’eux. Vous devez mapper les données requises pour chaque scénario aux noms de colonnes réels dans votre fichier CSV lors de la configuration du connecteur. Vous pouvez également charger un exemple de fichier CSV lors de la configuration du connecteur et l’Assistant vous aidera à mapper le nom des colonnes aux types de données requis.

Une fois cette étape terminée, veillez à copier l’ID de travail généré lors de la création du connecteur. Vous allez utiliser l’ID de travail lorsque vous exécutez le script.

1. Accédez au portail de conformité, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Connecteurs de données**</a>.

2. Dans la page **Connecteurs de données**, sélectionnez **RH (préversion).**

3. Dans la page **RH (préversion),** **sélectionnez Ajouter un connecteur**.

4. Dans la page **Configurer la connexion** , procédez comme suit, puis sélectionnez **Suivant** :

   1. Tapez ou collez l’ID d’application Azure AD pour l’application Azure que vous avez créée à l’étape 2.

   2. Tapez un nom pour le connecteur RH.

5. Dans la page Scénarios RH, sélectionnez un ou plusieurs scénarios RH pour lesquels vous souhaitez importer des données, puis sélectionnez **Suivant**.

   ![Sélectionnez un ou plusieurs scénarios RH.](../media/HRConnectorScenarios.png)

6. Dans la page de méthode de mappage de fichiers, sélectionnez un type de fichier si nécessaire, puis sélectionnez l’une des options suivantes, puis **sélectionnez Suivant**.

   - **Chargez un exemple de fichier**. Si vous sélectionnez cette option, **sélectionnez Charger l’exemple de fichier** pour charger le fichier CSV que vous avez préparé à l’étape 1. Cette option vous permet de sélectionner rapidement des noms de colonnes dans votre fichier CSV dans une liste déroulante pour les mapper aux types de données pour les scénarios RH que vous avez sélectionnés précédemment.

   OR

   - **Fournissez manuellement les détails du mappage**. Si vous sélectionnez cette option, vous devez taper le nom des colonnes de votre fichier CSV pour les mapper aux types de données pour les scénarios RH que vous avez sélectionnés précédemment.

7. Dans la page de détails du mappage de fichiers, effectuez l’une des opérations suivantes, selon que vous avez chargé un exemple de fichier CSV et si vous configurez le connecteur pour un scénario RH unique ou pour plusieurs scénarios. Si vous avez chargé un exemple de fichier, vous n’êtes pas obligé de taper les noms des colonnes. Vous les sélectionnez dans une liste déroulante.

    - Si vous avez sélectionné un scénario RH unique à l’étape précédente, tapez les noms d’en-tête de colonne (également *appelés paramètres*) à partir du fichier CSV que vous avez créé à l’étape 1 dans chacune des zones appropriées. Les noms de colonnes que vous tapez ne respectent pas la casse, mais veillez à inclure des espaces si les noms de colonnes de votre fichier CSV incluent des espaces. Comme expliqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de paramètres dans votre fichier CSV. Par exemple, la capture d’écran suivante montre les noms de paramètres de l’exemple de fichier CSV pour le scénario RH de démission de l’employé illustré à l’étape 1.

    - Si vous avez sélectionné plusieurs types de données à l’étape ci-dessus, vous devez entrer le nom de colonne d’identificateur qui identifie le type de données RH dans votre fichier CSV. Après avoir entré le nom de colonne d’identificateur, tapez la valeur qui identifie ce type de données RH, puis tapez les noms d’en-tête de colonne pour les types de données sélectionnés à partir du ou des fichiers CSV que vous avez créés à l’étape 1 dans chacune des zones appropriées pour chaque type de données sélectionné. Comme expliqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de colonnes dans votre fichier CSV.

8. Dans la page **Révision** , passez en revue vos paramètres, puis sélectionnez **Terminer** pour créer le connecteur.

   Une page d’état s’affiche pour confirmer la création du connecteur. Cette page contient deux éléments importants que vous devez effectuer à l’étape suivante pour exécuter l’exemple de script pour charger vos données RH.

   ![Consultez la page avec l’ID de travail et le lien vers github pour obtenir un exemple de script.](../media/HRConnector_Confirmation.png)

   1. **ID du travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez la copier à partir de cette page ou de la page de menu volant du connecteur.

   2. **Lien vers un exemple de script.** Sélectionnez le lien **ici** pour accéder au site GitHub pour accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Laissez cette fenêtre ouverte pour pouvoir copier le script à l’étape 4. Vous pouvez également marquer la destination ou copier l’URL pour pouvoir y accéder à nouveau lorsque vous exécutez le script. Ce lien est également disponible sur la page de menu volant du connecteur.

9. Sélectionnez **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous l’onglet **Connecteurs** .

10. Sélectionnez le connecteur RH que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

   ![Page de menu volant pour le nouveau connecteur RH.](../media/HRConnectorWizard7.png)

Si vous ne l’avez pas déjà fait, vous pouvez copier les valeurs de **l’ID de Azure App** et de **l’ID de travail du connecteur**. Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page de menu volant (ou le télécharger à l’aide du lien à l’étape suivante).)

Vous pouvez également sélectionner **Modifier** pour modifier l’ID Azure App ou les noms d’en-tête de colonne que vous avez définis sur la page **de mappage de fichiers**.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Étape 4 : Exécuter l’exemple de script pour charger vos données RH

La dernière étape de la configuration d’un connecteur RH consiste à exécuter un exemple de script qui charge les données RH dans le fichier CSV (que vous avez créé à l’étape 1) dans le cloud Microsoft. Plus précisément, le script charge les données dans le connecteur RH. Après avoir exécuté le script, le connecteur RH que vous avez créé à l’étape 3 importe les données RH dans votre organisation Microsoft 365, où elles sont accessibles par d’autres outils de conformité, tels que la solution de gestion des risques Insider. Après avoir exécuté le script, envisagez de planifier une tâche pour l’exécuter automatiquement tous les jours afin que les données d’arrêt des employés les plus actuelles soient chargées dans le cloud Microsoft. Consultez [Planifier l’exécution automatique du script](#optional-step-6-schedule-the-script-to-run-automatically).

1. Accédez à la fenêtre que vous avez laissée ouverte à l’étape précédente pour accéder au site GitHub avec l’exemple de script. Vous pouvez également ouvrir le site avec signet ou utiliser l’URL que vous avez copiée. Vous pouvez également accéder au script [ici](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Sélectionnez le bouton **Brut** pour afficher le script en mode texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Si nécessaire, modifiez l’exemple de script pour votre organisation.

5. Enregistrez le fichier texte en tant que fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de `.ps1`; par exemple, `HRConnector.ps1`. Vous pouvez également utiliser le nom de fichier GitHub pour le script, qui est `upload_termination_records.ps1`.

6. Ouvrez une invite de commandes sur votre ordinateur local et accédez au répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour charger les données RH dans le fichier CSV dans le cloud Microsoft ; par exemple :

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
    ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   | Paramètre | Description |
   |:-----|:-----|:-----|
   |`tenantId`|Il s’agit de l’ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 2. Vous pouvez également obtenir l’ID de locataire de votre organisation dans le panneau **Vue d’ensemble** du Centre d’administration Azure AD. Cela permet d’identifier votre organisation.|
   |`appId` |Il s’agit de l’ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 2. Azure AD l’utilise pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365. | 
   |`appSecret`|Il s’agit du secret d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 2. Cela est également utilisé pour l’authentification.|
   |`jobId`|Il s’agit de l’ID de travail du connecteur RH que vous avez créé à l’étape 3. Cela permet d’associer les données RH chargées dans le cloud Microsoft au connecteur RH.|
   |`filePath`|Il s’agit du chemin d’accès au fichier (stocké sur le même système que le script) que vous avez créé à l’étape 1. Essayez d’éviter les espaces dans le chemin d’accès au fichier ; sinon, utilisez des guillemets simples.|
   |||

   Voici un exemple de syntaxe pour le script de connecteur RH utilisant des valeurs réelles pour chaque paramètre :

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Si le chargement réussit, le script affiche le message **De réussite** du chargement.

   > [!NOTE]
   > Si vous rencontrez des problèmes lors de l’exécution de la commande précédente en raison de stratégies d’exécution, consultez [À propos des stratégies d’exécution](/powershell/module/microsoft.powershell.core/about/about_execution_policies) et [de Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des conseils sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-hr-connector"></a>Étape 5 : Surveiller le connecteur RH

Après avoir créé le connecteur RH et exécuté le script pour charger vos données RH, vous pouvez afficher le connecteur et charger l’état dans le portail de conformité. Si vous planifiez l’exécution automatique du script régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez au portail de conformité, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Connecteurs de données**</a>.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur RH pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

   ![Page de menu volant du connecteur RH avec les propriétés et l’état.](../media/HRConnectorFlyout1.png)

3. Sous **Progression**, **sélectionnez** le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque exécution du script et le chargement des données du fichier CSV dans le cloud Microsoft. 

   ![Le fichier journal du connecteur RH affiche les lignes numériques du fichier CSV qui ont été chargées.](../media/HRConnectorLogFile.png)

   Le `RecordsSaved` champ indique le nombre de lignes dans le fichier CSV chargé. Par exemple, si le fichier CSV contient quatre lignes, la valeur des `RecordsSaved` champs est 4, si le script a correctement chargé toutes les lignes du fichier CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes pour exécuter le script.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécution automatique du script

Pour vous assurer que les dernières données RH de votre organisation sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécution automatique du script de façon périodique, par exemple une fois par jour. Cela nécessite également que vous mettiez à jour les données RH dans le fichier CSV selon une planification similaire (si ce n’est pas la même) afin qu’elles contiennent les informations les plus récentes sur les employés qui quittent votre organisation. L’objectif est de charger les données RH les plus actuelles afin que le connecteur RH puisse les rendre disponibles pour la solution de gestion des risques internes.

Vous pouvez utiliser l’application Planificateur de tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, sélectionnez le bouton Démarrer de Windows, puis **tapez** **Planificateur de tâches**.

2. Sélectionnez l’application **Du planificateur de tâches** pour l’ouvrir.

3. Dans la section **Actions** , sélectionnez **Créer une tâche**.

4. Sous l’onglet **Général** , tapez un nom descriptif pour la tâche planifiée ; par exemple, **script du connecteur RH**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité**, procédez comme suit :

   1. Déterminez si vous devez exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou si vous l’exécutez lorsque vous êtes connecté ou non.

   1. Vérifiez que la case à cocher **Exécuter avec les privilèges les plus élevés** est cochée.

6. Sélectionnez l’onglet Déclencheurs, sélectionnez **Nouveau**, puis effectuez les **opérations suivantes** :

   1. Sous **Paramètres**, sélectionnez l’option **Quotidienne** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script s’exécute tous les jours à la même heure spécifiée.

   1. Sous **Paramètres avancés**, vérifiez que la case à cocher **Activé** est cochée.

   1. Sélectionnez **OK**.

7. Sélectionnez l’onglet **Actions** , sélectionnez **Nouveau**, puis effectuez les opérations suivantes :

   ![Paramètres d’action pour créer une tâche planifiée pour le script du connecteur RH.](../media/HRConnectorScheduleTask1.png)

   1. Dans la liste déroulante **Action** , vérifiez que **l’option Démarrer un programme** est sélectionnée.

   1. Dans la zone **Programme/script** , **sélectionnez Parcourir, accédez** à l’emplacement suivant et sélectionnez-le pour que le chemin d’accès s’affiche dans la zone : `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. Dans la zone **Ajouter des arguments (facultatif),** collez la commande de script que vous avez exécutée à l’étape 4. Par exemple, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Dans la zone **Démarrer (facultatif),** collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple : `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Sélectionnez **OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **Créer une tâche** , sélectionnez **Ok** pour enregistrer la tâche planifiée. Vous pouvez être invité à entrer les informations d’identification de votre compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche s’affiche dans la bibliothèque du planificateur de tâches.](../media/HRConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script s’est exécuté et la prochaine fois qu’il est planifié pour s’exécuter s’affiche. Vous pouvez double-sélectionner la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script s’est exécuté sur la page de menu volant du connecteur RH correspondant dans le centre de conformité.

## <a name="optional-step-7-upload-data-using-power-automate-templates"></a>(Facultatif) Étape 7 : Charger des données à l’aide de modèles Power Automate

Vous pouvez charger des données RH à l’aide de modèles Power Automate et définir des déclencheurs. Par exemple, vous pouvez configurer un modèle Power Automate pour qu’il se déclenche lorsque de nouveaux fichiers de connecteur RH sont disponibles dans les emplacements SharePoint ou OneDrive. Vous pouvez également simplifier ce processus en stockant des informations confidentielles telles que le secret d’application Azure AD (créé à **l’étape 2**) dans Azure Key Vault et en l’utilisant avec Power Automate pour l’authentification.

Effectuez les étapes suivantes pour charger automatiquement les données RH lorsque de nouveaux fichiers sont disponibles sur OneDrive Entreprise :

1.  Téléchargez le package *ImportHRDataforIRM.zip* à partir du [site GitHub](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/ImportHRDataforIRM.zip).
2. Dans [Power Automate](https://make.preview.powerautomate.com), accédez à **Mes flux**.
3.  Sélectionnez **Importer** et chargez le package *ImportHRDataforIRM.zip* .
4.  Une fois le package chargé, mettez à jour le contenu (nom & OneDrive Entreprise connexion), puis sélectionnez **Importer**.

    ![Importation de flux Power Automate.](../media/hr-connector-pa-import-flow.png)

5.  Sélectionnez **Ouvrir le flux** et mettez à jour les paramètres. Le tableau suivant décrit les paramètres à utiliser dans ce flux Power Automate et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

    |**Paramètre**|**Description**|
    |:------------|:--------------|
    | ID de l’application | Il s’agit de l’ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à **l’étape 2**. Azure AD l’utilise pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365. |
    | Secret de l’application | Il s’agit du secret d’application Azure AD pour l’application que vous avez créée dans Azure AD à **l’étape 2**. Utilisé pour l’authentification. |
    | Emplacement du fichier | Il s’agit de l’emplacement OneDrive Entreprise où Power Automate surveille les activités « nouveau fichier créé » pour déclencher ce flux.|
    | N° du travail | Identificateur du connecteur RH créé à **l’étape 3**. Cela permet d’associer les données RH chargées dans le cloud Microsoft au connecteur RH. |
    | ID client | Identificateur de votre organisation Microsoft 365 obtenu à **l’étape 2**. Vous pouvez également obtenir l’ID de locataire de votre organisation dans le panneau **Vue d’ensemble** du Centre d’administration Azure AD. Cela permet d’identifier votre organisation. |
    | URI | Vérifiez que la valeur de ce paramètre est *https://webhook.ingestion.office.com/api/signals* |

    ![Flux Power Automate.](../media/hr-connector-pa-flow.png)

6.  Sélectionnez **Enregistrer**.
7.  Accédez à **la vue d’ensemble de Flow** , puis **sélectionnez Activer**.

    ![Activez le flux Power Automate.](../media/hr-connector-pa-turn-on.png)

8.  Testez le flux manuellement en chargeant un nouveau fichier dans votre dossier OneDrive Entreprise et vérifiez qu’il s’est exécuté correctement. Cette opération peut prendre quelques minutes après le chargement avant le déclenchement du flux.

    ![Test de flux Power Automate.](../media/hr-connector-pa-test.png)

9.  Vous pouvez maintenant surveiller le connecteur RH comme décrit à **l’étape 5**.

Si nécessaire, vous pouvez mettre à jour le flux pour créer des déclencheurs en fonction de la disponibilité des fichiers et des événements de modification sur SharePoint et d’autres sources de données prises en charge par Power Automate Flows.

## <a name="existing-hr-connectors"></a>Connecteurs RH existants

Le 13 décembre 2021, nous avons publié le scénario de données de profil des employés pour les connecteurs RH. Si vous avez créé un connecteur RH avant cette date, nous allons migrer les instances existantes ou les connecteurs RH de votre organisation afin que vos données RH continuent d’être importées dans le cloud Microsoft. Vous n’avez rien à faire pour maintenir cette fonctionnalité. Vous pouvez continuer à utiliser ces connecteurs sans interruption.

Si vous souhaitez implémenter le scénario de données de profil d’employé, vous créez un connecteur RH et le configurez en fonction des besoins. Après avoir créé un connecteur RH, exécutez le script à l’aide de l’ID de travail du nouveau connecteur et des fichiers CSV avec les [données de profil des employés](#csv-file-for-employee-profile-data-preview) décrites précédemment dans cet article.
