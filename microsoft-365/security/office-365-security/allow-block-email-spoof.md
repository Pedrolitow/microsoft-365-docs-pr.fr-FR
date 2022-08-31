---
title: Autoriser ou bloquer des courriers utilisant la liste Autoriser/Bloquer des clients
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
description: Les administrateurs peuvent apprendre à autoriser ou bloquer les e-mails et les entrées d’expéditeur usurpés dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 03dd5247135e3d4d297e73ab166921adc73f3573
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67469578"
---
# <a name="allow-or-block-emails-using-the-tenant-allowblock-list"></a>Autoriser ou bloquer des courriers utilisant la liste Autoriser/Bloquer des clients

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article explique comment créer et gérer des entrées d’autorisation et de blocage pour les domaines et les adresses e-mail (y compris les expéditeurs usurpés) qui sont disponibles dans la liste d’autorisation/de blocage du locataire. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

Vous gérez les entrées d’autorisation et de blocage des e-mails dans le portail Microsoft 365 Defender ou dans Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>. Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour les domaines et les adresses e-mail, le nombre maximal d’entrées autorisées est de 500 et le nombre maximal d’entrées de bloc est de 500 (1 000 entrées de domaine et d’adresse e-mail au total).

- Pour les expéditeurs usurpés, le nombre maximal d’entrées est de 1 024.

- Les entrées des expéditeurs usurpés n’expirent jamais.

- Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, consultez la [syntaxe de la paire de domaines pour les entrées d’expéditeur usurpées](#domain-pair-syntax-for-spoofed-sender-entries) plus loin dans cet article.

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

## <a name="domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Domaines et adresses e-mail dans la liste d’autorisation/de blocage du locataire

### <a name="create-block-entries-for-domains-and-email-addresses"></a>Créer des entrées de bloc pour les domaines et les adresses e-mail

Vous disposez des options suivantes pour créer des entrées de bloc pour les domaines et les adresses e-mail :

- [Page Soumissions dans le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-block-entries-for-domains-and-email-addresses-in-the-submissions-portal)
- Liste verte/bloquée du locataire dans [le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list) ou dans [PowerShell](#use-powershell-to-create-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list)

Pour créer des entrées de bloc pour les expéditeurs usurpés d’identité, consultez [le portail Microsoft 365 Defender pour afficher les entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la section Autoriser/Bloquer la liste](#use-the-microsoft-365-defender-portal-to-view-allow-or-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list) des locataires plus loin dans cet article.

#### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-domains-and-email-addresses-in-the-submissions-portal"></a>Utilisez le portail Microsoft 365 Defender pour créer des entrées de bloc pour les domaines et les adresses e-mail dans le portail Soumissions

Lorsque vous utilisez le portail <https://security.microsoft.com/reportsubmission> Soumissions pour signaler les messages électroniques comme ayant **dû être bloqués (faux négatif),** vous pouvez sélectionner **Bloquer tous les e-mails de ce destinataire** pour ajouter une entrée de bloc pour le domaine ou l’expéditeur dans la liste d’autorisation/de blocage du locataire.

Pour obtenir des instructions, consultez [Signaler un e-mail douteux à Microsoft](admin-submission.md#report-questionable-email-to-microsoft).

#### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour créer des entrées de bloc pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

Vous créez des entrées de bloc pour les domaines et les adresses e-mail directement dans la liste d’autorisation/de blocage du locataire.

> [!NOTE]
> Email messages de ces expéditeurs sont marqués comme *courrier indésirable à haut niveau de confiance* (SCL = 9). Ce qui arrive aux messages est déterminé par la [stratégie anti-courrier indésirable](configure-your-spam-filter-policies.md) qui a détecté le message pour le destinataire. Dans la stratégie anti-courrier indésirable par défaut et les nouvelles stratégies personnalisées, les messages marqués comme courrier indésirable à haut niveau de confiance sont remis par défaut au dossier Junk Email. Dans les [stratégies de sécurité prédéfinies](preset-security-policies.md) Standard et Strict, les messages indésirables à haut niveau de confiance sont mis en quarantaine.
>
> Les utilisateurs de l’organisation ne peuvent pas envoyer de courrier électronique à ces domaines et adresses bloqués. Ils recevront le rapport de non-remise suivant (également appelé NDR ou message de rebond) : `5.7.1  Your message can't be delivered because one or more recipients are blocked by your organization's tenant allow/block list policy.`

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Dans la page **Autoriser/Bloquer la liste** des locataires, vérifiez que l’onglet **Domaines & adresses** est sélectionné.

3. **Onglet Domaines & adresses** , cliquez sur ![l’icône Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

4. Dans le **menu volant Bloquer les domaines & adresses** qui s’affiche, configurez les paramètres suivants :

   - **Domaines & adresses** : entrez une adresse e-mail ou un domaine par ligne, jusqu’à un maximum de 20.

   - **Supprimer l’entrée de bloc après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
     - **1 jour**
     - **7 jours**
     - **30 jours**
     - **N’expirez jamais**
     - **Date spécifique** : la valeur maximale est de 90 jours à partir d’aujourd’hui.

   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

5. Lorsque vous avez terminé, cliquez sur **Ajouter**.

##### <a name="use-powershell-to-create-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour créer des entrées de bloc pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "DomainOrEmailAddress1","DomainOrEmailAddress1",..."DomainOrEmailAddressN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple ajoute une entrée de bloc pour l’adresse e-mail spécifiée qui expire à une date spécifique.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com","test2@anotherattackerdomain.com" -ExpirationDate 8/20/2022
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal"></a>Utilisez le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail Soumissions

Vous ne pouvez pas créer d’entrées d’autorisation pour les domaines et les adresses e-mail directement dans la liste d’autorisation/de blocage du locataire. Au lieu de cela, vous utilisez le portail Soumissions pour <https://security.microsoft.com/reportsubmission> signaler le message sous la forme d’un faux positif. Pour plus d’informations sur les soumissions d’administrateurs, consultez [Utiliser le portail soumissions pour envoyer des courriers indésirables suspects, des hameçonnages, des URL, des messages électroniques légitimes bloqués et des pièces jointes à Microsoft](admin-submission.md).

> [!NOTE]
> Étant donné que Microsoft gère les entrées d’autorisation pour vous, les entrées d’autorisation inutiles pour les domaines et les adresses e-mail seront supprimées. Ce comportement protège votre organisation et permet d’éviter les entrées d’autorisation mal configurées. Si vous n’êtes pas d’accord avec le verdict, vous devrez peut-être ouvrir une demande de support pour déterminer pourquoi un message est toujours considéré comme incorrect.
>
> Si le domaine ou l’adresse e-mail n’a pas encore été bloqué, aucune entrée d’autorisation pour le domaine ou l’adresse e-mail n’est créée.
>
> Dans la plupart des cas où le message a été déterminé comme un faux positif qui a été bloqué de manière incorrecte, l’entrée d’autorisation est supprimée à la date d’expiration spécifiée.
>
> Pour créer des entrées d’autorisation pour les expéditeurs usurpés, consultez la section [Créer des entrées d’autorisation pour les expéditeurs usurpés](#create-allow-entries-for-spoofed-senders) plus loin dans cet article.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné.

3. Sous l’onglet **e-mails** , cliquez sur ![l’icône Envoyer à Microsoft pour l’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type de soumission** : vérifiez que la valeur **Email** est sélectionnée.

   - **Ajoutez l’ID de message réseau ou chargez le fichier e-mail** : sélectionnez l’une des options suivantes :

     - **Ajoutez l’ID de message réseau de messagerie** : il s’agit d’une valeur GUID disponible dans l’en-tête **X-MS-Exchange-Organization-Network-Message-Id** dans le message ou dans l’en-tête **X-MS-Office365-Filtering-Correlation-Id** dans les messages mis en quarantaine.

     - **Charger le fichier e-mail (.msg ou .eml)** : cliquez sur **Parcourir les fichiers**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier .eml ou .msg, puis cliquez sur **Ouvrir**.

   - **Choisissez un destinataire qui a rencontré un problème** : spécifiez le destinataire sur lequel vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si l’e-mail a été bloqué en raison de stratégies d’utilisateur ou d’organisation.

   - **Sélectionnez une raison pour l’envoi à Microsoft** : La sélection **ne doit pas avoir été bloquée (Faux positif),** puis configurez les paramètres suivants :

     - **Autoriser les e-mails avec des attributs similaires (URL, expéditeur, etc.)** : activez ce paramètre![.](../../media/scc-toggle-on.png)

         - **Supprimer l’entrée d’autorisation après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **Date spécifique** : la valeur maximale est de 30 jours à compter d’aujourd’hui.

         - **Autoriser la note d’entrée** : entrez des informations facultatives sur la raison pour laquelle vous autorisez cet e-mail.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

   :::image type="content" source="../../media/admin-submission-email-allow.png" alt-text="Envoyez un e-mail faux positif (bon) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-email-allow.png":::

5. Après quelques instants, l’entrée d’autorisation s’affiche sous l’onglet **Domaines & adresses** de la page **Autoriser/Bloquer le locataire** .

> [!NOTE]
>
> - Les autorisations sont ajoutées pendant le flux de messagerie, en fonction des filtres qui ont déterminé que le message était malveillant. Par exemple, si l’expéditeur et une URL du message ont été déterminés comme étant incorrects, une entrée d’autorisation est créée pour l’expéditeur et une entrée d’autorisation est créée pour l’URL.
> - Lorsque cette entité (adresse de domaine ou e-mail, URL, fichier) est à nouveau rencontrée, tous les filtres associés à cette entité sont ignorés.
> - Pendant le flux de courrier, si les messages du domaine ou de l’adresse e-mail passent d’autres vérifications dans la pile de filtrage, les messages sont remis. Par exemple, si [l’authentification par e-mail](email-validation-and-authentication.md) réussit, un message d’un expéditeur dans l’entrée d’autorisation est remis.

### <a name="use-the-microsoft-365-defender-portal-to-view-allow-or-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour afficher les entrées d’autorisation ou de blocage pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Ou, pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Vérifiez que l’onglet **Domaines & adresses** est sélectionné. Les colonnes suivantes sont disponibles :

   - **Valeur** : domaine ou adresse e-mail.
   - **Action** : valeur **Allow** ou **Block**.
   - **Modifié par**
   - **Dernière mise à jour**
   - **Supprimer le** : date d’expiration.
   - **Remarques**

   Vous pouvez cliquer sur un en-tête de colonne pour trier dans l’ordre croissant ou décroissant.

   Cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** les résultats par **aucune** ou **action**.

   Cliquez sur l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Recherchez**, entrez tout ou partie d’une valeur, puis appuyez sur Entrée pour rechercher une valeur spécifique. Lorsque vous avez terminé, cliquez sur ![l’icône Effacer la recherche.](../../media/m365-cc-sc-close-icon.png) **Effacer la recherche**.

   Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer les résultats. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :

   - **Action** : **Autoriser** et **bloquer**.
   - **N’expirez jamais** : ![basculez dessus.](../../media/scc-toggle-on.png) ou ![désactiver.](../../media/scc-toggle-off.png)
   - **Dernière mise à jour** : Sélectionner à **partir** et **à** des dates.
   - **Remove on**: Select **From** and **To** dates.

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur ![Effacer les filtres **dans**](../../media/m365-cc-sc-clear-filters-icon.png) le menu volant **Filtrer**.

#### <a name="use-powershell-to-view-allow-or-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour afficher ou bloquer des entrées d’autorisation pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType Sender [-Allow] [-Block] [-Entry <Domain or Email address value>] [<-ExpirationDate Date | -NoExpiration>]
```

Cet exemple retourne toutes les entrées d’autorisation et de blocage pour les domaines et les adresses e-mail.

```powershell
Get-TenantAllowBlockListItems -ListType Sender
```

Cet exemple filtre les résultats des entrées de bloc pour les domaines et les adresses e-mail.

```powershell
Get-TenantAllowBlockListItems -ListType Sender -Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-the-microsoft-365-defender-portal-to-modify-allow-or-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour modifier les entrées d’autorisation ou de blocage pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

Lorsque vous modifiez une entrée d’autorisation ou de blocage pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire, vous ne pouvez modifier que la date d’expiration et les notes.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Vérifiez que l’onglet **Domaines & adresses** est sélectionné.

3. Sous l’onglet **Domaines & adresses** , cochez la case de l’entrée à modifier, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Bouton Modifier** qui s’affiche.

4. Les paramètres suivants sont disponibles dans le menu volant **Modifier le domaine & adresses** qui s’affiche :

   - **Supprimez l’entrée d’autorisation après** ou **supprimez l’entrée de bloc après** :
     - Vous pouvez étendre les entrées d’autorisation pendant un maximum de 30 jours après la date de création.
     - Vous pouvez étendre les entrées de bloc pendant un maximum de 90 jours après la date de création ou les définir sur **Jamais expirer**.

   - **Remarque facultative**

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

> [!NOTE]
> Pour autoriser les entrées uniquement, si vous sélectionnez l’entrée en cliquant n’importe où dans la ligne autre que la case à cocher, vous pouvez sélectionner ![l’icône Afficher la soumission.](../../media/m365-cc-sc-view-submission-icon.png) **Affichez la soumission** dans le menu volant des détails qui semble accéder à la page **Soumissions** à l’adresse <https://security.microsoft.com/reportsubmission>.

#### <a name="use-powershell-to-modify-allow-or-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour modifier ou bloquer des entrées d’autorisation pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType Sender <-Ids <Identity value> | -Entries <Value value>> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Cet exemple montre comment modifier la date d’expiration de l’entrée de bloc spécifiée pour les domaines et les adresses e-mail.

```powershell
Set-TenantAllowBlockListItems -ListType Sender -Entries "julia@fabrikam.com" -ExpirationDate "9/1/2022"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-the-microsoft-365-defender-portal-to-remove-allow-or-block-entries-for-domains-and-email-addresses-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour supprimer les entrées d’autorisation ou de blocage pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Vérifiez que l’onglet **Domaines & adresses** est sélectionné.

3. Sous l’onglet **Domaines & adresses** , effectuez l’une des étapes suivantes :

   - Cochez la case de l’entrée à supprimer, puis cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche.
   - Sélectionnez l’entrée à supprimer en cliquant n’importe où dans la ligne autre que la case à cocher. Dans le menu volant des détails qui s’affiche, cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer**.

> [!NOTE]
> Vous pouvez sélectionner plusieurs entrées en cochant chaque case ou toutes les entrées en cochant la case en regard de l’en-tête **de colonne Valeur** .

#### <a name="use-powershell-to-remove-allow-or-block-entries-for-domains-and-email-addresses-from-the-tenant-allowblock-list"></a>Utiliser PowerShell pour supprimer des entrées d’autorisation ou de blocage pour les domaines et les adresses e-mail de la liste d’autorisation/de blocage du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType Sender <-Ids <Identity value> | -Entries <Value value>>
```

Cet exemple supprime l’entrée de bloc spécifiée pour les domaines et les adresses e-mail de la liste d’autorisations/de blocs du locataire.

```powershell
Remove-TenantAllowBlockListItems -ListType Sender -Entries "adatum.com"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="spoofed-senders-in-the-tenant-allowblock-list"></a>Expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

### <a name="create-allow-entries-for-spoofed-senders"></a>Créer des entrées d’autorisation pour les expéditeurs usurpés

Vous disposez des options suivantes pour créer des entrées de bloc pour les expéditeurs usurpés d’identité :

- [Page Soumissions dans le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal)
- Liste verte/bloquée du locataire dans [le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-spoofed-senders-in-the-tenant-allowblock-list) ou dans [PowerShell](#use-powershell-to-create-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list)

> [!NOTE]
> Autoriser les entrées pour les expéditeurs usurpés s’occupent de l’usurpation intra-org, inter-org et DMARC.
>
> Seule la combinaison de l’utilisateur usurpé *et* de l’infrastructure d’envoi définie dans la [paire de domaines](#domain-pair-syntax-for-spoofed-sender-entries) est autorisée à usurper.
>
> Lorsque vous configurez une entrée d’autorisation pour une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans [l’insight d’intelligence de l’usurpation d’identité](learn-about-spoof-intelligence.md).
>
> Les entrées autorisées pour les expéditeurs usurpés n’expirent jamais.

#### <a name="use-the-microsoft-365-defender-portal-to-create-allow-entries-for-spoofed-senders-in-the-submissions-portal"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les expéditeurs usurpés dans le portail Soumissions

L’envoi de messages bloqués par [l’usurpation d’identité](learn-about-spoof-intelligence.md) à Microsoft à partir de la page **Soumissions** ajoute l’expéditeur en tant qu’entrée verte sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisation/de blocage du locataire.

> [!NOTE]
> Lorsque vous remplacez le verdict dans l’insight d’intelligence de l’usurpation d’identité, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisation/de blocage du locataire.
>
> Si l’expéditeur n’a pas été bloqué par l’usurpation d’identité, l’envoi de l’e-mail à Microsoft ne crée pas d’entrée verte dans la liste d’autorisation/de blocage du locataire.

Les instructions pour signaler le message sont presque identiques aux étapes décrites dans [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail Soumissions](#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal).

Les seules différences sont les suivantes :

- **L’entrée Supprimer l’autorisation après** la définition à l’étape 4 n’a aucun sens, car les entrées des expéditeurs usurpés n’expirent jamais.
- Le paramètre **Autoriser la note d’entrée** à l’étape 4 ne s’applique pas aux entrées pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire.

#### <a name="use-the-microsoft-365-defender-portal-to-create-allow-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

Dans la liste d’autorisation/de blocage des locataires, vous pouvez créer des entrées d’autorisation pour les expéditeurs usurpés avant qu’elles ne soient détectées et bloquées par [l’intelligence de l’usurpation d’identité](learn-about-spoof-intelligence.md).

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Dans la page **Autoriser/Bloquer la liste** des locataires, sélectionnez l’onglet **Expéditeurs usurpés** , puis cliquez sur ![l’icône Ajouter.](../../media/m365-cc-sc-create-icon.png) **Ajouter**.

3. Dans le menu volant **Ajouter de nouvelles paires de domaines** qui s’affiche, configurez les paramètres suivants :

   - **Ajoutez des paires de domaines avec des caractères génériques** : entrez une paire de domaines par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, consultez la [syntaxe de la paire de domaines pour les entrées d’expéditeur usurpées](#domain-pair-syntax-for-spoofed-sender-entries) plus loin dans cet article.

   - **Type d’usurpation** d’identité : sélectionnez l’une des valeurs suivantes :
     - **Interne** : l’expéditeur usurpé se trouve dans un domaine qui appartient à votre organisation ( [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Externe** : l’expéditeur usurpé se trouve dans un domaine externe.

   - **Action** : sélectionnez **Autoriser** ou **Bloquer**.

   Lorsque vous avez terminé, cliquez sur **Ajouter**.

##### <a name="use-powershell-to-create-allow-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour créer des entrées d’autorisation pour les expéditeurs usurpés dans la liste d’autorisation/de blocage du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -Identity Default -Action Allow -SpoofedUser <Domain | EmailAddress> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal>
```

Cet exemple crée une entrée d’autorisation pour l’bob@contoso.com de l’expéditeur à partir du contoso.com source.

```powershell
New-TenantAllowBlockListSpoofItems -Identity Default -Action Allow -SendingInfrastructure contoso.com -SpoofedUser bob@contoso.com -SpoofType External
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées de bloc pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

Vous créez des entrées de bloc pour les expéditeurs usurpés directement dans la liste d’autorisations/de blocs du locataire.

> [!NOTE]
> Email messages de ces expéditeurs sont bloqués en tant que *hameçonnage*.
>
> Seule la combinaison de l’utilisateur usurpé *et* de l’infrastructure d’envoi définie dans la [paire de domaines](#domain-pair-syntax-for-spoofed-sender-entries) est bloquée pour l’usurpation d’identité.
>
> Lorsque vous configurez une entrée de bloc pour une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans [l’insight d’intelligence de l’usurpation d’identité](learn-about-spoof-intelligence.md).
>
> Les entrées de bloc pour les expéditeurs usurpés n’expirent jamais.

Les instructions pour signaler le message sont presque identiques aux étapes décrites dans [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail Soumissions](#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal).

La seule différence est : pour la valeur **Action** de l’étape 4, **choisissez Bloquer** au lieu **d’Autoriser**.

#### <a name="use-powershell-to-create-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour créer des entrées de bloc pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -Identity Default -Action Block -SpoofedUser <Domain | EmailAddress> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal>
```

Cet exemple crée une entrée de bloc pour l’expéditeur laura@adatum.com à partir de la source 172.17.17.17/24.

```powershell
New-TenantAllowBlockListSpoofItems -Identity Default -Action Allow -SendingInfrastructure 172.17.17.17/24 -SpoofedUser laura@adatum.com -SpoofType External
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

### <a name="use-the-microsoft-365-defender-portal-to-view-allow-or-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour afficher les entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Ou, pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Vérifiez que l’onglet **Expéditeurs usurpés** est sélectionné. Les colonnes suivantes sont disponibles :

   - **Utilisateur usurpé**
   - **Envoi d’une infrastructure**
   - **Type d’usurpation** d’identité : valeur **interne** ou **externe**.
   - **Action** : valeur **Bloquer** ou **Autoriser**.

   Vous pouvez cliquer sur un en-tête de colonne pour trier dans l’ordre croissant ou décroissant.

   Cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** les résultats par **type None**, **Action** ou **Spoof**.

   Cliquez sur l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Recherchez**, entrez tout ou partie d’une valeur, puis appuyez sur Entrée pour rechercher une valeur spécifique. Lorsque vous avez terminé, cliquez sur ![l’icône Effacer la recherche.](../../media/m365-cc-sc-close-icon.png) **Effacer la recherche**.

   Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer les résultats. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :

   - **Action** : **Autoriser** et **bloquer**.
   - **Type d’usurpation** d’identité : **interne** et **externe**.

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur ![Effacer les filtres **dans**](../../media/m365-cc-sc-clear-filters-icon.png) le menu volant **Filtrer**.

#### <a name="use-powershell-to-view-allow-or-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour afficher les entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

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

### <a name="use-the-microsoft-365-defender-portal-to-modify-allow-or-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utiliser le portail Microsoft 365 Defender pour modifier les entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

Lorsque vous modifiez une entrée d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste Autoriser/Bloquer du locataire, vous pouvez uniquement modifier l’entrée de **Autoriser** à **Bloquer**, ou inversement.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **Expéditeurs usurpés** .

3. Sous **l’onglet Expéditeurs usurpés** , sélectionnez l’entrée à modifier, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Bouton Modifier** qui s’affiche.

4. Dans le menu volant **Modifier l’expéditeur usurpé** qui s’affiche, choisissez **Autoriser** ou **Bloquer**.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="use-powershell-to-modify-allow-or-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour modifier des entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListSpoofItems -Identity Default -Ids <Identity value> -Action <Allow | Block>
```

Cet exemple montre comment faire passer l’entrée de l’expéditeur usurpé de l’autorisation au bloc.

```powershell
Set-TenantAllowBlockListItems -Identity Default -Ids 3429424b-781a-53c3-17f9-c0b5faa02847 -Action Block
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="use-the-microsoft-365-defender-portal-to-remove-allow-or-block-entries-for-spoofed-senders-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour supprimer les entrées d’autorisation ou de blocage pour les expéditeurs usurpés dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **Expéditeurs usurpés** .

3. Sous **l’onglet Expéditeurs usurpés** , sélectionnez l’entrée à supprimer, puis cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche.

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer**.

> [!NOTE]
> Vous pouvez sélectionner plusieurs entrées en cochant chaque case, ou en sélectionnant toutes les entrées en cochant la case en regard de l’en-tête **de colonne utilisateur usurpé** .

#### <a name="use-powershell-to-remove-allow-or-block-entries-for-spoofed-senders-from-the-tenant-allowblock-list"></a>Utiliser PowerShell pour supprimer des entrées d’autorisation ou de blocage pour les expéditeurs usurpés de la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListSpoofItems -Identity domain.com\Default -Ids <Identity value>
```

```powershell
Remove-TenantAllowBlockListSpoofItems -Identity domain.com\Default -Ids d86b3b4b-e751-a8eb-88cc-fe1e33ce3d0c
```

Cet exemple supprime l’expéditeur usurpé spécifié. Vous obtenez la valeur du paramètre Ids à partir de la propriété Identity dans la sortie de Get-TenantAllowBlockListSpoofItems commande.

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).

### <a name="domain-pair-syntax-for-spoofed-sender-entries"></a>Syntaxe de paire de domaines pour les entrées d’expéditeur usurpées

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

L’ajout d’une paire de domaines autorise ou bloque uniquement la *combinaison* de l’utilisateur usurpé *et* de l’infrastructure d’envoi. Il n’autorise pas les e-mails de l’utilisateur usurpé d’identité à partir d’une source quelconque, ni le courrier électronique provenant de la source d’infrastructure d’envoi pour tout utilisateur usurpé.

Par exemple, vous ajoutez une entrée d’autorisation pour la paire de domaines suivante :

- **Domaine** : gmail.com
- **Infrastructure** : tms.mx.com

Seuls les messages de cette paire d’infrastructure de domaine *et* d’envoi sont autorisés à usurper. Les autres expéditeurs qui tentent d’usurper gmail.com ne sont pas autorisés. Les messages des expéditeurs d’autres domaines provenant de tms.mx.com sont vérifiés par l’intelligence par usurpation d’identité.

> [!NOTE]
> Vous ne pouvez pas utiliser de caractères génériques dans l’infrastructure d’envoi.

## <a name="about-impersonated-domains-or-senders"></a>À propos des domaines ou expéditeurs usurpés d’identité

Dans les organisations avec Microsoft Defender pour Office 365, vous ne pouvez pas créer d’entrées d’autorisation dans la liste De locataire/Autoriser/Bloquer pour les messages détectés comme emprunt d’identité par la protection d’emprunt d’identité du [domaine ou de l’expéditeur](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Le signalement d’un message qui a été bloqué de manière incorrecte en tant qu’emprunt d’identité dans le portail <https://security.microsoft.com/reportsubmission>  d’envoi n’ajoute pas l’expéditeur ou le domaine en tant qu’entrée d’autorisation dans la liste d’autorisation/de blocage du locataire.

Au lieu de cela, le domaine ou l’expéditeur est ajouté à la **section Expéditeurs approuvés et domaines** dans la [stratégie anti-hameçonnage](configure-mdo-anti-phishing-policies.md#use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies) qui a détecté le message.

Les instructions pour signaler le message sont identiques aux étapes décrites dans [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail Soumissions](#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal).

> [!NOTE]
> Actuellement, l’emprunt d’identité Graph n’est pas pris en charge à partir d’ici.

## <a name="related-articles"></a>Articles connexes

- [Utilisez le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL, des e-mails légitimes bloqués et des pièces jointes à Microsoft](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Autoriser ou bloquer des fichiers dans la liste d’autorisations/de blocs du locataire](allow-block-files.md)
- [Autoriser ou bloquer des URL dans la liste d’autorisations/de blocs du locataire](allow-block-urls.md)
