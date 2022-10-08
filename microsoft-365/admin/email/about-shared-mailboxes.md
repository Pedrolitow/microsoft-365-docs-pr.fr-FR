---
title: À propos des boîtes aux lettres partagées
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Les boîtes aux lettres partagées servent lorsque plusieurs personnes doivent accéder à la même boîte aux lettres. Découvrez les éléments à connaître avant de créer une boîte aux lettres partagée.
ms.openlocfilehash: d7d4bf06fa9e91bca7a3847a9db99aee0a6ca97f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68204956"
---
# <a name="about-shared-mailboxes"></a>À propos des boîtes aux lettres partagées

Les Boîtes aux lettres partagées sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique, du bureau d'accueil, ou d'un autre poste pouvant être partagé par plusieurs personnes.

Les utilisateurs disposant d’autorisations sur la boîte aux lettres du groupe peuvent Envoyer en tant que ou Envoyer de la part pour le compte de l’adresse de messagerie de la boîte aux lettres si l’administrateur leur a accordé cette autorisation. Cette fonctionnalité est particulièrement utile pour les boîtes aux lettres d’aide et de support, car les utilisateurs peuvent envoyer des e-mails à partir du « Support technique de Contoso » ou du « Bureau d'accueil du bâtiment A ».

## <a name="before-you-begin"></a>Avant de commencer

Avant de [créer une boîte aux lettres partagée](create-a-shared-mailbox.md), voici quelques points à connaître :

- **Licences :** Votre boîte aux lettres partagée peut stocker jusqu’à 50 Go de données sans que vous n’ayez besoin de lui attribuer une licence. Après cela, vous devez attribuer une licence à la boîte aux lettres pour stocker davantage de données. Si vous souhaitez en savoir plus sur les licences de boîte aux lettres partagées, veuillez consulter la rubrique [Exchange Online limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Lorsqu'une boîte aux lettres partagée atteint sa limite de stockage, vous serez en mesure de recevoir des courriers électroniques pendant un certain temps, mais vous ne pourrez pas envoyer de nouveaux messages électroniques. Puis, après cela, vous ne pourrez plus recevoir de message. Les expéditeurs des courriers vers votre boîte aux lettres recevront un accusé de réception négatif.

- **User permissions:** You need to give users permissions (membership) to use the shared mailbox. Only people inside your organization can use a shared mailbox.

- **External users:** You can't give people outside your business (such as people with a Gmail account) access to your shared mailbox. If you want to do this, consider creating a group for Outlook instead. To learn more, see [Create a Microsoft 365 group in the admin center](../create-groups/create-groups.md).

- **Utilisation avec Outlook :** outre l’utilisation d’Outlook sur le web depuis votre navigateur pour accéder aux boîtes aux lettres partagées, vous pouvez également utiliser l’application Outlook pour iOS ou Outlook pour Android. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Ajouter une boîte aux lettres partagée dans Outlook Mobile](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). Vous pouvez également créer un groupe pour votre boîte aux lettres partagée. Pour plus d'informations, voir [Comparer les groupes](../create-groups/compare-groups.md).

- **Chiffrement :** vous ne pouvez pas chiffrer l’e-mail envoyé depuis une boîte aux lettres partagée. Cela s’explique par le fait qu’une boîte aux lettres partagée ne dispose pas de sa propre stratégie de sécurité (nom d’utilisateur/mot de passe) et que celle-ci ne peut donc pas se voir attribuer de clé. Si plusieurs personnes sont membres et envoient/reçoivent des messages électroniques chiffrés à l’aide de leur propre clé, certains membres pourront lire le message électronique et d’autres pas, selon la clé publique ayant servi à chiffrer le message.

- **Conversion de boîte aux lettres :** Vous pouvez convertir des boîtes aux lettres utilisateur en boîtes aux lettres partagées. Voir [Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md).

- **Rôles d'administrateur :** les utilisateurs dotés du rôle d’administrateur général ou Administrateur Exchange peuvent créer des boîtes aux lettres partagées.

