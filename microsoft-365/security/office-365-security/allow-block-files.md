---
title: Autoriser ou bloquer des fichiers utilisant la liste Autoriser/Bloquer des clients
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
description: Les administrateurs peuvent apprendre à autoriser ou bloquer des fichiers dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 61d9a3f2c1ae370183d88afce0077ecaea6a422c
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67497113"
---
# <a name="allow-or-block-files-using-the-tenant-allowblock-list"></a>Autoriser ou bloquer des fichiers utilisant la liste Autoriser/Bloquer des clients

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article explique comment gérer les entrées d’autorisation et de blocage de fichiers disponibles dans la liste d’autorisations/de blocs du locataire. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

Vous gérez les entrées d’autorisation et de blocage des fichiers dans le portail Microsoft 365 Defender ou dans Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>. Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Vous spécifiez des fichiers à l’aide de la valeur de hachage SHA256 du fichier. Pour rechercher la valeur de hachage SHA256 d’un fichier dans Windows, exécutez la commande suivante dans une invite de commandes :

  ```DOS
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Un exemple de valeur est `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Les valeurs de hachage perceptuel (pHash) ne sont pas prises en charge.

- Pour les fichiers, le nombre maximal d’entrées autorisées est de 500 et le nombre maximal d’entrées de bloc est de 500 (1 000 entrées de fichier au total).

- Vous pouvez entrer un maximum de 64 caractères dans une entrée de fichier.

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

## <a name="create-block-entries-for-files"></a>Créer des entrées de bloc pour les fichiers

Vous disposez des options suivantes pour créer des entrées de bloc pour les fichiers :

