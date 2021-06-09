---
title: Configurer un connecteur pour importer des données RH dans le cloud pour le gouvernement des États-Unis
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
description: Les administrateurs du cloud pour le gouvernement des États-Unis peuvent configurer un connecteur de données pour importer les données des employés à partir du système des ressources humaines (RH) de leur organisation pour Microsoft 365. Cela vous permet d’utiliser des données RH dans les stratégies de gestion des risques internes pour vous aider à détecter les activités par des utilisateurs spécifiques qui peuvent poser une menace interne à votre organisation.
ms.openlocfilehash: 16d6d72d557744e30d41795d5f8c8a17db81c6a3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905926"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>Configurer un connecteur pour importer des données RH dans le gouvernement des États-Unis

Vous pouvez configurer un connecteur de données dans le centre de conformité Microsoft 365 pour importer des données de ressources humaines (RH) dans votre organisation pour le gouvernement des États-Unis. Les données liées aux ressources humaines incluent la date à laquelle un employé a envoyé sa préresignation et la date du dernier jour de l’employé. Ces données RH peuvent ensuite être utilisées par les solutions de protection des informations Microsoft, telles que la [solution](insider-risk-management.md)de gestion des risques internes, pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation. La configuration d’un connecteur RH consiste à créer une application dans Azure Active Directory utilisée pour l’authentification par connecteur, à créer un fichier de mappage CSV qui contient vos données RH, à créer un connecteur de données dans le centre de conformité, puis à exécutez un script (sur une base programmée) qui insérait les données RH dans le fichier CSV dans le cloud Microsoft. Ensuite, le connecteur de données est utilisé par l’outil de gestion des risques internes pour accéder aux données RH importées dans votre organisation Microsoft 365 gouvernement américain.

## <a name="before-you-begin"></a>Avant de commencer

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée le connecteur RH à l’étape 3 Exchange Online. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

- Vous devez déterminer comment récupérer ou exporter les données à partir du système RH de votre organisation (régulièrement) et les ajouter au fichier CSV décrit à l’étape 2. Le script que vous exécutez à l’étape 4 charge les données RH du fichier CSV dans le cloud Microsoft.

- L’exemple de script que vous exécutez à l’étape 4 télécharge les données RH dans le cloud Microsoft afin qu’elles soient utilisées par d’autres outils Microsoft, tels que la solution de gestion des risques internes. Cet exemple de script n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Étape 1 : Créer une application dans Azure Active Directory

La première étape consiste à créer et inscrire une nouvelle application dans Azure Active Directory (Azure AD). L’application correspond au connecteur RH que vous créez à l’étape 3. La création de cette application permettra à Azure AD d’authentifier le connecteur RH lorsqu’il s’exécute et tente d’accéder à votre organisation. Cette application sera également utilisée pour authentifier le script que vous exécutez à l’étape 4 pour charger vos données RH dans le cloud Microsoft. Lors de la création de cette application Azure AD, n’oubliez pas d’enregistrer les informations suivantes. Ces valeurs seront utilisées dans les étapes ultérieures.

- ID d’application Azure AD (également appelé *ID* d’application ou *ID client)*

- Secret d’application Azure AD (également appelé *secret client)*

- ID de client (également appelé *ID d’annuaire)*

