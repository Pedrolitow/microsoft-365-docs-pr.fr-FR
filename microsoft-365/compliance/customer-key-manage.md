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
description: Après avoir installé la clé client, découvrez comment la gérer en restaurant des clés AKV et en gérant les autorisations et vos stratégies de chiffrement de données.
ms.openlocfilehash: de85edd5c53fc2b76be4361575e1a85655c0f297
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547084"
---
# <a name="manage-customer-key"></a>Gérer la clé client

Après avoir installé la clé client pour Office 365, vous pouvez gérer vos clés comme décrit dans cet article. En savoir plus sur la clé client dans les rubriques connexes.

## <a name="restore-azure-key-vault-keys"></a>Restaurer les clés Azure Key Vault

Avant d’effectuer une restauration, utilisez les fonctionnalités de récupération fournies par la suppression soft. Toutes les clés utilisées avec la clé client doivent être activées pour la suppression possible. La suppression souple agit comme une corbeille et permet une récupération pendant 90 jours sans avoir à le restaurer. La restauration ne doit être nécessaire que dans des circonstances extrêmes ou inhabituelles, par exemple si la clé ou le coffre de clés est perdu. Si vous devez restaurer une clé à utiliser avec la clé client, dans Azure PowerShell, exécutez l'Restore-AzureKeyVaultKey suivante :
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Par exemple :
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Si le coffre de clés contient déjà une clé du même nom, l’opération de restauration échoue. Restore-AzKeyVaultKey restaure toutes les versions clés et toutes les métadonnées de la clé, y compris le nom de la clé.
  
## <a name="manage-key-vault-permissions"></a>Gérer les autorisations de coffre de clés

