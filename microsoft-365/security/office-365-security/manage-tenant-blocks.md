---
title: Gérer vos blocs dans la liste d’autorisations/de blocs du locataire
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
description: Les administrateurs peuvent apprendre à configurer des blocs dans la liste d’autorisations/de blocs du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 60038a2b82ea452ed921d16042cb81d4f0e023a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100652"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Ajouter des blocs dans la liste verte/rouge du locataire

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Créer des entrées d’expéditeur de blocs dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, accédez à la section Stratégies **& règles de règles** sur les stratégies \> **de menaces** \> , section  \> **Listes d’autorisation/de blocage du locataire**.

2. Dans la page **Autoriser/Bloquer la liste** des locataires, vérifiez que l’onglet **Expéditeurs** est sélectionné, puis cliquez sur l’icône ![Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

3. Dans le menu volant **Bloquer les expéditeurs** qui s’affiche, configurez les paramètres suivants :
   - **Adresses de messagerie ou domaines de l’expéditeur** : entrez un expéditeur (adresse e-mail ou domaine) par ligne, jusqu’à un maximum de 20.
   - **N’expirez jamais** : effectuez l’une des étapes suivantes :
     - Vérifiez que le paramètre est désactivé (![désactiver.](../../media/scc-toggle-off.png)) et utilisez la case **Supprimer** pour spécifier la date d’expiration des entrées.

       ou

     - Déplacez le bouton bascule vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer/désactiver.](../../media/scc-toggle-on.png).
   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

> [!NOTE]
> Les e-mails de ces expéditeurs seront bloqués en tant que *courrier indésirable à haut niveau de confiance (SCL = 9).* 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Créer des entrées d’URL de bloc dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, accédez à la section Stratégies **& règles de règles** sur les stratégies \> **de menaces** \> , section  \> **Listes d’autorisation/de blocage du locataire**.

2. Dans la page **Autoriser/Bloquer la liste** des **locataires** , vérifiez que l’onglet URL est sélectionné, puis cliquez sur l’icône ![Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

3. Dans le menu volant **Des URL de bloc** qui s’affiche, configurez les paramètres suivants :
   - **Ajouter des URL avec des caractères génériques** : entrez une URL par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’URL, consultez la section Syntaxe de l’URL dans [Gérer la liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md).
   - **N’expirez jamais** : effectuez l’une des étapes suivantes :
     - Vérifiez que le paramètre est désactivé (![désactiver.](../../media/scc-toggle-off.png)) et utilisez la case **Supprimer** pour spécifier la date d’expiration des entrées.

       ou

     - Déplacez le bouton bascule vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer/désactiver.](../../media/scc-toggle-on.png).
   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

> [!NOTE]
> Les e-mails contenant ces URL seront bloqués en tant que *hameçonnage*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Créer des entrées de fichier de bloc dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, accédez à la section Stratégies **& règles de règles** sur les stratégies \> **de menaces** \> , section  \> **Listes d’autorisation/de blocage du locataire**.

2. Dans la page **Autoriser/Bloquer la liste des locataires** , sélectionnez l’onglet **Fichiers** , puis cliquez sur l’icône ![Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

3. Dans le menu volant **Bloquer les fichiers** qui s’affiche, configurez les paramètres suivants :
   - **Ajouter des hachages de fichier** : entrez une valeur de hachage SHA256 par ligne, jusqu’à un maximum de 20.
   - **N’expirez jamais** : effectuez l’une des étapes suivantes :
     - Vérifiez que le paramètre est désactivé (![désactiver.](../../media/scc-toggle-off.png)) et utilisez la case **Supprimer** pour spécifier la date d’expiration des entrées.

     ou

     - Déplacez le bouton bascule vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer/désactiver.](../../media/scc-toggle-on.png).
   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

> [!NOTE]
> Les e-mails contenant ces fichiers sont bloqués en tant que *programmes malveillants*. 

### <a name="create-spoofed-sender-block-entries"></a>Créer des entrées de bloc d’expéditeur usurpées

**Remarques** :

- Seule la _combinaison_ de l’utilisateur usurpé _et_ de l’infrastructure d’envoi définie dans la paire de domaines est spécifiquement autorisée ou bloquée pour l’usurpation d’identité.
- Lorsque vous configurez une entrée d’autorisation ou de blocage pour une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans l’insight d’intelligence de l’usurpation d’identité.
- Les entrées des expéditeurs usurpés n’expirent jamais.
- L’usurpation d’identité prend en charge l’autorisation et le blocage.

1. Dans le portail Microsoft 365 Defender, accédez à la section Stratégies **& règles de règles** sur les stratégies \> **de menaces** \> , section  \> **Listes d’autorisation/de blocage du locataire**.

2. Dans la page **Autoriser/Bloquer la liste des locataires** , sélectionnez l’onglet **Usurpation d’identité** , puis cliquez sur l’icône ![Bloquer.](../../media/m365-cc-sc-create-icon.png) **Ajouter**.

3. Dans le menu volant **Ajouter de nouvelles paires de domaines** qui s’affiche, configurez les paramètres suivants :
   - **Ajoutez de nouvelles paires de domaines avec des caractères génériques** : entrez une paire de domaines par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, consultez [Gérer la liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md).
   - **Type d’usurpation** d’identité : sélectionnez l’une des valeurs suivantes :
     - **Interne** : l’expéditeur usurpé se trouve dans un domaine qui appartient à votre organisation ( [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Externe** : l’expéditeur usurpé se trouve dans un domaine externe.
   - **Action** : Sélectionnez **Bloquer**.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.
> [!NOTE]
> Les e-mails de ces expéditeurs seront bloqués en tant que *hameçonnage*. 

## <a name="use-powershell"></a>Utiliser PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Ajouter des entrées d’expéditeur de bloc, de fichier ou d’URL à la liste d’autorisations/de blocs du locataire

Pour ajouter des entrées d’expéditeur de bloc, de fichier ou d’URL dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple montre comment ajouter une entrée d’expéditeur de bloc pour l’expéditeur spécifié qui expire à une date spécifique.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

Cet exemple ajoute une entrée de fichier de bloc pour les fichiers spécifiés qui n’expirent jamais.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Cet exemple montre comment ajouter une entrée d’URL de bloc pour contoso.com et tous les sous-domaines (par exemple, contoso.com, www.contoso.com et xyz.abc.contoso.com). Étant donné que nous n’avons pas utilisé les paramètres ExpirationDate ou NoExpiration, l’entrée expire après 30 jours.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Ajouter des entrées de bloc d’expéditeur usurpées 

Pour ajouter des entrées d’expéditeur usurpées dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
