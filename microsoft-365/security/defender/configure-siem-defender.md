---
title: Intégrer les outils SIEM avec Microsoft 365 Defender pour point de terminaison
description: Découvrez comment utiliser l’API REST et configurer les outils de gestion des informations de sécurité et des événements pris en charge pour recevoir et extraire des détections.
keywords: configurer des siems, des informations de sécurité et des outils de gestion des événements, splunk, arcsight, indicateurs personnalisés, api rest, définitions d’alertes, indicateurs de compromission
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
ms.openlocfilehash: 3e2772fd458c60e48f78c0d4b816cdac8ca25940
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530309"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>Intégrer les outils SIEM avec Microsoft 365 Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Extraire Microsoft 365 Defender incidents et diffuser en continu des données d’événement à l’aide des outils SIEM (Security Information and Events Management)

> [!NOTE]
>
> - [Microsoft 365 Defender incidents](incident-queue.md) se compose de collections d’alertes corrélées et de leurs preuves.
> - [Microsoft 365 Defender l’API streaming](streaming-api.md) diffuse des données d’événements de Microsoft 365 Defender vers des hubs d’événements ou des comptes de stockage Azure.

Microsoft 365 Defender prend en charge les outils SIEM (Security Information and Event Management) qui ingèrent des informations à partir de votre locataire d’entreprise dans Azure Active Directory (AAD) à l’aide du protocole d’authentification OAuth 2.0 pour une application AAD inscrite représentant la solution ou le connecteur SIEM spécifique installé dans votre environnement. 

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Microsoft 365 Defender licence et conditions d’utilisation des API](api-terms.md)
- [Accéder aux API Microsoft 365 Defender](api-access.md)
- [Exemple Hello World](api-hello-world.md)
- [Obtenir l’accès avec le contexte de l’application](api-create-app-web.md)

Il existe deux modèles principaux pour ingérer des informations de sécurité : 

1.  Ingestion Microsoft 365 Defender incidents et leurs alertes contenues à partir d’une API REST dans Azure. 

2.  Ingestion de données d’événement de streaming via Azure Event Hubs ou des comptes de stockage Azure. 

Microsoft 365 Defender prend actuellement en charge les intégrations de solutions SIEM suivantes : 

- [Ingestion d’incidents à partir de l’API REST incidents](#ingesting-incidents-from-the-incidents-rest-api)
- [Ingestion de données d’événement en streaming via Event Hub](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Ingestion d’incidents à partir de l’API REST incidents

### <a name="incident-schema"></a>Schéma d’incident
Pour plus d’informations sur Microsoft 365 Defender propriétés d’incident, notamment les métadonnées des entités d’alerte et de preuve contenues, consultez [mappage de schéma](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Utilisation du nouveau module complémentaire Splunk entièrement pris en charge pour Microsoft Security qui prend en charge :

- Ingestion d’incidents qui contiennent des alertes provenant des produits suivants, mappés sur le modèle d’information commune (CIM) de Splunk :

  - Microsoft 365 Defender
  - Microsoft Defender pour point de terminaison
  - Microsoft Defender pour Identity et Azure Active Directory Identity Protection
  - Microsoft Defender for Cloud Apps

- Ingestion d’alertes Defender pour point de terminaison (à partir du point de terminaison Azure de Defender pour point de terminaison) et mise à jour de ces alertes

- La prise en charge de la mise à jour des incidents Microsoft 365 Defender et/ou des alertes Microsoft Defender pour point de terminaison et des tableaux de bord respectifs a été déplacée vers l’application Microsoft 365 pour Splunk. 

Pour plus d’informations :

- Le module complémentaire Splunk pour Microsoft Security, consultez le module complémentaire [de sécurité Microsoft sur Splunkbase](https://splunkbase.splunk.com/app/6207/#/overview)

- Application Microsoft 365 pour Splunk, consultez [l’application Microsoft 365 sur Splunkbase](https://splunkbase.splunk.com/app/3786/)

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Le nouveau SmartConnector pour Microsoft 365 Defender ingère les incidents dans ArcSight et les mappe à son Infrastructure d’événements commun (CEF).

Pour plus d’informations sur le nouveau SmartConnector ArcSight pour Microsoft 365 Defender, consultez la [documentation du produit ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

SmartConnector remplace le FlexConnector précédent pour Microsoft Defender pour point de terminaison qui a été déprécié.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Ingestion de données d’événement de streaming via Event Hubs

Tout d’abord, vous devez diffuser en continu des événements de votre locataire AAD vers votre Event Hubs ou votre compte de stockage Azure. Pour plus d’informations, consultez [l’API de diffusion en continu](../defender/streaming-api.md).

Pour plus d’informations sur les types d’événements pris en charge par l’API de streaming, consultez [Types d’événements de streaming pris en charge](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk

Utilisez le module complémentaire Splunk pour Microsoft Services cloud pour ingérer des événements à partir de Azure Event Hubs.  

Pour plus d’informations sur le module complémentaire Splunk pour Microsoft Services cloud, consultez le module complémentaire [Microsoft Services cloud sur Splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Utilisez le nouveau module DSM (Ibm QRadar Microsoft 365 Defender Device Support Module) qui appelle [l’API de diffusion en continu Microsoft 365 Defender](streaming-api.md) qui permet d’ingérer des données d’événement de streaming à partir de produits Microsoft 365 Defender via Event Hubs ou un compte de stockage Azure. Pour plus d’informations sur les types d’événements pris en charge, consultez [Types d’événements pris en charge](supported-event-types.md).
