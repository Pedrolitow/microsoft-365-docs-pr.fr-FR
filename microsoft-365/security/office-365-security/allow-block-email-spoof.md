---
title: Autoriser ou bloquer des courriers utilisant la liste Autoriser/Bloquer des clients
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
description: Les administrateurs peuvent apprendre à autoriser ou bloquer les e-mails et les entrées d’expéditeur usurpés dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 107aef5dd4cc3098d6e77f45e6b95352997ef738
ms.sourcegitcommit: d7193ee954c01c4172e228d25b941026c8d92d30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2022
ms.locfileid: "67175001"
---
# <a name="allow-or-block-emails-using-the-tenant-allowblock-list"></a>Autoriser ou bloquer des courriers utilisant la liste Autoriser/Bloquer des clients

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous pouvez utiliser le portail Microsoft 365 Defender ou PowerShell pour autoriser ou bloquer les e-mails (y compris les e-mails d’usurpation d’identité) à l’aide de la liste d’autorisation/de blocage du locataire.

## <a name="create-block-sender-entries"></a>Créer des entrées d’expéditeur de blocs 

### <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Dans la page **Autoriser/Bloquer la liste** des locataires, vérifiez que l’onglet **Domaines & adresses** est sélectionné, puis cliquez sur l’icône ![Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

3. Dans le **menu volant Bloquer les domaines & adresses** qui s’affiche, configurez les paramètres suivants :
   - **Email adresses ou domaines** : entrez une adresse e-mail ou un domaine par ligne, jusqu’à un maximum de 20.
   - **N’expirez jamais** : effectuez l’une des étapes suivantes :
     - Vérifiez que le paramètre est désactivé (![désactiver.](../../media/scc-toggle-off.png)) et utilisez la case **Supprimer** pour spécifier la date d’expiration des entrées.

       ou

     - Déplacez le bouton bascule vers la droite pour configurer les entrées pour qu’ils n’expirent jamais : ![Activer/désactiver.](../../media/scc-toggle-on.png).
   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

> [!NOTE]
> Les e-mails de ces expéditeurs seront bloqués en tant que _courrier indésirable à haut niveau de confiance_ (SCL = 9).
> Les utilisateurs de l’organisation ne pourront pas envoyer d’e-mails à ces domaines et adresses bloqués. Ils recevront un rapport de non-remise qui indiquera ce qui suit : « 5.7.1 Votre message ne peut pas être remis, car un ou plusieurs destinataires sont bloqués par la stratégie d’autorisation/de liste de blocage du locataire de votre organisation. »

### <a name="use-powershell"></a>Utiliser PowerShell

Pour ajouter des entrées d’expéditeur de bloc dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <Sender> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple montre comment ajouter une entrée d’expéditeur de bloc pour l’expéditeur spécifié qui expire à une date spécifique.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-sender-entries"></a>Créer des entrées d’expéditeur autorisées 

### <a name="use-microsoft-365-defender"></a>Utiliser Microsoft 365 Defender

Autorisez les expéditeurs (ou domaines) sur la page **Soumissions** dans Microsoft 365 Defender.

Vous ne pouvez pas modifier directement la liste d’autorisations/de blocs de locataire pour ajouter des entrées d’autorisation. Utilisez plutôt [les soumissions d’administrateur](admin-submission.md) pour envoyer le message bloqué. Cette action ajoute l’URL, le fichier, la paire de domaines de l’expéditeur usurpé d’identité, le domaine emprunté (ou l’utilisateur) et/ou l’expéditeur à la liste d’autorisations/de blocs du locataire. Si l’élément n’a pas été bloqué, l’autorisation n’est pas créée. Dans la plupart des cas où le message a été déterminé comme un faux positif qui a été bloqué de manière incorrecte, l’entrée d’autorisation est supprimée à la date d’expiration spécifiée.

> [!IMPORTANT]
> - Étant donné que Microsoft gère les entrées d’autorisation pour vous, l’expéditeur inutile, l’URL ou les entrées d’autorisation de fichier qui ne sont pas nécessaires seront supprimées. Ce comportement protège votre organisation et permet d’éviter les entrées d’autorisation mal configurées. Si vous n’êtes pas d’accord avec le verdict, vous devrez peut-être ouvrir une demande de support pour déterminer pourquoi un message est toujours considéré comme incorrect.


