---
title: Gérer la clé client
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 02/05/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Après avoir configuré la clé client, Découvrez comment la gérer en restaurant les clés AKV et en gérant les autorisations et vos stratégies de chiffrement de données.
ms.openlocfilehash: 4796fcef69e052725b635acb4170d73bb36de787
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43635600"
---
# <a name="manage-customer-key"></a>Gérer la clé client

Une fois que vous avez configuré la clé client pour Office 365, vous pouvez gérer vos clés comme décrit dans cet article. Pour plus d’informations sur la clé client, consultez les rubriques connexes.

## <a name="restore-azure-key-vault-keys"></a>Restaurer les clés Azure Key Vault

Avant d’effectuer une restauration, utilisez les fonctionnalités de récupération fournies par la fonction de suppression récupérable. Toutes les clés utilisées avec la clé client doivent être activées pour la suppression logicielle. La suppression douce se comporte comme une corbeille et permet la récupération jusqu’à 90 jours sans nécessiter de restauration. La restauration doit être uniquement requise dans des circonstances extrêmes ou inhabituelles, par exemple en cas de perte de la clé ou du coffre-fort. Si vous devez restaurer une clé à utiliser avec la clé client, dans Azure PowerShell, exécutez la cmdlet Restore-AzureKeyVaultKey comme suit :
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Par exemple :
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Si le coffre-fort de clés contient déjà une clé portant le même nom, l’opération de restauration échoue. Restore-AzKeyVaultKey restaure toutes les versions clés et toutes les métadonnées pour la clé, y compris le nom de la clé.
  
## <a name="manage-key-vault-permissions"></a>Gérer les autorisations de coffre-fort

