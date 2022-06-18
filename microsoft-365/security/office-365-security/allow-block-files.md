---
title: Autoriser ou bloquer des fichiers à l’aide de la liste d’autorisations/de blocs du locataire
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
description: Les administrateurs peuvent apprendre à autoriser ou bloquer des fichiers dans la liste d’autorisation/de blocage du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 65f5a0706b49312ee4b12a626f7ecd0d600c93df
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159799"
---
# <a name="allow-or-block-files-using-the-tenant-allowblock-list"></a>Autoriser ou bloquer des fichiers à l’aide de la liste d’autorisations/de blocs du locataire

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous pouvez utiliser le portail Microsoft 365 Defender ou PowerShell pour autoriser ou bloquer des fichiers dans la liste d’autorisation/de blocage du locataire.

## <a name="create-block-file-entries"></a>Créer des entrées de fichier de bloc 

### <a name="use-microsoft-365-defender"></a>Utiliser Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

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
> Les e-mails contenant ces fichiers sont bloqués en tant que _programmes malveillants_.

### <a name="use-powershell"></a>Utiliser PowerShell

Pour ajouter des entrées de fichier de bloc dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListItems -ListType <FileHash> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Cet exemple ajoute une entrée de fichier de bloc pour les fichiers spécifiés qui n’expirent jamais.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-file-entries"></a>Créer des entrées de fichier autorisées

### <a name="use-microsoft-365-defender"></a>Utiliser Microsoft 365 Defender

Autoriser les fichiers sur la page **Soumissions** dans Microsoft 365 Defender.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Actions & soumissions** \> **soumissions**. Ou, pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , sélectionnez l’onglet **Pièces jointes de l’e-mail** , puis cliquez sur ![Envoyer à Microsoft pour l’icône d’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

3. Utilisez le menu volant **Envoyer à Microsoft pour passer en revue** l’envoi d’un message en ajoutant le fichier ou les fichiers.

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft**, sélectionnez **Ne doit pas avoir été bloquée (faux positif).**

5. Activez les **fichiers Autoriser comme cette** option.

6. Dans la liste déroulante **Supprimer après** , spécifiez la durée pendant laquelle vous souhaitez que l’option d’autorisation fonctionne.

7. Lorsque vous avez terminé, cliquez sur le bouton **Envoyer** .

  :::image type="content" source="../../media/submit-email-for-analysis.png" alt-text="Envoyer un e-mail à des fins d’analyse." lightbox="../../media/submit-email-for-analysis.png":::

> [!NOTE]
>
> Lorsque le fichier est à nouveau rencontré, il n’est pas envoyé pour des vérifications de détonation ou de réputation, et tous les autres filtres basés sur des fichiers sont ignorés. Pendant le flux de courrier, si le reste des filtres trouve l’e-mail qui contient le fichier à nettoyer, l’e-mail est remis.

## <a name="view-file-entries"></a>Afficher les entrées de fichier 

Pour afficher les entrées de fichier de bloc dans la liste d’autorisation/de blocage du locataire, utilisez la syntaxe suivante :

```powershell
Get-TenantAllowBlockListItems -ListType <FileHash> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Cet exemple retourne des informations pour la valeur de hachage de fichier spécifiée.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-file-entries"></a>Modifier les entrées de fichier

Pour modifier les entrées de fichier d’autorisation ou de blocage dans la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Set-TenantAllowBlockListItems -ListType <FileHash> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-file-entries"></a>Supprimer des entrées de fichier 

Pour supprimer les entrées de fichier d’autorisation ou de blocage de la liste d’autorisations/de blocs du locataire, utilisez la syntaxe suivante :

```powershell
Remove-TenantAllowBlockListItems -ListType <FileHash> -Ids <"Id1","Id2",..."IdN">
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>Articles connexes

- [Envois par l’administrateur](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Autoriser ou bloquer des e-mails dans la liste d’autorisations/blocages du locataire](allow-block-email-spoof.md)
- [Autoriser ou bloquer des URL dans la liste d’autorisations/de blocs du locataire](allow-block-urls.md)