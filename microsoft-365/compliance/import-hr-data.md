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
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur de données pour importer les données des employés depuis le système des ressources humaines (RH) de leur organisation vers Microsoft 365. Cela vous permet d’utiliser des données RH dans des stratégies de gestion des risques initiées pour vous aider à détecter les activités d’utilisateurs spécifiques susceptibles de constituer une menace interne pour votre organisation.
ms.openlocfilehash: 49589d2e5a6a716a2e224aa28b73bd14f9048d0b
ms.sourcegitcommit: 195172dd836e8a793e8e0c2db3323b7391bc51ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "47255767"
---
# <a name="set-up-a-connector-to-import-hr-data-preview"></a>Configurer un connecteur pour importer des données RH (aperçu)

Vous pouvez configurer un connecteur de données dans le centre de conformité Microsoft 365 afin d’importer des données de ressources humaines (RH) liées à des événements tels que la démission d’un utilisateur ou un changement de niveau de travail d’un utilisateur. Ces données RH peuvent ensuite être utilisées par la [solution de gestion des risques inSided](insider-risk-management.md) pour générer des indicateurs de risque qui peuvent vous aider à identifier les activités malveillantes potentielles ou les vols de données par les utilisateurs au sein de votre organisation.

Configuration d’un connecteur pour les données RH que les stratégies de gestion des risques internes peuvent utiliser pour générer des indicateurs de risque consistent en la création d’un fichier CSV contenant les données RH. création d’une application dans Azure Active Directory utilisée pour l’authentification, la création d’un connecteur de données RH dans le centre de conformité Microsoft 365, puis l’exécution d’un script (planifié de manière planifiée) qui informe les données RH dans des fichiers CSV vers le Cloud Microsoft afin qu’elle soit disponible pour les Insiders solution de gestion des risques.

## <a name="before-you-begin"></a>Avant de commencer

- Déterminer les scénarios et les données RH à importer vers Microsoft 365. Cela vous permettra de déterminer le nombre de fichiers CSV et de connecteurs RH à créer, ainsi que la façon de générer et de structurer les fichiers CSV. Les données RH que vous importez sont déterminées par les stratégies de gestion des risques Insider que vous souhaitez mettre en œuvre. Pour plus d’informations, reportez-vous à l’étape 1.

- Déterminez comment récupérer ou exporter les données à partir du système RH de votre organisation (et de manière régulière) et les ajouter aux fichiers CSV que vous créez à l’étape 1. Le script que vous exécutez à l’étape 4 télécharge les données RH dans les fichiers CSV vers le Cloud Microsoft.

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de votre organisation. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général Microsoft 365, puis acceptez la demande. Vous devez effectuer cette étape avant de pouvoir créer le connecteur RH à l’étape 3.

- L’utilisateur qui crée le connecteur RH à l’étape 3 doit se voir attribuer le rôle importation/exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

- L’exemple de script que vous exécutez à l’étape 4 télécharge vos données RH dans le Cloud Microsoft afin qu’elles puissent être utilisées par la solution de gestion des risques Insiders. Cet exemple de script n’est pas pris en charge dans les services ou programmes de support standard Microsoft. L’exemple de script est fourni en l’État sans aucune garantie. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. L’ensemble des risques liés à l’utilisation ou aux performances de l’exemple de script et de la documentation reste avec vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>Étape 1 : préparer un fichier CSV avec vos données RH

La première étape consiste à créer un fichier CSV qui contient les données RH importées par le connecteur vers Microsoft 365. Ces données seront utilisées par la solution Risk Insider pour générer des indicateurs de risque potentiels. Les données pour les scénarios de RH suivants peuvent être importées dans Microsoft 365 :

- Retrait d’un employé. Informations sur les utilisateurs qui ont quitté votre organisation.

- Modifications de niveau de travail. Informations sur les modifications de niveau de travail pour les utilisateurs, telles que les promotions et les rétrogradations.

- Analyse des performances. Informations sur les performances de l’utilisateur.

