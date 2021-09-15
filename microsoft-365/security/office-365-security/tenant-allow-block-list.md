---
title: Gérer vos autoriser et bloquer dans la liste d’autoriser/bloquer le client
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
description: Les administrateurs peuvent apprendre à gérer les autoriser et les blocs dans la liste d’adresses client autoriser/bloquer dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 511dde8921f9406f753c857e2d813ccd80976c40
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59353633"
---
# <a name="manage-the-tenant-allowblock-list"></a>Gérer la liste Autoriser/Bloquer du client

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Certaines des fonctionnalités décrites dans cet article sont en prévisualisation, sont sujettes à modification et ne sont pas disponibles dans toutes les organisations.
>
> Si votre organisation ne dispose pas des fonctionnalités d’usurpation d’informations décrites dans cet article, consultez l’ancienne expérience de gestion de l’usurpation d’adresse chez [Manage spoofof senders using the spoof intelligence policy and spoof intelligence insight in EOP](walkthrough-spoof-intelligence-insight.md).

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, vous pouvez ne pas être d’accord avec le verdict de filtrage EOP. Par exemple, un bon message peut être marqué comme mauvais (faux positif) ou un message erroné peut être autorisé (faux négatif).

La liste des locataires autoriser/bloquer dans le portail Microsoft 365 Defender vous permet de remplacer manuellement les verdicts de filtrage Microsoft 365 client. La liste d’adresses client autoriser/bloquer est utilisée pendant le flux de messagerie pour les messages entrants (ne s’applique pas aux messages intra-organisationaux) et au moment des clics de l’utilisateur. Vous pouvez spécifier les types de substitutions suivants :

- URL à bloquer.
- Fichiers à bloquer.
- Messages électroniques ou domaines de l’expéditeur à bloquer.
- Expéditeurs usurpés à autoriser ou bloquer. Si vous remplacez le verdict [](learn-about-spoof-intelligence.md)d’usurpation d’informations sur l’usurpation d’adresse, l’expéditeur  usurpé devient une entrée d’accès ou de blocage manuelle qui apparaît uniquement sous l’onglet Usurpation d’adresse dans la liste d’adresses client autoriser/bloquer. Vous pouvez également créer manuellement des entrées d’autoriser ou de bloquer des expéditeurs usurpés ici avant qu’ils ne sont détectés par la veille contre l’usurpation d’adresses.
- URL à autoriser.
- Fichiers à autoriser.
- Messages électroniques ou domaines de l’expéditeur à autoriser.

Cet article explique comment configurer des entrées dans la liste d’adresses client autoriser/bloquer dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres en Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com/>. Pour aller directement à la page Des listes **d’accueil/de** blocage des clients, utilisez <https://security.microsoft.com/tenantAllowBlockList> .

- Vous spécifiez des fichiers à l’aide de la valeur de hachage SHA256 du fichier. Pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes :

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Un exemple de valeur est `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a` . Les valeurs de hachage perceptif (pHash) ne sont pas pris en charge.

