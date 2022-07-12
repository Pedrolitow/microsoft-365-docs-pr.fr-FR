---
title: Vue d’ensemble de la page Utilisateurs dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez la page Utilisateurs.
ms.openlocfilehash: 05c889167cc7359900c0dea3396e657c0aa93fba
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717557"
---
# <a name="overview-of-the-users-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Utilisateurs dans Microsoft 365 Lighthouse 

Microsoft 365 Lighthouse vous permet de gérer les utilisateurs entre les comptes clients en sélectionnant l’un des liens sous **Utilisateurs** dans le volet de navigation gauche. À partir de la page Utilisateurs, vous pouvez rechercher des utilisateurs et évaluer et agir sur l’état de sécurité de vos comptes d’utilisateur. Vous pouvez également afficher des insights sur les utilisateurs à risque et l’état de l’authentification multifacteur et de la réinitialisation de mot de passe en libre-service.  
  
## <a name="search-users-tab"></a>Onglet Rechercher des utilisateurs  
  
Sous l’onglet Rechercher des utilisateurs, vous pouvez rapidement rechercher des utilisateurs spécifiques dans les locataires et effectuer des tâches courantes de gestion des utilisateurs, telles que la mise à jour des informations de compte d’utilisateur, la réinitialisation des mots de passe, l’attribution de licences et la gestion des groupes d’utilisateurs, de la boîte aux lettres ou de OneDrive.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Capture d’écran de l’onglet Rechercher des utilisateurs.":::

## <a name="risky-users-tab"></a>Onglet Utilisateurs à risque

L’onglet Utilisateurs à risque affiche les comptes d’utilisateur sur vos locataires qui ont été marqués pour un comportement à risque. Sélectionnez l’un des utilisateurs pour afficher plus d’informations sur un risque détecté ou pour atténuer un risque en réinitialisant le mot de passe d’un utilisateur ou en bloquant la connexion. Pour plus d’informations sur les types de risques et la détection, consultez [Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

L’onglet Utilisateurs à risque comprend également les options suivantes :
- **Exportation:** Sélectionnez cette option pour exporter les données de conformité des appareils vers un fichier de valeurs séparées par des virgules Excel (.csv).
- **Actualiser:** Sélectionnez cette option pour récupérer les données de conformité des appareils les plus actuelles.
- **Vérifiez que les utilisateurs sont compromis :** Sélectionnez cette option pour confirmer que l’utilisateur a été compromis.
- **Ignorer le ou les risques d’utilisateurs :** Sélectionnez cette option pour ignorer le risque de l’utilisateur.  
- **Réinitialiser le mot de passe :** Sélectionnez cette option pour modifier ou réinitialiser le mot de passe de l’utilisateur.
- **Bloquer la connexion :** Sélectionnez cette option pour empêcher quiconque de se connecter en tant qu’utilisateur.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Capture d’écran de l’onglet Utilisateurs à risque.":::

## <a name="multifactor-authentication-tab"></a>Onglet Authentification multifacteur

L’onglet Authentification multifacteur fournit des informations détaillées sur l’état de l’activation de l’authentification multifacteur (MFA) sur vos locataires. Sélectionnez un locataire dans la liste pour afficher plus de détails pour ce locataire, notamment les stratégies d’accès conditionnel nécessitant l’authentification multifacteur qui sont déjà configurées et les utilisateurs qui ne se sont pas encore inscrits à l’authentification multifacteur.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Capture d’écran de l’onglet Authentification multifacteur.":::

## <a name="password-reset-tab"></a>Onglet Réinitialisation du mot de passe

L’onglet Réinitialisation de mot de passe affiche des informations détaillées sur l’état de l’activation de la réinitialisation de mot de passe en libre-service sur vos locataires. Il fournit également des insights sur les utilisateurs qui sont activés mais qui doivent toujours s’inscrire avant de pouvoir réinitialiser leur mot de passe par eux-mêmes.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Capture d’écran de l’onglet Réinitialisation du mot de passe.":::

## <a name="related-content"></a>Contenu associé

[Microsoft 365 Lighthouse vue d’ensemble de la page de conformité des appareils](m365-lighthouse-device-compliance-page-overview.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
