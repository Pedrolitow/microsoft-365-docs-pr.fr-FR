---
title: Utilisation de PowerShell pour effectuer une migration intermédiaire vers Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Découvrez comment utiliser PowerShell pour déplacer du contenu à partir d’un système de messagerie source au fil du temps à l’aide d’une migration intermédiaire vers Microsoft 365.
ms.openlocfilehash: 872ae883728e1c20a6233e14e56bda804e757590
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091960"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration intermédiaire vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez migrer le contenu des boîtes aux lettres utilisateur d’un système de messagerie source vers Microsoft 365 au fil du temps à l’aide d’une migration intermédiaire.

Cet article décrit les tâches nécessaires pour effectuer une migration de messagerie intermédiaire à l'aide d'Exchange Online PowerShell. La rubrique, [Ce que vous devez savoir sur une migration par e-mail intermédiaire](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration), vous donne une vue d’ensemble du processus de migration. Une fois familiarisé avec son contenu, reportez-vous au présent article pour migrer des boîtes aux lettres d'un système de messagerie vers un autre.

> [!NOTE]
> Vous pouvez également utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> pour effectuer une migration intermédiaire. Voir [Effectuer une migration intermédiaire de l’e-mail vers Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur d’autres facteurs qui affectent le temps nécessaire à la migration des boîtes aux lettres vers Microsoft 365, consultez [Performances de migration](/Exchange/mailbox-migration/office-365-migration-best-practices).

Des autorisations doivent vous être attribuées que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans la rubrique [Autorisations des destinataires](/exchange/recipients-permissions-exchange-2013-help).

Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-a-staged-migration"></a>Étape 1 : Préparez une migration intermédiaire

Avant de migrer des boîtes aux lettres vers Microsoft 365 à l’aide d’une migration intermédiaire, vous devez apporter quelques modifications à votre environnement Exchange.

 **Configurer Outlook Anywhere sur votre Exchange Server local** Le service de migration de la messagerie utilise Outlook Anywhere (également appelé RPC sur HTTP) pour se connecter à votre Exchange Server local. Pour plus d'informations sur la configuration d'Outlook Anywhere pour Exchange Server 2007 et Exchange 2003, consultez les rubriques suivantes :

- [Exchange 2007 : Procédure d'activation d'Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Procédure de configuration d'Outlook Anywhere avec Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Vous devez utiliser un certificat émis par une autorité de certification (AC) approuvée pour votre configuration Outlook Anywhere. Outlook Anywhere ne peut pas être configuré avec un certificat auto-signé. Pour plus d'informations, consultez la rubrique [Procédure de configuration de SSL pour Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **Facultatif : vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :

- Utilisez Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.

- Utilisez Microsoft [Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.

- Dans Exchange Online PowerShell, exécutez les commandes suivantes :

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Définir des autorisations** Le compte d’utilisateur local que vous utilisez pour vous connecter à votre organisation locale Exchange (également appelée administrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous souhaitez migrer vers Microsoft 365. Ce compte d’utilisateur est utilisé lorsque vous vous connectez à votre système de messagerie en créant un point de terminaison de migration plus loin dans cette procédure [Étape 3 : Créer un point de terminaison de migration](#step-3-create-a-migration-endpoint).

Pour migrer les boîtes aux lettres, l’administrateur doit disposer de l’un des jeux d’autorisations suivants :

- Être membre du groupe **Administrateurs du domaine** dans Active Directory au sein de l'organisation locale.

    ou

- Disposer de l'autorisation **Accès total** pour chaque boîte aux lettres locale et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur les comptes des utilisateurs locaux.

    ou

- Disposer de l'autorisation **Recevoir en tant que** sur la base de données de boîtes aux lettres locale qui contient les boîtes aux lettres utilisateur et de l'autorisation **WriteProperty** lui permettant de modifier la propriété **TargetAddress** sur le compte d'utilisateur local.

Pour obtenir des instructions sur la définition de ces autorisations, consultez [Affecter des autorisations pour migrer des boîtes aux lettres vers Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Désactiver la messagerie unifiée (MU)** Si la messagerie unifiée est activée pour les boîtes aux lettres locales que vous migrez, désactivez-la avant la migration. Réactivez-la ensuite pour les boîtes aux lettres une fois la migration terminée. Pour la procédure correspondante, voir [Désactivation d'une messagerie unifiée pour un utilisateur](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Utilisez la synchronisation d’annuaires pour créer des utilisateurs dans Microsoft 365.** Vous utilisez la synchronisation d’annuaires pour créer tous les utilisateurs locaux de votre organisation Microsoft 365.

Vous devez attribuer une licence aux utilisateurs créés. Vous disposez pour cela de 30 jours à compter de leur création. Pour la procédure d'ajout de licences, voir [Étape 8 : Exécutez les tâches post-migration](#step-8-complete-post-migration-tasks).

 Vous pouvez utiliser l’outil de synchronisation Microsoft Azure Active Directory (Azure AD) ou les services de synchronisation Microsoft Azure AD pour synchroniser et créer vos utilisateurs locaux dans Microsoft 365. Une fois les boîtes aux lettres migrées vers Microsoft 365, vous gérez les comptes d’utilisateur dans votre organisation locale et ils sont synchronisés avec votre organisation Microsoft 365. Pour plus d'informations, voir [Intégration d'annuaire](/previous-versions/azure/azure-services/jj573653(v=azure.100)).

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Étape 2 : Créez un fichier CSV pour un lot de migration intermédiaire

Après avoir identifié les utilisateurs dont vous souhaitez migrer des boîtes aux lettres locales vers Microsoft 365, vous utilisez un fichier de valeurs séparées par des virgules (CSV) pour créer un lot de migration. Chaque ligne du fichier CSV, utilisée par Microsoft 365 pour exécuter la migration, contient des informations sur une boîte aux lettres locale.

> [!NOTE]
> Il n’existe pas de limite pour le nombre de boîtes aux lettres que vous pouvez migrer vers Microsoft 365 à l’aide d’une migration intermédiaire. Le fichier CSV d'un lot de migration peut contenir au maximum 2 000 lignes. Pour migrer plus de 2 000 boîtes aux lettres, vous devez créer des fichiers CSV supplémentaires et les utiliser pour créer de nouveaux lots de migration.

 **Attributs pris en charge**

Le fichier CSV destiné à une migration intermédiaire prend en charge les trois attributs suivants. Chaque ligne du fichier CSV correspond à une boîte aux lettres et doit contenir une valeur pour chacun des attributs ci-dessous.

|**Attribut**|**Description**|**Requis ?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Permet de définir l’adresse de messagerie SMTP principale, par exemple pilarp@contoso.com, pour les boîtes aux lettres locales.  <br/> Utilisez l’adresse SMTP principale pour les boîtes aux lettres locales et non les ID utilisateur du Microsoft 365. Par exemple, si le domaine local est nommé contoso.com mais que le domaine de messagerie Microsoft 365 est nommé service.contoso.com, vous devez utiliser le nom de domaine contoso.com pour les adresses e-mail dans le fichier CSV.  <br/> |Requis  <br/> |
|Mot de passe  <br/> |Mot de passe à définir pour la nouvelle boîte aux lettres Microsoft 365. Toutes les restrictions de mot de passe appliquées à votre organisation Microsoft 365 s’appliquent également aux mots de passe inclus dans le fichier CSV.  <br/> |Facultatif  <br/> |
|ForceChangePassword  <br/> |Spécifie si un utilisateur doit modifier le mot de passe la première fois qu’il se connecte à sa nouvelle boîte aux lettres Microsoft 365. Pour ce paramètre, utilisez la valeur **True** ou **False**. <br/> > [!NOTE]> Si vous avez implémenté une solution d'authentification unique (SSO) en déployant Active Directory Federation Services (AD FS) dans votre organisation locale, vous devez utiliser la valeur **False** pour l'attribut **ForceChangePassword**.          |Facultatif  <br/> |

 **Format de fichier CSV**

Voici un exemple de format pour le fichier CSV. Dans cet exemple, trois boîtes aux lettres locales sont migrées vers Microsoft 365.

La première ligne, ou ligne d'en-tête, du fichier CSV répertorie les noms des attributs, ou champs, spécifiés dans les lignes qui suivent. Les noms d'attributs sont séparés par des virgules.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

Chaque ligne sous la ligne d’en-tête représente un utilisateur et fournit les informations qui seront utilisées pour migrer la boîte aux lettres de l’utilisateur. Les valeurs d’attribut de chaque ligne doivent respecter l’ordre des noms d’attribut dans la ligne d’en-tête.

Pour créer le fichier CSV, utilisez un éditeur de texte ou une application telle qu’Excel. Enregistrez le fichier au format .csv ou .txt.

> [!NOTE]
> Si le fichier CSV contient des caractères non ASCII ou des caractères spéciaux, enregistrez-le avec l’encodage UTF-8 ou un autre encodage Unicode. Selon l’application, l’enregistrement du fichier CSV avec l’encodage UTF-8 ou un autre encodage Unicode peut être facilité lorsque les paramètres régionaux système de l’ordinateur correspondent à la langue utilisée dans le fichier CSV.

### <a name="step-3-create-a-migration-endpoint"></a>Étape 3 : Créez un point de terminaison de migration

Pour migrer correctement l’e-mail, Microsoft 365 doit se connecter et communiquer avec le système de messagerie source. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Pour créer un point de terminaison de migration Outlook Anywhere à l'aide de PowerShell, afin d'effectuer une migration intermédiaire, commencez par vous [connecter à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

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
> La cmdlet **New-MigrationEndpoint** peut être utilisée pour spécifier une base de données pour le service à l'aide de l'option **-TargetDatabase**. Sinon, une base de données est affectée de manière aléatoire à partir du site Services ADFS (Active Directory Federation Services) 2.0 où se trouve la boîte aux lettres de gestion.

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « StagedEndpoint » :

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Étape 4 : Créez et démarrez un lot de migration intermédiaire

La cmdlet **New-MigrationBatch** d'Exchange Online PowerShell permet de créer un lot pour une migration à basculement. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer manuellement son traitement par la suite à l'aide de la cmdlet **Start-MigrationBatch**. Cet exemple de code crée un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

Cet exemple de code crée également un lot de migration appelé « StagedBatch1 » et utilise le point de terminaison de migration créé à l'étape précédente. Le paramètre  _AutoStart_ n'étant pas inclus, le traitement du lot de migration doit être lancé manuellement sur le tableau de bord de migration ou à l'aide de la cmdlet **Start-MigrationBatch**. Comme indiqué précédemment, il ne peut y avoir qu'une seule lot de migration à basculement à la fois.

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

Une fois la migration d’un premier lot effectuée, vous devez permettre aux utilisateurs d’accéder à leur messagerie. Un utilisateur dont la boîte aux lettres a été migrée dispose désormais d’une boîte aux lettres locale et d’une boîte aux lettres dans Microsoft 365. Les utilisateurs qui ont une boîte aux lettres dans Microsoft 365 cesseront de recevoir de nouveaux messages dans leur boîte aux lettres locale.

Étant donné que vous n’avez pas terminé vos migrations, vous n’êtes pas encore prêt à diriger tous les utilisateurs vers Microsoft 365 pour leur courrier électronique. Que faire alors pour les personnes qui disposent de deux boîtes aux lettres ? Eh bien vous pouvez convertir les boîtes aux lettres qui ont déjà été migrées en utilisateurs à extension messagerie. Lorsque vous passez d’une boîte aux lettres à un utilisateur à extension messagerie, vous pouvez demander à l’utilisateur de Microsoft 365 pour son e-mail au lieu d’accéder à sa boîte aux lettres locale.

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

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Étape 7 : Attribuer des licences à Microsoft 365 utilisateurs

Activez Microsoft 365 comptes d’utilisateur pour les comptes migrés en attribuant des licences. Si vous n’attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour attribuer une licence dans le Centre d'administration Microsoft 365, consultez [Affecter ou annuler l’attribution de licences](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Étape 8 : Exécutez les tâches post-migration

- **Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres** Une fois toutes les boîtes aux lettres locales migrées vers Microsoft 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Microsoft 365 afin de permettre aux utilisateurs de se connecter facilement à leurs nouvelles boîtes aux lettres Microsoft 365 avec des clients Outlook et mobiles. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui que vous utilisez pour votre organisation Microsoft 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l’enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.

    Microsoft 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour les clients Outlook et mobiles. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :

  - **Alias :** autodiscover

  - **Cible :** autodiscover.outlook.com

    Pour plus d’informations, consultez [Ajouter des enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Désactivez des serveurs Exchange locaux.** Une fois que vous avez vérifié que tous les e-mails sont acheminés directement vers les boîtes aux lettres Microsoft 365 et que vous n’avez plus besoin de gérer votre organisation de messagerie locale ou de ne pas planifier l’implémentation d’une solution d’authentification unique, vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.

    Pour plus d’informations, voir les commandes suivantes :

  - [Modifier ou supprimer Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Procédure de suppression d'une organisation Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Procédure de désinstallation d'Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
