---
title: Autoriser les utilisateurs à réinitialiser leurs mots de passe
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5bc3f460-13cc-48c0-abd6-b80bae72d04a
description: Découvrez comment définir une stratégie pour permettre aux utilisateurs de réinitialiser leur mot de passe à l’aide de l’outil de réinitialisation de mot de passe en libre-service.
ms.openlocfilehash: 2c79d5611ab2db00f4de5f227b0ec2f411955558
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52571852"
---
# <a name="let-users-reset-their-own-passwords"></a>Autoriser les utilisateurs à réinitialiser leurs mots de passe

En tant qu’administrateur Microsoft 365, vous pouvez laisser les utilisateurs utiliser l’outil de réinitialisation de mot de passe [libre-service](https://go.microsoft.com/fwlink/p/?LinkId=522677) afin de ne pas avoir à réinitialiser les mots de passe pour eux. Moins de travail pour vous !
  
## <a name="before-you-begin"></a>Avant de commencer
  
- Vous obtenez la réinitialisation  du mot de passe en libre-service pour les utilisateurs du cloud gratuitement avec n’importe quel plan Microsoft 365 entreprise, éducation ou à but non lucratif. Elle ne fonctionne pas avec Microsoft 365 d’essai.

- Elle utilise Azure. Vous bénéficierez automatiquement et **gratuitement** de cette fonction dans Azure lorsque vous effectuerez ces étapes. L'activation de la réinitialisation du mot de passe libre-service ne vous coûtera rien si vous n'utilisez aucune autre fonctionnalité Azure.

- **Si vous utilisez un active directory** local, les deux points ci-dessus ne s’appliquent pas. Au lieu de cela, vous pouvez configurer cette fonctionnalité, mais elle nécessite un abonnement payant à **Azure AD Premium**.

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../../business-video/admin-center-overview.md)

Vous devez être administrateur général ou administrateur de [mot de](about-admin-roles.md) passe pour effectuer ces étapes.

## <a name="watch-let-users-reset-their-own-passwords"></a>Regardez : laisser les utilisateurs réinitialiser leur mot de passe

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S]

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="steps-let-people-reset-their-own-passwords"></a>Étapes : laisser les utilisateurs réinitialiser leur mot de passe

Ces étapes activent la réinitialisation du mot de passe libre-service pour tout le monde dans votre entreprise.

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration,</a>allez à la page **Paramètres**  >  **paramètres de l’organisation.**

2. En haut de la page **Paramètres de l’organisation,** sélectionnez l’onglet Sécurité **& confidentialité.**
  
3. Sélectionnez **Réinitialiser le mot de passe en libre-service.**

4. Sous **réinitialisation du mot** de passe en **libre-service, sélectionnez Go to the Azure portal to turn on self-service password reset**.

5. Dans le volet de navigation de gauche, sélectionnez **Utilisateurs,** puis, dans le volet **Utilisateurs | Page Tous les utilisateurs,** sélectionnez **Réinitialiser le mot de passe.**
  
6. Dans la page **Propriétés,** **sélectionnez Tout** pour l’activer pour tous les utilisateurs de votre entreprise, puis sélectionnez **Enregistrer.**
  
7. Lorsque vos utilisateurs se connectent, ils sont invités à entrer des informations de contact supplémentaires qui les aideront à réinitialiser leur mot de passe à l’avenir.

## <a name="related-content"></a>Contenu associé

[Définir la stratégie d’expiration de mot de passe pour votre organisation](../manage/set-password-expiration-policy.md) (article)

[Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais](set-password-to-never-expire.md) (article)

[Microsoft 365 Business vidéos de formation](../../business-video/index.yml) (page de liens)