- Plans d’amélioration des performances. Informations sur les plans d’amélioration des performances pour les utilisateurs.

Le type de données RH à importer dépend de la stratégie de gestion des risques inSided et du modèle de stratégie correspondant que vous souhaitez mettre en œuvre. Le tableau suivant indique le type de données RH requis pour chaque modèle de stratégie :

| **Modèle de stratégie**| **Type de données RH**|
|:-----------------------------------------------|:---------------------------------------------------------------------|
| Vol de données en faisant part des utilisateurs                   | Resignature d’employé                                                 |
| Fuites de données générales                              | Non applicable                                                        |
| Fuites de données par les utilisateurs prioritaires                    | Non applicable                                                        |
| Fuites de données par les utilisateurs mécontents                 | Modifications au niveau des tâches, analyses des performances, plans d’amélioration des performances |
| Violations de stratégie de sécurité générale              | Non applicable                                                        |
| Violations de stratégie de sécurité en faisant départion des utilisateurs   | Resignature d’employé                                                 |
| Violations de stratégie de sécurité par utilisateurs prioritaires    | Non applicable                                                        |
| Violations de stratégie de sécurité par des utilisateurs mécontents | Modifications au niveau des tâches, analyses des performances, plans d’amélioration des performances |
| Langage offensant dans les messages électroniques                     | Non applicable                                                        |