- **Conditions d’abonnement :** pour créer une boîte aux lettres partagée, vous devez vous abonner à une offre Microsoft 365 Entreprise incluant l’e-mail (service Exchange Online). L’abonnement Microsoft 365 Apps for business n’inclut pas l’e-mail. Microsoft 365 Business Standard inclut bel et bien l’e-mail.

- **Connexion :** une boîte aux lettres partagée n’est pas destinée à la connexion directe par le compte d’utilisateur associé. Vous devez toujours bloquer la connexion au compte de boîte aux lettres partagée, puis la conserver bloquée.

- **Trop d’utilisateurs :** lorsqu’un trop grand nombre d’utilisateurs désignés accèdent simultanément à une boîte aux lettres partagée (pas plus de 25 est recommandé), ils peuvent échouer par intermittence à se connecter à cette boîte aux lettres ou présenter des incohérences telles que le doublon des messages dans la boîte d’envoi. Dans ce cas, vous pouvez envisager de réduire le nombre d’utilisateurs ou d’utiliser une charge de travail différente, telle qu’un groupe Microsoft 365 ou un dossier public.

- **Suppression de messages :** malheureusement, vous ne pouvez pas empêcher les personnes de supprimer des courriers dans une boîte aux lettres partagée. La seule façon de contourner ce problème consiste à [créer un groupe Microsoft 365](/microsoft-365/admin/create-groups/create-groups) au lieu d’une boîte aux lettres partagée. Dans Outlook, les groupes sont semblables à une boîte aux lettres partagée. Si vous souhaitez obtenir une comparaison des deux options, veuillez consulter la rubrique [Comparer les groupes](../create-groups/compare-groups.md). Pour en savoir plus sur les groupes, consultez [En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

- **Multigéographique** Dans un environnement multigéographique, les boîtes aux lettres partagées doivent être concédées sous licence de la même façon qu’une boîte aux lettres utilisateur. Notez que l’audit intergéographique des boîtes aux lettres n’est pas pris en charge. Par exemple, si un utilisateur se voit attribuer les autorisations d’accès à une boîte aux lettres partagée dans un autre emplacement géographique, les actions de boîte aux lettres effectuées par cet utilisateur ne sont pas enregistrées dans le journal d’audit de la boîte aux lettres partagée. 


> [!NOTE]
> Pour accéder à une boîte aux lettres partagée, un utilisateur doit disposer d’une licence Exchange Online, mais la boîte aux lettres partagée ne nécessite pas de licence séparée. Chaque boîte aux lettres partagée a un compte d'utilisateur correspondant. Vous n'avez pas été invité à fournir un mot de passe lors de la création de la boîte aux lettres partagée ? Le compte a un mot de passe qui est généré par le système (inconnu). Vous ne devez pas utiliser le compte pour vous connecter à la boîte aux lettres partagée. Sans licence, les boîtes aux lettres partagées sont limitées à 50 Go. Pour augmenter la taille limite à 100 Go, une licence Exchange Online Plan 2 doit être attribuée à la boîte aux lettres partagée. La licence Exchange Online Plan 1 avec une licence de module complémentaire d’archivage Exchange Online augmente uniquement la taille de la boîte aux lettres d’archivage. Cela vous permet également d’activer l’archivage à extension automatique pour une capacité de stockage d’archivage supplémentaire. De même, si vous voulez placer une boîte aux lettres partagée au maintien d’un litige, la boîte aux lettres partagée doit avoir une licence Exchange Online Plan 2 ou une licence Exchange Online Plan 1 avec une licence de composant additionnel archivage Exchange Online. Si vous souhaitez appliquer des fonctionnalités avancées telles que Microsoft Defender pour Office 365, eDiscovery (Premium) ou des stratégies de rétention automatique, la boîte aux lettres partagée doit être concédée sous licence pour ces fonctionnalités.

> [!NOTE]
> Avant juillet 2018, toutes les boîtes aux lettres partagées sans licence avaient une taille de 100 Go. Pour plus [d’informations, consultez Correction de l’approvisionnement et du dimensionnement des boîtes aux lettres partagées](https://techcommunity.microsoft.com/t5/exchange-team-blog/correcting-shared-mailbox-provisioning-and-sizing/ba-p/607991).

## <a name="related-content"></a>Contenu associé

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)
