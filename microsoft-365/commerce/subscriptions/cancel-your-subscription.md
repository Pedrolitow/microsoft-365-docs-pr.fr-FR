---
title: Annuler votre abonnement
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
ms.assetid: b1bc0bef-4608-4601-813a-cdd9f746709a
description: Découvrez comment annuler votre abonnement Office 365 pour les entreprises ou Microsoft 365 (version d’évaluation ou abonnement payant).
ms.openlocfilehash: 58c545257895de8da4256cea4826029916b66961
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42354595"
---
# <a name="cancel-your-subscription"></a>Annuler votre abonnement

*Éligibilité :* Si vous avez moins de 25 licences attribuées à des utilisateurs, vous pouvez annuler votre abonnement Office 365 pour les entreprises ou votre abonnement payant en ligne dans le centre d’administration à tout moment. Si vous avez plus de 25 licences affectées à des utilisateurs, [appelez le support pour annuler votre abonnement](../../admin/contact-support-for-business-products.md).

*Remboursement :* Tout crédit prorata vous sera renvoyé au cours du cycle de facturation suivant.

> [!NOTE]
> Si vous avez plusieurs abonnements au même produit, comme Office 365 entreprise E3, l’annulation de l’un d’entre eux n’a pas d’impact sur les licences ou services achetés dans les autres abonnements.

## <a name="steps-to-cancel-your-subscription"></a>Étapes d’annulation de votre abonnement

Si vous avez ajouté votre propre nom de domaine à utiliser avec votre abonnement, vous devez supprimer le domaine avant d’annuler votre abonnement. Pour plus d'informations, voir [Supprimer un domaine d'Office 365](../../admin/get-help-with-domains/remove-a-domain.md).

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits et services</a>.

2. Recherchez l’abonnement que vous souhaitez annuler et sous **paramètres & Actions**, sélectionnez Annuler l' **abonnement**.

3. Examinez les dates importantes, fournissez des commentaires sur la raison de votre annulation, puis sélectionnez **Annuler l’abonnement**.

    Votre abonnement s’affiche désormais dans un état **désactivé** et dispose de fonctionnalités réduites jusqu’à ce qu’il soit supprimé. Pour plus d’informations sur ce que vous pouvez vous attendre lors de l’annulation d’un abonnement Office 365 pour les entreprises payant, voir [qu’arrive-t-il à mes données et à Access lorsque mon abonnement office 365 pour les entreprises prend fin ?](what-if-my-subscription-expires.md)

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">abonnements</a> de **facturation** \> .

2. Sur la page **abonnements** , sélectionnez un abonnement.

3. Dans le menu **actions supplémentaires** , sélectionnez **Annuler l’abonnement**.

    ![Fermez le menu autres actions.](../../media/befa74b7-62c1-42a3-a38e-db76a1c97dba.png)

4. Examinez les dates importantes, fournissez des commentaires sur la raison de votre annulation, puis sélectionnez **Annuler l’abonnement**.

    Votre abonnement s’affiche désormais dans un état **désactivé** et dispose de fonctionnalités réduites jusqu’à ce qu’il soit supprimé. Pour plus d’informations sur ce que vous pouvez vous attendre lors de l’annulation d’un abonnement Office 365 pour les entreprises payant, voir [qu’arrive-t-il à mes données et à Access lorsque mon abonnement office 365 pour les entreprises prend fin ?](what-if-my-subscription-expires.md)

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">abonnements</a> de **facturation** \> .

2. Sur la page **abonnements** , sélectionnez un abonnement.

3. Dans le menu **actions supplémentaires** , sélectionnez **Annuler l’abonnement**.

    ![Fermez le menu autres actions.](../../media/befa74b7-62c1-42a3-a38e-db76a1c97dba.png)

4. Examinez les dates importantes, fournissez des commentaires sur la raison de votre annulation, puis sélectionnez **Annuler l’abonnement**.

    Votre abonnement s’affiche désormais dans un état **désactivé** et dispose de fonctionnalités réduites jusqu’à ce qu’il soit supprimé. Pour plus d’informations sur ce que vous pouvez vous attendre lors de l’annulation d’un abonnement Office 365 pour les entreprises payant, voir [qu’arrive-t-il à mes données et à Access lorsque mon abonnement office 365 pour les entreprises prend fin ?](what-if-my-subscription-expires.md)

::: moniker-end


## <a name="other-steps-you-might-have-to-take"></a>Autres étapes que vous pouvez être amené à effectuer

### <a name="change-custom-domain-settings"></a>Modifier les paramètres de domaine personnalisés