Pour plus d’informations sur les modèles de stratégie pour la gestion des risques initiés, consultez la rubrique [stratégies de gestion des risques internes](insider-risk-management-policies.md#policy-templates).

Pour chaque scénario de RH, vous devrez fournir les données RH correspondantes dans un ou plusieurs fichiers CSV. Le nombre de fichiers CSV à utiliser pour votre implémentation de gestion des risques inSided est abordé plus loin dans cette section.

Après avoir créé le fichier CSV avec les données RH requises, stockez-le sur l’ordinateur local sur lequel vous exécutez le script à l’étape 4. Vous devez également implémenter une stratégie de mise à jour pour vous assurer que le fichier CSV contient toujours les informations les plus récentes afin que ce que vous exécutez le script, les données RH les plus récentes soient téléchargées vers le Cloud Microsoft et accessibles à la solution de gestion des risques Insiders.

> [!IMPORTANT]
> Les noms de colonne décrits dans les sections suivantes ne sont pas des paramètres obligatoires, mais uniquement des exemples. Vous pouvez utiliser n’importe quel nom de colonne dans vos fichiers CSV. Toutefois, les noms de colonne que vous utilisez dans un fichier CSV *doivent* être mappés sur le type de données lorsque vous créez le connecteur RH à l’étape 3. Notez également que les exemples de fichiers CSV dans les sections suivantes sont affichés dans le mode bloc-notes. Il est beaucoup plus facile d’afficher et de modifier les fichiers CSV dans Microsoft Excel.

Les sections suivantes décrivent les données CSV requises pour chaque scénario RH.

### <a name="csv-file-for-employee-resignation-data"></a>Fichier CSV pour les données de démission d’un employé

Voici un exemple de fichier CSV pour les données de démission d’un employé.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de démission d’un employé.

| **Colonne**  |  **Description**|
|:------------|:----------------|
|**EmailAddress**| Spécifie l’adresse de messagerie (UPN) de l’utilisateur terminé.|
| **ResignationDate** | Indique la date à laquelle l’emploi de l’utilisateur a été officiellement terminé au sein de votre organisation. Par exemple, il peut s’agir de la date à laquelle l’utilisateur a donné une notification sur la fermeture de votre organisation. Cette date peut être différente de la date du dernier jour de travail de la personne. Vous devez utiliser le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **LastWorkingDate** | Spécifie le dernier jour de travail de l’utilisateur terminé. Vous devez utiliser le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>Fichier CSV pour les données de modifications de niveau de travail

Voici un exemple de fichier CSV pour les données de modifications de niveau de travail.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 – Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 – Director,Level 60- Sr. Manager
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données de modifications de niveau de travail.

| **Colonne**|**Description**|
|:--------- |:------------- |
| **EmailAddress**  | Spécifie l’adresse de messagerie de l’utilisateur (UPN).|
| **EffectiveDate** | Indique la date à laquelle le niveau de travail de l’utilisateur a été officiellement modifié. Vous devez utiliser le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies sur la modification du niveau de travail. Il s’agit d’un paramètre de texte d’une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
| **OldLevel**| Spécifie le niveau de travail de l’utilisateur avant sa modification. Il s’agit d’un paramètre de texte libre pouvant contenir une taxonomie hiérarchique pour votre organisation. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
| **NewLevel**| Spécifie le niveau de travail de l’utilisateur une fois qu’il a été modifié. Il s’agit d’un paramètre de texte libre pouvant contenir une taxonomie hiérarchique pour votre organisation. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-performance-review-data"></a>Fichier CSV pour les données d’analyse des performances

Voici un exemple de fichier CSV pour les données de performances.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’analyse des performances.

| **Colonne**|**Description**|
|:----------|:--------------|
| **EmailAddress**  | Spécifie l’adresse de messagerie de l’utilisateur (UPN).|
| **EffectiveDate** | Indique la date à laquelle l’utilisateur a été officiellement informé du résultat de son examen des performances. Il peut s’agir de la date à laquelle le cycle de révision des performances est terminé. Vous devez utiliser le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies à l’utilisateur pour l’analyse des performances. Il s’agit d’un paramètre de texte d’une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
| **Rating**| Spécifie l’évaluation fournie pour l’analyse des performances. Il s’agit d’un paramètre de type texte qui peut contenir n’importe quel texte libre que votre organisation utilise pour reconnaître l’évaluation. Par exemple, « 3 Attentes satisfaites » ou « 2 au-dessous de la moyenne ». Il s’agit d’un paramètre de texte d’une limite de 25 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>Fichier CSV pour les données du plan d’amélioration des performances

Voici un exemple de fichier CSV pour les données des données du plan d’amélioration des performances.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

Le tableau suivant décrit chaque colonne du fichier CSV pour les données d’analyse des performances.

| **Colonne**| **Description**|
|:----------|:---------------|
| **EmailAddress**  | Spécifie l’adresse de messagerie de l’utilisateur (UPN).|
| **EffectiveDate** | Indique la date à laquelle l’utilisateur a été officiellement informé de son plan d’amélioration des performances. Vous devez utiliser le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Remarques**| Spécifie les remarques que l’évaluateur a fournies sur le plan d’amélioration des performances. Il s’agit d’un paramètre de texte d’une limite de 200 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV. |
| **Rating**| Indique toute évaluation ou toute autre information relative à l’analyse des performances. plan d’amélioration des performances. Il s’agit d’un paramètre de type texte qui peut contenir n’importe quel texte de formulaire libre que votre organisation utilise pour reconnaître l’évaluation. Par exemple, « 3 Attentes satisfaites » ou « 2 au-dessous de la moyenne ». Il s’agit d’un paramètre de texte avec une limite de 25 caractères. Ce paramètre est facultatif. Vous n’avez pas besoin de l’inclure dans le fichier CSV.|
|||

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>Détermination du nombre de fichiers CSV à utiliser pour les données RH

À l’étape 3, vous pouvez choisir de créer des connecteurs distincts pour chaque type de données RH ou vous pouvez choisir de créer un connecteur unique pour tous les types de données. Vous pouvez utiliser des fichiers CSV distincts qui contiennent des données pour un scénario de RH (comme les exemples de fichiers CSV décrits dans les sections précédentes). Vous pouvez également utiliser un seul fichier CSV contenant des données pour au moins deux scénarios de RH. Voici quelques conseils pour vous aider à déterminer le nombre de fichiers CSV à utiliser pour les données RH.

- Si la stratégie de gestion des risques initiaux que vous souhaitez implémenter nécessite plusieurs types de données RH, envisagez l’utilisation d’un fichier CSV unique qui contient tous les types de données requis.

- La méthode de génération ou de collecte des données RH peut déterminer le nombre de fichiers CSV. Par exemple, si les différents types de données RH utilisés pour configurer un connecteur RH se trouvent dans un seul système DRH de votre organisation, vous pouvez peut-être exporter les données dans un seul fichier CSV. Toutefois, si les données sont réparties sur différents systèmes RH, il peut être plus facile d’exporter des données dans différents fichiers CSV. Par exemple, les données de démission d’un employé peuvent se trouver dans un système de RH différent du niveau de travail ou des données d’analyse des performances. Dans ce cas, il peut être plus facile de disposer de fichiers CSV distincts au lieu de devoir combiner manuellement les données dans un seul fichier CSV. Par conséquent, la façon dont vous récupérez ou exportez des données à partir de vos systèmes RH peut déterminer le nombre de fichiers CSV dont vous aurez besoin.

- En règle générale, le nombre de connecteurs RH que vous devrez créer est déterminé par les types de données dans un fichier CSV. Par exemple, si un fichier CSV contient tous les types de données nécessaires à la prise en charge de votre implémentation de gestion des risques Insiders, vous n’avez besoin que d’un seul connecteur RH. Toutefois, si vous avez deux fichiers CSV distincts qui contiennent chacun un seul type de données, vous devez créer deux connecteurs RH. En d’autres exceptions, si vous ajoutez une colonne **HRScenario** à un fichier CSV (voir la section suivante), vous pouvez configurer un connecteur HR unique pouvant traiter différents fichiers CSV.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Configuration d’un fichier CSV unique pour plusieurs types de données RH

Vous pouvez ajouter plusieurs types de données RH à un seul fichier CSV. Ceci est utile si la solution de gestion des risques Insider que vous implémentez nécessite plusieurs types de données RH ou si les types de données se trouvent dans un seul système DRH de votre organisation. Le fait d’avoir moins de fichiers CSV vous permet toujours d’avoir moins de connecteurs RH à créer et à gérer.

Voici les conditions requises pour la configuration d’un fichier CSV avec plusieurs types de données :

- Vous devez ajouter les colonnes requises (et facultatives si vous les utilisez) pour chaque type de données et le nom de colonne correspondant dans la ligne d’en-tête. Si un type de données ne correspond pas à une colonne, vous pouvez laisser la valeur vide.

- Pour utiliser un fichier CSV avec plusieurs types de données RH, le connecteur RH doit savoir quelles lignes du fichier CSV contiennent les données RH de type. Pour ce faire, vous ajoutez une colonne **HRScenario** supplémentaire dans le fichier CSV. Les valeurs de cette colonne identifient le type de données RH de chaque ligne. Par exemple, les valeurs qui correspondent aux quatre scénarios de RH peuvent être déconseillées \` \` , \` modification du niveau du travail \` , examen des \` performances \` et plan d' \` amélioration des performances \` .

- Si vous avez plusieurs fichiers CSV qui contiennent une colonne HRScenario * *, assurez-vous que chaque fichier utilise le même nom de colonne et les mêmes valeurs qui identifient les scénarios de RH spécifiques.

L’exemple suivant montre un fichier CSV qui contient la colonne **HRScenario** . Les valeurs de la colonne HRScenario identifient le type de données dans la ligne correspondante.

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
> Vous pouvez utiliser n’importe quel nom pour la colonne qui identifie le type de données RH, car vous mapperez le nom de la colonne dans votre fichier CSV en tant que colonne qui identifie le type de données RH lorsque vous configurez le connecteur à l’étape 3. Vous mapperez également les valeurs utilisées pour la colonne type de données lorsque vous configurez le connecteur.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Ajout de la colonne HRScenario à un fichier CSV qui contient un seul type de données

En fonction des systèmes RH de votre organisation et de la façon dont vous allez exporter les données RH au format CSV, il se peut que vous deviez créer plusieurs fichiers CSV contenant un seul type de données HR. Dans ce cas, vous pouvez toujours créer un connecteur HR unique pour importer des données à partir de différents fichiers CSV. Pour ce faire, il vous suffit d’ajouter une colonne HRScenario au fichier CSV et de spécifier le type de données RH. Vous pouvez ensuite exécuter le script pour chaque fichier CSV, mais utiliser le même ID de travail pour le connecteur. Voir [étape 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>Étape 2 : créer une application dans Azure Active Directory

L’étape suivante consiste à créer et à enregistrer une nouvelle application dans Azure Active Directory (AAD). L’application correspond au connecteur RH que vous créez à l’étape 3. La création de cette application permettra à AAD d’authentifier le connecteur RH lorsqu’il s’exécute et tente d’accéder à votre organisation. Cette application est également utilisée pour authentifier le script que vous exécutez à l’étape 4 pour télécharger vos données RH dans le Cloud de Microsoft. Lors de la création de cette application AAD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées à l’étape 3 et à l’étape 4.

- ID de l’application AAD (également *appelé ID de* l’application ou *ID client*)

- Clé secrète de l’application AAD (également appelée *clé secrète client*)

- ID de client (également appelé *ID d’annuaire*)

Pour obtenir des instructions détaillées sur la création d’une application dans AAD, consultez [la rubrique enregistrer une application avec la plateforme d’identité Microsoft](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app).

## <a name="step-3-create-the-hr-connector"></a>Étape 3 : créer le connecteur RH

L’étape suivante consiste à créer un connecteur RH dans le centre de conformité Microsoft 365. Une fois que vous avez exécuté le script à l’étape 4, le connecteur RH que vous créez exporte les données RH du fichier CSV vers votre organisation Microsoft 365. Avant de créer un connecteur, assurez-vous d’avoir une liste des scénarios RH et des noms de colonne CSV correspondants pour chacun d’eux. Vous devez mapper les données requises pour chaque scénario aux noms de colonne réels dans votre fichier CSV lors de la configuration du connecteur. Vous pouvez également télécharger un exemple de fichier CSV lors de la configuration du connecteur et l’Assistant vous aidera à mapper le nom des colonnes aux types de données requis.

Une fois cette étape terminée, veillez à copier l’ID de travail qui est généré lors de la création du connecteur. Vous utiliserez l’ID de travail lorsque vous exécuterez le script.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Dans la page **connecteurs de données (aperçu)** , sous **RH**, cliquez sur **affichage**.

3. Sur la page **personnalisée RH** , cliquez sur **Ajouter un connecteur**.

4. Sur la page **configurer la connexion** , effectuez les opérations suivantes, puis cliquez sur **suivant**:

   a. Tapez ou collez l’ID d’application AAD pour l’application Azure que vous avez créée à l’étape 2.

   b. Tapez un nom pour le connecteur RH.

5. Sur la page scénarios des RH, sélectionnez un ou plusieurs scénarios de RH pour lesquels vous souhaitez importer des données, puis cliquez sur **suivant**.

6. Sur la page méthode de mappage de fichiers, sélectionnez l’une des options suivantes, puis cliquez sur **suivant**.

   - **Téléchargez un fichier d’exemple**. Si vous sélectionnez cette option, cliquez sur **Télécharger un exemple de fichier** pour charger le fichier CSV que vous avez préparé à l’étape 1. Cette option vous permet de sélectionner rapidement des noms de colonne dans votre fichier CSV à partir d’une liste déroulante pour les mapper aux types de données pour les scénarios de RH précédemment sélectionnés.

   OR

   - **Fournissez manuellement les détails de mappage**. Si vous sélectionnez cette option, vous devez taper le nom des colonnes dans votre fichier CSV pour les mapper aux types de données pour les scénarios de RH que vous avez précédemment sélectionnés.

7. Sur la page Détails du mappage de fichiers, effectuez l’une des opérations suivantes, selon que vous avez téléchargé un exemple de fichier CSV et que vous configurez le connecteur pour un seul scénario de RH ou pour plusieurs scénarios. Si vous avez téléchargé un fichier d’exemple, il n’est pas nécessaire de taper les noms de colonne. Vous les sélectionnez dans une liste déroulante.

    - Si vous avez sélectionné un scénario de RH unique à l’étape précédente, tapez les noms d’en-tête de colonne (également appelés *paramètres*) à partir du fichier CSV que vous avez créé à l’étape 1 dans chacune des zones appropriées. Les noms de colonne que vous tapez ne sont pas sensibles à la casse, mais veillez à inclure des espaces si les noms de colonne dans votre fichier CSV incluent des espaces. Comme expliqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de paramètres dans votre fichier CSV. Par exemple, la capture d’écran suivante montre les noms des paramètres de l’exemple de fichier CSV pour le scénario de RH d’abandon d’un employé indiqué à l’étape 1.

    - Si vous avez sélectionné plusieurs types de données dans l’étape ci-dessus, vous devez entrer le nom de la colonne d’identificateur qui identifiera le type de données RH dans votre fichier CSV. Après avoir entré le nom de colonne d’identificateur, tapez la valeur qui identifie ce type de données RH, puis tapez les noms d’en-tête de colonne pour les types de données sélectionnés dans les fichiers CSV que vous avez créés à l’étape 1 dans chacune des zones appropriées pour chaque type de données sélectionné. Comme expliqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de colonne dans votre fichier CSV.

8. Sur la page **révision** , vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Une page d’État s’affiche pour confirmer que le connecteur a été créé. Cette page contient deux éléments importants que vous devez suivre pour exécuter l’exemple de script pour charger vos données RH.

   ![Examiner la page avec l’ID de travail et le lien vers GitHub pour obtenir un exemple de script](../media/HRConnector_Confirmation.png)

   a. **ID de travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez la copier à partir de cette page ou de la page mobile du connecteur.

   b. **Lien vers l’exemple de script.** Cliquez sur le lien **ici** pour accéder au site github afin d’accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Laissez cette fenêtre ouverte pour pouvoir copier le script à l’étape 4. Vous pouvez également insérer un signet dans la destination ou copier l’URL afin de pouvoir y accéder à nouveau lorsque vous exécutez le script. Ce lien est également disponible sur la page mobile du connecteur.

9. Cliquez sur **Terminé**.

   Le nouveau connecteur est affiché dans la liste sous l’onglet **connecteurs** .

10. Cliquez sur le connecteur RH que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

   ![Page de menu volant pour le nouveau connecteur RH](../media/HRConnectorWizard7.png)

Si vous ne l’avez pas déjà fait, vous pouvez copier les valeurs pour l’ID d' **application Azure** et l' **ID de travail de connecteur**. Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page de menu volant (ou le télécharger en utilisant le lien de l’étape suivante).

Vous pouvez également cliquer sur **modifier** pour modifier l’ID de l’application Azure ou les noms d’en-tête de colonne que vous avez définis sur la page **mappage de fichiers** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Étape 4 : exécuter l’exemple de script pour charger vos données RH

La dernière étape de la configuration d’un connecteur RH consiste à exécuter un exemple de script qui télécharge les données RH dans le fichier CSV (que vous avez créé à l’étape 1) vers le Cloud Microsoft. Plus précisément, le script télécharge les données vers le connecteur RH. Après avoir exécuté le script, le connecteur RH que vous avez créé à l’étape 3 importe les données RH dans votre organisation Microsoft 365 où il peut accéder à d’autres outils de conformité, tels que la solution de gestion des risques Insiders. Après avoir exécuté le script, envisagez de planifier une tâche pour qu’elle s’exécute automatiquement quotidiennement de sorte que les données de fin d’employé les plus récentes soient téléchargées vers le Cloud Microsoft. Consultez [la rubrique planifier le script pour qu’il s’exécute automatiquement](#optional-step-6-schedule-the-script-to-run-automatically).

1. Accédez à la fenêtre que vous avez laissée ouverte à l’étape précédente pour accéder au site GitHub à l’aide de l’exemple de script. Vous pouvez également ouvrir le site signet ou utiliser l’URL que vous avez copiée.

2. Cliquez sur le bouton **RAW** pour afficher le script en mode texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, le cas échéant.

5. Enregistrez le fichier texte sous forme de fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier `.ps1` , par exemple, `HRConnector.ps1` .

6. Ouvrez une invite de commandes sur votre ordinateur local et accédez au répertoire dans lequel vous avez enregistré le script.

7. Exécutez la commande suivante pour télécharger les données RH dans le fichier CSV vers le Cloud Microsoft ; par exemple :

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   |**Paramètre**|**Description**
   |:-----|:-----|:-----|
   |`tenantId`|Il s’agit de l’ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 2. Vous pouvez également obtenir l’ID de client de votre organisation sur le panneau de présentation dans le centre **d'** administration Azure ad. Il est utilisé pour identifier votre organisation.|
   |`appId` |Il s’agit de l’ID d’application AAD pour l’application que vous avez créée dans Azure AD à l’étape 2. Il est utilisé par Azure AD pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365. | 
   |`appSecret`|Il s’agit de la clé secrète de l’application AAD pour l’application que vous avez créée dans Azure AD à l’étape 2. Cela est également utilisé pour l’authentification.|
   |`jobId`|Il s’agit de l’ID de travail pour le connecteur HR que vous avez créé à l’étape 3. Il est utilisé pour associer les données RH téléchargées vers le Cloud Microsoft avec le connecteur RH.|
   |`csvFilePath`|Il s’agit du chemin d’accès au fichier CSV (stocké sur le même système que le script) que vous avez créé à l’étape 1. Essayez d’éviter les espaces dans le chemin d’accès du fichier ; Sinon, utilisez des guillemets simples.|
   |||

   Voici un exemple de syntaxe pour le script du connecteur RH en utilisant les valeurs réelles de chaque paramètre :

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Si le chargement réussit, le script affiche le message **chargement réussi** .
   
   > [!NOTE]
   > Si vous rencontrez des problèmes lors de l’exécution de la commande précédente en raison des stratégies excution, voir [about Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies) et [Set-ExecutionPolicy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des instructions sur la définition des stratégies d’exécution. 

## <a name="step-5-monitor-the-hr-connector"></a>Étape 5 : surveiller le connecteur RH

Après avoir créé le connecteur RH et exécuté le script pour charger vos données RH, vous pouvez consulter le connecteur et l’état du chargement dans le centre de conformité Microsoft 365. Si vous planifiez le script pour qu’il s’exécute automatiquement régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur RH pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

   ![Page mobile du connecteur RH avec les propriétés et l’État](../media/HRConnectorFlyout1.png)

3. Sous en **cours**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données à partir du fichier CSV vers le Cloud Microsoft. 

   ![Le fichier journal du connecteur RH affiche les lignes numériques à partir du fichier CSV qui ont été téléchargées](../media/HRConnectorLogFile.png)

   Le `RecordsSaved` champ indique le nombre de lignes du fichier CSV téléchargé. Par exemple, si le fichier CSV contient quatre lignes, la valeur des `RecordsSaved` champs est 4, si le script a téléchargé avec succès toutes les lignes dans le fichier CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien vers le téléchargement du script est affiché lors de la **dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes pour exécuter le script.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>Module Étape 6 : planifier le script pour qu’il s’exécute automatiquement

Pour vous assurer que les dernières données RH de votre organisation sont accessibles aux outils comme la solution de gestion des risques Insiders, nous vous recommandons de planifier le script pour qu’il s’exécute automatiquement de manière récurrente, par exemple une fois par jour. Cela vous oblige également à mettre à jour les données RH dans le fichier CSV sur une planification similaire (si elle n’est pas la même) de façon à ce qu’elles contiennent les informations les plus récentes sur les employés qui quittent votre organisation. L’objectif est de télécharger les données RH les plus récentes afin que le connecteur RH puisse le mettre à la disposition de la solution de gestion des risques Insiders.

Vous pouvez utiliser l’application planificateur de tâches de Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton **Démarrer** de Windows, puis tapez **Planificateur de tâches**.

2. Cliquez sur l’application **Planificateur de tâches** pour l’ouvrir.

3. Dans la section **actions** , cliquez sur **créer une tâche**.

4. Sous l’onglet **général** , entrez un nom descriptif pour la tâche planifiée ; par exemple, le **script du connecteur RH**. Vous pouvez également ajouter une description facultative.

5. Sous **options de sécurité**, procédez comme suit :

   a. Déterminez s’il faut exécuter le script uniquement lorsque vous avez ouvert une session sur l’ordinateur ou que vous l’exécutez lorsque vous êtes connecté.

   b. Assurez-vous que la case à cocher **exécuter avec les privilèges les plus élevés** est activée.

6. Sélectionnez l’onglet **déclencheurs** , cliquez sur **nouveau**, puis effectuez les opérations suivantes :

   a. Sous **paramètres**, sélectionnez l’option **quotidien** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script se verra tous les jours au même moment.

   b. Sous **Paramètres avancés**, vérifiez que la case à cocher **activé** est activée.

   c. Cliquez sur **OK**.

7. Sélectionnez l’onglet **actions** , cliquez sur **nouveau**, puis effectuez les opérations suivantes :

   ![Paramètres des actions pour créer une tâche planifiée pour le script du connecteur RH](../media/HRConnectorScheduleTask1.png)

   a. Dans la liste déroulante **action** , assurez-vous que l’option **Démarrer un programme** est sélectionnée.

   b. Dans la zone **programme/script** , cliquez sur **Parcourir**, accédez à l’emplacement suivant et sélectionnez-le pour afficher le chemin d’accès dans la zone : `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` .

   c. Dans la zone **Ajouter des arguments (facultatif)** , collez la même commande de script que celle que vous avez exécutée à l’étape 4. Par exemple, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   d. Dans la zone **commencer dans (facultatif)** , collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple, `C:\Users\contosoadmin\Desktop\Scripts`.

   e. Cliquez sur **OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **créer une tâche** , cliquez sur **OK** pour enregistrer la tâche planifiée. Vous serez peut-être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche est affichée dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche est affichée dans la bibliothèque du planificateur de tâches.](../media/HRConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script est exécuté et la prochaine fois qu’il est planifiée pour s’exécuter. Vous pouvez double-cliquer sur la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script s’est exécuté sur la page de menu volant du connecteur RH correspondant dans le centre de conformité.

## <a name="existing-hr-connectors"></a>Connecteurs RH existants

Le 20 juillet 2020, nous avons publié des scénarios supplémentaires pris en charge par les connecteurs RH. Voici les scénarios de RH décrits précédemment dans cet article. Tout connecteur RH créé avant cette date ne prend en charge que le scénario de démission de l’employé. Si vous avez créé un connecteur RH avant le 20 juillet 2020, nous l’avons migré afin qu’il continue à migrer vos données RH vers le Cloud Microsoft. Vous n’avez rien à faire pour maintenir cette fonctionnalité. Vous pouvez continuer à utiliser le connecteur sans interruption.

Si vous souhaitez implémenter des scénarios de RH supplémentaires, créez un nouveau connecteur RH et configurez-le pour les scénarios de RH supplémentaires publiés. Vous devrez également créer un ou plusieurs nouveaux fichiers CSV qui contiennent les données afin de prendre en charge les scénarios de RH supplémentaires. Après avoir créé un nouveau connecteur RH, exécutez le script à l’aide de l’ID du nouveau connecteur et des fichiers CSV avec les données de vos scénarios de RH supplémentaires.
