---
title: Utilisation de PowerShell pour effectuer une migration intermédiaire vers Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/07/2022
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Découvrez comment utiliser PowerShell pour déplacer du contenu à partir d’un système de messagerie source au fil du temps à l’aide d’une migration intermédiaire vers Microsoft 365.
ms.openlocfilehash: be60b6469b8e432728ef174104403900e115e68f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68191692"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration intermédiaire vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez migrer le contenu des boîtes aux lettres utilisateur d’un système de messagerie source vers Microsoft 365 au fil du temps à l’aide d’une migration intermédiaire.

Cet article décrit les tâches nécessaires pour effectuer une migration de messagerie intermédiaire à l'aide d'Exchange Online PowerShell. La rubrique, [Ce que vous devez savoir sur une migration par e-mail intermédiaire](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration), vous donne une vue d’ensemble du processus de migration. Une fois familiarisé avec son contenu, reportez-vous au présent article pour migrer des boîtes aux lettres d'un système de messagerie vers un autre.

> [!NOTE]
> Vous pouvez également utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> pour effectuer une migration intermédiaire. Voir [Effectuer une migration intermédiaire de l’e-mail vers Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur d’autres facteurs qui affectent le temps nécessaire pour migrer des boîtes aux lettres vers Microsoft 365, consultez [Performances de migration](/Exchange/mailbox-migration/office-365-migration-best-practices).

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](/exchange/recipients-permissions-exchange-2013-help) topic.

Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour obtenir des instructions[, consultez Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-a-staged-migration"></a>Étape 1 : Préparez une migration intermédiaire

Avant de migrer des boîtes aux lettres vers Microsoft 365 à l’aide d’une migration intermédiaire, vous devez apporter quelques modifications à votre environnement Exchange.

 **Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:

- [Exchange 2007 : Procédure d'activation d'Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Procédure de configuration d'Outlook Anywhere avec Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **Facultatif : vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :

- Utilisez Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.

- Utilisez Microsoft [Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/) pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.

- Dans Exchange Online PowerShell, exécutez les commandes suivantes :

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Définir des autorisations** Le compte d’utilisateur local que vous utilisez pour vous connecter à votre organisation Exchange locale (également appelée administrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous souhaitez migrer vers Microsoft 365. Ce compte d’utilisateur est utilisé lorsque vous vous connectez à votre système de messagerie en créant un point de terminaison de migration plus loin dans cette procédure [Étape 3 : Créer un point de terminaison de migration](#step-3-create-a-migration-endpoint).

Pour migrer les boîtes aux lettres, l’administrateur doit disposer de l’un des jeux d’autorisations suivants :

- Être membre du groupe **Administrateurs du domaine** dans Active Directory au sein de l'organisation locale.

    ou

- Disposer de l'autorisation **Accès total** pour chaque boîte aux lettres locale et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur les comptes des utilisateurs locaux.

    ou

- Disposer de l'autorisation **Recevoir en tant que** sur la base de données de boîtes aux lettres locale qui contient les boîtes aux lettres utilisateur et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur le compte d'utilisateur local.

Pour obtenir des instructions sur la définition de ces autorisations, consultez [Affecter des autorisations pour migrer des boîtes aux lettres vers Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Utilisez la synchronisation d’annuaires pour créer des utilisateurs dans Microsoft 365.** Vous utilisez la synchronisation d’annuaires pour créer tous les utilisateurs locaux de votre organisation Microsoft 365.

You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](#step-8-complete-post-migration-tasks).

 Vous pouvez utiliser l’outil de synchronisation Microsoft Azure Active Directory (Azure AD) ou les services de synchronisation Microsoft Azure AD pour synchroniser et créer vos utilisateurs locaux dans Microsoft 365. Une fois les boîtes aux lettres migrées vers Microsoft 365, vous gérez les comptes d’utilisateur dans votre organisation locale et ils sont synchronisés avec votre organisation Microsoft 365. Pour plus d'informations, voir [Intégration d'annuaire](/previous-versions/azure/azure-services/jj573653(v=azure.100)).

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Étape 2 : Créez un fichier CSV pour un lot de migration intermédiaire

Après avoir identifié les utilisateurs dont vous souhaitez migrer des boîtes aux lettres locales vers Microsoft 365, vous utilisez un fichier de valeurs séparées par des virgules (CSV) pour créer un lot de migration. Chaque ligne du fichier CSV, utilisée par Microsoft 365 pour exécuter la migration, contient des informations sur une boîte aux lettres locale.

> [!NOTE]
> Il n’existe pas de limite pour le nombre de boîtes aux lettres que vous pouvez migrer vers Microsoft 365 à l’aide d’une migration intermédiaire. Le fichier CSV d'un lot de migration peut contenir au maximum 2 000 lignes. Pour migrer plus de 2 000 boîtes aux lettres, vous devez créer des fichiers CSV supplémentaires et les utiliser pour créer de nouveaux lots de migration.

 **Attributs pris en charge**

The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.

|**Attribut**|**Description**|**Requis ?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Permet de définir l’adresse de messagerie SMTP principale, par exemple pilarp@contoso.com, pour les boîtes aux lettres locales.  <br/> Utilisez l’adresse SMTP principale pour les boîtes aux lettres locales et non les ID utilisateur de Microsoft 365. Par exemple, si le domaine local est nommé contoso.com mais que le domaine de messagerie Microsoft 365 est nommé service.contoso.com, vous devez utiliser le nom de domaine contoso.com pour les adresses e-mail dans le fichier CSV.  <br/> |Requis  <br/> |
|Mot de passe  <br/> |Mot de passe à définir pour la nouvelle boîte aux lettres Microsoft 365. Toutes les restrictions de mot de passe appliquées à votre organisation Microsoft 365 s’appliquent également aux mots de passe inclus dans le fichier CSV.  <br/> |Facultatif  <br/> |
|ForceChangePassword  <br/> |Spécifie si un utilisateur doit modifier le mot de passe la première fois qu’il se connecte à sa nouvelle boîte aux lettres Microsoft 365. Pour ce paramètre, utilisez la valeur **True** ou **False**. <br/> > [!NOTE]> Si vous avez implémenté une solution d'authentification unique (SSO) en déployant Active Directory Federation Services (AD FS) dans votre organisation locale, vous devez utiliser la valeur **False** pour l'attribut **ForceChangePassword**.          |Facultatif  <br/> |

 **Format de fichier CSV**

Voici un exemple de format pour le fichier CSV. Dans cet exemple, trois boîtes aux lettres locales sont migrées vers Microsoft 365.

The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.

Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.

> [!NOTE]
> If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.

### <a name="step-3-create-a-migration-endpoint"></a>Étape 3 : Créez un point de terminaison de migration

Pour migrer correctement le courrier électronique, Microsoft 365 doit se connecter et communiquer avec le système de messagerie source. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Pour créer un point de terminaison de migration Outlook Anywhere à l'aide de PowerShell, afin d'effectuer une migration intermédiaire, commencez par vous [connecter à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

Pour créer un point de terminaison de migration Outlook Anywhere appelé « StagedEndpoint » dans Exchange Online PowerShell, exécutez les commandes suivantes :

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Pour plus d'informations sur la cmdlet **New-MigrationEndpoint**, voir [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « StagedEndpoint » :

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Étape 4 : Créez et démarrez un lot de migration intermédiaire

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

Cet exemple de code crée également un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente. Étant donné que le paramètre _De démarrage automatique_ n’est pas inclus, le lot de migration doit être démarré manuellement sur le tableau de bord de migration ou à l’aide de l’applet de commande **Start-MigrationBatch** . Comme indiqué précédemment, il ne peut y avoir qu’une seule lot de migration à basculement à la fois.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « StagedBatch1 » :

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Vous pouvez également vérifier que le lot a démarré en exécutant la commande suivante :

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Étape 5 : Convertissez des boîtes aux lettres locales en utilisateurs à extension messagerie

Une fois la migration d’un premier lot effectuée, vous devez permettre aux utilisateurs d’accéder à leur messagerie. Un utilisateur dont la boîte aux lettres a été migrée dispose désormais d’une boîte aux lettres locale et d’une autre dans Microsoft 365. Les utilisateurs qui ont une boîte aux lettres dans Microsoft 365 cesseront de recevoir de nouveaux messages dans leur boîte aux lettres locale.

Étant donné que vous n’avez pas terminé vos migrations, vous n’êtes pas encore prêt à diriger tous les utilisateurs vers Microsoft 365 pour leur courrier électronique. Que faire alors pour les personnes qui disposent de deux boîtes aux lettres ? Eh bien vous pouvez convertir les boîtes aux lettres qui ont déjà été migrées en utilisateurs à extension messagerie. Lorsque vous passez d’une boîte aux lettres à un utilisateur à extension messagerie, vous pouvez diriger l’utilisateur vers Microsoft 365 pour son e-mail au lieu d’accéder à sa boîte aux lettres locale.

Une autre raison importante de convertir des boîtes aux lettres locales en utilisateurs à extension messagerie est de conserver les adresses proxy des boîtes aux lettres Microsoft 365 en copiant les adresses proxy vers les utilisateurs à extension messagerie. Cela vous permet de gérer des utilisateurs en nuage à partir de votre organisation locale à l'aide d'Active Directory. En outre, si vous décidez de désactiver votre organisation Exchange Server locale une fois que toutes les boîtes aux lettres ont été migrées vers Microsoft 365, les adresses proxy que vous avez copiées vers les utilisateurs à extension messagerie resteront dans votre Active Directory local.

### <a name="step-6-delete-a-staged-migration-batch"></a>Étape 6 : Supprimez un lot de migration intermédiaire

 Après avoir migré toutes les boîtes aux lettres d'un lot de migration et converti les boîtes aux lettres locales du lot en utilisateurs à extension messagerie, vous êtes prêt à supprimer un lot de migration intermédiaire. Veillez à vérifier que le courrier est transféré aux boîtes aux lettres Microsoft 365 dans le lot de migration. Lorsque vous supprimez un lot de migration intermédiaire, le service de migration nettoie tous les enregistrements associés au lot de migration, puis supprime ce dernier.

Pour supprimer le lot de migration « StagedBatch1 » dans Exchange Online PowerShell, exécutez la commande ci-dessous.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Pour plus d'informations sur la cmdlet **Remove-MigrationBatch**, voir [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPBatch1 » :

```powershell
Get-MigrationBatch StagedBatch1
```

La commande renvoie soit le lot de migration avec l'état **Suppression**, soit un message d'erreur indiquant que le lot de migration est introuvable, confirmant que le lot a été supprimé.

Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Étape 7 : Attribuer des licences à des utilisateurs Microsoft 365

Activez les comptes d’utilisateur Microsoft 365 pour les comptes migrés en attribuant des licences. Si vous n’attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour attribuer une licence dans le Centre d'administration Microsoft 365, consultez [Affecter ou annuler l’attribution de licences](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Étape 8 : Exécutez les tâches post-migration

- **Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres** Une fois toutes les boîtes aux lettres locales migrées vers Microsoft 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Microsoft 365 afin de permettre aux utilisateurs de se connecter facilement à leurs nouvelles boîtes aux lettres Microsoft 365 avec des clients Outlook et mobiles. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui que vous utilisez pour votre organisation Microsoft 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l’enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.

    Microsoft 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour les clients Outlook et mobiles. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :

  - **Alias :** autodiscover

  - **Cible :** autodiscover.outlook.com

    Pour plus d’informations, consultez [Ajouter des enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Désactivez des serveurs Exchange locaux.** Une fois que vous avez vérifié que tous les e-mails sont acheminés directement vers les boîtes aux lettres Microsoft 365 et que vous n’avez plus besoin de gérer votre organisation de messagerie locale ou de ne pas planifier l’implémentation d’une solution d’authentification unique, vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.

> [!NOTE]
> La désaffectation d'Exchange peut avoir des conséquences inattendues. Avant de désaffecter votre organisation Exchange locale, il est recommandé de contacter le support technique Microsoft.

Pour plus d’informations, voir les commandes suivantes :

- [Modifier ou supprimer Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

- [Procédure de suppression d'une organisation Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

- [Procédure de désinstallation d'Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
