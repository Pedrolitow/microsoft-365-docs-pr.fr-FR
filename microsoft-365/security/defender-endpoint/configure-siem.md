---
title: Pull detections to your SIEM tools from Microsoft Defender for Endpoint
description: Découvrez comment utiliser l’API REST et configurer les outils de gestion des événements et des informations de sécurité pris en charge pour recevoir et tirer des détections.
keywords: configurer siem, outils de gestion des informations de sécurité et des événements, splunk, arcsight, indicateurs personnalisés, api rest, définitions d’alerte, indicateurs de compromis
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 23940fc05e08dec6074dbdc420d529425cec0027
ms.sourcegitcommit: 87d994407fb69a747239b8589ad11ddf9b47e527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2021
ms.locfileid: "53595821"
---
# <a name="pull-detections-to-your-siem-tools"></a>Tirer les détections vers vos outils SIEM

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="pull-detections-using-security-information-and-events-management-siem-tools"></a>Détections de pull à l’aide des outils de gestion des événements et des informations de sécurité (SIEM)

>[!NOTE]
>- [Microsoft Defender pour l’alerte de point de terminaison](alerts.md) est composé d’une ou plusieurs détections.
>- [Microsoft Defender pour la détection des points](api-portal-mapping.md) de terminaison est composé de l’événement suspect qui s’est produit sur l’appareil et de ses détails d’alerte associés.
>-The Microsoft Defender for Endpoint Alert API is the latest API for alert consumption and contain a detailed list of related evidence for each alert. Pour plus d’informations, voir [Méthodes et propriétés d’alerte et](alerts.md) Liste des [alertes.](get-alerts.md)

Defender pour le point de terminaison prend en charge les outils de gestion des événements et des informations de sécurité (SIEM) pour tirer les détections. Defender pour le point de terminaison expose les alertes via un point de terminaison HTTPS hébergé dans Azure. Le point de terminaison peut être configuré pour tirer les détections de votre client d’entreprise dans Azure Active Directory (AAD) à l’aide du protocole d’authentification OAuth 2.0 pour une application AAD qui représente le connecteur SIEM spécifique installé dans votre environnement.

Defender pour le point de terminaison prend actuellement en charge les outils de solution SIEM spécifiques suivants via un modèle d’intégration SIEM dédié :

- IBM QRadar
- Micro Focus ArcSight

D’autres solutions SIEM (telles que Splunk, RSA NetWitness) sont pris en charge via un modèle d’intégration différent basé sur la nouvelle API d’alerte. Pour plus d’informations, consultez la page [Application](https://securitycenter.microsoft.com/interoperability/partners) partenaire et sélectionnez la section Informations sur la sécurité et analyse pour plus d’informations.

Pour utiliser l’un de ces outils SIEM pris en charge, vous devez :

- [Activer l’intégration SIEM dans Defender for Endpoint](enable-siem-integration.md)
- Configurez l’outil SIEM pris en charge :
     - [Configurer Micro Focus ArcSight pour tirer Defender pour les détections de points de terminaison](configure-arcsight.md)
     - Configurez IBM QRadar pour tirer Defender pour les détections de points de terminaison Pour plus d’informations, voir [le Centre de connaissances IBM.](https://www.ibm.com/support/knowledgecenter/SS42VS_DSM/com.ibm.dsm.doc/c_dsm_guide_MS_Win_Defender_ATP_overview.html?cp=SS42VS_7.3.1)

Pour plus d’informations sur la liste des champs exposés dans l’API de détection, voir Defender pour les champs de détection [de point de terminaison.](api-portal-mapping.md)
