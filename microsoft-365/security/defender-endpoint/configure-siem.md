---
title: Intégrer vos outils SIEM à Microsoft Defender pour Endpoint
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
ms.openlocfilehash: 1438e346f693ede4a54eeb7c850a2d8cd4164129
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62074521"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Intégrer vos outils SIEM à Microsoft Defender pour Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Ing d’alertes à l’aide des outils de gestion des événements et des informations de sécurité (SIEM)

> [!NOTE]
>
> [Microsoft Defender pour l’alerte de point](alerts.md) de terminaison se compose d’un ou de plusieurs événements suspects ou malveillants qui se sont produits sur l’appareil et de leurs détails connexes. L’API d’alerte Microsoft Defender pour point de terminaison est la dernière API pour la consommation des alertes et contient une liste détaillée des preuves associées à chaque alerte. Pour plus d’informations, voir [Méthodes et propriétés d’alerte et](alerts.md) Liste des [alertes.](get-alerts.md)

Microsoft Defender pour point de terminaison prend en charge les outils de gestion des événements et des informations de sécurité (SIEM) qui ingaient les informations de votre client d’entreprise dans Azure Active Directory (AAD) à l’aide du protocole d’authentification OAuth 2.0 pour une application AAD inscrite représentant la solution ou le connecteur SIEM spécifique installé dans votre environnement.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Licence et conditions d’utilisation des API Microsoft Defender for Endpoint](api-terms-of-use.md) 
- [Accéder aux API Microsoft Defender pour point de terminaison](apis-intro.md)
- [Exemple Hello World (décrit comment inscrire une application dans Azure Active Directory)](api-hello-world.md)
- [Obtenir l’accès avec le contexte de l’application](exposed-apis-create-app-webapp.md)


Microsoft Defender pour le point de terminaison prend actuellement en charge les intégrations de solution SIEM suivantes : 

- [Ing d’incidents et d’alertes du Microsoft 365 Defender et de Microsoft Defender pour les incidents de point de terminaison et alertes API REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Inginging Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Ing d’incidents et d’alertes du Microsoft 365 Defender et de Microsoft Defender pour les incidents de point de terminaison et alertes API REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Ing d’incidents à partir de l’API REST Microsoft 365 Defender incidents de connexion

Pour plus d’informations sur l’API Microsoft 365 Defender incidents, voir [les méthodes et propriétés des incidents.](../defender/api-incident.md)

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Ing d’alertes à partir de l’API REST des alertes Microsoft Defender pour les points de terminaison

Pour plus d’informations sur l’API d’alertes microsoft Defender pour les points de terminaison, voir les méthodes [et propriétés des alertes.](alerts.md)

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Intégration de l’outil SIEM à Microsoft Defender pour Endpoint

### <a name="splunk"></a>Splunk

Utilisation du Microsoft 365 Defender pour Splunk qui prend en charge :

- Ing d’alertes Microsoft Defender pour les points de terminaison
- Mise à jour des alertes dans Microsoft Defender pour le point de terminaison à partir de Splunk

Pour plus d’informations sur Microsoft 365 Defender module complémentaire splunk, voir [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Le nouveau SmartConnector pour Microsoft 365 Defender insérant des incidents qui contiennent des alertes de tous les produits Microsoft 365 Defender , y compris à partir de Microsoft Defender pour Endpoint, dans ArcSight et les cartes sur son cadre d’événements communs (CEF).

Pour plus d’informations sur le nouveau SmartConnector ArcSight Microsoft 365 Defender, voir la documentation du [produit ArcSight.](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender)

SmartConnector remplace le flexConnector précédent pour Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>
>L’intégration d’IBM QRadar à Microsoft Defender pour Endpoint est désormais prise en charge par le nouveau module de prise en charge des appareils (DSM) Microsoft 365 Defender qui appelle [l’API](../defender/streaming-api.md) de diffusion en continu Microsoft 365 Defender qui permet la prise en charge des données d’événements de diffusion en continu à partir de Microsoft 365 Defender  produits, y compris Microsoft Defender pour point de terminaison. Pour plus d’informations sur les types d’événements pris en charge, voir [Types d’événements pris en charge.](../defender/supported-event-types.md)
Les nouveaux clients ne sont plus intégrés à l’aide du module DSM (Device Support Module) QRadar Microsoft Defender ATP précédent, et les clients existants sont encouragés à adopter le nouveau DSM Microsoft 365 Defender comme point d’intégration unique avec tous les produits Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Inginging Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API

Microsoft 365 Defender données d’événement de diffusion en continu inclut des alertes et d’autres événements de Microsoft Defender pour Endpoint et d’autres produits Microsoft Defender. Ces événements peuvent être diffusés vers un compte stockage Azure ou vers des Hubs d’événements Azure. Le modèle d’intégration via les hubs d’événements est actuellement pris en charge par Splunk et IBM QRadar.

Pour plus d’informations, [voir Microsoft 365 Defender’intégration SIEM.](../defender/configure-siem-defender.md)
