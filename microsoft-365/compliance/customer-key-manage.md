---
title: Gérer la clé client
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Après avoir installé la clé client, découvrez comment la gérer en restaurant des clés AKV, en gérant les autorisations et en créant et en attribuant des stratégies de chiffrement de données.
ms.openlocfilehash: 2329df5a7bb7fac7a6013e1236024ba0a4a31567
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60172454"
---
# <a name="manage-customer-key"></a>Gérer la clé client

Une fois que vous avez installé la clé client pour Office 365, vous devez créer et affecter une ou plusieurs stratégies de chiffrement de données (DEP). Une fois que vous avez affecté vos dep, vous pouvez gérer vos clés comme décrit dans cet article. En savoir plus sur la clé client dans les rubriques connexes.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Créer un PD DEP pour une utilisation avec plusieurs charges de travail pour tous les utilisateurs clients

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer le client. Pour plus d’informations, [voir Configurer la clé client.](customer-key-set-up.md) Pour créer le PED, vous avez besoin des URIs de coffre de clés que vous avez obtenus lors de l’installation. Pour plus d’informations, [voir Obtenir l’URI de chaque clé Azure Key Vault.](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key)

Pour créer une PD DEP à charges multiples, suivez les étapes suivantes :
  
1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Pour créer un dep, utilisez l'New-M365DataAtRestEncryptionPolicy cmdlet.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Où :

   - *PolicyName est* le nom que vous souhaitez utiliser pour la stratégie. Les noms ne peuvent pas contenir d’espaces. Par exemple, Contoso_Global.

   - *KeyVaultURI1 est* l’URI de la première clé de la stratégie. Par exemple, <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2 est* l’URI de la deuxième clé de la stratégie. Par exemple, <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. Séparez les deux URS par une virgule et un espace.

   - *La description de* la stratégie est une description conviviale de la stratégie qui vous aidera à vous souvenir de l’objectif de la stratégie. Vous pouvez inclure des espaces dans la description. Par exemple, « Stratégie racine pour plusieurs charges de travail pour tous les utilisateurs du client ».

Exemple :

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Attribuer une stratégie à charges de travail multiples

Attribuez le PDV à l’aide Set-M365DataAtRestEncryptionPolicyAssignment cmdlet. Une fois la stratégie assignée, Microsoft 365 chiffre les données avec la clé identifiée dans le PDV.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Où *PolicyName est* le nom de la stratégie. Par exemple, Contoso_Global.

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Créer un deP à utiliser avec des boîtes aux lettres Exchange Online de messagerie

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer Azure Key Vault. Pour plus d’informations, [voir Configurer la clé client.](customer-key-set-up.md) Vous effectuerez ces étapes en vous connectant à distance à Exchange Online avec Windows PowerShell.

Un dep est associé à un ensemble de clés stockées dans Azure Key Vault. Vous affectez un deP à une boîte aux lettres dans Microsoft 365. Microsoft 365 utiliser les clés identifiées dans la stratégie pour chiffrer la boîte aux lettres. Pour créer le PED, vous avez besoin des URIs de coffre de clés que vous avez obtenus lors de l’installation. Pour plus d’informations, [voir Obtenir l’URI de chaque clé Azure Key Vault.](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key)

N’oubliez pas ! Lorsque vous créez un deP, vous spécifiez deux clés dans deux coffres de clés Azure différents. Créez ces clés dans deux régions Azure distinctes pour assurer la redondance géographique.

Pour créer un deP à utiliser avec une boîte aux lettres, suivez les étapes suivantes :
  
1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général ou d’administrateur Exchange Online dans votre organisation, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Pour créer une dep, utilisez la cmdlet New-DataEncryptionPolicy en tapant la commande suivante.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Où :

   - *PolicyName est* le nom que vous souhaitez utiliser pour la stratégie. Les noms ne peuvent pas contenir d’espaces. Par exemple, USA_mailboxes.

   - *La description de* la stratégie est une description conviviale de la stratégie qui vous aidera à vous souvenir de l’objectif de la stratégie. Vous pouvez inclure des espaces dans la description. Par exemple, « Clé racine pour les boîtes aux lettres aux États-Unis et ses territoires ».

   - *KeyVaultURI1 est* l’URI de la première clé de la stratégie. Par exemple, <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2 est* l’URI de la deuxième clé de la stratégie. Par exemple, <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Séparez les deux URS par une virgule et un espace.

   Exemple :
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Affecter un deP à une boîte aux lettres