- Les valeurs d’URL disponibles sont décrites dans la [syntaxe d’URL](#url-syntax-for-the-tenant-allowblock-list) de la section Tenant Allow/Block List plus loin dans cet article.

- La liste d’adresses client autorise un maximum de 500 entrées pour les expéditeurs, 500 entrées pour les URL, 500 entrées pour les hèmes de fichiers et 1 024 entrées pour l’usurpation d’adresse (expéditeurs usurpés).

- Le nombre maximal de caractères pour chaque entrée est :
  - Hèmes de fichier = 64
  - URL = 250

- Une entrée doit être active dans les 30 minutes.

- Par défaut, les entrées de la liste d’inscriptions au client sont expirées au bout de 30 jours. Vous pouvez spécifier une date ou les définir pour qu’elles n’expirent jamais.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans Exchange Online pour que vous puissiez effectuer les procédures décrites dans cet article :
  - **Expéditeurs, URL et fichiers**:
    - Pour ajouter et supprimer des valeurs de la liste d’attente des locataires,  vous devez être membre des groupes de rôles Gestion de l’organisation, Administrateur de la sécurité ou Opérateur de sécurité, ou le rôle Gestionnaire **AllowBlockList** du client vous est attribué.
    - Pour un accès en lecture seule à la liste d’accès  au  client autorisé/bloqué, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.
  - **Usurpation :** l’une des combinaisons suivantes :
    - **Gestion de l'organisation**
    - **Administrateur de sécurité** <u>et</u> **configuration en affichage seul** ou gestion de **l’organisation en affichage seul.**

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="configure-the-tenant-allowblock-list"></a>Configurer la liste d’accès au client

### <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender

Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

Pour ajouter tous les blocs, voir [Ajouter des blocs dans la liste d’attente des locataires.](manage-tenant-blocks.md)

Pour ajouter tous les autoriser, voir Ajouter des autoriser dans la liste des locataires [autoriser/bloquer](manage-tenant-allows.md).

Pour modifier et supprimer tous les blocs et tous les blocs, voir Modifier et supprimer des entrées dans la liste [d’attente/d’accès au client.](modify-remove-entries-tenant-allow-block.md)

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome

Pour gérer tous les blocs et tous les autoriser, voir Ajouter des blocs dans la liste d’attente [du](manage-tenant-blocks.md)client, Ajouter des autoriser dans la liste des locataires [autoriser/bloquer,](manage-tenant-allows.md)et modifier et supprimer des entrées dans la liste d’inscriptions client [autoriser/bloquer](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Afficher les entrées dans la liste des locataires autoriser/bloquer

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Sélectionnez l’onglet de votre choix. Les colonnes disponibles dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs**:
     - **Valeur**: le domaine ou l’adresse e-mail de l’expéditeur.
     - **Action**: la valeur **Autoriser** ou **Bloquer**.
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Remarques**
   - **URL**:
     - **Valeur**: URL.
     - **Action**: la valeur **Autoriser** ou **Bloquer**.
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Remarques**
   - **Files**
     - **Valeur**: hachage du fichier.
     - **Action**: la valeur **Autoriser** ou **Bloquer**.
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Remarques**
   - **Usurpation**
     - **Utilisateur usurpé**
     - **Infrastructure d’envoi**
     - **Type d’usurpation**: valeur **Interne** ou **Externe.**
     - **Action**: la valeur **Bloquer ou** **Autoriser**.

   Vous pouvez cliquer sur un en-tête de colonne pour trier par ordre croissant ou décroit.

   Vous pouvez cliquer sur **Grouper** pour grouper les résultats. Les valeurs disponibles dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs**: vous pouvez grouper les résultats par **action.**
   - **URL : vous** pouvez grouper les résultats par **action.**
   - **Fichiers**: vous pouvez grouper les résultats par **action.**
   - **Usurpation :** vous pouvez grouper les résultats par **action** ou **type d’usurpation.**

   Cliquez **sur** Rechercher, entrez une partie ou l’ensemble d’une valeur, puis appuyez sur Entrée pour trouver une valeur spécifique. Lorsque vous avez terminé, cliquez sur ![ Effacer l’icône de recherche.](../../media/m365-cc-sc-close-icon.png) **Effacer la recherche.**

   Cliquez **sur Filtrer** pour filtrer les résultats. Les valeurs disponibles dans le flyout **Filter** qui s’affiche dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs**
     - **Action**
     - **Ne jamais expirer**
     - **Date de la dernière mise à jour**
     - **Supprimer le**
   - **URL**
     - **Action**
     - **Ne jamais expirer**
     - **Date de la dernière mise à jour**
     - **Supprimer le**
   - **Files**
     - **Action**
     - **Ne jamais expirer**
     - **Dernière mise à jour**
     - **Supprimer le**
   - **Usurpation**
     - **Action**
     - **Type d’usurpation**

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants,  cliquez sur **Filtrer** et dans le volant de filtre qui s’affiche, cliquez **sur Effacer les filtres.**

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Afficher les entrées de l’expéditeur, du fichier ou de l’URL dans la liste d’adresses client autoriser/bloquer

Pour afficher les entrées d’expéditeur, de fichier ou d’URL de blocage dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Cet exemple renvoie des informations pour la valeur de hachage de fichier spécifiée.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Cet exemple renvoie toutes les URL bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-TenantAllowBlockListItems.](/powershell/module/exchange/get-tenantallowblocklistitems)

## <a name="view-spoofed-sender-entries"></a>Afficher les entrées d’expéditeur usurpées

Pour afficher les entrées d’expéditeur usurpées dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

Cet exemple renvoie toutes les entrées d’expéditeur usurpées dans la liste d’adresses client autoriser/bloquer.

```powershell
Get-TenantAllowBlockListSpoofItems
```

Cet exemple renvoie toutes les entrées d’expéditeur usurpées qui sont internes.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

Cet exemple renvoie toutes les entrées d’expéditeur usurpées bloquées qui sont externes.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Syntaxe d’URL pour la liste d’adresses client autoriser/bloquer

- Les adresses IP4v et IPv6 sont autorisées, mais pas les ports TCP/UDP.

- Les extensions de nom de fichier ne sont pas autorisées (par exemple, test.pdf).

- Unicode n’est pas pris en charge, mais c’est le cas de Punycode.

- Les noms d’hôte sont autorisés si toutes les instructions suivantes sont vraies :
  - Le nom d’hôte contient un point.
  - Il y a au moins un caractère à gauche du point.
  - Il y a au moins deux caractères à droite du point.

  Par exemple, `t.co` est autorisé ou `.com` `contoso.` non.

- Les sous-chemins ne sont pas implicites pour les allows.

  Par exemple, `contoso.com` n’inclut pas `contoso.com/a` .

- Les caractères génériques (*) sont autorisés dans les scénarios suivants :

  - Un caractère générique gauche doit être suivi d’un point pour spécifier un sous-domaine.

    Par exemple, `*.contoso.com` est autorisé ; `*contoso.com` n’est pas autorisé.

  - Un caractère générique droit doit suivre une barre oblique (/) pour spécifier un chemin d’accès.

    Par exemple, `contoso.com/*` est autorisé ou `contoso.com*` `contoso.com/ab*` non.

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

- **Caractère générique sur du texte ou sans espacement**:

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

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Syntaxe de paire de domaines pour les entrées d’expéditeur usurpées dans la liste d’adresses client autoriser/bloquer

Une paire de domaines pour un expéditeur usurpé dans la liste d’adresses client autoriser/bloquer utilise la syntaxe suivante `<Spoofed user>, <Sending infrastructure>` :

- **Utilisateur usurpé**: cette valeur implique l’adresse e-mail de l’utilisateur  usurpé qui s’affiche dans la zone De des clients de messagerie. Cette adresse est également appelée `5322.From` adresse. Les valeurs valides sont les suivantes :
  - Adresse de messagerie individuelle (par exemple, chris@contoso.com).
  - Un domaine de messagerie (par exemple, contoso.com).
  - Caractère générique (par exemple, \* ).

- **Infrastructure d’envoi**: cette valeur indique la source des messages de l’utilisateur usurpé. Les valeurs valides sont les suivantes :
  - Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source (par exemple, fabrikam.com).
  - Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\> /24 (par exemple, 192.168.100.100/24).

Voici quelques exemples de paires de domaines valides pour identifier les expéditeurs usurpés :

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Le nombre maximal d’entrées d’expéditeur usurpées est de 1 000.

L’ajout d’une paire de domaines autorise ou bloque uniquement la *combinaison* de l’utilisateur usurpé *et* de l’infrastructure d’envoi. Il n’autorise pas le courrier électronique provenant de l’utilisateur usurpé d’aucune source, ni le courrier provenant de la source d’infrastructure d’envoi pour tout utilisateur usurpé. 

Par exemple, vous ajoutez une entrée d’accès pour la paire de domaines suivante :

- **Domaine**: gmail.com
- **Infrastructure**: tms.mx.com

Seuls les messages provenant *de* ce domaine et de cette paire d’infrastructure d’envoi sont autorisés à usurper l’usurpation. Les autres expéditeurs qui tentent d’usurper gmail.com ne sont pas autorisés. Les messages provenant d’expéditeurs d’autres domaines tms.mx.com sont vérifiés par la veille contre l’usurpation d’adresse.
