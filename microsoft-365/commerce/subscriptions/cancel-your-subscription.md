---
title: Annuler un abonnement
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
- AdminTemplateSet
search.appverid: MET150
description: Si vous avez moins de 25 licences d'utilisateur, vous pouvez annuler votre version d'essai ou votre abonnement payant de Microsoft 365 pour entreprise dans le centre d'administration.
ms.date: 04/08/2021
ms.openlocfilehash: 900fd5f544a405b5f337623ba35a353cefaf9bab
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209449"
---
# <a name="cancel-your-subscription"></a>Annuler un abonnement

> [!IMPORTANT]
> Cet article s'applique uniquement aux abonnements Microsoft 365 pour entreprises. Si vous avez Microsoft 365 Famille ou Personnel, voir Annuler un [abonnement Microsoft 365](https://support.microsoft.com/en-us/office/cancel-a-microsoft-365-subscription-46e2634c-c64b-4c65-94b9-2cc9c960e91b?OCID=M365_DocsCancel_Link) .

*Conditions :* Si vous disposez de moins de 25 licences attribuées à vos utilisateurs, vous pouvez à tout moment annuler votre abonnement payant ou version d’évaluation de Microsoft 365 dans le centre d’administration Microsoft 365. Si vous disposez de plus de 25 licences attribuées à vos utilisateurs, réduisez ce nombre à moins de 25 ou bien [appelez le service clientèle pour annuler votre abonnement](../../business-video/get-help-support.md).

*Remboursement :* Tout crédit calculé au prorata vous sera remboursé au cours du cycle de facturation suivant.

> [!NOTE]
> Si vous disposez de plusieurs abonnements pour un même produit tel que Microsoft 365 Business Premium, l’annulation d’un de ces abonnements n’impacte pas les licences ou les services relatifs aux autres abonnements.

## <a name="before-you-begin"></a>Avant de commencer

Pour suivre les étapes décrites dans cet article, vous devez être administrateur général ou de facturation. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="steps-to-cancel-your-subscription"></a>Étapes d’annulation d’un abonnement

Si vous avez ajouté votre propre nom de domaine pour l’utiliser avec votre abonnement, vous devez retirer le domaine avant d'annuler votre abonnement. Pour plus d'informations, consultez la rubrique [Retirer un domaine](../../admin/get-help-with-domains/remove-a-domain.md).

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Produits</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Vos produits</a>.

::: moniker-end

2. Recherchez l’abonnement que vous souhaitez annuler. Sélectionnez les trois points (autres actions), puis sélectionnez **Annuler l'abonnement**.
3. Dans le volet **Annuler l'abonnement**, choisissez la raison pour laquelle vous annulez. Si vous le souhaitez, vous pouvez fournir des commentaires.
4. Sélectionnez **Enregistrer**.

Votre abonnement présente désormais l’état **Désactivé** et propose des fonctionnalités réduites jusqu’à sa suppression. Pour plus d'informations sur les conséquences de l'annulation d'un abonnement payant pour Microsoft 365 for business, consultez la rubrique [Qu'arrive-t-il à mes données et à mon accès à la fin de mon abonnement Microsoft 365 for business ?](what-if-my-subscription-expires.md)

> [!NOTE]
> Si vous supprimez explicitement un abonnement, cela ignore les étapes Expiré et Désactivé, et les données et le contenu SharePoint Online, dont OneDrive, sont supprimés immédiatement.

## <a name="what-happens-when-you-cancel-a-subscription"></a>Que se passe-t-il lorsqu’un abonnement est annulé ?

Si vous annulez un abonnement avant son expiration, son statut passe directement à l'état « Désactivé ». Pour la plupart des abonnements et dans la plupart des pays et régions, l'état désactivé dure 90 jours. Quand un abonnement est en état désactivé, les administrateurs peuvent toujours consulter et sauvegarder les données pour leur organisation, mais nous recommandons que les administrateurs [sauvegardent les données](back-up-data-before-switching-plans.md) d'un abonnement avant l'annulation de celui-ci, en particulier s'il s'agit de leur seul abonnement. Les administrateurs peuvent également réactiver l’abonnement tant qu’il est à l’état « Désactivé ».

L’abonnement passe à l’état supprimé après 90 jours. Toutes les données dépendantes de cet abonnement peuvent être supprimées à l’issue de ces 90 jours et le seront 180 jours au plus tard après le passage à cet état. Vous ne pouvez retirer un mode de paiement d’un abonnement annulé qu’une fois cet état « Supprimé » atteint.

### <a name="what-to-expect-for-you-and-your-users-if-you-cancel-a-subscription"></a>Voici ce à quoi vous et vos utilisateurs devez vous attendre si vous annulez un abonnement.
  
- **Accès des administrateurs** Les administrateurs peuvent toujours se connecter et accéder au centre d'administration, et acheter d'autres abonnements si nécessaire. En tant qu'administrateur général ou de facturation, vous disposez de 90 jours pour [réactiver l’abonnement](reactivate-your-subscription.md) et retrouver toutes les données intactes.

- **Accès des utilisateurs** Vos utilisateurs ne peuvent plus utiliser les services tels que OneDrive Entreprise ou accéder aux données client (par exemple, des courriers électroniques ou des documents sur des sites d'équipe). Les applications Office, telles que Word et Excel, finissent par passer en mode d'utilisation en lecture seule avec fonctionnalités réduites, et affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx).

