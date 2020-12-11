---
title: Configurer un connecteur pour importer des données badges physiques
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
description: Les administrateurs peuvent configurer un connecteur de données pour importer des données à partir du système badges physique de leur organisation vers Microsoft 365. Cela vous permet d’utiliser ces données dans des stratégies de gestion des risques initiées pour vous aider à détecter l’accès à vos bâtiments physiques par des utilisateurs spécifiques susceptibles d’indiquer une éventuelle menace interne pour votre organisation.
ms.openlocfilehash: 7e745b42d0df79f5c39f9fa02cb1b63f164ec2a5
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620130"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Configurer un connecteur pour importer des données badges physiques (aperçu)

Vous pouvez configurer un connecteur de données dans le centre de conformité Microsoft 365 pour importer des données badges physiques, telles que des événements d’accès physique bruts de l’employé ou toute alerte d’accès physique générée par le système badges de votre organisation. Des exemples de points d’accès physiques constituent une entrée dans un immeuble ou une entrée dans une salle de serveur ou un centre de données. Les données badges physiques peuvent être utilisées par la solution de gestion des risques Microsoft 365 [Insider](insider-risk-management.md) pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation.

La configuration d’un connecteur badges physique comprend les tâches suivantes :

- Création d’une application dans Azure Active Directory (Azure AD) pour accéder à un point de terminaison d’API qui accepte une charge utile JSON qui contient des données badges physiques.

- Création de la charge utile JSON avec un schéma défini par le connecteur de données badges physique.

- Création d’un connecteur de données badges physique dans le centre de conformité Microsoft 365.

- Exécution d’un script pour acheminer les données badges physiques vers le point de terminaison de l’API.

- Si vous le souhaitez, planifiez le script pour qu’il s’exécute automatiquement pour importer les données badges physiques actuelles.

## <a name="before-you-set-up-the-connector"></a>Avant de configurer le connecteur

- L’utilisateur qui crée le connecteur badges physique à l’étape 3 doit se voir attribuer le rôle importation/exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

- Vous devez déterminer comment récupérer ou exporter les données à partir du système badges physique de votre organisation (quotidiennement) et créer un fichier JSON décrit à l’étape 2. Le script que vous exécutez à l’étape 4 envoie les données du fichier JSON au point de terminaison de l’API.

- L’exemple de script que vous exécutez à l’étape 4 transfère les données badges physiques du fichier JSON vers l’API de connecteur afin qu’elles puissent être utilisées par la solution de gestion des risques inSided. Cet exemple de script n’est pas pris en charge dans les services ou programmes de support standard Microsoft. L’exemple de script est fourni en l’État sans aucune garantie. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. L’ensemble des risques liés à l’utilisation ou aux performances de l’exemple de script et de la documentation reste avec vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

La première étape consiste à créer et à enregistrer une nouvelle application dans Azure Active Directory (Azure AD). L’application correspond au connecteur badges physique que vous créez à l’étape 3. La création de cette application permettra à Azure AD d’authentifier la demande de transmission pour la charge utile JSON contenant des données badges physiques. Lors de la création de cette application Azure AD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID de l’application Azure AD (également appelé *ID* de l’application ou *ID client*)

- Secret d’application Azure AD (également appelé *clé secrète client*)