Plusieurs cmdlets sont disponibles qui vous permettent d’afficher et, si nécessaire, de supprimer les autorisations de coffre de clés. Vous devrez peut-être supprimer des autorisations, par exemple, lorsqu’un employé quitte l’équipe. Pour chacune de ces tâches, vous allez utiliser Azure PowerShell. Pour plus d’informations sur Azure Powershell, voir [Vue d’ensemble d’Azure PowerShell.](https://docs.microsoft.com/powershell/azure/)

Pour afficher les autorisations de coffre de clés, exécutez Get-AzKeyVault cmdlet.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Par exemple :

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Pour supprimer les autorisations d’un administrateur, exécutez l'Remove-AzKeyVaultAccessPolicy cmdlet :
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Par exemple :

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="manage-data-encryption-policies-deps-with-customer-key"></a>Gérer les stratégies de chiffrement de données (DEP) avec la clé client

La clé client gère les ppp différemment entre les différents services. Par exemple, vous pouvez créer un nombre différent de deP pour les différents services.

**Exchange Online et Skype Entreprise :** Vous pouvez créer jusqu’à 50 dep. Pour obtenir des instructions, voir Créer une stratégie de chiffrement de données à utiliser avec [Exchange Online et Skype Entreprise.](customer-key-set-up.md#create-a-data-encryption-policy-dep-for-use-with-exchange-online-and-skype-for-business)

**Fichiers SharePoint Online, OneDrive Entreprise et Teams :** Une PD DEP s’applique aux données dans un emplacement géographique, également appelé _géo_. Si vous utilisez la fonctionnalité multigé géographique d’Office 365, vous pouvez en créer un par géo. Si vous n’utilisez pas multigéogé, vous pouvez en créer un. Normalement, vous créez le PD DEP lorsque vous définissez la clé client. Pour obtenir des instructions, voir Créer une stratégie de chiffrement de données [(DEP)](customer-key-set-up.md#create-a-data-encryption-policy-dep-for-each-sharepoint-online-and-onedrive-for-business-geo)pour chaque site géographique SharePoint Online et OneDrive Entreprise.

### <a name="view-the-deps-youve-created-for-exchange-online-and-skype-for-business"></a>Afficher les deps que vous avez créés pour Exchange Online et Skype Entreprise

Pour afficher la liste de tous les dep que vous avez créés pour Exchange Online et Skype Entreprise à l’aide de la cmdlet PowerShell Get-DataEncryptionPolicy, complétez ces étapes.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

2. Pour retourner tous les DDP de votre organisation, exécutez la cmdlet Get-DataEncryptionPolicy sans aucun paramètre.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Pour plus d’informations sur Get-DataEncryptionPolicy cmdlet, voir [Get-DataEncryptionPolicy](https://docs.microsoft.com/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Affecter un dep avant de migrer une boîte aux lettres vers le cloud

Lorsque vous affectez le deP, Microsoft 365 chiffre le contenu de la boîte aux lettres à l’aide de la dep affectée lors de la migration. Ce processus est plus efficace que la migration de la boîte aux lettres, l’affectation du dep, puis l’attente du chiffrement, ce qui peut prendre des heures, voire des jours.

Pour affecter un dep à une boîte aux lettres avant de la migrer vers Office 365, exécutez la cmdlet Set-MailUser dans Exchange Online PowerShell :

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez lSet-MailUser cmdlet.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et *DataEncryptionPolicyIdParameter* est l’ID du deP. Pour plus d’informations sur Set-MailUser cmdlet, voir [Set-MailUser](https://docs.microsoft.com/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Déterminer le deP affecté à une boîte aux lettres

Pour déterminer le dep affecté à une boîte aux lettres, utilisez la cmdlet Get-MailboxStatistics. La cmdlet renvoie un identificateur unique (GUID).
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et DataEncryptionPolicyID renvoie le GUID du deP. Pour plus d’informations sur Get-MailboxStatistics cmdlet, [voir Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/get-mailboxstatistics).
  
2. Exécutez Get-DataEncryptionPolicy cmdlet pour connaître le nom convivial du dep auquel la boîte aux lettres est affectée.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Où *GUID est* le GUID renvoyé par l'Get-MailboxStatistics cmdlet à l’étape précédente.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Vérifier que le chiffrement de la clé client est terminé

Que vous venons d’inscrire une clé client, d’attribuer un nouveau dep ou de migrer une boîte aux lettres, utilisez les étapes de cette section pour vous assurer que le chiffrement est terminé.

### <a name="verify-encryption-completes-for-exchange-online-and-skype-for-business"></a>Vérifier que le chiffrement est terminé pour Exchange Online et Skype Entreprise

Le chiffrement d’une boîte aux lettres peut prendre un certain temps. Nous vous recommandons d’attendre 72 heures avant d’essayer de valider le chiffrement après avoir changé de dep ou la première fois que vous affectez un deP à une boîte aux lettres.
  
Utilisez la cmdlet Get-MailboxStatistics pour déterminer si une boîte aux lettres est chiffrée.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

La propriété IsEncrypted renvoie la valeur **true** si la boîte aux lettres est chiffrée et la valeur **false** si la boîte aux lettres n’est pas chiffrée.

Le temps de déplacement des boîtes aux lettres dépend de la taille de la boîte aux lettres. Si la clé client n’a pas entièrement chiffré la boîte aux lettres après 72 heures après l’affectation d’un nouveau PED, contactez le support Microsoft pour obtenir de l’aide. La cmdlet New-MoveRequest n’est plus disponible pour les déplacements de boîtes aux lettres locaux. Pour plus [d’informations,](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) reportez-vous à cette annonce.

### <a name="verify-encryption-completes-for-sharepointonlineonedriveforbusinessandteamsfiles"></a>Vérifier que le chiffrement est terminé pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

Vérifiez l’état du chiffrement en exécutant la cmdlet Get-SPODataEncryptionPolicy comme suit :

```powershell
Get-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl>
```

Le résultat de cette cmdlet inclut :
  
- URI de la clé primaire.

- URI de la clé secondaire.

- État du chiffrement pour la géo. Les états possibles sont les suivants :

  - **Non enregistré :** Le chiffrement de clé client n’a pas encore été appliqué.

  - **Inscription :** Le chiffrement de la clé client a été appliqué et vos fichiers sont en cours de chiffrement. Si la clé de la géo est inscrite, des informations sur le pourcentage de sites de la géo sont également affichées, ce qui vous permet de surveiller la progression du chiffrement.

  - **Inscrit :** Le chiffrement de clé client a été appliqué et tous les fichiers de tous les sites ont été chiffrés.

  - **Déploiement :** Un roulis de touches est en cours. Si la clé de la géo est en cours de déploiement, vous verrez également des informations sur le pourcentage de sites qui ont terminé l’opération de déploiement de clé afin de pouvoir surveiller la progression.

## <a name="unassign-a-dep-from-a-mailbox"></a>Désattribuer un deP d’une boîte aux lettres

Vous désattribuez un deP d’une boîte aux lettres à l’aide de la cmdlet Set-mailbox PowerShell et définissez le `DataEncryptionPolicy` paramètre sur `$NULL` . L’exécution de cette cmdlet désattribue le dep actuellement affecté et recrypte la boîte aux lettres à l’aide de la dep associée aux clés gérées par défaut de Microsoft. Vous ne pouvez pas désattribuer le deP utilisé par les clés gérées microsoft. Si vous ne souhaitez pas utiliser de clés gérées par Microsoft, vous pouvez affecter un autre deP à la boîte aux lettres.

Pour désattribuer le PDV d’une boîte aux lettres à l’aide Set-Mailbox cmdlet PowerShell, complétez ces étapes.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez lSet-Mailbox cmdlet.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Révoquer vos clés et démarrer le processus de purge des données

Vous contrôlez la révocation de toutes les clés racines, y compris la clé de disponibilité. La clé client vous permet de contrôler l’aspect de planification de sortie des exigences réglementaires. Si vous décidez de révoquer vos clés pour vider vos données et quitter le service, le service supprime la clé de disponibilité une fois le processus de purge des données terminé.

Microsoft 365 audite et valide le chemin de purge des données. Pour plus d’informations, voir le rapport SSAE 18 SOC 2 disponible sur le portail [d’confiance des services.](https://servicetrust.microsoft.com/) En outre, Microsoft recommande les documents suivants :

- [Guide d’évaluation et de conformité des risques pour les institutions financières dans microsoft cloud](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Considérations sur la planification de sortie d’O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Le chemin d’accès de la purge des données diffère légèrement entre les différents services.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Révoquer vos clés client et la clé de disponibilité pour Exchange Online et Skype Entreprise

Lorsque vous lancez le chemin d’accès de purge des données pour Exchange Online et Skype Entreprise, vous définissez une demande de purge permanente des données sur un deP. Cela supprime définitivement les données chiffrées dans les boîtes aux lettres à laquelle ce dep est affecté.

Étant donné que vous ne pouvez exécuter l’cmdlet PowerShell que sur une seule dep à la fois, envisagez de réaffecter une seule dep à toutes vos boîtes aux lettres avant de lancer le chemin de purge des données.

> [!WARNING]
> N’utilisez pas le chemin de purge des données pour supprimer un sous-ensemble de vos boîtes aux lettres. Ce processus est destiné uniquement aux clients qui quittent le service.

Pour lancer le chemin d’accès de la purge des données, effectuer les étapes suivantes :

1. Supprimez les autorisations wrap et unwrap pour « O365 Exchange Online » des coffres de clés Azure.

2. À l’aide d’un compte professionnel ou scolaire qui dispose de privilèges d’administrateur général dans votre organisation, connectez-vous [à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

3. Pour chaque PDE qui contient des boîtes aux lettres à supprimer, exécutez la cmdlet [Set-DataEncryptionPolicy](https://docs.microsoft.com/powershell/module/exchange/set-dataencryptionpolicy) comme suit.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Si la commande échoue, assurez-vous que vous avez supprimé les autorisations Exchange Online des deux clés dans Azure Key Vault, comme indiqué précédemment dans cette tâche.Une fois que vous avez définie le commutateur PermanentDataPurgeRequested à l’aide de la cmdlet Set-DataEncryptionPolicy, vous ne pourrez plus affecter ce deP aux boîtes aux lettres.

4. Contactez le support Microsoft et demandez l’eDocument de purge des données.

    À votre demande, Microsoft vous envoie un document juridique pour accusé de réception et autoriser la suppression des données. La personne de votre organisation qui s’est inscrite en tant qu’approuveur dans l’offre FastTrack lors de l’intégration doit signer ce document. Normalement, il s’agit d’un cadre supérieur ou d’une autre personne désignée de votre entreprise qui est légalement autorisé à signer les formalités au nom de votre organisation.

5. Une fois que votre représentant a signé le document juridique, renvoyez-le à Microsoft (généralement via une signature eDoc).

    Une fois que Microsoft a reçu le document juridique, Microsoft exécute des cmdlets pour déclencher la purge des données qui supprime d’abord la stratégie, marque les boîtes aux lettres pour suppression définitive, puis supprime la clé de disponibilité. Une fois le processus de purge des données terminé, les données ont été purgées, sont inaccessibles à Exchange Online et ne sont pas récupérables.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepointonlineonedriveforbusinessandteamsfiles"></a>Révoquer vos clés client et la clé de disponibilité pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

Pour lancer le chemin d’accès de purge des données pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, effectuer les étapes suivantes :

1. Révoquer l’accès à Azure Key Vault. Tous les administrateurs de coffre de clés doivent accepter de révoquer l’accès.

   Vous ne supprimez pas le coffre de clés Azure pour SharePoint Online. Les coffres de clés peuvent être partagés entre plusieurs locataires et deps SharePoint Online.

2. Contactez Microsoft pour supprimer la clé de disponibilité.

    Lorsque vous contactez Microsoft pour supprimer la clé de disponibilité, nous vous envoyons un document juridique. La personne de votre organisation qui s’est inscrite en tant qu’approuveur dans l’offre FastTrack lors de l’intégration doit signer ce document. Normalement, il s’agit d’un cadre supérieur ou d’une autre personne désignée de votre entreprise qui est légalement autorisée à signer les formalités au nom de votre organisation.

3. Une fois que votre représentant signe le document juridique, renvoyez-le à Microsoft (généralement par le biais d’une signature eDoc).

   Une fois que Microsoft a reçu le document juridique, nous exécuterons des cmdlets pour déclencher la purge des données qui effectue la suppression de chiffrement de la clé de client, de la clé de site et de toutes les clés de document individuelles, ce qui a pour effet de rompre irrévocablement la hiérarchie des clés. Une fois les cmdlets de purge des données terminées, vos données ont été purgées.

## <a name="related-articles"></a>Articles connexes

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [Référentiel sécurisé client](customer-lockbox-requests.md)

- [Chiffrement de service](office-365-service-encryption.md)
