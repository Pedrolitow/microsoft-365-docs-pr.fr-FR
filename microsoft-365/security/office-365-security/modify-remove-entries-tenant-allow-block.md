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
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir comment modifier et supprimer des entrées dans la liste d’adresses client autoriser/bloquer dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 951468fb9b3245135356d956e488c55390e9c6f9
ms.sourcegitcommit: 99817013bcb26b7ed051e011c8addb716cc91d8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58349787"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Modifier et supprimer des entrées dans la liste verte/rouge du client

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous pouvez utiliser le portail Microsoft 365 Defender ou PowerShell pour modifier et supprimer des entrées dans la liste d’attente des locataires.

## <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Modifier des entrées dans la liste d’inscriptions du client

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Sélectionnez l’onglet qui contient le type d’entrée à modifier :
   - **Expéditeurs)
   - **URL**
   - **Files**
   - **Usurpation**

3. Sélectionnez l’entrée à modifier, puis cliquez sur ![ Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier.** Les valeurs que vous pouvez modifier dans le volant qui s’affiche dépendent de l’onglet que vous avez sélectionné à l’étape précédente :
   - **Expéditeurs**
     - **Ne jamais expirer** et/ou date d’expiration.
     - **Note facultative**
   - **URL**
     - **Ne jamais expirer** et/ou date d’expiration.
     - **Note facultative**
   - **Files**
     - **Ne jamais expirer** et/ou date d’expiration.
     - **Note facultative**
   - **Usurpation**
     - **Action**: vous pouvez modifier la valeur sur **Autoriser** ou **Bloquer**.
4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

> [!NOTE]
> Vous ne pouvez étendre les périodes d’extension que 30 jours au maximum après la date de création. Les blocs peuvent être étendus jusqu’à 90 jours, mais contrairement aux autoriser, ils peuvent également être définies sur Ne jamais expirer.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Supprimer des entrées de la liste des locataires autoriser/bloquer

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Sélectionnez l’onglet qui contient le type d’entrée à supprimer :
   - **Expéditeurs**
   - **URL**
   - **Files**
   - **Usurpation**

3. Sélectionnez l’entrée à supprimer, puis cliquez sur ![ Supprimer ](../../media/m365-cc-sc-delete-icon.png) **l’icône Supprimer.**

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer.**

## <a name="use-powershell"></a>Utiliser PowerShell

### <a name="modify-block-file-and-url-entries-in-the-tenant-allowblock-list"></a>Modifier les entrées de blocage de fichiers et d’URL dans la liste d’adresses client autoriser/bloquer

Pour modifier les entrées d’expéditeur, de fichier et d’URL de blocage dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Cet exemple modifie la date d’expiration de l’entrée d’URL de bloc spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-url-or-file-entries-from-the-tenant-allowblock-list"></a>Supprimer des entrées d’URL ou de fichier de la liste d’adresses client autoriser/bloquer

Pour supprimer des entrées d’expéditeur, de fichier et d’URL de la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

Cet exemple supprime l’entrée d’URL de bloc spécifiée de la liste d’adresses client autoriser/bloquer.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries"></a>Modifier les entrées d’expéditeurs usurpées ou d’autoriser ou bloquer

Pour modifier les entrées d’expéditeurs usurpées dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

Cet exemple modifie l’entrée de l’expéditeur usurpé de l’autoriser à la bloquer.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries"></a>Supprimer les entrées d’expéditeurs usurpées ou autoriser

Pour supprimer les entrées d’expéditeurs usurpant l’usurpation d’adresse de client de la liste d’expéditeurs bloqués ou d’expéditeurs d’usurpation d’adresses, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