Pour obtenir des instructions détaillées sur la création d’une application dans Azure AD, voir Inscrire une application avec le [Plateforme d’identités Microsoft](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>Étape 2 : Préparer un fichier CSV avec vos données RH

L’étape suivante consiste à créer un fichier CSV qui contient des informations sur les employés qui ont quitté votre organisation. Comme expliqué dans la section Avant de commencer, vous devez déterminer comment générer ce fichier CSV à partir du système RH de votre organisation. L’exemple suivant montre un fichier CSV terminé (ouvert dans le Bloc-notes) qui contient les trois paramètres requis (colonnes). Il est beaucoup plus facile de modifier le fichier CSV dans Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

La première ligne, ou ligne d’en-tête, du fichier CSV répertorie les noms de colonne requis. Vous devez utiliser le nom utilisé dans chaque en-tête de colonne (ceux de l’exemple précédent sont des suggestions). Toutefois, les noms de colonne que  vous utilisez dans le fichier CSV doivent être spécifiés lorsque vous créez le connecteur RH à l’étape 3. N’incluez pas d’espaces dans les noms de colonne.

Le tableau suivant décrit chaque colonne du fichier CSV :

| Nom de colonne | Description |
|:-----|:-----|
| **EmailAddress** <br/> |Spécifie l’adresse e-mail de l’employé licencié.|
| **TerminationDate** <br/> |Spécifie la date à laquelle le contrat de travail de la personne a été officiellement résilié dans votre organisation. Par exemple, il peut s’agit de la date à laquelle l’employé a donné son avis de départ de votre organisation. Cette date peut être différente de la date du dernier jour de travail de la personne. Utilisez le format de date suivant : , qui est le format de date et d’heure `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Spécifie le dernier jour de travail de l’employé licencié. Utilisez le format de date suivant : , qui est le format de date et d’heure `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm` [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Après avoir créé le fichier CSV avec les données RH requises, stockez-le sur le même système que le script que celui que vous exécutez à l’étape 4. Assurez-vous d’implémenter une stratégie de mise à jour afin que le fichier CSV contienne toujours les informations les plus à jour. Cela garantit que, quel que soit le script exécuté, les données de résiliation les plus récentes des employés sont téléchargées vers le cloud Microsoft.

## <a name="step-3-create-the-hr-connector"></a>Étape 3 : Créer le connecteur RH

L’étape suivante consiste à créer un connecteur RH dans le centre Microsoft 365 conformité. Après avoir exécuté le script à l’étape 4, le connecteur RH que vous créez inséra les données RH du fichier CSV vers votre organisation Microsoft 365. Dans cette étape, assurez-vous de copier l’ID de travail généré lorsque vous créez le connecteur. Vous utiliserez l’ID de travail lorsque vous exécuterez le script.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and then click Data **connectors** in the left nav.

2. Dans la page **Connecteurs de données** sous **RH,** cliquez sur **Afficher.**

3. Dans la page **RESSOURCES HUMAINES,** cliquez sur **Ajouter un connecteur.**

4. Dans la page **Informations d’identification** d’authentification, faites ce qui suit, puis cliquez sur **Suivant**:

   1. Tapez ou collez l’ID d’application Azure AD pour l’application Azure que vous avez créée à l’étape 1.

   1. Tapez un nom pour le connecteur RH.

5. Dans la **page** Mappage de fichiers, tapez les noms des trois en-têtes de colonne (également *appelés paramètres)* à partir du fichier CSV que vous avez créé à l’étape 2 dans chacune des zones appropriées. Les noms ne sont pas sensibles à la cas. Comme indiqué précédemment, les noms que vous tapez dans ces zones doivent correspondre aux noms de paramètres dans votre fichier CSV. Par exemple, la capture d’écran suivante montre les noms des paramètres de l’exemple dans l’exemple de fichier CSV présenté à l’étape 2.

   ![Les noms d’en-tête de colonne correspondent à ceux du fichier CSV](../media/HRConnectorWizard3.png)

6. Dans la page **Révision,** examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Une page d’état qui confirme que le connecteur a été créé s’affiche. Cette page contient deux éléments importants que vous devez effectuer à l’étape suivante pour exécuter l’exemple de script pour télécharger vos données RH.

   ![Page de révision avec ID de travail et lien vers github pour un exemple de script](../media/HRConnector_Confirmation.png)

   1. **ID de travail.** Vous aurez besoin de cet ID de travail pour exécuter le script à l’étape suivante. Vous pouvez le copier à partir de cette page ou à partir de la page de flyout du connecteur.
   
   1. **Lien vers l’exemple de script.** Cliquez sur **le lien** ici pour accéder au site GitHub pour accéder à l’exemple de script (le lien ouvre une nouvelle fenêtre). Gardez cette fenêtre ouverte afin de pouvoir copier le script à l’étape 4. Vous pouvez également réserver un signet à la destination ou copier l’URL afin de pouvoir y accéder à nouveau à l’étape 4. Ce lien est également disponible sur la page volante du connecteur.

7. Cliquez sur **Terminé**.

   Le nouveau connecteur s’affiche dans la liste sous l’onglet **Connecteurs.** 

8. Cliquez sur le connecteur RH que vous avez créé pour afficher la page de présentation, qui contient des propriétés et d’autres informations sur le connecteur.

   ![Page de flyout pour le nouveau connecteur RH](../media/HRConnectorWizard7.png)

   Si ce n’est pas déjà fait, vous pouvez copier les valeurs de **l’ID d’application Azure** et de l’ID de travail **connecteur.** Vous en aurez besoin pour exécuter le script à l’étape suivante. Vous pouvez également télécharger le script à partir de la page volante (ou le télécharger à l’aide du lien de l’étape suivante).)

   Vous pouvez également cliquer sur **Modifier** pour modifier l’ID d’application Azure ou les noms d’en-tête de colonne que vous avez définis sur la page **de mappage de** fichiers.

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Étape 4 : Exécuter l’exemple de script pour télécharger vos données RH

La dernière étape de la configuration d’un connecteur RH consiste à exécuter un exemple de script qui chargera les données RH dans le fichier CSV (que vous avez créé à l’étape 2) dans le cloud Microsoft. Plus précisément, le script charge les données vers le connecteur RH. Après avoir exécuté le script, le connecteur RH que vous avez créé à l’étape 3 importe les données RH dans votre organisation Microsoft 365 où il est accessible par d’autres outils de conformité, tels que la solution de gestion des risques internes. Après avoir exécuté le script, envisagez de planifier une tâche pour qu’elle s’exécute automatiquement quotidiennement afin que les données les plus récentes de résiliation d’employé sont chargées dans le cloud Microsoft. Voir [Planifier le script pour qu’il s’exécute automatiquement.](#optional-step-6-schedule-the-script-to-run-automatically)

1. Accédez à la fenêtre que vous avez laissée ouverte à partir de l’étape précédente pour accéder au site GitHub avec l’exemple de script. Vous pouvez également ouvrir le site avec signet ou utiliser l’URL que vous avez copiée.

2. Cliquez sur **le bouton Brut** pour afficher le script en affichage texte.

3. Copiez toutes les lignes de l’exemple de script, puis enregistrez-les dans un fichier texte.

4. Modifiez l’exemple de script pour votre organisation, si nécessaire.

5. Enregistrez le fichier texte en tant que fichier Windows PowerShell script à l’aide d’un suffixe de nom de fichier de `.ps1` ; par exemple, `HRConnector.ps1` .

6. Ouvrez une invite de commandes sur votre ordinateur local et allez dans le répertoire où vous avez enregistré le script.

7. Exécutez la commande suivante pour télécharger les données RH dans le fichier CSV dans le cloud Microsoft . par exemple :

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   Le tableau suivant décrit les paramètres à utiliser avec ce script et leurs valeurs requises. Les informations obtenues lors des étapes précédentes sont utilisées dans les valeurs de ces paramètres.

   | Paramètre | Description |
   |:-----|:-----|:-----|
   |`tenantId`|ID de votre organisation Microsoft 365 que vous avez obtenu à l’étape 1. Vous pouvez également obtenir l’ID de locataire de votre organisation dans le panneau **Vue** d’ensemble du Centre d’administration Azure AD. Il est utilisé pour identifier votre organisation.|
   |`appId` |ID d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Il est utilisé par Azure AD pour l’authentification lorsque le script tente d’accéder à Microsoft 365 organisation. |
   |`appSecret`|Secret d’application Azure AD pour l’application que vous avez créée dans Azure AD à l’étape 1. Cette fonction est également utilisée pour l’authentification.|
   |`jobId`|ID de travail pour le connecteur RH que vous avez créé à l’étape 3. Cette fonction permet d’associer les données RH téléchargées vers le cloud Microsoft au connecteur RH.|
   |`csvFilePath`|Chemin d’accès au fichier CSV (stocké sur le même système que le script) que celui que vous avez créé à l’étape 2. Essayez d’éviter les espaces dans le chemin d’accès du fichier . sinon, utilisez des guillemets simples.|
   |||
   
   Voici un exemple de syntaxe pour le script de connecteur RH utilisant des valeurs réelles pour chaque paramètre :

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Si le téléchargement réussit, le script affiche **l’Télécharger message** Réussite.

   > [!NOTE]
   > Si vous avez des problèmes lors de [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) l’exécution de la commande précédente en raison de stratégies d’exécution, voir À propos des stratégies d’exécution et [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) pour obtenir des instructions sur la définition des stratégies d’exécution.

## <a name="step-5-monitor-the-hr-connector"></a>Étape 5 : Surveiller le connecteur RH

Après avoir créé le connecteur RH et exécuté le script pour télécharger vos données RH, vous pouvez afficher le connecteur et l’état de chargement dans le centre de conformité Microsoft 365 de gestion. Si vous programmez l’exécuter automatiquement sur une base régulière, vous pouvez également afficher l’état actuel après la dernière fois que le script a été exécuté.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur RH pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

   ![Page de flyout du connecteur RH avec les propriétés et l’état](../media/HRConnectorFlyout1.png)

3. Sous **Progression,** cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur chaque fois que le script s’exécute et charge les données du fichier CSV dans le cloud Microsoft. 

   ![Le fichier journal du connecteur RH affiche les lignes de numéro à partir du fichier CSV qui ont été téléchargées](../media/HRConnectorLogFile.png)

   Le `RecordsSaved` champ indique le nombre de lignes dans le fichier CSV téléchargé. Par exemple, si le fichier CSV contient quatre lignes, la valeur des champs est 4, si le script a correctement téléchargé toutes les lignes du fichier `RecordsSaved` CSV.

Si vous n’avez pas exécuté le script à l’étape 4, un lien pour télécharger le script s’affiche sous **Dernière importation.** Vous pouvez télécharger le script, puis suivre les étapes de l’étape 4 pour l’exécuter.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Facultatif) Étape 6 : Planifier l’exécuter automatiquement

Pour vous assurer que les dernières données RH de votre organisation sont disponibles pour des outils tels que la solution de gestion des risques internes, nous vous recommandons de planifier l’exécuter automatiquement de manière périodique, par exemple une fois par jour. Vous devez également mettre à jour les données RH dans le fichier CSV selon une planification similaire (si ce n’est pas la même) afin qu’elles contiennent les dernières informations sur les employés qui quittent votre organisation. L’objectif est de télécharger les données RH les plus récentes afin que le connecteur RH puisse les rendre disponibles pour la solution de gestion des risques internes.

Vous pouvez utiliser l’application Planification des tâches dans Windows pour exécuter automatiquement le script tous les jours.

1. Sur votre ordinateur local, cliquez sur le bouton Windows **démarrer,** puis tapez Planification **des tâches.**

2. Cliquez sur **l’application De planification des** tâches pour l’ouvrir.

3. Dans la section **Actions,** cliquez sur **Créer une tâche.**

4. Sous **l’onglet** Général, tapez un nom descriptif pour la tâche programmée . par exemple, **SCRIPT DE CONNECTEUR RH**. Vous pouvez également ajouter une description facultative.

5. Sous **Options de sécurité,** faites les actions suivantes :

   1. Déterminez s’il faut exécuter le script uniquement lorsque vous êtes connecté à l’ordinateur ou l’exécuter lorsque vous êtes connecté ou non.
   
   1. Assurez-vous que la **case à cocher** Exécuter avec les privilèges les plus élevés est cocher.

6. Sélectionnez **l’onglet Déclencheurs,** cliquez **sur Nouveau,** puis faites les choses suivantes :

   1. Sous **Paramètres**, sélectionnez l’option  Quotidienne, puis choisissez une date et une heure pour exécuter le script pour la première fois. Le script sera tous les jours à la même heure spécifiée.
   
   1. Sous **Paramètres avancés,** assurez-vous que **la case à** cocher Activée est activée.
   
   1. Cliquez sur **OK**.

7. Sélectionnez **l’onglet Actions,** cliquez **sur Nouveau,** puis faites les actions suivantes :

   ![Paramètres d’action pour créer une tâche programmée pour le script de connecteur RH](../media/HRConnectorScheduleTask1.png)

   1. Dans la **liste de** listes d’actions, assurez-vous que démarrer **un programme** est sélectionné.

   1. Dans la **zone Programme/script,** cliquez sur **Parcourir,** puis accédez à l’emplacement suivant et sélectionnez-le afin que le chemin d’accès s’affiche dans la zone `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` :

   1. Dans la **zone Ajouter des arguments (facultatif),** collez la même commande de script que celle que vous avez l’étape 4. Par exemple, `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. Dans la **zone Démarrer dans (facultatif),** collez l’emplacement du dossier du script que vous avez écrit à l’étape 4. Par exemple, `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Cliquez **sur OK** pour enregistrer les paramètres de la nouvelle action.

8. Dans la **fenêtre Créer une** tâche, cliquez sur **OK** pour enregistrer la tâche programmée. Vous pouvez être invité à entrer vos informations d’identification de compte d’utilisateur.

   La nouvelle tâche s’affiche dans la bibliothèque du Programmeur de tâches.

   ![La nouvelle tâche s’affiche dans la bibliothèque du Programmeur des tâches](../media/HRConnectorTaskSchedulerLibrary.png)

   La dernière fois que le script a été exécuté et la prochaine fois qu’il est programmé pour s’exécuter, s’affiche. Vous pouvez double-cliquer sur la tâche pour la modifier.

   Vous pouvez également vérifier la dernière fois que le script a été écrit sur la page volante du connecteur RH correspondant dans le centre de conformité.