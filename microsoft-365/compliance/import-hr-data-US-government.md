---
title: Configurer un connecteur pour importer des données RH vers le Cloud du gouvernement américain
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
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs dans le nuage des États-Unis peuvent configurer un connecteur de données pour importer les données des employés à partir du système de ressources humaines (RH) de leur organisation vers Microsoft 365. Cela vous permet d’utiliser des données RH dans des stratégies de gestion des risques initiées pour vous aider à détecter les activités d’utilisateurs spécifiques susceptibles de constituer une menace interne pour votre organisation.
ms.openlocfilehash: 28f4c77ec626e2035451ec6e7c9562c5bf20f101
ms.sourcegitcommit: 3c39866865c8c61bce2169818d8551da65033cfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48816839"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>Configurer un connecteur pour importer des données RH dans le secteur public américain

Vous pouvez configurer un connecteur de données dans le centre de conformité Microsoft 365 pour importer les données des ressources humaines (RH) vers votre organisation gouvernementale américaine. Les données relatives aux ressources humaines incluent la date à laquelle un employé a envoyé sa démission et sa date de la dernière journée de son employé. Ces données RH peuvent ensuite être utilisées par les solutions de protection des informations de Microsoft, telles que la [solution de gestion des risques d’Insiders](insider-risk-management.md), pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation. La configuration d’un connecteur RH consiste à créer une application dans Azure Active Directory qui est utilisée pour l’authentification par un connecteur, à créer un fichier de mappage CSV contenant vos données RH, à créer un connecteur de données dans le centre de conformité, puis à exécuter un script (de manière planifiée) qui informera les données RH dans le fichier CSV vers le Cloud Microsoft. Le connecteur de données est ensuite utilisé par l’outil de gestion des risques inSided pour accéder aux données RH importées dans votre organisation Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de votre organisation. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général Microsoft 365, puis acceptez la demande. Vous devez effectuer cette étape avant de pouvoir créer le connecteur RH à l’étape 3.

- L’utilisateur qui crée le connecteur RH à l’étape 3 doit se voir attribuer le rôle importation/exportation de boîte aux lettres dans Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

- Vous devez déterminer comment récupérer ou exporter les données à partir du système RH de votre organisation (de manière régulière) et les ajouter au fichier CSV décrit à l’étape 2. Le script que vous exécutez à l’étape 4 télécharge les données RH dans le fichier CSV vers le Cloud Microsoft.

- L’exemple de script que vous exécutez à l’étape 4 téléchargera les données RH dans le Cloud Microsoft afin qu’elles puissent être utilisées par d’autres outils Microsoft, comme la solution de gestion des risques inSided. Cet exemple de script n’est pas pris en charge dans les services ou programmes de support standard Microsoft. L’exemple de script est fourni en l’État sans aucune garantie. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. L’ensemble des risques liés à l’utilisation ou aux performances de l’exemple de script et de la documentation reste avec vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

La première étape consiste à créer et à enregistrer une nouvelle application dans Azure Active Directory (Azure AD). L’application correspond au connecteur RH que vous créez à l’étape 3. La création de cette application permettra à Azure AD d’authentifier le connecteur RH lorsqu’il s’exécute et tente d’accéder à votre organisation. Cette application est également utilisée pour authentifier le script que vous exécutez à l’étape 4 pour télécharger vos données RH dans le Cloud de Microsoft. Lors de la création de cette application Azure AD, veillez à enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID de l’application Azure AD (également appelé *ID* de l’application ou *ID client* )

- Secret d’application Azure AD (également appelé *clé secrète client* )

