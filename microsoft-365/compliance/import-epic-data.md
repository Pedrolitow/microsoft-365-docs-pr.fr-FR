---
title: Configurer un connecteur pour importer les données EHR d’Ehr
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
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données d’enregistrements de santé électroniques (EHR) à partir du système de Contrôle de votre organisation vers Microsoft 365. Cela vous permet d’utiliser des données EHR dans les stratégies de gestion des risques internes pour vous aider à détecter l’activité d’accès non autorisé aux données des patients par vos employés.
ms.openlocfilehash: 0da7386aa2b230492fedd5fdac5477d204aa63a8
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62321122"
---
# <a name="set-up-a-connector-to-import-epic-ehr-audit-data-preview"></a>Configurer un connecteur pour importer les données d’audit EHR d’Ehr (prévisualisation)

Vous pouvez configurer un connecteur de données dans le Centre de conformité Microsoft 365 pour importer des enregistrements d’audit pour l’activité des utilisateurs dans le système EHR (Electronic Healthcare Records) de votre organisation. Les enregistrements d’audit à partir de votre système EHR d’Ehr d’Ehr incluent des enregistrements pour les événements liés à l’accès aux enregistrements de santé d’un patient. Les enregistrements d’audit EHR peuvent être utilisés par la [solution](insider-risk-management.md) Microsoft 365 de gestion des risques internes pour protéger votre organisation contre tout accès non autorisé aux informations des patients.

La configuration d’un connecteur de Connecteur comprend les tâches suivantes :

- Création d’une application dans Azure Active Directory (Azure AD) pour accéder à un point de terminaison d’API qui accepte un fichier texte séparé par des tabulations contenant des enregistrements d’audit EHR.

- Création d’un fichier texte avec tous les champs requis tels que définis dans le schéma du connecteur.

- Création d’une instance de connecteur Dent dans le Centre de conformité Microsoft 365.

- Exécution d’un script pour pousser les enregistrements d’audit EHR d’Ehr vers le point de terminaison de l’API.

- Éventuellement, planifier l’exécuter automatiquement pour importer des enregistrements d’audit.

