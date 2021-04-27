---
title: Fonctionnalités d'aperçu dans Microsoft 365 Defender
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: c82e1abf9e539ad169bbc488ade9cd21bb8e6727
ms.sourcegitcommit: e02cf5702af178ddd2968877a808874ecb49ed2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52029073"
---
# <a name="microsoft-365-defender-preview-features"></a>Fonctionnalités d'aperçu de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> [!IMPORTANT]
> Les versions d'aperçu sont fournies sans contrat de niveau de service et ne sont pas recommandées pour les charges de travail de production. Certaines fonctionnalités peuvent ne pas être pris en charge ou avoir des fonctionnalités contraintes.

**S’applique à :**
- Microsoft 365 Defender

Le service Microsoft 365 Defender est constamment mis à jour pour inclure de nouvelles améliorations et fonctionnalités.

Découvrez les nouvelles fonctionnalités de la version d'aperçu de Microsoft 365 Defender et soyez parmi les premiers à essayer les fonctionnalités à venir en 2013.

Pour plus d'informations sur les nouvelles fonctionnalités généralement disponibles, voir Nouveautés [de Microsoft 365 Defender.](whats-new.md)

## <a name="required-permissions"></a>Autorisations requises

Les comptes affectés aux rôles Azure Active Directory (Azure AD) suivants peuvent activer les fonctionnalités de Microsoft 365 Defender Preview :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité

## <a name="turn-on-preview-features"></a>Activer les fonctionnalités d’aperçu

Vous aurez accès aux fonctionnalités à venir sur qui vous pourrez nous faire part de vos commentaires afin d'améliorer l'expérience globale avant que les fonctionnalités ne soient généralement disponibles.

Activez le paramètre d’expérience de préversion pour être parmi les premiers à essayer les fonctionnalités à venir.

1. Dans le volet de navigation, sélectionnez **Paramètres**.
2. Sélectionnez **Microsoft 365 Defender.**
3. Sélectionnez **Fonctionnalités d’aperçu** > **Activer les fonctionnalités d’aperçu**. 
4. Sélectionnez **Enregistrer**.

Vous savez que vous avez activé les fonctionnalités d’aperçu lorsque la case **Activer les fonctionnalités d’aperçu** est cochée. 

## <a name="preview-features"></a>Fonctionnalités d’aperçu

Les fonctionnalités et améliorations suivantes sont actuellement disponibles en mode aperçu :

- API **[Microsoft 365 Defender](api-overview.md)** - Les API Microsoft 365 Defender de niveau supérieur vous permettent d'automatiser les flux de travail en fonction de l'incident partagé et des tables de recherche avancées. 
- **[Prendre des mesures dans le hunting avancé —](advanced-hunting-take-action.md)** Contenir rapidement des menaces ou traiter les ressources compromises que vous trouvez dans le hunting [avancé](advanced-hunting-overview.md).
- **[Référence de schéma dans le](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** portail — Obtenez des informations sur les tableaux de schéma de recherche avancée directement dans le centre de sécurité. Outre les descriptions de tableau et de colonne, cette référence inclut les types d'événements pris en charge (valeurs) et `ActionType` les exemples de requêtes.
- **[Fonction DeviceFromIP()](advanced-hunting-devicefromip-function.md)**: permet d'obtenir des informations sur les appareils pour lesquels une ou plusieurs adresses IP spécifiques ont été attribuées à un moment donné.
