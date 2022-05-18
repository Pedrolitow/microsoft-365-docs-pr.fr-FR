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
description: Après avoir configuré la clé client, découvrez comment la gérer en restaurant les clés AKV, en gérant les autorisations et en créant et en affectant des stratégies de chiffrement des données.
ms.openlocfilehash: 0ca6aa1e2cf725359d74477b486a4763a35ba681
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465907"
---
# <a name="manage-customer-key"></a>Gérer la clé client

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une fois que vous avez configuré la clé client, vous devez créer et affecter une ou plusieurs stratégies de chiffrement des données (DEP). Une fois que vous avez affecté vos dep, vous pouvez gérer vos clés comme décrit dans cet article. En savoir plus sur la clé client dans les rubriques connexes.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Créer un DEP à utiliser avec plusieurs charges de travail pour tous les utilisateurs locataires

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer la clé client. Pour plus d’informations, consultez [Configurer la clé client](customer-key-set-up.md). Pour créer le DEP, vous avez besoin des URI Key Vault que vous avez obtenus lors de l’installation. Pour plus d’informations, consultez [Obtenir l’URI pour chaque clé Azure Key Vault](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Pour créer un dep multi-charge de travail, procédez comme suit :
  
1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Pour créer un dep, utilisez l’applet de commande New-M365DataAtRestEncryptionPolicy.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Où :

   - *PolicyName* est le nom que vous souhaitez utiliser pour la stratégie. Les noms ne peuvent pas contenir d’espaces. Par exemple, Contoso_Global.

   - *KeyVaultURI1* est l’URI de la première clé de la stratégie. Par exemple : <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* est l’URI de la deuxième clé de la stratégie. Par exemple : <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. Séparez les deux URI par une virgule et un espace.

   - *La description* de la stratégie est une description conviviale de la stratégie qui vous aidera à vous rappeler à quoi sert la stratégie. Vous pouvez inclure des espaces dans la description. Par exemple, « Stratégie racine pour plusieurs charges de travail pour tous les utilisateurs du locataire ».

Exemple :

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Attribuer une stratégie multi-charges de travail

Affectez le DEP à l’aide de l’applet de commande Set-M365DataAtRestEncryptionPolicyAssignment. Une fois que vous avez affecté la stratégie, Microsoft 365 chiffre les données avec la clé identifiée dans le DEP.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Où *PolicyName* est le nom de la stratégie. Par exemple, Contoso_Global.

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Créer un dep à utiliser avec des boîtes aux lettres Exchange Online

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer Azure Key Vault. Pour plus d’informations, consultez [Configurer la clé client](customer-key-set-up.md). Vous effectuerez ces étapes en vous connectant à distance à Exchange Online avec Windows PowerShell.

Un DEP est associé à un ensemble de clés stockées dans Azure Key Vault. Vous affectez un DEP à une boîte aux lettres dans Microsoft 365. Microsoft 365 utilisera ensuite les clés identifiées dans la stratégie pour chiffrer la boîte aux lettres. Pour créer le DEP, vous avez besoin des URI Key Vault que vous avez obtenus lors de l’installation. Pour plus d’informations, consultez [Obtenir l’URI pour chaque clé Azure Key Vault](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Rappelez-vous! Lorsque vous créez un DEP, vous spécifiez deux clés dans deux coffres de clés Azure différents. Créez ces clés dans deux régions Azure distinctes pour garantir la géoredondance.

Pour créer un dep à utiliser avec une boîte aux lettres, procédez comme suit :
  
1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général ou Exchange Online dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Pour créer un dep, utilisez l’applet de commande New-DataEncryptionPolicy en tapant la commande suivante.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Où :

   - *PolicyName* est le nom que vous souhaitez utiliser pour la stratégie. Les noms ne peuvent pas contenir d’espaces. Par exemple, USA_mailboxes.

   - *La description* de la stratégie est une description conviviale de la stratégie qui vous aidera à vous rappeler à quoi sert la stratégie. Vous pouvez inclure des espaces dans la description. Par exemple, « Clé racine pour les boîtes aux lettres aux États-Unis et dans ses territoires ».

   - *KeyVaultURI1* est l’URI de la première clé de la stratégie. Par exemple : <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* est l’URI de la deuxième clé de la stratégie. Par exemple : <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Séparez les deux URI par une virgule et un espace.

   Exemple :
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Affecter un DEP à une boîte aux lettres

Affectez le dep à une boîte aux lettres à l’aide de l’applet de commande Set-Mailbox. Une fois que vous avez affecté la stratégie, Microsoft 365 pouvez chiffrer la boîte aux lettres avec la clé identifiée dans le DEP.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailboxIdParameter* spécifie une boîte aux lettres utilisateur. Pour plus d’informations sur l’applet de commande Set-Mailbox, consultez [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Dans les environnements hybrides, vous pouvez affecter un DEP aux données de boîte aux lettres locales synchronisées dans votre locataire Exchange Online. Pour affecter un dep à ces données de boîte aux lettres synchronisées, vous allez utiliser l’applet de commande Set-MailUser. Pour plus d’informations sur les données de boîte aux lettres dans l’environnement hybride, consultez [les boîtes aux lettres locales utilisant Outlook pour iOS et Android avec l’authentification moderne hybride](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Où *MailUserIdParameter* spécifie un utilisateur de messagerie (également appelé utilisateur à activation du courrier). Pour plus d’informations sur l’applet de commande Set-MailUser, consultez [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>Créer un dep à utiliser avec SharePoint Online, OneDrive Entreprise et Teams fichiers

Avant de commencer, assurez-vous d’avoir effectué les tâches requises pour configurer Azure Key Vault. Pour plus d’informations, consultez [Configurer la clé client](customer-key-set-up.md).
  
Pour configurer la clé client pour SharePoint En ligne, OneDrive Entreprise et Teams fichiers, vous effectuez ces étapes en vous connectant à distance à SharePoint Online avec Windows PowerShell.
  
Vous associez un DEP à un ensemble de clés stockées dans Azure Key Vault. Vous appliquez un DEP à toutes vos données dans un emplacement géographique, également appelé géo. Si vous utilisez la fonctionnalité multigéographique de Office 365, vous pouvez créer un DEP par géo avec la possibilité d’utiliser différentes clés par géo. Si vous n’utilisez pas multigéographique, vous pouvez créer un DEP dans votre organisation pour une utilisation avec SharePoint En ligne, OneDrive Entreprise et Teams fichiers. Microsoft 365 utilise les clés identifiées dans le DEP pour chiffrer vos données dans cette zone géographique. Pour créer le DEP, vous avez besoin des URI Key Vault que vous avez obtenus lors de l’installation. Pour plus d’informations, consultez [Obtenir l’URI pour chaque clé Azure Key Vault](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
Rappelez-vous! Lorsque vous créez un DEP, vous spécifiez deux clés dans deux coffres de clés Azure différents. Créez ces clés dans deux régions Azure distinctes pour garantir la géoredondance.
  
Pour créer un dep, vous devez vous connecter à distance à SharePoint Online à l’aide de Windows PowerShell.
  
1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [Connecter pour SharePoint PowerShell en ligne](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. Dans Microsoft Office SharePoint Online Management Shell, exécutez l’applet de commande Register-SPODataEncryptionPolicy comme suit :

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Exemple :
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a'
   ```

   Lorsque vous inscrivez le dep, le chiffrement commence sur les données dans la zone géographique. Le chiffrement peut prendre un certain temps. Pour plus d’informations sur l’utilisation de ce paramètre, consultez [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Afficher les adresses DEP que vous avez créées pour Exchange Online boîtes aux lettres

Pour afficher la liste de toutes les adresses DEP que vous avez créées pour les boîtes aux lettres, utilisez la Get-DataEncryptionPolicy cmdlet PowerShell.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Pour renvoyer toutes les dep de votre organisation, exécutez l’applet de commande Get-DataEncryptionPolicy sans aucun paramètre.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Pour plus d’informations sur l’applet de commande Get-DataEncryptionPolicy, consultez [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Affecter un dep avant de migrer une boîte aux lettres vers le cloud

Lorsque vous attribuez le DEP, Microsoft 365 chiffre le contenu de la boîte aux lettres à l’aide du dep affecté pendant la migration. Ce processus est plus efficace que la migration de la boîte aux lettres, l’affectation du DEP, puis l’attente du chiffrement, ce qui peut prendre des heures, voire des jours.

Pour affecter un dep à une boîte aux lettres avant de la migrer vers Office 365, exécutez l’applet de commande Set-MailUser dans Exchange Online PowerShell :

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-MailUser.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et *DataEncryptionPolicyIdParameter* est l’ID du DEP. Pour plus d’informations sur l’applet de commande Set-MailUser, consultez [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Déterminer le DEP affecté à une boîte aux lettres

Pour déterminer le DEP affecté à une boîte aux lettres, utilisez l’applet de commande Get-MailboxStatistics. L’applet de commande retourne un identificateur unique (GUID).
  
1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Où *GeneralMailboxOrMailUserIdParameter* spécifie une boîte aux lettres et DataEncryptionPolicyID retourne le GUID du DEP. Pour plus d’informations sur l’applet de commande Get-MailboxStatistics, consultez [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. Exécutez l’applet de commande Get-DataEncryptionPolicy pour connaître le nom convivial du dep auquel la boîte aux lettres est affectée.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Où *GUID* est le GUID retourné par l’applet de commande Get-MailboxStatistics à l’étape précédente.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Vérifier que le chiffrement de la clé client est terminé

Que vous ayez déployé une clé client, affecté un nouveau dep ou migré une boîte aux lettres, suivez les étapes décrites dans cette section pour vous assurer que le chiffrement se termine.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Vérifier que le chiffrement est terminé pour Exchange Online boîtes aux lettres

Le chiffrement d’une boîte aux lettres peut prendre un certain temps. Pour le premier chiffrement, la boîte aux lettres doit également passer complètement d’une base de données à une autre avant que le service puisse chiffrer la boîte aux lettres.
  
Utilisez l’applet de commande Get-MailboxStatistics pour déterminer si une boîte aux lettres est chiffrée.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

La propriété IsEncrypted retourne la valeur **true** si la boîte aux lettres est chiffrée et la valeur **false** si la boîte aux lettres n’est pas chiffrée. Le délai de déplacement de la boîte aux lettres dépend du nombre de boîtes aux lettres auxquelles vous attribuez un DEP pour la première fois et de la taille des boîtes aux lettres. Si les boîtes aux lettres n’ont pas été chiffrées après une semaine à partir du moment où vous avez affecté le dep, contactez Microsoft.

L’applet de commande New-MoveRequest n’est plus disponible pour les déplacements de boîtes aux lettres locales. Pour plus d’informations, reportez-vous à [cette annonce](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) .

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Vérifier que le chiffrement est terminé pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

Vérifiez l’état du chiffrement en exécutant l’applet de commande Get-SPODataEncryptionPolicy comme suit :

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

La sortie de cette applet de commande inclut :
  
- URI de la clé primaire.

- URI de la clé secondaire.

- État de chiffrement pour la zone géographique. Les états possibles sont les suivants :

  - **Non:** Le chiffrement de clé client n’a pas encore été appliqué.

  - **Enregistrement:** Le chiffrement de clé client a été appliqué et vos fichiers sont en cours de chiffrement. Si la clé de la zone géographique est inscrite, des informations sur le pourcentage de sites dans la zone géographique sont également affichées afin de pouvoir surveiller la progression du chiffrement.

  - **Enregistré:** Le chiffrement de la clé client a été appliqué et tous les fichiers de tous les sites ont été chiffrés.

  - **Roulement:** Un rouleau de clés est en cours. Si la clé de la zone géographique est en cours de déploiement, vous verrez également des informations sur le pourcentage de sites ayant terminé l’opération de lancement de clé afin de pouvoir surveiller la progression.

- Il génère également le pourcentage de sites intégrés.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Obtenir des détails sur les DEP que vous utilisez avec plusieurs charges de travail

Pour obtenir des détails sur toutes les dep que vous avez créées pour être utilisées avec plusieurs charges de travail, procédez comme suit :

1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

   - Pour retourner la liste de toutes les dep multi-charges de travail de l’organisation, exécutez cette commande.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Pour retourner des détails sur un DEP spécifique, exécutez cette commande. Cet exemple retourne des informations détaillées pour le dep nommé « Contoso_Global ».

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Obtenir des informations d’affectation DEP multi-charges de travail

Pour savoir quel DEP est actuellement affecté à votre locataire, procédez comme suit. 

1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Tapez cette commande.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Désactiver un DEP multi-charges de travail

Avant de désactiver un DEP multi-charges de travail, désattribuez le DEP des charges de travail de votre locataire. Pour désactiver un DEP utilisé avec plusieurs charges de travail, procédez comme suit :

1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Exécutez l’applet de commande Set-M365DataAtRestEncryptionPolicy.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Où *PolicyName* est le nom ou l’ID unique de la stratégie. Par exemple, Contoso_Global.

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Restaurer des clés Azure Key Vault

Avant d’effectuer une restauration, utilisez les fonctionnalités de récupération fournies par la suppression réversible. Toutes les clés utilisées avec la clé client doivent être activées pour que la suppression réversible soit activée. La suppression réversible agit comme une corbeille et permet la récupération jusqu’à 90 jours sans avoir à restaurer. La restauration ne doit être nécessaire que dans des circonstances extrêmes ou inhabituelles, par exemple si la clé ou le coffre de clés est perdu. Si vous devez restaurer une clé à utiliser avec la clé client, dans Azure PowerShell, exécutez l’applet de commande Restore-AzureKeyVaultKey comme suit :
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Par exemple :
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Si le coffre de clés contient déjà une clé portant le même nom, l’opération de restauration échoue. Restore-AzKeyVaultKey restaure toutes les versions de clé et toutes les métadonnées de la clé, y compris le nom de la clé.
  
## <a name="manage-key-vault-permissions"></a>Gérer les autorisations de coffre de clés

Plusieurs applets de commande sont disponibles pour vous permettre d’afficher et, si nécessaire, de supprimer des autorisations de coffre de clés. Vous devrez peut-être supprimer des autorisations, par exemple, lorsqu’un employé quitte l’équipe. Pour chacune de ces tâches, vous allez utiliser Azure PowerShell. Pour plus d’informations sur Azure PowerShell, consultez [Vue d’ensemble de Azure PowerShell](/powershell/azure/).

Pour afficher les autorisations du coffre de clés, exécutez l’applet de commande Get-AzKeyVault.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Par exemple :

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Pour supprimer les autorisations d’un administrateur, exécutez l’applet de commande Remove-AzKeyVaultAccessPolicy :
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Par exemple :

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Restaurer de la clé client aux clés gérées par Microsoft

Si vous devez revenir aux clés gérées par Microsoft, vous pouvez le faire. Lorsque vous vous déconnectez, vos données sont rechiffrées à l’aide du chiffrement par défaut pris en charge par chaque charge de travail individuelle. Par exemple, Exchange Online prend en charge le chiffrement par défaut à l’aide de clés gérées par Microsoft.

> [!IMPORTANT]
> Le désintégrage n’est pas le même qu’un vidage des données. Un vidage de données supprime définitivement les données de votre organisation de Microsoft 365, ce qui n’est pas le cas de la désintégrage. Vous ne pouvez pas effectuer de vidage des données pour une stratégie de charge de travail multiple.

Si vous décidez de ne plus utiliser la clé client pour attribuer des dep à plusieurs charges de travail, vous devez contacter le support Microsoft avec une demande de « désinscription » à partir de la clé client. Demandez à l’équipe de support technique de déposer une demande de service auprès de l’équipe Microsoft Purview Customer Key. Contactez m365-ck@service.microsoft.com si vous avez des questions.

Si vous ne souhaitez plus chiffrer des boîtes aux lettres individuelles à l’aide de dep au niveau de la boîte aux lettres, vous pouvez annuler l’affectation de dep au niveau de la boîte aux lettres de toutes vos boîtes aux lettres.

Pour annuler l’affectation des dep de boîte aux lettres, utilisez l’applet de commande PowerShell Set-Mailbox.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-Mailbox.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

L’exécution de cette applet de commande désattribue le DEP actuellement affecté et recrypte la boîte aux lettres à l’aide du dep associé aux clés gérées par Microsoft par défaut. Vous ne pouvez pas annuler l’affectation du dep utilisé par les clés gérées par Microsoft. Si vous ne souhaitez pas utiliser de clés gérées par Microsoft, vous pouvez affecter un autre DEP de clé client à la boîte aux lettres.

> [!IMPORTANT]
> La restauration de la clé client vers les clés gérées par Microsoft n’est pas prise en charge pour les fichiers SharePoint Online, OneDrive Entreprise et Teams. 

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Révoquer vos clés et démarrer le processus de chemin de vidage des données

Vous contrôlez la révocation de toutes les clés racine, y compris la clé de disponibilité. La clé client vous permet de contrôler l’aspect de la planification de sortie des exigences réglementaires. Si vous décidez de révoquer vos clés pour vider vos données et quitter le service, le service supprime la clé de disponibilité une fois le processus de vidage des données terminé. Cela est pris en charge pour les dep de clé client qui sont affectées à des boîtes aux lettres individuelles.

Microsoft 365 audite et valide le chemin de vidage des données. Pour plus d’informations, consultez le rapport SSAE 18 SOC 2 disponible sur le [portail d’approbation de services](https://servicetrust.microsoft.com/). En outre, Microsoft recommande les documents suivants :

- [Guide d’évaluation des risques et de conformité pour les institutions financières dans le cloud Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Considérations relatives à la planification de la sortie O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Le vidage du DEP multi-charges de travail n’est pas pris en charge pour la clé client. Le DEP multi-charges de travail est utilisé pour chiffrer les données sur plusieurs charges de travail sur tous les utilisateurs locataires. Le vidage de ce dep entraînerait l’inaccessibilité des données provenant de plusieurs charges de travail. Si vous décidez de quitter complètement Microsoft 365 services, vous pouvez poursuivre le chemin de suppression de locataire selon le processus documenté. Découvrez [comment supprimer un locataire dans Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Révoquez vos clés client et la clé de disponibilité pour Exchange Online et Skype Entreprise

Lorsque vous lancez le chemin de vidage des données pour Exchange Online et Skype Entreprise, vous définissez une demande de vidage permanent des données sur un dep. Cela supprime définitivement les données chiffrées dans les boîtes aux lettres auxquelles ce DEP est affecté.

Étant donné que vous ne pouvez exécuter l’applet de commande PowerShell que sur un DEP à la fois, envisagez de réaffecter un dep unique à toutes vos boîtes aux lettres avant de lancer le chemin de vidage des données.

> [!WARNING]
> N’utilisez pas le chemin de vidage des données pour supprimer un sous-ensemble de vos boîtes aux lettres. Ce processus est uniquement destiné aux clients qui quittent le service.

Pour lancer le chemin de vidage des données, procédez comme suit :

1. Supprimez les autorisations wrap et unwrap pour « O365 Exchange Online » dans Azure Key Vaults.

2. À l’aide d’un compte professionnel ou scolaire disposant de privilèges d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. Pour chaque dep qui contient les boîtes aux lettres que vous souhaitez supprimer, exécutez l’applet de commande [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) comme suit.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Si la commande échoue, vérifiez que vous avez supprimé les autorisations de Exchange Online des deux clés dans Azure Key Vault comme indiqué précédemment dans cette tâche. Une fois que vous avez défini le commutateur PermanentDataPurgeRequested à l’aide de l’applet de commande Set-DataEncryptionPolicy, vous ne pourrez plus affecter ce DEP aux boîtes aux lettres.

4. Contactez le support Microsoft et demandez l’eDocument de vidage des données.

    À votre demande, Microsoft vous envoie un document juridique pour confirmer et autoriser la suppression des données. La personne de votre organisation qui s’est inscrite en tant qu’approbateur dans l’offre FastTrack lors de l’intégration doit signer ce document. Normalement, il s’agit d’un cadre ou d’une autre personne désignée dans votre entreprise qui est légalement autorisée à signer les documents au nom de votre organisation.

5. Une fois que votre représentant a signé le document juridique, renvoyez-le à Microsoft (généralement par le biais d’une signature eDoc).

    Une fois que Microsoft reçoit le document légal, Microsoft exécute des applets de commande pour déclencher le vidage des données qui supprime d’abord la stratégie, marque les boîtes aux lettres pour suppression définitive, puis supprime la clé de disponibilité. Une fois le processus de vidage des données terminé, les données ont été vidées, sont inaccessibles à Exchange Online et ne sont pas récupérables.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Révoquer vos clés client et la clé de disponibilité des fichiers SharePoint Online, OneDrive Entreprise et Teams

Le vidage de SharePoint, de OneDrive pour le travail ou l’école, et les fichiers de Teams dep. n’est pas pris en charge dans la clé client. Ces dep multi-charges de travail sont utilisées pour chiffrer les données sur plusieurs charges de travail sur tous les utilisateurs locataires. Le vidage d’un dep de ce type entraînerait l’inaccessibilité des données provenant de plusieurs charges de travail. Si vous décidez de quitter complètement Microsoft 365 services, vous pouvez poursuivre le chemin de suppression de locataire selon le processus documenté. Découvrez comment [supprimer un locataire dans Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).  

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec la clé client Microsoft Purview](customer-key-overview.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [Référentiel sécurisé client](customer-lockbox-requests.md)

- [Chiffrement de service](office-365-service-encryption.md)
