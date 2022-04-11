---
title: Echanger ou alterner entre une clé client ou de disponibilité
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
description: Découvrez comment restaurer les clés racine du client stockées dans Azure Key Vault qui sont utilisées avec la clé client. Les services incluent des fichiers Exchange Online, Skype for Business, SharePoint Online, OneDrive Entreprise et Teams.
ms.openlocfilehash: 81d82f49c056f5a6ec9b8731b549aee68d5d658b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761348"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Echanger ou alterner entre une clé client ou de disponibilité

> [!CAUTION]
> Exécutez uniquement une clé de chiffrement que vous utilisez avec la clé client lorsque vos exigences de sécurité ou de conformité vous imposent de la déployer. En outre, ne supprimez pas les clés qui sont ou ont été associées à des stratégies. Lorsque vous roulez vos clés, le contenu est chiffré avec les clés précédentes. Par exemple, bien que les boîtes aux lettres actives soient rechiffrées fréquemment, les boîtes aux lettres inactives, déconnectées et désactivées peuvent toujours être chiffrées avec les clés précédentes. SharePoint Online effectue une sauvegarde du contenu à des fins de restauration et de récupération. Il peut donc toujours y avoir du contenu archivé à l’aide de clés plus anciennes.

## <a name="about-rolling-the-availability-key"></a>À propos du déploiement de la clé de disponibilité

Microsoft n’expose pas le contrôle direct de la clé de disponibilité aux clients. Par exemple, vous pouvez uniquement restaurer (faire pivoter) les clés que vous possédez dans Azure Key Vault. Microsoft 365 cumule les clés de disponibilité selon une planification définie en interne. Il n’existe aucun contrat de niveau de service (SLA) orienté client pour ces rouleaux de clés. Microsoft 365 fait pivoter la clé de disponibilité à l’aide Microsoft 365 code de service dans un processus automatisé et non manuel. Les administrateurs Microsoft peuvent lancer le processus de lancement. La clé est déployée à l’aide de mécanismes automatisés sans accès direct au magasin de clés. L’accès au magasin de clés secrètes de disponibilité n’est pas approvisionné pour les administrateurs Microsoft. Le déploiement de clé de disponibilité utilise le même mécanisme que celui utilisé pour générer initialement la clé. Pour plus d’informations sur la clé de disponibilité, consultez [Comprendre la clé de disponibilité](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online et les clés de disponibilité Skype for Business peuvent être déployées efficacement par les clients qui créent un dep, car une clé de disponibilité unique est générée pour chaque DEP que vous créez. Les clés de disponibilité des fichiers SharePoint Online, OneDrive Entreprise et Teams existent au niveau de la forêt et sont partagées entre les dep et les clients, ce qui signifie que le déploiement se produit uniquement à une planification définie en interne par Microsoft. Pour atténuer le risque de ne pas déployer la clé de disponibilité chaque fois qu’un nouveau DEP est créé, SharePoint, OneDrive et Teams de restaurer la clé intermédiaire de locataire (TIK), la clé encapsulée par les clés racine du client et la clé de disponibilité, chaque fois qu’un nouveau DEP est créé.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Demander une nouvelle version de chaque clé racine existante à restaurer

Lorsque vous déployez une clé, vous demandez une nouvelle version d’une clé existante. Pour demander une nouvelle version d’une clé existante, vous utilisez la même applet de commande, [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey), avec la même syntaxe que celle utilisée pour créer la clé. Une fois que vous avez terminé de déployer une clé associée à une stratégie de chiffrement des données (DEP), exécutez une autre applet de commande pour vous assurer que la clé client commence à utiliser la nouvelle clé. Effectuez cette étape dans chaque Key Vault Azure (AKV).

Par exemple :

1. Connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, consultez [Se connecter avec Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez l’applet de commande Add-AzKeyVaultKey comme indiqué dans l’exemple suivant :

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   Dans cet exemple, étant donné qu’une clé nommée **Contoso-CK-EX-NA-VaultA1-Key001** existe dans le coffre **Contoso-CK-EX-NA-VaultA1** , l’applet de commande crée une nouvelle version de la clé. Cette opération conserve les versions de clé précédentes dans l’historique des versions de la clé. Vous avez besoin de la version de clé précédente pour déchiffrer les données qu’elle chiffre toujours. Une fois que vous avez effectué le déploiement d’une clé associée à un dep, exécutez une applet de commande supplémentaire pour vous assurer que la clé client commence à utiliser la nouvelle clé. Les sections suivantes décrivent les applets de commande plus en détail.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Mettre à jour les clés pour les dep multi-charges de travail

Lorsque vous roulez l’une des clés Azure Key Vault associées à un DEP utilisé avec plusieurs charges de travail, vous devez mettre à jour le dep pour pointer vers la nouvelle clé. Ce processus ne fait pas pivoter la clé de disponibilité.

Pour indiquer à customer Key d’utiliser la nouvelle clé pour chiffrer plusieurs charges de travail, procédez comme suit :

1. Sur votre ordinateur local, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général ou d’administrateur de conformité dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) dans une fenêtre Windows PowerShell.

2. Exécutez l’applet de commande Set-M365DataAtRestEncryptionPolicy.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Où *PolicyName* est le nom ou l’ID unique de la stratégie. Par exemple, Contoso_Global.

Exemple :

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Mettre à jour les clés pour Exchange Online DEP

Lorsque vous roulez l’une des clés Azure Key Vault associées à un DEP utilisé avec Exchange Online et Skype for Business, vous devez mettre à jour le dep pour qu’il pointe vers la nouvelle clé. Cela ne fait pas pivoter la clé de disponibilité.

Pour demander à customer Key d’utiliser la nouvelle clé pour chiffrer les boîtes aux lettres, exécutez l’applet de commande Set-DataEncryptionPolicy comme suit :

1. Exécutez l’applet de commande Set-DataEncryptionPolicy dans Azure PowerShell :
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Pour vérifier la valeur de la propriété DataEncryptionPolicyID de la boîte aux lettres, suivez les étapes [décrites dans Déterminer le dep affecté à une boîte aux lettres](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). La valeur de cette propriété change une fois que le service applique la clé mise à jour.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Mettre à jour les clés des fichiers SharePoint Online, OneDrive Entreprise et Teams

SharePoint Online vous permet uniquement de rouler une clé à la fois. Si vous souhaitez déployer les deux clés dans un coffre de clés, attendez la fin de la première opération. Microsoft vous recommande d’échelonner vos opérations pour éviter ce problème. Lorsque vous roulez l’une des clés Azure Key Vault associées à un DEP utilisé avec SharePoint Online et OneDrive Entreprise, vous devez mettre à jour le dep pour pointer vers la nouvelle clé. Cela ne fait pas pivoter la clé de disponibilité.

1. Exécutez l’applet de commande Update-SPODataEncryptionPolicy comme suit :
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Bien que cette applet de commande démarre l’opération de lancement de clé pour SharePoint Online et OneDrive Entreprise, l’action ne se termine pas immédiatement.

2. Pour voir la progression de l’opération de lancement de clé, exécutez l’applet de commande Get-SPODataEncryptionPolicy comme suit :

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec clé client pour Office 365](customer-key-overview.md)

- [Configurer la clé client pour Office 365](customer-key-set-up.md)

- [Gérer la clé client pour Office 365](customer-key-manage.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)
