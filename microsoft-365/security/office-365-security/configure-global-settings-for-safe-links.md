---
title: Configurer les paramètres globaux pour les paramètres de liens fiables dans Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à afficher et à configurer les paramètres globaux (la liste des URL de blocage et la liste 365 des URL suivantes) pour les liens fiables dans Microsoft Defender pour Office 365.
ms.openlocfilehash: bc44432d4d9478e4c6a2414a70acc785c5b2c005
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682904"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Configurer les paramètres globaux pour les liens fiables dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](office-365-atp.md). Si vous êtes un utilisateur à domicile et que vous recherchez des informations sur Safelinks dans Outlook, consultez la rubrique [Advanced Outlook.com Security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

La fonctionnalité liens fiables est une fonctionnalité de [Microsoft Defender pour Office 365](office-365-atp.md) qui permet d’analyser les messages électroniques entrants dans le flux de messagerie et de cliquer sur vérification des URL et des liens dans les messages électroniques et à d’autres emplacements. Pour plus d’informations, reportez-vous à [liens fiables dans Microsoft Defender pour Office 365](atp-safe-links.md).

Vous configurez la plupart des paramètres de liens fiables dans stratégies de liens fiables. Pour obtenir des instructions, reportez-vous à la rubrique [configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-atp-safe-links-policies.md).

Toutefois, les liens fiables utilisent également des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans les stratégies de liens fiables actives. Ces paramètres globaux :

