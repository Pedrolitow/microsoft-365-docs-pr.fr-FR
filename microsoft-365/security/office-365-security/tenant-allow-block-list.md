---
title: Gérer vos autoriser et bloquer dans la liste d’autoriser/bloquer des locataires
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à configurer des autoriser et des blocs dans la liste d’adresses client autoriser/bloquer dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2f97308bfc3600e4e85f5ac92d951b12d9a50f24
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50928531"
---
# <a name="manage-the-tenant-allowblock-list"></a>Gérer la liste Autoriser/Bloquer du client

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

> [!NOTE]
>
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et ne sont pas disponibles dans toutes les organisations.
>
> Vous ne pouvez pas **configurer les éléments** autorisés dans la liste des locataires autorisés/bloqués pour le moment.

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou dans des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, vous pouvez ne pas être d’accord avec le verdict de filtrage EOP. Par exemple, un bon message peut être marqué comme mauvais (faux positif) ou un message erroné peut être autorisé (faux négatif).

La liste d’attente des clients dans le Centre de sécurité & conformité vous permet de remplacer manuellement les verdicts de filtrage Microsoft 365. La liste d’adresses client autoriser/bloquer est utilisée pendant le flux de messagerie et au moment des clics de l’utilisateur. Vous pouvez spécifier des URL ou des fichiers à toujours bloquer.

Cet article explique comment configurer des entrées dans la liste d’adresses client autoriser/bloquer dans le Centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour aller directement à la page **Autoriser/Bloquer la liste des** locataires, utilisez <https://protection.office.com/tenantAllowBlockList> .

- Vous spécifiez des fichiers à l’aide de la valeur de hachage SHA256 du fichier. Pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes :

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Un exemple de valeur est `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a` . Les valeurs de hachage perceptif (pHash) ne sont pas pris en charge.

- Les valeurs d’URL disponibles sont décrites dans la [syntaxe d’URL](#url-syntax-for-the-tenant-allowblock-list) de la section Tenant Allow/Block List plus loin dans cet article.

- La liste d’adresses client autorise un maximum de 500 entrées pour les URL et 500 entrées pour les hâchés de fichiers.

- Le nombre maximal de caractères pour chaque entrée est :
  - Hèmes de fichier = 64
  - URL = 250

- Une entrée doit être active dans les 30 minutes.

- Par défaut, les entrées de la liste d’inscriptions au client sont expirées au bout de 30 jours. Vous pouvez spécifier une date ou la définir pour qu’elles n’expirent jamais.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter et supprimer des valeurs de la liste d’attente des locataires, vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité. 
  - Pour un accès en lecture seule à la liste des locataires  autorisé/bloqué, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité. 

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > 
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="use-the-security--compliance-center-to-create-url-entries-in-the-tenant-allowblock-list"></a>Utiliser le Centre de sécurité & conformité pour créer des entrées d’URL dans la liste d’adresses client autoriser/bloquer

Pour plus d’informations sur la syntaxe des entrées d’URL, voir la [syntaxe d’URL](#url-syntax-for-the-tenant-allowblock-list) pour la section Tenant Allow/Block List plus loin dans cet article.

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.

2. Dans la page **Liste d’adresses** client autoriser/bloquer, vérifiez que l’onglet **URL** est sélectionné, puis cliquez sur **Bloquer**

3. Dans le **volant Bloquer les URL** qui s’affiche, configurez les paramètres suivants :

   - **Ajouter des URL à bloquer :** entrez une URL par ligne, jusqu’à un maximum de 20.

   - **N’expirez jamais**: faites l’une des étapes suivantes :

     - Vérifiez que le paramètre est désactivé (basculement désactivé) et utilisez la case Expires on pour spécifier la ![ ](../../media/scc-toggle-off.png) date d’expiration des entrées. 

       ou

     - Déplacez le basculement vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer](../../media/scc-toggle-on.png).

   - **Remarque facultative**: entrez un texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="use-the-security--compliance-center-to-create-file-entries-in-the-tenant-allowblock-list"></a>Utiliser le Centre de sécurité & conformité pour créer des entrées de fichier dans la liste d’attente des locataires

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.

2. Dans la page **Liste des clients autoriser/bloquer,** sélectionnez **l’onglet Fichiers,** puis cliquez sur **Bloquer**.

3. Dans la **zone Ajouter des fichiers pour bloquer** le flyout qui s’affiche, configurez les paramètres suivants :

   - **Ajouter des hachages de fichier**: entrez une valeur de hachage SHA256 par ligne, jusqu’à un maximum de 20.

   - **N’expirez jamais**: faites l’une des étapes suivantes :

     - Vérifiez que le paramètre est désactivé (basculement désactivé) et utilisez la case Expires on pour spécifier la ![ ](../../media/scc-toggle-off.png) date d’expiration des entrées. 

     ou

     - Déplacez le basculement vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer](../../media/scc-toggle-on.png).

   - **Remarque facultative**: entrez un texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="use-the-security--compliance-center-to-view-entries-in-the-tenant-allowblock-list"></a>Utiliser le Centre de sécurité & conformité pour afficher les entrées dans la liste d’attente des locataires

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.

