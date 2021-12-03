---
title: Examiner les privilèges d’administration des partenaires
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
search.appverid: MET150
description: Découvrez comment passer en revue votre liste de fournisseurs de solutions (partenaires) certifiés par Microsoft pour déterminer les privilèges d’administration dont ils ont et comment supprimer ces privilèges.
ms.date: 12/03/2021
ms.openlocfilehash: 7dc0a52526da1f0da9cd85b438b6f30b798c2dfa
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61302492"
---
# <a name="review-partner-administrative-privileges"></a>Examiner les privilèges d’administration des partenaires

Si vous avez un fournisseur de solutions cloud certifié par Microsoft (partenaire revendeur), nous vous recommandons d’effectuer une révision trimestrielle des privilèges d’administration délégués (DAP) qui lui sont attribués. Assurez-vous que votre organisation souhaite que ce partenaire accède aux données de votre organisation et effectuer des achats en votre nom.

> [!IMPORTANT]
> L’autorisation DAP, qui inclut des autorisations d’administrateur global, à n’importe quel partenaire peut présenter un risque de sécurité. Le fait d’avoir trop d’administrateurs globaux est également un risque pour la sécurité. [En savoir plus sur l’activité récente ciblant les privilèges délégués.](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/)

Une fois que vous avez accepté un contrat DAP d’un partenaire revendeur, il peut attribuer le rôle d’administrateur global de votre organisation à ses employés. Le rôle d’administrateur global permet aux employés du partenaire d’accéder aux données personnelles de vos employés et à d’autres informations sensibles. Il leur donne également l’autorisation d’agir à l’échelle du client, telles que les actions suivantes :

- Modification des mots de passe utilisateur
- Ajout d’utilisateurs avec des comptes de messagerie
- Ajout et gestion de domaines web associés à votre organisation

Lorsque le DAP est activé, vous n’avez aucun contrôle sur le nombre d’administrateurs globaux que votre partenaire peut ajouter. Vous pouvez uniquement accorder ou refuser l’accès DAP partenaire (administrateur global) à votre compte.

## <a name="review-and-remove-roles-from-partners"></a>Examiner et supprimer des rôles de partenaires

1. Dans la Centre d'administration Microsoft 365, go to the **Paramètres**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partner relationships</a> page. Les partenaires avec DAP ont **un administrateur général** répertorié dans la colonne **Rôles.**
2. Pour supprimer le rôle d’administrateur global d’un partenaire, recherchez le nom du partenaire à supprimer.
3. Sélectionnez la ligne dont **Le revendeur est le** type de **relation.**
4. Dans la page des détails du partenaire, **sélectionnez Supprimer des rôles,** puis Sélectionnez **Oui.**

> [!NOTE]
>
> - Si vous supprimez le DAP (rôle d’administrateur global) d’un partenaire, nous vous recommandons de le contacter pour discuter de la remise future des services. Par exemple, vous pouvez créer un compte d’utilisateur avec des privilèges inférieurs et partager ces informations de compte avec votre partenaire. En savoir plus sur [l’ajout d’utilisateurs](../admin/add-users/add-users.md) [et l’attribution de rôles d’administrateur.](../admin/add-users/assign-admin-roles.md)
> - Même si le rôle d’administrateur global est supprimé, le partenaire peut toujours effectuer des achats en votre nom. Nous vous recommandons de contacter le partenaire pour lui demander de supprimer cette possibilité dans l’Partner Center.

## <a name="related-content"></a>Contenu associé

[Gérer les relations des partenaires](manage-partners.md) (article)\
[À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md) (article)\
[Privilèges d’administrateur délégués dans Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (article)
