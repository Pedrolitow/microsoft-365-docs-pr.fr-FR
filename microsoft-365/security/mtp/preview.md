---
title: Fonctionnalités d’aperçu de la protection contre les menaces Microsoft
description: Découvrez les nouvelles fonctionnalités de sécurité Microsoft 365
keywords: Aperçu, nouvelle M365 sécurité, sécurité, 365, fonctionnalités
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: 45bc42e825c55ca228b13e8d308f9a1384301d07
ms.sourcegitcommit: 11218af1d792af297b4280ca5975d139d2bbe350
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "45048266"
---
# <a name="microsoft-threat-protection-preview-features"></a>Fonctionnalités d’aperçu de la protection contre les menaces Microsoft

**S’applique à :**
- Protection Microsoft contre les menaces


Le service de protection contre les menaces Microsoft est constamment mis à jour pour inclure de nouvelles améliorations et fonctionnalités.

Découvrez les nouvelles fonctionnalités de la version d’évaluation de Microsoft Threat Protection et soyez parmi les premières à essayer les fonctionnalités à venir en activant l’aperçu.

Pour plus d’informations sur les nouvelles fonctionnalités généralement disponibles, voir [Nouveautés de la Protection Microsoft contre les menaces](whats-new.md).

## <a name="turn-on-preview-features"></a>Activer les fonctionnalités d’aperçu
Vous aurez accès aux fonctionnalités à venir, sur lesquelles vous pouvez faire part de vos commentaires afin d’améliorer l’expérience globale avant que les fonctionnalités soient disponibles en général.

Activez le paramètre aperçu de l’expérience pour commencer à utiliser les fonctionnalités à venir.

1. Dans le volet de navigation, sélectionnez **paramètres**.

2. Sélectionnez **Microsoft Threat Protection**.


3. Sélectionnez **Aperçu**  >  **des fonctionnalités activer les fonctionnalités d’aperçu**. 

3. Sélectionnez **Enregistrer**.

Vous saurez que les fonctionnalités d’aperçu sont activées lorsque vous voyez que la case à cocher **activer l’aperçu des fonctionnalités** est activée. 

## <a name="preview-features"></a>Fonctionnalités de préversion
Les fonctionnalités et améliorations suivantes sont actuellement disponibles lors de l’aperçu :

- **[Guide de référence de schéma dans le portail](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** : informations sur les tables de schéma disponibles directement dans le centre de sécurité. Outre les descriptions de table et de colonne, cette référence fournit des informations sur les types d’événement pris en charge ( `ActionType` valeurs) et les exemples de requêtes.  

- **[Tables d’identité et d’application](advanced-hunting-schema-tables.md)** : obtenez une visibilité sur les événements d’authentification, les requêtes Active Directory et l’activité liée aux applications avec les tables [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md), [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)et [AppFileEvents](advanced-hunting-appfileevents-table.md) dans le schéma de chasse avancé.

- **[Aller-retour : parcourir](advanced-hunting-go-hunt.md)** rapidement un tableau croisé dynamique à partir de l’examen d’un événement spécifique, d’un utilisateur, d’un appareil ou d’autres types d’entité à l’aide des fonctionnalités de recherche [avancée](advanced-hunting-overview.md) basées sur les requêtes.

- **[Fonction FileProfile ()](advanced-hunting-fileprofile-function.md)** : utilisez dans vos requêtes de [chasse avancée](advanced-hunting-overview.md) pour incorporer des informations complètes sur les fichiers.
