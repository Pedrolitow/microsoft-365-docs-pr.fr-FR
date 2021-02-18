---
title: Fonctionnalités d’aperçu dans Microsoft 365 Defender
description: En savoir plus sur les nouvelles fonctionnalités de la Sécurité Microsoft 365
keywords: aperçu, nouveautés, sécurité M365, sécurité, 365, capacités
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 1636b1deb5f35d8286b33238a8f4bbfff0b33521
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50288124"
---
# <a name="microsoft-365-defender-preview-features"></a>Fonctionnalités d’aperçu de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> [!IMPORTANT]
> Les versions d’aperçu sont fournies sans contrat de niveau de service et ne sont pas recommandées pour les charges de travail de production. Certaines fonctionnalités peuvent ne pas être pris en charge ou avoir des fonctionnalités contraintes.

**S’applique à :**
- Microsoft 365 Defender

Le service Microsoft 365 Defender est constamment mis à jour pour inclure de nouvelles améliorations et fonctionnalités.

Découvrez les nouvelles fonctionnalités de la version d’aperçu de Microsoft 365 Defender et soyez parmi les premiers à essayer les fonctionnalités à venir en 2013.

Pour plus d’informations sur les nouvelles fonctionnalités généralement disponibles, voir [Nouveautés de Microsoft 365 Defender.](whats-new.md)

## <a name="required-permissions"></a>Autorisations requises

Les comptes affectés aux rôles Azure Active Directory (Azure AD) suivants peuvent activer les fonctionnalités de Microsoft 365 Defender Preview :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité

## <a name="turn-on-preview-features"></a>Activer les fonctionnalités d’aperçu

Vous aurez accès aux fonctionnalités à venir sur qui vous pourrez nous faire part de vos commentaires afin d’améliorer l’expérience globale avant que les fonctionnalités ne soient généralement disponibles.

Activez le paramètre d’expérience de préversion pour être parmi les premiers à essayer les fonctionnalités à venir.

1. Dans le volet de navigation, sélectionnez **Paramètres**.
2. Sélectionnez **Microsoft 365 Defender.**
3. Sélectionnez **Fonctionnalités d’aperçu** > **Activer les fonctionnalités d’aperçu**. 
4. Sélectionnez **Enregistrer**.

Vous savez que vous avez activé les fonctionnalités d’aperçu lorsque la case **Activer les fonctionnalités d’aperçu** est cochée. 

## <a name="preview-features"></a>Fonctionnalités d’aperçu

Les fonctionnalités et améliorations suivantes sont actuellement disponibles en mode aperçu :

### <a name="improved-microsoft-365-security-center"></a>Centre de sécurité Microsoft 365 amélioré
Le [Centre de sécurité Microsoft 365](https://security.microsoft.com) est à présent disponible en préversion publique. Cette nouvelle expérience apporte Defender pour Endpoint, Defender pour Office 365, Microsoft 365 Defender et bien plus encore dans le Centre de sécurité Microsoft 365. Il s’agit du nouvel accueil pour gérer vos contrôles de sécurité. [Découvrir les nouveautés](https://docs.microsoft.com/microsoft-365/security/mtp/overview-security-center).

- Rapport d’analyse des menaces **[Microsoft 365 Defender](threat-analytics.md)** : l’analyse des menaces vous aide à répondre aux attaques actives et à les réduire. Vous pouvez également en savoir plus sur les tentatives d’attaques bloquées par les solutions Microsoft 365 Defender et prendre des mesures préventives qui atténuent les risques d’exposition supplémentaire et augmentent la résilience. Dans le cadre de l’expérience de sécurité unifiée, l’analyse des menaces est désormais disponible pour les titulaires de licence Microsoft Defender pour Endpoint et Microsoft Defender pour Office E5.
- API **[Microsoft 365 Defender](api-overview.md)** - Les API Microsoft 365 Defender de niveau supérieur vous permettent d’automatiser les flux de travail en fonction de l’incident partagé et des tables de recherche avancées. 
- **[Prendre des mesures dans le hunting avancé —](advanced-hunting-take-action.md)** Contenir rapidement des menaces ou traiter les ressources compromises que vous trouvez dans le hunting [avancé](advanced-hunting-overview.md).
- **[Référence de schéma dans le](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** portail — Obtenez des informations sur les tableaux de schéma de recherche avancée directement dans le centre de sécurité. Outre les descriptions de tableau et de colonne, cette référence inclut les types d’événements pris en charge (valeurs) et `ActionType` les exemples de requêtes.
- **[Fonction DeviceFromIP()](advanced-hunting-devicefromip-function.md)**: permet d’obtenir des informations sur les appareils pour lesquels une ou plusieurs adresses IP spécifiques ont été attribuées à un moment donné.
