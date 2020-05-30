---
title: Gérer les URL et les fichiers autorisés et bloqués dans la liste d’autorisation/de blocage du client
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent apprendre à configurer les entrées d’URL et de fichiers dans la liste des clients autorisés/bloqués du centre de sécurité & Compliance Center.
ms.openlocfilehash: b3a25458bbde2b3a78cfecc60ccb75fe298013f7
ms.sourcegitcommit: 6746fae2f68400fd985711b1945b66766d2a59a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419260"
---
# <a name="manage-urls-and-files-in-the-tenant-allowblock-list"></a>Gérer les URL et les fichiers dans la liste d’autorisation/de blocage du client

> [!NOTE]
> Les fonctionnalités décrites dans cette rubrique sont en mode aperçu, sont sujettes à modification et ne sont pas disponibles dans toutes les organisations.

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, vous pouvez ne pas utiliser le verdict de filtrage EOP. Par exemple, un bon message peut être marqué comme incorrect (faux positif) ou un message incorrect peut être autorisé par (faux négatif).

La liste des clients autorisés/bloqués du centre de sécurité & conformité vous offre un moyen de remplacer manuellement les verdicts de filtrage Microsoft 365. La liste d’autorisation/de blocage de client est utilisée pendant le flux de messagerie et au moment de l’utilisateur clique dessus. Vous pouvez spécifier des URL et des fichiers à autoriser ou à bloquer dans la liste des clients autorisés/bloqués.

Cette rubrique décrit comment configurer les entrées dans la liste des clients autorisés/bloqués du centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande autonome EOP PowerShell pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de sécurité et conformité sur <https://protection.office.com/>. Pour accéder directement à la page d' **autorisation/de blocage de client** , utilisez <https://protection.office.com/tenantAllowBlockList> .

