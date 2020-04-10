---
title: Supprimer un domaine d'Office 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Découvrez comment supprimer un ancien domaine d’Office 365 et déplacer des utilisateurs et des groupes vers un autre domaine.
ms.openlocfilehash: 621b50384b39a21bc0bf5256841c703b3ee0f74a
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43210367"
---
# <a name="remove-a-domain-from-office-365"></a>Supprimer un domaine d'Office 365

[] Contributeurs : [![Peter Baumgartner](../../media/e70dc696-c5f8-4717-a48b-9087431503e7.png)](https://go.microsoft.com/fwlink/p/?linkid=847121)
  
 **[Consultez les Forums aux questions des domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Souhaitez-vous supprimer votre domaine pour l'ajouter à un autre plan d'abonnement Office 365 ? Ou souhaitez-vous annuler votre abonnement ? Vous pouvez [modifier votre plan ou abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) ou [annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).
  
### <a name="step-1-move-users-to-another-domain"></a>Étape 1 : déplacer des utilisateurs vers un autre domaine

#### <a name="move-users"></a>Déplacer des utilisateurs

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration</a>.

2. > Sélectionnez **utilisateurs** **actifs**.

3. Activez les cases à cocher en regard des noms de tous les utilisateurs que vous souhaitez déplacer.

4. Sélectionnez **plus d’options** (**...**), en haut de la page, puis choisissez **modifier les domaines**.

5. Dans le volet **modifier les domaines** , sélectionnez un autre domaine.

Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>.  

2. > Sélectionnez **utilisateurs** **actifs**.

3. Activez les cases à cocher en regard des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, choisissez **plus** > **modifier les domaines**.

5. Dans le volet **modifier les domaines** , sélectionnez un autre domaine.
  
Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>.  

2. > Sélectionnez **utilisateurs** **actifs**.

3. Activez les cases à cocher en regard des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, choisissez **plus** > **modifier les domaines**.

5. Dans le volet **modifier les domaines** , sélectionnez un autre domaine.
  
Vous devrez également effectuer cette action pour vous-même si vous êtes sur le domaine que vous souhaitez supprimer. Lorsque vous modifiez le domaine de votre compte, vous devez vous déconnecter puis vous reconnecter en utilisant le nouveau domaine que vous avez choisi.

::: moniker-end

#### <a name="move-yourself"></a>Vous déplacer

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>.

2. Accédez à **Users** \> utilisateurs **actifs**, puis sélectionnez votre compte dans la liste.

3. Dans l’onglet **compte** , sélectionnez **gérer le nom d’utilisateur**, puis choisissez un autre domaine.
  
4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **déconnectez-vous**.

5. Connectez-vous avec le nouveau domaine et le même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

::: moniker range="o365-germany"

1. Accédez à **Users** \> utilisateurs **actifs**, puis sélectionnez votre nom dans la liste.

2. Dans la section **nom d’utilisateur/adresse de messagerie** , sélectionnez **modifier**, puis choisissez un autre domaine.

3. Sélectionnez **définir comme** > **enregistrement** > principal- **Fermer**.
  
4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **déconnectez-vous**.

5. Connectez-vous avec le nouveau domaine et le même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez à **Users** \> utilisateurs **actifs**, puis sélectionnez votre nom dans la liste.

2. Dans la section **nom d’utilisateur/adresse de messagerie** , sélectionnez **modifier**, puis choisissez un autre domaine.

3. Sélectionnez **définir comme** > **enregistrement** > principal- **Fermer**.
  
4. Dans la partie supérieure, sélectionnez le nom de votre compte, puis **déconnectez-vous**.

5. Connectez-vous avec le nouveau domaine et le même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).

::: moniker-end

### <a name="step-2-move-groups-to-another-domain"></a>Étape 2 : déplacer des groupes vers un autre domaine

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez \> à **la page groupes de** <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes.</a>
  
2. Sélectionnez le nom du groupe, puis sous l’onglet **général** , sous **adresse de messagerie, principal**, sélectionnez **modifier**.

3. Utilisez la liste déroulante pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à **la** > page groupes de **groupes.**

2. Sélectionnez le nom du groupe, puis cliquez sur **modifier** en regard de **nom**.

3. Utilisez la liste déroulante pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à **la** > page groupes de **groupes.**

2. Sélectionnez le nom du groupe, puis cliquez sur **modifier** en regard de **nom**.

3. Utilisez la liste déroulante pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

::: moniker-end

### <a name="step-3-remove-the-old-domain"></a>Étape 3 : supprimer l’ancien domaine

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> **d’installation** \> .

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaines</a> **d’installation** \> .

::: moniker-end
  
2. Dans la page **domaines** , sélectionnez le domaine que vous souhaitez supprimer.

3. Dans le volet droit, sélectionnez **supprimer**.

4. Suivez les invites supplémentaires, puis sélectionnez **Fermer**.

## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Combien de temps faut-il pour qu'un domaine soit supprimé ?

La suppression d’un domaine par Office 365 peut prendre jusqu’à 5 minutes s’il n’est pas référencé dans de nombreux emplacements, tels que les groupes de sécurité, les listes de distribution, les utilisateurs et les groupes Office 365. Si plusieurs références utilisent le domaine, la suppression du domaine peut prendre plusieurs heures (une journée).
  
Si vous avez des centaines voire des milliers d'utilisateurs, utilisez PowerShell pour interroger tous les utilisateurs, puis déplacez-les vers un autre domaine. Sinon, il est possible que quelques-uns des utilisateurs manquent dans l'interface utilisateur. De plus, lorsque vous voudrez supprimer le domaine, vous ne pourrez pas et vous ne saurez pas pourquoi. Pour en savoir plus, voir [Set-MsolUserPrincipalName](https://docs.microsoft.com/powershell/module/msonline/set-msoluserprincipalname?view=azureadps-1.0). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/set-msoldomain?view=azureadps-1.0).
  
## <a name="still-need-help"></a>Vous avez encore besoin d’aide ?

::: moniker range="o365-worldwide"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« onmicrosoft.com »](https://support.office.com/article/b9fc3018-8844-43f3-8db1-1b3a8e9cfd5a.aspx) de votre compte.
  
Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../contact-support-for-business-products.md) et nous vous aiderons à effectuer cette tâche.
  
::: moniker-end

## <a name="related-articles"></a>Articles connexes

[Foire aux questions domaines](../setup/domains-faq.md)

[Obtenir de l’aide sur les domaines Office 365](get-help-with-domains.md)

[Basculer vers une autre offre Office 365 pour les entreprises](../../commerce/subscriptions/switch-to-a-different-plan.md)

[Annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md)
