---
title: Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à gérer les autorisations et les blocs dans la liste d’autorisations/blocs du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a067672a013f3e0ed7b9009604f8a4fe000ea47f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172813"
---
# <a name="manage-the-tenant-allowblock-list"></a>Gérer la liste Autoriser/Bloquer du client

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans Exchange Online boîtes aux lettres, vous pouvez être en désaccord avec le verdict de filtrage EOP. Par exemple, un bon message peut être marqué comme mauvais (faux positif) ou un message incorrect peut être autorisé (un faux négatif).

La liste d’autorisation/de blocage des locataires dans le portail Microsoft 365 Defender vous permet de remplacer manuellement les verdicts de filtrage Microsoft 365. La liste d’autorisation/de blocage du locataire est utilisée pendant le flux de messagerie pour les messages entrants (ne s’applique pas aux messages intra-organisation) et au moment où l’utilisateur clique. Vous pouvez spécifier les types de remplacements suivants :

- URL à bloquer.
- Fichiers à bloquer.
- E-mails ou domaines de l’expéditeur à bloquer.
- Expéditeurs usurpés à autoriser ou bloquer. Si vous remplacez le verdict d’autorisation ou de blocage dans [l’insight d’intelligence](learn-about-spoof-intelligence.md) de l’usurpation d’identité, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui n’apparaît que sous l’onglet **Usurpation** d’identité dans la liste d’autorisation/de blocage du locataire. Vous pouvez également créer manuellement des entrées d’autorisation ou de blocage pour les expéditeurs usurpés ici avant qu’elles ne soient détectées par l’intelligence de l’usurpation d’identité.
- URL à autoriser.
- Fichiers à autoriser.
- E-mails ou domaines de l’expéditeur à autoriser.

Cet article explique comment configurer des entrées dans la liste verte/bloquée du locataire dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans Exchange Online boîtes aux lettres).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