- ID de client (également appelé *ID d’annuaire* )

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, consultez [la rubrique enregistrer une application avec la plateforme d’identité Microsoft](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>Étape 2 : préparer un fichier CSV avec vos données RH

L’étape suivante consiste à créer un fichier CSV contenant des informations sur les employés qui ont quitté votre organisation. Comme expliqué dans la section avant de commencer, vous devez déterminer comment générer ce fichier CSV à partir du système RH de votre organisation. L’exemple suivant montre un fichier CSV terminé (ouvert dans le pavé de notes) qui contient les trois paramètres obligatoires (colonnes). Il est beaucoup plus facile de modifier le fichier CSV dans Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

La première ligne, ou ligne d’en-tête, du fichier CSV répertorie les noms de colonne requis. Le nom utilisé dans chaque en-tête de colonne est à votre place (ceux de l’exemple précédent sont des suggestions). Toutefois, les mêmes noms de colonne que ceux utilisés dans le fichier CSV *doivent* être spécifiés lorsque vous créez le connecteur RH à l’étape 3. N’incluez pas d’espaces dans les noms de colonne.

Le tableau suivant décrit chaque colonne du fichier CSV :

| Nom de colonne | Description |
|:-----|:-----|
| **EmailAddress** <br/> |Spécifie l’adresse e-mail de l’employé qui a terminé.|
| **TerminationDate** <br/> |Indique la date à laquelle l’emploi de la personne a été officiellement terminé au sein de votre organisation. Par exemple, il peut s’agir de la date à laquelle l’employé a donné son avis sur la cessation de son organisation. Cette date peut être différente de la date du dernier jour de travail de la personne. Utilisez le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Spécifie le dernier jour de travail de l’employé terminé. Utilisez le format de date suivant : `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` , qui est le [format de date et d’heure ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Après avoir créé le fichier CSV avec les données RH requises, stockez-le sur le même système que le script exécuté à l’étape 4. N’oubliez pas d’implémenter une stratégie de mise à jour afin que le fichier CSV contienne toujours les informations les plus récentes. Cela garantit que tout ce que vous exécutez le script, les données de terminaison de l’employé les plus récentes sont téléchargées vers le Cloud Microsoft.

## <a name="step-3-create-the-hr-connector"></a>Étape 3 : créer le connecteur RH

L’étape suivante consiste à créer un connecteur RH dans le centre de conformité Microsoft 365. Une fois que vous avez exécuté le script à l’étape 4, le connecteur RH que vous créez exporte les données RH du fichier CSV vers votre organisation Microsoft 365. Dans cette étape, veillez à copier l’ID de travail qui est généré lorsque vous créez le connecteur. Vous utiliserez l’ID de travail lorsque vous exécuterez le script.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Sur la page **connecteurs de données** , sous **RH** , cliquez sur **affichage** .

3. Sur la page **RH** , cliquez sur **Ajouter un connecteur** .

4. Sur la page **informations d’identification d’authentification** , effectuez les opérations suivantes, puis cliquez sur **suivant** :

   1. Tapez ou collez l’ID de l’application Azure AD pour l’application Azure que vous avez créée à l’étape 1.

   1. Tapez un nom pour le connecteur RH.

5. Sur la page **mappage de fichiers** , tapez les noms des trois en-têtes de colonne (également appelés *paramètres* ) à partir du fichier CSV que vous avez créé à l’étape 2 dans chacune des zones appropriées. Les noms ne respectent pas la casse. Comme expliqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de paramètres dans votre fichier CSV. Par exemple, la capture d’écran suivante montre les noms des paramètres de l’exemple dans le fichier CSV d’exemple illustré à l’étape 2.

   ![Les titres des en-têtes de colonne correspondent à ceux du fichier CSV.](../media/HRConnectorWizard3.png)

6. Sur la page **révision** , vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Une page d’État s’affiche pour confirmer que le connecteur a été créé. Cette page contient deux éléments importants que vous devez suivre pour exécuter l’exemple de script pour charger vos données RH.

   ![Examiner la page avec l’ID de travail et le lien vers GitHub pour obtenir un exemple de script](../media/HRConnector_Confirmation.png)

   1. **ID de travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez la copier à partir de cette page ou de la page mobile du connecteur.
   
   1. **Lien vers l’exemple de script.** Cliquez sur le lien **ici** pour accéder au site github afin d’accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Laissez cette fenêtre ouverte pour pouvoir copier le script à l’étape 4. Vous pouvez également insérer un signet dans la destination ou copier l’URL afin de pouvoir y accéder à nouveau à l’étape 4. Ce lien est également disponible sur la page mobile du connecteur.

7. Cliquez sur **Terminé** .

   Le nouveau connecteur est affiché dans la liste sous l’onglet **connecteurs** . 

8. Cliquez sur le connecteur RH que vous venez de créer pour afficher la page de menu volant, qui contient des propriétés et d’autres informations sur le connecteur.

   ![Page de menu volant pour le nouveau connecteur RH](../media/HRConnectorWizard7.png)

   Si vous ne l’avez pas déjà fait, vous pouvez copier les valeurs pour l’ID d' **application Azure** et l' **ID de travail de connecteur** . Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page de menu volant (ou le télécharger en utilisant le lien de l’étape suivante).

   Vous pouvez également cliquer sur **modifier** pour modifier l’ID de l’application Azure ou les noms d’en-tête de colonne que vous avez définis sur la page **mappage de fichiers** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Étape 4 : exécuter l’exemple de script pour charger vos données RH

La dernière étape de la configuration d’un connecteur RH consiste à exécuter un exemple de script qui télécharge les données RH dans le fichier CSV (que vous avez créé à l’étape 2) vers le Cloud Microsoft. Plus précisément, le script télécharge les données vers le connecteur RH. Après avoir exécuté le script, le connecteur RH que vous avez créé à l’étape 3 importe les données RH dans votre organisation Microsoft 365 où il peut accéder à d’autres outils de conformité, tels que la solution de gestion des risques Insiders. Après avoir exécuté le script, envisagez de planifier une tâche pour qu’elle s’exécute automatiquement quotidiennement de sorte que les données de fin d’employé les plus récentes soient téléchargées vers le Cloud Microsoft. Consultez [la rubrique planifier le script pour qu’il s’exécute automatiquement](#optional-step-6-schedule-the-script-to-run-automatically).

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

   | Paramètre | Description |
   |:-----|:-----|:-----|
   |`tenantId`|ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir l’ID de client de votre organisation sur le panneau de présentation dans le centre **d'** administration Azure ad. Il est utilisé pour identifier votre organisation.|
   |`appId` |L’ID de l’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est utilisé par Azure AD pour l’authentification lorsque le script tente d’accéder à votre organisation Microsoft 365. |
   |`appSecret`|La clé secrète de l’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Cela est également utilisé pour l’authentification.|
   |`jobId`|ID de travail pour le connecteur HR que vous avez créé à l’étape 3. Il est utilisé pour associer les données RH téléchargées vers le Cloud Microsoft avec le connecteur RH.|
   |`csvFilePath`|Chemin d’accès au fichier CSV (stocké sur le même système que le script) que vous avez créé à l’étape 2. Essayez d’éviter les espaces dans le chemin d’accès du fichier ; Sinon, utilisez des guillemets simples.|
   |||
   
   Voici un exemple de syntaxe pour le script du connecteur RH en utilisant les valeurs réelles de chaque paramètre :

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Si le chargement réussit, le script affiche le message **chargement réussi** .

   > [!NOTE]
   > Si vous rencontrez des problèmes lors de l’exécution de la commande précédente en raison de stratégies d’exécution, voir [about Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies) et [Set-ExecutionPolicy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des instructions sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-hr-connector"></a>Étape 5 : surveiller le connecteur RH

Après avoir créé le connecteur RH et exécuté le script pour charger vos données RH, vous pouvez consulter le connecteur et l’état du chargement dans le centre de conformité Microsoft 365. Si vous planifiez le script pour qu’il s’exécute automatiquement régulièrement, vous pouvez également afficher l’état actuel après la dernière exécution du script.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur RH pour afficher la page de menu volant. Cette page contient les propriétés et les informations relatives au connecteur.

   ![Page mobile du connecteur RH avec les propriétés et l’État](../media/HRConnectorFlyout1.png)

3. Sous en **cours** , cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données à partir du fichier CSV vers le Cloud Microsoft. 

   ![Le fichier journal du connecteur RH affiche les lignes numériques à partir du fichier CSV qui ont été téléchargées](../media/HRConnectorLogFile.png)

   Le `RecordsSaved` champ indique le nombre de lignes du fichier CSV téléchargé. Par exemple, si le fichier CSV contient quatre lignes, la valeur des `RecordsSaved` champs est 4, si le script a téléchargé avec succès toutes les lignes dans le fichier CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien vers le téléchargement du script est affiché lors de la **dernière importation** . Vous pouvez télécharger le script, puis suivre les étapes de l’étape 4 pour l’exécuter.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>Module Étape 6 : planifier le script pour qu’il s’exécute automatiquement

Pour vous assurer que les dernières données RH de votre organisation sont accessibles aux outils comme la solution de gestion des risques Insiders, nous vous recommandons de planifier le script pour qu’il s’exécute automatiquement de manière récurrente, par exemple une fois par jour. Cela vous oblige également à mettre à jour les données RH dans le fichier CSV sur une planification similaire (si elle n’est pas la même) de façon à ce qu’elles contiennent les informations les plus récentes sur les employés qui quittent votre organisation. L’objectif est de télécharger les données RH les plus récentes afin que le connecteur RH puisse le mettre à la disposition de la solution de gestion des risques Insiders.

Vous pouvez utiliser l’application planificateur de tâches de Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton **Démarrer** de Windows, puis tapez **Planificateur de tâches** .

2. Cliquez sur l’application **Planificateur de tâches** pour l’ouvrir.

3. Dans la section **actions** , cliquez sur **créer une tâche** .

4. Sous l’onglet **général** , entrez un nom descriptif pour la tâche planifiée ; par exemple, le **script du connecteur RH** . Vous pouvez également ajouter une description facultative.

5. Sous **options de sécurité** , procédez comme suit :

   1. Déterminez s’il faut exécuter le script uniquement lorsque vous avez ouvert une session sur l’ordinateur ou que vous l’exécutez lorsque vous êtes connecté.
   
   1. Assurez-vous que la case à cocher **exécuter avec les privilèges les plus élevés** est activée.

6. Sélectionnez l’onglet **déclencheurs** , cliquez sur **nouveau** , puis effectuez les opérations suivantes :

   1. Sous **paramètres** , sélectionnez l’option **quotidien** , puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script se verra tous les jours au même moment.
   
   1. Sous **Paramètres avancés** , vérifiez que la case à cocher **activé** est activée.
   
   1. Cliquez sur  **OK** .

7. Sélectionnez l’onglet **actions** , cliquez sur **nouveau** , puis effectuez les opérations suivantes :

   ![Paramètres des actions pour créer une tâche planifiée pour le script du connecteur RH](../media/HRConnectorScheduleTask1.png)

   1. Dans la liste déroulante **action** , assurez-vous que l’option **Démarrer un programme** est sélectionnée.

   1. Dans la zone **programme/script** , cliquez sur **Parcourir** , accédez à l’emplacement suivant et sélectionnez-le pour afficher le chemin d’accès dans la zone : `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` .

   1. Dans la zone **Ajouter des arguments (facultatif)** , collez la même commande de script que celle que vous avez exécutée à l’étape 4. Par exemple, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Dans la zone **commencer dans (facultatif)** , collez l’emplacement du dossier du script que vous avez exécuté à l’étape 4. Par exemple, `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Cliquez sur **OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la fenêtre **créer une tâche** , cliquez sur **OK** pour enregistrer la tâche planifiée. Vous serez peut-être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche est affichée dans la bibliothèque du planificateur de tâches.

   ![La nouvelle tâche est affichée dans la bibliothèque du planificateur de tâches.](../media/HRConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script est exécuté et la prochaine fois qu’il est planifiée pour s’exécuter. Vous pouvez double-cliquer sur la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script s’est exécuté sur la page de menu volant du connecteur RH correspondant dans le centre de conformité.