- La liste **bloquer les URL suivantes** . Pour plus d’informations, reportez-vous à [la liste « bloquer les URL suivantes » pour les liens fiables](atp-safe-links.md#block-the-following-urls-list-for-safe-links)
- Protection des liens fiables pour les applications Office 365. Pour plus d’informations, consultez la rubrique [paramètres de liens approuvés pour les applications Office 365](atp-safe-links.md#safe-links-settings-for-office-365-apps).

Vous pouvez configurer les paramètres de liens de sécurité globaux dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange pour les organisations sans boîtes aux lettres Exchange Online, mais avec Microsoft Defender for Office 365 compléments d’abonnement).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Les fonctionnalités fournies par les paramètres globaux pour les liens fiables s’appliquent uniquement aux utilisateurs qui sont inclus dans les stratégies de liens fiables actifs. Il n’existe pas de stratégie de liens de sécurité intégrée ou par défaut, vous devez donc créer au moins une stratégie de liens fiables pour que ces paramètres globaux soient actifs. Pour obtenir des instructions, reportez-vous à la rubrique [configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-atp-safe-links-policies.md).

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **liens approuvés** , utilisez <https://protection.office.com/safelinksv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour pouvoir utiliser ce cmdlet, vous devez disposer des autorisations dans le centre de sécurité et conformité Office 365.
  - Pour configurer les paramètres globaux pour les liens fiables, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** .
  - Pour un accès en lecture seule aux paramètres globaux pour les liens fiables, vous devez être membre des groupes de rôles **lecteur global** ou **lecteur de sécurité** .

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour connaître les valeurs recommandées pour les paramètres globaux des liens fiables, consultez la rubrique [Safe Links Settings](recommended-settings-for-eop-and-office365-atp.md#safe-links-settings).

- Autoriser jusqu’à 30 minutes pour l’application d’une stratégie nouvelle ou mise à jour.

- De [nouvelles fonctionnalités sont continuellement ajoutées à Microsoft Defender pour Office 365](office-365-atp.md#new-features-in-microsoft-defender-for-office-365). À mesure que de nouvelles fonctionnalités sont ajoutées, vous devrez peut-être apporter des ajustements aux stratégies de liens fiables existantes.

## <a name="configure-the-block-the-following-urls-list-in-the-security--compliance-center"></a>Configurer la liste « bloquer les URL suivantes » dans le centre de sécurité & conformité

La liste **bloquer les URL suivantes** identifie les liens qui doivent toujours être bloqués par l’analyse des liens fiables dans les applications prises en charge. Pour plus d’informations, reportez-vous à [la section « bloquer les URL suivantes » pour les liens fiables](atp-safe-links.md#block-the-following-urls-list-for-safe-links).

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \>  \> **liens approuvés ATP**, puis cliquez sur **paramètres globaux**.

2. Dans la **stratégie de liens fiables pour votre organisation** , passez à la zone **bloquer les URL suivantes** .

3. Configurez une ou plusieurs entrées comme décrit dans [la syntaxe d’entrée pour la liste « bloquer les URL suivantes »](atp-safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Configurer la liste « bloquer les URL suivantes » dans PowerShell

Pour plus d’informations sur la syntaxe d’entrée, voir la [syntaxe d’entrée pour la liste « bloquer les URL suivantes »](atp-safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

Vous pouvez utiliser la cmdlet **Get-AtpPolicyForO365** pour afficher les entrées existantes dans la propriété _BlockURLs_ .

- Pour ajouter des valeurs qui remplaceront toutes les entrées existantes, utilisez la syntaxe suivante dans Exchange Online PowerShell ou Exchange Online Protection PowerShell :

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  Cet exemple montre comment ajouter les entrées suivantes à la liste :

  - Bloquez le domaine, les sous-domaines et les chemins d’accès pour fabrikam.com.
  - Bloquer la recherche de sous-domaine, mais pas le domaine parent, ni les autres sous-domaines dans tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Pour ajouter ou supprimer des valeurs sans affecter les entrées existantes, utilisez la syntaxe suivante :

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  Cet exemple montre comment ajouter une nouvelle entrée pour adatum.com et supprimer l’entrée pour fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-security--compliance-center"></a>Configuration de la protection des liens fiables pour les applications Office 365 dans le centre de sécurité & conformité

La protection des liens fiables pour les applications Office 365 s’applique aux documents dans les applications de bureau, mobiles et Web Office prises en charge. Pour plus d’informations, consultez la rubrique [paramètres de liens approuvés pour les applications Office 365](atp-safe-links.md#safe-links-settings-for-office-365-apps).

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \>  \> **liens approuvés ATP**, puis cliquez sur **paramètres globaux**.

2. Dans la **stratégie de liens fiables pour votre organisation** , la fonctionnalité de survol qui s’affiche, configurez les paramètres suivants dans la section **paramètres qui s’appliquent au contenu à l’exception de la messagerie** :

   - **Applications office 365**: Vérifiez que le bouton bascule est sur la droite pour activer les liens fiables pour les applications Office 365 prises en charge : ![ activer/désactiver ](../../media/scc-toggle-on.png) .

   - **Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables**: déplacer le bouton bascule vers la gauche pour suivre les clics d’utilisateur liés aux URL bloquées dans les applications Office 365 prises en charge : désactiver ![ ](../../media/scc-toggle-off.png) .

   - **Ne laissez pas les utilisateurs cliquer via les liens fiables à l’URL d’origine**: Vérifiez que le bouton bascule est sur la droite pour empêcher les utilisateurs de cliquer sur l’URL bloquée d’origine dans les applications Office 365 prises en charge : ![ activer/désactiver ](../../media/scc-toggle-on.png) .

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>Configurer la protection des liens fiables pour les applications Office 365 dans PowerShell

Si vous préférez utiliser PowerShell pour configurer la protection des liens approuvés pour les applications Office 365, utilisez la syntaxe suivante dans Exchange Online PowerShell ou Exchange Online Protection PowerShell :

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

Cet exemple montre comment configurer les paramètres suivants pour la protection des liens fiables dans les applications Office 365 :

- Les liens approuvés pour les applications Office 365 sont activés (nous n’utilisons pas le paramètre _EnableSafeLinksForO365Clients_ et la valeur par défaut est $true).
- Les utilisateurs cliquent sur en relation avec les URL bloquées dans les applications Office 365 prises en charge sont suivies.
- Les utilisateurs ne sont pas autorisés à cliquer à travers l’URL bloquée d’origine dans les applications Office 365 prises en charge (nous n’utilisons pas le paramètre _AllowClickThrough_ et la valeur par défaut est $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien configuré les paramètres globaux pour les liens fiables (la liste **bloquer les URL suivantes** et les paramètres protection des applications Office 365), effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \>  \> **liens approuvés ATP**, cliquez sur **paramètres globaux** et vérifiez les paramètres dans le survol qui s’affiche.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, exécutez la commande suivante et vérifiez les paramètres :

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/get-atppolicyforo365).
