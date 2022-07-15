---
title: Configurer un connecteur pour importer des données de badging physiques
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données du système de badging physique de leur organisation vers Microsoft 365. Cela vous permet d’utiliser ces données dans les stratégies de gestion des risques internes pour vous aider à détecter l’accès à vos bâtiments physiques par des utilisateurs spécifiques qui peuvent indiquer une menace interne possible pour votre organisation.
ms.openlocfilehash: e34706e7fc6be5d813d718e0d927859ca91d9ee8
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823106"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Configurer un connecteur pour importer des données de badging physiques (préversion)

Vous pouvez configurer un connecteur de données dans le portail de conformité Microsoft Purview pour importer des données de badging physiques, telles que les événements d’accès physique bruts de l’employé ou les alarmes d’accès physique générées par le système de badging de votre organisation. Des exemples de points d’accès physiques sont une entrée d’un bâtiment ou une entrée dans une salle de serveur ou un centre de données. Les données de badging physiques peuvent être utilisées par la [solution de gestion des risques internes](insider-risk-management.md) Microsoft 365 pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation.

La configuration d’un connecteur de badging physique se compose des tâches suivantes :

- Création d’une application dans Azure Active Directory (Azure AD) pour accéder à un point de terminaison d’API qui accepte une charge utile JSON qui contient des données de badging physiques.

- Création de la charge utile JSON avec un schéma défini par le connecteur de données de badging physique.

- Création d’un connecteur de données de badging physique dans le portail de conformité.

- Exécution d’un script pour envoyer (push) les données de badging physiques au point de terminaison de l’API.

- Si vous le souhaitez, vous pouvez planifier l’exécution automatique du script pour importer des données actuellement incorrectes physiques.

Si vous souhaitez participer à la préversion, contactez l’équipe à dcfeedback@microsoft.com.

## <a name="before-you-set-up-the-connector"></a>Avant de configurer le connecteur