2. Sélectionnez **l’onglet URL** ou **Fichiers.**

Cliquez sur les en-tête de colonne suivants pour trier par ordre croissant ou décroit :

- **Valeur**: URL ou hachage du fichier.
- **Date de la dernière mise à jour**
- **Date d’expiration**
- **Remarque**

Cliquez **sur** Rechercher, entrez une partie ou l’ensemble d’une valeur, puis appuyez sur Entrée pour trouver une valeur spécifique. Lorsque vous avez terminé, cliquez sur **Effacer l’icône** ![ effacer la ](../../media/b6512677-5e7b-42b0-a8a3-3be1d7fa23ee.gif) recherche.

Cliquez sur **Filtrer.** Dans le **volant de** filtre qui s’affiche, configurez l’un des paramètres suivants :

- **N’expirez** jamais : sélectionnez Off: ![ Toggle off ](../../media/scc-toggle-off.png) or on: ![ Toggle on ](../../media/scc-toggle-on.png) .

- **Dernière mise à jour**: sélectionnez une date de début (**De**), une date de fin (**À**) ou les deux.

- **Date d’expiration**: sélectionnez une date de début (**De**), une date de fin (**À**) ou les deux.

Lorsque vous avez terminé, cliquez sur **Appliquer.**

Pour effacer les filtres existants,  cliquez sur **Filtrer** et dans le volant de filtre qui s’affiche, cliquez **sur Effacer les filtres.**

## <a name="use-the-security--compliance-center-to-modify-block-entries-in-the-tenant-allowblock-list"></a>Utiliser le Centre de sécurité & conformité pour modifier les entrées de blocage dans la liste d’attente des locataires

Vous ne pouvez pas modifier l’URL ou les valeurs de fichier bloquées existantes dans une entrée. Pour modifier ces valeurs, vous devez supprimer et recréer l’entrée.

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.

2. Sélectionnez **l’onglet URL** ou **Fichiers.**

3. Sélectionnez l’entrée de blocage à modifier, puis cliquez **sur** Modifier ![ l’icône ](../../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) Modifier.

4. Dans le volant qui s’affiche, configurez les paramètres suivants :

   - **N’expirez jamais**: faites l’une des étapes suivantes :

     - Vérifiez que le paramètre est désactivé (basculement désactivé) et utilisez la case Expires on pour spécifier la ![ ](../../media/scc-toggle-off.png) date d’expiration de l’entrée. 

       ou

     - Déplacez le basculement vers la droite pour configurer l’entrée de manière à ce qu’elle n’expire jamais : ![Activer](../../media/scc-toggle-on.png).

   - **Remarque facultative**: entrez un texte descriptif pour l’entrée.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-remove-block-entries-from-the-tenant-allowblock-list"></a>Utiliser le Centre de sécurité & conformité pour supprimer des entrées de blocage de la liste d’attente des locataires

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.

