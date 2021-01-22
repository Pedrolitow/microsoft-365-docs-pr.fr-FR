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
description: Découvrez comment réinitialiser vos mots de passe à l’aide de l’outil de réinitialisation de mot de passe en libre-service.
ms.openlocfilehash: c777b9d840e0e9e467c1283fff94eca9a061ee73
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49925553"
---
# <a name="let-users-reset-their-own-passwords"></a>Autoriser les utilisateurs à réinitialiser leurs mots de passe

En tant qu’administrateur Microsoft 365, vous pouvez laisser les utilisateurs utiliser l’outil de réinitialisation de mot de passe en [libre-service](https://go.microsoft.com/fwlink/p/?LinkId=522677) afin de ne pas avoir à réinitialiser les mots de passe pour eux. Moins de travail pour vous !
  
## <a name="before-you-begin"></a>Avant de commencer
  
- Vous obtenez la réinitialisation  du mot de passe en libre-service pour les utilisateurs du cloud gratuitement avec n’importe quel plan payant Microsoft 365 Business, Éducation ou à but non lucratif. Elle ne fonctionne pas avec la version d’essai de Microsoft 365.

- Elle utilise Azure. Vous bénéficierez automatiquement et **gratuitement** de cette fonction dans Azure lorsque vous effectuerez ces étapes. L'activation de la réinitialisation du mot de passe libre-service ne vous coûtera rien si vous n'utilisez aucune autre fonctionnalité Azure.

- **Si vous utilisez un active directory** local, les deux points ci-dessus ne s’appliquent pas. Au lieu de cela, vous pouvez configurer cette fonctionnalité, mais elle nécessite un abonnement payant **à Azure AD Premium**.

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../admin-overview/admin-overview.md)

Vous devez être administrateur général ou administrateur de [mot de](about-admin-roles.md) passe pour effectuer ces étapes.

## <a name="watch-let-users-reset-their-own-passwords"></a>Regardez : laisser les utilisateurs réinitialiser leur mot de passe

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S]

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

## <a name="steps-let-people-reset-their-own-passwords"></a>Étapes : laisser les utilisateurs réinitialiser leur mot de passe

Ces étapes activent la réinitialisation du mot de passe libre-service pour tout le monde dans votre entreprise.
  
::: moniker range="o365-worldwide"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration,</a>allez à la page **Paramètres** > **de l’organisation.**

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">d’administration,</a>allez à la page Confidentialité de la sécurité  \> **&amp; des** paramètres.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration,</a>go to the **Settings** \> **Settings** \> **Security &amp; privacy** page.

::: moniker-end

2. En haut de la page **Paramètres de l’organisation,** sélectionnez l’onglet Sécurité **& confidentialité.**
  
3. Sélectionnez **Réinitialiser le mot de passe en libre-service.**

4. Sous **réinitialisation du mot** de passe en **libre-service, sélectionnez Go to the Azure portal to turn on self-service password reset**.

5. Dans le volet de navigation de gauche, sélectionnez **Utilisateurs,** puis, dans le volet **Utilisateurs | Page Tous les utilisateurs,** sélectionnez **Réinitialiser le mot de passe.**
  
6. Dans la page **Propriétés,** **sélectionnez Tout** pour l’activer pour tous les utilisateurs de votre entreprise, puis sélectionnez **Enregistrer.**
  
7. Lorsque vos utilisateurs se connectent, ils sont invités à entrer des informations de contact supplémentaires qui les aideront à réinitialiser leur mot de passe à l’avenir.

## <a name="related-content"></a>Contenu connexe

[Définir la stratégie d'expiration des mots de passe pour votre organisation](../manage/set-password-expiration-policy.md)

[Définir le mot de passe d'un utilisateur de façon à ce qu'il n'expire jamais](set-password-to-never-expire.md)

[Vidéos de formation Microsoft 365 Entreprise](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)
