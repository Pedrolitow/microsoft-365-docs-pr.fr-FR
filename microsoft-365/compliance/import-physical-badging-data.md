---
title: Configurer un connecteur pour importer des données de mauvaise qualité physiques
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
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données à partir du système de mauvaise gestion physique de leur organisation Microsoft 365. Cela vous permet d’utiliser ces données dans les stratégies de gestion des risques internes pour vous aider à détecter l’accès à vos bâtiments physiques par des utilisateurs spécifiques qui peuvent indiquer une menace interne possible pour votre organisation.
ms.openlocfilehash: 800614ef38e065027238d32bf877a059e2022378a1a86b2f33c6f11f3827de2a
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53895430"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Configurer un connecteur pour importer des données de mauvaise qualité physiques (aperçu)

Vous pouvez configurer un connecteur de données dans l’Centre de conformité Microsoft 365 pour importer des données de mauvaise qualité physiques, telles que les événements d’accès physique bruts de l’employé ou les alarmes d’accès physique générées par le système de badging de votre organisation. Une entrée d’un bâtiment ou d’une entrée de salle de serveur ou de centre de données est un exemple de points d’accès physique. Les données de mauvais traitement physique peuvent être utilisées par la [solution](insider-risk-management.md) de gestion des risques internes Microsoft 365 pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation.

La configuration d’un connecteur de badging physique comprend les tâches suivantes :

- Création d’une application Azure Active Directory (Azure AD) pour accéder à un point de terminaison d’API qui accepte une charge utile JSON qui contient des données de mauvaise gestion physiques.

- Création de la charge utile JSON avec un schéma défini par un connecteur de données de badging physique.

- Création d’un connecteur de données de badging physique dans le Centre de conformité Microsoft 365.

- Exécution d’un script pour pousser les données de badging physique au point de terminaison de l’API.

- Éventuellement, planifier l’exécuter automatiquement pour importer les données de mauvaise qualité physiques.

## <a name="before-you-set-up-the-connector"></a>Avant de configurer le connecteur

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée le connecteur de badging physique à l’étape 3 Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

- Vous devez déterminer comment récupérer ou exporter les données à partir du système de mauvaise gestion physique de votre organisation (quotidiennement) et créer un fichier JSON décrit à l’étape 2. Le script que vous exécutez à l’étape 4 va pousser les données du fichier JSON vers le point de terminaison de l’API.

- L’exemple de script que vous exécutez à l’étape 4 pousse les données de badging physiques du fichier JSON vers l’API du connecteur afin qu’elles soient utilisées par la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à créer et inscrire une nouvelle application dans Azure Active Directory (Azure AD). L’application correspond au connecteur de badging physique que vous créez à l’étape 3. La création de cette application permettra à Azure AD d’authentifier la demande Push pour la charge utile JSON contenant des données de badging physiques. Lors de la création de cette application Azure AD, n’oubliez pas d’enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID d’application Azure AD (également appelé *ID* d’application ou *ID client)*

- Secret d’application Azure AD (également appelé *secret client)*