- Vous spécifiez des fichiers à l’aide de la valeur de hachage SHA256 du fichier. Pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes :

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Un exemple de valeur est `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Les valeurs de hachage perceptuel (pHash) ne sont pas prises en charge.

- Les valeurs d’URL disponibles sont décrites dans la [syntaxe d’URL de la section Tenant Allow/Block List](#url-syntax-for-the-tenant-allowblock-list) plus loin dans cet article.

- La liste d’autorisation/de blocage du locataire autorise un maximum de 500 entrées pour les expéditeurs, 500 entrées pour les URL, 500 entrées pour les hachages de fichier et 1 024 entrées pour l’usurpation d’identité (expéditeurs usurpés).

- Le nombre maximal de caractères pour chaque entrée est le suivant :
  - Hachages de fichier = 64
  - URL = 250

- Une entrée doit être active dans les 30 minutes.

- Par défaut, les entrées de la liste d’autorisations/de blocs du locataire expirent après 30 jours. Vous pouvez spécifier une date ou les définir pour qu’elles n’expirent jamais.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans Exchange Online pour que vous puissiez effectuer les procédures décrites dans cet article :
  - **Expéditeurs, URL et fichiers** :
    - Pour ajouter et supprimer des valeurs de la liste d’autorisations/de blocs du locataire, vous devez être membre de
      - **Groupe de rôles Gestion de l’organisation** ou **Administrateur de la sécurité** (**rôle Administrateur de la sécurité**)
      - Groupe **de rôles Opérateur de sécurité** (**Tenant AllowBlockList Manager**).
    - Pour accéder en lecture seule à la liste d’autorisations/de blocs de locataire, vous devez être membre de
      - **Groupe de rôles Lecteur global**
      - **Groupe de rôles Lecteur de sécurité**
  - **Usurpation d’identité** : une des combinaisons suivantes :
    - **Gestion de l'organisation**
    - **Administrateur de sécurité** <u>et</u> **configuration en mode seul** ou gestion de l’organisation **en mode affichage uniquement**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises *et* les autorisations pour les autres fonctionnalités de [Microsoft 365](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="configure-the-tenant-allowblock-list"></a>Configurer la liste d’autorisations/blocages du locataire

### <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender

Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

Pour ajouter tous les blocs, consultez [Ajouter des blocs dans la liste d’autorisations/blocs du locataire](manage-tenant-blocks.md).

Pour ajouter toutes les autorisations, consultez [Ajouter des autorisations dans la liste d’autorisations/de blocs du locataire](manage-tenant-allows.md).

Pour modifier et supprimer tous les blocs et toutes les [autorisations, consultez Modifier et supprimer des entrées dans la liste d’autorisations/de blocs du locataire](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Utiliser Exchange Online PowerShell ou PowerShell EOP autonome

Pour gérer tous les blocs et autorisations, consultez [Ajouter des blocs dans la liste d’autorisations/blocs du locataire](manage-tenant-blocks.md), [Ajouter des autorisations dans la liste d’autorisations/blocs de locataire](manage-tenant-allows.md), et [Modifier et supprimer des entrées dans la liste d’autorisation/de blocs du locataire](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Afficher les entrées dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet souhaité. Les colonnes disponibles dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs** :
     - **Valeur** : domaine ou adresse e-mail de l’expéditeur.
     - **Action** : valeur **Allow** ou **Block**.
     - **Modifié par**
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Notes**
   - **URLs**:
     - **Valeur** : URL.
     - **Action** : valeur **Allow** ou **Block**.
     - **Modifié par**
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Notes**
   - **Files**
     - **Valeur** : hachage du fichier.
     - **Action** : valeur **Allow** ou **Block**.
     - **Modifié par**
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Notes**
   - **Spoofing**
     - **Utilisateur usurpé**
     - **Envoi d’une infrastructure**
     - **Type d’usurpation** d’identité : valeur **interne** ou **externe**.
     - **Action** : valeur **Bloquer** ou **Autoriser**.

   Vous pouvez cliquer sur un en-tête de colonne pour trier dans l’ordre croissant ou décroissant.

   Vous pouvez cliquer sur **Groupe** pour regrouper les résultats. Les valeurs disponibles dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs** : vous pouvez regrouper les résultats par **action**.
   - **URL** : vous pouvez regrouper les résultats par **action**.
   - **Fichiers** : vous pouvez regrouper les résultats par **action**.
   - **Usurpation d’identité** : vous pouvez regrouper les résultats par **type Action** ou **Usurpation d’identité**.

   Cliquez sur **Rechercher**, entrez tout ou partie d’une valeur, puis appuyez sur Entrée pour rechercher une valeur spécifique. Lorsque vous avez terminé, cliquez sur ![l’icône Effacer la recherche.](../../media/m365-cc-sc-close-icon.png) **Effacer la recherche**.

   Cliquez sur **Filtrer** pour filtrer les résultats. Les valeurs disponibles dans le menu volant **Filtre** qui s’affiche dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs**
     - **Action**
     - **N’expirez jamais**
     - **Dernière date de mise à jour**
     - **Supprimer le**
   - **Url**
     - **Action**
     - **N’expirez jamais**
     - **Dernière date de mise à jour**
     - **Supprimer le**
   - **Files**
     - **Action**
     - **N’expirez jamais**
     - **Dernière mise à jour**
     - **Supprimer le**
   - **Spoofing**
     - **Action**
     - **Type d’usurpation d’identité**

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur **Filtrer**, puis dans le menu volant **Filtre** qui s’affiche, cliquez sur **Effacer les filtres**.

3. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Afficher les entrées de l’expéditeur, du fichier ou de l’URL dans la liste d’autorisation/de blocage du locataire

Pour afficher les entrées d’expéditeur de bloc, de fichier ou d’URL dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Cet exemple retourne des informations pour la valeur de hachage de fichier spécifiée.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Cet exemple retourne toutes les URL bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Afficher les entrées de l’expéditeur usurpé

Pour afficher les entrées d’expéditeur usurpées dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

Cet exemple retourne toutes les entrées d’expéditeur usurpées dans la liste d’autorisations/de blocs du locataire.

```powershell
Get-TenantAllowBlockListSpoofItems
```

Cet exemple retourne toutes les entrées d’expéditeur usurpées autorisées qui sont internes.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

Cet exemple retourne toutes les entrées d’expéditeur usurpées bloquées qui sont externes.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

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

  - Un caractère générique gauche doit être suivi d’un point pour spécifier un sous-domaine.

    Par exemple, `*.contoso.com` est autorisé ; `*contoso.com` il n’est pas autorisé.

  - Un caractère générique droit doit suivre une barre oblique (/) pour spécifier un chemin d’accès.

    Par exemple, `contoso.com/*` est autorisé ; `contoso.com*` ou `contoso.com/ab*` ne sont pas autorisés.

  - `*.com*` n’est pas valide (il ne s’agit pas d’un domaine pouvant être résolu et le caractère générique approprié ne suit pas une barre oblique).

  - Les caractères génériques ne sont pas autorisés dans les adresses IP.

- Le caractère tilde (~) est disponible dans les scénarios suivants :

  - Un tilde gauche implique un domaine et tous les sous-domaines.

    Par exemple `~contoso.com` , inclut `contoso.com` et `*.contoso.com`.

- Les entrées d’URL qui contiennent des protocoles (par exemple, `http://`, `https://`ou `ftp://`) échouent, car les entrées d’URL s’appliquent à tous les protocoles.

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
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Correspondance de bloc** :

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Bloc non mis en correspondance** : abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scénario : Caractère générique gauche (sous-domaine)

**Entrée** : `*.contoso.com`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - www.contoso.com
  - xyz.abc.contoso.com

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scénario : Caractère générique droit en haut du chemin d’accès

**Entrée** : `contoso.com/a/*`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scénario : Tilde gauche

**Entrée** : `~contoso.com`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Autoriser la mise en correspondance non mise en correspondance** et **Bloquer non mis en correspondance** :

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

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

**Entrée** : `*.contoso.com/*`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Autoriser non mis en correspondance** et **Bloquer non mis en correspondance** : contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scénario : Tilde gauche et droit

**Entrée** : `~contoso.com~`

- **Autoriser la correspondance** et **bloquer la correspondance** :

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
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

  - conto\* so.com
  - conto~so.com

- **Caractères génériques doubles**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Syntaxe de paire de domaines pour les entrées d’expéditeur usurpées dans la liste d’autorisations/de blocs du locataire

Une paire de domaines pour un expéditeur usurpé dans la liste d’autorisations/de blocs du locataire utilise la syntaxe suivante : `<Spoofed user>, <Sending infrastructure>`.

- **Utilisateur usurpé** : cette valeur implique l’adresse e-mail de l’utilisateur usurpé qui s’affiche dans la zone **From** dans les clients de messagerie. Cette adresse est également appelée adresse `5322.From` . Les valeurs valides sont les suivantes :
  - Adresse e-mail individuelle (par exemple, chris@contoso.com).
  - Un domaine de messagerie (par exemple, contoso.com).
  - Caractère générique (par exemple, \*).

- **Infrastructure d’envoi** : cette valeur indique la source des messages de l’utilisateur usurpé. Les valeurs valides sont les suivantes :
  - Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source (par exemple, fabrikam.com).
  - Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\>/24 (par exemple, 192.168.100.100/24).

Voici quelques exemples de paires de domaines valides pour identifier les expéditeurs usurpés :

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Le nombre maximal d’entrées d’expéditeur usurpées est de 1 000.

L’ajout d’une paire de domaines autorise ou bloque uniquement la *combinaison* de l’utilisateur usurpé *et* de l’infrastructure d’envoi. Il n’autorise pas les e-mails de l’utilisateur usurpé d’identité à partir d’une source quelconque, ni le courrier électronique provenant de la source d’infrastructure d’envoi pour tout utilisateur usurpé.

Par exemple, vous ajoutez une entrée d’autorisation pour la paire de domaines suivante :

- **Domaine** : gmail.com
- **Infrastructure** : tms.mx.com

Seuls les messages de cette paire d’infrastructure de domaine *et* d’envoi sont autorisés à usurper. Les autres expéditeurs qui tentent d’usurper gmail.com ne sont pas autorisés. Les messages des expéditeurs d’autres domaines provenant de tms.mx.com sont vérifiés par l’intelligence par usurpation d’identité.
