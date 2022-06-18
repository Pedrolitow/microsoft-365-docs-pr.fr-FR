---
title: Gérer les autorisations et les blocs dans la liste d’autorisations/de blocs du locataire
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
description: Découvrez comment gérer les autorisations et les blocs dans la liste d’autorisations/blocs du locataire dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dc32e6827e9751dc72d28b8eff79d1966f43f646
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159770"
---
# <a name="manage-your-allows-and-blocks-in-the-tenant-allowblock-list"></a>Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

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

- Pour les expéditeurs, les URL et les hachages de fichiers, la liste d’autorisations/blocs du locataire autorise 500 entrées chacune pour les blocs et les autorisations, ce qui en fait un total de 1 000 entrées. Pour l’usurpation d’identité (expéditeurs usurpés), le nombre total d’entrées autorisées est de 1 024.

- Le nombre maximal de caractères pour chaque entrée est le suivant :
  - Hachages de fichier = 64
  - URL = 250

- Une entrée doit être active dans les 30 minutes.

- Par défaut, les entrées de la liste d’autorisations/de blocs du locataire expirent après 30 jours. Vous pouvez spécifier une date ou les définir pour qu’elles n’expirent jamais (pour le type de bloc d’entrées).

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans Exchange Online pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter et supprimer des valeurs de la liste d’autorisations/de blocs du locataire, vous devez être membre de
    - **Groupe de rôles Gestion de l’organisation** ou **Administrateur de la sécurité** (**rôle Administrateur de la sécurité**)
    - Groupe **de rôles Opérateur de sécurité** (**Tenant AllowBlockList Manager**).
  - Pour accéder en lecture seule à la liste d’autorisations/de blocs de locataire, vous devez être membre de
    - **Groupe de rôles Lecteur global**
    - **Groupe de rôles Lecteur de sécurité**
    - **Groupe de rôles de configuration Affichage uniquement**

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises *et* les autorisations pour les autres fonctionnalités de [Microsoft 365](../../admin/add-users/about-admin-roles.md).
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="configure-the-tenant-allowblock-list"></a>Configurer la liste d’autorisations/blocages du locataire

### <a name="use-the-microsoft-365-defender-portal"></a>Utiliser le portail Microsoft 365 Defender

Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Utiliser Exchange Online PowerShell ou PowerShell EOP autonome

Pour autoriser ou bloquer des e-mails, consultez [Autoriser ou bloquer les e-mails à l’aide de la liste d’autorisation/de blocage du locataire](allow-block-email-spoof.md).

Pour autoriser ou bloquer des fichiers, consultez [Autoriser ou bloquer des fichiers à l’aide de la liste d’autorisations/de blocs du locataire](allow-block-files.md).

Pour autoriser ou bloquer des URL, consultez [Autoriser ou bloquer des URL à l’aide de la liste d’autorisations/de blocs du locataire](allow-block-urls.md).

### <a name="what-to-expect-after-you-add-an-allow-or-block-entry"></a>À quoi vous attendre après l’ajout d’une entrée d’autorisation ou de blocage

Une fois que vous avez ajouté une entrée d’autorisation via le portail Soumissions ou une entrée de bloc dans la liste d’autorisation/de blocage du locataire, l’entrée doit commencer à fonctionner immédiatement.