## <a name="before-you-set-up-the-connector"></a>Avant de configurer le connecteur

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée le connecteur Connecteur à l’étape 3 Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, [](/Exchange/permissions-exo/role-groups#create-role-groups) voir [les sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

- Vous devez déterminer comment récupérer ou exporter les données à partir du système EHR de Votre organisation (quotidiennement) et créer un fichier texte décrit à l’étape 2. Le script que vous exécutez à l’étape 4 envoie les données du fichier texte au point de terminaison de l’API.

- L’exemple de script que vous exécutez à l’étape 4 pousse les enregistrements d’audit EHR d’Ehr d’Ehr de fichier texte vers l’API du connecteur afin qu’il puisse être utilisé par la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à créer et inscrire une nouvelle application dans Azure Active Directory (Azure AD). L’application correspond au connecteur Connecteur de Connecteur que vous créez à l’étape 3. La création de cette application permet Azure AD authentifier la demande Push pour un fichier texte contenant des enregistrements d’audit EHR. Lors de la création de cette Azure AD, n’oubliez pas d’enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- Azure AD’ID d’application (également appelé *ID* d’application ou *ID client*)

- Azure AD’application secrète (également appelée *la secret client*)

- ID de client (également appelé *ID d’annuaire*)

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, voir Enregistrer une application avec le [Plateforme d'identités Microsoft](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-epic-ehr-audit-records"></a>Étape 2 : Préparer un fichier texte avec les enregistrements d’audit EHR d’Ehr

L’étape suivante consiste à créer un fichier texte qui contient des informations sur l’accès des employés aux dossiers de santé des patients dans le système EHR de Votre organisation. Comme indiqué précédemment, vous devez déterminer comment générer ce fichier texte à partir de votre système EHR d’Ehr. Le flux de travail connecteur de Connecteur de Connecteur requiert un fichier texte avec des valeurs séparées par des tabulations pour mammiser ces données dans le fichier texte avec le schéma de connecteur requis. Le format de fichier pris en charge est un fichier .txt canal ou tabulation.

> [!NOTE]
> La taille maximale du fichier texte qui contient les données d’audit est de 3 Go. Le nombre maximal de lignes est de 5 millions. En outre, n’incluez que les données d’audit pertinentes de votre système ehr de santé.

Le tableau suivant répertorie les champs requis pour activer les scénarios de gestion des risques internes. Un sous-ensemble de ces champs est obligatoire. Ces champs sont mis en surbrill plan avec un astérisque (*). Si l’un des champs obligatoires est manquant dans le fichier texte, le fichier n’est pas validé et les données du fichier ne sont pas importées.

|Field|Catégorie|
|:----|:----------|
| ACCESS_LOG. *<br/>ACCESS_TIME ACCESS_LOG_METRIC. METRIC_NAME*<br/>ACCESS_LOG. WORKSTATION_ID<br/>ZCMETRIC\_\_ GROUP.NAME<br/>ZCACCESS\_\_ ACTION.NAME |Ces champs sont utilisés pour identifier les événements d’activité d’accès dans votre système EHR d’Ehr d’Ehr.|
| PATIENT. PAT_MRN_ID<br/>PATIENT. PAT_FIRST_NAME* <br/>PATIENT. PAT_MIDDLE_NAME <br/>PATIENT. PAT_LAST_NAME* <br/>PATIENT. ADD_LINE_1* <br/>PATIENT. ADD_LINE_2  <br/>PATIENT. CITY* <br/>PATIENT.ZIP*  <br/>ZC_STATE.NAME <br/>ZC_COUNTRY.NAME <br/>CLARITY_DEP. DEPARTMENT_NAME              | Ces champs sont utilisés pour identifier les informations de profil de patient.|
| ZC_BTG_REASON.NAME*<br/> PAT_BTG_AUDIT. BTG_EXPLANATION | Ces champs sont utilisés pour identifier l’accès aux enregistrements restreints.|
| EMP. SYSTEM_LOGIN*<br/>CLARITY_EMP. USER_ID <br/> employee_last_name <sup>1</sup> <br/> employee_first_name <sup>1</sup>                | Ces champs sont utilisés pour identifier les informations de profil d’employé pour la correspondance d’adresse et de nom requise pour déterminer l’accès aux enregistrements famille/voisin/employé. |
|||

> [!NOTE]
> Assurez-vous que vous exportez uniquement les mesures log pertinentes à partir de Contrôle. 
> <sup>1</sup> Ce champ n’est pas disponible par défaut dans Le Domaine. Vous devez configurer l’exportation pour vous assurer que le fichier texte contient ce champ.

## <a name="step-3-create-the-epic-connector"></a>Étape 3 : Créer le connecteur Connecteur

L’étape suivante consiste à créer un connecteur Connecteur dans le Centre de conformité Microsoft 365. Après avoir exécuté le script à l’étape 4, le fichier texte que vous avez créé à l’étape 2 est traitée et envoyé au point de terminaison de l’API que vous avez installé à l’étape 1. Dans cette étape, assurez-vous de copier le JobId généré lorsque vous créez le connecteur. Vous utiliserez JobId lorsque vous exécuterez le script.

1. Go to <https://compliance.microsoft.com> and then click **Data connectors** in the left nav.

2. Dans la page **Connecteurs de données** sous **Connecteur de Connecteur,** cliquez sur **Afficher**.

3. Dans la page **Connecteur de connecteur** , cliquez **sur Ajouter un connecteur**.

4. Dans la page **Configuration de la connexion** , faites ce qui suit, puis cliquez sur **Suivant** :

    1. Tapez ou collez l Azure AD’application pour l’application Azure que vous avez créée à l’étape 2.

    2. Tapez un nom pour le connecteur Connecteur de Connecteur.

5. Dans la page **Révision** , examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Une page d’état qui confirme que le connecteur a été créé s’affiche. Cette page contient deux éléments importants que vous devez effectuer à l’étape suivante pour exécuter l’exemple de script afin de télécharger vos données d’enregistrements d’audit EHR d’Ehr.

    Page de révision avec ID de travail et lien vers github pour un exemple de script

    1. **ID de travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez le copier à partir de cette page ou à partir de la page de flyout du connecteur.

    2. **Schéma de référence.** Reportez-vous au schéma pour comprendre quels champs de votre système de Contrôle sont acceptés par connecteur. Cela vous aidera à créer un fichier avec tous les champs de base de données De Base de données Requis.

    3. **Lien vers l’exemple de script.** Cliquez sur **le lien** ici pour accéder au site GitHub pour accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Gardez cette fenêtre ouverte afin de pouvoir copier le script à l’étape 4. Vous pouvez également réserver un signet à la destination ou copier l’URL afin de pouvoir y accéder à nouveau lorsque vous exécutez le script. Ce lien est également disponible sur la page volante du connecteur.

6. Cliquez sur **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous **l’onglet Connecteurs** .

7. Cliquez sur le connecteur de Connecteur que vous avez créé pour afficher la page de présentation, qui contient des propriétés et d’autres informations sur le connecteur.

Si ce n’est pas déjà fait, vous pouvez copier les valeurs de **l’ID d’application Azure** et de **l’ID** de travail connecteur. Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page volante (ou le télécharger à l’aide du lien de l’étape suivante).)

Vous pouvez également cliquer sur **Modifier** pour modifier l’ID d’application Azure ou les noms d’en-tête de colonne que vous avez définis sur la page **de mappage de** fichiers.

## <a name="step-4-run-the-sample-script-to-upload-your-epic-ehr-audit-records"></a>Étape 4 : Exécuter l’exemple de script pour télécharger vos enregistrements d’audit EHR Ehr

La dernière étape de la configuration d’un connecteur Der consiste à exécuter un exemple de script qui téléchargera les données d’enregistrements d’audit EHR De Sons dans le fichier texte (que vous avez créé à l’étape 1) dans le cloud Microsoft. Plus précisément, le script charge les données vers le connecteur Connecteur de Connecteur. Une fois que vous avez exécuté le script, le connecteur Connecteur de Connecteur que vous avez créé à l’étape 3 importe les données des enregistrements d’audit EHR d’Ehr à votre organisation Microsoft 365 où ils sont accessibles par d’autres outils de conformité, tels que la solution de gestion des risques internes. Après avoir exécuté le script, envisagez de planifier une tâche pour qu’elle s’exécute automatiquement quotidiennement afin que les données les plus récentes de résiliation d’employé sont chargées dans le cloud Microsoft. Voir [(facultatif) Étape 6 : planifier l’exécuter automatiquement](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Comme indiqué précédemment, la taille maximale du fichier texte qui contient les données d’audit est de 3 Go. Le nombre maximal de lignes est de 5 millions. Le script que vous exécutez dans cette étape prendra environ 30 à 40 minutes pour importer les données d’audit à partir de fichiers texte de grande taille. En outre, le script divise les fichiers texte de grande taille en blocs plus petits de 100 000 lignes, puis importe ces blocs séquentiellement.

1. Accédez à la fenêtre que vous avez laissée ouverte à partir de l’étape précédente pour accéder au site GitHub avec l’exemple de script. Vous pouvez également ouvrir le site avec signet ou utiliser l’URL que vous avez copiée. Vous pouvez également accéder au script [ici](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Cliquez sur **le bouton Brut** pour afficher le script en affichage texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, si nécessaire.

5. Enregistrez le fichier texte en tant que fichier Windows PowerShell script à l’aide d’un suffixe `.ps1`de nom de fichier de ; par exemple, `EpicConnector.ps1`.

6. Ouvrez une invite de commandes sur votre ordinateur local et allez dans le répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour télécharger les données d’audit de Lasa dans le fichier texte dans le cloud Microsoft . par exemple :

   ```powershell
   .\EpicConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations obtenues lors des étapes précédentes sont utilisées dans les valeurs de ces paramètres.

|Paramètre  |Description|
|:----------|:----------|
|tenantId|Il s’agit de l’ID de votre Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir l’ID de locataire de votre organisation  dans le panneau Vue d’ensemble du centre d Azure AD’administration. Il est utilisé pour identifier votre organisation.|
|appId|Il s’agit Azure AD’ID d’application pour l’application que vous avez créée Azure AD l’étape 1. Il est utilisé par les Azure AD pour l’authentification lorsque le script tente d’accéder à Microsoft 365 organisation.|
|appSecret|Il s’agit de la Azure AD’application secrète de l’application que vous avez créée Azure AD l’étape 1. Cette fonction est également utilisée pour l’authentification.|
|jobId|Il s’agit de l’ID de travail pour le connecteur Connecteur de Connecteur que vous avez créé à l’étape 3. Il permet d’associer les enregistrements d’audit EHR d’Ehr d’Ehr qui sont téléchargés vers le cloud Microsoft au connecteur de Connecteur de Connecteur.|
|filePath|Il s’agit du chemin d’accès au fichier texte (stocké sur le même système que le script) que vous avez créé à l’étape 2. Essayez d’éviter les espaces dans le chemin d’accès du fichier . sinon, utilisez des guillemets simples.|
|||

Voici un exemple de syntaxe pour le script Connecteur de Connecteur à l’aide de valeurs réelles pour chaque paramètre :

```powershell
.\EpicConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\epic_audit_records.txt'
```

Si le chargement réussit, le script affiche le message **Télécharger réussite**.

> [!NOTE]
> Si vous avez des problèmes lors de l’exécution de la commande précédente [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) en raison des stratégies d’exécution, voir À propos des stratégies d’exécution et [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des instructions sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-epic-connector"></a>Étape 5 : Surveiller le connecteur Connecteur

Une fois que vous avez créé le connecteur De Connecteur et envoyé vos enregistrements d’audit EHR, vous pouvez afficher le connecteur et télécharger l’état dans le Centre de conformité Microsoft 365. Si vous programmez l’exécuter automatiquement sur une base régulière, vous pouvez également afficher l’état actuel après la dernière fois que le script a été exécuté.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs** , puis sélectionnez le connecteur Connecteur de Connecteur pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **Dernière importation**, cliquez sur le lien **Télécharger le** journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données du fichier texte vers le cloud Microsoft.

    Le fichier journal du connecteur de connecteur affiche les lignes de numéro à partir du fichier texte qui ont été téléchargées

    Le `RecordsSaved` champ indique le nombre de lignes dans le fichier texte téléchargé. Par exemple, si le fichier texte contient quatre lignes, `RecordsSaved` la valeur des champs est 4, si le script a correctement téléchargé toutes les lignes du fichier texte.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes pour exécuter le script.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécuter automatiquement

Pour vous assurer que les derniers enregistrements d’audit de votre système EHR d’Ehr sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécuter automatiquement tous les jours. Pour ce faire, vous devez également mettre à jour les données d’enregistrement d’audit dans le même fichier texte selon une planification similaire (si ce n’est pas la même) afin qu’elles contiennent les dernières informations sur les activités d’accès aux enregistrements de patients par vos employés. L’objectif est de télécharger les enregistrements d’audit les plus à jour afin que le connecteur Connecteur puisse le mettre à la disposition de la solution de gestion des risques internes. 

Vous pouvez utiliser l’application De planification des tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur Windows **bouton** Démarrer, puis tapez Planification **des tâches**.

2. Cliquez sur **l’application De planification des** tâches pour l’ouvrir.

3. Dans la section **Actions** , cliquez sur **Créer une tâche**.

4. Sous **l’onglet** Général, tapez un nom descriptif pour la tâche programmée . par exemple, **script connecteur de connecteur**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité**, faites les actions suivantes :

    1. Déterminez s’il faut exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou l’exécuter lorsque vous êtes connecté ou non.

    2. Assurez-vous que la case **à cocher Exécuter avec les privilèges les plus élevés** est sélectionnée.

6. Sélectionnez **l’onglet Déclencheurs** , cliquez **sur Nouveau**, puis faites les choses suivantes :

    1. Sous **Paramètres**, sélectionnez l’option **Quotidienne**, puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script s’exécute tous les jours à la même heure spécifiée.

    2. Sous **Paramètres avancés**, vérifiez que la case **à** cocher Activée est activée.

    3. Cliquez sur **OK**.

7. Sélectionnez **l’onglet Actions** , cliquez **sur Nouveau**, puis faites les actions suivantes :

   ![Paramètres d’action pour créer une tâche programmée pour le script de connecteur de connecteur de connecteur.](../media/EpicConnectorScheduleTask1.png)

    1. Dans la **liste liste de** listes d’actions, assurez-vous que **démarrer un programme** est sélectionné.

    2. Dans la **zone Programme/script** , cliquez sur **Parcourir, puis** accédez à l’emplacement suivant et sélectionnez-le afin que le chemin d’accès s’affiche dans la zone : C:.0.exe.

    3. Dans la **zone Ajouter des arguments (facultatif),** collez la même commande de script que celle que vous avez l’étape 4. Par exemple, `.\EpicConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Epic\audit\records.txt"`

    4. Dans la **zone Démarrer dans (facultatif),** collez l’emplacement du dossier du script que vous avez écrit à l’étape 4. Par exemple, C:\Contrôle\audit.

    5. Cliquez **sur OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la **fenêtre Créer une** tâche, cliquez sur **OK** pour enregistrer la tâche programmée. Vous pouvez être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du Programmeur de tâches.

   ![La nouvelle tâche pour le script de connecteur de soins de santé s’affiche dans la bibliothèque du Programmeur de tâches.](../media/EpicConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script a été exécuté et la prochaine fois qu’il est programmé pour s’exécuter, s’affiche. Vous pouvez double-cliquer sur la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script a été en cours d’utilisation sur la page volante du connecteur Connecteur de connecteur correspondant dans le centre de conformité.