2. Sélectionnez **l’onglet URL** ou **Fichiers.**

3. Sélectionnez l’entrée de blocage à supprimer, puis cliquez **sur** Supprimer ![ l’icône ](../../media/87565fbb-5147-4f22-9ed7-1c18ce664392.png) Supprimer.

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer.**

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-the-tenant-allowblock-list"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer la liste d’adresses client autoriser/bloquer

### <a name="use-powershell-to-add-block-entries-to-the-tenant-allowblock-list"></a>Utiliser PowerShell pour ajouter des entrées de bloc à la liste d’accès au client

Pour ajouter des entrées de bloc dans la liste d’accès au client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <Url | FileHash> -Block -Entries <String[]> [-ExpirationDate <DateTime>] [-NoExpiration] [-Notes <String>]
```

Cet exemple ajoute une entrée d’URL de bloc pour contoso.com et tous les sous-contoso.com (par exemple, contoso.com, www.contoso.com et xyz.abc.contoso.com). Étant donné que nous n’avons pas utilisé les paramètres ExpirationDate ou NoExpiration, l’entrée expire au bout de 30 jours.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Cet exemple ajoute une entrée de bloc de fichiers pour les fichiers spécifiés qui n’expire jamais.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-entries-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour afficher les entrées dans la liste d’attente des locataires

Pour afficher les entrées de la liste d’inscriptions client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <Url | FileHash> [-Entry <URLValue | FileHashValue>] [-Block] [-ExpirationDate <DateTime>] [-NoExpiration]
```

Cet exemple renvoie toutes les URL bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Cet exemple renvoie des informations pour la valeur de hachage de fichier spécifiée.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-block-entries-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour modifier les entrées de bloc dans la liste d’accès au client

Vous ne pouvez pas modifier l’URL ou les valeurs de fichier existantes dans une entrée de bloc. Pour modifier ces valeurs, vous devez supprimer et recréer l’entrée.

Pour modifier les entrées de bloc dans la liste d’accès au client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <Url | FileHash> -Ids <"Id1","Id2",..."IdN"> [-Block] [-ExpirationDate <DateTime>] [-NoExpiration] [-Notes <String>]
```

Cet exemple modifie la date d’expiration de l’entrée de bloc spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate (Get-Date "5/30/2020 9:30 AM").ToUniversalTime()
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-block-entries-from-the-tenant-allowblock-list"></a>Utiliser PowerShell pour supprimer des entrées de blocage de la liste d’accès au client

Pour supprimer des entrées de blocage de la liste d’accès au client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <Url | FileHash> -Ids <"Id1","Id2",..."IdN">
```

Cet exemple supprime l’entrée d’URL de bloc spécifiée de la liste d’adresses client autoriser/bloquer.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Syntaxe d’URL pour la liste d’adresses client autoriser/bloquer

- Les adresses IP4v et IPv6 sont autorisées, mais pas les ports TCP/UDP.

- Les extensions de nom de fichier ne sont pas autorisées (par exemple, test.pdf).

- Unicode n’est pas pris en charge, mais c’est le cas de Punycode.

- Les noms d’hôte sont autorisés si toutes les instructions suivantes sont vraies :
  - Le nom d’hôte contient un point.
  - Il y a au moins un caractère à gauche du point.
  - Il y a au moins deux caractères à droite du point.

  Par exemple, `t.co` est autorisé ou `.com` `contoso.` non.

- Les sous-chemins ne sont pas implicites.

  Par exemple, `contoso.com` n’inclut pas `contoso.com/a` .