Affectez le deP à une boîte aux lettres à l’aide Set-Mailbox cmdlet. Une fois la stratégie assignée, Microsoft 365 pouvez chiffrer la boîte aux lettres avec la clé identifiée dans le PDV.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailboxIdParameter* spécifie une boîte aux lettres utilisateur. Pour plus d’informations sur la cmdlet Set-Mailbox, voir [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Dans les environnements hybrides, vous pouvez affecter un deP aux données de boîte aux lettres sur site qui sont synchronisées dans votre Exchange Online client. Pour affecter un dep à ces données de boîte aux lettres synchronisées, vous devez utiliser la cmdlet Set-MailUser de messagerie. Pour plus d’informations sur les données de boîte aux lettres dans l’environnement hybride, voir les boîtes aux lettres sur site utilisant Outlook pour iOS et Android avec l’authentification [moderne hybride.](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailUserIdParameter* spécifie un utilisateur de messagerie (également appelé utilisateur à messagerie). Pour plus d’informations sur la cmdlet Set-MailUser, voir [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>Créer une PD DEP à utiliser avec SharePoint Online, OneDrive Entreprise et Teams fichiers

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer Azure Key Vault. Pour plus d’informations, [voir Configurer la clé client.](customer-key-set-up.md)
  
Pour configurer la clé client pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, vous devez effectuer ces étapes en vous connectant à distance à SharePoint Online avec Windows PowerShell.
  
Vous associez un deP à un ensemble de clés stockées dans Azure Key Vault. Vous appliquez un deP à toutes vos données dans un emplacement géographique, également appelé géo. Si vous utilisez la fonctionnalité multigéogé Office 365, vous pouvez créer une dep par géo avec la possibilité d’utiliser différentes clés par géo. Si vous n’utilisez pas multigéogé, vous pouvez en créer un dans votre organisation pour l’utiliser avec les fichiers SharePoint Online, OneDrive Entreprise et Teams. Microsoft 365 utilise les clés identifiées dans la PD DEP pour chiffrer vos données dans cette géo. Pour créer le PED, vous avez besoin des URIs de coffre de clés que vous avez obtenus lors de l’installation. Pour plus d’informations, [voir Obtenir l’URI de chaque clé Azure Key Vault.](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key)
  
N’oubliez pas ! Lorsque vous créez un deP, vous spécifiez deux clés dans deux coffres de clés Azure différents. Créez ces clés dans deux régions Azure distinctes pour assurer la redondance géographique.
  
Pour créer un dep, vous devez vous connecter à distance à SharePoint Online à l’aide de Windows PowerShell.
  
1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, Connecter [à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. Dans l’Microsoft Office SharePoint Online Management Shell, exécutez la cmdlet Register-SPODataEncryptionPolicy suivante :

   ```powershell
   Register-SPODataEncryptionPolicy <adminSiteCollectionURL> -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Exemple :
  
   ```powershell
   Register-SPODataEncryptionPolicy  https://contoso.sharepoint.com -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a’
   ```

   Lorsque vous inscrivez la PD DEP, le chiffrement commence sur les données de la géo. Le chiffrement peut prendre un certain temps. Pour plus d’informations sur l’utilisation de ce paramètre, voir [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Afficher les deps que vous avez créés pour Exchange Online boîtes aux lettres

Pour afficher la liste de tous les dep que vous avez créés pour les boîtes aux lettres, utilisez la cmdlet PowerShell Get-DataEncryptionPolicy'accès.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

2. Pour retourner tous les DDP de votre organisation, exécutez l'Get-DataEncryptionPolicy cmdlet sans aucun paramètre.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Pour plus d’informations sur Get-DataEncryptionPolicy cmdlet, voir [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Affecter un dep avant de migrer une boîte aux lettres vers le cloud

Lorsque vous affectez le deP, Microsoft 365 chiffre le contenu de la boîte aux lettres à l’aide de la PD DEP affectée pendant la migration. Ce processus est plus efficace que la migration de la boîte aux lettres, l’affectation du dep, puis l’attente du chiffrement, ce qui peut prendre des heures, voire des jours.

Pour affecter un dep à une boîte aux lettres avant de la migrer vers Office 365, exécutez la cmdlet Set-MailUser dans Exchange Online PowerShell :

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez lSet-MailUser cmdlet.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et *DataEncryptionPolicyIdParameter* est l’ID du deP. Pour plus d’informations sur la cmdlet Set-MailUser, voir [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Déterminer le deP affecté à une boîte aux lettres

Pour déterminer le dep affecté à une boîte aux lettres, utilisez la cmdlet Get-MailboxStatistics. La cmdlet renvoie un identificateur unique (GUID).
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et DataEncryptionPolicyID renvoie le GUID du deP. Pour plus d’informations sur Get-MailboxStatistics cmdlet, [voir Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. Exécutez Get-DataEncryptionPolicy cmdlet pour connaître le nom convivial du dep auquel la boîte aux lettres est affectée.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Où *GUID est* le GUID renvoyé par l'Get-MailboxStatistics cmdlet à l’étape précédente.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Vérifier que le chiffrement de la clé client est terminé

Que vous avez inscrit une clé client, affecté un nouveau dep ou migré une boîte aux lettres, utilisez les étapes de cette section pour vous assurer que le chiffrement est terminé.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Vérifier que le chiffrement est terminé pour Exchange Online boîtes aux lettres

Le chiffrement d’une boîte aux lettres peut prendre un certain temps. Pour le premier chiffrement, la boîte aux lettres doit également passer complètement d’une base de données à une autre pour que le service puisse chiffrer la boîte aux lettres.
  
Utilisez la cmdlet Get-MailboxStatistics pour déterminer si une boîte aux lettres est chiffrée.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

La propriété IsEncrypted renvoie la valeur **true** si la boîte aux lettres est chiffrée et la valeur **false** si la boîte aux lettres n’est pas chiffrée. Le temps de déplacement des boîtes aux lettres dépend du nombre de boîtes aux lettres à laquelle vous attribuez une dep pour la première fois et de la taille des boîtes aux lettres. Si les boîtes aux lettres n’ont pas été chiffrées après une semaine à partir de l’heure à partir de la PED, contactez Microsoft.

La cmdlet New-MoveRequest n’est plus disponible pour les déplacements de boîtes aux lettres locales. Pour plus [d’informations,](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) reportez-vous à cette annonce.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Vérifier que le chiffrement est terminé pour SharePoint en ligne, OneDrive Entreprise et Teams fichiers

Vérifiez l’état du chiffrement en exécutant la cmdlet Get-SPODataEncryptionPolicy comme suit :

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Le résultat de cette cmdlet inclut :
  
- URI de la clé primaire.

- URI de la clé secondaire.

- État du chiffrement pour la géo. Les états possibles sont les suivants :

  - **Non enregistré :** Le chiffrement de clé client n’a pas encore été appliqué.

  - **Inscription :** Le chiffrement de la clé client a été appliqué et vos fichiers sont en cours de chiffrement. Si la clé de la géo est inscrite, des informations sur le pourcentage de sites de la géo sont également affichées, ce qui vous permet de surveiller la progression du chiffrement.

  - **Inscrit :** Le chiffrement de clé client a été appliqué et tous les fichiers de tous les sites ont été chiffrés.

  - **Déploiement :** Un roulis de touches est en cours. Si la clé de la géo est en cours de déploiement, vous verrez également des informations sur le pourcentage de sites qui ont terminé l’opération de déploiement de clé afin de pouvoir surveiller la progression.

- Il produit également le pourcentage de sites intégrés.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Obtenir des détails sur les PD DEP que vous utilisez avec plusieurs charges de travail

Pour obtenir des détails sur tous les dep que vous avez créés pour utiliser plusieurs charges de travail, complétez les étapes suivantes :

1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans Windows PowerShell fenêtre.

   - Pour renvoyer la liste de tous les dep de charges de travail multiples dans l’organisation, exécutez cette commande.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Pour renvoyer des détails sur un deP spécifique, exécutez cette commande. Cet exemple renvoie des informations détaillées sur la PED nommée « Contoso_Global ».

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Obtenir des informations sur les affectations PDN à charges multiples

Pour savoir quel deP est actuellement affecté à votre client, suivez ces étapes. 

1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans Windows PowerShell fenêtre.

2. Tapez cette commande.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Désactiver un PD DEP à charges multiples

Avant de désactiver une PD DEP à charges multiples, désattribuez-la des charges de travail de votre client. Pour désactiver un deP utilisé avec plusieurs charges de travail, effectuer les étapes suivantes :

1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans Windows PowerShell fenêtre.

2. Exécutez lSet-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Où *PolicyName est* le nom ou l’ID unique de la stratégie. Par exemple, Contoso_Global.

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Restaurer les clés Azure Key Vault

Avant d’effectuer une restauration, utilisez les fonctionnalités de récupération fournies par la suppression soft. Toutes les clés utilisées avec la clé client doivent être activées pour la suppression possible. La suppression souple agit comme une corbeille et permet une récupération pendant 90 jours sans avoir à le restaurer. La restauration ne doit être nécessaire que dans des circonstances extrêmes ou inhabituelles, par exemple si la clé ou le coffre de clés est perdu. Si vous devez restaurer une clé à utiliser avec la clé client, dans Azure PowerShell, exécutez la cmdlet Restore-AzureKeyVaultKey comme suit :
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Par exemple :
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Si le coffre de clés contient déjà une clé du même nom, l’opération de restauration échoue. Restore-AzKeyVaultKey toutes les versions clés et toutes les métadonnées de la clé, y compris le nom de la clé.
  
## <a name="manage-key-vault-permissions"></a>Gérer les autorisations de coffre de clés

Plusieurs cmdlets sont disponibles pour vous permettre d’afficher et, si nécessaire, de supprimer les autorisations de coffre de clés. Vous devrez peut-être supprimer des autorisations, par exemple, lorsqu’un employé quitte l’équipe. Pour chacune de ces tâches, vous utiliserez Azure PowerShell. Pour plus d’informations Azure PowerShell, voir [Vue d’ensemble Azure PowerShell](/powershell/azure/).

Pour afficher les autorisations de coffre de clés, exécutez Get-AzKeyVault cmdlet.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Par exemple :

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Pour supprimer les autorisations d’un administrateur, exécutez Remove-AzKeyVaultAccessPolicy cmdlet :
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Par exemple :

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Revenir de la clé client aux clés gérées Microsoft

Si vous devez revenir aux clés gérées par Microsoft, vous pouvez. Lorsque vous déboardez, vos données sont re-chiffrées à l’aide du chiffrement par défaut pris en charge par chaque charge de travail individuelle. Par exemple, Exchange Online prend en charge le chiffrement par défaut à l’aide de clés gérées par Microsoft.

> [!IMPORTANT]
> Laboarding n’est pas la même chose qu’une purge de données. Une purge des données supprime définitivement les données de votre organisation de l’Microsoft 365, ce qui n’est pas le cas de la suppression de l’board. Vous ne pouvez pas effectuer de purge de données pour une stratégie de charges de travail multiples.

Si vous décidez de ne plus utiliser la clé client pour affecter des deP multi-charges de travail, vous devrez joindre le support Microsoft avec une demande de « désintégration » à partir de la clé client. Demandez à l’équipe de support de déposer une demande de service auprès Microsoft 365'équipe de clé client. Si vous avez des questions, m365-ck@service.microsoft.com posent des questions.

Si vous ne souhaitez plus chiffrer des boîtes aux lettres individuelles à l’aide de DEP au niveau de la boîte aux lettres, vous pouvez désattribuer les DPS de niveau boîte aux lettres de toutes vos boîtes aux lettres.

Pour désattribuer des DPS de boîte aux lettres, utilisez Set-Mailbox cmdlet PowerShell.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez lSet-Mailbox cmdlet.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

L’exécution de cette cmdlet désattribue le dep actuellement affecté et recrypte la boîte aux lettres à l’aide de la dep associée aux clés gérées par Microsoft par défaut. Vous ne pouvez pas désattribuer le deP utilisé par les clés gérées microsoft. Si vous ne souhaitez pas utiliser de clés gérées par Microsoft, vous pouvez affecter une autre clé client DEP à la boîte aux lettres.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Révoquer vos clés et démarrer le processus de purge des données

Vous contrôlez la révocation de toutes les clés racine, y compris la clé de disponibilité. La clé client vous permet de contrôler l’aspect de planification de sortie des exigences réglementaires. Si vous décidez de révoquer vos clés pour vider vos données et quitter le service, le service supprime la clé de disponibilité une fois le processus de purge des données terminé. Ceci est pris en charge pour les DPS de clé client qui sont affectés à des boîtes aux lettres individuelles.

Microsoft 365 audite et valide le chemin de purge des données. Pour plus d’informations, voir le rapport SSAE 18 SOC 2 disponible sur le portail [d’confiance des services.](https://servicetrust.microsoft.com/) En outre, Microsoft recommande les documents suivants :

- [Guide d’évaluation et de conformité des risques pour les institutions financières dans microsoft cloud](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Considérations sur la planification de sortie d’O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

La purge de la PDV à charges multiples n’est pas prise en charge Microsoft 365 clé client. Le PD DEP à charges multiples est utilisé pour chiffrer des données sur plusieurs charges de travail pour tous les utilisateurs du client. La purge de ce type de PDN entraînerait l’in inaccessible des données provenant de plusieurs charges de travail. Si vous décidez de quitter Microsoft 365 services, vous pouvez suivre le chemin d’accès à la suppression du client selon le processus documenté. Découvrez [comment supprimer un client dans Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Révoquer vos clés client et la clé de disponibilité Exchange Online et Skype Entreprise

Lorsque vous lancez le chemin d’accès de purge des données pour Exchange Online et Skype Entreprise, vous définissez une demande de purge permanente des données sur un deP. Cela supprime définitivement les données chiffrées dans les boîtes aux lettres à laquelle ce dep est affecté.

Étant donné que vous ne pouvez exécuter l’cmdlet PowerShell que sur une seule dep à la fois, envisagez de réaffecter une seule dep à toutes vos boîtes aux lettres avant de lancer le chemin de purge des données.

> [!WARNING]
> N’utilisez pas le chemin de purge des données pour supprimer un sous-ensemble de vos boîtes aux lettres. Ce processus est destiné uniquement aux clients qui quittent le service.

Pour lancer le chemin d’accès de la purge des données, effectuer les étapes suivantes :

1. Supprimez les autorisations wrap et unwrap pour « O365 Exchange Online » des coffres de clés Azure.

2. À l’aide d’un compte professionnel ou scolaire qui dispose de privilèges d’administrateur général dans votre organisation, connectez-vous [Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

3. Pour chaque PDE qui contient des boîtes aux lettres à supprimer, exécutez la cmdlet [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) comme suit.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Si la commande échoue, assurez-vous que vous avez supprimé les autorisations Exchange Online des deux clés dans Azure Key Vault, comme indiqué précédemment dans cette tâche.Une fois que vous avez définie le commutateur PermanentDataPurgeRequested à l’aide de la cmdlet Set-DataEncryptionPolicy, vous ne pourrez plus affecter ce deP aux boîtes aux lettres.

4. Contactez le support Microsoft et demandez l’eDocument de purge des données.

    À votre demande, Microsoft vous envoie un document juridique pour accusé de réception et autoriser la suppression des données. La personne de votre organisation qui s’est inscrite en tant qu’approuveur dans l’offre FastTrack lors de l’intégration doit signer ce document. Normalement, il s’agit d’un cadre supérieur ou d’une autre personne désignée de votre entreprise qui est légalement autorisé à signer les formalités au nom de votre organisation.

5. Une fois que votre représentant a signé le document juridique, renvoyez-le à Microsoft (généralement via une signature eDoc).

    Une fois que Microsoft a reçu le document juridique, Microsoft exécute des cmdlets pour déclencher la purge des données qui supprime d’abord la stratégie, marque les boîtes aux lettres pour suppression définitive, puis supprime la clé de disponibilité. Une fois le processus de purge des données terminé, les données ont été purgées, sont inaccessibles Exchange Online et ne sont pas récupérables.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Révoquer vos clés client et la clé de disponibilité pour les fichiers SharePoint Online, OneDrive Entreprise et Teams client

Pour lancer le chemin d’accès de purge des données pour SharePoint Online, OneDrive Entreprise et Teams fichiers, effectuer les étapes suivantes :

1. Révoquer l’accès à Azure Key Vault. Tous les administrateurs de coffre de clés doivent accepter de révoquer l’accès.

   Vous ne supprimez pas le coffre de clés Azure pour SharePoint Online. Les coffres de clés peuvent être partagés entre plusieurs locataires SharePoint online et de dép.

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
