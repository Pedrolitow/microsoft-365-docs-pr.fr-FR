---
title: Diffuser des événements Microsoft Defender for Endpoint vers votre compte Stockage de données
description: Découvrez comment configurer Microsoft Defender pour le point de terminaison pour diffuser des événements de recherche avancée vers Stockage compte.
keywords: exportation de données brutes, API de diffusion en continu, API, Hubs d’événements, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.custom: api
ms.openlocfilehash: 77220c8e34cfcbcdb6b1ca527786696bb67e5d79
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465777"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Configurer Microsoft Defender pour le point de terminaison pour diffuser des événements de recherche avancée vers Stockage compte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Avant de commencer

1. Créez [un Stockage dans](/azure/storage/common/storage-account-overview) votre client.

2. Connectez-vous à [votre client Azure](https://ms.portal.azure.com/), > Abonnements > fournisseurs de ressources > **s’inscrire à Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Activer la diffusion en continu des données brutes

1. Connectez-vous [Microsoft 365 Defender](https://security.microsoft.com) en **tant qu’administrateur** général ou _*_administrateur de_ sécurité**.

2. Go to [Data export settings page](https://security.microsoft.com/interoperability/dataexport) in Microsoft 365 Defender.

3. Cliquez sur **Ajouter des paramètres d’exportation de données**.

4. Choisissez un nom pour vos nouveaux paramètres.

5. **Sélectionnez Les événements Forward à stockage Azure**.

6. Tapez votre **ID Stockage de compte de compte.** Pour obtenir votre **ID** de ressource de compte Stockage, go to your Stockage account page on [Azure portal](https://ms.portal.azure.com/) \> properties tab \> copy the text under **Stockage account resource ID**:

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="Hubs d’événements avec ID1 de ressource" lightbox="images/storage-account-resource-id.png":::

7. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schéma des événements dans le compte Stockage client

- Un conteneur d’objets blob est créé pour chaque type d’événement :

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="Hubs d’événements avec ID2 de ressource" lightbox="images/storage-account-event-schema.png":::

- Le schéma de chaque ligne d’un objet blob est le JSON suivant :

  ```json
  {
      "time": "<The time WDATP received the event>"
      "tenantId": "<Your tenant ID>"
      "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
      "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Chaque objet blob contient plusieurs lignes.

- Chaque ligne contient le nom de l’événement, le moment où Defender pour le point de terminaison a reçu l’événement, le client qu’il appartient (vous recevez uniquement les événements de votre client) et l’événement au format JSON dans une propriété appelée « properties ».

- Pour plus d’informations sur le schéma des événements Microsoft Defender for Endpoint, consultez [la vue d’ensemble de la recherche avancée](advanced-hunting-overview.md).

- Dans la recherche avancée, la table **DeviceInfo** comporte une colonne nommée **MachineGroup** qui contient le groupe de l’appareil. Ici, chaque événement est également décorée avec cette colonne. Pour plus [d’informations](machine-groups.md) , voir Groupes d’appareils.

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données pour nos propriétés d’événements, vous pouvez :

1. Connectez-vous [Microsoft 365 Defender](https://security.microsoft.com) et allez à la [page Recherche avancée](https://security.microsoft.com/hunting-package).

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Voici un exemple d’événement Device Info :

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="Hubs d’événements avec ID3 de ressource" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble du chasse avancée](advanced-hunting-overview.md)
- [API de diffusion en continu De Microsoft Defender pour les points de terminaison](raw-data-export.md)
- [Diffuser des événements Microsoft Defender for Endpoint vers votre compte de stockage Azure](raw-data-export-storage.md)
- [stockage Azure de compte d’utilisateur](/azure/storage/common/storage-account-overview)
