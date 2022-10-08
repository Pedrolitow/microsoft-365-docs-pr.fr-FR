---
title: Utilisation de PowerShell pour effectuer une migration IMAP vers Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/19/2022
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: Découvrez comment utiliser PowerShell pour effectuer une migration du protocole IMAP (Internet Mail Access Protocol) vers Microsoft 365.
ms.openlocfilehash: e34a4afd18a0e3234d61261ed7504b25b389aacf
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68179238"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration IMAP vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Dans le cadre du processus de déploiement de Microsoft 365, vous pouvez choisir de migrer le contenu des boîtes aux lettres utilisateur d’un service de messagerie IMAP (Internet Mail Access Protocol) vers Microsoft 365. Cet article décrit les tâches correspondant à une migration de messagerie IMAP à l'aide d'Exchange Online PowerShell.

> [!NOTE]
> Vous pouvez également utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> pour effectuer une migration IMAP. Voir [Migrer vos boîtes aux lettres IMAP](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur d’autres facteurs qui affectent le temps nécessaire pour migrer des boîtes aux lettres vers Microsoft 365, consultez [Performances de migration](/Exchange/mailbox-migration/office-365-migration-best-practices).

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](/exchange/recipients-permissions-exchange-2013-help) topic.

Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour obtenir des instructions[, consultez Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

Les migrations IMAP font l'objet des restrictions suivantes :

- Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.

- Vous ne pouvez pas migrer plus de 500 000 éléments d'une boîte aux lettres d'utilisateur.

- Vous ne pouvez pas non plus migrer des messages d’une taille supérieure à 35 Mo.

## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-an-imap-migration"></a>Étape 1 : Préparez une migration IMAP
<a name="BK_Step1"> </a>

- **Si vous avez un domaine pour votre organisation IMAP, ajoutez-le en tant que domaine accepté de votre organisation Microsoft 365.** Si vous souhaitez utiliser le même domaine que celui que vous possédez déjà pour vos boîtes aux lettres Microsoft 365, vous devez d’abord l’ajouter en tant que domaine accepté à Microsoft 365. Une fois que vous l’avez ajouté, vous pouvez créer vos utilisateurs dans Microsoft 365. Pour plus d’informations, consultez[Vérifier votre domaine](../admin/setup/add-domain.md).

- **Ajoutez chaque utilisateur à Microsoft 365 afin qu’il dispose d’une boîte aux lettres.** Pour obtenir des instructions, consultez[Ajouter des utilisateurs à Microsoft 365 pour les entreprises](../admin/add-users/add-users.md).

- **Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.

- **Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](./urls-and-ip-address-ranges.md).

- **Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.

