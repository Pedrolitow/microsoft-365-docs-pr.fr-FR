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
ms.openlocfilehash: 21a3505f39f7a822283deddb7c8fcc8c41b1f640
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67469930"
---
# <a name="overview-of-the-users-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Utilisateurs dans Microsoft 365 Lighthouse 

Microsoft 365 Lighthouse vous permet de gérer les utilisateurs entre les comptes clients en sélectionnant l’un des liens sous **Utilisateurs** dans le volet de navigation gauche. À partir de la page Utilisateurs, vous pouvez rechercher des utilisateurs et évaluer et agir sur l’état de sécurité de vos comptes d’utilisateur. Vous pouvez également afficher des insights sur les utilisateurs à risque et l’état de l’authentification multifacteur et de la réinitialisation de mot de passe en libre-service.  
  
## <a name="account-management-page"></a>Page de gestion des comptes  
  
Dans la page Gestion des comptes, vous pouvez rapidement rechercher des utilisateurs spécifiques dans les locataires et effectuer des tâches courantes de gestion des utilisateurs, telles que la mise à jour des informations de compte d’utilisateur, la réinitialisation des mots de passe, l’attribution de licences et la gestion des groupes d’utilisateurs, de la boîte aux lettres ou de OneDrive. Vous pouvez également afficher les comptes inactifs et prendre les actions de sécurité appropriées et récupérer les licences inutilisées.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Capture d’écran de la page Rechercher et utilisateurs inactifs.":::

## <a name="risky-users-page"></a>Page Utilisateurs à risque

La page Utilisateurs à risque affiche les comptes d’utilisateur sur vos locataires qui ont été marqués pour un comportement à risque. Sélectionnez l’un des utilisateurs pour afficher plus d’informations sur un risque détecté ou pour atténuer un risque en réinitialisant le mot de passe d’un utilisateur ou en bloquant la connexion. Pour plus d’informations sur les types de risques et la détection, consultez [Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

La page Utilisateurs à risque comprend également les options suivantes :
- **Exportation:** Sélectionnez cette option pour exporter les données de conformité des appareils vers un fichier de valeurs séparées par des virgules Excel (.csv).
- **Actualiser:** Sélectionnez cette option pour récupérer les données de conformité des appareils les plus actuelles.
- **Vérifiez que les utilisateurs sont compromis :** Sélectionnez cette option pour confirmer que l’utilisateur a été compromis.
- **Ignorer le ou les risques d’utilisateurs :** Sélectionnez cette option pour ignorer le risque de l’utilisateur.  
- **Réinitialiser le mot de passe :** Sélectionnez cette option pour modifier ou réinitialiser le mot de passe de l’utilisateur.
- **Bloquer la connexion :** Sélectionnez cette option pour empêcher quiconque de se connecter en tant qu’utilisateur.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Capture d’écran de la page Utilisateurs à risque.":::

## <a name="multifactor-authentication-page"></a>Page Authentification multifacteur

La page Authentification multifacteur fournit des informations détaillées sur l’état de l’activation de l’authentification multifacteur (MFA) sur vos locataires. Sélectionnez un locataire dans la liste pour afficher plus de détails pour ce locataire, notamment les stratégies d’accès conditionnel nécessitant l’authentification multifacteur qui sont déjà configurées et les utilisateurs qui ne se sont pas encore inscrits à l’authentification multifacteur.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Capture d’écran de la page Authentification multifacteur.":::

## <a name="password-reset-page"></a>Page réinitialisation du mot de passe

La page Réinitialisation de mot de passe affiche des informations détaillées sur l’état de l’activation de la réinitialisation de mot de passe en libre-service sur vos locataires. Il fournit également des insights sur les utilisateurs qui sont activés mais qui doivent toujours s’inscrire avant de pouvoir réinitialiser leur mot de passe par eux-mêmes.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Capture d’écran de la page réinitialisation du mot de passe.":::

## <a name="related-content"></a>Contenu associé

[Microsoft 365 Lighthouse vue d’ensemble de la page de conformité des appareils](m365-lighthouse-device-compliance-page-overview.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
