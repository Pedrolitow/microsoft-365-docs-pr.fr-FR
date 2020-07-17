---
title: Autoriser les utilisateurs à réinitialiser leur mot de passe
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
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5bc3f460-13cc-48c0-abd6-b80bae72d04a
description: Découvrez comment réinitialiser vos mots de passe à l’aide de l’outil de réinitialisation du mot de passe libre-service.
ms.openlocfilehash: 288613023ee61626bf12f7090ad0ff73139ef06d
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780588"
---
# <a name="let-users-reset-their-own-passwords"></a>Autoriser les utilisateurs à réinitialiser leur mot de passe

Vous êtes inondé de demandes de réinitialisation de mots de passe ? En tant qu’administrateur 365 de Microsoft, vous pouvez autoriser les utilisateurs à utiliser l' [outil de réinitialisation du mot de passe libre-service](https://go.microsoft.com/fwlink/p/?LinkId=522677) afin de ne pas avoir à réinitialiser leur mot de passe. Moins de travail pour vous ! 
  
Voici quelques informations à retenir :
  
- Vous bénéficiez d’une réinitialisation du mot de passe en libre-service pour les utilisateurs du Cloud **gratuitement** avec les plans payants Microsoft 365 Business, Education ou imprévus. Elle ne fonctionne pas avec la version d’évaluation de Microsoft 365.

- Elle utilise Azure. Vous bénéficierez automatiquement et **gratuitement** de cette fonction dans Azure lorsque vous effectuerez ces étapes. L'activation de la réinitialisation du mot de passe libre-service ne vous coûtera rien si vous n'utilisez aucune autre fonctionnalité Azure.

- **Si vous utilisez un annuaire Active Directory local**, les deux points ci-dessus ne s’appliquent pas. Au lieu de cela, vous pouvez configurer cela, mais **il nécessite un abonnement payant à Azure ad Premium**.

Regardez une courte vidéo sur la façon de permettre aux utilisateurs de réinitialiser leur mot de passe. <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S]

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

## <a name="let-people-reset-their-own-passwords"></a>Autoriser les utilisateurs à réinitialiser leur mot de passe

Ces étapes activent la réinitialisation du mot de passe libre-service pour tout le monde dans votre entreprise.
  
::: moniker range="o365-worldwide"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration</a>, accédez à **Settings** la > page Paramètres d' **organisation** des paramètres.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **paramètres** de \> ** &amp; confidentialité** de la sécurité.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la **Settings** \> **Settings** \> page ** &amp; confidentialité** de la sécurité des paramètres de paramètres.

::: moniker-end

2. En haut de la page **paramètres** de l’organisation, sélectionnez l’onglet **sécurité & confidentialité** .
  
3. Sélectionnez **réinitialisation du mot de passe en libre-service**.

4. Sous **réinitialisation du mot de passe libre-service**, sélectionnez **accéder au portail Azure pour activer la réinitialisation du mot de passe libre-service**.

5. Dans le volet de navigation de gauche, sélectionnez **utilisateurs**, puis, dans le volet **utilisateurs | Page tous les utilisateurs** , sélectionnez **Réinitialiser le mot de passe**.
  
6. Sur la page **Propriétés** , sélectionnez **tous** pour l’activer pour tous les membres de votre entreprise, puis sélectionnez **Enregistrer**.
  
7. Lorsque les utilisateurs se connectent, ils sont invités à entrer des informations de contact supplémentaires qui les aideront à réinitialiser leur mot de passe à l’avenir.

## <a name="related-articles"></a>Articles connexes

[Définir la stratégie d'expiration des mots de passe pour votre organisation](../manage/set-password-expiration-policy.md)
  
[Définir le mot de passe d'un utilisateur de façon à ce qu'il n'expire jamais](set-password-to-never-expire.md)

[Vidéos de formation Microsoft 365 Entreprise](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)
