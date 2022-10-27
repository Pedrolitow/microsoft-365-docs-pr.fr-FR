---
title: Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce
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
- Tier2
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
ms.date: 10/10/2022
ms.openlocfilehash: 755e8c6314cbb21f1adef6d55acaf696445fc434
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720899"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce

Le module **MsCommerce** PowerShell est désormais disponible sur [PowerShell Gallery](https://aka.ms/allowselfservicepurchase-powershell-gallery). Le module inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service.

Vous pouvez utiliser le module **PowerShell MSCommerce** pour :

- Afficher l’état par défaut de la valeur du paramètre **AllowSelfServicePurchase** , qu’il soit activé, désactivé ou autorise les essais sans mode de paiement
- Affichez la liste des produits applicables et indiquez si l’achat en libre-service est activé, désactivé ou autorise les essais sans mode de paiement
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver
- Afficher ou modifier le paramètre pour les essais sans modes de paiement

## <a name="requirements"></a>Conditions requises

Pour utiliser le module **PowerShell MSCommerce** , vous avez besoin des éléments suivants :

- Système d’exploitation Windows 10 ou version ultérieure.
- PowerShell 5 ou version antérieure. Actuellement, PowerShell 6.x/7.x n’est pas pris en charge avec ce module.
- Le rôle d’administrateur général ou d’administrateur de facturation pour votre locataire afin de modifier les stratégies de produit **MSCommerce** .
- Rôle de lecteur global pour votre locataire afin d’afficher une liste en lecture seule des stratégies de produit **MSCommerce** .

## <a name="install-the-mscommerce-powershell-module"></a>Installer le module PowerShell MSCommerce

Vous installez le module **PowerShell MSCommerce** sur votre appareil Windows 10 une fois, puis vous l’importez dans chaque session PowerShell que vous démarrez. Téléchargez le module **PowerShell MSCommerce** à partir du [PowerShell Gallery](https://aka.ms/allowselfservicepurchase-powershell-gallery).

Pour installer le module **MsCommerce** PowerShell avec **PowerShellGet**, exécutez la commande suivante :

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

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Afficher la liste des produits achetés en libre-service et leur état

Pour afficher la liste de tous les produits d’achat en libre-service disponibles et l’état de chacun d’eux, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

Le tableau suivant répertorie les produits disponibles et leur **ProductId**. Il indique également quels produits ont une version d’évaluation disponible et ne nécessitent pas de mode de paiement. Le cas échéant, tous les autres essais nécessitent un mode de paiement. Pour les produits pour lesquels la version d’évaluation sans mode de paiement est activé, vous pouvez activer la version d’évaluation, tout en gardant la possibilité d’acheter le produit désactivée. Pour obtenir des exemples de commandes, consultez Afficher ou définir l’état de **AllowSelfServicePurchase**.

| Produit | Productid | La version d’évaluation sans mode de paiement est-elle activée ? |
|-----------------------------|--------------|--------------|
| Power Apps par utilisateur* | CFQ7TTC0LH2H | Non |
| Power Automate par utilisateur | CFQ7TTC0KP0N | Non |
| Power Automate RPA | CFQ7TTC0KXG6  | Non |
| Power BI Premium (autonome) | CFQ7TTC0KXG7  | Non |
| Power BI Pro | CFQ7TTC0L3PB | Non |
| Project (plan 1)* | CFQ7TTC0HDB1 | Oui |
| Project (plan 3)* | CFQ7TTC0HDB0 | Non |
| Visio (plan 1)* | CFQ7TTC0HD33 | Non |
| Visio (plan 2)* | CFQ7TTC0HD32 | Non |
| Windows 365 Entreprise | CFQ7TTC0HHS9 | Non |
| Windows 365 Business | CFQ7TTC0J203 | Non |
| Windows 365 Affaires avec Windows Hybrid Benefit | CFQ7TTC0HX99 | Non |
| Microsoft 365 F3 | CFQ7TTC0LH05 | Non |
| Dynamics 365 Marketing | CFQ7TTC0LH3N | Non |
| Dynamics 365 Marketing Attach | CFQ7TTC0LHWP | Non |
| Application supplémentaire Dynamics 365 Marketing | CFQ7TTC0LHVK | Non |
| Application dynamics 365 Marketing supplémentaire non-Prod | CFQ7TTC0LHWM | Non |

*Ces ID ont changé. Si vous avez précédemment bloqué des produits à l’aide des anciens ID, ils sont automatiquement bloqués à l’aide des nouveaux ID. Aucun autre travail n’est nécessaire.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Afficher ou définir l’état de AllowSelfServicePurchase

Vous pouvez définir le paramètre **Value** pour **AllowSelfServicePurchase** afin d’autoriser ou d’empêcher les utilisateurs d’effectuer un achat en libre-service. Vous pouvez également utiliser la valeur **OnlyTrialsWithoutPaymentMethod** pour permettre aux utilisateurs d’essayer des produits qui n’ont pas de paiement d’essai requis. Reportez-vous à la liste des produits ci-dessus pour connaître les produits pour lesquels ces essais sont activés. Les utilisateurs peuvent acheter le produit uniquement après la fin de la version d’évaluation si **AllowSelfServicePurchase** est activé.

> [!NOTE]
> La modification de la valeur de **AllowSelfServicePurchase** ou **OnlyTrialsWithoutPaymentMethod** affecte uniquement les essais ou les achats effectués pour le produit spécifié à partir de ce moment. Les essais ou achats existants pour le produit spécifié ne sont pas affectés.

Le tableau suivant décrit les paramètres du paramètre **Value** .

| **Paramètre** | **Impact** |
|---|---|
| Activé | Les utilisateurs peuvent effectuer des achats en libre-service et acquérir des essais pour le produit. |
| OnlyTrialsWithoutPaymentMethod | Les utilisateurs ne peuvent pas effectuer d’achats en libre-service, mais peuvent acquérir des essais gratuits pour les produits qui n’ont pas besoin d’ajouter un mode de paiement. Une fois la version d’évaluation expirée, un utilisateur ne peut pas acheter la version payante du produit. |
| Désactivé | Les utilisateurs ne peuvent pas effectuer d’achats en libre-service ou acquérir des essais pour le produit. |

Pour obtenir le paramètre de stratégie d’un produit spécifique, exécutez la commande suivante :

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Pour activer le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Value "Enabled"
```

Pour désactiver le paramètre de stratégie pour un produit spécifique, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Value "Disabled"
```

Pour permettre aux utilisateurs d’essayer un produit spécifique sans mode de paiement, exécutez la commande suivante :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Value "OnlyTrialsWithoutPaymentMethod" 
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Exemple de script pour désactiver AllowSelfServicePurchase

L’exemple suivant vous montre comment importer le module **MSCommerce** , vous connecter avec votre compte, obtenir le **ProductId** pour Power Automate par utilisateur, puis désactiver **AllowSelfServicePurchase** pour ce produit.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate per user'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Value "Disabled"
```

S’il existe plusieurs valeurs pour le produit, vous pouvez exécuter la commande individuellement pour chaque valeur, comme indiqué dans l’exemple suivant :

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Value "Disabled"
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Value "Disabled"
```

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="problem"></a>Problème

Le message d’erreur suivant s’affiche :

> HandleError : échec de la récupération de la stratégie avec PolicyId 'AllowSelfServicePurchase', ErrorMessage - La connexion sous-jacente a été fermée : une erreur inattendue s’est produite lors d’un envoi.

Cela peut être dû à une version antérieure de TLS (Transport Layer Security). Lorsque vous vous connectez à ce service, vous devez utiliser TLS 1.2 ou une version ultérieure

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

[Gérer les achats en libre-service (Administration)](manage-self-service-purchases-admins.md) (article)\
[FAQ sur les achats en libre-service](self-service-purchase-faq.yml) (article)
