---
title: Configurer un connecteur pour importer des données d’audit de santé génériques
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 07/15/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données d’enregistrements de santé électroniques (DSE) à partir de leur système de santé vers Microsoft 365. Cela vous permet d’utiliser les données DSE dans les stratégies de gestion des risques internes pour vous aider à détecter l’activité d’accès non autorisé aux données des patients par vos employés.
ms.openlocfilehash: 00d0419a2db39642b87797254f89dc1c721b69e2
ms.sourcegitcommit: 61df6377a6185a8b55e668cfb81adbd8462a9cce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2022
ms.locfileid: "67071522"
---
# <a name="set-up-a-connector-to-import-healthcare-ehr-audit-data-preview"></a>Configurer un connecteur pour importer des données d’audit DSE de santé (préversion)

Vous pouvez configurer un connecteur de données dans le portail de conformité Microsoft Purview pour importer des données d’audit pour l’activité des utilisateurs dans le système DSE (Electronic Healthcare Records) de votre organisation. Les données d’audit de votre système de DSE de santé incluent des données relatives aux événements liés à l’accès aux dossiers de santé d’un patient. Les données d’audit DSE de santé peuvent être utilisées par la solution Microsoft Purview [Insider Risk Management](insider-risk-management.md) pour protéger votre organisation contre tout accès non autorisé aux informations sur les patients.

La configuration d’un connecteur Healthcare se compose des tâches suivantes :

- Création d’une application dans Azure Active Directory (Azure AD) pour accéder à un point de terminaison d’API qui accepte un fichier texte séparé par des onglets contenant des données d’audit de DSE de santé.

- Création d’un fichier texte avec tous les champs requis tels que définis dans le schéma du connecteur.

- Création d’une instance de connecteur Healthcare dans le portail de conformité.

- Exécution d’un script pour envoyer (push) les données d’audit DSE de santé au point de terminaison de l’API.

- Vous pouvez également planifier l’exécution automatique du script pour importer les données d’audit.

Si vous souhaitez participer à la préversion, contactez l’équipe à dcfeedback@microsoft.com.

## <a name="before-you-set-up-the-connector"></a>Avant de configurer le connecteur

- L’utilisateur qui crée le connecteur Healthcare à l’étape 3 doit se faire attribuer le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Vous devez déterminer comment récupérer ou exporter les données à partir du système de DSE de santé de votre organisation (quotidiennement) et créer un fichier texte décrit à l’étape 2. Le script que vous exécutez à l’étape 4 envoie (push) les données du fichier texte au point de terminaison de l’API.

- L’exemple de script que vous exécutez à l’étape 4 envoie (push) les données d’audit DSE des soins de santé du fichier texte à l’API du connecteur afin qu’elles puissent être utilisées par la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à créer et à inscrire une application dans Azure Active Directory (Azure AD). L’application correspond au connecteur Healthcare que vous créez à l’étape 3. La création de cette application permet à Azure AD d’authentifier la demande Push pour le fichier texte contenant des données d’audit DSE de santé. Lors de la création de cette application Azure AD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID d’application Azure AD (également appelé *ID d’application* ou *ID client*)

- Secret d’application Azure AD (également appelé *clé secrète client*)

