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
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Découvrez comment annuler votre Dynamics 365, Intune, Power Platform et Microsoft 365 pour un essai professionnel ou des abonnements payants dans le Centre d'administration Microsoft 365.
ms.date: 01/20/2022
ms.openlocfilehash: 2d800fbba8ce2290de395179589b1d4110cd1345
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62322577"
---
# <a name="cancel-your-subscription"></a>Annuler votre abonnement

Vous pouvez annuler votre abonnement à tout moment dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre d'administration Microsoft 356</a>. Cependant, pour recevoir un remboursement, vous devez répondre à certaines conditions d'éligibilité au remboursement. Pour plus d'informations, voir [Comprendre l'éligibilité au remboursement](#understand-refund-eligibility).

Si vous avez plusieurs abonnements au même produit, comme Microsoft 365 Business Premium, l'annulation d'un abonnement n'aura pas d'incidence sur les licences ou services achetés dans les autres.

> [!IMPORTANT]
> Cet article s'applique uniquement aux abonnements Dynamics 365, Intune, Power Platform et Microsoft 365 pour les entreprises. Si vous avez Microsoft 365 Famille ou Personnel, voir Annuler un [abonnement Microsoft 365](https://support.microsoft.com/office/cancel-a-microsoft-365-subscription-46e2634c-c64b-4c65-94b9-2cc9c960e91b?OCID=M365_DocsCancel_Link) .

## <a name="before-you-begin"></a>Avant de commencer

Pour effectuer les étapes de cet article, vous devez être administrateur général ou de facturation. Pour plus d’informations, voir [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="understand-refund-eligibility"></a>Comprendre l'éligibilité au remboursement

### <a name="if-you-have-a-billing-profile"></a>Si vous avez un profil de facturation

Vous devez annuler dans les 72 heures suivant le début d'un abonnement payant pour obtenir un remboursement au prorata du temps inutilisé que vous avez déjà payé. Les remboursements ne sont pas disponibles après 72 heures.

Par exemple, supposons que vous ayez acheté un abonnement d'un an pour lequel vous payez 20 $ par mois pour une seule licence. Vous avez acheté l'abonnement le 1er février 2022 à 11 h 00 UST et décidez de l'annuler le 3 février 2022 à 11 h 00 UST. Nous déduisons 1,43 $ pour les deux jours d'abonnement et vous recevez un remboursement au prorata de 18,57 $.

**Vous ne savez pas si vous avez un profil de facturation ?** Pour savoir comment savoir si vous avez un profil de facturation, consultez [Afficher mes profils de facturation](../billing-and-payments/manage-billing-profiles.md#view-my-billing-profiles).

### <a name="if-you-dont-have-a-billing-profile"></a>Si vous n'avez pas de profil de facturation

Utilisez le tableau suivant pour vous aider à déterminer si vous pouvez annuler vous-même votre abonnement.

|Si votre abonnement a  |Vous pouvez  |
|--------------|--------------|
|25 licences ou moins  | Annuler votre essai ou votre abonnement payant en ligne dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre d'administration Microsoft 356</a> à tout moment.        |
|Plus de 25 licences   | Réduire le nombre de licences à 25 ou moins et réessayer, ou [appeler l'assistance pour annuler votre abonnement](../../admin/get-help-support.md).        |

Pour les abonnements qui n'ont pas de profil de facturation, vous ne pouvez annuler que pendant une période limitée après avoir acheté ou renouvelé votre abonnement. Si la fenêtre d'annulation est passée, [désactiver la facturation récurrente](renew-your-subscription.md) pour annuler l'abonnement à la fin de sa durée.

Si vous annulez pendant la fenêtre de temps limitée, tout crédit au prorata vous sera restitué au cours du prochain cycle de facturation.

## <a name="steps-to-cancel-your-subscription"></a>Étapes d’annulation d’un abonnement

Si vous avez ajouté votre propre nom de domaine pour l’utiliser avec votre abonnement, vous devez retirer le domaine avant d'annuler votre abonnement. Pour plus d’informations, voir [Supprimer un domaine](../../admin/get-help-with-domains/remove-a-domain.md).

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Produits</a>.

::: moniker-end

2. Recherchez l'abonnement que vous souhaitez annuler. Sélectionnez les trois points (autres actions), puis sélectionnez **Annuler l’abonnement**.

3. Dans le volet **Annuler l'abonnement**, choisissez la raison pour laquelle vous annulez. Si vous le souhaitez, vous pouvez fournir des commentaires.

4. Sélectionnez **Enregistrer**.

Votre abonnement s’affiche à présent dans un état **Désactivé** et dispose de fonctionnalités réduites jusqu’à sa suppression. Pour plus d'informations sur les conséquences de l'annulation d'un abonnement payant pour Microsoft 365 Entreprise, consultez [Qu'arrive-t-il à mes données et à mon accès à la fin de mon abonnement Microsoft 365 Entreprise ?](what-if-my-subscription-expires.md)

> [!NOTE]
> Si vous supprimez explicitement un abonnement, cela ignore les étapes Expiré et Désactivé, et les données et le contenu SharePoint Online, dont OneDrive, sont supprimés immédiatement.

## <a name="what-happens-when-you-cancel-a-subscription"></a>Que se passe-t-il lorsqu’un abonnement est annulé ?

Si vous annulez un abonnement avant son expiration, son statut passe directement à l'état « Désactivé ». Pour la plupart des abonnements et dans la plupart des pays et régions, l'état désactivé dure 90 jours. Quand un abonnement est en état désactivé, les administrateurs peuvent toujours consulter et sauvegarder les données pour leur organisation, mais nous recommandons que les administrateurs [sauvegardent les données](back-up-data-before-switching-plans.md) d'un abonnement avant l'annulation de celui-ci, en particulier s'il s'agit de leur seul abonnement. Les administrateurs peuvent également réactiver l’abonnement tant qu’il est à l’état « Désactivé ».

L’abonnement passe à l’état supprimé après 90 jours. Toutes les données dépendantes de cet abonnement peuvent être supprimées à l’issue de ces 90 jours et le seront 180 jours au plus tard après le passage à cet état. Vous ne pouvez retirer un mode de paiement d’un abonnement annulé qu’une fois cet état « Supprimé » atteint.

### <a name="what-to-expect-for-you-and-your-users-if-you-cancel-a-subscription"></a>Voici ce à quoi vous et vos utilisateurs devez vous attendre si vous annulez un abonnement.
  
- **Accès des administrateurs** Les administrateurs peuvent toujours se connecter et accéder au Centre d'administration et acheter d'autres abonnements si nécessaire. En tant qu'administrateur général ou de facturation, vous disposez de 90 jours pour [réactiver l’abonnement](reactivate-your-subscription.md) avec toutes les données intactes.

- **Accès des utilisateurs** Vos utilisateurs ne peuvent plus utiliser les services tels que OneDrive Entreprise ou accéder aux données client (par exemple, des courriers électroniques ou des documents sur des sites d'équipe). Les applications Office, telles que Word et Excel, finissent par passer en mode d'utilisation en lecture seule avec fonctionnalités réduites, et affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

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

- Pour déplacer votre courrier électronique, vos contacts, vos tâches et vos informations de calendrier vers un autre compte, voir [Exporter ou sauvegarder les courriers électroniques, les contacts et le calendrier vers un fichier .pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91).

- Pour enregistrer le contenu d'une bibliothèque de documents ou d'une liste (par exemple, des contacts) à partir d'un environnement SharePoint Online (OneDrive Entreprise ou sites d'équipe) vers des partages de fichiers ou un ordinateur local, voir [Migration manuelle de contenu SharePoint Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

### <a name="uninstall-office-optional"></a>Désinstaller Office (facultatif)

Si vous avez annulé votre abonnement sans avoir [déplacé les utilisateurs sur un autre abonnement](move-users-different-subscription.md) l’incluant, Microsoft 365 s’exécute en mode de fonctionnalité réduite. Quand cela se produit, les utilisateurs peuvent uniquement lire et imprimer des documents, et les applications de Microsoft 365 affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380). Pour éviter toute confusion, demandez à vos utilisateurs de [désinstaller Office](https://support.microsoft.com/office/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8) de leurs ordinateurs.

## <a name="next-steps"></a>Étapes suivantes

Pour clôturer complétement votre compte Microsoft, consultez la rubrique [Clôturer un compte](../close-your-account.md).

## <a name="related-content"></a>Contenu connexe

[Renouveler un abonnement](renew-your-subscription.md) (article)\
[Réactiver votre abonnement](reactivate-your-subscription.md) (article)\
[Déplacer des utilisateurs vers un autre abonnement](move-users-different-subscription.md) (article)