Nous vous recommandons de laisser les entrées expirer automatiquement après 30 jours pour voir si le système a découvert l’autorisation ou le bloc. Si ce n’est pas le cas, vous devez faire une autre entrée pour donner au système encore 30 jours pour apprendre.

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Afficher les entrées dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Policies & rules** \> **Threat Policies** \> **Tenant Allow/Block Lists** dans la section **Règles**. Ou, pour accéder directement à la page **Autoriser/Bloquer les listes de locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet souhaité. Les colonnes disponibles dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs** :
     - **Valeur** : domaine ou adresse e-mail de l’expéditeur.
     - **Action** : valeur **Allow** ou **Block**.
     - **Modifié par**
     - **Dernière mise à jour**
     - **Supprimer le**
     - **Notes**
   - **Usurpation**
     - **Utilisateur usurpé**
     - **Envoi d’une infrastructure**
     - **Type d’usurpation** d’identité : valeur **interne** ou **externe**.
     - **Action** : valeur **Bloquer** ou **Autoriser**.
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

   Vous pouvez cliquer sur un en-tête de colonne pour trier dans l’ordre croissant ou décroissant.

   Vous pouvez cliquer sur **Groupe** pour regrouper les résultats. Les valeurs disponibles dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs** : vous pouvez regrouper les résultats par **action**.
   - **Usurpation d’identité** : vous pouvez regrouper les résultats par **type Action** ou **Usurpation d’identité**.
   - **URL** : vous pouvez regrouper les résultats par **action**.
   - **Fichiers** : vous pouvez regrouper les résultats par **action**.

   Cliquez sur **Rechercher**, entrez tout ou partie d’une valeur, puis appuyez sur Entrée pour rechercher une valeur spécifique. Lorsque vous avez terminé, cliquez sur ![l’icône Effacer la recherche.](../../media/m365-cc-sc-close-icon.png) **Effacer la recherche**.

   Cliquez sur **Filtrer** pour filtrer les résultats. Les valeurs disponibles dans le menu volant **Filtre** qui s’affiche dépendent de l’onglet que vous avez sélectionné :

   - **Expéditeurs**
     - **Action**
     - **N’expirez jamais**
     - **Dernière date de mise à jour**
     - **Supprimer le**
   - **Usurpation**
     - **Action**
     - **Type d’usurpation d’identité**
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

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur **Filtrer**, puis dans le menu volant **Filtre** qui s’affiche, cliquez sur **Effacer les filtres**.

## <a name="modify-entries-in-the-tenant-allowblock-list"></a>Modifier les entrées dans la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet qui contient le type d’entrée à modifier :
   - **Expéditeurs**
   - **Usurpation**
   - **Url**
   - **Files**

3. Sélectionnez l’entrée à modifier, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**. Les valeurs que vous pouvez modifier dans le menu volant qui s’affiche dépendent de l’onglet que vous avez sélectionné à l’étape précédente :
   - **Expéditeurs**
     - **N’expirez jamais** et/ou date d’expiration.
     - **Remarque facultative**
   - **Usurpation**
     - **Action** : vous pouvez modifier la valeur en **Allow** ou **Block**.
   - **Url**
     - **N’expirez jamais** et/ou date d’expiration.
     - **Remarque facultative**
   - **Files**
     - **N’expirez jamais** et/ou date d’expiration.
     - **Remarque facultative**

    Notez que les valeurs des expéditeurs, des URL et des fichiers n’expirent jamais uniquement pour les entrées bloquées. 

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

> [!NOTE]
> Vous ne pouvez étendre que 30 jours après la date de création. Les blocs peuvent être étendus jusqu’à 90 jours, mais contrairement aux autorisations, ils peuvent également être définis sur Ne jamais expirer.

## <a name="remove-entries-from-the-tenant-allowblock-list"></a>Supprimer des entrées de la liste d’autorisations/de blocs du locataire

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la section Stratégies **& règles sur les règles** \> de **menaces** \> **,** section \> **Listes d’autorisations/listes de blocs du locataire**. Ou, pour accéder directement à la page **Autoriser/Bloquer la liste des locataires** , utilisez <https://security.microsoft.com/tenantAllowBlockList>.

2. Sélectionnez l’onglet qui contient le type d’entrée à supprimer :
   - **Expéditeurs**
   - **Usurpation**
   - **Url**
   - **Files**

3. Sélectionnez l’entrée à supprimer, puis cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**.

4. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur **Supprimer**.

## <a name="related-articles"></a>Articles connexes

- [Autoriser ou bloquer des fichiers dans la liste d’autorisations/de blocs du locataire](allow-block-files.md)
- [Autoriser ou bloquer des e-mails dans la liste d’autorisations/blocages du locataire](allow-block-email-spoof.md)
- [Autoriser ou bloquer des URL dans la liste d’autorisations/de blocs du locataire](allow-block-urls.md)