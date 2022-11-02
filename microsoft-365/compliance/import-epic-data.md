---
title: Configurer un connecteur pour importer des données Epic EHR
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données de dossiers médicaux électroniques (DSE) à partir du système Epic de votre organisation vers Microsoft 365. Cela vous permet d’utiliser les données Epic EHR dans les stratégies de gestion des risques internes pour vous aider à détecter l’activité d’accès non autorisé aux données des patients par vos employés.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 07/15/2022
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
ms.openlocfilehash: f3e6c9a04d11a629d6dc8136c101939713078102
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68812693"
---
# <a name="set-up-a-connector-to-import-epic-ehr-audit-data-preview"></a>Configurer un connecteur pour importer des données d’audit Epic EHR (préversion)

Vous pouvez configurer un connecteur de données dans le portail de conformité Microsoft Purview pour importer des enregistrements d’audit pour l’activité des utilisateurs dans le système Epic Electronic Healthcare Records (EHR) de votre organisation. Les enregistrements d’audit de votre système Epic EHR incluent des enregistrements pour les événements liés à l’accès aux dossiers médicaux d’un patient. Les enregistrements d’audit epic EHR peuvent être utilisés par la [solution de gestion des risques internes](insider-risk-management.md) Microsoft Purview pour protéger votre organisation contre tout accès non autorisé aux informations des patients.

La configuration d’un connecteur Epic comprend les tâches suivantes :

- Création d’une application dans Azure Active Directory (Azure AD) pour accéder à un point de terminaison d’API qui accepte un fichier texte séparé par des tabulations contenant des enregistrements d’audit Epic EHR.

- Création d’un fichier texte avec tous les champs obligatoires tels que définis dans le schéma du connecteur.

- Création d’une instance de connecteur Epic dans le portail de conformité.

- Exécution d’un script pour envoyer (push) des enregistrements d’audit Epic EHR au point de terminaison d’API.

- Si vous le souhaitez, planifiez l’exécution automatique du script pour importer des enregistrements d’audit.

Si vous souhaitez participer à la préversion, contactez l’équipe à dcfeedback@microsoft.com.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-set-up-the-connector"></a>Avant de configurer le connecteur

- L’utilisateur qui crée le connecteur Epic à l’étape 3 doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Vous devez déterminer comment récupérer ou exporter les données à partir du système Epic EHR de votre organisation (sur une base quotidienne) et créer un fichier texte décrit à l’étape 2. Le script que vous exécutez à l’étape 4 envoie les données du fichier texte au point de terminaison de l’API.

- L’exemple de script que vous exécutez à l’étape 4 envoie (push) les enregistrements d’audit Epic EHR du fichier texte à l’API du connecteur afin qu’il puisse être utilisé par la solution de gestion des risques internes. Cet exemple de script n’est pris en charge dans aucun programme ou service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à créer et inscrire une application dans Azure Active Directory (Azure AD). L’application correspond au connecteur Epic que vous créez à l’étape 3. La création de cette application permet à Azure AD d’authentifier la demande Push pour le fichier texte contenant des enregistrements d’audit Epic EHR. Lors de la création de cette application Azure AD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID d’application Azure AD (également appelé *ID d’application* ou *ID client*)

- Clé secrète d’application Azure AD (également appelée *clé secrète client*)

- ID de locataire (également appelé *ID d’annuaire*)