Pour en savoir plus, consultez la rubrique [Qu'arrive-t-il à mes données et à mon accès à la fin de mon abonnement for business ?](what-if-my-subscription-expires.md)

> [!IMPORTANT]
> Si vous voulez que les données de votre abonnement soient supprimées avant la fin établie de l’étape de désactivation, vous pouvez [clôturer votre compte](../close-your-account.md).

## <a name="other-steps-you-might-have-to-take"></a>Étapes supplémentaires potentielles

### <a name="change-custom-domain-settings"></a>Modifiez les paramètres de domaine personnalisé

Si vous utilisez un domaine personnalisé avec votre abonnement, vous devez effectuer un certain nombre d’étapes supplémentaires pour pouvoir annuler votre abonnement. Si vous n’avez pas de domaine personnalisé, vous pouvez passer à l’étape [Enregistrer vos données](#save-your-data).

#### <a name="change-your-domain-nameserver-records-if-needed"></a>Modifiez les enregistrements du serveur de noms de votre domaine (si applicable)

Si vous avez configuré un domaine personnalisé, vous avez ajouté des enregistrements DNS afin que le domaine fonctionne avec les services Microsoft 365. Avant de supprimer votre domaine, veillez à mettre à jour les enregistrements DNS, tels que de l'enregistrement MX de votre domaine, auprès de votre hôte DNS.

Par exemple, modifiez l'enregistrement MX auprès de votre hôte DNS. Le courrier électronique envoyé à votre domaine n'arrive plus à votre adresse Microsoft, mais parvienne plutôt à votre nouveau fournisseur de courrier. (Un enregistrement MX détermine où le courrier destiné à votre domaine est envoyé).

- Si vos enregistrements de serveur de noms (NS) [pointent vers des serveurs de noms Microsoft 365](../../admin/setup/add-domain.md), la modification de votre enregistrement MX reste sans effet jusqu’à ce que vous modifiez vos enregistrements NS de façon à ce qu'ils pointent vers votre nouvel hôte DNS (voir l'étape 2).

- Avant de mettre à jour l’enregistrement MX, indiquez à vos utilisateurs la date de basculement de leur adresse électronique et le nouveau fournisseur de services de messagerie électronique. De même, si vos utilisateurs souhaitent déplacer leurs courriers Microsoft vers le nouveau fournisseur, des étapes supplémentaires peuvent s’ajouter.

- Le jour où vous modifiez l’enregistrement MX, suivez le reste des étapes décrites dans cet article.

#### <a name="update-your-domain-mx-and-other-dns-records-if-youre-using-a-custom-domain"></a>Mettre à jour l'enregistrement MX et les autres enregistrements DNS de votre domaine (si vous utilisez un domaine personnalisé)

Si vous avez basculé vos enregistrements de serveur de noms (NS) vers Microsoft 365 lors de la configuration de votre domaine, vous devez configurer ou mettre à jour votre enregistrement MX et les autres enregistrements DNS auprès de l'hôte DNS que vous comptez utiliser, puis modifier votre enregistrement NS de façon à ce qu'il pointe vers cet hôte DNS.

Si vous n'avez pas basculé les enregistrements NS lors de la configuration de votre domaine, lorsque vous modifiez l'enregistrement MX, votre courrier électronique commence immédiatement à parvenir à la nouvelle adresse.

Pour modifier vos enregistrements NS, consultez la rubrique [Retirer un domaine](../../admin/get-help-with-domains/remove-a-domain.md).

### <a name="save-your-data"></a>Enregistrer vos données

Lorsque l’annulation prend effet, les utilisateurs perdent l’accès à leurs données. Avant de procéder à l’annulation de votre abonnement, invitez-les à sauvegarder leurs fichiers OneDrive Entreprise et SharePoint Online autre part. Toutes les données client dépendantes de cet abonnement sont susceptibles d’être supprimées après 30 jours, et pas plus tard que 180 jours après l'annulation.

- Pour déplacer votre courrier électronique, vos contacts, vos tâches et vos informations de calendrier vers un autre compte, voir [Exporter ou sauvegarder les courriers électroniques, les contacts et le calendrier vers un fichier .pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91.aspx).

- Pour enregistrer le contenu d'une bibliothèque de documents ou d'une liste (par exemple, des contacts) à partir d'un environnement SharePoint Online (OneDrive Entreprise ou sites d'équipe) vers des partages de fichiers ou un ordinateur local, voir [Migration manuelle de contenu SharePoint Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

### <a name="uninstall-office-optional"></a>Désinstaller Office (facultatif)

Si vous avez annulé votre abonnement sans avoir [déplacé les utilisateurs sur un autre abonnement](move-users-different-subscription.md) l’incluant, Microsoft 365 s’exécute en mode de fonctionnalité réduite. Quand cela se produit, les utilisateurs peuvent uniquement lire et imprimer des documents, et les applications de Microsoft 365 affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx). Pour éviter toute confusion, demandez à vos utilisateurs de [désinstaller Office](https://support.microsoft.com/office/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8.aspx) de leurs ordinateurs.

## <a name="next-steps"></a>Étapes suivantes

Pour clôturer complétement votre compte Microsoft, consultez la rubrique [Clôturer un compte](../close-your-account.md).

## <a name="related-content"></a>Contenu connexe

[Renouveler un abonnement](renew-your-subscription.md) (article)\
[Réactiver votre abonnement](reactivate-your-subscription.md) (article)\
[Déplacer des utilisateurs vers un autre abonnement](move-users-different-subscription.md) (article)
