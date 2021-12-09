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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Découvrez comment supprimer un ancien domaine d’Microsoft 365 et déplacer des utilisateurs et des groupes vers un autre domaine ou annuler votre abonnement.
ms.openlocfilehash: 3b6bd67c8678d4be2b483865ee76574fd727cda5
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61370007"
---
# <a name="remove-a-domain"></a>Supprimer un domaine

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Supprimez-vous votre domaine, car vous souhaitez l’ajouter à un autre plan Microsoft 365 abonnement ? Ou souhaitez-vous annuler votre abonnement ? Vous pouvez [modifier votre plan ou abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) ou [annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).

### <a name="step-1-move-users-to-another-domain"></a>Étape 1 : Déplacer des utilisateurs vers un autre domaine

#### <a name="move-users"></a>Déplacer des utilisateurs

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre administratif</a>.      

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.      

::: moniker-end

2. Sélectionnez   >  **Utilisateurs actifs.**

3. Sélectionnez les cases en de côté des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, puis choisissez **Modifier les domaines.**

5. Dans le **volet Modifier les domaines,** sélectionnez un autre domaine.

Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

#### <a name="move-yourself"></a>Se déplacer vous-même

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre administratif</a>.      

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.      

::: moniker-end

2. Go to **Users** \> **Active Users**, and select your account from the list.

3. Sous **l’onglet** Compte, **sélectionnez Gérer** le nom d’utilisateur, puis choisissez un autre domaine.

4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **sélectionnez Se sortir.**

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

### <a name="step-2-move-groups-to-another-domain"></a>Étape 2 : Déplacer des groupes vers un autre domaine

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Groupes.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration,</a>allez à la page  > **Groupes.**

::: moniker-end

2. Sélectionnez le nom du groupe, puis sous **l’onglet Général** sous **Adresse de messagerie, Principal,** sélectionnez **Modifier**.

3. Utilisez la liste de listes pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

### <a name="step-3-remove-the-old-domain"></a>Étape 3 : Supprimer l’ancien domaine

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, allez à la page  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines d’installation.</a>

::: moniker-end

2. Dans la page **Domaines,** sélectionnez le domaine à supprimer.

3. Dans le volet droit, sélectionnez **Supprimer.**

4. Suivez les invites supplémentaires, puis sélectionnez **Fermer.**

## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Combien de temps faut-il pour qu'un domaine soit supprimé ?

La suppression d’un domaine par Microsoft 365 peut prendre jusqu’à 5 minutes s’il n’est pas référencé dans un grand nombre d’endroits tels que les groupes de sécurité, les listes de distribution, les utilisateurs et les groupes Microsoft 365 de sécurité. Si plusieurs références utilisent le domaine, la suppression du domaine peut prendre plusieurs heures (une journée).

Si vous avez des centaines voire des milliers d'utilisateurs, utilisez PowerShell pour interroger tous les utilisateurs, puis déplacez-les vers un autre domaine. Sinon, il est possible que quelques-uns des utilisateurs manquent dans l'interface utilisateur. De plus, lorsque vous voudrez supprimer le domaine, vous ne pourrez pas et vous ne saurez pas pourquoi. Pour en savoir plus, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

## <a name="still-need-help"></a>Encore besoin d’aide ?

::: moniker range="o365-worldwide"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« onmicrosoft.com »](../setup/domains-faq.yml) de votre compte. Lorsque vous supprimez un domaine, les comptes d’utilisateurs reviennent à l’adresse « .onmicrosoft.com » en tant que SMTP/UserprincipalName principal.

Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../../business-video/get-help-support.md) et nous vous aiderons à effectuer cette tâche.

::: moniker-end

::: moniker range="o365-21vianet"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« .partner.onmschina.cn »](../setup/domains-faq.yml) de votre compte. Lorsque vous supprimez un domaine, les comptes d’utilisateurs reviennent à l’adresse « .partner.onmschina.cn » en tant que SMTP/UserprincipalName principal.

Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../../business-video/get-help-support.md?view=o365-21vianet&preserve-view=true) et nous vous aiderons à effectuer cette tâche.

::: moniker-end

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](../setup/domains-faq.yml) (article)

[Basculer vers une autre Microsoft 365 pour les entreprises](../../commerce/subscriptions/switch-to-a-different-plan.md) (article)

[Annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md) (article)
