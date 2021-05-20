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
description: Découvrez comment supprimer un ancien domaine de votre Microsoft 365 déplacer les utilisateurs et les groupes vers un autre domaine.
ms.openlocfilehash: 3586cc8b288b77725c0dd3484629688e98e0a218
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572116"
---
# <a name="remove-a-domain"></a>Supprimer un domaine
  
 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Supprimez-vous votre domaine parce que vous souhaitez l’ajouter à un autre plan Microsoft 365'abonnement ? Ou souhaitez-vous annuler votre abonnement ? Vous pouvez [modifier votre plan ou abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) ou [annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).
  
### <a name="step-1-move-users-to-another-domain"></a>Étape 1 : Déplacer les utilisateurs vers un autre domaine

#### <a name="move-users"></a>Déplacer les utilisateurs

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre administratif</a>.      

2. Sélectionnez **utilisateurs** > **utilisateurs actifs**.

3. Sélectionnez les cases à côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, puis choisissez **les domaines De changement**.

5. Dans le **volet Domaines de** modification, sélectionnez un domaine différent.

Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

::: moniker range="o365-germany"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">centre administratif</a>.        

2. Sélectionnez **utilisateurs** > **utilisateurs actifs**.

3. Sélectionnez les cases à côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, choisissez **plus de** > **domaines Edit**.

5. Dans le **volet Modifier les domaines,** sélectionnez un domaine différent.
  
Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.        

2. Sélectionnez **utilisateurs** > **utilisateurs actifs**.

3. Sélectionnez les cases à côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, choisissez **plus de** > **domaines Edit**.

5. Dans le **volet Modifier les domaines,** sélectionnez un domaine différent.
  
Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

#### <a name="move-yourself"></a>Bougez-vous

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.      

2. Allez aux **utilisateurs** \> **utilisateurs actifs**, et sélectionnez votre compte à partir de la liste.

3. Sur **l’onglet** Compte, sélectionnez **Gérer le nom d’utilisateur,** puis choisissez un domaine différent.
  
4. En haut, sélectionnez le nom de votre compte, puis **sélectionnez Dé inscrivez-vous**.

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

::: moniker range="o365-germany"

1. Allez aux **utilisateurs** \> **utilisateurs actifs**, et sélectionnez votre nom dans la liste.

2. Dans la section **Nom d’utilisateur /** E-mail, **sélectionnez** Modifier, puis choisissez un domaine différent.

3. Sélectionnez **Définir comme principal** Enregistrer >  > **fermer**.
  
4. En haut, sélectionnez le nom de votre compte, puis **sélectionnez Dé inscrivez-vous**.

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez aux **utilisateurs** \> **utilisateurs actifs**, et sélectionnez votre nom dans la liste.

2. Dans la section **Nom d’utilisateur /** E-mail, **sélectionnez** Modifier, puis choisissez un domaine différent.

3. Sélectionnez **Définir comme principal** Enregistrer >  > **fermer**.
  
4. En haut, sélectionnez le nom de votre compte, puis **sélectionnez Dé inscrivez-vous**.

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

### <a name="step-2-move-groups-to-another-domain"></a>Étape 2 : Déplacer les groupes vers un autre domaine

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, rendez-vous sur la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Groupes Groupes.</a>
  
2. Sélectionnez le nom du groupe, puis sur **l’onglet Général sous** adresse **e-mail, Primaire**, sélectionnez **Modifier**.

3. Utilisez la liste de drop-down pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">admin</a>, allez à la page **Groupes** > **Groupes.**

2. Sélectionnez le nom du groupe, puis sélectionnez **Modifier à** côté du **nom**.

3. Utilisez la liste de drop-down pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">admin</a>, allez à la page **Groupes** > **Groupes.**

2. Sélectionnez le nom du groupe, puis sélectionnez **Modifier à** côté du **nom**.

3. Utilisez la liste de drop-down pour choisir un autre domaine.

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
  
2. Sur la page **Domaines,** sélectionnez le domaine que vous souhaitez supprimer.

3. Dans le volet droit, sélectionnez **Supprimer**.

4. Suivez toutes les invites supplémentaires, puis sélectionnez **Fermer**.

## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Combien de temps faut-il pour qu'un domaine soit supprimé ?

Il peut prendre aussi peu que 5 minutes pour Microsoft 365 de supprimer un domaine si elle n’est pas référencée dans un grand nombre d’endroits tels que les groupes de sécurité, listes de distribution, utilisateurs et groupes Microsoft 365. Si plusieurs références utilisent le domaine, la suppression du domaine peut prendre plusieurs heures (une journée).
  
Si vous avez des centaines voire des milliers d'utilisateurs, utilisez PowerShell pour interroger tous les utilisateurs, puis déplacez-les vers un autre domaine. Sinon, il est possible que quelques-uns des utilisateurs manquent dans l'interface utilisateur. De plus, lorsque vous voudrez supprimer le domaine, vous ne pourrez pas et vous ne saurez pas pourquoi. Pour en savoir plus, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).
  
## <a name="still-need-help"></a>Vous avez encore besoin d’aide ?

::: moniker range="o365-worldwide"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« onmicrosoft.com »](../setup/domains-faq.yml) de votre compte. Lorsque vous supprimez un domaine, les comptes utilisateur reviennent à l’adresse « .onmicrosoft.com » comme le Nom SMTP/Userprincipal Primaire.
  
Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../../business-video/get-help-support.md) et nous vous aiderons à effectuer cette tâche.
  
::: moniker-end

## <a name="related-articles"></a>Articles connexes

[Foire aux questions domaines](../setup/domains-faq.yml)

[Basculer vers une autre offre Microsoft 365 pour les entreprises](../../commerce/subscriptions/switch-to-a-different-plan.md)

[Annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md)