- [Page Soumissions dans le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-block-entries-for-files-in-the-submissions-portal)
- Liste verte/bloquée du locataire dans [le portail Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-block-entries-for-files-in-the-tenant-allowblock-list) ou dans [PowerShell](#use-powershell-to-create-block-entries-for-files-in-the-tenant-allowblock-list)

### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-files-in-the-submissions-portal"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées de bloc pour les fichiers dans le portail Soumissions

Lorsque vous utilisez le portail Soumissions pour <https://security.microsoft.com/reportsubmission> signaler les fichiers comme ayant **dû être bloqués (Faux négatif),** vous pouvez sélectionner **Bloquer ce fichier** pour ajouter une entrée de bloc pour le fichier dans la liste d’autorisation/de blocage du locataire.

Pour obtenir des instructions, consultez [l’article Signaler les pièces jointes contestables à Microsoft](admin-submission.md#report-questionable-email-attachments-to-microsoft).

### <a name="use-the-microsoft-365-defender-portal-to-create-block-entries-for-files-in-the-tenant-allowblock-list"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées de bloc pour les fichiers dans la liste d’autorisations/de blocs du locataire

Vous pouvez créer des entrées de bloc pour les fichiers directement dans la liste d’autorisation/de blocage du locataire.

Email messages qui contiennent ces fichiers bloqués sont bloqués en tant que *programmes malveillants*.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Dans la page **Autoriser/Bloquer la liste des locataires** , sélectionnez l’onglet **Fichiers** .

3. Sous l’onglet **Fichiers** , cliquez sur ![l’icône Bloquer.](../../media/m365-cc-sc-create-icon.png) **Bloquer**.

4. Dans le menu volant **Bloquer les fichiers** qui s’affiche, configurez les paramètres suivants :

   - **Ajouter des hachages de fichier** : entrez une valeur de hachage SHA256 par ligne, jusqu’à un maximum de 20.

   - **Supprimer l’entrée de bloc après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
     - **1 jour**
     - **7 jours**
     - **30 jours**
     - **N’expirez jamais**
     - **Date spécifique** : la valeur maximale est de 90 jours à partir d’aujourd’hui.

   - **Remarque facultative** : entrez du texte descriptif pour les entrées.

5. Lorsque vous avez terminé, cliquez sur **Ajouter**.

#### <a name="use-powershell-to-create-block-entries-for-files-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour créer des entrées de bloc pour les fichiers dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <FileHash> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple ajoute une entrée de fichier de bloc pour les fichiers spécifiés qui n’expirent jamais.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="use-the-microsoft-365-defender-portal-to-create-allow-entries-for-files-in-the-submissions-portal"></a>Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les fichiers dans le portail Soumissions

Vous ne pouvez pas créer d’entrées d’autorisation pour les fichiers directement dans la liste d’autorisation/de blocage du locataire. Au lieu de cela, vous utilisez le portail Soumissions pour <https://security.microsoft.com/reportsubmission> signaler le message sous la forme d’un faux positif. Pour plus d’informations sur les soumissions d’administrateurs, consultez [Utiliser le portail soumissions pour envoyer des courriers indésirables suspects, des hameçonnages, des URL, des messages électroniques légitimes bloqués et des pièces jointes à Microsoft](admin-submission.md).

Le fait de signaler le fichier sous la forme d’un faux positif sur la page Soumissions ajoute une entrée d’autorisation pour le fichier dans la liste d’autorisations/de **blocs** du locataire.

> [!IMPORTANT]
> Étant donné que Microsoft gère les entrées d’autorisation pour vous, les entrées d’autorisation inutiles pour les fichiers sont supprimées. Ce comportement protège votre organisation et permet d’éviter les entrées d’autorisation mal configurées. Si vous n’êtes pas d’accord avec le verdict, vous devrez peut-être ouvrir une demande de support pour déterminer pourquoi un fichier est toujours considéré comme incorrect.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions**, sélectionnez l’onglet **Email pièces jointes**.

3. Sous l’onglet **Email pièces jointes**, cliquez sur ![l’icône Envoyer à Microsoft pour l’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type d’envoi** : vérifiez la valeur **Email pièce jointe** est sélectionnée.

   - **Fichier** : cliquez sur **Parcourir les fichiers** pour rechercher et sélectionner le fichier à envoyer.

   - **Sélectionnez une raison pour l’envoi à Microsoft** : La sélection **ne doit pas avoir été bloquée (Faux positif),** puis configurez les paramètres suivants :

     - **Autoriser ce fichier** : activez ce paramètre ![activé](../../media/scc-toggle-on.png).

         - **Supprimer l’entrée d’autorisation après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **Date spécifique** : la valeur maximale est de 30 jours à compter d’aujourd’hui.

         - **Note d’entrée d’autorisation** : entrez des informations facultatives sur la raison pour laquelle vous autorisez ce fichier.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

   :::image type="content" source="../../media/admin-submission-file-allow.png" alt-text="Envoyez une pièce jointe de faux positif (bon) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-file-allow.png":::

5. Après quelques instants, l’entrée d’autorisation s’affiche sous l’onglet **Fichiers** de la page **Autoriser/Bloquer** la liste des locataires.

> [!NOTE]
> Lorsque le fichier est à nouveau rencontré, il n’est pas envoyé pour la détonation des [pièces jointes sécurisées ou les vérifications](safe-attachments.md) de la réputation des fichiers, et tous les autres filtres basés sur des fichiers sont ignorés. Pendant le flux de courrier, si les messages contenant le fichier passent d’autres vérifications non liées aux fichiers dans la pile de filtrage, les messages sont remis.

## <a name="use-the-microsoft-365-defender-portal-to-view-allow-or-block-entries-for-files-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour afficher les entrées d’autorisation ou de blocage des fichiers dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Ou, pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **Fichiers** . Les colonnes suivantes sont disponibles :

   - **Valeur** : hachage du fichier.
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

### <a name="use-powershell-to-view-allow-or-block-entries-for-files-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour afficher les entrées d’autorisation ou de blocage pour les fichiers dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType FileHash [-Allow] [-Block] [-Entry <FileHashValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Cet exemple retourne tous les fichiers autorisés et bloqués.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash
```

Cet exemple retourne des informations pour la valeur de hachage de fichier spécifiée.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Cet exemple filtre les résultats par fichiers bloqués.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Block
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="use-the-microsoft-365-defender-portal-to-modify-allow-or-block-entries-for-files-in-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour modifier les entrées d’autorisation ou de blocage des fichiers dans la liste d’autorisation/de blocage du locataire

Lorsque vous modifiez une entrée de fichier d’autorisation ou de blocage dans la liste d’autorisations/de blocs de locataire, vous pouvez uniquement modifier la date d’expiration et les notes.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionner l’onglet **Fichiers**

3. Sous l’onglet **Fichiers** , cochez la case de l’entrée à modifier, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Bouton Modifier** qui s’affiche.

4. Les paramètres suivants sont disponibles dans le menu volant **Modifier le fichier** qui s’affiche :

   - **Supprimez l’entrée d’autorisation après** ou **supprimez l’entrée de bloc après** :
     - Vous pouvez étendre les entrées d’autorisation pendant un maximum de 30 jours après la date de création.
     - Vous pouvez étendre les entrées de bloc pendant un maximum de 90 jours après la date de création ou les définir sur **Jamais expirer**.

   - **Remarque facultative**

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

> [!NOTE]
> Pour autoriser les entrées uniquement, si vous sélectionnez l’entrée en cliquant n’importe où dans la ligne autre que la case à cocher, vous pouvez sélectionner ![l’icône Afficher la soumission.](../../media/m365-cc-sc-view-submission-icon.png) **Affichez la soumission** dans le menu volant des détails qui semble accéder à la page **Soumissions** à l’adresse <https://security.microsoft.com/reportsubmission>.

### <a name="use-powershell-to-modify-allow-or-block-entries-for-files-in-the-tenant-allowblock-list"></a>Utiliser PowerShell pour modifier des entrées d’autorisation ou de blocage pour les fichiers dans la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <FileHash> <-Ids <Identity value> | -Entries <Value value>> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Cet exemple montre comment modifier la date d’expiration de l’entrée de bloc de fichier spécifiée.

```powershell
Set-TenantAllowBlockListItems -ListType FileHash -Entries "27c5973b2451db9deeb01114a0f39e2cbcd2f868d08cedb3e210ab3ece102214" -ExpirationDate "9/1/2022"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="use-the-microsoft-365-defender-portal-to-remove-allow-or-block-entries-for-files-from-the-tenant-allowblock-list"></a>Utilisez le portail Microsoft 365 Defender pour supprimer les entrées d’autorisation ou de blocage des fichiers de la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet **Fichiers** .

3. Sous l’onglet **Fichiers** , effectuez l’une des étapes suivantes :

   - Cochez la case de l’entrée à supprimer, puis cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche.
   - Sélectionnez l’entrée à supprimer en cliquant n’importe où dans la ligne autre que la case à cocher. Dans le menu volant des détails qui s’affiche, cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer**.

> [!NOTE]
> Vous pouvez sélectionner plusieurs entrées en cochant chaque case ou toutes les entrées en cochant la case en regard de l’en-tête **de colonne Valeur** .

### <a name="use-powershell-to-remove-allow-or-block-entries-for-files-from-the-tenant-allowblock-list"></a>Utiliser PowerShell pour supprimer des entrées d’autorisation ou de blocage pour les fichiers de la liste d’autorisations/de blocs du locataire

Dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType FileHash <-Ids <Identity value> | -Entries <Value value>>
```

Cet exemple montre comment supprimer le bloc de fichiers spécifié de la liste d’autorisations/de blocs du locataire.

```powershell
Remove-TenantAllowBlockListItems -ListType FileHash -Entries "27c5973b2451db9deeb01114a0f39e2cbcd2f868d08cedb3e210ab3ece102214"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>Articles connexes

- [Utilisez le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL, des e-mails légitimes bloqués et des pièces jointes à Microsoft](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Autoriser ou bloquer des e-mails dans la liste d’autorisations/blocages du locataire](allow-block-email-spoof.md)
- [Autoriser ou bloquer des URL dans la liste d’autorisations/de blocs du locataire](allow-block-urls.md)
