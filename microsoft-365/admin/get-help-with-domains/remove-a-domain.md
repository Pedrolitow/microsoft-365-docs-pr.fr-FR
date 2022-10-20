---
title: Supprimer un domaine
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Découvrez comment supprimer un ancien domaine de Microsoft 365 et déplacer des utilisateurs et des groupes vers un autre domaine ou annuler votre abonnement.
ms.openlocfilehash: d7dca16ad65e97940b268b300975f242accaf137
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68629300"
---
# <a name="remove-a-domain"></a>Supprimer un domaine

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Supprimez-vous votre domaine parce que vous souhaitez l’ajouter à un autre plan d’abonnement Microsoft 365 ? Ou souhaitez-vous annuler votre abonnement ? Vous pouvez [modifier votre plan ou abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) ou [annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

### <a name="step-1-move-users-to-another-domain"></a>Étape 1 : Déplacer des utilisateurs vers un autre domaine

#### <a name="move-users"></a>Déplacer des utilisateurs

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre administratif</a>.      

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.      

::: moniker-end

2. Sélectionnez **Utilisateurs** > **actifs**.

3. Sélectionnez les zones en regard des noms de tous les utilisateurs que vous souhaitez déplacer.

4. En haut de la page, puis **choisissez Modifier les domaines**.

5. Dans le volet **Modifier les domaines** , sélectionnez un autre domaine.

You'll need to do this for yourself, too, if you're on the domain that you want to remove. When you edit the domain for your account, you'll have to log out and log back in using the new domain you chose to continue.

#### <a name="move-yourself"></a>Déplacer vous-même

::: moniker range="o365-worldwide"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre administratif</a>.      

::: moniker-end

::: moniker range="o365-21vianet"

1. Allez au <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre administratif</a>.      

::: moniker-end

2. Accédez à **Utilisateurs** \> **actifs** et sélectionnez votre compte dans la liste.

3. Sous l’onglet **Compte** , sélectionnez **Gérer le nom d’utilisateur**, puis choisissez un autre domaine.

4. En haut, sélectionnez le nom de votre compte, puis **déconnectez-vous**.

5. Connectez-vous avec le nouveau domaine et votre même mot de passe.

Vous pouvez également utiliser PowerShell pour déplacer des utilisateurs vers un autre domaine. Pour des informations supplémentaires, voir [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname). Pour définir le domaine par défaut, utilisez [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

### <a name="step-2-move-groups-to-another-domain"></a>Étape 2 : Déplacer des groupes vers un autre domaine

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes**>.

::: moniker-end

2. Sélectionnez le nom du groupe, puis sous l’onglet **Général** sous **Email adresse, Principal**, **sélectionnez Modifier**.

3. Utilisez la liste déroulante pour choisir un autre domaine.

4. Sélectionnez **Enregistrer**, puis **Fermer**. Répétez cette procédure pour les groupes ou listes de distribution associés au domaine que vous souhaitez supprimer.

### <a name="step-3-remove-the-old-domain"></a>Étape 3 : Supprimer l’ancien domaine

::: moniker range="o365-worldwide"

> [!NOTE]
> Si vous supprimez un domaine personnalisé, consultez [supprimer un domaine personnalisé](#remove-a-custom-domain) avant de continuer.

1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines</a> **d’installation**\>.

::: moniker-end

2. Dans la page **Domaines** , sélectionnez le domaine à supprimer.

3. Dans le volet droit, **sélectionnez Supprimer**.

4. Suivez les invites supplémentaires, puis sélectionnez **Fermer**.




### <a name="remove-a-custom-domain"></a>Supprimer un domaine personnalisé

Si vous annulez votre abonnement et que vous utilisez un domaine personnalisé, vous devez effectuer quelques étapes supplémentaires avant de pouvoir annuler votre abonnement. 

#### <a name="change-your-domain-nameserver-records-if-needed"></a>Modifiez les enregistrements du serveur de noms de votre domaine (si applicable)

If you set up a custom domain, you added DNS records so the domain would work with Microsoft 365 services. Before you remove your domain, be sure to update the DNS records, such as your domain MX record, at your DNS host.

For example, change the MX record at your DNS host. Email sent to your domain stops coming to your Microsoft address and goes to your new email provider instead. (An MX record determines where email for your domain is sent.)

- Si vos enregistrements de serveur de noms (NS) [pointent vers des serveurs de noms Microsoft 365](../../admin/setup/add-domain.md), la modification de votre enregistrement MX reste sans effet jusqu’à ce que vous modifiez vos enregistrements NS de façon à ce qu'ils pointent vers votre nouvel hôte DNS (voir l'étape 2).

- Avant de mettre à jour l’enregistrement MX, indiquez à vos utilisateurs la date de basculement de leur adresse électronique et le nouveau fournisseur de services de messagerie électronique. De même, si vos utilisateurs souhaitent déplacer leurs courriers Microsoft vers le nouveau fournisseur, des étapes supplémentaires peuvent s’ajouter.

- Le jour où vous modifiez l’enregistrement MX, veillez à [enregistrer vos données](/microsoft-365/commerce/subscriptions/cancel-your-subscription#save-your-data) et [à désinstaller Office si nécessaire](/microsoft-365/commerce/subscriptions/cancel-your-subscription#uninstall-office-optional).

#### <a name="update-your-domain-mx-and-other-dns-records-if-youre-using-a-custom-domain"></a>Mettre à jour l'enregistrement MX et les autres enregistrements DNS de votre domaine (si vous utilisez un domaine personnalisé)

Si vous avez basculé vos enregistrements de serveur de noms (NS) vers Microsoft 365 lors de la configuration de votre domaine, vous devez configurer ou mettre à jour votre enregistrement MX et les autres enregistrements DNS auprès de l'hôte DNS que vous comptez utiliser, puis modifier votre enregistrement NS de façon à ce qu'il pointe vers cet hôte DNS.

Si vous n'avez pas basculé les enregistrements NS lors de la configuration de votre domaine, lorsque vous modifiez l'enregistrement MX, votre courrier électronique commence immédiatement à parvenir à la nouvelle adresse.

Pour modifier vos enregistrements NS, consultez [Modifier les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau d’enregistrement de domaines](../../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md).



## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Combien de temps faut-il pour qu'un domaine soit supprimé ?

La suppression d’un domaine par Microsoft 365 peut prendre jusqu’à cinq minutes s’il n’est pas référencé dans un grand nombre d’emplacements tels que les groupes de sécurité, les listes de distribution, les utilisateurs, les alias, les boîtes aux lettres partagées, les boîtes aux lettres de ressources et les groupes Microsoft 365. Si plusieurs références utilisent le domaine, la suppression du domaine peut prendre plusieurs heures (une journée).

If you have hundreds or thousands of users, use PowerShell to query for all users and then move them to another domain. Otherwise, it's possible for a handful of users to be missed in the UI, and then when you go to remove the domain, you won't be able to and you won't know why. See [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname) for more information. To set the default domain, use [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

## <a name="still-need-help"></a>Encore besoin d’aide ?

::: moniker range="o365-worldwide"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« onmicrosoft.com »](../setup/domains-faq.yml) de votre compte. Lorsque vous supprimez un domaine, les comptes d’utilisateur reviendront à l’adresse « .onmicrosoft.com » en tant que SMTP/UserprincipalName principal.

Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../../business-video/get-help-support.md) et nous vous aiderons à effectuer cette tâche.

::: moniker-end

::: moniker range="o365-21vianet"

> [!NOTE]
> Vous ne pouvez pas supprimer le domaine [« .partner.onmschina.cn »](../setup/domains-faq.yml) de votre compte. Lorsque vous supprimez un domaine, les comptes d’utilisateur reviendront à l’adresse « .partner.onmschina.cn » en tant que SMTP/UserprincipalName principal.

Cela ne fonctionne toujours pas ? Vous devez peut-être supprimer votre domaine manuellement. [Appelez-nous](../../business-video/get-help-support.md?view=o365-21vianet&preserve-view=true) et nous vous aiderons à effectuer cette tâche.

::: moniker-end

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](../setup/domains-faq.yml) (article)

[Basculer vers un autre plan Microsoft 365 pour les entreprises](../../commerce/subscriptions/switch-to-a-different-plan.md) (article)

[Annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md) (article)
