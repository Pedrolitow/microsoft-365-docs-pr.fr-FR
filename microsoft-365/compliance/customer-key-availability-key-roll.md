---
title: Echanger ou alterner entre une clé client ou de disponibilité
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Découvrez comment déployer les clés racine du client stockées dans Azure Key Vault qui sont utilisées avec la clé client. Les services incluent Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Teams fichiers.
ms.openlocfilehash: 892d77959bec1fb33b0ea6bcfaa8c530dd9b8911
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52345117"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Echanger ou alterner entre une clé client ou de disponibilité

> [!CAUTION]
> Ne lancez qu’une clé de chiffrement que vous utilisez avec la clé client lorsque vos exigences de sécurité ou de conformité vous imposent de la mettre en place. En outre, ne supprimez pas les clés qui sont ou qui ont été associées à des stratégies. Lorsque vous rollez vos clés, le contenu est chiffré avec les clés précédentes. Par exemple, alors que les boîtes aux lettres actives sont fréquemment chiffrées, les boîtes aux lettres inactives, déconnectées et désactivées peuvent toujours être chiffrées avec les clés précédentes. SharePoint Online effectue la sauvegarde du contenu à des fins de restauration et de récupération, de sorte qu’il peut toujours y avoir du contenu archivé à l’aide d’anciennes clés.

## <a name="about-rolling-the-availability-key"></a>À propos du déploiement de la clé de disponibilité

Microsoft n’expose pas le contrôle direct de la clé de disponibilité aux clients. Par exemple, vous pouvez uniquement faire pivoter (faire pivoter) les clés que vous possédez dans Azure Key Vault. Microsoft 365 les clés de disponibilité selon une planification définie en interne. Il n’existe aucun contrat de niveau de service (SLA) client pour ces chiffres clés. Microsoft 365 la clé de disponibilité à l’aide Microsoft 365 code de service dans un processus automatisé et non manuel. Les administrateurs Microsoft peuvent lancer le processus de déploiement. La clé est déployée à l’aide de mécanismes automatisés sans accès direct au magasin de clés. L’accès au magasin de clés secrètes de disponibilité n’est pas disponible pour les administrateurs Microsoft. Le déploiement de la clé de disponibilité exploite le mécanisme utilisé initialement pour générer la clé. Pour plus d’informations sur la clé de disponibilité, voir [Comprendre la clé de disponibilité.](customer-key-availability-key-understand.md)

> [!IMPORTANT]
> Exchange Online et Skype Entreprise clés de disponibilité peuvent être correctement déployées par les clients qui créent une nouvelle dep, car une clé de disponibilité unique est générée pour chaque deP que vous créez. Les clés de disponibilité pour les fichiers SharePoint Online, OneDrive Entreprise et Teams existent au niveau de la forêt et sont partagées entre les PD DEP et les clients, ce qui signifie que le déploiement se produit uniquement selon une planification définie en interne par Microsoft. Pour atténuer le risque de ne pas déployer la clé de disponibilité chaque fois qu’un nouveau dep est créé, SharePoint, OneDrive et Teams la clé intermédiaire du client (TIK), la clé wrapped par les clés racine du client et la clé de disponibilité, chaque fois qu’un nouveau dep est créé.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Demander une nouvelle version de chaque clé racine existante que vous souhaitez déployer

Lorsque vous rollez une clé, vous demandez une nouvelle version d’une clé existante. Pour demander une nouvelle version d’une clé existante, utilisez la même cmdlet, [Add-AzKeyVaultKey,](/powershell/module/az.keyvault/add-azkeyvaultkey)avec la même syntaxe que celle utilisée pour créer la clé. Une fois que vous avez terminé le déploiement d’une clé associée à une stratégie de chiffrement de données ( DEP), vous exécutez une autre cmdlet pour vous assurer que la clé client commence à utiliser la nouvelle clé. Faites cette étape dans chaque coffre de clés Azure (AKV).

Par exemple :

1. Connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, [voir Se Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez la cmdlet Add-AzKeyVaultKey comme illustré dans l’exemple suivant :

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   Dans cet exemple, étant donné qu’une clé nommée **Contoso-CK-EX-NA-VaultA1-Key001** existe dans le coffre **Contoso-CK-EX-NA-VaultA1,** l’cmdlet crée une nouvelle version de la clé. Cette opération conserve les versions de clé précédentes dans l’historique des versions de la clé. Vous avez besoin de la version de clé précédente pour déchiffrer les données qu’elle chiffre toujours. Une fois que vous avez terminé le déploiement d’une clé associée à une dep, exécutez une cmdlet supplémentaire pour vous assurer que la clé client commence à utiliser la nouvelle clé. Les sections suivantes décrivent les cmdlets plus en détail.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Mettre à jour les clés pour les ppp multi-charges de travail

Lorsque vous rollez l’une des clés Azure Key Vault associées à un dep utilisé avec plusieurs charges de travail, vous devez mettre à jour le deP pour pointer vers la nouvelle clé. Ce processus ne fait pas pivoter la clé de disponibilité.

Pour demander à la clé client d’utiliser la nouvelle clé pour chiffrer plusieurs charges de travail, effectuer les étapes suivantes :

1. Sur votre ordinateur local, à l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Exécutez lSet-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Où *PolicyName est* le nom ou l’ID unique de la stratégie. Par exemple, Contoso_Global.

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Mettre à jour les clés pour Exchange Online DEP

Lorsque vous rollez l’une des clés Azure Key Vault associées à un dep utilisé avec Exchange Online et Skype Entreprise, vous devez mettre à jour le dep pour pointer vers la nouvelle clé. Cela ne fait pas pivoter la clé de disponibilité.

Pour demander à la clé client d’utiliser la nouvelle clé pour chiffrer les boîtes aux lettres, exécutez la cmdlet Set-DataEncryptionPolicy comme suit :

1. Exécutez la cmdlet Set-DataEncryptionPolicy dans Azure PowerShell :
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Pour vérifier la valeur de la propriété DataEncryptionPolicyID pour la boîte aux lettres, utilisez les étapes de déterminer le [dep](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox)affecté à une boîte aux lettres . La valeur de cette propriété change une fois que le service applique la clé mise à jour.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Mettre à jour les clés pour SharePoint en ligne, OneDrive Entreprise et Teams fichiers

SharePoint Online ne vous permet de déployer qu’une seule clé à la fois. Si vous souhaitez mettre les deux clés dans un coffre de clés, attendez la fin de la première opération. Microsoft vous recommande d’échelonner vos opérations pour éviter ce problème. Lorsque vous rollez l’une des clés Azure Key Vault associées à un dep utilisé avec SharePoint Online et OneDrive Entreprise, vous devez mettre à jour le dep pour pointer vers la nouvelle clé. Cela ne fait pas pivoter la clé de disponibilité.

1. Exécutez la cmdlet Update-SPODataEncryptionPolicy suivante :
  
   ```powershell
   Update-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Bien que cette cmdlet démarre l’opération de SharePoint En ligne et OneDrive Entreprise, l’action ne se termine pas immédiatement.

2. Pour voir la progression de l’opération de roulis de touches, exécutez Get-SPODataEncryptionPolicy cmdlet comme suit :

   ```powershell
   Get-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec clé client pour Office 365](customer-key-overview.md)

- [Configurer la clé client pour Office 365](customer-key-set-up.md)

- [Gérer la clé client pour Office 365](customer-key-manage.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)