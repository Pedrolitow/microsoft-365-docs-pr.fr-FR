---
title: Diffuser en continu des événements Microsoft Defender pour point de terminaison vers Azure Event Hubs
description: Découvrez comment configurer Microsoft Defender pour point de terminaison pour diffuser en continu des événements Advanced Hunting vers votre Event Hub.
keywords: exportation de données brutes, API de streaming, API, Azure Event Hubs, stockage Azure, compte de stockage, repérage avancé, partage de données brutes
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
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 7e3466e5a7ba8a5a8c0a5e2041d2022ffd9ce3ce
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686766"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>Configurer Microsoft Defender pour point de terminaison pour diffuser en continu des événements de repérage avancé vers votre Azure Event Hubs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Avant de commencer

1. Créez un [hub d’événements](/azure/event-hubs/) dans votre locataire.

2. Connectez-vous à votre [locataire Azure](https://ms.portal.azure.com/), accédez à **Abonnements > votre abonnement > fournisseurs de ressources > inscrivez-vous à Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Activer le streaming de données brutes

1. Connectez-vous au [Microsoft 365 Defender](https://security.microsoft.com) en tant qu'***administrateur général** _ ou _*_Administrateur de sécurité_**.

2. Accédez à la [page Des paramètres d’exportation de données](https://security.microsoft.com/interoperability/dataexport) dans le portail Microsoft Defender.

3. Cliquez sur **Ajouter des paramètres d’exportation de données**.

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choisissez **Transférer les événements à Azure Event Hubs**.

6. Tapez votre **nom Event Hubs** et votre **ID de ressource Event Hubs**.

   Pour obtenir votre **ID de ressource Event Hubs**, accédez à la page de votre espace de noms Azure Event Hubs sous l’onglet \> Propriétés [d’Azure](https://ms.portal.azure.com/) > copiez le texte sous **l’ID de ressource** :

   :::image type="content" source="images/event-hub-resource-id.png" alt-text="ID de ressource Event Hubs-1" lightbox="images/event-hub-resource-id.png":::

7. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer**.

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>Schéma des événements dans Azure Event Hubs

```json
{
    "records": [
                    {
                        "time": "<The time WDATP received the event>"
                        "tenantId": "<The Id of the tenant that the event belongs to>"
                        "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                        "properties": { <WDATP Advanced Hunting event as Json> }
                    }
                    ...
                ]
}
```

- Chaque message event hub dans Azure Event Hubs contient la liste des enregistrements.

- Chaque enregistrement contient le nom de l’événement, l’heure à laquelle Microsoft Defender pour point de terminaison reçu l’événement, le locataire auquel il appartient (vous obtiendrez uniquement les événements de votre locataire) et l’événement au format JSON dans une propriété appelée « **properties** ».

- Pour plus d’informations sur le schéma des événements Microsoft Defender pour point de terminaison, consultez [la vue d’ensemble de la chasse avancée](advanced-hunting-overview.md).

- Dans La chasse avancée, la table **DeviceInfo** a une colonne nommée **MachineGroup** qui contient le groupe de l’appareil. Ici, chaque événement sera également décoré avec cette colonne. Pour plus d’informations [, consultez Groupes](machine-groups.md) d’appareils.

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données pour les propriétés d’événement, procédez comme suit :

1. Connectez-vous à [Microsoft 365 Defender](https://security.microsoft.com) et accédez à la [page Repérage avancé](https://security.microsoft.com/hunting-package).

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Voici un exemple d’événement Device Info :

  :::image type="content" source="images/machine-info-datatype-example.png" alt-text="ID de ressource Event Hubs-2" lightbox="images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la chasse avancée](advanced-hunting-overview.md)
- [API de diffusion en continu Microsoft Defender pour point de terminaison](raw-data-export.md)
- [Diffuser en continu des événements Microsoft Defender pour point de terminaison vers votre compte de stockage Azure](raw-data-export-storage.md)
- [documentation Azure Event Hubs](/azure/event-hubs/)
- [Résoudre les problèmes de connectivité - Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
