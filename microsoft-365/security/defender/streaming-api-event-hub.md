---
title: Diffuser des Microsoft 365 Defender aux Hubs d’événements Azure
description: Découvrez comment configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée vers votre Hub d’événements.
keywords: exportation de données brutes, API de diffusion en continu, API, Hubs d’événements Azure, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.openlocfilehash: b96ae78b0f2decfe7b2c6f695a4456ac93919c35
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772507"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>Configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée vers vos Hubs d’événements Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Avant de commencer :

1. Créez [un hub d’événements](/azure/event-hubs/) dans votre client.

2. Connectez-vous à votre client [Azure,](https://ms.portal.azure.com/)allez à Abonnements > Votre abonnement > fournisseurs de ressources **> s’inscrire à Microsoft.Insights**.

3. Créez un espace de noms Hub d’événements, sélectionnez **Hubs** d’événements > Ajoutez et sélectionnez le niveau de tarification, les unités de débit et la fonction d’auto-évaluation appropriée à la charge attendue. Pour plus d’informations, voir [Tarification - Hubs d’événements | Microsoft Azure](https://azure.microsoft.com/en-us/pricing/details/event-hubs/).  

4. Une fois l’espace de noms hub d’événements créé, vous devez ajouter le principal du service d’inscription d’application en tant que lecteur, récepteur de données Azure Event Hubs et utilisateur qui se connectera à Microsoft 365 Defender en tant que collaborateur (cette opération peut également être effectuée au niveau du groupe de ressources ou de l’abonnement). Accédez à l’espace de noms Hubs d'> contrôle d’accès **(IAM) >** ajouter et vérifier sous **Attributions de rôles**.

## <a name="enable-raw-data-streaming"></a>Activez la diffusion en continu des données brutes :

1. Connectez-vous au [centre Microsoft 365 de sécurité Defender](https://security.microsoft.com) en tant qu’administrateur général * ou _*_administrateur_ de sécurité **.

2. Go to the [Data export settings page](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Cliquez sur **Ajouter.**

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choose **Forward events to Azure Event Hubs**.

6. Vous pouvez choisir d’exporter les données d’événement vers un hub d’événements unique ou d’exporter chaque table d’événements vers un hub d’événements différent dans votre espace de noms de hub d’événements. 

7. Pour exporter les données d’événement vers un hub d’événements unique, entrez **le** nom de votre Hub d’événements et votre **ID de ressource Hub d’événements.**

   Pour obtenir votre ID de ressource **Event Hubs,** go to your Azure Event Hubs namespace page on [Azure](https://ms.portal.azure.com/)  >  **Properties** tab > copy the text under **Resource ID:**

   ![Image de l’ID1 de ressource du hub d’événements](../defender-endpoint/images/event-hub-resource-id.png)

8. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer.**

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>Schéma des événements dans les Hubs d’événements Azure :

```
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

- Chaque message de hub d’événements dans Azure Event Hubs contient la liste des enregistrements.

- Chaque enregistrement contient le nom de l’événement, l’heure à Microsoft 365 Defender a reçu l’événement, le client qu’il appartient (vous recevez uniquement les événements de votre client) et l’événement au format JSON dans une propriété appelée **«** properties ».

- Pour plus d’informations sur le schéma des événements Microsoft 365 Defender, voir [vue d’ensemble de la recherche avancée.](advanced-hunting-overview.md)

- Dans la recherche avancée, la table **DeviceInfo** comporte une colonne nommée **MachineGroup** qui contient le groupe de l’appareil. Ici, chaque événement est également décorée avec cette colonne. 

9. Pour exporter chaque table d’événements vers un hub d’événements différent, laissez simplement le nom du **hub** d’événements vide et Microsoft 365 Defender fera le reste.


## <a name="data-types-mapping"></a>Mappage des types de données :

Pour obtenir les types de données pour les propriétés d’événement, faites les choses suivantes :

1. Connectez-vous [Microsoft 365 centre de sécurité et](https://security.microsoft.com) allez à la page Recherche [avancée.](https://security.microsoft.com/hunting-package)

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :
 
   ```
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Voici un exemple d’événement Device Info : 

  ![Image de l’ID2 de ressource du hub d’événements](../defender-endpoint/images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du chasse avancée](advanced-hunting-overview.md)
- [Microsoft 365 API de diffusion en continu Defender](streaming-api.md)
- [Diffuser Microsoft 365 événements Defender sur votre compte de stockage Azure](streaming-api-storage.md)
- [Documentation Azure Event Hubs](/azure/event-hubs/)
- [Résoudre les problèmes de connectivité : Hubs d’événements Azure](/azure/event-hubs/troubleshooting-guide)