- ID de locataire (également appelé *ID de répertoire*)

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, consultez [Inscrire une application auprès du Plateforme d'identités Microsoft](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-healthcare-ehr-auditing-data"></a>Étape 2 : Préparer un fichier texte avec des données d’audit de DSE de santé

L’étape suivante consiste à créer un fichier texte qui contient des informations sur l’accès des employés aux dossiers de santé des patients dans le système de DSE de votre organisation. Comme expliqué précédemment, vous devez déterminer comment générer ce fichier texte à partir de votre système de DSE de santé. Le flux de travail du connecteur Healthcare nécessite un fichier texte avec des valeurs séparées par des tabulations pour mapper ces données dans le fichier texte avec le schéma de connecteur requis. Le format de fichier pris en charge est un fichier texte séparé par une virgule (.csv), un canal (.psv) ou un onglet (.tsv).

> [!NOTE]
> La taille maximale du fichier texte qui contient les données d’audit est de 3 Go. Le nombre maximal de lignes est de 5 millions. Veillez également à inclure uniquement les données d’audit pertinentes de votre système de DSE de santé.

Le tableau suivant répertorie les champs qui sont nécessaires pour activer les scénarios de gestion des risques internes. Un sous-ensemble de ces champs est obligatoire. Ces champs sont mis en surbrillance avec un astérisque (*). Si l’un des champs obligatoires est manquant dans le fichier texte, le fichier n’est pas validé et les données du fichier ne sont pas importées.

|Champ|Catégorie|
|:----|:----------|
| Nom de *l’événement heure<br/>* de création<br/>ID de station de travail<br/>Section d’événements<br/>Catégorie de l'événement |Ces champs sont utilisés pour identifier les événements d’activité d’accès dans votre système de DSE de santé.|
| Patient Reg Id<br/>Nom du *patient prénom patient prénom <br/>patient nom de famille<br/>* <br/>Ligne d’adresse du patient 1* <br/>Ligne d’adresse du patient 2<br/>Ville du patient* <br/>Code postal du patient*  <br/>État du patient <br/>Pays du patient <br/>Service des patients              | Ces champs sont utilisés pour identifier les informations de profil des patients.|
| Raison de l’accès restreint*<br/> Commentaire d’accès restreint | Ces champs sont utilisés pour identifier l’accès aux enregistrements restreints.|
| Email Address (UPN) ou SamAccountName*<br/>Nom d’utilisateur de l’employé <br/> ID d’employé <br/> Nom de l’employé <sup>1</sup> <br/> Prénom de l’employé <sup>1</sup> | Ces champs sont utilisés pour identifier les informations de profil d’employé pour la correspondance d’adresse et de nom requises pour déterminer l’accès aux enregistrements famille/voisin/employé. |
|||

> [!NOTE] 
> <sup>1</sup> Ce champ n’est peut-être pas disponible par défaut dans votre système de DSE de santé. Vous devez configurer l’exportation pour vous assurer que le fichier texte contient ce champ.

## <a name="step-3-create-the-healthcare-connector"></a>Étape 3 : Créer le connecteur Healthcare

L’étape suivante consiste à créer un connecteur Healthcare dans le portail de conformité. Après avoir exécuté le script à l’étape 4, le fichier texte que vous avez créé à l’étape 2 est traité et envoyé (push) au point de terminaison d’API que vous avez configuré à l’étape 1. Dans cette étape, veillez à copier le JobId généré lorsque vous créez le connecteur. Vous allez utiliser JobId lorsque vous exécutez le script.

1. Accédez, <https://compliance.microsoft.com> puis cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Sous l’onglet **Vue d’ensemble**, cliquez sur **Santé (préversion).**

3. Dans la page **Santé (préversion),** cliquez sur **Ajouter un connecteur**.

4. Acceptez les conditions d’utilisation.

5. Dans la page **Informations d’identification d’authentification** , procédez comme suit, puis cliquez sur **Suivant** :

    1. Tapez ou collez l’ID d’application Azure AD pour l’application Azure que vous avez créée à l’étape 1.

    2. Tapez un nom pour le connecteur de soins de santé.

6. Dans la page méthode **de mappage de fichiers** , sélectionnez l’une des options suivantes, puis cliquez sur **Suivant**.

   - **Chargez un exemple de fichier**. Si vous sélectionnez cette option, cliquez sur **Charger l’exemple de fichier** pour charger le fichier que vous avez préparé à l’étape 2. Cette option vous permet de sélectionner rapidement les noms de colonnes dans votre fichier texte dans une liste déroulante pour mapper les colonnes au schéma requis pour le connecteur de soins de santé. 

    Ou

   - **Fournissez manuellement les détails du mappage**. Si vous sélectionnez cette option, vous devez taper le nom des colonnes de votre fichier texte pour mapper les colonnes au schéma requis pour le connecteur de soins de santé.

7. Dans la page de détails du mappage de fichiers, effectuez l’une des **opérations suivantes** , selon que vous avez chargé ou non un exemple de fichier à l’étape précédente :

   - Utilisez les listes déroulantes pour mapper les colonnes de l’exemple de fichier à chaque champ requis pour le connecteur de soins de santé.

    Ou

   - Pour chaque champ, tapez le nom de colonne à partir du fichier que vous avez préparé à l’étape 2 qui correspond au champ du connecteur de soins de santé.

8. Dans la page **Révision** , passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Une page d’état s’affiche pour confirmer la création du connecteur. Cette page contient deux éléments importants dont vous avez besoin pour effectuer l’étape suivante afin d’exécuter l’exemple de script pour charger vos données d’audit DSE de santé.

    - **ID du travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez la copier à partir de cette page ou de la page de menu volant du connecteur.

    - **Lien vers un exemple de script.** Cliquez sur le lien **ci-après** pour accéder au site GitHub pour accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Laissez cette fenêtre ouverte pour pouvoir copier le script à l’étape 4. Vous pouvez également marquer la destination ou copier l’URL pour pouvoir y accéder à nouveau lorsque vous exécutez le script. Ce lien est également disponible sur la page de menu volant du connecteur.

9. Cliquez sur **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous l’onglet **Connecteurs** .

10. Cliquez sur le connecteur Healthcare que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

Si vous ne l’avez pas déjà fait, vous pouvez copier les valeurs de **l’ID de Azure App** et de **l’ID de travail du connecteur**. Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page de menu volant (ou le télécharger à l’aide du lien à l’étape suivante).)

