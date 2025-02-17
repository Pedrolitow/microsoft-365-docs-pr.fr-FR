---
title: Diffuser en continu des événements Microsoft 365 Defender vers Azure Event Hubs
description: Découvrez comment configurer Microsoft 365 Defender pour diffuser en continu des événements Advanced Hunting vers vos Event Hubs.
keywords: exportation de données brutes, API de streaming, API, Azure Event Hubs, stockage Azure, compte de stockage, repérage avancé, partage de données brutes
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.openlocfilehash: 00f7d69923514b5e7736042db939d4366990978a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633436"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Configurer Microsoft 365 Defender pour diffuser en continu des événements Advanced Hunting vers votre Hub d’événements Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="prerequisites"></a>Configuration requise

Avant de configurer Microsoft 365 Defender pour diffuser des données vers Event Hubs, vérifiez que les conditions préalables suivantes sont remplies :

1. Créez un Event Hubs (pour plus d’informations, consultez [Configurer Event Hubs](configure-event-hub.md#set-up-event-hubs)).

2. Création d’un espace de noms Event Hubs (pour plus d’informations, consultez [Configurer l’espace de noms Event Hubs](configure-event-hub.md#set-up-event-hubs-namespace)).

3. Ajoutez des autorisations à l’entité qui dispose des privilèges d’un **contributeur** afin que cette entité puisse exporter des données vers Event Hubs. Pour plus d’informations sur l’ajout d’autorisations, consultez [Ajouter des autorisations](configure-event-hub.md#add-permissions)

> [!NOTE]
> L’API de streaming peut être intégrée via Event Hubs ou un compte de stockage Azure.

## <a name="enable-raw-data-streaming"></a>Activer le streaming de données brutes

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> en tant qu'***administrateur général** _ ou _*_Administrateur de sécurité_**.

2. Accédez à la [page paramètres de l’API de diffusion en continu](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Cliquez sur **Ajouter**.

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choisissez **Transférer des événements vers Azure Event Hub**.

6. Vous pouvez sélectionner si vous souhaitez exporter les données d’événement vers un hub d’événements unique ou exporter chaque table d’événements vers un hub d’événements différent dans votre espace de noms Event Hubs.

7. Pour exporter les données d’événement vers un hub d’événements unique, entrez votre **nom Event Hub** et votre **ID de ressource Event Hub**.

   Pour obtenir votre **ID de ressource Event Hub**, accédez à votre page d’espace de noms Azure Event Hubs sous l’onglet **Propriétés** [Azure](https://ms.portal.azure.com/) >  > copiez le texte sous **l’ID de ressource** :

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Un ID de ressource Event Hub" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. Accédez aux [types d’événements Microsoft 365 Defender pris en charge dans l’API de streaming d’événements](supported-event-types.md) pour passer en revue l’état de prise en charge des types d’événements dans l’API de streaming Microsoft 365.

9. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Schéma des événements dans Azure Event Hub

```JSON
{
   "records": [
               {
                  "time": "<The time Microsoft 365 Defender received the event>"
                  "tenantId": "<The Id of the tenant that the event belongs to>"
                  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                  "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
               }
               ...
            ]
}
```

- Chaque message Event Hubs dans Azure Event Hubs contient la liste des enregistrements.

- Chaque enregistrement contient le nom de l’événement, l’heure à laquelle Microsoft 365 Defender reçu l’événement, le locataire auquel il appartient (vous obtiendrez uniquement les événements de votre locataire) et l’événement au format JSON dans une propriété appelée « **properties** ».

- Pour plus d’informations sur le schéma des événements Microsoft 365 Defender, consultez [la vue d’ensemble de la chasse avancée](advanced-hunting-overview.md).

- Dans La chasse avancée, la table **DeviceInfo** a une colonne nommée **MachineGroup** qui contient le groupe de l’appareil. Ici, chaque événement sera également décoré avec cette colonne.

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données pour les propriétés d’événement, procédez comme suit :

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> et accédez à la [page Repérage avancé](https://security.microsoft.com/hunting-package).

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Voici un exemple d’événement Device Info :

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Exemple de requête pour les informations sur l’appareil" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="estimating-initial-event-hub-capacity"></a>Estimation de la capacité initiale d’Event Hub
La requête Advanced Hunting suivante peut vous aider à fournir une estimation approximative du débit du volume de données et de la capacité initiale du hub d’événements en fonction des événements/s et du Mo/s estimé. Nous vous recommandons d’exécuter la requête pendant les heures normales de bureau afin de capturer le débit « réel ».
 
```kusto 
let bytes_ = 500;
union withsource=MDTables*
| where Timestamp > startofday(ago(6h))
| summarize count() by bin(Timestamp, 1m), MDTables
| extend EPS = count_ /60
| summarize avg(EPS), estimatedMBPerSec = (avg(EPS) * bytes_ ) / (1024*1024) by MDTables
| sort by toint(estimatedMBPerSec) desc
```

## <a name="monitoring-created-resources"></a>Surveillance des ressources créées

Vous pouvez surveiller les ressources créées par l’API de streaming à l’aide **d’Azure Monitor**. Pour plus d’informations, consultez [l’exportation de données de l’espace de travail Log Analytics dans Azure Monitor](/azure/azure-monitor/logs/logs-data-export). 

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la chasse avancée](advanced-hunting-overview.md)
- [API de diffusion en continu Microsoft 365 Defender](streaming-api.md)
- [Types d’événements Microsoft 365 Defender pris en charge dans l’API de streaming d’événements](supported-event-types.md)
- [Diffuser en continu des événements Microsoft 365 Defender vers votre compte de stockage Azure](streaming-api-storage.md)
- [documentation Azure Event Hubs](/azure/event-hubs/)
- [Résoudre les problèmes de connectivité - Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
