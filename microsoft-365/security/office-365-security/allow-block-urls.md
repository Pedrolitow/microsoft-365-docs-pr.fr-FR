---
title: Autoriser ou bloquer des URL utilisant la liste Autoriser/Bloquer des clients
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
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à autoriser ou bloquer des URL dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 69d9b4725e0a2c57dac8bb711655b9e0ff02e3e5
ms.sourcegitcommit: 7df8adc9e67ab65e413d7ea7bb0dcb9fd2da1a11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185811"
---
# <a name="allow-or-block-urls-using-the-tenant-allowblock-list"></a>Autoriser ou bloquer des URL utilisant la liste Autoriser/Bloquer des clients

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous pouvez utiliser le portail Microsoft 365 Defender ou PowerShell pour autoriser ou bloquer des URL dans la liste d’autorisation/de blocage du locataire.

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
  - contoso.com
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

## <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Créer des entrées d’URL de bloc dans la liste d’autorisations/de blocs du locataire

### <a name="use-microsoft-365-defender"></a>Utiliser Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

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
> Les e-mails contenant ces URL seront bloqués en tant que _hameçonnage_.

### <a name="use-powershell"></a>Utiliser PowerShell

Pour ajouter des entrées d’URL de bloc dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple montre comment ajouter une entrée d’URL de bloc pour contoso.com et tous les sous-domaines (par exemple, contoso.com et xyz.abc.contoso.com). Étant donné que nous n’avons pas utilisé les paramètres ExpirationDate ou NoExpiration, l’entrée expire après 30 jours.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-url-entries"></a>Créer des entrées d’URL d’autorisation

### <a name="use-microsoft-365-defender"></a>Utiliser Microsoft 365 Defender

Autorisez les URL sur la page **Soumissions** dans Microsoft 365 Defender.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Actions & soumissions** \> **soumissions**. Ou, pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , sélectionnez l’onglet **URL** , puis cliquez sur ![Envoyer à Microsoft pour l’icône d’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

3. Utilisez le menu volant **Envoyer à Microsoft pour passer en revue** l’envoi d’un message en ajoutant l’URL.

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft**, sélectionnez **Ne doit pas avoir été bloquée (faux positif).**

5. Activez les **URL Allow comme celle-ci** .

6. Dans la liste déroulante **Supprimer après** , spécifiez la durée pendant laquelle vous souhaitez que l’option d’autorisation fonctionne.

7. Ajoutez la raison pour laquelle vous ajoutez autoriser à l’aide de la **note facultative**. 

8. Lorsque vous avez terminé, cliquez sur le bouton **Envoyer** .

    :::image type="content" source="../../media/submit-url-for-analysis.png" alt-text="Envoyer l’URL à des fins d’analyse" lightbox="../../media/submit-url-for-analysis.png":::

> [!NOTE]
>
> - Lorsque l’URL est à nouveau rencontrée, l’URL n’est pas envoyée pour des vérifications de détonation ou de réputation, et tous les autres filtres basés sur l’URL sont ignorés.
> - Par conséquent, pour un e-mail (contenant cette URL), pendant le flux de courrier, si le reste des filtres trouve l’e-mail propre, l’e-mail est remis.

## <a name="view-url-entries"></a>Afficher les entrées d’URL

Pour afficher les entrées d’URL de bloc dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Cet exemple retourne toutes les URL bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-url-entries"></a>Modifier les entrées d’URL 

Pour modifier les entrées d’URL d’autorisation ou de blocage dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <URL> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Cet exemple montre comment modifier la date d’expiration de l’entrée d’URL de bloc spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-url-entries"></a>Supprimer les entrées d’URL 

Pour supprimer les entrées d’URL d’autorisation ou de blocage de la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <URL> -Ids <"Id1","Id2",..."IdN">
```
Cet exemple montre comment supprimer l’entrée d’URL de bloc spécifiée de la liste d’autorisations/de blocs du locataire.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>Articles connexes

- [Envois par l’administrateur](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Autoriser ou bloquer des fichiers dans la liste d’autorisations/de blocs du locataire](allow-block-files.md)
- [Autoriser ou bloquer des e-mails dans la liste d’autorisations/blocages du locataire](allow-block-email-spoof.md)