- **Pour utiliser les cmdlets Exchange Online PowerShell**, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour obtenir des instructions[, consultez Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

    Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

- **Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    La valeur du paramètre **Port** utilisée est généralement 143 pour les connexions chiffrées ou TLS, et 993 pour les connexions SSL.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Étape 2 : Créez un fichier CSV pour un lot de migration IMAP

Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.

Les attributs obligatoires pour chaque utilisateur sont les suivants :

- **EmailAddress** spécifie l’ID utilisateur de la boîte aux lettres Microsoft 365 de l’utilisateur.

- **UserName** spécifie le nom de connexion du compte à utiliser pour accéder à la boîte aux lettres sur le serveur IMAP.

- **Password** spécifie le mot de passe du compte dans la colonne UserName **UserName**.

Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

Pour l'attribut **UserName**, en plus du nom d'utilisateur, vous pouvez utiliser les informations d'identification d'un compte disposant des autorisations nécessaires pour accéder à des boîtes aux lettres sur le serveur IMAP. Vous trouverez ci-dessous quelques-uns des formats spécifiques utilisés pour certains serveurs IMAP :

 **Microsoft Exchange**

Si vous migrez une messagerie à partir de l'implémentation IMAP pour Microsoft Exchange, utilisez le format **Domain/Admin_UserName/User_UserName** pour l'attribut **UserName** dans le fichier CSV. Supposons que vous migrez la messagerie à partir d'Exchange pour Terry Adams, Ann Beebe et Paul Cannon. Vous disposez d’un compte d’administrateur de messagerie, où le nom d’utilisateur est **mailadmin** et le mot **de passe P\@ssw0rd**. Voici à quoi ressemblerait votre fichier CSV :

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot**

Pour les serveurs IMAP qui prennent en charge Simple SASL Authentication and Security Layer (SASL), comme un serveur IMAP Dovecot, utilisez le format **User_UserName*Admin_UserName**, où l'astérisque ( * ) est un caractère de séparation configurable. Supposons que vous migrez l’e-mail de ces mêmes utilisateurs à partir d’un serveur IMAP Dovecot à l’aide du **mailadmin** des informations d’identification de l’administrateur et **de P\@ssw0rd**. Voici à quoi ressemblerait votre fichier CSV :

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint**

Si vous migrez des e-mails à partir du serveur de messages Mirapoint, utilisez le format **#user\@domaine#Admin_UserName#** pour les informations d’identification de l’administrateur. Pour migrer le courrier électronique à partir de Mirapoint à l’aide de **mailadmin** d’informations d’identification d’administrateur et **de P\@ssw0rd**, votre fichier CSV se présente comme suit :

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP :**

Certains systèmes de messagerie source, tels que Courier IMAP, ne prennent pas en charge l’utilisation des informations d’identification d’administrateur de boîte aux lettres pour migrer des boîtes aux lettres vers Microsoft 365. Au lieu de cela, vous pouvez configurer votre système de messagerie source de sorte qu'il utilise des dossiers partagés virtuels. Les dossiers partagés virtuels vous permettent d'utiliser les informations d'identification d'administrateur de boîte aux lettres pour accéder aux boîtes aux lettres utilisateur sur le système de messagerie source. Pour plus d'informations sur la façon de configurer des dossiers partagés virtuels pour Courier IMAP, consultez l'article relatif aux [dossiers partagés](https://go.microsoft.com/fwlink/p/?LinkId=398870).

To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.

Voici un exemple de fichier CSV contenant l'attribut **UserRoot**:

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Étape 3 : Créez un point de terminaison de migration IMAP

Pour migrer correctement l’e-mail, Microsoft 365 doit se connecter au système de messagerie source et communiquer avec lui. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Le point de terminaison de migration définit également le nombre de boîtes aux lettres à migrer simultanément, ainsi que le nombre de boîtes aux lettres à synchroniser simultanément durant la synchronisation incrémentielle qui se produit toutes les 24 heures. Pour créer un point de terminaison de migration pour la migration IMAP, la première étape est de [se connecter à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

Pour créer le point de terminaison de migration IMAP appelé « IMAPEndpoint » dans Exchange Online PowerShell, exécutez la commande suivante :

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Pour plus d'informations sur la cmdlet **New-MigrationEndpoint**, voir [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPEndpoint » :

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Étape 4 : Créez et démarrez un lot de migration IMAP

You can use the [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](/powershell/module/exchange/start-migrationbatch) cmdlet.

La commande Exchange Online PowerShell suivante démarre automatiquement le lot de migration appelé « IMAPBatch1 » à l’aide du point de terminaison IMAP appelé « IMAPEndpoint » :

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécuter la cmdlet [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) pour afficher des informations sur le lot « IMAPBatch1 » :

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Vous pouvez également vérifier que le lot a démarré en exécutant la commande suivante :

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Étape 5 : Acheminer votre e-mail vers Microsoft 365

Les systèmes de messagerie utilisent un enregistrement DNS appelé enregistrement MX pour identifier l'emplacement de remise des messages électroniques. Pendant le processus de migration de la messagerie, votre enregistrement MX pointe vers votre système de messagerie source. Maintenant que la migration de l’e-mail vers Microsoft 365 est terminée, il est temps de pointer votre enregistrement MX vers Microsoft 365. Cela permet de s’assurer que le courrier électronique est remis à vos boîtes aux lettres Microsoft 365. En déplaçant l'enregistrement MX, vous pouvez également désactiver votre ancien système de messagerie lorsque vous êtes prêt.

Pour plusieurs fournisseurs DNS, il existe des instructions spécifiques pour modifier votre enregistrement MX. Si votre fournisseur DNS n’est pas inclus, ou si vous souhaitez avoir une idée des instructions générales, [des instructions d’enregistrement MX générales](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider#add-an-mx-record-for-email-outlook-exchange-online) sont également fournies.

It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.

### <a name="step-6-delete-imap-migration-batch"></a>Étape 6 : Supprimez le lot de migration IMAP

Après avoir modifié l'enregistrement MX et vérifié que tout le courrier est routé vers les boîtes aux lettres Microsoft 365, informez les utilisateurs que leur courrier est envoyé vers Microsoft 365. Après cela, vous pouvez supprimer le lot de migration IMAP. Avant de supprimer le lot de migration, vérifiez les points suivants.

- Tous les utilisateurs utilisent des boîtes aux lettres Microsoft 365. Une fois le lot supprimé, le courrier envoyé aux boîtes aux lettres locales Exchange Server n’est pas copié dans les boîtes aux lettres Microsoft 365 correspondantes.

- Les boîtes aux lettres Microsoft 365 ont été synchronisées au moins une fois après que le courrier leur a été envoyé directement. Pour ce faire, assurez-vous que la valeur de la zone Heure de la dernière synchronisation pour le lot de migration est plus récente que lorsque le courrier a commencé à être routé directement vers les boîtes aux lettres Microsoft 365.

Pour supprimer le lot de migration « IMAPBatch1 » dans Exchange Online PowerShell, exécutez la commande ci-dessous :

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Pour plus d'informations sur la cmdlet **Remove-MigrationBatch**, voir [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le lot « IMAPBatch1 » :

```powershell
Get-MigrationBatch IMAPBatch1"
```

La commande renvoie soit le lot de migration avec l'état **Suppression**, soit un message d'erreur indiquant que le lot de migration est introuvable, confirmant que le lot a été supprimé.

Pour plus d'informations sur la cmdlet **Get-MigrationBatch**, voir [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Voir aussi

[Utilitaire de dépannage de migration IMAP](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)