- ID de client (également appelé *ID d’annuaire)*

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, voir Inscrire une application avec le [Plateforme d’identités Microsoft](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Étape 2 : Préparer un fichier JSON avec des données de mauvaise qualité physiques

L’étape suivante consiste à créer un fichier JSON qui contient des informations sur les données d’accès physique des employés. Comme expliqué dans la section avant de commencer, vous devez déterminer comment générer ce fichier JSON à partir du système de badging physique de votre organisation.

Le fichier JSON doit être conforme à la définition de schéma requise par le connecteur. Voici les descriptions des propriétés de schéma requises pour le fichier JSON :

|Propriété|Description|Type de données|
|---|---|---|
|UserId|Un employé peut avoir plusieurs identités numériques sur les systèmes. L’ID Azure AD doit déjà être résolu par le système source pour l’entrée.|UPN ou adresse de messagerie|
|AssetId|ID de référence du bien physique ou du point d’accès physique.|Chaîne alphanumérique|
|AssetName|Nom convivial du bien physique ou du point d’accès physique.|Chaîne alphanumérique|
|EventTime|Horodaté de l’accès.|Date et heure, au format UTC|
|AccessStatus|Valeur de `Success` ou `Failed`|Chaîne|
|||

Voici un exemple de fichier JSON conforme au schéma requis :

```json
[
    {
        "UserId":"sarad@contoso.com"
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T01:57:49",
        "AccessStatus":"Failed",
    },
    {
        "UserId":"pilarp@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T02:57:49",
        "AccessStatus":"Success",
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

L’étape suivante consiste à créer un connecteur de badging physique dans le Centre de conformité Microsoft 365. Après avoir exécuté le script à l’étape 4, le fichier JSON que vous avez créé à l’étape 3 est traitée et poussée vers le point de terminaison de l’API que vous avez configuré à l’étape 1. Dans cette étape, assurez-vous de copier le JobId généré lorsque vous créez le connecteur. Vous utiliserez JobId lorsque vous exécuterez le script.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors** in the left nav.

2. Dans la page **Connecteurs de données** sous **Badging physique,** cliquez **sur Afficher**.

3. Dans la page **Problèmes physiques,** cliquez sur **Ajouter un connecteur.**

4. Dans la page **Informations d’identification** d’authentification, faites ce qui suit, puis cliquez sur **Suivant**:

   1. Tapez ou collez l’ID d’application Azure AD pour l’application Azure que vous avez créée à l’étape 1.

   2. Téléchargez l’exemple de schéma pour votre référence pour créer le fichier JSON.

   3. Tapez un nom unique pour le connecteur de badging physique.

5. Dans la page **Révision,** examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

6. Une page d’état confirme que le connecteur a été créé. Cette page contient également l’ID de travail. Vous pouvez copier l’ID de travail à partir de cette page ou de la page volante du connecteur. Vous avez besoin de cet ID de travail lors de l’exécution du script.

   La page d’état contient également un lien vers le script. Reportez-vous à ce script pour comprendre comment publier le fichier JSON sur le point de terminaison de l’API.

7. Cliquez sur **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous l’onglet **Connecteurs.**

8. Cliquez sur le connecteur de badging physique que vous avez créé pour afficher la page volante, qui contient des propriétés et d’autres informations sur le connecteur.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Étape 4 : Exécutez le script pour PUBLIER votre fichier JSON contenant des données de mauvaise gestion physiques

L’étape suivante de la configuration d’un connecteur de mauvaise gestion physique consiste à exécuter un script qui placera les données de mauvaise qualité physiques dans le fichier JSON (que vous avez créé à l’étape 2) vers le point de terminaison d’API que vous avez créé à l’étape 1. Nous fournissons un exemple de script pour votre référence et vous pouvez choisir de l’utiliser ou de créer votre propre script pour publier le fichier JSON sur le point de terminaison de l’API.

Après avoir exécuté le script, le fichier JSON contenant les données de mauvaise gestion physiques est dirigé vers votre organisation Microsoft 365 où il est accessible par la solution de gestion des risques internes. Nous vous recommandons de publier quotidiennement des données de mauvaise qualité physiques. Pour ce faire, vous pouvez automatiser le processus de création du fichier JSON tous les jours à partir de votre système de mauvaise gestion physique, puis planifier le script pour la diffusion des données.

> [!NOTE]
> Le nombre maximal d’enregistrements dans le fichier JSON qui peuvent être traitées par l’API est de 50 000.

1. Accédez [à ce site GitHub pour](https://github.com/microsoft/m365-hrconnector-sample-scripts/blob/master/upload_termination_records.ps1) accéder à l’exemple de script.

2. Cliquez sur **le bouton Brut** pour afficher le script en affichage texte

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, si nécessaire.

5. Enregistrez le fichier texte en tant que fichier Windows PowerShell script à l’aide d’un suffixe de nom de fichier .ps1 ; par exemple, PhysicalBadging.ps1.

6. Ouvrez une invite de commandes sur votre ordinateur local et allez dans le répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour pousser les données de mauvaise gestion physiques dans le fichier JSON vers le cloud Microsoft . par exemple :

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations obtenues lors des étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   |Parameter|Description|
   |---|---|
   |tenantId|Il s’agit de l’ID de votre Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir le tenantId de votre organisation dans le panneau **Vue** d’ensemble du Centre d’administration Azure AD. Il est utilisé pour identifier votre organisation.|
   |appId|Il s’agit de l’ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est utilisé par Azure AD pour l’authentification lorsque le script tente d’accéder à Microsoft 365 organisation.|
   |appSecret|Il s’agit de la question secrète de l’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est également utilisé pour l’authentification.|
   |jobId|Il s’agit de l’ID de travail du connecteur de badging physique que vous avez créé à l’étape 3. Il permet d’associer les données de mauvaise gestion physiques qui sont poussées vers le cloud Microsoft au connecteur de badging physique.|
   |JsonFilePath|Il s’agit du chemin d’accès au fichier sur l’ordinateur local (celui que vous utilisez pour exécuter le script) pour le fichier JSON que vous avez créé à l’étape 2. Ce fichier doit suivre l’exemple de schéma décrit à l’étape 3.|
   |||

   Voici un exemple de syntaxe pour le script de connecteur de badging physique utilisant des valeurs réelles pour chaque paramètre :

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Si le téléchargement réussit, le script affiche **l’Télécharger message** Réussite.

   Si vous avez plusieurs fichiers JSON, vous devez exécuter le script pour chaque fichier.

> [!NOTE]
> Vous pouvez également choisir de pousser les données de badging physique au point de terminaison de l’API par d’autres méthodes que l’exécution du script précédent. Par exemple, voici un exemple d’utilisation de Postman pour pousser vos données vers le point de terminaison de l’API.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Étape 5 : Surveiller le connecteur de badging physique

Une fois que vous avez créé le connecteur de badging physique et envoyé vos données de mauvais traitement physiques, vous pouvez afficher le connecteur et l’état de chargement dans le Centre de conformité Microsoft 365. Si vous programmez l’exécuter automatiquement sur une base régulière, vous pouvez également afficher l’état actuel après la dernière fois que le script a été exécuté.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur de badging physique pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

   ![Page de volant d’état pour le connecteur de badging physique](..\media\PhysicalBadgingStatusFlyout.png)

3. Sous **Dernière importation,** cliquez sur le lien **du journal** de téléchargement pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et télécharge les données du fichier CSV dans le cloud Microsoft.

   ![Le fichier journal du connecteur de badging physique affiche les lignes de numéro à partir du fichier JSON qui ont été téléchargées](..\media\PhysicalBadgingConnectorLogFile.png)

   Le **champ RecordsSaved** indique le nombre de lignes dans le fichier CSV téléchargé. Par exemple, si le fichier CSV contient quatre lignes, la valeur des champs **RecordsSaved** est 4, si le script a correctement chargé toutes les lignes du fichier CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes de l’étape 4 pour l’exécuter.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécuter automatiquement

Pour vous assurer que les dernières données de mauvaise gestion physique de votre organisation sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier le script pour qu’il s’exécute automatiquement de manière récurrente, par exemple une fois par jour. Pour ce faire, vous devez également mettre à jour les données de mauvaise gestion physiques dans le fichier JSON selon une planification similaire (si ce n’est pas la même) afin qu’elle contienne les dernières informations sur les employés qui quittent votre organisation. L’objectif est de télécharger les données de mauvaise gestion physiques les plus récentes afin que le connecteur de mauvaise gestion physique puisse les mettre à la disposition de la solution de gestion des risques internes.

Vous pouvez utiliser l’application Planification des tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton Windows **démarrer,** puis tapez Planification **des tâches.**

2. Cliquez sur **l’application De planification des** tâches pour l’ouvrir.

3. Dans la section **Actions,** cliquez sur **Créer une tâche.**

4. Sous **l’onglet** Général, tapez un nom descriptif pour la tâche programmée . par exemple, **script du connecteur de badging physique.** Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité,** faites les actions suivantes :

   1. Déterminez s’il faut exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou l’exécuter lorsque vous êtes connecté ou non.

   2. Assurez-vous que la case à cocher Exécuter avec **les privilèges** les plus élevés est sélectionnée.

6. Sélectionnez **l’onglet Déclencheurs,** cliquez **sur Nouveau,** puis faites les choses suivantes :

   1. Sous **Paramètres**, sélectionnez l’option  Tous les jours, puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script sera tous les jours à la même heure spécifiée.

   2. Sous **Paramètres avancés,** assurez-vous que **la case à** cocher Activée est activée.

   3. Cliquez sur **OK**.

7. Sélectionnez **l’onglet Actions,** cliquez **sur Nouveau,** puis faites les actions suivantes :

   ![Paramètres d’action pour créer une tâche programmée pour le script du connecteur de badging physique](..\media\SchedulePhysicalBadgingScript1.png)

   1. Dans la **liste de** listes d’actions, assurez-vous que démarrer **un programme** est sélectionné.

   2. Dans la **zone Programme/script,** cliquez sur Parcourir, puis accédez à l’emplacement suivant et sélectionnez-le afin que le chemin d’accès s’affiche dans la zone : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe. 

   3. Dans la **zone Ajouter des arguments (facultatif),** collez la même commande de script que celle que vous avez ran à l’étape 4. Par exemple, .\PhysicalBadging.ps1-tenantId « d5723623-11cf-4e2e-b5a5-01d1506273g9 » -appId « c12823b7-b55a-4989-faba-02de41bb97c3 » -appSecret « MNubVGbcQDkGCnn » -jobId « e081f4f4-3831-48d6-7bb3-fcfab1581458 » -jsonFilePath « C:\Users\contosoadmin\Desktop\Data\physical_badging_data.csv »

   4. Dans la **zone Démarrer dans (facultatif),** collez l’emplacement du dossier du script que vous avez écrit à l’étape 4. Par exemple, C:\Users\contosoadmin\Desktop\Scripts.

   5. Cliquez **sur OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la **fenêtre Créer une** tâche, cliquez sur **OK** pour enregistrer la tâche programmée. Vous pouvez être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du Programmeur de tâches.

   ![La nouvelle tâche s’affiche dans la bibliothèque du Programmeur des tâches](..\media\SchedulePhysicalBadgingScript2.png)

La dernière fois que le script a été exécuté et la prochaine fois qu’il est programmé pour s’exécuter, s’affiche. Vous pouvez double-cliquer sur la tâche pour la modifier.

Vous pouvez également vérifier la dernière fois que le script s’est passé sur la page volante du connecteur de badging physique correspondant dans le centre de conformité.
