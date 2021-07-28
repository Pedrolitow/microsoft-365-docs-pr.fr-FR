---
title: Gérer vos blocs dans la liste d’attente des locataires
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
description: Les administrateurs peuvent apprendre à configurer des blocs dans la liste d’adresses client autoriser/bloquer dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 38347850b66c2a83708df12aaa3233a0afe01444
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53543932"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Ajouter des blocs dans la liste des locataires autoriser/bloquer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Créer des entrées d’URL de bloc dans la liste d’adresses client autoriser/bloquer

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Dans la page Liste d’adresses  client **autoriser/bloquer,** vérifiez que l’onglet URL est sélectionné, puis cliquez sur Bloquer l’icône ![ ](../../media/m365-cc-sc-create-icon.png) **Bloquer.**

3. Dans le **volant Bloquer les URL** qui s’affiche, configurez les paramètres suivants :
   - **Ajouter des URL avec des caractères génériques**: entrez une URL par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’URL, voir la section syntaxe de l’URL dans Gérer la liste d’adresses client [autoriser/bloquer.](tenant-allow-block-list.md)
   - **N’expirez jamais**: faites l’une des étapes suivantes :
     - Vérifiez que le paramètre est désactivé (basculement désactivé) et utilisez la zone Supprimer sur pour spécifier la ![ date d’expiration ](../../media/scc-toggle-off.png) des entrées. 

       ou

     - Déplacez le basculement vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer](../../media/scc-toggle-on.png).
   - **Remarque facultative**: entrez un texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Créer des entrées de fichiers bloqués dans la liste d’attente du client

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Dans la page Liste des clients **autoriser/bloquer,** sélectionnez l’onglet **Fichiers,** puis cliquez sur Bloquer l’icône ![ ](../../media/m365-cc-sc-create-icon.png) **Bloquer.**

3. Dans le **volant Bloquer les fichiers** qui s’affiche, configurez les paramètres suivants :
   - **Ajouter des hachages de fichier**: entrez une valeur de hachage SHA256 par ligne, jusqu’à un maximum de 20.
   - **N’expirez jamais**: faites l’une des étapes suivantes :
     - Vérifiez que le paramètre est désactivé (basculement désactivé) et utilisez la zone Supprimer sur pour spécifier la ![ date d’expiration ](../../media/scc-toggle-off.png) des entrées. 

     ou

     - Déplacez le basculement vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer](../../media/scc-toggle-on.png).
   - **Remarque facultative**: entrez un texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

### <a name="create-spoofed-sender-block-entries"></a>Créer des entrées de bloc d’expéditeurs usurpées

**Remarques** :

- Seule la _combinaison_ de l’utilisateur usurpé et de l’infrastructure d’envoi, telle que définie dans la paire de domaines, est spécifiquement autorisée ou bloquée à l’usurpation. 
- Lorsque vous configurez une entrée d’autoriser ou de bloquer une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans l’aperçu de l’usurpation d’intelligence.
- Les entrées des expéditeurs usurpés n’expirent jamais.
- L’usurpation prend en charge à la fois autoriser et bloquer. L’URL prend uniquement en charge l’autoriser.

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Dans la page **Client autoriser/Bloquer la liste,** sélectionnez l’onglet **Usurpation** d’informations, puis cliquez sur Bloquer ![ l’icône ](../../media/m365-cc-sc-create-icon.png) **Ajouter.**

3. Dans le **volant Ajouter de nouvelles paires de domaines** qui s’affiche, configurez les paramètres suivants :
   - **Ajoutez de nouvelles paires de domaines avec des caractères génériques**: entrez une paire de domaines par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, voir Gérer la liste d’adresses client [autoriser/bloquer.](tenant-allow-block-list.md)
   - **Type d’usurpation**: sélectionnez l’une des valeurs suivantes :
     - **Interne**: l’expéditeur usurpé se trouve dans un domaine appartenant à votre organisation [(un domaine accepté).](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)
     - **Externe**: l’expéditeur usurpé se trouve dans un domaine externe.
   - **Action**: **sélectionnez Autoriser** ou **Bloquer.**

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="use-powershell"></a>Utiliser PowerShell

### <a name="add-block-file-or-url-entries-to-the-tenant-allowblock-list"></a>Ajouter des entrées de bloc de fichier ou d’URL à la liste d’adresses client autoriser/bloquer

Pour ajouter des entrées de blocage de fichier ou d’URL dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple ajoute une entrée de bloc de fichiers pour les fichiers spécifiés qui n’expire jamais.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Cet exemple ajoute une entrée d’URL de bloc pour contoso.com et tous les sous-contoso.com (par exemple, contoso.com, www.contoso.com et xyz.abc.contoso.com). Étant donné que nous n’avons pas utilisé les paramètres ExpirationDate ou NoExpiration, l’entrée expire au bout de 30 jours.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Ajouter des entrées de blocage des expéditeurs usurpés 

Pour ajouter des entrées d’expéditeur usurpées dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).