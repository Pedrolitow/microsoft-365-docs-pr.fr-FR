---
title: Utiliser AllowSelfServicePurchase pour le module MSCommerce PowerShell
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: ''
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
search.appverid:
- MET150
description: Découvrez comment utiliser l’applet de commande PowerShell AllowSelfServicePurchase pour activer ou désactiver l’achat en libre-service.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 4/7/2022
ms.openlocfilehash: 8bc0771c259df759ecf900872db048b86a338443
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68163511"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Utiliser AllowSelfServicePurchase pour le module MSCommerce PowerShell

Le module **MSCommerce** PowerShell est désormais disponible sur [PowerShell Gallery](https://aka.ms/allowselfservicepurchase-powershell-gallery). Le module inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service.

Vous pouvez utiliser le module **MSCommerce** PowerShell pour :

- Afficher l’état par défaut de la valeur du paramètre **AllowSelfServicePurchase** , qu’elle soit activée ou désactivée
- Afficher la liste des produits applicables et déterminer si l’achat en libre-service est activé ou désactivé
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver

## <a name="requirements"></a>Conditions requises

Pour utiliser le module **MSCommerce** PowerShell, vous avez besoin des éléments suivants :

- Un appareil Windows 10
- PowerShell 5 ou version ultérieure. Actuellement, PowerShell 6.x/7.x n’est pas pris en charge avec ce module.
- Autorisation administrateur pour l’appareil
- Rôle de Administration globale ou de facturation pour votre locataire

## <a name="install-the-mscommerce-powershell-module"></a>Installer le module MSCommerce PowerShell

Vous installez le module **MSCommerce** PowerShell sur votre appareil Windows 10 une seule fois, puis vous l’importez dans chaque session PowerShell que vous démarrez. Téléchargez le module **MSCommerce** PowerShell à partir du [PowerShell Gallery](https://aka.ms/allowselfservicepurchase-powershell-gallery).

Pour installer le module **MSCommerce** PowerShell avec **PowerShellGet**, exécutez la commande suivante :

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importer MSCommerce dans la session PowerShell

Après avoir installé le module sur votre appareil Windows 10, vous l’importez dans chaque session PowerShell que vous démarrez. Pour l’importer dans une session PowerShell, exécutez la commande suivante :

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Se connecter à MSCommerce avec vos informations d’identification

Pour vous connecter au module PowerShell avec vos informations d’identification, exécutez la commande suivante.

```powershell
Connect-MSCommerce
```

Cette commande connecte la session PowerShell actuelle à un locataire Azure Active Directory. La commande vous invite à entrer un nom d’utilisateur et un mot de passe pour le locataire auquel vous souhaitez vous connecter. Si l’authentification multifacteur est activée pour vos informations d’identification, vous utilisez l’option interactive pour vous connecter.

## <a name="view-details-for-allowselfservicepurchase"></a>Afficher les détails de AllowSelfServicePurchase

Pour afficher une description de la valeur du paramètre **AllowSelfServicePurchase** et de l’état par défaut, en fonction de votre organisation, exécutez la commande suivante :

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Afficher la liste des produits d’achat en libre-service et leur état

Pour afficher la liste de tous les produits d’achat en libre-service disponibles et l’état de chacun d’eux, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

Le tableau suivant répertorie les produits disponibles et leur **ProductId**.

| Produit | Productid |
|-----------------------------|--------------|
| Power Apps par utilisateur* | CFQ7TTC0LH2H |
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
| Windows 365 Affaires avec Windows Hybrid Benefit | CFQ7TTC0HX99 |
| Microsoft 365 F3 | CFQ7TTC0LH05 |
| Dynamics 365 Marketing | CFQ7TTC0LH3N |
| Dynamics 365 Marketing Attach | CFQ7TTC0LHWP | 
| Application supplémentaire Dynamics 365 Marketing | CFQ7TTC0LHVK |
| Dynamics 365 Marketing - Application non prod supplémentaire | CFQ7TTC0LHWM |

*Ces ID ont changé. Si vous avez précédemment bloqué des produits à l’aide des anciens ID, ils sont automatiquement bloqués à l’aide des nouveaux ID. Aucun travail supplémentaire n’est nécessaire.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Afficher ou définir l’état de AllowSelfServicePurchase

Une fois que vous avez affiché la liste des produits disponibles pour l’achat en libre-service, vous pouvez afficher ou modifier le paramètre d’un produit spécifique.

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

L’exemple suivant vous guide tout au long de l’importation du module **MSCommerce** , de la connexion avec votre compte, de l’obtention du **ProductId** pour Power Automate par utilisateur, puis de la désactivation de **AllowSelfServicePurchase** pour ce produit.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate per user'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

S’il existe plusieurs valeurs pour le produit, vous pouvez exécuter la commande individuellement pour chaque valeur, comme indiqué dans l’exemple suivant :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="problem"></a>Problème

Le message d’erreur suivant s’affiche :

> HandleError : Échec de la récupération de la stratégie avec PolicyId « AllowSelfServicePurchase », ErrorMessage : la connexion sous-jacente a été fermée : une erreur inattendue s’est produite lors d’un envoi.

Cela peut être dû à une version antérieure de TLS (Transport Layer Security). Pour connecter ce service, vous devez utiliser TLS 1.2 ou version ultérieure

### <a name="solution"></a>Solution

Effectuez une mise à niveau vers TLS 1.2. La syntaxe suivante met à jour le protocole de sécurité ServicePointManager pour autoriser TLS1.2 :

```powershell
 [Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12
```

Pour en savoir plus, consultez [Comment activer TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>Contenu associé

[Gérer les achats en libre-service (Administration)](manage-self-service-purchases-admins.md) (article)

[FAQ sur l’achat en libre-service](self-service-purchase-faq.yml) (article)