- ID de client (également appelé *ID d’annuaire*)

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, consultez [la rubrique enregistrer une application avec la plateforme d’identité Microsoft](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Étape 2 : préparer un fichier JSON avec des données badges physiques

L’étape suivante consiste à créer un fichier JSON qui contient des informations sur les données d’accès physique des employés. Comme expliqué dans la section avant de commencer, vous devez déterminer comment générer ce fichier JSON à partir du système badges physique de votre organisation.

Le fichier JSON doit être conforme à la définition de schéma requise par le connecteur. Voici les descriptions des propriétés de schéma requises pour le fichier JSON :

| Propriété | Description | Type de données |
|:-----------|:--------------|:------------|
|UserId|Un employé peut avoir plusieurs identités numériques sur les systèmes. L’ID d’Azure AD doit déjà être résolu par le système source. |Nom d’utilisateur principal ou adresse de messagerie|
|AssetId|ID de référence de l’immobilisation physique ou du point d’accès physique.| Chaîne alphanumérique|
|AssetName|Nom convivial de l’immobilisation physique ou du point d’accès physique.|Chaîne alphanumérique|
|EventTime|Horodatage de l’accès.|Date et heure, au format UTC|
|AccessStatus|Valeur `Success` ou `Failed`| String|
|||

Voici un exemple d’un fichier JSON conforme au schéma requis :

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
Vous pouvez également télécharger la définition de schéma suivante pour le fichier JSON à partir de l’Assistant lorsque vous créez le connecteur badges physique à l’étape 3.

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

## <a name="step-3-create-the-physical-badging-connector"></a>Étape 3 : créer le connecteur badges physique

L’étape suivante consiste à créer un connecteur badges physique dans le centre de conformité Microsoft 365. Une fois que vous avez exécuté le script à l’étape 4, le fichier JSON que vous avez créé à l’étape 3 est traité et transmis au point de terminaison de l’API que vous avez configuré à l’étape 1. Dans cette étape, veillez à copier le JobId généré lors de la création du connecteur. Vous utiliserez le JobId lors de l’exécution du script.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Sur la page **connecteurs de données** , sous **badges physique**, cliquez sur **Afficher**.

3. Sur la page **badges physique** , cliquez sur **Ajouter un connecteur**.

4. Sur la page **informations d’identification d’authentification** , effectuez les opérations suivantes, puis cliquez sur **suivant**:
  
   1. Tapez ou collez l’ID de l’application Azure AD pour l’application Azure que vous avez créée à l’étape 1.
  
   2. Téléchargez le schéma d’exemple pour votre référence afin de créer le fichier JSON.
  
   3. Tapez un nom unique pour le connecteur badges physique.

5. Sur la page **révision** , vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

6. Une page d’État s’affiche pour confirmer que le connecteur a été créé. Cette page contient également l’ID du travail. Vous pouvez copier l’ID de travail à partir de cette page ou de la page de menu volant pour le connecteur. Vous avez besoin de cet ID de travail lors de l’exécution du script.

   La page d’état contient également un lien vers le script. Reportez-vous à ce script pour savoir comment publier le fichier JSON sur le point de terminaison de l’API.

7. Cliquez sur **Terminé**.

   Le nouveau connecteur est affiché dans la liste sous l’onglet **connecteurs** .

8. Cliquez sur le connecteur badges physique que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Étape 4 : exécuter le script pour publier votre fichier JSON contenant des données badges physiques

L’étape suivante de la configuration d’un connecteur badges physique consiste à exécuter un script qui enverra les données badges physiques dans le fichier JSON (que vous avez créé à l’étape 2) vers le point de terminaison de l’API que vous avez créé à l’étape 1. Nous fournissons un exemple de script pour votre référence et vous pouvez choisir de l’utiliser ou de créer votre propre script pour publier le fichier JSON dans le point de terminaison de l’API.

Après avoir exécuté le script, le fichier JSON contenant les données badges physiques est poussé vers votre organisation Microsoft 365 où il peut accéder à la solution de gestion des risques inSided. Nous vous recommandons de publier quotidiennement les données badges physiques. Pour ce faire, vous pouvez automatiser le processus de génération du fichier JSON tous les jours à partir de votre système badges physique, puis en planifiant le script pour qu’il envoie les données.

> [!NOTE]
> Le nombre maximal d’enregistrements dans le fichier JSON pouvant être traités par l’API est de 50 000 enregistrements.

1. Accédez à [ce site github](https://github.com/microsoft/m365-hrconnector-sample-scripts/blob/master/upload_termination_records.ps1) pour accéder à l’exemple de script.

2. Cliquez sur le bouton **RAW** pour afficher le script en mode texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, le cas échéant.

5. Enregistrez le fichier texte sous forme de fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier. ps1 ; par exemple, PhysicalBadging.ps1.

6. Ouvrez une invite de commandes sur votre ordinateur local et accédez au répertoire dans lequel vous avez enregistré le script.

7. Exécutez la commande suivante pour envoyer les données badges physiques dans le fichier JSON vers le Cloud Microsoft ; par exemple :

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations que vous avez obtenues dans les étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   | Paramètre | Description |
   |:-------------|:--------------|
   |tenantId | Il s’agit de l’ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir le tenantId pour votre organisation sur le panneau de présentation dans le centre **d'** administration Azure ad. Il est utilisé pour identifier votre organisation. |
   |appId | Il s’agit de l’ID de l’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est utilisé par Azure AD pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365.                    |
   |appSecret | Il s’agit de la clé secrète de l’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est également utilisé pour l’authentification.                                                        |
   |Identificateur | Il s’agit de l’ID de travail pour le connecteur badges physique que vous avez créé à l’étape 3. Il est utilisé pour associer les données badges physiques envoyées au Cloud Microsoft avec le connecteur badges physique.              |
   |JsonFilePath | Il s’agit du chemin d’accès au fichier sur l’ordinateur local (celui que vous utilisez pour exécuter le script) pour le fichier JSON que vous avez créé à l’étape 2. Ce fichier doit suivre le schéma d’exemple décrit à l’étape 3.|
   |||

   Voici un exemple de syntaxe pour le script du connecteur badges physique utilisant les valeurs réelles de chaque paramètre :

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Si le chargement réussit, le script affiche le message **chargement réussi** .

   Si vous avez plusieurs fichiers JSON, vous devez exécuter le script pour chaque fichier.

> [!NOTE]
> Vous pouvez également choisir d’envoyer les données badges physiques au point de terminaison de l’API par des méthodes autres que l’exécution du script précédent. Par exemple, voici un exemple d’utilisation du post pour envoyer vos données au point de terminaison de l’API.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Étape 5 : surveiller le connecteur badges physique

Après avoir créé le connecteur badges physique et diffusé vos données badges physiques, vous pouvez afficher le connecteur et l’état du chargement dans le centre de conformité Microsoft 365. Si vous planifiez le script pour qu’il s’exécute automatiquement régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur badges physique pour afficher la page de menu volant. Cette page contient les propriétés et les informations relatives au connecteur.

   ![Page de menu volant d’État pour le connecteur badges physique](..\media\PhysicalBadgingStatusFlyout.png)

3. Sous **dernière importation**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données à partir du fichier CSV vers le Cloud Microsoft.

   ![Le fichier journal du connecteur badges physique affiche les lignes numériques du fichier JSON qui ont été téléchargées](..\media\PhysicalBadgingConnectorLogFile.png)

   Le champ **RecordsSaved** indique le nombre de lignes du fichier CSV téléchargé. Par exemple, si le fichier CSV contient quatre lignes, la valeur des champs **RecordsSaved** est 4, si le script a téléchargé avec succès toutes les lignes dans le fichier CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien vers le téléchargement du script est affiché lors de la **dernière importation**. Vous pouvez télécharger le script, puis suivre les étapes de l’étape 4 pour l’exécuter.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>Module Étape 6 : planifier le script pour qu’il s’exécute automatiquement

Pour vous assurer que les dernières données badges physiques de votre organisation sont accessibles aux outils comme la solution de gestion des risques Insiders, nous vous recommandons de planifier l’exécution du script automatiquement sur une base récurrente, par exemple une fois par jour. Cela vous oblige également à mettre à jour les données badges physiques en fichiers JSON sur une planification similaire (si elle n’est pas la même) afin qu’elle contienne les informations les plus récentes sur les employés qui quittent votre organisation. L’objectif est de télécharger les données badges physiques les plus récentes afin que le connecteur badges physique puisse le mettre à la disposition de la solution de gestion des risques Insiders.

Vous pouvez utiliser l’application planificateur de tâches de Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton **Démarrer** de Windows, puis tapez **Planificateur de tâches**.

2. Cliquez sur l’application **Planificateur de tâches** pour l’ouvrir.

3. Dans la section **actions** , cliquez sur **créer une tâche**.

4. Sous l’onglet **général** , entrez un nom descriptif pour la tâche planifiée ; par exemple, le **script de connecteur badges physique**. Vous pouvez également ajouter une description facultative.

5. Sous **options de sécurité**, procédez comme suit :

   1. Déterminez s’il faut exécuter le script uniquement lorsque vous avez ouvert une session sur l’ordinateur ou que vous l’exécutez lorsque vous êtes connecté.

   2. Assurez-vous que la case à cocher **exécuter avec les privilèges les plus élevés** est activée.

6. Sélectionnez l’onglet **déclencheurs** , cliquez sur **nouveau**, puis effectuez les opérations suivantes :

   1. Sous **paramètres**, sélectionnez l’option **quotidien** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script se verra tous les jours au même moment.

   2. Sous **Paramètres avancés**, vérifiez que la case à cocher **activé** est activée.

   3. Cliquez sur **OK**.

7. Sélectionnez l’onglet **actions** , cliquez sur **nouveau**, puis effectuez les opérations suivantes :

   ![Paramètres des actions pour créer une tâche planifiée pour le script du connecteur badges physique](..\media\SchedulePhysicalBadgingScript1.png)

   1. Dans la liste déroulante **action** , assurez-vous que l’option **Démarrer un programme** est sélectionnée.

   2. Dans la zone **programme/script** , cliquez sur **Parcourir**, accédez à l’emplacement suivant et sélectionnez-le pour afficher le chemin d’accès dans la zone : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. Dans la zone **Ajouter des arguments (facultatif)** , collez la même commande de script que celle que vous avez exécutée à l’étape 4. Par exemple, .\PhysicalBadging.ps1-tenantId "d5723623-11CF-4E2E-B5A5-01d1506273g9"-appId "c12823b7-b55a-4989-faba-02de41bb97c3"-appSecret "MNubVGbcQDkGCnn"-jobId "e081f4f4-3831-48D6-7BB3-fcfab1581458"-jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.csv"

   4. Dans la zone **commencer dans (facultatif)** , collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple, C:\Users\contosoadmin\Desktop\Scripts.

   5. Cliquez sur **OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **créer une tâche** , cliquez sur **OK** pour enregistrer la tâche planifiée. Vous serez peut-être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche est affichée dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche est affichée dans la bibliothèque du planificateur de tâches.](..\media\SchedulePhysicalBadgingScript2.png)

La dernière fois que le script est exécuté et la prochaine fois qu’il est planifiée pour s’exécuter. Vous pouvez double-cliquer sur la tâche pour la modifier.

Vous pouvez également vérifier la dernière fois que le script s’est exécuté sur la page de menu volant du connecteur badges physique correspondant dans le centre de conformité.