1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Actions & soumissions** \> **soumissions**. Ou, pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné, puis cliquez sur ![Envoyer à Microsoft pour l’icône d’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

3. Utilisez le menu volant **Envoyer à Microsoft pour passer en revue** l’envoi d’un message en ajoutant l’ID de message réseau ou en chargeant le fichier e-mail.

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft**, sélectionnez **Ne doit pas avoir été bloquée (faux positif).**

5. Activez **Autoriser les messages comme cette** option.

6. Dans la liste **déroulante Supprimer après** la liste déroulante, spécifiez la durée pendant laquelle vous souhaitez que l’option d’autorisation fonctionne.

7. Ajoutez la raison pour laquelle vous ajoutez l’autorisation à l’aide de la zone **Note facultative** . 

8. Lorsque vous avez terminé, sélectionnez le bouton **Envoyer** .

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="Envoyer des programmes malveillants à Microsoft à des fins d’analyse, par exemple." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
>
> - Pendant le flux de courrier, en fonction des filtres qui ont déterminé que le courrier était malveillant, les autorisations sont ajoutées. Par exemple, l’expéditeur et l’URL sont déterminés comme étant incorrects, une autorisation est ajoutée pour chacune d’elles.
> - Lorsque cette entité (expéditeur, domaine, URL, fichier) est à nouveau rencontrée, tous les filtres associés à cette entité sont ignorés.
> - Pendant le flux de courrier, si le reste des filtres trouve l’e-mail contenant cette entité propre, l’e-mail est remis. Par exemple, l’autorisation d’un expéditeur (lorsque l’authentification réussit) contourne tous les verdicts, à l’exception des programmes malveillants et du hameçonnage à haut niveau de confiance associé à une pièce jointe ou à une URL.

## <a name="view-sender-entries"></a>Afficher les entrées de l’expéditeur 

Pour afficher les entrées de l’expéditeur de blocs dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <Sender> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```
Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-sender-entries"></a>Modifier les entrées de l’expéditeur 

Pour modifier les entrées d’expéditeur d’autorisation ou de blocage dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <Sender> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-sender-entries"></a>Supprimer les entrées de l’expéditeur 

Pour supprimer ou bloquer les entrées d’expéditeur de la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender> -Ids <"Id1","Id2",..."IdN">
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="domain-pair-syntax-for-spoofed-sender-entries"></a>Syntaxe de paire de domaines pour les entrées d’expéditeur usurpées

Une paire de domaines pour un expéditeur usurpé dans la liste d’autorisations/de blocs du locataire utilise la syntaxe suivante : `<Spoofed user>, <Sending infrastructure>`.

- **Utilisateur usurpé** : cette valeur implique l’adresse e-mail de l’utilisateur usurpé qui s’affiche dans la zone **From** dans les clients de messagerie. Cette adresse est également appelée adresse `5322.From` . Les valeurs valides sont les suivantes :
  - Adresse e-mail individuelle (par exemple, chris@contoso.com).
  - Un domaine de messagerie (par exemple, contoso.com).
  - Caractère générique (par exemple, \*).

- **Infrastructure d’envoi** : cette valeur indique la source des messages de l’utilisateur usurpé. Les valeurs valides sont les suivantes :
  - Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source (par exemple, fabrikam.com).
  - Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée comme \<source IP\>/24 (par exemple, 192.168.100.100/24).
  - Domaine DKIM vérifié.

Voici quelques exemples de paires de domaines valides pour identifier les expéditeurs usurpés :

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Le nombre maximal d’entrées d’expéditeur usurpées est de 1 000.

L’ajout d’une paire de domaines autorise ou bloque uniquement la *combinaison* de l’utilisateur usurpé *et* de l’infrastructure d’envoi. Il n’autorise pas les e-mails de l’utilisateur usurpé d’identité à partir d’une source quelconque, ni le courrier électronique provenant de la source d’infrastructure d’envoi pour tout utilisateur usurpé.

Par exemple, vous ajoutez une entrée d’autorisation pour la paire de domaines suivante :

- **Domaine** : gmail.com
- **Infrastructure** : tms.mx.com

Seuls les messages de cette paire d’infrastructure de domaine _et_ d’envoi sont autorisés à usurper. Les autres expéditeurs qui tentent d’usurper gmail.com ne sont pas autorisés. Les messages des expéditeurs d’autres domaines provenant de tms.mx.com sont vérifiés par l’intelligence par usurpation d’identité.

## <a name="create-blocked-spoofed-sender-entries"></a>Créer des entrées d’expéditeur usurpées bloquées

### <a name="use-microsoft-365-defender"></a>Utiliser Microsoft 365 Defender

> [!NOTE]
> Email de ces expéditeurs seront bloqués en tant que _hameçonnage_.
>
> Seule la _combinaison_ de l’utilisateur usurpé _et_ de l’infrastructure d’envoi définie dans la paire de domaines est spécifiquement autorisée ou bloquée pour l’usurpation d’identité.
>
> Lorsque vous configurez une entrée d’autorisation ou de blocage pour une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans l’insight d’intelligence contre l’usurpation d’identité.
>
> Les entrées des expéditeurs usurpés n’expirent jamais.

1. Dans le portail Microsoft 365 Defender, accédez à la section Stratégies **& règles de règles** sur les stratégies \> **de menaces** \> , section  \> **Listes d’autorisation/de blocage du locataire**.

2. Dans la page **Autoriser/Bloquer la liste** des locataires, sélectionnez l’onglet **Expéditeurs usurpés** , puis cliquez sur l’icône ![Bloquer.](../../media/m365-cc-sc-create-icon.png) **Ajouter**.

3. Dans le menu volant **Ajouter de nouvelles paires de domaines** qui s’affiche, configurez les paramètres suivants :
   - **Ajoutez de nouvelles paires de domaines avec des caractères génériques** : entrez une paire de domaines par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, consultez [Gérer la liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md).
   - **Type d’usurpation** d’identité : sélectionnez l’une des valeurs suivantes :
     - **Interne** : l’expéditeur usurpé se trouve dans un domaine qui appartient à votre organisation ( [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Externe** : l’expéditeur usurpé se trouve dans un domaine externe.
   - **Action** : Sélectionnez **Bloquer**.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

> [!NOTE]
> Les e-mails de ces expéditeurs seront bloqués en tant que _hameçonnage_.

### <a name="use-powershell"></a>Utiliser PowerShell

Pour ajouter des entrées d’expéditeur usurpées dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="create-allowed-spoofed-sender-entries"></a>Créer des entrées d’expéditeur usurpées autorisées 

### <a name="use-the-tenant-allowblock-list-in-microsoft-365-defender"></a>Utiliser la liste verte/bloquée du locataire dans Microsoft 365 Defender

> [!NOTE]
>
> - Seule la _combinaison_ de l’utilisateur usurpé _et_ de l’infrastructure d’envoi définie dans la paire de domaines est spécifiquement autorisée ou bloquée pour l’usurpation d’identité.
> - Lorsque vous configurez une entrée d’autorisation ou de blocage pour une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans l’insight d’intelligence contre l’usurpation d’identité.
> - Les entrées des expéditeurs usurpés n’expirent jamais.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & stratégies de **collaboration** \> **& règles Les stratégies** \> **de menace** **sont des listes** \> d’autorisation/de blocage dans la section **Règles**. Ou, pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Dans la page **Autoriser/Bloquer la liste** des locataires, sélectionnez l’onglet **Expéditeurs usurpés** , puis cliquez sur ![l’icône Ajouter.](../../media/m365-cc-sc-create-icon.png) **Ajouter**.

3. Dans le menu volant **Ajouter de nouvelles paires de domaines** qui s’affiche, configurez les paramètres suivants :
   - **Ajoutez de nouvelles paires de domaines avec des caractères génériques** : entrez une paire de domaines par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, consultez [Gérer la liste d’autorisation/de blocage du locataire](tenant-allow-block-list.md).
   - **Type d’usurpation** d’identité : sélectionnez l’une des valeurs suivantes :
     - **Interne** : l’expéditeur usurpé se trouve dans un domaine qui appartient à votre organisation ( [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Externe** : l’expéditeur usurpé se trouve dans un domaine externe.
   - **Action** : Sélectionnez **Autoriser**.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

### <a name="use-admin-submission-in-microsoft-365-defender"></a>Utiliser Administration soumission dans Microsoft 365 Defender

Vous pouvez également autoriser les expéditeurs usurpés d’identité à l’aide de la page **Soumissions** dans Microsoft 365 Defender.

Utilisez [les soumissions d’administrateur](admin-submission.md) pour envoyer le message bloqué. Cette action ajoute l’URL, le fichier, la paire de domaines de l’expéditeur usurpé d’identité, le domaine emprunté (ou l’utilisateur) et/ou l’expéditeur à la liste d’autorisations/de blocs du locataire. Si l’élément n’a pas été bloqué, l’autorisation n’est pas créée. 

> [!IMPORTANT]
>
> - L’usurpation d’identité permet de s’occuper de l’usurpation intra-organisation, inter-org et DMARC.
> - La note facultative dans la soumission de l’administrateur ne s’applique pas à l’usurpation d’identité.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Actions & soumissions** \> **soumissions**. Ou, pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné, puis cliquez sur ![Envoyer à Microsoft pour l’icône d’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

3. Utilisez le menu volant **Envoyer à Microsoft pour passer en revue** l’envoi d’un message en ajoutant l’ID de message réseau ou en chargeant le fichier e-mail.

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft**, sélectionnez **Ne doit pas avoir été bloquée (faux positif).**

5. Activez **Autoriser les messages comme cette** option.

6. Dans la liste **déroulante Supprimer après** la liste déroulante, spécifiez la durée pendant laquelle vous souhaitez que l’option d’autorisation fonctionne, bien qu’elle ne s’applique pas à l’usurpation d’identité, car elles n’expirent jamais.

7. Lorsque vous avez terminé, sélectionnez le bouton **Envoyer** .

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="Envoyer des programmes malveillants à Microsoft à des fins d’analyse, par exemple." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
>
> - La paire de domaines d’expéditeur usurpé sera créée et visible sous l’onglet **Expéditeurs usurpés** sous la page **d’autorisation/liste de blocs du locataire** .


### <a name="use-powershell"></a>Utiliser PowerShell

Pour ajouter des entrées d’expéditeur usurpées dans la liste d’autorisation/de blocage du locataire dans [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

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

## <a name="modify-spoofed-sender-entries"></a>Modifier les entrées d’expéditeur usurpées 

Pour modifier ou bloquer les entrées d’expéditeur usurpées dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

Cet exemple montre comment faire passer l’entrée de l’expéditeur usurpé de l’autorisation au bloc.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

## <a name="remove-spoofed-sender-entries"></a>Supprimer les entrées d’expéditeur usurpées 

Pour supprimer les entrées d’expéditeur d’autorisation ou de blocage de la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).

## <a name="create-impersonated-sender-entries"></a>Créer des entrées d’expéditeur empruntées

### <a name="use-admin-submission-in-microsoft-365-defender"></a>Utiliser Administration soumission dans Microsoft 365 Defender

Vous pouvez également autoriser les expéditeurs usurpés d’identité à l’aide de la page **Soumissions** dans Microsoft 365 Defender.

Utilisez [les soumissions d’administrateur](admin-submission.md) pour envoyer le message bloqué. Cette action ajoute l’URL, le fichier, la paire de domaines de l’expéditeur usurpé d’identité, le domaine emprunté (ou l’utilisateur) et/ou l’expéditeur à la liste d’autorisations/de blocs du locataire. Si l’élément n’a pas été bloqué, l’autorisation n’est pas créée. 

> [!IMPORTANT]
>
> - L’emprunt d’identité permet de prendre en charge l’emprunt d’identité de domaine et d’utilisateur.
> - L’emprunt d’identité graphe n’est pas pris en charge à partir d’ici pour l’instant.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Actions & soumissions** \> **soumissions**. Ou, pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné, puis cliquez sur ![Envoyer à Microsoft pour l’icône d’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

3. Utilisez le menu volant **Envoyer à Microsoft pour passer en revue** l’envoi d’un message en ajoutant l’ID de message réseau ou en chargeant le fichier e-mail.

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft**, sélectionnez **Ne doit pas avoir été bloquée (faux positif).**

5. Activez **Autoriser les messages comme cette** option.

6. Dans la liste **déroulante Supprimer après** la liste déroulante, spécifiez la durée pendant laquelle vous souhaitez que l’option d’autorisation fonctionne, même si elle ne s’applique pas aux autorisations empruntées, car elles n’expirent jamais.

7. Lorsque vous avez terminé, sélectionnez le bouton **Envoyer** .

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="Envoyer des programmes malveillants à Microsoft à des fins d’analyse, par exemple." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
> Le domaine usurpé d’identité (ou utilisateur) sera créé et visible dans la section **Expéditeurs et domaines approuvés** de la stratégie anti-hameçonnage à l’adresse <https://security.microsoft.com/antiphishing>.

## <a name="related-articles"></a>Articles connexes

- [Envois par l’administrateur](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Autoriser ou bloquer des fichiers dans la liste d’autorisations/de blocs du locataire](allow-block-files.md)
- [Autoriser ou bloquer des URL dans la liste d’autorisations/de blocs du locataire](allow-block-urls.md)