- Vous spécifiez les fichiers à l’aide de la valeur de hachage SHA256 du fichier. Pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes :

  ```dos
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Par exemple, la valeur est `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a` . Les valeurs de hachage de percepteur (pHash) ne sont pas autorisées.

- Les valeurs d’URL disponibles sont décrites dans la [syntaxe URL de la section liste des clients autorisés/bloqués](#url-syntax-for-the-tenant-allowblock-list) plus loin dans cette rubrique.

- La liste d’autorisation/de blocage de client autorise un nombre maximal de 500 entrées pour les URL et 500 entrées pour les hachages de fichiers.

- Une entrée doit être active dans les 15 minutes.

- Les entrées bloquées prévalent sur les entrées autoriser.

- Par défaut, les entrées de la liste d’autorisation/de blocage client expirent au bout de 30 jours. Vous pouvez spécifier une date ou la définir pour qu’elle n’expire jamais.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Pour ajouter et supprimer des valeurs dans la liste d’autorisation/de blocage de client, vous devez être membre des groupes de rôles de gestion de l' **organisation** ou d' **administrateur de sécurité** . Pour un accès en lecture seule à la liste verte/rouge de client, vous devez être membre du groupe de rôles **lecteur de sécurité** . Pour des informations supplémentaires sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="use-the-security--compliance-center-to-create-url-entries-in-the-tenant-allowblock-list"></a>Utiliser le centre de sécurité & conformité pour créer des entrées d’URL dans la liste verte/rouge de client

Pour plus d’informations sur la syntaxe des entrées d’URL, voir la syntaxe de l' [URL de la section liste des clients autorisés/bloqués](#url-syntax-for-the-tenant-allowblock-list) plus loin dans cette rubrique.

1. Dans le centre de sécurité & conformité, accédez **Threat management** à \> **Policy** \> **liste verte/rouge**de la stratégie de gestion des menaces.

2. Sur la page **liste des clients autorisés/bloqués** , vérifiez que l’onglet **URL** est sélectionné, puis cliquez sur **Ajouter** .

3. Dans la fenêtre mobile **ajouter de nouvelles URL** qui s’affiche, configurez les paramètres suivants :

   - **Ajouter des URL avec des caractères génériques**: entrez une URL par ligne, jusqu’à un maximum de 20.

   - **Bloquer/autoriser**: indiquez si vous souhaitez **autoriser** ou **bloquer** les URL spécifiées.

   - N' **expire jamais**: effectuez l’une des opérations suivantes :

     - Vérifiez que le paramètre est désactivé (désactivez-le ![ ](../../media/scc-toggle-off.png) ) et utilisez la zone **expire** le, pour spécifier la date d’expiration des entrées.

     ou

     - Déplacez le bouton bascule vers la droite pour configurer les entrées de sorte qu’elles n’expirent jamais : ![Activer](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png).

   - **Facultatif Remarque**: entrez un texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="use-the-security--compliance-center-to-create-file-entries-in-the-tenant-allowblock-list"></a>Utiliser le centre de sécurité & conformité pour créer des entrées de fichier dans la liste des clients autorisés/bloqués

1. Dans le centre de sécurité & conformité, accédez **Threat management** à \> **Policy** \> **liste verte/rouge**de la stratégie de gestion des menaces.

2. Sur la page **liste des clients autorisés/bloqués** , sélectionnez l’onglet **fichiers** , puis cliquez sur **Ajouter**.

3. Dans la fenêtre mobile **ajouter de nouveaux fichiers** qui s’affiche, configurez les paramètres suivants :

   - **Ajouter des hachages de fichier**: saisissez une valeur de hachage SHA256 par ligne, jusqu’à un maximum de 20.

   - **Bloquer/autoriser**: indiquez si vous souhaitez **autoriser** ou **bloquer** les fichiers spécifiés.

   - N' **expire jamais**: effectuez l’une des opérations suivantes :

     - Vérifiez que le paramètre est désactivé (désactivez-le ![ ](../../media/scc-toggle-off.png) ) et utilisez la zone **expire** le, pour spécifier la date d’expiration des entrées.

     ou

     - Déplacez le bouton bascule vers la droite pour configurer les entrées de sorte qu’elles n’expirent jamais : ![Activer](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png).

   - **Facultatif Remarque**: entrez un texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="use-the-security--compliance-center-to-view-url-and-file-entries-in-the-tenant-allowblock-list"></a>Utiliser le centre de sécurité & conformité pour afficher les entrées d’URL et de fichiers dans la liste d’autorisation/de blocage de client

1. Dans le centre de sécurité & conformité, accédez **Threat management** à \> **Policy** \> **liste verte/rouge**de la stratégie de gestion des menaces.

2. Sélectionnez l’onglet **URL** ou **fichiers** .

Cliquez sur les en-têtes de colonne suivants pour trier dans l’ordre croissant ou décroissant :

- **Valeur**: l’URL ou le hachage du fichier.
- **Action**: **bloquer** ou **autoriser**.
- **Date de la dernière mise à jour**
- **Date d’expiration**
- **Remarque**

Cliquez sur **groupe** pour regrouper les entrées par **action** (**bloquer** ou **autoriser**) ou **aucune**.

Cliquez sur **Rechercher**, entrez la totalité ou une partie d’une URL ou d’une valeur de fichier, puis appuyez sur entrée pour rechercher une valeur spécifique. Lorsque vous avez terminé, cliquez sur **Effacer** l' ![ icône Rechercher ](../../media/b6512677-5e7b-42b0-a8a3-3be1d7fa23ee.gif) .

Cliquez sur **filtre**. Dans le menu volant **filtre** qui s’affiche, configurez l’un des paramètres suivants :

- **Action**: sélectionnez **autoriser**, **bloquer** ou les deux.

- **N’expire jamais**: sélectionnez désactivé (désactiver ![ ](../../media/scc-toggle-off.png) ) ou activé ( ![ bascule ](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png) ).

- **Dernière mise à jour**: sélectionnez une date**de**début (de), une date de fin (**à**) ou les deux.

- **Date d’expiration**: sélectionnez une date de début (**de**), une date de fin (**à**) ou les deux.

Lorsque vous avez terminé, cliquez sur **appliquer**.

Pour effacer les filtres existants, cliquez sur **Filtrer**et, dans le menu volant **filtre** qui s’affiche, cliquez sur **effacer les filtres**.

## <a name="use-the-security--compliance-center-to-modify-url-and-file-entries-in-the-tenant-allowblock-list"></a>Utiliser le centre de sécurité & conformité pour modifier les entrées d’URL et de fichiers dans la liste d’autorisation/de blocage de client

Vous ne pouvez pas modifier la valeur de l’URL ou du fichier lui-même. Au lieu de cela, vous devez supprimer l’entrée et la recréer.

1. Dans le centre de sécurité & conformité, accédez **Threat management** à \> **Policy** \> **liste verte/rouge**de la stratégie de gestion des menaces.

2. Sélectionnez l’onglet **URL** ou **fichiers** .

3. Sélectionnez l’entrée que vous souhaitez modifier, puis cliquez sur **modifier** l' ![ icône modifier ](../../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) .

4. Dans le menu volant qui s’affiche, configurez les paramètres suivants :

   - **Bloquer/autoriser**: sélectionnez **autoriser** ou **bloquer**.

   - N' **expire jamais**: effectuez l’une des opérations suivantes :

     - Vérifiez que le paramètre est désactivé (désactivez-le ![ ](../../media/scc-toggle-off.png) ) et utilisez la zone **expire** le, pour spécifier la date d’expiration de l’entrée.

     ou

     - Déplacez le bouton bascule vers la droite pour configurer l’entrée de sorte qu’elle n’expire jamais : ![Activer](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png).

   - **Facultatif Remarque**: entrez un texte descriptif pour l’entrée.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-remove-url-and-file-entries-from-the-tenant-allowblock-list"></a>Utiliser le centre de sécurité & conformité pour supprimer les entrées d’URL et de fichier de la liste des clients autorisés/bloqués

1. Dans le centre de sécurité & conformité, accédez **Threat management** à \> **Policy** \> **liste verte/rouge**de la stratégie de gestion des menaces.

2. Sélectionnez l’onglet **URL** ou **fichiers** .

3. Sélectionnez l’entrée que vous souhaitez supprimer, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/87565fbb-5147-4f22-9ed7-1c18ce664392.png) .

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **supprimer**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-the-tenant-allowblock-list"></a>Utiliser Exchange Online PowerShell ou le PowerShell autonome EOP pour configurer la liste d’autorisation/de blocage de client

### <a name="use-powershell-to-add-url-and-file-entries-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour ajouter des entrées d’URL et de fichiers dans la liste d’autorisation/de blocage de client

Pour ajouter des entrées d’URL et de fichier dans la liste des clients autorisés/bloqués, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <Url | FileHash> -Action <Allow | Block> -Entries <String[]> [-ExpirationDate <DateTime>] [-NoExpiration] [-Notes <String>]
```

