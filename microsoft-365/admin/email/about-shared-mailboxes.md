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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Les boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes ont besoin d’accéder à la même boîte aux lettres. Découvrez ce que vous devez savoir avant de créer une boîte aux lettres partagée.
ms.openlocfilehash: f6c03787db890e1963f659aa9d2ece052d50a82c
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53541636"
---
# <a name="about-shared-mailboxes"></a>À propos des boîtes aux lettres partagées

Les Boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique, du bureau d'accueil, ou d'un autre poste pouvant être partagé par plusieurs personnes.

Les utilisateurs disposant d’autorisations sur la boîte aux lettres du groupe peuvent Envoyer en tant que ou Envoyer de la part pour le compte de l’adresse de messagerie de la boîte aux lettres si l’administrateur leur a accordé cette autorisation. Cette fonctionnalité est particulièrement utile pour les boîtes aux lettres d’aide et de support, car les utilisateurs peuvent envoyer des e-mails à partir du « Support technique de Contoso » ou du « Bureau d'accueil du bâtiment A ».

## <a name="before-you-begin"></a>Avant de commencer

Avant de [créer une boîte aux lettres partagée,](create-a-shared-mailbox.md)voici quelques éléments que vous devez connaître :

- **Licences :** Votre boîte aux lettres partagée peut stocker jusqu’à 50 Go de données sans que vous lui attribuiez de licence. Après cela, vous devez attribuer une licence à la boîte aux lettres pour stocker davantage de données. Pour plus d’informations sur les licences de boîtes aux lettres partagées, consultez [Exchange Online limites.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits) Lorsqu'une boîte aux lettres partagée atteint sa limite de stockage, vous serez en mesure de recevoir des courriers électroniques pendant un certain temps, mais vous ne pourrez pas envoyer de nouveaux messages électroniques. Puis, après cela, vous ne pourrez plus recevoir de message. Les expéditeurs des courriers vers votre boîte aux lettres recevront un accusé de réception négatif.

- **Autorisations utilisateur :** Vous devez accorder aux utilisateurs des autorisations (appartenance) pour utiliser la boîte aux lettres partagée. Seules les personnes internes à votre organisation peuvent utiliser une boîte aux lettres partagée.

- **Utilisateurs externes :** Vous ne pouvez pas accorder à des personnes extérieures à votre entreprise (par exemple, des personnes ayant un compte Gmail) l’accès à votre boîte aux lettres partagée. Si vous voulez effectuer cette action, envisagez plutôt de créer un groupe pour Outlook. Pour plus d’informations, voir [Créer un Microsoft 365 dans le Centre d’administration.](../create-groups/create-groups.md)

- **À utiliser avec Outlook :** Outre l’Outlook sur le web à partir de votre navigateur pour accéder aux boîtes aux lettres partagées, vous pouvez également utiliser l’application Outlook pour iOS ou l’application Outlook pour Android. Pour plus d’informations, voir [Ajouter une boîte aux lettres partagée à Outlook mobile.](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f) Une autre option consiste à créer un groupe pour votre boîte aux lettres partagée. Pour plus d'informations, voir [Comparer les groupes](../create-groups/compare-groups.md).

- **Chiffrement :** Vous ne pouvez pas chiffrer les messages électroniques envoyés à partir d’une boîte aux lettres partagée. Cela est dû au fait qu’une boîte aux lettres partagée ne possède pas son propre contexte de sécurité (nom d’utilisateur/mot de passe) et ne peut donc pas être affectée à une clé. Si plusieurs personnes sont membres et qu’elles envoient/reçoivent des e-mails qu’elles ont chiffrés avec leurs propres clés, d’autres membres peuvent être en mesure de lire le courrier électronique et d’autres non, selon la clé publique avec laquelle le message a été chiffré.

- **Conversion de boîte aux lettres :** Vous pouvez convertir des boîtes aux lettres utilisateur en boîtes aux lettres partagées. Voir [Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md).

- **Rôles d’administrateur :** Les utilisateurs ayant des rôles d’administrateur Exchange ou d’administrateur peuvent créer des boîtes aux lettres partagées.

- **Conditions d’abonnement :** Pour créer une boîte aux lettres partagée, vous devez vous abonner à une offre Microsoft 365 entreprise qui inclut la messagerie (le service Exchange Online). L Applications Microsoft 365 pour les PME’abonnement n’inclut pas de courrier électronique. Microsoft 365 Business Standard n’inclut pas de courrier électronique.

- **La signature :** Une boîte aux lettres partagée n’est pas destinée à la signature directe par son compte d’utilisateur associé. Vous devez toujours bloquer la connectez-vous pour le compte de boîte aux lettres partagé et le conserver bloqué.

- **Trop d’utilisateurs :** Lorsqu’il y a trop d’utilisateurs désignés qui accèdent simultanément à une boîte aux lettres partagée (pas plus de 25 est recommandé), ils risquent de ne pas pouvoir se connecter à cette boîte aux lettres par intermittence ou d’avoir des incohérences telles que la duplication des messages dans la boîte d’envoi. Dans ce cas, vous pouvez envisager de réduire le nombre d’utilisateurs ou d’utiliser une charge de travail différente, telle qu’un groupe Microsoft 365 ou un dossier public.

- **Suppression de message :** Malheureusement, vous ne pouvez pas empêcher des personnes de supprimer des messages dans une boîte aux lettres partagée. La seule solution consiste à créer un groupe Microsoft 365 au lieu d’une boîte aux lettres partagée. Un groupe dans Outlook est comme une boîte aux lettres partagée. Pour une comparaison des deux, voir [Comparer les groupes.](../create-groups/compare-groups.md) Pour en savoir plus sur les groupes, voir [En savoir plus sur les groupes.](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)


> [!NOTE]
> Pour accéder à une boîte aux lettres partagée, un utilisateur doit avoir une licence Exchange Online, mais la boîte aux lettres partagée ne nécessite pas de licence distincte. Chaque boîte aux lettres partagée a un compte d'utilisateur correspondant. Vous n'avez pas été invité à fournir un mot de passe lors de la création de la boîte aux lettres partagée ? Le compte a un mot de passe qui est généré par le système (inconnu). Vous ne devez pas utiliser le compte pour vous connecter à la boîte aux lettres partagée. Sans licence, les boîtes aux lettres partagées sont limitées à 50 Go. Pour augmenter la taille limite de 100 Go, la boîte aux lettres partagée doit être attribuée à une licence Exchange Online (plan 2) ou une licence Exchange Online (plan 1) avec une licence de composant additionnel d’archivage Exchange Online. Cela vous permet également d’activer l’archivage à extension automatique pour une quantité illimitée de capacité de stockage d’archive. De même, si vous voulez placer une boîte aux lettres partagée au maintien d’un litige, la boîte aux lettres partagée doit avoir une licence Exchange Online Plan 2 ou une licence Exchange Online Plan 1 avec une licence de composant additionnel archivage Exchange Online. Si vous souhaitez appliquer des fonctionnalités avancées telles que Microsoft Defender pour Office 365, Advanced eDiscovery ou des stratégies de rétention automatique, la boîte aux lettres partagée doit être titulaire d’une licence pour ces fonctionnalités.

## <a name="related-content"></a>Contenu associé

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)
