---
title: Supprimer un domaine
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Découvrez comment supprimer un ancien domaine de Microsoft 365 et déplacer des utilisateurs et des groupes vers un autre domaine.
ms.openlocfilehash: 39f8d97abb3a424251d6847da02f0dcc58baff31
ms.sourcegitcommit: 0d709e9ab0d8d56c5fc11a921298f82e40e122c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50114008"
---
# <a name="remove-a-domain"></a>Supprimer un domaine

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet&preserve-view=true).

::: moniker-end
  
 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Supprimez-vous votre domaine car vous souhaitez l’ajouter à un autre plan d’abonnement Microsoft 365 ? Ou souhaitez-vous annuler votre abonnement ? Vous pouvez [modifier votre plan ou abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) ou [annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).
  
### <a name="step-1-move-users-to-another-domain"></a>Étape 1 : Déplacer des utilisateurs vers un autre domaine

#### <a name="move-users"></a>Déplacer des utilisateurs

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre administratif</a>.      

2. Sélectionnez  > **Utilisateurs actifs.**

3. Sélectionnez les cases en de côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. Sélectionnez **Plus d’options** (**...**), en haut de la page, puis choisissez Modifier **les domaines.**

5. Dans le **volet Modifier les domaines,** sélectionnez un autre domaine.

Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

::: moniker range="o365-germany"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">centre administratif</a>.        

2. Sélectionnez  > **Utilisateurs actifs.**

3. Sélectionnez les cases en de côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. At the top of the page, choose **More** > **Edit domains**.

5. Dans le **volet Modifier les domaines,** sélectionnez un autre domaine.
  
Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.        

2. Sélectionnez  > **Utilisateurs actifs.**

3. Sélectionnez les cases en de côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. At the top of the page, choose **More** > **Edit domains**.

5. Dans le **volet Modifier les domaines,** sélectionnez un autre domaine.
  
Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

#### <a name="move-yourself"></a>Se déplacer vous-même

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.      

2. Go to **Users** \> **Active Users**, and select your account from the list.

3. Sous **l’onglet** Compte, **sélectionnez Gérer** le nom d’utilisateur, puis choisissez un autre domaine.
  
4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **sélectionnez Se sortir.**

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

::: moniker range="o365-germany"

1. Go to **Users** \> **Active Users**, and select your name in the list.

2. Dans la section **Nom d’utilisateur/Courrier** électronique, **sélectionnez Modifier,** puis choisissez un autre domaine.

3. Sélectionnez **Définir comme principal** > **Save** > **Close**.
  
4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **sélectionnez Se sortir.**

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

::: moniker range="o365-21vianet"

1. Go to **Users** \> **Active Users**, and select your name in the list.

2. Dans la section **Nom d’utilisateur/Courrier** électronique, **sélectionnez Modifier,** puis choisissez un autre domaine.

3. Sélectionnez **Définir comme principal** > **Save** > **Close**.
  
4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **sélectionnez Se sortir.**

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

### <a name="step-2-move-groups-to-another-domain"></a>Étape 2 : Déplacer des groupes vers un autre domaine

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Groupes.</a>
  
2. Sélectionnez le nom du groupe, puis sous **l’onglet Général** sous **Adresse de messagerie, Principal,** sélectionnez **Modifier**.

3. Utilisez la liste de listes pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration,</a>allez à la page  > **Groupes.**

2. Sélectionnez le nom du groupe, puis **sélectionnez Modifier** en plus du **nom.**

3. Utilisez la liste de listes pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration,</a>allez à la page  > **Groupes.**

2. Sélectionnez le nom du groupe, puis **sélectionnez Modifier** en plus du **nom.**

3. Utilisez la liste de listes pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

### <a name="step-3-remove-the-old-domain"></a>Étape 3 : Supprimer l’ancien domaine

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, allez à la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">Domaines d’installation.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, allez à la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines d’installation.</a>

::: moniker-end
  
2. Dans la page **Domaines,** sélectionnez le domaine à supprimer.

3. Dans le volet droit, sélectionnez **Supprimer.**

4. Suivez les invites supplémentaires, puis sélectionnez **Fermer.**

## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Combien de temps faut-il pour qu'un domaine soit supprimé ?

La suppression d’un domaine par Microsoft 365 peut prendre jusqu’à 5 minutes s’il n’est pas référencé dans un grand nombre d’endroits tels que les groupes de sécurité, les listes de distribution, les utilisateurs et les groupes Microsoft 365. Si plusieurs références utilisent le domaine, la suppression du domaine peut prendre plusieurs heures (une journée).
  
Si vous avez des centaines voire des milliers d'utilisateurs, utilisez PowerShell pour interroger tous les utilisateurs, puis déplacez-les vers un autre domaine. Sinon, il est possible que quelques-uns des utilisateurs manquent dans l'interface utilisateur. De plus, lorsque vous voudrez supprimer le domaine, vous ne pourrez pas et vous ne saurez pas pourquoi. Pour en savoir plus, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).
  
## <a name="still-need-help"></a>Encore besoin d’aide ?

::: moniker range="o365-worldwide"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« onmicrosoft.com »](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) de votre compte. Lorsque vous supprimez un domaine, les comptes d’utilisateurs reviennent à l’adresse « .onmicrosoft.com » en tant que SMTP/UserprincipalName principal.
  
Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../contact-support-for-business-products.md) et nous vous aiderons à effectuer cette tâche.
  
::: moniker-end

## <a name="related-articles"></a>Articles connexes

[Foire aux questions domaines](../setup/domains-faq.yml)

[Basculer vers une autre offre Microsoft 365 pour les entreprises](../../commerce/subscriptions/switch-to-a-different-plan.md)

[Annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md)
