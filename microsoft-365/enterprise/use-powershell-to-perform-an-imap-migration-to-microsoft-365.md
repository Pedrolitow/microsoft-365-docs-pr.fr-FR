---
title: Utilisation de PowerShell pour effectuer une migration IMAP vers Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: Découvrez comment utiliser PowerShell pour effectuer une migration du protocole IMAP (Internet Mail Access Protocol) vers Microsoft 365.
ms.openlocfilehash: a01eaf367f6780aafe5491e5da66c6aae777040e
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67671894"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration IMAP vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Dans le cadre du processus de déploiement de Microsoft 365, vous pouvez choisir de migrer le contenu des boîtes aux lettres utilisateur d’un service de messagerie IMAP (Internet Mail Access Protocol) vers Microsoft 365. Cet article décrit les tâches correspondant à une migration de messagerie IMAP à l'aide d'Exchange Online PowerShell.

> [!NOTE]
> Vous pouvez également utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> pour effectuer une migration IMAP. Voir [Migrer vos boîtes aux lettres IMAP](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur d’autres facteurs qui affectent le temps nécessaire pour migrer des boîtes aux lettres vers Microsoft 365, consultez [Performances de migration](/Exchange/mailbox-migration/office-365-migration-best-practices).

Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](/exchange/recipients-permissions-exchange-2013-help).

Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour obtenir des instructions[, consultez Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

Les migrations IMAP font l'objet des restrictions suivantes :

- Vous pouvez migrer uniquement des éléments figurant dans la boîte de réception ou d'autres dossiers de courrier d'un utilisateur. Vous ne pouvez pas migrer des contacts, des éléments du calendrier ou des tâches.

- Vous ne pouvez pas migrer plus de 500 000 éléments d'une boîte aux lettres d'utilisateur.

- Vous ne pouvez pas non plus migrer des messages d’une taille supérieure à 35 Mo.

## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-an-imap-migration"></a>Étape 1 : Préparez une migration IMAP
<a name="BK_Step1"> </a>

- **Si vous avez un domaine pour votre organisation IMAP, ajoutez-le en tant que domaine accepté de votre organisation Microsoft 365.** Si vous souhaitez utiliser le même domaine que celui que vous possédez déjà pour vos boîtes aux lettres Microsoft 365, vous devez d’abord l’ajouter en tant que domaine accepté à Microsoft 365. Une fois que vous l’avez ajouté, vous pouvez créer vos utilisateurs dans Microsoft 365. Pour plus d’informations, consultez[Vérifier votre domaine](../admin/setup/add-domain.md).

- **Ajoutez chaque utilisateur à Microsoft 365 afin qu’il dispose d’une boîte aux lettres.** Pour obtenir des instructions, consultez[Ajouter des utilisateurs à Microsoft 365 pour les entreprises](../admin/add-users/add-users.md).

- **Obtenez le nom de domaine complet (FQDN) du serveur IMAP.** Lorsque vous créez un point de terminaison de migration IMAP, vous devez fournir le nom de domaine complet (FQDN) (également appelénom complet de l'ordinateur) du serveur IMAP à partir duquel vous allez migrer les données de boîte aux lettres. Utilisez un client IMAP ou la commande PING pour vérifier que vous pouvez utiliser le FQDN pour communiquer avec le serveur IMAP sur Internet.

- **Configurez le pare-feu pour autoriser les connexions IMAP.** Il se peut que vous deviez ouvrir des portes dans le pare-feu de l'organisation hébergeant le serveur IMAP afin que le trafic réseau en provenance du centre de données Microsoft durant la migration soit autorisé à pénétrer dans l'organisation hébergeant le serveur IMAP. Pour obtenir la liste des adresses IP utilisées par les centres de données Microsoft, consultez la rubrique relative aux [URL Exchange Online et plages d'adresses IP](./urls-and-ip-address-ranges.md).

- **Attribuez les autorisations de compte administrateur pour accéder aux boîtes aux lettres de votre organisation**. Si vous utilisez des informations d'identification d'administrateur dans le fichier CSV, le compte utilisé doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales. Celles-ci sont déterminées par le serveur IMAP spécifique.

- **Pour utiliser les cmdlets Exchange Online PowerShell**, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour obtenir des instructions[, consultez Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

    Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

- **Vérifiez que vous pouvez vous connecter à votre serveur IMAP.** Pour tester les paramètres de connexion à votre serveur IMAP, exécutez la commande suivante dans Exchange Online PowerShell.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    La valeur du paramètre **Port** utilisée est généralement 143 pour les connexions chiffrées ou TLS, et 993 pour les connexions SSL.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Étape 2 : Créez un fichier CSV pour un lot de migration IMAP

Identifiez le groupe d'utilisateurs dont vous voulez migrer les boîtes aux lettres dans un lot de migration IMAP. Chaque ligne du fichier CSV contient les informations nécessaires pour se connecter à une boîte aux lettres dans le système de messagerie IMAP.

Les attributs obligatoires pour chaque utilisateur sont les suivants :

- **EmailAddress** spécifie l’ID utilisateur de la boîte aux lettres Microsoft 365 de l’utilisateur.

- **UserName** spécifie le nom de connexion du compte à utiliser pour accéder à la boîte aux lettres sur le serveur IMAP.

- **Password** spécifie le mot de passe du compte dans la colonne UserName **UserName**.

Voici un exemple du format du fichier CSV. Dans cet exemple, trois boîtes aux lettres sont migrées :

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

Pour migrer des boîtes aux lettres après avoir configuré des dossiers partagés virtuels sur votre système de messagerie source, vous devez inclure l'attribut facultatif **UserRoot** dans le fichier de migration. Cet attribut spécifie l'emplacement de la boîte aux lettres de chaque utilisateur dans la structure de dossiers partagés virtuels sur le système de messagerie source. Par exemple, le chemin d'accès de la boîte aux lettres de Terry est /users/terry.adams.

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

Vous pouvez également ajouter des paramètres pour spécifier les migrations simultanées, les migrations incrémentielles simultanées et le port à utiliser. La commande Exchange Online PowerShell suivante crée un point de terminaison de migration IMAP appelé « IMAPEndpoint » qui prend en charge 50 migrations simultanées et jusqu'à 25 synchronisations incrémentielles simultanées. Il configure également le point de terminaison pour utiliser le port 143 pour le chiffrement TLS.

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

La cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) permet de créer un lot pour une migration IMAP. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer son traitement par la suite à l'aide de la cmdlet [Start-MigrationBatch](/powershell/module/exchange/start-migrationbatch).

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

Il faut compter jusqu’à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l’enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : Étape 6 : Supprimez le lot de migration IMAP

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
