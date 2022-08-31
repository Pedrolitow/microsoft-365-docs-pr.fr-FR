---
title: Configurer des paramètres globaux pour les paramètres Liens fiables dans Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à afficher et à configurer des paramètres globaux (liste « Bloquer les URL suivantes » et protection pour les applications Office 365) pour les liens sécurisés dans Microsoft Defender pour Office 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: fb9e5159b4bee43d7e376af569151293aefd20f0
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481149"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Configurer les paramètres globaux des liens sécurisés dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous êtes un utilisateur à la recherche d’informations sur safelinks dans Outlook, consultez [Advanced Outlook.com security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Les liens sécurisés sont une fonctionnalité de [Microsoft Defender pour Office 365](defender-for-office-365.md) qui fournit l’analyse d’URL des messages électroniques entrants dans le flux de messagerie, ainsi que l’heure de clic de vérification des URL et des liens dans les messages électroniques et dans d’autres emplacements. Pour plus d’informations, consultez [Liens sécurisés dans Microsoft Defender pour Office 365](safe-links.md).

Vous configurez la plupart des paramètres Liens sécurisés dans les stratégies Liens sécurisés, y compris [les paramètres Liens sécurisés pour les applications Office prises en charge](safe-links.md#safe-links-settings-for-office-apps). Pour obtenir des instructions, consultez [Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

Toutefois, Liens sécurisés utilise également les paramètres globaux suivants que vous configurez en dehors des stratégies Liens fiables eux-mêmes :

- Liste **Bloquer les URL suivantes** . Ce paramètre s’applique à tous les utilisateurs inclus dans toutes les stratégies de liens fiables actives. Pour plus d’informations, consultez [la liste « Bloquer les URL suivantes » pour les liens fiables](safe-links.md#block-the-following-urls-list-for-safe-links)

Vous pouvez configurer les paramètres de liens fiables globaux dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans Exchange Online boîtes aux lettres, mais avec Microsoft Defender pour Office 365 abonnements aux modules complémentaires).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Bien qu’il n’existe aucune stratégie de liens fiables par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des liens sécurisés à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de liens fiables personnalisées ou les stratégies de sécurité standard ou strictes). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md). Vous pouvez également créer des stratégies de liens fiables à appliquer à des utilisateurs, des groupes ou des domaines spécifiques. Pour obtenir des instructions, consultez [Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour configurer les paramètres globaux des liens fiables, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux paramètres globaux des liens sécurisés, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour connaître les valeurs recommandées pour les paramètres globaux des liens fiables, consultez [les paramètres liens fiables](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Autorisez jusqu’à 30 minutes pour l’application d’une stratégie nouvelle ou mise à jour.

- [De nouvelles fonctionnalités sont continuellement ajoutées à Microsoft Defender pour Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). À mesure que de nouvelles fonctionnalités sont ajoutées, vous devrez peut-être apporter des ajustements à vos stratégies de liens fiables existantes.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Configurer la liste « Bloquer les URL suivantes » dans le portail Microsoft 365 Defender

> [!NOTE]
> Vous pouvez désormais gérer les entrées d’URL de bloc dans la [liste d’autorisations/de blocs du locataire](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-tenant-allowblock-list). La liste « Bloquer les URL suivantes » est en cours de dépréciation. Nous allons essayer de migrer des entrées existantes de la liste « Bloquer les URL suivantes » pour bloquer les entrées d’URL dans la liste d’autorisations/de blocs du locataire. Les messages contenant l’URL bloquée seront mis en quarantaine.

La liste **Bloquer les URL suivantes** identifie les liens qui doivent toujours être bloqués par l’analyse des liens fiables dans les applications prises en charge. Pour plus d’informations, consultez [la liste « Bloquer les URL suivantes » pour les liens sécurisés](safe-links.md#block-the-following-urls-list-for-safe-links).

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies **de menace** \> **des règles** \> **liens sécurisés** dans la section **Stratégies**. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Liens fiables** , cliquez sur **Paramètres globaux**. Dans la **stratégie Liens sécurisés pour votre organisation** qui s’affiche, accédez à la zone **Bloquer les URL suivantes** .

3. Configurez une ou plusieurs entrées comme décrit dans [la syntaxe d’entrée pour la liste « Bloquer les URL suivantes](safe-links.md#entry-syntax-for-the-block-the-following-urls-list) ».

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Configurer la liste « Bloquer les URL suivantes » dans PowerShell

Pour plus d’informations sur la syntaxe d’entrée, consultez [la syntaxe d’entrée pour la liste « Bloquer les URL suivantes](safe-links.md#entry-syntax-for-the-block-the-following-urls-list) ».

Vous pouvez utiliser l’applet de commande **Get-AtpPolicyForO365** pour afficher les entrées existantes dans la propriété _BlockURLs_ .

- Pour ajouter des valeurs qui remplaceront les entrées existantes, utilisez la syntaxe suivante dans Exchange Online PowerShell ou Exchange Online Protection PowerShell :

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  Cet exemple montre comment ajouter les entrées suivantes à la liste :

  - Bloquez le domaine, les sous-domaines et les chemins d’accès pour fabrikam.com.
  - Bloquer la recherche de sous-domaine, mais pas le domaine parent ou d’autres sous-domaines dans tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Pour ajouter ou supprimer des valeurs sans affecter d’autres entrées existantes, utilisez la syntaxe suivante :

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  Cet exemple ajoute une nouvelle entrée pour adatum.com et supprime l’entrée pour fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement configuré les paramètres globaux pour les liens sécurisés (la liste **Bloquer les URL suivantes et les paramètres** de protection des applications Office 365), effectuez l’une des étapes suivantes :

- Dans la page **Liens sécurisés** du portail <https://security.microsoft.com/safelinksv2>Microsoft 365 Defender, cliquez sur **Paramètres globaux** et vérifiez les paramètres dans le menu volant qui s’affiche.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, exécutez la commande suivante et vérifiez les paramètres :

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
