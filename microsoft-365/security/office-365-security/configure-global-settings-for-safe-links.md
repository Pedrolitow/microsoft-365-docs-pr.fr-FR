---
title: Configurer les paramètres globaux des paramètres de liens sécurisés dans Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir comment afficher et configurer les paramètres globaux (la liste « Bloquer les URL suivantes » et la protection pour les applications Office 365) pour les liens sécurisés dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 623b1bcd670f42c7c6b49c06cacfa31cb8adfd49
ms.sourcegitcommit: f3d1009840513703c38bab99a6e13a3656eae5ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2021
ms.locfileid: "52792991"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Configurer les paramètres globaux pour la stratégie de liens sécurisés dans Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous êtes un utilisateur d’accueil à la recherche d’informations sur les liens sécurisés dans Outlook, voir [Advanced Outlook.com security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

La fonctionnalité Liens sécurisés de [Microsoft Defender](defender-for-office-365.md) pour Office 365 permet d’analyser les URL des messages électroniques entrants dans le flux de messagerie et de vérifier en un clic les URL et les liens dans les messages électroniques et à d’autres emplacements. Pour plus d’informations, [voir Liens sécurisés dans Microsoft Defender pour Office 365](safe-links.md).

Vous configurez la plupart des paramètres de liens sécurisés dans les stratégies de liens sécurisés. Pour obtenir des instructions, voir [Configurer des stratégies de liens sécurisés dans Microsoft Defender Office 365](set-up-safe-links-policies.md).

Toutefois, la stratégie de liens sécurisés utilise également les paramètres globaux suivants que vous configurez en dehors des stratégies de liens sécurisés elles-mêmes :

- La **liste Bloquer les URL suivantes.** Ce paramètre s’applique à tous les utilisateurs inclus dans les stratégies de liens sécurisés actives. Pour plus d’informations, consultez la liste [« Bloquer les URL suivantes](safe-links.md#block-the-following-urls-list-for-safe-links) » pour les liens sécurisés
- Protection des liens sécurisés pour Office 365 applications. Ces paramètres s’appliquent à tous les utilisateurs de l’organisation titulaires d’une licence Defender pour Office 365, que les utilisateurs soient inclus ou non dans les stratégies de liens sécurisés actives. Pour plus d’informations, voir paramètres de liens [sécurisés pour Office 365 applications.](safe-links.md#safe-links-settings-for-office-365-apps)

Vous pouvez configurer les paramètres globaux de liens sécurisés dans le Centre de sécurité Microsoft 365 ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres en Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online, mais avec Microsoft Defender pour les abonnements de modules supplémentaires Office 365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

- Il n’existe aucune stratégie de liens sécurisés intégrée ou par défaut. Vous devez donc créer au moins une stratégie de liens sécurisés pour que la liste Bloquer les URL **suivantes** soit active. Pour obtenir des instructions, voir [Configurer des stratégies de liens sécurisés dans Microsoft Defender Office 365](set-up-safe-links-policies.md).

- Vous ouvrez le centre de sécurité à <https://security.microsoft.com/>. Pour aller directement à la page **Liens sécurisés,** utilisez <https://security.microsoft.com/safelinksv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour configurer les paramètres globaux des liens sécurisés,  vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité.
  - Pour accéder en lecture seule aux paramètres globaux des liens  sécurisés,  vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour obtenir les valeurs recommandées pour les paramètres globaux de liens sécurisés, consultez les [paramètres de liens sécurisés.](recommended-settings-for-eop-and-office365.md#safe-links-settings)

- Autorisez jusqu’à 30 minutes pour qu’une stratégie nouvelle ou mise à jour soit appliquée.

- [De nouvelles fonctionnalités sont continuellement ajoutées à Microsoft Defender pour Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). À mesure que de nouvelles fonctionnalités sont ajoutées, vous devrez peut-être apporter des ajustements à vos stratégies de liens sécurisés existantes.

## <a name="configure-the-block-the-following-urls-list-in-the-security-center"></a>Configurer la liste « Bloquer les URL suivantes » dans le centre de sécurité

La **liste Bloquer les URL suivantes** identifie les liens qui doivent toujours être bloqués par l’analyse des liens sécurisés dans les applications pris en charge. Pour plus d’informations, consultez la liste « Bloquer les URL suivantes » [pour les liens sécurisés.](safe-links.md#block-the-following-urls-list-for-safe-links)

1. Dans le centre de sécurité, go to **Email & Collaboration** Policies & \> **Rules** Threat \>  \> **policies** section \> **Safe Links**.

2. Dans la page **Liens sécurisés,** cliquez **sur Paramètres globaux.** Dans la **stratégie de liens sécurisés de votre** organisation qui s’affiche, allez dans la zone Bloquer les URL **suivantes.**

3. Configurez une ou plusieurs entrées comme décrit dans la syntaxe d’entrée pour la liste [« Bloquer les URL suivantes](safe-links.md#entry-syntax-for-the-block-the-following-urls-list)».

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Configurer la liste « Bloquer les URL suivantes » dans PowerShell

Pour plus d’informations sur la syntaxe d’entrée, voir la syntaxe d’entrée pour la liste [« Bloquer les URL suivantes](safe-links.md#entry-syntax-for-the-block-the-following-urls-list)».

Vous pouvez utiliser la cmdlet **Get-AtpPolicyForO365** pour afficher les entrées existantes dans la _propriété BlockURLs._

- Pour ajouter des valeurs qui remplaceront les entrées existantes, utilisez la syntaxe suivante dans Exchange Online PowerShell ou Exchange Online Protection PowerShell :

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  Cet exemple ajoute les entrées suivantes à la liste :

  - Bloquez le domaine, les sous-domaines et les chemins d’accès fabrikam.com.
  - Bloquer la recherche de sous-domaine, mais pas le domaine parent ou d’autres sous-domaines dans tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Pour ajouter ou supprimer des valeurs sans affecter les autres entrées existantes, utilisez la syntaxe suivante :

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  Cet exemple ajoute une nouvelle entrée pour adatum.com et supprime l’entrée pour fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-security-center"></a>Configurer la protection des liens sécurisés pour Office 365 applications dans le centre de sécurité

La protection des liens sécurisés Office 365 applications s’applique aux documents dans les applications Office bureau, mobiles et web pris en charge. Pour plus d’informations, voir paramètres de liens [sécurisés pour Office 365 applications.](safe-links.md#safe-links-settings-for-office-365-apps)

1. Dans le centre de sécurité, go to **Email & Collaboration** Policies & \> **Rules** Threat \>  \> **policies** section \> **Safe Links**.

2. Dans la page **Liens sécurisés,** cliquez **sur Paramètres globaux.** Dans **la** stratégie de liens sécurisés de votre organisation qui s’affiche, configurez les paramètres suivants dans la Paramètres qui s’appliquent au contenu de la section applications Office 365 **pris** en charge :

   - **Utilisez des liens sécurisés dans Office 365 applications**: vérifiez que le basculement se trouve à droite pour activer les liens sécurisés pour les applications Office 365 pris en charge : ![ activer/ ](../../media/scc-toggle-on.png) activer.

   - Ne suivez pas le moment où les utilisateurs cliquent sur les liens protégés dans les applications **Office 365**: déplacez le bouton bascule vers la gauche pour suivre les clics des utilisateurs liés aux URL bloquées dans les applications Office 365 pris en charge : basculez vers la ![ ](../../media/scc-toggle-off.png) gauche.

   - Ne laissez pas les utilisateurs accéder à l’URL d’origine dans les applications **Office 365 :** vérifiez que le bouton bascule est à droite pour empêcher les utilisateurs de cliquer sur l’URL bloquée d’origine dans les applications Office 365 pris en charge : basculez sur ![ ](../../media/scc-toggle-on.png) .

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>Configurer la protection des liens sécurisés pour Office 365 applications dans PowerShell

Si vous préférez utiliser PowerShell pour configurer la protection des liens sécurisés pour les applications Office 365, utilisez la syntaxe suivante dans Exchange Online PowerShell ou Exchange Online Protection PowerShell :

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

Cet exemple configure les paramètres suivants pour la protection des liens sécurisés dans Office 365 applications :

- La fonction Liens sécurisés pour Office 365 applications est activée (nous n’utilisons pas le paramètre _EnableSafeLinksForO365Clients_ et la valeur par défaut est $true).
- L’utilisateur clique sur les URL bloquées dans les Office 365 les applications sont suivis.
- Les utilisateurs ne sont pas autorisés à accéder à l’URL bloquée d’origine dans les applications Office 365 pris en charge (nous n’utilisons pas le paramètre _AllowClickThrough_ et la valeur par défaut est $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement configuré les paramètres globaux des liens sécurisés (la liste Bloquer les URL suivantes et les **paramètres** de protection des applications Office 365), vous devez suivre l’une des étapes suivantes :

- Dans le centre de  sécurité, rendez-vous dans la section Stratégies de stratégies de menace des règles de & de messagerie & Cliquez sur Paramètres globaux et vérifiez les paramètres dans le volant qui \>  \>  \>  \>  \> s’affiche. 

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, exécutez la commande suivante et vérifiez les paramètres :

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