Plusieurs cmdlets sont disponibles, qui vous permettent d’afficher et, si nécessaire, de supprimer des autorisations de coffre-fort clé. Vous devrez peut-être supprimer des autorisations, par exemple, lorsqu’un employé quitte l’équipe. Pour chacune de ces tâches, vous allez utiliser Azure PowerShell. Pour plus d’informations sur Azure PowerShell, consultez la rubrique [Overview of Azure PowerShell](https://docs.microsoft.com/powershell/azure/).

Pour afficher les autorisations de coffre-fort, exécutez la cmdlet Get-AzKeyVault.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Par exemple :

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Pour supprimer les autorisations d’un administrateur, exécutez l’applet de commande Remove-AzKeyVaultAccessPolicy :
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Par exemple :

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="manage-data-encryption-policies-deps-with-customer-key"></a>Gérer les stratégies de chiffrement de données (DEPs) avec la clé client

Les handles de clé du client DEPs différemment entre les différents services. Par exemple, vous pouvez créer un nombre différent de DEPs pour les différents services.

**Exchange Online et Skype entreprise :** Vous pouvez créer jusqu’à 50 DEPs. Pour obtenir des instructions, voir [Create a Data Encryption Policy (DEP) for use with Exchange Online and Skype for Business](customer-key-set-up.md#create-a-data-encryption-policy-dep-for-use-with-exchange-online-and-skype-for-business).

**SharePoint Online, OneDrive entreprise et fichiers teams :** Une DEP s’applique aux données d’un emplacement géographique, également appelé _géo_. Si vous utilisez la fonctionnalité multigéographique d’Office 365, vous pouvez créer une DEP par zone géographique. Si vous n’utilisez pas de multi-géo, vous pouvez créer une DEP. Normalement, vous créez la DEP lorsque vous configurez la clé client. Pour obtenir des instructions, consultez [la rubrique créer une stratégie de chiffrement de données (DEP) pour chaque zone géographique SharePoint Online et OneDrive entreprise](customer-key-set-up.md#create-a-data-encryption-policy-dep-for-each-sharepoint-online-and-onedrive-for-business-geo).

### <a name="view-the-deps-youve-created-for-exchange-online-and-skype-for-business"></a>Afficher le DEPs que vous avez créé pour Exchange Online et Skype entreprise

Pour afficher la liste de tous les DEPs que vous avez créés pour Exchange Online et Skype entreprise à l’aide de l’applet de commande Get-DataEncryptionPolicy PowerShell, procédez comme suit.

1. À l’aide d’un compte professionnel ou scolaire doté d’autorisations d’administrateur globales dans votre organisation, [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).

2. Pour renvoyer tous les DEPs de votre organisation, exécutez la cmdlet Get-DataEncryptionPolicy sans aucun paramètre.

  ```powershell
  Get-DataEncryptionPolicy
  ```

  Pour plus d’informations sur la cmdlet Get-DataEncryptionPolicy, consultez la rubrique [Get-DataEncryptionPolicy](https://docs.microsoft.com/powershell/module/exchange/encryption-and-certificates/get-dataencryptionpolicy?view=exchange-ps).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Affectation d’une DEP avant la migration d’une boîte aux lettres vers le Cloud

Lorsque vous affectez la DEP, Microsoft 365 chiffre le contenu de la boîte aux lettres à l’aide de la DEP attribuée lors de la migration. Ce processus est plus efficace que la migration de la boîte aux lettres, l’affectation de la DEP, puis l’attente du chiffrement, ce qui peut prendre des heures voire des jours.

Pour affecter une DEP à une boîte aux lettres avant de la migrer vers Office 365, exécutez la cmdlet Set-MailUser dans Exchange Online PowerShell :

1. À l’aide d’un compte professionnel ou scolaire doté d’autorisations d’administrateur globales dans votre organisation, [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).

2. Exécutez la cmdlet Set-MailUser.

  ```powershell
  Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
  ```

  Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et *DATAENCRYPTIONPOLICYIDPARAMETER* est l’ID de la DEP. Pour plus d’informations sur la cmdlet Set-MailUser, voir [Set-MailUser](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/set-mailuser?view=exchange-ps).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Déterminer la DEP affectée à une boîte aux lettres

Pour déterminer la DEP affectée à une boîte aux lettres, utilisez la cmdlet Get-MailboxStatistics. L’applet de commande renvoie un identificateur unique (GUID).
  
1. À l’aide d’un compte professionnel ou scolaire doté d’autorisations d’administrateur globales dans votre organisation, [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et DataEncryptionPolicyID renvoie le GUID de la DEP. Pour plus d’informations sur la cmdlet Get-MailboxStatistics, consultez la rubrique [Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/get-mailboxstatistics?view=exchange-ps).
  
2. Exécutez la cmdlet Get-DataEncryptionPolicy pour connaître le nom convivial de la DEP à laquelle la boîte aux lettres est affectée.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Où *GUID* est le GUID renvoyé par la cmdlet Get-MailboxStatistics à l’étape précédente.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Vérifier que la clé client a terminé le chiffrement

Qu’il s’agisse d’une clé client, d’une nouvelle DEP ou d’une migration de boîte aux lettres, utilisez les étapes de cette section pour vous assurer que le chiffrement est terminé.

### <a name="verify-encryption-completes-for-exchange-online-and-skype-for-business"></a>Vérifier que le chiffrement est terminé pour Exchange Online et Skype entreprise

Le chiffrement d’une boîte aux lettres peut prendre du temps. Nous vous recommandons d’attendre 72 heures avant de valider le chiffrement après avoir modifié une DEP ou la première fois que vous affectez une DEP à une boîte aux lettres.
  
Utilisez la cmdlet Get-MailboxStatistics pour déterminer si une boîte aux lettres est chiffrée.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

La propriété IsEncrypted renvoie la valeur **true** si la boîte aux lettres est chiffrée et la valeur **false** si la boîte aux lettres n’est pas chiffrée.

Le temps nécessaire pour effectuer des déplacements de boîtes aux lettres dépend de la taille de la boîte aux lettres. Si la clé client n’a pas entièrement chiffré la boîte aux lettres après 72 heures après l’heure où vous affectez une nouvelle DEP, lancez un déplacement de boîte aux lettres. Pour ce faire, utilisez la cmdlet New-MoveRequest et fournissez l’alias de la boîte aux lettres. Par exemple :
  
```powershell
New-MoveRequest <alias>
```

Pour plus d’informations sur cette cmdlet, consultez la rubrique [Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps).

### <a name="verify-encryption-completes-for-sharepointonlineonedriveforbusinessandteamsfiles"></a>Vérifier que le chiffrement est terminé pour SharePoint Online, OneDrive entreprise et les fichiers teams

Vérifiez l’état du chiffrement en exécutant la cmdlet Get-SPODataEncryptionPolicy comme suit :

```powershell
Get-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl>
```

La sortie de cette cmdlet comprend les éléments suivants :
  
- URI de la clé primaire.

- URI de la clé secondaire.

- État de chiffrement de la zone géographique. Les États possibles sont les suivants :

  - Non **enregistré :** Le chiffrement de clé client n’a pas encore été appliqué.

  - **Inscription :** Le chiffrement de clés client a été appliqué et vos fichiers sont en cours de chiffrement. Si la clé de la zone géographique est inscrite, vous verrez également des informations sur le pourcentage de sites dans la zone géographique, afin que vous puissiez surveiller la progression du chiffrement.

  - **Inscrit :** Le chiffrement de clés client a été appliqué et tous les fichiers de tous les sites ont été chiffrés.

  - **Roulement :** Un roulement de clé est en cours. Si la clé pour le géo est propagée, vous verrez également des informations sur le pourcentage de sites ayant terminé l’opération de Roll Key afin de pouvoir surveiller la progression.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Révoquer vos clés et démarrer le processus de purge des données

Vous contrôlez la révocation de toutes les clés racines, y compris la clé de disponibilité. La clé client permet de contrôler l’aspect de la planification de sortie des exigences réglementaires. Si vous décidez d’annuler vos clés pour purger vos données et quitter le service, le service supprime la clé de disponibilité une fois le processus de purge des données terminé.

Microsoft 365 audite et valide le chemin de purge des données. Pour plus d’informations, reportez-vous au rapport SSAE 18 SOC 2 disponible sur le [portail d’approbation de services](https://servicetrust.microsoft.com/). En outre, Microsoft recommande les documents suivants :

- [Guide de conformité et d’évaluation des risques pour les établissements financiers dans le Cloud Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Considérations relatives à la planification de la sortie de O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Le chemin de purge des données diffère légèrement entre les différents services.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Révoquer vos clés client et la clé de disponibilité pour Exchange Online et Skype entreprise

Lorsque vous lancez le chemin de purge des données pour Exchange Online et Skype entreprise, vous définissez une demande de purge des données permanente sur une DEP. Cette opération supprime définitivement les données chiffrées dans les boîtes aux lettres auxquelles cette DEP est attribuée.

Étant donné que vous ne pouvez exécuter l’applet de commande PowerShell que sur une seule DEP à la fois, envisagez de réaffecter une seule DEP à toutes vos boîtes aux lettres avant d’initier le chemin de purge des données.

> [!WARNING]
> N’utilisez pas le chemin de purge des données pour supprimer un sous-ensemble de vos boîtes aux lettres. Ce processus est destiné uniquement aux clients qui quittent le service.

Pour lancer le chemin de purge des données, procédez comme suit :

1. Supprimez les autorisations Wrap et Unwrap pour « O365 Exchange Online » à partir de coffres de clés Azure.

2. À l’aide d’un compte professionnel ou scolaire disposant de privilèges d’administrateur général dans votre organisation, [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).

3. Pour chaque DEP contenant des boîtes aux lettres que vous souhaitez supprimer, exécutez la cmdlet [Set-DataEncryptionPolicy](https://docs.microsoft.com/powershell/module/exchange/encryption-and-certificates/set-dataencryptionpolicy) comme suit.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Si la commande échoue, vérifiez que vous avez supprimé les autorisations Exchange Online des deux clés dans le coffre de clés Azure, comme indiqué précédemment dans cette tâche.Une fois que vous avez défini le commutateur PermanentDataPurgeRequested à l’aide de l’applet de commande Set-DataEncryptionPolicy, vous ne pourrez plus affecter cette DEP à des boîtes aux lettres.

4. Contactez le support Microsoft et demandez la purge des données eDocument.

    À votre demande, Microsoft vous envoie un document légal pour valider et autoriser la suppression des données. La personne de votre organisation qui s’est inscrite en tant qu’approbateur dans l’offre FastTrack pendant l’intégration doit signer ce document. En règle générale, il s’agit d’un cadre ou d’une autre personne désignée dans votre société qui est légalement autorisée à signer les documents au nom de votre organisation.

5. Une fois que votre représentant a signé le document juridique, renvoyez-le à Microsoft (généralement par le biais d’une signature eDoc).

    Une fois que Microsoft reçoit le document juridique, Microsoft exécute des applets de commande pour déclencher la purge des données qui supprime la stratégie, marque les boîtes aux lettres pour la suppression définitive, puis supprime la clé de disponibilité. Une fois le processus de purge des données terminé, les données ont été purgées, sont inaccessibles à Exchange Online et ne sont pas récupérables.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepointonlineonedriveforbusinessandteamsfiles"></a>Révoquer vos clés client et la clé de disponibilité pour les fichiers SharePoint Online, OneDrive entreprise et Teams

Pour lancer le chemin de purge des données pour SharePoint Online, OneDrive entreprise et les fichiers Teams, procédez comme suit :

1. Révoquer l’accès au coffre de clés Azure. Tous les administrateurs de coffre-fort principal doivent accepter de révoquer l’accès.

   Vous ne supprimez pas le coffre-fort de clés Azure pour SharePoint Online. Les coffres clés peuvent être partagés entre plusieurs clients SharePoint Online et DEPs.

2. Contactez Microsoft pour supprimer la clé de disponibilité.

    Lorsque vous contactez Microsoft pour supprimer la clé de disponibilité, nous vous enverrons un document légal. La personne de votre organisation qui s’est inscrite en tant qu’approbateur dans l’offre FastTrack pendant l’intégration doit signer ce document. En règle générale, il s’agit d’un cadre ou d’une autre personne désignée dans votre société qui est légalement habilitée à signer des documents au nom de votre organisation.

3. Une fois que votre représentant signe le document juridique, renvoyez-le à Microsoft (généralement par le biais d’une signature eDoc).

   Une fois que Microsoft reçoit le document juridique, nous exécutons des cmdlets pour déclencher la purge des données qui effectue la suppression de chiffrement de la clé de client, de la clé de site et de toutes les clés individuelles par document, tout en fractionnant la hiérarchie de clés. Une fois les cmdlets de purge des données terminées, vos données ont été purgées.

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec clé client](customer-key-overview.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [Référentiel sécurisé client](customer-lockbox-requests.md)

- [Chiffrement de service](office-365-service-encryption.md)