- L’utilisateur qui crée le connecteur de badging physique à l’étape 3 doit disposer du rôle de Administration du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Le rôle Administration connecteur de données n’est actuellement pas pris en charge dans les environnements US Government GCC High et DoD. Par conséquent, l’utilisateur qui crée le connecteur RH dans les environnements GCC High et DoD doit se voir attribuer le rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle d’exportation d’importation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, consultez les sections [Créer des groupes de rôles](/Exchange/permissions-exo/role-groups#create-role-groups) ou [Modifier des groupes de rôles](/Exchange/permissions-exo/role-groups#modify-role-groups) dans l’article « Gérer les groupes de rôles dans Exchange Online ».

- Vous devez déterminer comment récupérer ou exporter les données à partir du système de badging physique de votre organisation (quotidiennement) et créer un fichier JSON décrit à l’étape 2. Le script que vous exécutez à l’étape 4 envoie (push) les données du fichier JSON au point de terminaison de l’API.

- L’exemple de script que vous exécutez à l’étape 4 envoie (push) les données de badging physiques du fichier JSON à l’API du connecteur afin qu’elles puissent être utilisées par la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

- Ce connecteur est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à créer et à inscrire une application dans Azure Active Directory (Azure AD). L’application correspond au connecteur de badging physique que vous créez à l’étape 3. La création de cette application permet à Azure AD d’authentifier la demande Push pour la charge utile JSON contenant des données de mauvais traitement physiques. Lors de la création de cette application Azure AD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID d’application Azure AD (également appelé *ID d’application* ou *ID client*)

- Secret d’application Azure AD (également appelé *clé secrète client*)

- ID de locataire (également appelé *ID de répertoire*)

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, consultez [Inscrire une application auprès du Plateforme d'identités Microsoft](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Étape 2 : Préparer un fichier JSON avec des données de badging physiques

L’étape suivante consiste à créer un fichier JSON qui contient des informations sur les données d’accès physique des employés. Comme expliqué dans la section avant de commencer, vous devez déterminer comment générer ce fichier JSON à partir du système de badging physique de votre organisation.

Le fichier JSON doit être conforme à la définition de schéma requise par le connecteur. Voici les descriptions des propriétés de schéma requises pour le fichier JSON :

|Propriété|Description|Type de données|
|---|---|---|
|UserId|Un employé peut avoir plusieurs identités numériques sur les systèmes. L’ID Azure AD doit déjà être résolu par le système source pour l’entrée.|UPN ou adresse e-mail|
|AssetId|ID de référence de la ressource physique ou du point d’accès physique.|Chaîne alphanumérique|
|AssetName|Nom convivial de la ressource physique ou du point d’accès physique.|Chaîne alphanumérique|
|EventTime|Horodatage de l’accès.|Date et heure, au format UTC|
|AccessStatus|Valeur de `Success` ou `Failed`|String|
|||

Voici un exemple de fichier JSON conforme au schéma requis :

```json
[
    {
        "UserId":"sarad@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T01:57:49",
        "AccessStatus":"Failed"
    },
    {
        "UserId":"pilarp@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T02:57:49",
        "AccessStatus":"Success"
    }
]
```

Vous pouvez également télécharger la définition de schéma suivante pour le fichier JSON à partir de l’Assistant lorsque vous créez le connecteur de badging physique à l’étape 3.

```text
{
   "title" : "Physical Badging Signals",
   "description" : "Access signals from physical badging systems",
   "DataType" : {
      "description" : "Identify what is the data type for input signal",
      "type" : "string",
   },
   "type" : "object",
   "properties": {
      "UserId" : {
         "description" : "Unique identifier AAD Id resolved by the source system",
         "type" : "string",
      },
      "AssetId": {
         "description" : "Unique ID of the physical asset/access point",
         "type" : "string",
      },
      "AssetName": {
         "description" : "friendly name of the physical asset/access point",
         "type" : "string",
      },
      "EventTime" : {
         "description" : "timestamp of access",
         "type" : "string",
      },
      "AccessStatus" : {
         "description" : "what was the status of access attempt - Success/Failed",
         "type" : "string",
      },
   }
   "required" : ["UserId", "AssetId", "EventTime" "AccessStatus"]
}
```

## <a name="step-3-create-the-physical-badging-connector"></a>Étape 3 : Créer le connecteur de badging physique

L’étape suivante consiste à créer un connecteur de mise en échec physique dans le portail de conformité. Après avoir exécuté le script à l’étape 4, le fichier JSON que vous avez créé à l’étape 3 est traité et envoyé (push) au point de terminaison d’API que vous avez configuré à l’étape 1. Dans cette étape, veillez à copier le JobId généré lorsque vous créez le connecteur. Vous allez utiliser JobId lorsque vous exécutez le script.

1. Accédez au portail de conformité, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Connecteurs de données**</a>.

2. Dans la page **Connecteurs de données** sous **Échec physique**, cliquez sur **Affichage**.

3. Dans la page **De badging physique** , cliquez sur **Ajouter un connecteur**.

4. Dans la page **Informations d’identification d’authentification** , procédez comme suit, puis cliquez sur **Suivant** :

   1. Tapez ou collez l’ID d’application Azure AD pour l’application Azure que vous avez créée à l’étape 1.

   2. Téléchargez l’exemple de schéma de votre référence pour créer le fichier JSON.

   3. Tapez un nom unique pour le connecteur de badging physique.

5. Dans la page **Révision** , passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

6. Une page d’état s’affiche pour confirmer la création du connecteur. Cette page contient également l’ID de travail. Vous pouvez copier l’ID du travail à partir de cette page ou de la page de menu volant du connecteur. Vous avez besoin de cet ID de travail lors de l’exécution du script.

   La page d’état contient également un lien vers le script. Reportez-vous à ce script pour comprendre comment publier le fichier JSON sur le point de terminaison de l’API.

7. Cliquez sur **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous l’onglet **Connecteurs** .

8. Cliquez sur le connecteur de badging physique que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Étape 4 : Exécutez le script pour PUBLIER votre fichier JSON contenant des données de mauvais fonctionnement physiques

L’étape suivante de la configuration d’un connecteur de badging physique consiste à exécuter un script qui envoie (push) les données de badging physiques dans le fichier JSON (que vous avez créé à l’étape 2) au point de terminaison d’API que vous avez créé à l’étape 1. Nous fournissons un exemple de script pour votre référence et vous pouvez choisir de l’utiliser ou de créer votre propre script pour publier le fichier JSON sur le point de terminaison de l’API.

Après avoir exécuté le script, le fichier JSON contenant les données de badging physiques est envoyé à votre organisation Microsoft 365, où elle est accessible par la solution de gestion des risques internes. Nous vous recommandons de publier des données de badging physiques quotidiennement. Pour ce faire, vous pouvez automatiser le processus de génération du fichier JSON tous les jours à partir de votre système de badging physique, puis planifier le script pour envoyer (push) les données.

> [!NOTE]
> Le nombre maximal d’enregistrements dans le fichier JSON qui peuvent être traités par l’API est de 50 000 enregistrements.

1. Accédez à [ce site GitHub](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) pour accéder à l’exemple de script.

2. Cliquez sur le bouton **Brut** pour afficher le script en mode texte

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Si nécessaire, modifiez l’exemple de script pour votre organisation.

5. Enregistrez le fichier texte en tant que fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de .ps1 ; par exemple, PhysicalBadging.ps1.

6. Ouvrez une invite de commandes sur votre ordinateur local, puis accédez au répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour envoyer (push) les données de badging physiques dans le fichier JSON vers le cloud Microsoft ; par exemple :

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   |Paramètre|Description|
   |---|---|
   |tenantId|Il s’agit de l’ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir le tenantId pour votre organisation dans le panneau **Vue d’ensemble** du Centre d’administration Azure AD. Cela permet d’identifier votre organisation.|
   |appId|Il s’agit de l’ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Azure AD l’utilise pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365.|
   |appSecret|Il s’agit du secret d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est également utilisé pour l’authentification.|
   |jobId|Il s’agit de l’ID de travail du connecteur de badging physique que vous avez créé à l’étape 3. Cela permet d’associer les données de badging physiques envoyées au cloud Microsoft avec le connecteur de badging physique.|
   |JsonFilePath|Il s’agit du chemin d’accès du fichier JSON que vous avez créé à l’étape 2 sur l’ordinateur local (celui que vous utilisez pour exécuter le script). Ce fichier doit suivre l’exemple de schéma décrit à l’étape 3.|
   |||

   Voici un exemple de syntaxe pour le script de connecteur de badging physique utilisant des valeurs réelles pour chaque paramètre :

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Si le chargement réussit, le script affiche le message **De réussite** du chargement.

   Si vous avez plusieurs fichiers JSON, vous devez exécuter le script pour chaque fichier.

> [!NOTE]
> Vous pouvez également choisir d’envoyer (push) les données de badging physiques au point de terminaison de l’API par d’autres méthodes que l’exécution du script précédent. Par exemple, voici un exemple d’utilisation de Postman pour envoyer vos données au point de terminaison de l’API.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Étape 5 : Surveiller le connecteur de mise en échec physique

Une fois que vous avez créé le connecteur de badging physique et envoyé (push) vos données de badging physiques, vous pouvez afficher le connecteur et charger l’état dans le portail de conformité. Si vous planifiez l’exécution automatique du script régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez au portail de conformité, puis sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Connecteurs de données**</a>.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur de badging physique pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

   ![Page de menu volant d’état pour le connecteur de badging physique.](..\media\PhysicalBadgingStatusFlyout.png)

3. Sous **Dernière importation**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque exécution du script et le chargement des données du fichier JSON dans le cloud Microsoft.

   ![Le fichier journal du connecteur de badging physique affiche le nombre d’objets du fichier JSON qui ont été chargés.](..\media\PhysicalBadgingConnectorLogFile.png)

   Le champ **RecordsSaved** indique le nombre d’enregistrements dans le fichier JSON qui ont été chargés. Par exemple, si le fichier JSON contient quatre enregistrements, la valeur des champs **RecordsSaved** est 4 si le script a correctement chargé tous les enregistrements dans le fichier JSON. Le champ **RecordsSkipped** indique le nombre d’enregistrements du fichier JSON qui ont été ignorés. Avant de charger des enregistrements dans le fichier JSON, les ID Email des enregistrements sont validés. Tout enregistrement avec un ID de Email non valide est ignoré et l’ID de Email correspondant s’affiche dans le champ **EmailIdsNotSaved**

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes de l’étape 4 pour l’exécuter.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécution automatique du script

Pour vous assurer que les dernières données de badging physiques de votre organisation sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécution automatique du script de façon périodique, par exemple une fois par jour. Cela nécessite également que vous mettiez à jour les données de mise à jour physique vers le fichier JSON selon une planification similaire (si ce n’est pas la même) afin qu’elles contiennent les informations les plus récentes sur les employés qui quittent votre organisation. L’objectif est de charger les données de badging physiques les plus actuelles afin que le connecteur de badging physique puisse les rendre disponibles pour la solution de gestion des risques internes.

Vous pouvez utiliser l’application Planificateur de tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton Démarrer de Windows, puis **tapez** **Planificateur de tâches**.

2. Cliquez sur l’application **Du planificateur de tâches** pour l’ouvrir.

3. Dans la section **Actions** , cliquez sur **Créer une tâche**.

4. Sous l’onglet **Général** , tapez un nom descriptif pour la tâche planifiée ; par exemple, **script de connecteur de badging physique**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité**, procédez comme suit :

   1. Déterminez si vous devez exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou si vous l’exécutez lorsque vous êtes connecté ou non.

   2. Vérifiez que la case à cocher **Exécuter avec les privilèges les plus élevés** est cochée.

6. Sélectionnez l’onglet Déclencheurs, cliquez sur **Nouveau**, puis effectuez les **opérations suivantes** :

   1. Sous **Paramètres**, sélectionnez l’option **Quotidienne** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script s’exécute tous les jours à la même heure spécifiée.

   2. Sous **Paramètres avancés**, vérifiez que la case à cocher **Activé** est cochée.

   3. Cliquez sur **OK**.

7. Sélectionnez l’onglet **Actions** , cliquez sur **Nouveau**, puis effectuez les opérations suivantes :

   ![Paramètres d’action pour créer une tâche planifiée pour le script de connecteur de badging physique.](..\media\SchedulePhysicalBadgingScript1.png)

   1. Dans la liste déroulante **Action** , vérifiez que **l’option Démarrer un programme** est sélectionnée.

   2. Dans la zone **Programme/script** , cliquez sur **Parcourir, accédez** à l’emplacement suivant et sélectionnez-le pour que le chemin d’accès s’affiche dans la zone : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. Dans la zone **Ajouter des arguments (facultatif),** collez la commande de script que vous avez exécutée à l’étape 4. Par exemple, .\PhysicalBadging.ps1-tenantId « d5723623-11cf-4e2e-b5a5-01d1506273g9 » -appId « c12823b7-b55a-4989-faba-02de41bb97c3 » -appSecret « MNubVGbcQDkGCnn » -jobId « e081f4f4-3831-48d6-7bb3-fcfab1581458 » -jsonFilePath « C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json »

   4. Dans la zone **Démarrer (facultatif),** collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple, C:\Users\contosoadmin\Desktop\Scripts.

   5. Cliquez sur **Ok** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **Créer une tâche** , cliquez sur **Ok** pour enregistrer la tâche planifiée. Vous pouvez être invité à entrer les informations d’identification de votre compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche s’affiche dans la bibliothèque du planificateur de tâches.](..\media\SchedulePhysicalBadgingScript2.png)

La dernière fois que le script s’est exécuté et la prochaine fois qu’il est planifié pour s’exécuter s’affiche. Vous pouvez double-cliquer sur la tâche pour la modifier.

Vous pouvez également vérifier la dernière fois que le script s’est exécuté sur la page de menu volant du connecteur de badging physique correspondant dans le centre de conformité.
