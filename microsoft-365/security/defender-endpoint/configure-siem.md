---
title: Intégrer vos outils SIEM à Microsoft Defender pour point de terminaison
description: Découvrez comment ingérer des incidents et des alertes et intégrer des outils SIEM.
keywords: configurer des siems, des informations de sécurité et des outils de gestion des événements, splunk, arcsight, indicateurs personnalisés, api rest, définitions d’alertes, indicateurs de compromission
search.appverid: met150
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.openlocfilehash: b00a9f02f4cd370985dfa5c094c6be36aa34ab1e
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679512"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Intégrer vos outils SIEM à Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Ingérer des alertes à l’aide des outils de gestion des informations et des événements de sécurité (SIEM)

> [!NOTE]
>
> [Microsoft Defender pour point de terminaison alerte](alerts.md) est composée d’un ou de plusieurs événements suspects ou malveillants qui se sont produits sur l’appareil et de leurs détails connexes. L’API d’alerte Microsoft Defender pour point de terminaison est la dernière API pour la consommation des alertes et contient une liste détaillée des preuves associées pour chaque alerte. Pour plus d’informations, consultez [Les méthodes d’alerte, les propriétés et](alerts.md) [les alertes de liste](get-alerts.md).

Microsoft Defender pour point de terminaison prend en charge les outils SIEM (Security Information and Event Management) qui ingèrent des informations à partir de votre locataire d’entreprise dans Azure Active Directory (AAD) à l’aide du protocole d’authentification OAuth 2.0 pour une application AAD inscrite représentant la solution ou le connecteur SIEM spécifique installé dans votre environnement.

Pour plus d’informations, consultez l’article suivant :

- [Microsoft Defender pour point de terminaison licence et conditions d’utilisation des API](api-terms-of-use.md) 
- [Accéder aux API Microsoft Defender pour point de terminaison](apis-intro.md)
- [Hello World exemple (décrit comment inscrire une application dans Azure Active Directory)](api-hello-world.md)
- [Obtenir l’accès avec le contexte de l’application](exposed-apis-create-app-webapp.md)


Microsoft Defender pour point de terminaison prend actuellement en charge les intégrations de solutions SIEM suivantes : 

- [Ingestion d’incidents et d’alertes à partir des Microsoft 365 Defender et des Microsoft Defender pour point de terminaison incidents et alertes DES API REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Ingestion d’événements Microsoft Defender pour point de terminaison à partir de l’API de streaming d’événements Microsoft 365 Defender](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Ingestion d’incidents et d’alertes à partir des Microsoft 365 Defender et des Microsoft Defender pour point de terminaison incidents et alertes DES API REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Ingestion d’incidents à partir de l’API REST Microsoft 365 Defender incidents

Pour plus d’informations sur l’API Microsoft 365 Defender incidents, consultez [les méthodes et les propriétés des incidents](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Ingestion d’alertes à partir de l’API REST d’alertes Microsoft Defender pour point de terminaison

Pour plus d’informations sur l’API d’alertes Microsoft Defender pour point de terminaison, consultez [les méthodes et propriétés des alertes](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Intégration de l’outil SIEM à Microsoft Defender pour point de terminaison

### <a name="splunk"></a>Splunk

Utilisation du module complémentaire Microsoft 365 Defender pour Splunk qui prend en charge :

- Ingestion d’alertes Microsoft Defender pour point de terminaison
- Mise à jour des alertes dans Microsoft Defender pour point de terminaison à partir de Splunk

Pour plus d’informations sur le module complémentaire Microsoft 365 Defender pour Splunk, consultez [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="datadog"></a>Datadog

Microsoft 365 Defender pour l’intégration de point de terminaison à Datadog prend en charge :

- Ingestion d’alertes et d’incidents Microsoft Defender pour point de terminaison
- Tableaux de bord qui permettent de surveiller les métriques entre les points de terminaison, les menaces et les vulnérabilités, ainsi que les logiciels

Pour plus d’informations sur l’intégration, consultez [La Place de marché Datadog](https://app.datadoghq.com/marketplace/app/crest-data-systems-microsoft-defender/support).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Le nouveau SmartConnector pour Microsoft 365 Defender ingère les incidents qui contiennent des alertes de tous les produits Microsoft 365 Defender, y compris à partir de Microsoft Defender pour point de terminaison, dans ArcSight et les mappe à son Infrastructure d’événements commun (CEF).

Pour plus d’informations sur le nouveau SmartConnector ArcSight pour Microsoft 365 Defender, consultez la [documentation d’ArcSight Product](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

SmartConnector remplace le FlexConnector précédent pour Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>L’intégration d’IBM QRadar à Microsoft 365 Defender, qui inclut Microsoft Defender pour point de terminaison, est désormais prise en charge par le nouveau module de support d’appareil Microsoft 365 Defender (DSM) qui appelle le [ Microsoft 365 Defender API de streaming](../defender/streaming-api.md) qui permet d’ingérer des données d’événement de streaming à partir de produits Microsoft 365 Defender, y compris Microsoft Defender pour point de terminaison. Pour plus d’informations sur le nouveau QRadar Microsoft 365 Defender DSM, consultez [la documentation du produit IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender) et pour plus d’informations sur les types d’événements pris en charge par l’API de streaming, consultez [Types d’événements pris en charge](../defender/supported-event-types.md).

Les nouveaux clients ne sont plus intégrés à l’aide du module DSM (Device Support Module) Microsoft Defender ATP (QRadar) précédent, et les clients existants sont encouragés à adopter le nouveau Microsoft 365 Defender DSM comme point d’intégration unique avec tous les produits Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Ingestion d’événements Microsoft Defender pour point de terminaison à partir de l’API de streaming d’événements Microsoft 365 Defender

Microsoft 365 Defender données d’événement de streaming incluent des alertes et d’autres événements provenant de Microsoft Defender pour point de terminaison et d’autres produits Microsoft Defender. Ces événements peuvent être diffusés en continu vers un compte de stockage Azure ou vers Azure Event Hubs. Le modèle d’intégration via event hubs est actuellement pris en charge par Splunk et IBM QRadar.

Pour plus d’informations, consultez [Microsoft 365 Defender intégration SIEM](../defender/configure-siem-defender.md).
