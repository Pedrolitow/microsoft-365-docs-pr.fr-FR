---
title: Echanger ou alterner entre une clé client ou de disponibilité
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
description: Découvrez comment faire en sorte que les clés racines du client stockées dans le coffre-fort de clés Azure soient utilisées avec la clé client. Les services incluent les fichiers Exchange Online, Skype entreprise, SharePoint Online, OneDrive entreprise et Teams.
ms.openlocfilehash: 29a36636253f5f01181f231941d0c3a9e26abacc
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43633641"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Echanger ou alterner entre une clé client ou de disponibilité

> [!CAUTION]
> Ne faites appel qu’à une clé de chiffrement que vous utilisez avec la clé client lorsque vos exigences en matière de sécurité ou de conformité vous obligent à lancer la clé. En outre, ne supprimez pas de clés qui sont ou n’ont pas été associées à des stratégies. Lorsque vous restaurez vos clés, le contenu est chiffré avec les clés précédentes. Par exemple, bien que les boîtes aux lettres actives soient rechiffrées fréquemment, les boîtes aux lettres inactives, déconnectées et désactivées peuvent toujours être chiffrées avec les clés précédentes. SharePoint Online effectue des sauvegardes de contenu à des fins de restauration et de récupération, de sorte qu’il peut toujours y avoir un archivage de contenu à l’aide de clés plus anciennes.

## <a name="about-rolling-the-availability-key"></a>À propos du déroulement de la clé de disponibilité

Microsoft n’expose pas le contrôle direct de la clé de disponibilité aux clients. Par exemple, vous pouvez uniquement faire pivoter les touches dont vous êtes propriétaire dans le coffre de clés Azure. Microsoft 365 annule les clés de disponibilité selon un calendrier défini en interne. Il n’existe aucun contrat de niveau de service (SLA) orienté vers le client pour ces rouleaux clés. Microsoft 365 fait pivoter la clé de disponibilité à l’aide du code de service Microsoft 365 dans un processus automatisé, non manuel. Les administrateurs Microsoft peuvent lancer le processus de déploiement. La clé est déployée à l’aide de mécanismes automatisés sans accès direct au magasin de clés. L’accès au magasin secret clé de disponibilité n’est pas approvisionné aux administrateurs Microsoft. Le laminage de clé de disponibilité exploite le même mécanisme que celui utilisé pour générer initialement la clé. Pour plus d’informations sur la clé de disponibilité, voir [comprendre la clé de disponibilité](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Les clés de disponibilité Exchange Online et Skype entreprise peuvent être déployées de manière efficace par les clients qui créent une nouvelle DEP, étant donné qu’une clé de disponibilité unique est générée pour chaque DEP que vous créez. Les clés de disponibilité pour SharePoint Online, OneDrive entreprise et les fichiers teams existent au niveau de la forêt et sont partagées entre DEPs et les clients, ce qui signifie que le déploiement se produit uniquement sur une planification définie de manière interne par Microsoft. Pour limiter les risques de non-déploiement de la clé de disponibilité chaque fois qu’une nouvelle DEP est créée, SharePoint, OneDrive et teams retournent la clé intermédiaire client (TIK), la clé incluse dans les clés racines du client et la clé de disponibilité, chaque fois qu’une nouvelle DEP est créée.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Demander une nouvelle version de chaque clé racine existante à effectuer

Lorsque vous restaurez une clé, vous demandez une nouvelle version d’une clé existante. Pour demander une nouvelle version d’une clé existante, vous utilisez la même cmdlet, [Add-AzKeyVaultKey](https://docs.microsoft.com/powershell/module/az.keyvault/add-azkeyvaultkey), avec la même syntaxe que celle que vous avez utilisée pour créer la clé. Une fois que vous avez terminé de lancer une clé associée à une stratégie de chiffrement de données (DEP), vous exécutez une autre cmdlet pour vous assurer que la clé client commence à utiliser la nouvelle clé. Effectuez cette étape dans chaque coffre-fort de clés Azure (AKV).

Par exemple :

1. Connectez-vous à votre abonnement Azure avec Azure PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](https://docs.microsoft.com/powershell/azure/authenticate-azureps).

2. Exécutez l’applet de commande Add-AzKeyVaultKey comme indiqué dans l’exemple suivant :

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -Name Contoso-O365EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   Dans cet exemple, étant donné qu’une clé nommée **contoso-O365EX-na-VaultA1-Key001** existe dans la chambre forte de **contoso-O365EX-na-VaultA1** , l’applet de commande crée une nouvelle version de la clé. Cette opération conserve les versions de clés précédentes dans l’historique des versions de la clé. Vous avez besoin de la version précédente de la clé pour déchiffrer les données qu’elle chiffre encore. Une fois que vous avez terminé le lancement de n’importe quelle clé associée à une DEP, exécutez une applet de commande supplémentaire afin de vous assurer que la clé client commence à utiliser la nouvelle clé. Les sections suivantes décrivent les applets de commande plus en détail.
  
## <a name="update-the-customer-key-for-exchange-online-and-skype-for-business"></a>Mettre à jour la clé client pour Exchange Online et Skype entreprise

Lorsque vous déployez l’une des clés Azure Key Vault associées à une DEP utilisée avec Exchange Online et Skype entreprise, vous devez mettre à jour la DEP pour qu’elle pointe vers la nouvelle clé. Cette opération ne fait pas pivoter la clé de disponibilité.

Pour indiquer à la clé du client d’utiliser la nouvelle clé pour chiffrer les boîtes aux lettres, exécutez la cmdlet Set-DataEncryptionPolicy comme suit :

1. Exécutez la cmdlet Set-DataEncryptionPolicy dans Azure PowerShell :
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

   Dans les 72 heures, les boîtes aux lettres actives associées à cette DEP deviennent chiffrées à l’aide de la nouvelle clé.

2. Pour vérifier la valeur de la propriété DataEncryptionPolicyID de la boîte aux lettres, suivez les étapes décrites dans la procédure [déterminer la DEP attribuée à une boîte aux lettres](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). La valeur de cette propriété change une fois que le service applique la clé mise à jour.
  
## <a name="update-the-customer-key-for-sharepointonlineonedriveforbusinessandteamsfiles"></a>Mettre à jour la clé client pour les fichiers SharePoint Online, OneDrive entreprise et Teams

SharePoint Online ne vous permet d’appliquer qu’une seule touche à la fois. Si vous souhaitez exécuter les deux clés dans un coffre-fort de clés, attendez que la première opération se termine. Microsoft vous recommande d’échelonner vos opérations pour éviter ce problème. Lorsque vous déployez l’une des clés Azure Key Vault associées à une DEP utilisée avec SharePoint Online et OneDrive entreprise, vous devez mettre à jour la DEP pour qu’elle pointe vers la nouvelle clé. Cette opération ne fait pas pivoter la clé de disponibilité.

1. Exécutez la cmdlet Update-SPODataEncryptionPolicy comme suit :
  
   ```powershell
   Update-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Bien que cette applet de commande démarre l’opération de roulis clés pour SharePoint Online et OneDrive entreprise, l’action ne s’exécute pas immédiatement.

2. Pour voir la progression de l’opération de la séquence de touches, exécutez la cmdlet Get-SPODataEncryptionPolicy comme suit :

   ```powershell
   Get-SPODataEncryptionPolicy -Identity <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec la clé client pour Office 365](customer-key-overview.md)

- [Configurer la clé client pour Office 365](customer-key-set-up.md)

- [Gérer la clé client pour Office 365](customer-key-manage.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)
