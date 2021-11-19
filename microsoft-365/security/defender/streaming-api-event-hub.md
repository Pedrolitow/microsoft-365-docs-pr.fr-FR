---
title: Diffuser Microsoft 365 Defender événements dans Azure Event Hub
description: Découvrez comment configurer les Microsoft 365 Defender pour diffuser des événements de recherche avancée vers votre Hub d’événements.
keywords: exportation de données brutes, API de diffusion en continu, API, Hub d’événements Azure, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 5658d2cbb0fd3f8307ceb6cb46057237436271eb
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111770"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée vers votre Hub d’événements Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Avant de commencer

1. Créez [un hub d’événements](/azure/event-hubs/) dans votre client.

2. Connectez-vous à votre client [Azure,](https://ms.portal.azure.com/)allez à Abonnements > Votre abonnement > fournisseurs de ressources **> inscrivez-vous à Microsoft.Informations**.

3. Créez un espace de noms Hub d’événements, sélectionnez hub d’événements **>** ajoutez et sélectionnez le niveau de tarification, les unités de débit et la capacité de resserrement automatique adaptée à la charge attendue. Pour plus d’informations, [voir la tarification des Hubs d’événements.](https://azure.microsoft.com/pricing/details/event-hubs/)

### <a name="add-contributor-permissions"></a>Ajouter des autorisations de collaborateur

Une fois l’espace de noms Hub d’événements créé, vous devez :

1. Définissez l’utilisateur qui se connectera à Microsoft 365 Defender en tant que Collaborateur.

2. Si vous vous connectez à une application, ajoutez le principal du service d’inscription d’application en tant que lecteur, récepteur de données Azure Event Hub (cette procédure peut également être effectuée au niveau du groupe de ressources ou de l’abonnement).

    Accédez à l’espace de noms **Hubs d’événements > contrôle d’accès (IAM) > ajouter** et vérifier sous **attributions de rôles.**

## <a name="enable-raw-data-streaming"></a>Activer la diffusion en continu des données brutes

1. Connectez-vous <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail en</a> tant qu’administrateur général * ou _*_Administrateur_ de sécurité **.

2. Go to the [Streaming API settings page](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Cliquez sur **Ajouter.**

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choose **Forward events to Azure Event Hub**.

6. Vous pouvez choisir d’exporter les données d’événement vers un hub d’événements unique ou d’exporter chaque table d’événements vers un hub d’événements différent dans votre espace de noms Event Hub.

7. Pour exporter les données d’événement vers un hub d’événements unique, entrez le nom de votre Hub d’événements **et** votre **ID de ressource Event Hub.**

   Pour obtenir votre ID de ressource **Event Hub,** rendez-vous sur votre page d’espace de noms Azure Event Hub sous l’onglet [Propriétés Azure](https://ms.portal.azure.com/)> copier le texte sous  >   **L’ID de ressource**:

   ![Image de l’ID1 de la ressource Hub d’événements.](../defender-endpoint/images/event-hub-resource-id.png)

8. Go to the [Supported Microsoft 365 Defender event types in event streaming API](supported-event-types.md) to review the support status of event types in the Microsoft 365 Streaming API.

9. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer.**

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

- Chaque message Event Hub dans Azure Event Hub contient la liste des enregistrements.

- Chaque enregistrement contient le nom de l’événement, l’heure à Microsoft 365 Defender reçu l’événement, le client qu’il appartient (vous obtenez uniquement les événements de votre client) et l’événement au format JSON dans une propriété appelée **«** properties ».

- Pour plus d’informations sur le schéma des événements Microsoft 365 Defender, voir [vue d’ensemble de la recherche avancée.](advanced-hunting-overview.md)

- Dans la recherche avancée, la table **DeviceInfo** comporte une colonne nommée **MachineGroup** qui contient le groupe de l’appareil. Ici, chaque événement est également décorée avec cette colonne.

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données pour les propriétés d’événement, faites les choses suivantes :

1. Connectez-vous <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> et allez à la [page Recherche avancée.](https://security.microsoft.com/hunting-package)

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Voici un exemple d’événement Device Info :

  ![Image de l’ID2 de la ressource Hub d’événements.](../defender-endpoint/images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Sujets connexes

- [Vue d’ensemble du chasse avancée](advanced-hunting-overview.md)
- [API Microsoft 365 Defender diffusion en continu](streaming-api.md)
- [Types d’Microsoft 365 Defender pris en charge dans l’API de diffusion en continu d’événements](supported-event-types.md)
- [Diffuser Microsoft 365 Defender événements sur votre compte de stockage Azure](streaming-api-storage.md)
- [Documentation Du Hub d’événements Azure](/azure/event-hubs/)
- [Résoudre les problèmes de connectivité - Hub d’événements Azure](/azure/event-hubs/troubleshooting-guide)