Pour obtenir des instructions pas à pas sur la création d’une application dans Azure AD, consultez [Inscrire une application auprès du Plateforme d'identités Microsoft](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-epic-ehr-audit-records"></a>Étape 2 : Préparer un fichier texte avec des enregistrements d’audit Epic EHR

L’étape suivante consiste à créer un fichier texte qui contient des informations sur l’accès des employés aux dossiers médicaux des patients dans le système Epic EHR de votre organisation. Comme expliqué précédemment, vous devez déterminer comment générer ce fichier texte à partir de votre système Epic EHR. Le workflow du connecteur Epic nécessite un fichier texte avec des valeurs séparées par des tabulations pour mapper ces données dans le fichier texte avec le schéma de connecteur requis. Le format de fichier pris en charge est un fichier .txt séparé par des barres verticales ou des onglets.

> [!NOTE]
> La taille maximale du fichier texte qui contient les données d’audit est de 3 Go. Le nombre maximal de lignes est de 5 millions. Veillez également à inclure uniquement les données d’audit pertinentes de votre système de DSE de santé.

Le tableau suivant répertorie les champs requis pour activer les scénarios de gestion des risques internes. Un sous-ensemble de ces champs est obligatoire. Ces champs sont mis en surbrillance avec un astérisque (*). Si l’un des champs obligatoires est manquant dans le fichier texte, le fichier ne sera pas validé et les données du fichier ne seront pas importées.

|Champ|Catégorie|
|:----|:----------|
| ACCESS_LOG. *<br/>ACCESS_TIME ACCESS_LOG_METRIC. METRIC_NAME*<br/>ACCESS_LOG. WORKSTATION_ID<br/>ZC\_METRIC\_GROUP.NAME<br/>ZC\_ACCESS\_ACTION.NAME |Ces champs sont utilisés pour identifier les événements d’activité d’accès dans votre système Epic EHR.|
| PATIENT. PAT_MRN_ID<br/>PATIENT. PAT_FIRST_NAME* <br/>PATIENT. PAT_MIDDLE_NAME <br/>PATIENT. PAT_LAST_NAME* <br/>PATIENT. ADD_LINE_1* <br/>PATIENT. ADD_LINE_2  <br/>PATIENT. VILLE* <br/>PATIENT.ZIP*  <br/>ZC_STATE.NAME <br/>ZC_COUNTRY.NAME <br/>CLARITY_DEP. DEPARTMENT_NAME              | Ces champs sont utilisés pour identifier les informations de profil des patients.|
| ZC_BTG_REASON.NAME*<br/> PAT_BTG_AUDIT. BTG_EXPLANATION | Ces champs sont utilisés pour identifier l’accès aux enregistrements restreints.|
| Emp. SYSTEM_LOGIN*<br/>CLARITY_EMP. USER_ID <br/> employee_last_name<sup>1</sup> <br/> employee_first_name<sup>1</sup>                | Ces champs sont utilisés pour identifier les informations de profil de l’employé pour les correspondances d’adresse et de nom requises pour déterminer l’accès aux enregistrements famille/voisin/employé. |
|||

> [!NOTE]
> Vérifiez que vous exportez uniquement les métriques de journal pertinentes à partir d’Epic. 
> <sup>1</sup> Ce champ n’est pas disponible par défaut dans Epic. Vous devez configurer l’exportation pour vous assurer que le fichier texte contient ce champ.

## <a name="step-3-create-the-epic-connector"></a>Étape 3 : Créer le connecteur Epic

L’étape suivante consiste à créer un connecteur Epic dans le portail de conformité. Après avoir exécuté le script à l’étape 4, le fichier texte que vous avez créé à l’étape 2 est traité et envoyé au point de terminaison d’API que vous avez configuré à l’étape 1. Dans cette étape, veillez à copier le JobId généré lorsque vous créez le connecteur. Vous utiliserez le JobId lorsque vous exécuterez le script.

1. Accédez à <https://compliance.microsoft.com> , puis sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Dans la page **Connecteurs de données** sous **Connecteur Epic**, sélectionnez **Afficher**.

3. Dans la page **Connecteur Epic** , sélectionnez **Ajouter un connecteur**.

4. Dans la page **Configurer la connexion** , procédez comme suit, puis sélectionnez **Suivant** :

    1. Tapez ou collez l’ID d’application Azure AD pour l’application Azure que vous avez créée à l’étape 2.

    2. Tapez un nom pour le connecteur Epic.

5. Dans la page **Révision** , passez en revue vos paramètres, puis sélectionnez **Terminer** pour créer le connecteur.

   Une page d’état s’affiche et confirme que le connecteur a été créé. Cette page contient deux éléments importants dont vous avez besoin pour effectuer l’étape suivante pour exécuter l’exemple de script afin de charger vos données d’enregistrements d’audit Epic EHR.

    Page de révision avec l’ID de travail et le lien vers GitHub pour l’exemple de script

    1. **ID du travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez le copier à partir de cette page ou à partir de la page de menu volant du connecteur.

    2. **Schéma de référence.** Reportez-vous au schéma pour comprendre quels champs de votre système Epic sont acceptés par le connecteur. Cela vous aidera à créer un fichier avec tous les champs de base de données Epic requis.

    3. **Lien vers l’exemple de script.** Sélectionnez le lien **ici** pour accéder au site GitHub afin d’accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Gardez cette fenêtre ouverte afin de pouvoir copier le script à l’étape 4. Vous pouvez également ajouter un signet à la destination ou copier l’URL pour y accéder à nouveau lorsque vous exécutez le script. Ce lien est également disponible sur la page de menu volant du connecteur.

6. Sélectionnez **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous l’onglet **Connecteurs** .

7. Sélectionnez le connecteur Epic que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

Si vous ne l’avez pas déjà fait, vous pouvez copier les valeurs de **l’ID Azure App** et de **l’ID de travail du connecteur**. Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page de menu volant (ou le télécharger à l’aide du lien à l’étape suivante).)

