---
title: Intégrer les outils SIEM avec Microsoft 365 Defender pour point de terminaison
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 210705bd3392e4aeeadd815ed8c1840e772f6ad9
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110426"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>Intégrer les outils SIEM avec Microsoft 365 Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Tirer les Microsoft 365 Defender et les données d’événements de diffusion en continu à l’aide des outils de gestion des informations et des événements de sécurité (SIEM)

> [!NOTE]
>
> - [Microsoft 365 Defender Incidents se](incident-queue.md) compose de collections d’alertes corrélées et de leurs preuves.
> - [Microsoft 365 Defender API de diffusion en](streaming-api.md) continu diffuse des données d’événements Microsoft 365 Defender vers des hubs d’événements ou des comptes de stockage Azure.

Microsoft 365 Defender prend en charge les outils de gestion des événements et des informations de sécurité (SIEM) qui ingaient les informations de votre client d’entreprise dans Azure Active Directory (AAD) à l’aide du protocole d’authentification OAuth 2.0 pour une application AAD inscrite représentant la solution ou le connecteur SIEM spécifique installé dans votre environnement. 

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Microsoft 365 Defender licence et conditions d’utilisation des API](api-terms.md)
- [Accéder aux API Microsoft 365 Defender de données](api-access.md)
- [Exemple Hello World](api-hello-world.md)
- [Obtenir l’accès avec le contexte de l’application](api-create-app-web.md)

Il existe deux modèles principaux pour l’ing d’informations de sécurité : 

1.  L’Microsoft 365 Defender incidents et leurs alertes contenues à partir d’une API REST dans Azure. 

2.  Ing d’ing d’événements de diffusion en continu via azure Event Hubs ou stockage Azure comptes. 

Microsoft 365 Defender prend actuellement en charge les intégrations de solution SIEM suivantes : 

- [Ing d’incidents à partir de l’API REST incidents](#ingesting-incidents-from-the-incidents-rest-api)
- [Ing d’ing de données d’événement de diffusion en continu via le Hub d’événements](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Ing d’incidents à partir de l’API REST incidents

### <a name="incident-schema"></a>Schéma d’incident
Pour plus d’informations sur Microsoft 365 Defender’incident, notamment sur les métadonnées d’entités d’alerte et de preuve contenues, voir [Mappage de schéma.](../defender/api-list-incidents.md#schema-mapping)

### <a name="splunk"></a>Splunk

Utilisation du Microsoft 365 Defender pour Splunk qui prend en charge :

- Incidents d’inglément contenant des alertes provenant des produits suivants, qui sont mappés sur le modèle d’informations communes (CIM) de Splunk :

  - Microsoft 365 Defender
  - Microsoft Defender pour point de terminaison
  - Microsoft Defender for Identity and Azure Active Directory Identity Protection
  - Microsoft Defender for Cloud Apps

- Mise à jour des incidents Microsoft 365 Defender dans Splunk

- Ingesting Defender for Endpoint alerts (from the Defender for Endpoint’s Azure endpoint) and updating these alerts

Pour plus d’informations sur Microsoft 365 Defender module complémentaire splunk, voir [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Le nouveau SmartConnector pour Microsoft 365 Defender les incidents dans ArcSight et les cartes sur son infrastructure d’événements communs (CEF).

Pour plus d’informations sur le nouveau SmartConnector ArcSight Microsoft 365 Defender, voir la documentation produit [ArcSight.](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender)

SmartConnector remplace le flexConnector précédent pour Microsoft Defender pour endpoint.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Ing d’ing de données d’événement de diffusion en continu via les Hubs d’événements

Tout d’abord, vous devez diffuser des événements depuis AAD client vers vos hubs d’événements ou stockage Azure compte. Pour plus d’informations, voir [l’API de diffusion en continu.](../defender/streaming-api.md)

Pour plus d’informations sur les types d’événements pris en charge par l’API de diffusion en continu, voir [Types d’événements de diffusion en](../defender/supported-event-types.md)continu pris en charge.

### <a name="splunk"></a>Splunk
Utilisez le module splunk pour microsoft cloud services pour ing d’événements à partir de Hubs d’événements Azure.  


Pour plus d’informations sur le module complémentaire Splunk pour Microsoft Cloud Services, voir [splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Utilisez le nouveau module de prise en charge d’appareil (DSM) IBM QRadar Microsoft 365 Defender qui appelle [l’API de](streaming-api.md) diffusion en continu Microsoft 365 Defender qui permet d’ing d’ing d’événements de diffusion en continu à partir Microsoft 365 Defender produits. Pour plus d’informations sur les types d’événements pris en charge, voir [Types d’événements pris en charge.](supported-event-types.md)
