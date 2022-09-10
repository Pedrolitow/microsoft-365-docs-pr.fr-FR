---
title: Autoriser ou bloquer des URL utilisant la liste Autoriser/Bloquer des clients
f1.keywords:
- NOCSH
ms.author: chrisda
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à autoriser ou bloquer des URL dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: ccfbd345edf69a1ebc0aef3bdfe5ab070659d819
ms.sourcegitcommit: 173f696dc8f81259d852775572a6938ec39f6115
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2022
ms.locfileid: "67644310"
---
# <a name="allow-or-block-urls-using-the-tenant-allowblock-list"></a>Autoriser ou bloquer des URL utilisant la liste Autoriser/Bloquer des clients

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article explique comment créer et gérer des entrées d’autorisation et de blocage d’URL disponibles dans la liste d’autorisations/de blocs du locataire. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

Vous gérez les entrées d’autorisation et de blocage des URL dans le portail Microsoft 365 Defender ou dans Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>. Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour obtenir la syntaxe d’entrée d’URL, consultez la [syntaxe d’URL de la section Autoriser/Bloquer la liste](#url-syntax-for-the-tenant-allowblock-list) des locataires plus loin dans cet article.

- Pour les URL, le nombre maximal d’entrées autorisées est de 500 et le nombre maximal d’entrées de bloc est de 500 (1 000 entrées d’URL au total).

- Vous pouvez entrer un maximum de 250 caractères dans une entrée d’URL.

- Une entrée doit être active dans un délai de 30 minutes, mais il peut prendre jusqu’à 24 heures pour que l’entrée soit active.

- Des autorisations doivent vous avoir été attribuées dans Exchange Online pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter et supprimer des valeurs de la liste d’autorisations/de blocs de locataire, vous devez être membre de l’un des groupes de rôles suivants :
    - **Groupe de rôles Gestion de l’organisation** ou **Administrateur de la sécurité** (**rôle Administrateur de la sécurité**)
    - Groupe **de rôles Opérateur de sécurité** (**Tenant AllowBlockList Manager**).
  - Pour accéder en lecture seule à la liste d’autorisations/de blocs du locataire, vous devez être membre de l’un des groupes de rôles suivants :
    - **Groupe de rôles Lecteur global**
    - **Groupe de rôles Lecteur de sécurité**
    - **Groupe de rôles de configuration Affichage uniquement**

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations *et* autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="create-block-entries-for-urls"></a>Créer des entrées de bloc pour les URL

Vous disposez des options suivantes pour créer des entrées de bloc pour les URL :

- [Page Soumissions dans le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-submissions-portal)
- Liste verte/bloquée du locataire dans [le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-tenant-allowblock-list) ou dans [PowerShell](#use-powershell-to-create-block-entries-for-urls-in-the-tenant-allowblock-list)

### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-submissions-portal"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées de bloc pour les URL dans le portail Soumissions

Lorsque vous utilisez le portail Soumissions pour <https://security.microsoft.com/reportsubmission> signaler les URL comme ayant **dû être bloquées (Faux négatif),** vous pouvez sélectionner **Bloquer cette URL** pour ajouter une entrée de bloc sous l’onglet **URL** dans la liste d’autorisation/de blocage du locataire.

Pour obtenir des instructions, consultez [Signaler des URL douteuses à Microsoft](admin-submission.md#report-questionable-urls-to-microsoft).

### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-tenant-allowblock-list"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées de bloc pour les URL dans la liste d’autorisations/de blocs du locataire

Vous pouvez créer des entrées de bloc pour les URL directement dans la liste d’autorisations/de blocs du locataire.

Email messages contenant ces URL bloquées sont bloqués en tant *qu’hameçonnage à haut niveau de confiance*.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Dans la page **Autoriser/Bloquer la liste** des **locataires** , sélectionnez l’onglet URL.

3. Sous l’onglet **URL** , cliquez sur ![l’icône Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

4. Dans le menu volant **Des URL de bloc** qui s’affiche, configurez les paramètres suivants :

   - **Ajouter des URL avec des caractères génériques** : entrez une URL par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’URL, consultez la [syntaxe d’URL de la section Autoriser/Bloquer la liste des locataires](#url-syntax-for-the-tenant-allowblock-list) plus loin dans cet article.

   - **Supprimer l’entrée de bloc après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
     - **N’expirez jamais**
     - **1 jour**
     - **7 jours**
     - **30 jours**
     - **Date spécifique** : la valeur maximale est de 90 jours à partir d’aujourd’hui.

   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

5. Lorsque vous avez terminé, cliquez sur **Ajouter**.

#### <a name="use-powershell-to-create-block-entries-for-urls-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour créer des entrées de bloc pour les URL dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate <Date> | -NoExpiration> [-Notes <String>]
```

Cet exemple montre comment ajouter une entrée de bloc pour le contoso.com d’URL et tous les sous-domaines (par exemple, contoso.com et xyz.abc.contoso.com). Étant donné que nous n’avons pas utilisé les paramètres ExpirationDate ou NoExpiration, l’entrée expire après 30 jours.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="use-the-microsoft-365-defender-portal-to-create-allow-entries-for-urls-in-the-submissions-portal"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les URL dans le portail Soumissions

Vous ne pouvez pas créer d’entrées d’autorisation d’URL directement dans la liste d’autorisation/de blocage du locataire. Au lieu de cela, vous utilisez le portail Soumissions pour <https://security.microsoft.com/reportsubmission> signaler l’URL sous la forme d’un faux positif, ce qui ajoute également une entrée d’autorisation sous l’onglet **URL** dans la liste d’autorisation/de blocage du locataire.

Pour obtenir des instructions, consultez [Signaler les BONNES URL à Microsoft](admin-submission.md#report-good-urls-to-microsoft).

> [!IMPORTANT]
> Étant donné que Microsoft gère les entrées d’autorisation pour vous, les entrées autorisées d’URL inutiles seront supprimées. Ce comportement protège votre organisation et permet d’éviter les entrées d’autorisation mal configurées. Si vous n’êtes pas d’accord avec le verdict, vous devrez peut-être ouvrir un dossier de support pour déterminer pourquoi une URL est toujours considérée comme incorrecte.

## <a name="use-the-microsoft-365-defender-portal-to-view-allow-or-block-entries-for-urls-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour afficher les entrées d’autorisation ou de blocage pour les URL dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Ou, pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **URL** . Les colonnes suivantes sont disponibles :

   - **Valeur** : URL.
   - **Action** : valeur **Allow** ou **Block**.
   - **Modifié par**
   - **Dernière mise à jour**
   - **Supprimer le** : date d’expiration.
   - **Remarques**

   Cliquez sur un en-tête de colonne pour trier dans l’ordre croissant ou décroissant.

   Cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** les résultats par **aucune** ou **action**.

   Cliquez sur l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Recherchez**, entrez tout ou partie d’une valeur, puis appuyez sur Entrée pour rechercher une valeur spécifique. Lorsque vous avez terminé, cliquez sur ![l’icône Effacer la recherche.](../../media/m365-cc-sc-close-icon.png) pour effacer la recherche.

   Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer les résultats. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :

   - **Action** : **Autoriser** et **bloquer**.
   - **N’expirez jamais** : ![basculez dessus.](../../media/scc-toggle-on.png) ou ![désactiver.](../../media/scc-toggle-off.png)
   - **Dernière mise à jour** : Sélectionner à **partir** et **à** des dates.
   - **Remove on**: Select **From** and **To** dates.

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur ![Effacer les filtres **dans**](../../media/m365-cc-sc-clear-filters-icon.png) le menu volant **Filtrer**.

### <a name="use-powershell-to-view-allow-or-block-entries-for-urls-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour afficher les entrées d’autorisation ou de blocage pour les URL dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType Url [-Allow] [-Block] [-Entry <URLValue>] [<-ExpirationDate <Date> | -NoExpiration>]
```

Cet exemple retourne toutes les URL autorisées et bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url
```

Cet exemple filtre les résultats par URL bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="use-the-microsoft-365-defender-portal-to-modify-allow-or-block-entries-for-urls-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour modifier les entrées d’autorisation ou de blocage des URL dans la liste d’autorisations/de blocs du locataire

Lorsque vous modifiez des entrées d’autorisation ou de blocage pour les URL dans la liste d’autorisations/de blocs de locataire, vous pouvez uniquement modifier la date d’expiration et les notes.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **URL**

3. Sous l’onglet **URL** , cochez la case de l’entrée à modifier, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Bouton Modifier** qui s’affiche.

4. Les valeurs suivantes sont disponibles dans le menu volant **Modifier l’URL** qui s’affiche :

   - **Supprimez l’entrée d’autorisation après** ou **supprimez l’entrée de bloc après** :
     - Vous pouvez étendre les entrées d’autorisation pendant un maximum de 30 jours après la date de création.
     - Vous pouvez étendre les entrées de bloc pendant un maximum de 90 jours après la date de création ou les définir sur **Jamais expirer**.

   - **Remarque facultative**

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

> [!NOTE]
> Pour autoriser les entrées uniquement, si vous sélectionnez l’entrée en cliquant n’importe où dans la ligne autre que la case à cocher, vous pouvez sélectionner ![l’icône Afficher la soumission.](../../media/m365-cc-sc-view-submission-icon.png) **Affichez la soumission** dans le menu volant des détails qui semble accéder à la page **Soumissions** à l’adresse <https://security.microsoft.com/reportsubmission>.

### <a name="use-powershell-to-modify-allow-or-block-entries-for-urls-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour modifier des entrées d’autorisation ou de blocage pour les URL dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType Url <-Ids <Identity value> | -Entries <Value value>> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Cet exemple montre comment modifier la date d’expiration de l’entrée de bloc pour l’URL spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Entries "~contoso.com" -ExpirationDate "9/1/2022"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="use-the-microsoft-365-defender-portal-to-remove-allow-or-block-entries-for-urls-from-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour supprimer les entrées d’autorisation ou de blocage des URL de la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **URL** .

3. Sous l’onglet **URL** , effectuez l’une des étapes suivantes :

   - Cochez la case de l’entrée à supprimer, puis cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche.
   - Sélectionnez l’entrée à supprimer en cliquant n’importe où dans la ligne autre que la case à cocher. Dans le menu volant des détails qui s’affiche, cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer**.

> [!NOTE]
> Vous pouvez sélectionner plusieurs entrées en cochant chaque case ou toutes les entrées en cochant la case en regard de l’en-tête **de colonne Valeur** .

### <a name="use-powershell-to-remove-allow-or-block-entries-for-urls-from-the-tenant-allowblock-list"></a>Utiliser PowerShell pour supprimer des entrées d’autorisation ou de blocage pour les URL de la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType Url <-Ids <Identity value> | -Entries <Value value>>
```

Cet exemple montre comment supprimer l’entrée de bloc de l’URL spécifiée de la liste d’autorisations/de blocs du locataire.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Entries "~cohovineyard.com
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Syntaxe d’URL pour la liste d’autorisations/de blocs de locataire

- Les adresses IPv4 et IPv6 sont autorisées, mais pas les ports TCP/UDP.

- Les extensions de nom de fichier ne sont pas autorisées (par exemple, test.pdf).

- Unicode n’est pas pris en charge, mais Punycode l’est.

- Les noms d’hôte sont autorisés si toutes les instructions suivantes sont vraies :
  - Le nom d’hôte contient un point.
  - Il y a au moins un caractère à gauche de la période.
  - Il y a au moins deux caractères à droite de la période.

  Par exemple, `t.co` est autorisé ; `.com` ou `contoso.` ne sont pas autorisés.

- Les sous-chemins ne sont pas implicites pour les autorisations.

  Par exemple, `contoso.com` n’inclut `contoso.com/a`pas .

- Les caractères génériques (*) sont autorisés dans les scénarios suivants :

  - Un caractère générique gauche doit être suivi d’un point pour spécifier un sous-domaine. (applicable uniquement aux blocs)

    Par exemple, `*.contoso.com` est autorisé ; `*contoso.com` il n’est pas autorisé.

  - Un caractère générique droit doit suivre une barre oblique (/) pour spécifier un chemin d’accès.

    Par exemple, `contoso.com/*` est autorisé ; `contoso.com*` ou `contoso.com/ab*` ne sont pas autorisés.

  - `*.com*` n’est pas valide (il ne s’agit pas d’un domaine pouvant être résolu et le caractère générique approprié ne suit pas une barre oblique).

  - Les caractères génériques ne sont pas autorisés dans les adresses IP.

- Le caractère tilde (~) est disponible dans les scénarios suivants :

  - Un tilde gauche implique un domaine et tous les sous-domaines.

    Par exemple `~contoso.com` , inclut `contoso.com` et `*.contoso.com`.

- Un nom d’utilisateur ou un mot de passe n’est pas pris en charge ou requis.

- Les guillemets (' ou « ) ne sont pas valides.

- Une URL doit inclure toutes les redirections si possible.

### <a name="url-entry-scenarios"></a>Scénarios d’entrée d’URL

Les entrées d’URL valides et leurs résultats sont décrits dans les sections suivantes.

#### <a name="scenario-no-wildcards"></a>Scénario : Aucun caractère générique

**Entrée** : `contoso.com`

- **Autoriser la correspondance** : contoso.com

- **Autoriser les correspondances non mises en correspondance** :
  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - contoso.com
  - contoso.com/q=a@contoso.com

- **Correspondance de bloc** :
  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - contoso.com
  - contoso.com/q=a@contoso.com

- **Bloc non mis en correspondance** : abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scénario : Caractère générique gauche (sous-domaine)

> [!NOTE]
> Ce scénario s’applique uniquement aux blocs.

**Entrée** : `*.contoso.com`

- **Correspondance de bloc** :
  - xyz.abc.contoso.com

- **Bloc non mis en correspondance** :
  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scénario : Caractère générique droit en haut du chemin d’accès

**Entrée** : `contoso.com/a/*`

- **Autoriser la correspondance** et **bloquer la correspondance** :
  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :
  - contoso.com
  - contoso.com/a
  - contoso.com
  - contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scénario : Tilde gauche

**Entrée** : `~contoso.com`

- **Autoriser la correspondance** et **bloquer la correspondance** :
  - contoso.com
  - contoso.com
  - xyz.abc.contoso.com

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :
  - 123contoso.com
  - contoso.com/abc
  - contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scénario : Suffixe générique droit

**Entrée** : `contoso.com/*`

- **Autoriser la correspondance** et **bloquer la correspondance** :
  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Autoriser l’absence de correspondance** et **Bloquer non mis en correspondance** : contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scénario : Sous-domaine de caractères génériques gauche et suffixe générique droit

> [!NOTE]
> Ce scénario s’applique uniquement aux blocs.

**Entrée** : `*.contoso.com/*`

- **Correspondance de bloc** :
  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - contoso.com/a
  - contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Bloc non mis en correspondance** : contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scénario : Tilde gauche et droit

**Entrée** : `~contoso.com~`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - contoso.com
  - contoso.com/a
  - contoso.com
  - contoso.com/b
  - xyz.abc.contoso.com

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scénario : adresse IP

**Entrée** : `1.2.3.4`

- **Autoriser la correspondance** et **bloquer la correspondance** : 1.2.3.4

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Adresse IP avec caractère générique droit

**Entrée** : `1.2.3.4/*`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Exemples d’entrées non valides

Les entrées suivantes ne sont pas valides :

- **Valeurs de domaine manquantes ou non valides** :

  - Contoso
  - \*.contoso.\*
  - \*.com
  - \*.pdf

- **Caractère générique sur le texte ou sans caractères d’espacement** :

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **Adresses IP avec ports** :

  - contoso.com:443
  - abc.contoso.com:25

- **Caractères génériques non descriptifs** :

  - \*
  - \*.\*

- **Caractères génériques intermédiaires** :

  - conto\*so.com
  - conto~so.com

- **Caractères génériques doubles**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="related-articles"></a>Articles connexes

- [Utilisez le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL, des e-mails légitimes bloqués et des pièces jointes à Microsoft](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Autoriser ou bloquer des fichiers dans la liste d’autorisations/de blocs du locataire](allow-block-files.md)
- [Autoriser ou bloquer des e-mails dans la liste d’autorisations/blocages du locataire](allow-block-email-spoof.md)
