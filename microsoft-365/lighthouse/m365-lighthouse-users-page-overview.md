---
title: vue d Microsoft 365 Lighthouse de la page Utilisateurs
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Utilisateurs.
ms.openlocfilehash: fad5ff4b41b43efb68c7e230401b80e50cea95a4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329936"
---
# <a name="microsoft-365-lighthouse-users-page-overview"></a>vue d Microsoft 365 Lighthouse de la page Utilisateurs 

Microsoft 365 Lighthouse vous permet de gérer les utilisateurs sur plusieurs comptes clients en sélectionnant Utilisateurs dans le volet de navigation de gauche pour ouvrir la page Utilisateurs. À partir de cette page, vous pouvez rechercher des utilisateurs, évaluer et agir sur l’état de sécurité de vos comptes d’utilisateurs. Vous pouvez également afficher des informations sur les utilisateurs à risque et l’état de l’authentification multifacteur et de la réinitialisation du mot de passe en libre-service.  
  
## <a name="search-users-tab"></a>Onglet Utilisateurs de la recherche  
  
À partir de l’onglet Utilisateurs de recherche, vous pouvez rapidement rechercher des utilisateurs spécifiques dans les clients et effectuer des actions de gestion des utilisateurs de base, telles que la réinitialisation d’un mot de passe de compte.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Capture d’écran de l’onglet Utilisateurs de la recherche.":::

## <a name="risky-users-tab"></a>Onglet Utilisateurs à risque

L’onglet Utilisateurs à risque affiche les comptes d’utilisateurs au sein de vos clients qui ont été signalés pour un comportement à risque. Sélectionnez l’un des utilisateurs pour afficher plus d’informations sur un risque détecté ou pour atténuer un risque en réinitialisation du mot de passe d’un utilisateur ou en bloquant la signature. Pour plus d’informations sur les types de risque et la détection, voir [Qu’est-ce qu’un risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

L’onglet Utilisateurs à risque inclut également les options suivantes :
- **Exporter :** Sélectionnez cette sélection pour exporter les données de conformité des appareils vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Actualiser :** Sélectionnez cette sélection pour récupérer les données de conformité des appareils les plus récentes.
- **Confirmez que les utilisateurs sont compromis :** Sélectionnez cette sélection pour confirmer que l’utilisateur a été compromis.
- **Ignorer les risques pour les utilisateurs :** Sélectionnez cette sélection pour ignorer les risques pour l’utilisateur.  
- **Réinitialisez le mot de passe :** Sélectionnez pour modifier ou réinitialiser le mot de passe de l’utilisateur.
- **Bloquer la connectez-vous :** Sélectionnez cette sélection pour empêcher tout le monde de se signer en tant qu’utilisateur.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Capture d’écran de l’onglet Utilisateurs à risque.":::

## <a name="multifactor-authentication-tab"></a>Onglet Authentification multifacteur

L’onglet Authentification multifacteur fournit des informations détaillées sur l’état de l’authentification multifacteur (MFA) sur vos locataires. Sélectionnez n’importe quel client dans la liste pour voir plus de détails sur ce client, notamment les stratégies d’accès conditionnel qui requièrent l’ation MFA qui sont déjà configurées et les utilisateurs qui ne sont pas encore inscrits à l’mf.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Capture d’écran de l’onglet Authentification multifacteur.":::

## <a name="password-reset-tab"></a>Onglet Réinitialisation du mot de passe

L’onglet Réinitialisation du mot de passe affiche des informations détaillées sur l’état de l’enablement de réinitialisation de mot de passe en libre-service pour tous vos clients. Il fournit également des informations sur les utilisateurs activés, mais qui doivent s’inscrire avant de pouvoir réinitialiser leur mot de passe par eux-mêmes.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Capture d’écran de l’onglet Réinitialisation du mot de passe.":::

## <a name="related-content"></a>Contenu associé

[Microsoft 365 Lighthouse page de conformité des appareils](m365-lighthouse-device-compliance-page-overview.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
