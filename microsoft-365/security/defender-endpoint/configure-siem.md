---
title: Intégrer vos outils SIEM à Microsoft Defender pour point de terminaison
description: Découvrez comment ingérer des incidents et des alertes, et intégrer des outils SIEM.
keywords: configurer siem, outils de gestion des informations de sécurité et des événements, splunk, arcsight, indicateurs personnalisés, api rest, définitions d’alerte, indicateurs de compromis
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
ms.openlocfilehash: ed88048b506ecfcddb8394667e7d800927fc1d83
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634908"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Intégrer vos outils SIEM à Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Ing d’alertes à l’aide des outils de gestion des événements et des informations de sécurité (SIEM)

> [!NOTE]
>
> [Microsoft Defender pour point de terminaison alerte se](alerts.md) compose d’un ou de plusieurs événements suspects ou malveillants qui se sont produits sur l’appareil et de leurs détails connexes. L Microsoft Defender pour point de terminaison API d’alerte est la dernière API pour la consommation des alertes et contient une liste détaillée des preuves associées à chaque alerte. Pour plus d’informations, voir [Méthodes et propriétés](alerts.md) d’alerte et [Lister les alertes](get-alerts.md).

Microsoft Defender pour point de terminaison prend en charge les outils de gestion des événements et des informations de sécurité (SIEM) qui ingaient des informations à partir de votre client d’entreprise dans Azure Active Directory (AAD) à l’aide du protocole d’authentification OAuth 2.0 pour une AAD  représentant la solution ou le connecteur SIEM spécifique installé dans votre environnement.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Microsoft Defender pour point de terminaison licence et conditions d’utilisation des API](api-terms-of-use.md) 
- [Accéder aux API Microsoft Defender pour point de terminaison](apis-intro.md)
- [Hello World exemple (décrit comment inscrire une application dans Azure Active Directory)](api-hello-world.md)
- [Obtenir l’accès avec le contexte de l’application](exposed-apis-create-app-webapp.md)


Microsoft Defender pour point de terminaison prend actuellement en charge les intégrations de solution SIEM suivantes : 

- [Ing d’incidents et d’alertes à partir Microsoft 365 Defender et Microsoft Defender pour point de terminaison incidents et alertes API REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Inginging Microsoft Defender pour point de terminaison events from the Microsoft 365 Defender event streaming API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Ing d’incidents et d’alertes à partir Microsoft 365 Defender et Microsoft Defender pour point de terminaison incidents et alertes API REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Ing d’incidents à partir de l’API REST Microsoft 365 Defender incidents de connexion

Pour plus d’informations sur l’API Microsoft 365 Defender incidents, voir [méthodes et propriétés des incidents](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Ing d’alertes à partir de l’API REST Microsoft Defender pour point de terminaison alertes

Pour plus d’informations sur l’API Microsoft Defender pour point de terminaison alertes, voir [les méthodes et propriétés des alertes](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Intégration de l’outil SIEM Microsoft Defender pour point de terminaison

### <a name="splunk"></a>Splunk

Utilisation du Microsoft 365 Defender pour Splunk qui prend en charge :

- Ing d’Microsoft Defender pour point de terminaison alertes
- Mise à jour des alertes Microsoft Defender pour point de terminaison dans Splunk

Pour plus d’informations sur Microsoft 365 Defender module complémentaire splunk, voir [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Le nouveau SmartConnector pour Microsoft 365 Defender insérant des incidents qui contiennent des alertes de tous les produits Microsoft 365 Defender, y compris depuis Microsoft Defender pour point de terminaison, dans ArcSight et les map après les mapgraphies sur son cadre d’événements communs (CEF).

Pour plus d’informations sur le nouveau SmartConnector ArcSight Microsoft 365 Defender, voir la [documentation du produit ArcSight](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

SmartConnector remplace le flexConnector précédent pour Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>L’intégration d’IBM QRadar avec Microsoft 365 Defender, qui inclut Microsoft Defender pour point de terminaison est désormais prise en charge par le nouveau module de prise en charge des périphériques Microsoft 365 Defender (DSM) [qui appelle le Microsoft 365 Defender API de diffusion](../defender/streaming-api.md) en continu qui permet d’ing d’ing d’événements de diffusion en continu à partir Microsoft 365 Defender produits, y compris Microsoft Defender pour point de terminaison. Pour plus d’informations sur la nouvelle Microsoft 365 Defender DSM QRadar, voir la [documentation produit IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender) et pour plus d’informations sur les types d’événements pris en charge par l’API de diffusion en continu, voir Types d’événements [pris en charge](../defender/supported-event-types.md).

Les nouveaux clients ne sont plus intégrés à l’aide du module DSM (Device Support Module) QRadar Microsoft Defender ATP précédent, et les clients existants sont encouragés à adopter le nouveau DSM Microsoft 365 Defender comme point d’intégration unique avec tous les produits Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Inginging Microsoft Defender pour point de terminaison events from the Microsoft 365 Defender event streaming API

Microsoft 365 Defender données d’événement de diffusion en continu incluent des alertes et d’autres événements Microsoft Defender pour point de terminaison et d’autres produits Microsoft Defender. Ces événements peuvent être diffusés vers un stockage Azure ou vers un Azure Event Hubs. Le modèle d’intégration via les hubs d’événements est actuellement pris en charge par Splunk et IBM QRadar.

Pour plus d’informations, [voir Microsoft 365 Defender’intégration SIEM](../defender/configure-siem-defender.md).