Cet exemple montre comment ajouter une entrée de bloc d’URL pour contoso.com et tous les sous-domaines (par exemple, contoso.com, www.contoso.com et xyz.abc.contoso.com). Étant donné que nous n’utilisons pas les paramètres ExpirationDate ou noexpiration, l’entrée expire au bout de 30 jours.

```powershell
New-TenantAllowBlockListItem -ListType Url -Action Block -Entries ~contoso.com
```

```powershell
New-TenantAllowBlockListItem -ListType FileHash -Action Allow -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Cet exemple ajoute une entrée d’autorisation de fichier pour les fichiers spécifiés qui n’expire jamais.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-url-and-file-entries-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour afficher les entrées d’URL et de fichiers dans la liste d’autorisation/de blocage de client

Pour afficher les entrées d’URL et de fichier dans la liste des clients autorisés/bloqués, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <Url | FileHash> [-Entry <URLValue | FileHashValue>] [-Action <Allow | Block>] [-ExpirationDate <DateTime>] [-NoExpiration]
```

Cet exemple renvoie toutes les URL bloquées.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Action Block
```

Cet exemple renvoie des informations sur la valeur de hachage de fichier spécifiée.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-url-and-file-entries-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour modifier les entrées d’URL et de fichiers dans la liste d’autorisation/de blocage de client

Vous ne pouvez pas modifier la valeur de l’URL ou du fichier lui-même. Au lieu de cela, vous devez supprimer l’entrée et la recréer.

Pour modifier les entrées d’URL et de fichier dans la liste des clients autorisés/bloqués, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <Url | FileHash> -Ids <"Id1","Id2",..."IdN"> [-Action <Allow | Block>] [-ExpirationDate <DateTime>] [-NoExpiration] [-Notes <String>]
```

Cet exemple montre comment modifier la date d’expiration de l’entrée spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate (Get-Date "5/30/2020 9:30 AM").ToUniversalTime()
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-url-and-file-entries-from-the-tenant-allowblock-list"></a>Utiliser PowerShell pour supprimer les entrées d’URL et de fichier de la liste des clients autorisés/bloqués

