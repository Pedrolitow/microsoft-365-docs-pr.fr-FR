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
ms.openlocfilehash: b0703aa14bee3d14d1c3ff4fe46ea9d72de73ce2
ms.sourcegitcommit: eee4f651bd51d5aedd64e42d02bfed8ccb9be4cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "44515866"
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

3. Cliquez sur **Enregistrer**.

Vous saurez que les fonctionnalités d’aperçu sont activées lorsque vous voyez que la case à cocher **activer l’aperçu des fonctionnalités** est activée. 

## <a name="preview-features"></a>Fonctionnalités de préversion
Les fonctionnalités et améliorations suivantes sont actuellement disponibles lors de l’aperçu :

- **[Tables d’identité et d’application](advanced-hunting-schema-tables.md)** : obtenez une visibilité sur les événements d’authentification, les requêtes Active Directory et l’activité liée aux applications avec les tables [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md), [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)et [AppFileEvents](advanced-hunting-appfileevents-table.md) dans le schéma de chasse avancé.

- **[Table EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** : utilisez ce tableau pour créer des requêtes de [chasse avancées](advanced-hunting-overview.md) qui vérifient les actions effectuées sur les messages électroniques une fois qu’ils ont été remis aux boîtes aux lettres des destinataires.

- **[Fonction FileProfile ()](advanced-hunting-fileprofile-function.md)** : utilisez dans vos requêtes de [chasse avancée](advanced-hunting-overview.md) pour incorporer des informations complètes sur les fichiers.
