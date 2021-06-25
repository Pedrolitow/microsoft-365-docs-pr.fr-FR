---
title: Aperçu des fonctionnalités dans Microsoft 365 Defender
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
ms.openlocfilehash: b852071c3fbfe12aac62e1d309fa130a4cd81e9c
ms.sourcegitcommit: b42dd3e706ebf9638cd893b35f75eaa56dd8fd7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53125397"
---
# <a name="microsoft-365-defender-preview-features"></a>Microsoft 365 Defender fonctionnalités d’aperçu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> [!IMPORTANT]
> Les versions d’aperçu sont fournies sans contrat de niveau de service et ne sont pas recommandées pour les charges de travail de production. Certaines fonctionnalités peuvent ne pas être pris en charge ou avoir des fonctionnalités contraintes.

**S’applique à :**
- Microsoft 365 Defender

Le service Microsoft 365 Defender est constamment mis à jour pour inclure de nouvelles améliorations et fonctionnalités.

Découvrez les nouvelles fonctionnalités de la Microsoft 365 Defender prévisualisation et soyez parmi les premiers à essayer les fonctionnalités à venir en 2013.

Pour plus d’informations sur les nouvelles fonctionnalités généralement disponibles, voir [Nouveautés](whats-new.md)de Microsoft 365 Defender .

## <a name="required-permissions"></a>Autorisations requises

Les comptes affectés aux rôles Azure Active Directory (Azure AD) peuvent activer Microsoft 365 Defender fonctionnalités d’aperçu :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité

## <a name="turn-on-preview-features"></a>Activer les fonctionnalités d’aperçu

Vous aurez accès aux fonctionnalités à venir sur qui vous pourrez nous faire part de vos commentaires afin d’améliorer l’expérience globale avant que les fonctionnalités ne soient généralement disponibles.

Activez le paramètre d’expérience de préversion pour être parmi les premiers à essayer les fonctionnalités à venir.

1. Dans le volet de navigation, sélectionnez **Paramètres**.
2. Sélectionnez **Microsoft 365 Defender**.
3. Sélectionnez **Fonctionnalités d’aperçu** > **Activer les fonctionnalités d’aperçu**. 
4. Sélectionnez **Enregistrer**.

Vous savez que vous avez activé les fonctionnalités d’aperçu lorsque la case **Activer les fonctionnalités d’aperçu** est cochée. 

## <a name="preview-features"></a>Fonctionnalités d’aperçu

Les fonctionnalités et améliorations suivantes sont actuellement disponibles en mode aperçu :

- **[Afficher les rapports par balise de menace](threat-analytics.md#view-reports-per-threat-tags)** : les balises de menace vous aident à vous concentrer sur des catégories de menaces spécifiques et à examiner les rapports les plus pertinents.
- **[API de diffusion](../defender-endpoint/raw-data-export.md)** en continu : Microsoft 365 Defender prend en charge la diffusion en continu de tous les événements disponibles via le service de recherche avancée vers un hub d’événements et/ou un compte de stockage Azure.
- **[Microsoft 365 Defender API](api-overview.md)** : les API de Microsoft 365 Defender de niveau supérieur vous permettent d’automatiser les flux de travail en fonction de l’incident partagé et des tables de recherche avancées. 
- **[Prendre des mesures dans le hunting avancé](advanced-hunting-take-action.md)** : contenir rapidement des menaces ou traiter les ressources compromises que vous trouvez dans le hunting [avancé](advanced-hunting-overview.md).
- **[Référence de schéma dans](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** le portail : obtenez des informations sur les tables de schéma de recherche avancée directement dans le centre de sécurité. Outre les descriptions de tableau et de colonne, cette référence inclut les types d’événements pris en charge (valeurs) et `ActionType` les exemples de requêtes.
- **[Fonction DeviceFromIP()](advanced-hunting-devicefromip-function.md)** : obtenir des informations sur les appareils qui ont été affectés à une ou plusieurs adresses IP spécifiques à une plage de temps donnée.
