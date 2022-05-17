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
ms.localizationpriority: medium
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
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5bc3f460-13cc-48c0-abd6-b80bae72d04a
description: Découvrez comment définir une stratégie dans le Centre d'administration Microsoft 365 pour permettre aux utilisateurs de réinitialiser leurs propres mots de passe à l’aide de l’outil de réinitialisation de mot de passe en libre-service.
ms.openlocfilehash: 2ade056638db03a0a38b7fe2bdacfe3d6d2e4530
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436688"
---
# <a name="let-users-reset-their-own-passwords"></a>Autoriser les utilisateurs à réinitialiser leurs mots de passe

En tant qu’administrateur Microsoft 365, vous pouvez autoriser les utilisateurs à utiliser [l’outil de réinitialisation de mot de passe en libre-service](https://go.microsoft.com/fwlink/p/?LinkId=522677) afin de ne pas avoir à réinitialiser les mots de passe pour eux. Moins de travail pour vous !

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.
 
## <a name="watch-let-users-reset-their-own-passwords"></a>Regarder : Permettre aux utilisateurs de réinitialiser leurs propres mots de passe

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S]

1. Dans le Centre d'administration Microsoft 365, dans le volet de navigation de gauche, sélectionnez **Paramètres** >  **Paramètres**, puis <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sécurité & confidentialité**</a>.
1. Sous **Laisser vos utilisateurs réinitialiser leurs propres mots de passe**, sélectionnez **Le Centre d’administrationAzure AD**.
1. Dans le volet de navigation de gauche, sélectionnez **Utilisateurs**, puis, dans la page **Utilisateurs - tous les utilisateurs** , sélectionnez **Réinitialiser le mot de passe**.
1. Sélectionnez **Tout** pour activer la réinitialisation de mot de passe en libre-service, puis **sélectionnez Enregistrer**.

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).
 
## <a name="before-you-begin"></a>Avant de commencer
  
- Vous bénéficiez gratuitement de la réinitialisation de mot de passe en libre-service **pour les** utilisateurs du cloud avec n’importe quel Microsoft 365 plan payant pour les entreprises, l’éducation ou les organisations à but non lucratif. Cela ne fonctionne pas avec Microsoft 365 version d’évaluation.

- Elle utilise Azure. Vous bénéficierez automatiquement et **gratuitement** de cette fonction dans Azure lorsque vous effectuerez ces étapes. L'activation de la réinitialisation du mot de passe libre-service ne vous coûtera rien si vous n'utilisez aucune autre fonctionnalité Azure.

- **Si vous utilisez un Active Directory local**, les deux points ci-dessus ne s’appliquent pas. Au lieu de cela, vous pouvez configurer cette option, mais **elle nécessite un abonnement payant pour Azure AD Premium**.

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?] (Vue d’ensemble de la Centre d'administration Microsoft 365](.. /admin-overview/admin-center-overview.md)

Vous devez être [administrateur général ou administrateur de mot de passe](about-admin-roles.md) pour effectuer ces étapes.

## <a name="steps-let-people-reset-their-own-passwords"></a>Étapes : permettre aux utilisateurs de réinitialiser leurs propres mots de passe

Ces étapes activent la réinitialisation du mot de passe libre-service pour tout le monde dans votre entreprise.

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration</a>, accédez à la page des **paramètres** **Paramètres** >  Org.

2. En haut de la page **Paramètres de l’organisation** , sélectionnez l’onglet **Sécurité & Confidentialité** .
  
3. Sélectionnez **Réinitialisation de mot de passe en libre-service**.

4. Sous **Réinitialisation de mot de passe en libre-service**, **sélectionnez Atteindre le Portail Azure pour activer la réinitialisation de mot de passe en libre-service**.

5. Dans la page **Propriétés** , sélectionnez **Tout** pour l’activer pour tous les membres de votre entreprise, puis **sélectionnez Enregistrer**.
  
6. Lorsque vos utilisateurs se connectent, ils sont invités à entrer des informations de contact supplémentaires qui les aideront à réinitialiser leur mot de passe à l’avenir.

## <a name="related-content"></a>Contenu connexe

[Définir la stratégie d’expiration du mot de passe pour votre organisation](../manage/set-password-expiration-policy.md) (article)\
[Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais](set-password-to-never-expire.md) (article)\
[vidéos de formation Microsoft 365 Business](../../business-video/index.yml) (page de liens)
