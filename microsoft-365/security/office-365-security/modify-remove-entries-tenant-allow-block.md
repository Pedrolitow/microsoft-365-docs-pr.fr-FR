---
title: Modifier et supprimer des entrées dans la liste verte/rouge du client
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à modifier et à supprimer des entrées dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ac612b51cab9069e50c4eec05948b3aa840b9cc9
ms.sourcegitcommit: 4d6a8e9d69a421d6c293b2485a8aa5e806b71616
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65182692"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Modifier et supprimer des entrées dans la liste verte/rouge du client

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous pouvez utiliser le portail Microsoft 365 Defender ou PowerShell pour modifier et supprimer des entrées dans la liste d’autorisation/de blocage du locataire.

## <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Modifier les entrées dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet qui contient le type d’entrée à modifier :
   - **Expéditeurs**
   - **Spoofing**
   - **Url**
   - **Files**

3. Sélectionnez l’entrée à modifier, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**. Les valeurs que vous pouvez modifier dans le menu volant qui s’affiche dépendent de l’onglet que vous avez sélectionné à l’étape précédente :
   - **Expéditeurs**
     - **N’expirez jamais** et/ou date d’expiration.
     - **Remarque facultative**
   - **Spoofing**
     - **Action** : vous pouvez modifier la valeur en **Allow** ou **Block**.
   - **Url**
     - **N’expirez jamais** et/ou date d’expiration.
     - **Remarque facultative**
   - **Files**
     - **N’expirez jamais** et/ou date d’expiration.
     - **Remarque facultative**

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

> [!NOTE]
> Vous ne pouvez étendre que 30 jours après la date de création. Les blocs peuvent être étendus jusqu’à 90 jours, mais contrairement aux autorisations, ils peuvent également être définis sur Ne jamais expirer.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Supprimer des entrées de la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet qui contient le type d’entrée à supprimer :
   - **Expéditeurs**
   - **Spoofing**
   - **Url**
   - **Files**

3. Sélectionnez l’entrée à supprimer, puis cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**.

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer**.

## <a name="use-powershell"></a>Utiliser PowerShell

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>Modifier les entrées autoriser ou bloquer l’expéditeur, le fichier et l’URL dans la liste d’autorisations/de blocs du locataire

Pour modifier les entrées d’expéditeur, de fichier et d’URL autorisées ou bloquées dans la liste d’autorisations/blocs du locataire, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Cet exemple montre comment modifier la date d’expiration de l’entrée d’URL de bloc spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>Supprimer l’expéditeur, l’URL ou les entrées de fichier autorisés ou bloqués de la liste d’autorisations/de blocs du locataire

Pour supprimer ou bloquer les entrées d’expéditeur, de fichier et d’URL de la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

Cet exemple montre comment supprimer l’entrée d’URL de bloc spécifiée de la liste d’autorisations/de blocs du locataire.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Modifier ou bloquer les entrées d’expéditeur usurpées à partir de la liste d’autorisations/de blocs du locataire

Pour modifier ou bloquer les entrées d’expéditeur usurpées dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

Cet exemple montre comment faire passer l’entrée de l’expéditeur usurpé de l’autorisation au bloc.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Supprimer les entrées d’expéditeur autorisées ou de bloquer les entrées d’expéditeur usurpées de la liste d’autorisations/de blocs du locataire

Pour supprimer les entrées d’expéditeur d’autorisation ou de blocage de la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
