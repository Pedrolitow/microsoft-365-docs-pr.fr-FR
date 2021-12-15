---
title: Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: ''
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_ssp
search.appverid:
- MET150
description: Découvrez comment utiliser l’cmdlet AllowSelfServicePurchase PowerShell pour activer ou désactiver l’achat en libre-service.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 07/16/2021
ms.openlocfilehash: 4c4272b532fd40f1062404716614f8a7ee4a5230
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531896"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce

Le module **PowerShell MSCommerce** est désormais disponible dans la [galerie PowerShell.](https://aka.ms/allowselfservicepurchase-powershell-gallery) Le module inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service.

Vous pouvez utiliser le module **PowerShell MSCommerce** pour :

- Afficher l’état par défaut de la valeur du paramètre **AllowSelfServicePurchase** , qu’elle soit activée ou désactivée
- Afficher la liste des produits applicables et si l’achat en libre-service est activé ou désactivé
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver

## <a name="requirements"></a>Configuration requise

Pour utiliser le module **PowerShell MSCommerce,** vous devez :

- Un Windows 10 de sécurité
- PowerShell 5 ou inférieur. Actuellement, PowerShell 6.x/7.x n’est pas pris en charge avec ce module.
- Autorisation d’administrateur pour l’appareil
- Rôle d’administrateur global ou de facturation pour votre client

## <a name="install-the-mscommerce-powershell-module"></a>Installer le module PowerShell MSCommerce

Vous installez le module **PowerShell MSCommerce** sur votre appareil Windows 10 une seule fois, puis vous l’importez dans chaque session PowerShell que vous démarrez. Téléchargez le module **PowerShell MSCommerce** à partir de la [galerie PowerShell.](https://aka.ms/allowselfservicepurchase-powershell-gallery)

Pour installer le module **PowerShell MSCommerce** avec **PowerShellGet,** exécutez la commande suivante :

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importer MSCommerce dans la session PowerShell

Après avoir installé le module sur votre Windows 10, vous l’importez dans chaque session PowerShell que vous démarrez. Pour l’importer dans une session PowerShell, exécutez la commande suivante :

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Connecter MSCommerce avec vos informations d’identification

Pour vous connecter au module PowerShell avec vos informations d’identification, exécutez la commande suivante.

```powershell
Connect-MSCommerce
```

Cette commande connecte la session PowerShell actuelle à un Azure Active Directory client. La commande vous invite à entrer un nom d’utilisateur et un mot de passe pour le client à qui vous voulez vous connecter. Si l’authentification multifacteur est activée pour vos informations d’identification, vous utilisez l’option interactive pour vous connecter.

## <a name="view-details-for-allowselfservicepurchase"></a>Afficher les détails de AllowSelfServicePurchase

Pour afficher une description de la valeur du paramètre **AllowSelfServicePurchase** et de l’état par défaut, en fonction de votre organisation, exécutez la commande suivante :

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Afficher la liste des produits d’achat libre-service et leur état

Pour afficher la liste de tous les produits d’achat libre-service disponibles et l’état de chacun d’eux, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

Le tableau suivant répertorie les produits disponibles et leur **ProductId**.

| Produit | ProductId |
|-----------------------------|--------------|
| Power Apps par utilisateur | CFQ7TTC0KP0P |
| Power Automate par utilisateur | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| Power BI Premium (autonome) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project (plan 1)* | CFQ7TTC0HDB1 |
| Project (plan 3)* | CFQ7TTC0HDB0 |
| Visio (plan 1)* | CFQ7TTC0HD33 |
| Visio (plan 2)* | CFQ7TTC0HD32 |
| Windows 365 Entreprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows 365 Business avec Windows Hybrid Benefit | CFQ7TTC0HX99 |

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Afficher ou définir l’état de AllowSelfServicePurchase

>[!NOTE] 
> Ces ID ont changé. Si vous avez précédemment bloqué les produits utilisant les anciens ID, ils sont automatiquement bloqués à l’aide des nouveaux ID. Aucun travail supplémentaire n’est requis.

Une fois que vous avez vu la liste des produits disponibles pour l’achat en libre-service, vous pouvez afficher ou modifier le paramètre d’un produit spécifique.

Pour obtenir le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Pour activer le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Pour désactiver le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Exemple de script pour désactiver AllowSelfServicePurchase

L’exemple suivant vous explique comment importer le module **MSCommerce,** vous connectez avec votre compte, obtenez **le ProductId** pour Power Automate, puis désactivez **AllowSelfServicePurchase** pour ce produit.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

S’il existe plusieurs valeurs pour le produit, vous pouvez exécuter la commande individuellement pour chaque valeur, comme illustré dans l’exemple suivant :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="problem"></a>Problème

Vous voyez le message d’erreur suivant :

> HandleError : Échec de récupération de la stratégie avec PolicyId « AllowSelfServicePurchase » et ErrorMessage : la connexion sous-jacente a été fermée : une erreur inattendue s’est produite lors d’un envoi.

Cela peut être dû à une version antérieure de TLS (Transport Layer Security). Pour connecter ce service, vous devez utiliser TLS 1.2 ou supérieur

### <a name="solution"></a>Solution

Mise à niveau vers TLS 1.2. La syntaxe suivante met à jour le protocole de sécurité ServicePointManager vers TLS1.2 :

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Pour plus d’informations, [voir Comment activer TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>Contenu associé

[Gérer les achats en libre-service (administrateur)](manage-self-service-purchases-admins.md) (article)

[FAQ sur l’achat en libre-service](self-service-purchase-faq.yml) (article)