Si vous utilisez un domaine personnalisé avec votre abonnement, vous devez effectuer quelques étapes supplémentaires avant de pouvoir annuler votre abonnement. Si vous n’avez pas de domaine personnalisé, vous pouvez passer à [la sauvegarde de vos données](#save-your-data).

#### <a name="change-your-domain-nameserver-records-if-needed"></a>Modifier les enregistrements de serveur de noms de domaine (le cas échéant)

Si vous configurez un domaine personnalisé, vous avez ajouté des enregistrements DNS de sorte que le domaine fonctionne avec les services Office 365. Avant de supprimer votre domaine, veillez à mettre à jour les enregistrements DNS, tels que votre enregistrement MX de domaine, sur votre hôte DNS.

Par exemple, modifiez l’enregistrement MX au niveau de votre hôte DNS. Les messages électroniques envoyés à votre domaine cessent de répondre à votre adresse Office 365 et vont à votre nouveau fournisseur de courrier. (Un enregistrement MX détermine où le courrier destiné à votre domaine est envoyé).

- Si vos enregistrements de serveur de noms (NS) [pointent vers des serveurs de noms Office 365](../../admin/setup/add-domain.md), les modifications apportées à votre enregistrement MX ne prennent effet que lorsque vous modifiez vos enregistrements NS afin qu’ils pointent vers votre nouvel hôte DNS (voir étape 2).

- Avant de mettre à jour l’enregistrement MX, indiquez à vos utilisateurs la date à laquelle vous envisagez de basculer leur courrier électronique, ainsi que le nouveau fournisseur de messagerie que vous envisagez d’utiliser. Par ailleurs, si vos utilisateurs souhaitent déplacer leur courrier électronique Office 365 existant vers le nouveau fournisseur, ils doivent suivre des étapes supplémentaires.

- Le jour où vous modifiez l'enregistrement MX, suivez le reste des étapes décrites dans cet article.

#### <a name="update-your-domain-mx-and-other-dns-records-if-youre-using-a-custom-domain"></a>Mettre à jour votre domaine MX et d’autres enregistrements DNS (si vous utilisez un domaine personnalisé)

Si vous avez converti vos enregistrements de serveur de noms (NS) en Office 365 lorsque vous avez configuré votre domaine, vous devez configurer ou mettre à jour votre enregistrement MX et d’autres enregistrements DNS au niveau de l’hôte DNS que vous prévoyez d’utiliser, puis modifier votre enregistrement NS en cet hôte DNS.

Si vous n’avez pas changé les enregistrements NS lors de la configuration de votre domaine, lorsque vous modifiez l’enregistrement MX, votre courrier électronique commence immédiatement à accéder à la nouvelle adresse.

Pour plus d’informations, voir [Comment Office 365 gère-t-il mes enregistrements DNS ?](../../admin/setup/domains-faq.md#how-does-office-365-manage-my-dns-records). Pour modifier vos enregistrements NS, consultez la rubrique [supprimer un domaine d’Office 365](../../admin/get-help-with-domains/remove-a-domain.md).

### <a name="save-your-data"></a>Enregistrer vos données

Lorsque l’annulation devient effective, vos utilisateurs perdent l’accès à leurs données. Avant d’annuler l’abonnement, demandez-lui d’enregistrer ses fichiers OneDrive entreprise ou SharePoint Online dans un autre emplacement. Toutes les données client que vous quittez derrière peuvent être supprimées au bout de 30 jours et supprimées au plus tard 180 jours après l’annulation.

- Pour déplacer votre courrier électronique, vos contacts, vos tâches et vos informations de calendrier vers un autre compte, voir [Exporter ou sauvegarder les courriers électroniques, les contacts et le calendrier vers un fichier .pst Outlook](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91.aspx).

- Pour enregistrer le contenu d'une bibliothèque de documents ou d'une liste (par exemple, des contacts) à partir d'un environnement SharePoint Online (OneDrive Entreprise ou sites d'équipe) vers des partages de fichiers ou un ordinateur local, voir [Migration manuelle de contenu SharePoint Online](https://support.microsoft.com/kb/2783484).

### <a name="uninstall-office-optional"></a>Désinstaller Office (facultatif)

Si vous avez annulé votre abonnement, et que vous n’avez pas déplacé les utilisateurs vers un autre abonnement qui inclut Office, Office 365 s’exécute en mode de fonctionnalités réduites. Lorsque cela se produit, les utilisateurs peuvent uniquement lire et imprimer des documents et les applications Office 365 afficher [des notifications de produit sans licence](https://support.office.com/article/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx). Pour éviter toute confusion, demandez à vos utilisateurs de [désinstaller Office](https://support.office.com/article/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8.aspx) de leurs ordinateurs.

## <a name="related-articles"></a>Articles connexes

[Renouveler votre abonnement](renew-your-subscription.md)

[Réactiver votre abonnement](reactivate-your-subscription.md)

[Changer d'offre ou d'abonnement](switch-to-a-different-plan.md)