Vous pouvez également sélectionner **Modifier** pour modifier l’ID Azure App ou les noms d’en-têtes de colonne que vous avez définis dans la page **Mappage de** fichiers.

## <a name="step-4-run-the-sample-script-to-upload-your-epic-ehr-audit-records"></a>Étape 4 : Exécuter l’exemple de script pour charger vos enregistrements d’audit Epic EHR

La dernière étape de la configuration d’un connecteur Epic consiste à exécuter un exemple de script qui charge les données des enregistrements d’audit Epic EHR dans le fichier texte (que vous avez créé à l’étape 1) dans le cloud Microsoft. Plus précisément, le script charge les données sur le connecteur Epic. Après avoir exécuté le script, le connecteur Epic que vous avez créé à l’étape 3 importe les données des enregistrements d’audit Epic EHR dans votre organisation Microsoft 365, où ils sont accessibles par d’autres outils de conformité, tels que la solution de gestion des risques internes. Après avoir exécuté le script, envisagez de planifier une tâche pour l’exécuter automatiquement quotidiennement afin que les données d’arrêt des employés les plus actuelles soient chargées dans le cloud Microsoft. Consultez [(Facultatif) Étape 6 : Planifier l’exécution automatique du script](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Comme indiqué précédemment, la taille maximale du fichier texte qui contient les données d’audit est de 3 Go. Le nombre maximal de lignes est de 5 millions. Le script que vous exécutez dans cette étape prend environ 30 à 40 minutes pour importer les données d’audit à partir de fichiers texte volumineux. En outre, le script divise les fichiers texte volumineux en blocs plus petits de 100 000 lignes, puis importe ces blocs séquentiellement.

1. Accédez à la fenêtre que vous avez laissée ouverte à l’étape précédente pour accéder au site GitHub avec l’exemple de script. Vous pouvez également ouvrir le site avec signet ou utiliser l’URL que vous avez copiée. Vous pouvez également accéder au script [ici](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Sélectionnez le bouton **Brut** pour afficher le script en mode texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, si nécessaire.

5. Enregistrez le fichier texte en tant que fichier de script Windows PowerShell en utilisant un suffixe de nom de fichier de `.ps1`; par exemple, `EpicConnector.ps1`.

6. Ouvrez une invite de commandes sur votre ordinateur local, puis accédez au répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour charger les données d’audit Epic dans le fichier texte dans le cloud Microsoft . par exemple :

   ```powershell
   .\EpicConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

|Paramètre  |Description|
|:----------|:----------|
|tenantId|Il s’agit de l’ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir l’ID de locataire de votre organisation dans le panneau **Vue d’ensemble** du Centre d’administration Azure AD. Cela permet d’identifier votre organisation.|
|appId|Il s’agit de l’ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est utilisé par Azure AD pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365.|
|appSecret|Il s’agit du secret de l’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est également utilisé pour l’authentification.|
|jobId|Il s’agit de l’ID de travail pour le connecteur Epic que vous avez créé à l’étape 3. Il permet d’associer les enregistrements d’audit Epic EHR chargés dans le cloud Microsoft au connecteur Epic.|
|Filepath|Il s’agit du chemin d’accès du fichier texte (stocké sur le même système que le script) que vous avez créé à l’étape 2. Essayez d’éviter les espaces dans le chemin d’accès au fichier ; sinon, utilisez des guillemets simples.|
|||

Voici un exemple de syntaxe pour le script de connecteur Epic utilisant des valeurs réelles pour chaque paramètre :

```powershell
.\EpicConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\epic_audit_records.txt'
```

Si le chargement réussit, le script affiche le message **Chargement réussi** .

> [!NOTE]
> Si vous rencontrez des problèmes lors de l’exécution de la commande précédente en raison de stratégies d’exécution, consultez [À propos des stratégies d’exécution](/powershell/module/microsoft.powershell.core/about/about_execution_policies) et [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des conseils sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-epic-connector"></a>Étape 5 : Surveiller le connecteur Epic

Après avoir créé le connecteur Epic et envoyé (push) vos enregistrements d’audit EHR, vous pouvez afficher l’état du connecteur et le chargement dans le portail de conformité. Si vous planifiez l’exécution automatique du script régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez à <https://compliance.microsoft.com> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur Epic pour afficher la page de menu volant. Cette page contient les propriétés et les informations relatives au connecteur.

3. Sous **Dernière importation**, sélectionnez le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données du fichier texte dans le cloud Microsoft.

    Le fichier journal du connecteur Epic affiche les lignes numériques du fichier texte qui ont été chargées

    Le `RecordsSaved` champ indique le nombre de lignes dans le fichier texte chargé. Par exemple, si le fichier texte contient quatre lignes, la valeur des `RecordsSaved` champs est 4, si le script a correctement chargé toutes les lignes du fichier texte.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes pour exécuter le script.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécution automatique du script

Pour vous assurer que les derniers enregistrements d’audit de votre système Epic EHR sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécution automatique du script quotidiennement. Cela nécessite également que vous mettez à jour les données d’enregistrement d’audit Epic dans le même fichier texte selon une planification similaire (sinon identique) afin qu’elle contienne les dernières informations sur les activités d’accès aux dossiers des patients par vos employés. L’objectif est de charger les enregistrements d’audit les plus actuels afin que le connecteur Epic puisse les mettre à la disposition de la solution de gestion des risques internes. 

Vous pouvez utiliser l’application Planificateur de tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, sélectionnez le bouton **Démarrer** de Windows, puis tapez **Planificateur de tâches**.

2. Sélectionnez l’application **Planificateur** de tâches pour l’ouvrir.

3. Dans la section **Actions** , sélectionnez **Créer une tâche**.

4. Sous l’onglet **Général** , tapez un nom descriptif pour la tâche planifiée. par exemple, **script de connecteur Epic**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité**, procédez comme suit :

    1. Déterminez s’il faut exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou l’exécuter lorsque vous êtes connecté ou non.

    2. Vérifiez que la case **Exécuter avec les privilèges les plus élevés** est cochée.

6. Sélectionnez l’onglet **Déclencheurs** , sélectionnez **Nouveau**, puis procédez comme suit :

    1. Sous **Paramètres**, sélectionnez l’option **Quotidien** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script s’exécute tous les jours à la même heure spécifiée.

    2. Sous **Paramètres avancés**, vérifiez que la case **Activé est cochée** .

    3. Sélectionnez **OK**.

7. Sélectionnez l’onglet **Actions** , sélectionnez **Nouveau**, puis procédez comme suit :

   ![Paramètres d’action pour créer une tâche planifiée pour le script de connecteur épique.](../media/EpicConnectorScheduleTask1.png)

    1. Dans la liste déroulante **Action** , vérifiez que **l’option Démarrer un programme** est sélectionnée.

    2. Dans la zone **Programme/script** , sélectionnez **Parcourir**, puis accédez à l’emplacement suivant et sélectionnez-le afin que le chemin d’accès s’affiche dans la zone : C:.0.exe.

    3. Dans la zone **Ajouter des arguments (facultatif),** collez la même commande de script que celle que vous avez exécutée à l’étape 4. Par exemple, `.\EpicConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Epic\audit\records.txt"`

    4. Dans la zone **Démarrer dans (facultatif),** collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple, C:\Epic\audit.

    5. Sélectionnez **OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **Créer une tâche** , sélectionnez **OK** pour enregistrer la tâche planifiée. Vous serez peut-être invité à entrer les informations d’identification de votre compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche pour le script de connecteur de soins de santé s’affiche dans la bibliothèque du planificateur de tâches.](../media/EpicConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script a été exécuté et la prochaine fois qu’il est planifié pour s’exécuter sont affichés. Vous pouvez double-sélectionner la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script a été exécuté sur la page volante du connecteur Epic correspondant dans le centre de conformité.
