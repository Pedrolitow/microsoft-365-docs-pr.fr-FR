---
title: À propos des boîtes aux lettres partagées
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
description: Les boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes ont besoin d’accéder à la même boîte aux lettres. Découvrez ce que vous devez savoir avant de créer une boîte aux lettres partagée.
ms.openlocfilehash: 744c4fece24cf1fa5ee7259a0d722ff123ff2664
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49926509"
---
# <a name="about-shared-mailboxes"></a>À propos des boîtes aux lettres partagées

Les Boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique, du bureau d'accueil, ou d'un autre poste pouvant être partagé par plusieurs personnes.

Les utilisateurs disposant d’autorisations sur la boîte aux lettres du groupe peuvent Envoyer en tant que ou Envoyer de la part pour le compte de l’adresse de messagerie de la boîte aux lettres si l’administrateur leur a accordé cette autorisation. Cette fonctionnalité est particulièrement utile pour les boîtes aux lettres d’aide et de support, car les utilisateurs peuvent envoyer des e-mails à partir du « Support technique de Contoso » ou du « Bureau d'accueil du bâtiment A ».

Avant de [créer une boîte aux lettres partagée,](create-a-shared-mailbox.md)voici quelques éléments que vous devez connaître :

- **Licences :** Votre boîte aux lettres partagée peut stocker jusqu’à 50 Go de données sans que vous ne lui attribuiez de licence. Après cela, vous devez attribuer une licence à la boîte aux lettres pour stocker davantage de données. Pour plus d’informations sur les licences de boîtes aux lettres partagées, consultez [les limites d’Exchange Online.](https://technet.microsoft.com/library/exchange-online-limits.aspx#StorageLimits) Lorsqu'une boîte aux lettres partagée atteint sa limite de stockage, vous serez en mesure de recevoir des courriers électroniques pendant un certain temps, mais vous ne pourrez pas envoyer de nouveaux messages électroniques. Puis, après cela, vous ne pourrez plus recevoir de message. Les expéditeurs des courriers vers votre boîte aux lettres recevront un accusé de réception négatif.

- **Autorisations utilisateur :** Vous devez accorder aux utilisateurs des autorisations (appartenance) pour utiliser la boîte aux lettres partagée. Seules les personnes internes à votre organisation peuvent utiliser une boîte aux lettres partagée.

- **Utilisateurs externes :** Vous ne pouvez pas accorder à des personnes extérieures à votre entreprise (par exemple, des personnes ayant un compte Gmail) l’accès à votre boîte aux lettres partagée. Si vous voulez effectuer cette action, envisagez plutôt de créer un groupe pour Outlook. Pour plus d’informations, [voir Créer un groupe Microsoft 365 dans le Centre d’administration.](../create-groups/create-groups.md)

- **À utiliser avec Outlook :** En plus d’utiliser Outlook sur le web à partir de votre navigateur pour accéder aux boîtes aux lettres partagées, vous pouvez également utiliser l’application Outlook pour iOS ou Outlook pour Android. Pour plus d’informations, voir [Ajouter une boîte aux lettres partagée à Outlook Mobile.](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f) Une autre option consiste à créer un groupe pour votre boîte aux lettres partagée. Pour plus d'informations, voir [Comparer les groupes](../create-groups/compare-groups.md).

- **Chiffrement :** Vous ne pouvez pas chiffrer les messages électroniques envoyés à partir d’une boîte aux lettres partagée. Cela est dû au fait qu’une boîte aux lettres partagée ne possède pas son propre contexte de sécurité (nom d’utilisateur/mot de passe) et ne peut donc pas être affectée à une clé. Si plusieurs personnes sont membres et qu’elles envoient/reçoivent des e-mails qu’elles ont chiffrés avec leurs propres clés, d’autres membres peuvent être en mesure de lire le courrier électronique et d’autres non, selon la clé publique avec laquelle le message a été chiffré.

- **Conversion de boîte aux lettres :** Vous pouvez convertir des boîtes aux lettres utilisateur en boîtes aux lettres partagées. Voir [Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md).

- **Rôles d’administrateur :** Les utilisateurs ayant des rôles d’administrateur global ou d’administrateur Exchange peuvent créer des boîtes aux lettres partagées.

- **Conditions d’abonnement :** Pour créer une boîte aux lettres partagée, vous devez vous abonner à une offre Microsoft 365 pour les entreprises qui inclut la messagerie (le service Exchange Online). L’abonnement Microsoft 365 Apps for business n’inclut pas la messagerie. Microsoft 365 Business Standard inclut le courrier électronique.

- **La signature :** Une boîte aux lettres partagée n’est pas destinée à la signature directe par son compte d’utilisateur associé. Vous devez toujours bloquer la connectez-vous pour le compte de boîte aux lettres partagé et le conserver bloqué.

- **Trop d’utilisateurs :** Lorsqu’un trop grand nombre d’utilisateurs désignés accèdent simultanément à une boîte aux lettres partagée, il se peut qu’ils ne parviennent pas à se connecter à cette boîte aux lettres par intermittence. Dans ce cas, vous pouvez envisager de réduire le nombre d’utilisateurs ou d’utiliser une charge de travail différente, comme un groupe Microsoft 365 ou un dossier public.

- **Suppression de message :** Malheureusement, vous ne pouvez pas empêcher les utilisateurs de supprimer des messages dans une boîte aux lettres partagée. La seule solution consiste à créer un groupe Microsoft 365 au lieu d’une boîte aux lettres partagée. Un groupe dans Outlook est comme une boîte aux lettres partagée. Pour une comparaison des deux, voir [Comparer les groupes.](../create-groups/compare-groups.md) Pour en savoir plus sur les groupes, voir [En savoir plus sur les groupes.](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

## <a name="related-articles"></a>Articles connexes

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md)

[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
