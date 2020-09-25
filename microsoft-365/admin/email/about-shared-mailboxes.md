---
title: À propos des boîtes aux lettres partagées
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
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Les boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes ont besoin d’accéder à la même boîte aux lettres. Découvrez ce que vous devez savoir avant de créer une boîte aux lettres partagée.
ms.openlocfilehash: f6feae1662093ffea2537a62c5e8fdf28c622166
ms.sourcegitcommit: 96b4593becc9450af136c528844e858c6e88b5a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48269348"
---
# <a name="about-shared-mailboxes"></a>À propos des boîtes aux lettres partagées

Les Boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique, du bureau d'accueil, ou d'un autre poste pouvant être partagé par plusieurs personnes.

Les utilisateurs disposant d’autorisations sur la boîte aux lettres du groupe peuvent Envoyer en tant que ou Envoyer de la part pour le compte de l’adresse de messagerie de la boîte aux lettres si l’administrateur leur a accordé cette autorisation. Cette fonctionnalité est particulièrement utile pour les boîtes aux lettres d’aide et de support, car les utilisateurs peuvent envoyer des e-mails à partir du « Support technique de Contoso » ou du « Bureau d'accueil du bâtiment A ».

Avant [de créer une boîte aux lettres partagée](create-a-shared-mailbox.md), voici quelques éléments que vous devez savoir :

- **Licences :** Votre boîte aux lettres partagée peut stocker jusqu’à 50 Go de données sans que vous lui avez attribué de licence. Après cela, vous devez attribuer une licence à la boîte aux lettres pour stocker davantage de données. Pour plus d’informations sur les licences de boîtes aux lettres partagées, consultez la rubrique [Exchange Online Limits](https://technet.microsoft.com/library/exchange-online-limits.aspx#StorageLimits). Lorsqu'une boîte aux lettres partagée atteint sa limite de stockage, vous serez en mesure de recevoir des courriers électroniques pendant un certain temps, mais vous ne pourrez pas envoyer de nouveaux messages électroniques. Puis, après cela, vous ne pourrez plus recevoir de message. Les expéditeurs des courriers vers votre boîte aux lettres recevront un accusé de réception négatif.

- **Autorisations de l’utilisateur :** Vous devez donner aux utilisateurs des autorisations (appartenance) pour utiliser la boîte aux lettres partagée. Seules les personnes internes à votre organisation peuvent utiliser une boîte aux lettres partagée.

- **Utilisateurs externes :** Vous ne pouvez pas autoriser les personnes extérieures à votre entreprise (comme les personnes disposant d’un compte Gmail) à accéder à votre boîte aux lettres partagée. Si vous voulez effectuer cette action, envisagez plutôt de créer un groupe pour Outlook. Pour en savoir plus, consultez [la rubrique créer un groupe Microsoft 365 dans le centre d’administration](../create-groups/create-groups.md).

-  **Utiliser avec Outlook :** En plus de l’utilisation d’Outlook sur le Web à partir de votre navigateur pour accéder aux boîtes aux lettres partagées, vous pouvez également utiliser l’application Outlook pour iOS ou Outlook pour Android. Pour en savoir plus, consultez <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">la rubrique ajouter une boîte aux lettres partagée à Outlook Mobile</a>. Une autre solution consiste à créer un groupe pour votre boîte aux lettres partagée. Pour plus d'informations, voir [Comparer les groupes](../create-groups/compare-groups.md).  

- **Chiffrement :** Vous ne pouvez pas chiffrer le courrier électronique envoyé à partir d’une boîte aux lettres partagée. Cela est dû au fait qu’une boîte aux lettres partagée ne dispose pas de son propre contexte de sécurité (nom d’utilisateur/mot de passe) et qu’elle ne peut pas recevoir de clé. Si plusieurs personnes sont membres et qu’elles envoient ou reçoivent des courriers électroniques chiffrés avec leurs propres clés, d’autres membres peuvent lire le courrier électronique et d’autres non, en fonction de la clé publique avec laquelle l’e-mail a été chiffré.

- **Conversion de boîtes aux lettres :** Vous pouvez convertir des boîtes aux lettres utilisateur en boîtes aux lettres partagées. Voir [Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md).

- **Rôles d’administrateur :** Les utilisateurs disposant de rôles d’administrateur général ou d’administrateur Exchange peuvent créer des boîtes aux lettres partagées.

- **Conditions requises en matière d’abonnement :** Pour créer une boîte aux lettres partagée, vous devez vous abonner à un forfait Microsoft 365 pour les entreprises qui inclut le courrier électronique (le service Exchange Online). L’abonnement aux applications pour les entreprises Microsoft 365 n’inclut pas le courrier électronique. Microsoft 365 Business standard inclut le courrier électronique.

- **Connexion :** Une boîte aux lettres partagée n’est pas destinée à se connecter directement par son compte d’utilisateur associé. Vous devez toujours bloquer la connexion pour le compte de boîte aux lettres partagé et le conserver bloqué.

- **Nombre d’utilisateurs trop important :** Lorsqu’il y a trop d’utilisateurs désignés qui accèdent simultanément à une boîte aux lettres partagée, ils peuvent ne pas se connecter par intermittence à cette boîte aux lettres. Dans ce cas, vous pouvez réduire le nombre d’utilisateurs ou utiliser une charge de travail différente, un groupe ou un dossier public Microsoft 365.

- **Suppression de message :** Malheureusement, vous ne pouvez pas empêcher les utilisateurs de supprimer des messages dans une boîte aux lettres partagée. La seule façon de le contourner est de créer un groupe Microsoft 365 au lieu d’une boîte aux lettres partagée. Un groupe dans Outlook est semblable à une boîte aux lettres partagée. Pour obtenir une comparaison des deux, consultez la rubrique [compare Groups](../create-groups/compare-groups.md). Pour en savoir plus sur les groupes, consultez la rubrique [en savoir plus sur les groupes](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

## <a name="related-articles"></a>Articles connexes

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md)

[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
