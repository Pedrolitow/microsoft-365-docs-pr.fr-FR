---
title: Utiliser AllowSelfServicePurchase pour le module MSCommerce PowerShell
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: None
ms.collection:
- commerce
ms.custom: ''
search.appverid:
- MET150
description: Découvrez comment utiliser l’applet de commande AllowSelfServicePurchase PowerShell pour activer ou désactiver l’achat libre-service.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: cb035294ff7f6007e73464f88fc69376fc5b8cc1
ms.sourcegitcommit: b535fe233234fd25146cfe15478e20d954f71e03
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748245"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Utiliser AllowSelfServicePurchase pour le module MSCommerce PowerShell

Le module PowerShell **MSCommerce** est désormais disponible dans la [Galerie PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery). Le module inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent faire des achats en libre-service.

Vous pouvez utiliser le module PowerShell **MSCommerce** pour :

- Afficher l’État par défaut de la valeur du paramètre **AllowSelfServicePurchase** , qu’elle soit activée ou désactivée
- Afficher la liste des produits applicables et indiquer si les achats en libre-service sont activés ou désactivés
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver

## <a name="requirements"></a>Configuration requise

Pour utiliser le module PowerShell **MSCommerce** , vous avez besoin des éléments suivants :

- Un appareil Windows 10
- Autorisation d’administrateur pour l’appareil
- Rôle d’administrateur général ou d’administrateur de facturation pour votre client

## <a name="install-the-mscommerce-powershell-module"></a>Installer le module MSCommerce PowerShell

Vous devez installer une fois le module **MSCommerce** PowerShell sur votre appareil Windows 10, puis l’importer dans chaque session PowerShell que vous démarrez. Téléchargez le module **MSCommerce** PowerShell à partir de la [Galerie PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery).

Pour installer le module **MSCommerce** PowerShell avec **PowerShellGet**, exécutez la commande suivante :

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importer MSCommerce dans la session PowerShell

Après avoir installé le module sur votre appareil Windows 10, vous l’importez dans chaque session PowerShell que vous démarrez. Pour l’importer dans une session PowerShell, exécutez la commande suivante :

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Se connecter à MSCommerce avec vos informations d’identification

Pour vous connecter au module PowerShell avec vos informations d’identification, exécutez la commande suivante.

```powershell
Connect-MSCommerce
```

Cette commande connecte la session PowerShell active à un client Azure Active Directory. La commande vous invite à entrer un nom d’utilisateur et un mot de passe pour le client auquel vous voulez vous connecter. Si l’authentification multifacteur est activée pour vos informations d’identification, vous utilisez l’option interactive pour vous connecter.

## <a name="view-details-for-allowselfservicepurchase"></a>Afficher les détails pour AllowSelfServicePurchase

Pour afficher une description de la valeur du paramètre **AllowSelfServicePurchase** et l’État par défaut, en fonction de votre organisation, exécutez la commande suivante :

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Affichage de la liste des produits achetés en libre-service et de leur statut

Pour afficher la liste de tous les produits d’achat libre-service disponibles et l’état de chacun d’eux, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

Le tableau suivant répertorie les produits disponibles et leur **ProductID**.

| Produit | Mentionnées |
|-----------------------------|--------------|
| Applications puissantes par utilisateur | CFQ7TTC0KP0P |
| Power Automated per User | CFQ7TTC0KP0N |
| Power BI Pro | CFQ7TTC0L3PB |

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Afficher ou définir l’État pour AllowSelfServicePurchase

Une fois que vous avez consulté la liste des produits disponibles pour l’achat en libre-service, vous pouvez afficher ou modifier le paramètre d’un produit spécifique.

Pour obtenir le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Pour activer le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Pour désactiver le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Exemple de script pour désactiver AllowSelfServicePurchase

L’exemple suivant explique comment importer le module **MSCommerce** , se connecter avec votre compte, obtenir le **ProductID** de Power automate, puis désactiver **AllowSelfServicePurchase** pour ce produit.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

## <a name="troubleshooting"></a>Résolution des problèmes

**Problème**

Le message d’erreur suivant s’affiche :

    HandleError : Failed to retrieve policy with PolicyId 'AllowSelfServicePurchase', ErrorMessage - The underlying
    connection was closed: An unexpected error occurred on a send.

Cela peut être dû à une version plus ancienne de TLS (Transport Layer Security). Pour connecter ce service, vous devez utiliser TLS 1,2 ou une version ultérieure.

**Solution**

Effectuez une mise à niveau vers TLS 1,2 :[https://docs.microsoft.com/configmgr/core/plan-design/security/enable-tls-1-2](https://docs.microsoft.com/configmgr/core/plan-design/security/enable-tls-1-2)

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->