Vous pouvez également cliquer sur **Modifier** pour modifier l’ID Azure App ou les noms d’en-tête de colonne que vous avez définis sur la page **de mappage de fichiers**.

## <a name="step-4-run-the-sample-script-to-upload-your-healthcare-ehr-auditing-data"></a>Étape 4 : Exécuter l’exemple de script pour charger vos données d’audit de DSE de santé

La dernière étape de la configuration d’un connecteur Healthcare consiste à exécuter un exemple de script qui charge les données d’audit DSE de santé dans le fichier texte (que vous avez créé à l’étape 1) dans le cloud Microsoft. Plus précisément, le script charge les données dans le connecteur Healthcare. Après avoir exécuté le script, le connecteur de soins de santé que vous avez créé à l’étape 3 importe les données d’audit de DSE dans votre organisation Microsoft 365, où elles sont accessibles par d’autres outils de conformité, tels que la solution de gestion des risques Insider. Après avoir exécuté le script, envisagez de planifier une tâche pour l’exécuter automatiquement tous les jours afin que les données d’arrêt des employés les plus actuelles soient chargées dans le cloud Microsoft. Voir [(Facultatif) Étape 6 : Planifier l’exécution automatique du script](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Comme indiqué précédemment, la taille maximale du fichier texte qui contient les données d’audit est de 3 Go. Le nombre maximal de lignes est de 5 millions. Le script que vous exécutez dans cette étape prend environ 30 à 40 minutes pour importer les données d’audit à partir de fichiers texte volumineux. En outre, le script divise les fichiers texte volumineux en blocs plus petits de 100 000 lignes, puis importe ces blocs de manière séquentielle.

1. Accédez à la fenêtre que vous avez laissée ouverte à l’étape précédente pour accéder au site GitHub avec l’exemple de script. Vous pouvez également ouvrir le site avec signet ou utiliser l’URL que vous avez copiée. Vous pouvez également accéder au script [ici](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Cliquez sur le bouton **Brut** pour afficher le script en mode texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Si nécessaire, modifiez l’exemple de script pour votre organisation.

5. Enregistrez le fichier texte en tant que fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de `.ps1`; par exemple, `HealthcareConnector.ps1`.

6. Ouvrez une invite de commandes sur votre ordinateur local, puis accédez au répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour charger les données d’audit des soins de santé dans le fichier texte dans le cloud Microsoft ; par exemple :

   ```powershell
   .\HealthcareConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

|Paramètre  |Description|
|:----------|:----------|
|tenantId|Il s’agit de l’ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir l’ID de locataire de votre organisation dans le panneau **Vue d’ensemble** du Centre d’administration Azure AD. Cela permet d’identifier votre organisation.|
|appId|Il s’agit de l’ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Azure AD l’utilise pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365.|
|appSecret|Il s’agit du secret d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Cela est également utilisé pour l’authentification.|
|jobId|Il s’agit de l’ID de travail du connecteur Healthcare que vous avez créé à l’étape 3. Cela permet d’associer les données d’audit de DSE de santé chargées dans le cloud Microsoft au connecteur Healthcare.|
|Filepath|Il s’agit du chemin d’accès au fichier texte (stocké sur le même système que le script) que vous avez créé à l’étape 2. Essayez d’éviter les espaces dans le chemin d’accès au fichier ; sinon, utilisez des guillemets simples.|
|||

Voici un exemple de syntaxe pour le script de connecteur Healthcare utilisant des valeurs réelles pour chaque paramètre :

```powershell
.\HealthcareConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\healthcare_audit_records.csv'
```

Si le chargement réussit, le script affiche le message **De réussite** du chargement.

> [!NOTE]
> Si vous rencontrez des problèmes lors de l’exécution de la commande précédente en raison de stratégies d’exécution, consultez [À propos des stratégies d’exécution](/powershell/module/microsoft.powershell.core/about/about_execution_policies) et [de Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des conseils sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-healthcare-connector"></a>Étape 5 : Surveiller le connecteur Healthcare

Après avoir créé le connecteur Healthcare et envoyé (push) vos données d’audit EHR, vous pouvez afficher le connecteur et charger l’état dans le portail de conformité. Si vous planifiez l’exécution automatique du script régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez et <https://compliance.microsoft.com> cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur Healthcare pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **Dernière importation**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque exécution du script et le chargement des données du fichier texte dans le cloud Microsoft.

    Le `RecordsSaved` champ indique le nombre de lignes dans le fichier texte chargé. Par exemple, si le fichier texte contient quatre lignes, la valeur des `RecordsSaved` champs est 4, si le script a correctement chargé toutes les lignes du fichier texte.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes pour exécuter le script.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécution automatique du script

Pour vous assurer que les données d’audit les plus récentes de votre système de DSE de santé sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécution automatique du script quotidiennement. Cela nécessite également que vous mettiez à jour les données d’audit de DSE dans le même fichier texte selon une planification similaire (si ce n’est pas la même) afin qu’elle contienne les informations les plus récentes sur les activités d’accès aux dossiers des patients par vos employés. L’objectif est de charger les données d’audit les plus actuelles afin que le connecteur de soins de santé puisse les mettre à la disposition de la solution de gestion des risques internes.

Vous pouvez utiliser l’application Planificateur de tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton Démarrer de Windows, puis **tapez** **Planificateur de tâches**.

2. Cliquez sur l’application **Du planificateur de tâches** pour l’ouvrir.

3. Dans la section **Actions** , cliquez sur **Créer une tâche**.

4. Sous l’onglet **Général** , tapez un nom descriptif pour la tâche planifiée ; par exemple, **le script du connecteur Healthcare**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité**, procédez comme suit :

    1. Déterminez si vous devez exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou si vous l’exécutez lorsque vous êtes connecté ou non.

    2. Vérifiez que la case à cocher **Exécuter avec les privilèges les plus élevés** est cochée.

6. Sélectionnez l’onglet Déclencheurs, cliquez sur **Nouveau**, puis effectuez les **opérations suivantes** :

    1. Sous **Paramètres**, sélectionnez l’option **Quotidienne** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script s’exécute tous les jours à la même heure spécifiée.

    2. Sous **Paramètres avancés**, vérifiez que la case à cocher **Activé** est cochée.

    3. Cliquez sur **OK**.

7. Sélectionnez l’onglet **Actions** , cliquez sur **Nouveau**, puis effectuez les opérations suivantes :

   ![Paramètres d’action pour créer une tâche planifiée pour le script du connecteur de soins de santé.](../media/GenericHealthCareConnectorScheduleTask1.png)

    1. Dans la liste déroulante **Action** , vérifiez que **l’option Démarrer un programme** est sélectionnée.

    2. Dans la zone **Programme/script** , cliquez sur **Parcourir, accédez** à l’emplacement suivant et sélectionnez-le pour que le chemin d’accès s’affiche dans la zone : C:.0.exe.

    3. Dans la zone **Ajouter des arguments (facultatif),** collez la commande de script que vous avez exécutée à l’étape 4. Par exemple, `.\HealthcareConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Healthcare\audit\records.txt"`

    4. Dans la zone **Démarrer (facultatif),** collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple, C:\Healthcare\audit.

    5. Cliquez sur **Ok** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **Créer une tâche** , cliquez sur **Ok** pour enregistrer la tâche planifiée. Vous pouvez être invité à entrer les informations d’identification de votre compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche du script du connecteur de soins de santé s’affiche dans la bibliothèque du planificateur de tâches.](../media/HealthcareConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script s’est exécuté et la prochaine fois qu’il est planifié pour s’exécuter s’affiche. Vous pouvez double-cliquer sur la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script s’est exécuté sur la page de menu volant du connecteur Healthcare correspondant dans le centre de conformité.