Pour supprimer les entrées d’URL et de fichier de la liste des clients autorisés/bloqués, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <Url | FileHash> -Ids <"Id1","Id2",..."IdN">
```

Cet exemple supprime l’entrée d’URL spécifiée de la liste des clients bloqués/bloqués.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Syntaxe d’URL de la liste d’autorisation/de blocage de client

- Les adresses IP4v et IPv6 sont autorisées, mais pas les ports TCP/UDP.

- Les extensions de nom de fichier ne sont pas autorisées (par exemple, test. pdf).

- Unicode n’est pas pris en charge, mais Punycode est.

- Les noms d’hôte sont autorisés si toutes les instructions suivantes sont vraies :

  - Le nom d’hôte contient un point.
  - Il y a au moins un caractère à gauche du point.
  - Il y a au moins deux caractères à droite de la période.

  Par exemple, `t.co` est autorisé ou n’est `.com` `contoso.` pas autorisé.

- Les sous-chemins ne sont pas implicites.

  Par exemple, `contoso.com` n’inclut pas `contoso.com/a` .

- Les caractères génériques (*) sont autorisés dans les scénarios suivants :

  - Un caractère générique gauche doit être suivi d’un point pour spécifier un sous-domaine.

    Par exemple, `*.contoso.com` est autorisé ; `*contoso.com` n’est pas autorisé.

  - Un caractère générique droit doit suivre une barre oblique (/) pour spécifier un chemin d’accès.

    Par exemple, `contoso.com/*` est autorisé ou n’est `contoso.com*` `contoso.com/ab*` pas autorisé.

  - Tous les sous-chemins ne sont pas implicitement par un caractère générique de droite.

    Par exemple, `contoso.com/*` n’inclut pas `contoso.com/a` .

  - `*.com*`n’est pas valide (ce n’est pas un domaine pouvant être résolu et le caractère générique droit ne suit pas une barre oblique).

  - Les caractères génériques ne sont pas autorisés dans les adresses IP.

- Le caractère tilde (~) est disponible dans les scénarios suivants :

  - Un tilde gauche implique un domaine et tous les sous-domaines.

    Par exemple `~contoso.com` `contoso.com` , inclut et `*.contoso.com` .

- Les entrées d’URL qui contiennent des protocoles (par exemple,, `http://` `https://` ou `ftp://` ) échouent, car les entrées d’URL s’appliquent à tous les protocoles.

- Un nom d’utilisateur ou un mot de passe n’est pas pris en charge ou obligatoire.

- Les guillemets ('ou ") sont des caractères non valides.

- Une URL doit inclure toutes les redirections, le cas échéant.

### <a name="url-entry-scenarios"></a>Scénarios d’entrée d’URL

Les entrées d’URL valides et leurs résultats sont décrits dans les sections suivantes.

#### <a name="scenario-no-wildcards"></a>Scénario : pas de caractères génériques

**Entrée**:`contoso.com`

- **Correspondance autorisée**: contoso.com

- **Ne pas faire correspondre**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www. contoso. com/q = a@contoso. com
  
- **Correspondance de bloc**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www. contoso. com/q = a@contoso. com

- **Bloc sans correspondance**: ABC-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scénario : caractère générique gauche (sous-domaine)

**Entrée**:`*.contoso.com`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc
  
#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scénario : caractère générique droit en haut du chemin d’accès

**Entrée**:`contoso.com/a/*`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso. com/a/ ? q = joe@t. com

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www. contoso. com/q = a@contoso. com
  
#### <a name="scenario-left-tilde"></a>Scénario : tilde gauche

**Entrée**:`~contoso.com`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scénario : suffixe de caractère générique droit

**Entrée**:`contoso.com/*`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - contoso. com/ ? q = whatever@fabrikam. com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scénario : sous-domaine du caractère générique gauche et suffixe générique droit

**Entrée**:`*.contoso.com/*`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scénario : tilde gauche et droit

**Entrée**:`~contoso.com~`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scénario : adresse IP

**Entrée**:`1.2.3.4`

- **Autoriser la correspondance** et la **correspondance de bloc**: 1.2.3.4

- **N’autoriser ni correspondance** , ni **bloc sans correspondance**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Adresse IP avec caractère générique droit

**Entrée**:`1.2.3.4/*`

- **Autoriser** la correspondance et la **correspondance de bloc**:

  - 1.2.3.4/b
  - 1.2.3.4/bAAAA

### <a name="examples-of-invalid-entries"></a>Exemples d’entrées non valides

Les entrées suivantes ne sont pas valides :

- **Valeurs de domaine manquantes ou non valides**:

  - contoso
  - \*contoso.\*
  - \*. com
  - \*.pdf

- **Caractères génériques sur le texte ou sans espacement**:

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **Adresses IP avec des ports**:

  - contoso.com:443
  - abc.contoso.com:25

- **Caractères génériques non descriptifs**:

  - \*
  - \*.\*

- **Caractères génériques intermédiaires**:

  - CONT \* so.com
  - Conto ~ so. com

- **Caractères génériques doubles**

  - contoso.com/\*\*
  - contoso.com/\*/\*