- Les caractères génériques (*) sont autorisés dans les scénarios suivants :

  - Un caractère générique gauche doit être suivi d’un point pour spécifier un sous-domaine.

    Par exemple, `*.contoso.com` est autorisé ; `*contoso.com` n’est pas autorisé.

  - Un caractère générique droit doit suivre une barre oblique (/) pour spécifier un chemin d’accès.

    Par exemple, `contoso.com/*` est autorisé ou `contoso.com*` `contoso.com/ab*` non.

  - Tous les sous-chemins ne sont pas impliqués par un caractère générique de droite.

    Par exemple, `contoso.com/*` n’inclut pas `contoso.com/a` .

  - `*.com*` n’est pas valide (domaine non résolvable et le caractère générique droit ne suit pas une barre oblique).

  - Les caractères génériques ne sont pas autorisés dans les adresses IP.

- Le caractère tilde (~) est disponible dans les scénarios suivants :

  - Un tilde gauche implique un domaine et tous les sous-domaines.

    Par `~contoso.com` exemple, `contoso.com` inclut et `*.contoso.com` .

- Les entrées d’URL qui contiennent des protocoles (par exemple, , ou ) échouent, car les entrées `http://` `https://` `ftp://` d’URL s’appliquent à tous les protocoles.

- Un nom d’utilisateur ou un mot de passe ne sont pas pris en charge ou requis.

- Les guillemets (' ou « ) sont des caractères non valides.

- Une URL doit inclure toutes les redirections lorsque cela est possible.

### <a name="url-entry-scenarios"></a>Scénarios d’entrée d’URL

Les entrées d’URL valides et leurs résultats sont décrits dans les sections suivantes.

#### <a name="scenario-no-wildcards"></a>Scénario : aucun caractère générique

**Entrée**: `contoso.com`

- **Autoriser la correspondance**: contoso.com

- **Autoriser non la correspondance**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Bloquer la correspondance**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Bloc non correspond :** abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scénario : caractère générique gauche (sous-domaine)

**Entrée**: `*.contoso.com`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **Autoriser non la correspondance et** Bloquer non correspond **:**

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scénario : caractère générique droit en haut du chemin d’accès

**Entrée**: `contoso.com/a/*`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Autoriser non la correspondance et** Bloquer non correspond **:**

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scénario : tilde gauche

**Entrée**: `~contoso.com`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Autoriser non la correspondance et** Bloquer non correspond **:**

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scénario : suffixe générique droit

**Entrée**: `contoso.com/*`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Autoriser non la correspondance et** Bloquer non correspond **:** contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scénario : sous-domaine générique gauche et suffixe générique droit

**Entrée**: `*.contoso.com/*`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Autoriser non la correspondance et** Bloquer non correspond **:** contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scénario : tilde gauche et droite

**Entrée**: `~contoso.com~`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Autoriser non la correspondance et** Bloquer non correspond **:**

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scénario : adresse IP

**Entrée**: `1.2.3.4`

- **Autoriser la correspondance** **et bloquer la correspondance**: 1.2.3.4

- **Autoriser non la correspondance et** Bloquer non correspond **:**

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Adresse IP avec caractère générique droit

**Entrée**: `1.2.3.4/*`

- **Autoriser la correspondance** et **bloquer la correspondance**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Exemples d’entrées non valides

Les entrées suivantes ne sont pas valides :

- **Valeurs de domaine manquantes ou non valides**:

  - contoso
  - \*.contoso.\*
  - \*.com
  - \*.pdf

- **Caractère générique sur du texte ou sans espacement :**

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **Adresses IP avec ports**:

  - contoso.com:443
  - abc.contoso.com:25

- **Caractères génériques non descriptifs**:

  - \*
  - \*.\*

- **Caractères génériques intermédiaires**:

  - conto \* so.com
  - conto~so.com

- **Caractères génériques doubles**

  - contoso.com/\*\*
  - contoso.com/\*/\*