---
title: intégration de Microsoft 365 Defender à Microsoft Sentinel
description: Utilisez Microsoft Sentinel comme SIEM pour Microsoft 365 Defender incident et événements.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: da57ca47c4c95246f7ed3278cc475ef313daec45
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68075510"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>intégration de Microsoft 365 Defender à Microsoft Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Le connecteur Microsoft 365 Defender pour Microsoft Sentinel (préversion) envoie tous les Microsoft 365 Defender incidents et informations d’alerte à Microsoft Sentinel et maintient la synchronisation des incidents. 

Une fois que vous avez ajouté le connecteur, Microsoft 365 Defender incidents&mdash;qui incluent toutes les alertes, entités et informations pertinentes reçues de Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity, Microsoft Defender pour Office 365 et Microsoft Defender for Cloud Apps&mdash; sont diffusés en continu vers Microsoft Sentinel en tant que données SIEM (Security Information and Event Management), ce qui vous fournit un contexte pour effectuer le triage et la réponse aux incidents avec Microsoft Sentinel. 

Une fois dans Microsoft Sentinel, les incidents restent synchronisés bidirectionnellement avec Microsoft 365 Defender, ce qui vous permet de tirer parti des avantages du portail Microsoft 365 Defender et de Microsoft Sentinel dans le Portail Azure pour l’investigation et la réponse aux incidents.

Regardez cette courte vue d’ensemble de l’intégration de Microsoft Sentinel à Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Voici comment cela fonctionne.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Flux et partage des données d’incident pour les portails Microsoft 365 Defender et Microsoft Sentinel" lightbox="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png":::

## <a name="next-steps"></a>Prochaines étapes

1. Découvrez plus en détail [Microsoft 365 Defender intégration à Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).
2. [Connectez les données de Microsoft 365 Defender à Microsoft Sentinel](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents dans Microsoft 365 Defender](incidents-overview.md)
- [Examiner les incidents avec Microsoft Sentinel](/azure/sentinel/tutorial-investigate-cases)
