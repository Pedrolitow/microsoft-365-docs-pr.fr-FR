---
title: Diffuser Microsoft 365 Defender événements sur votre compte Stockage client
description: Découvrez comment configurer des Microsoft 365 Defender pour diffuser en continu des événements de recherche avancée sur Stockage compte.
keywords: exportation de données brutes, API de diffusion en continu, API, Hubs d’événements, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.openlocfilehash: 159b4a41d423c2a7af3d367185e29af35a378b6b
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2021
ms.locfileid: "60963102"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée vers votre compte Stockage client

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Avant de commencer

1. Créez [un Stockage dans](/azure/storage/common/storage-account-overview) votre client.

2. Connectez-vous à votre client [Azure,](https://ms.portal.azure.com/)allez à Abonnements > Votre abonnement > fournisseurs de ressources **> inscrivez-vous à Microsoft.Informations**.

## <a name="enable-raw-data-streaming"></a>Activer la diffusion en continu des données brutes

1. Connectez-vous <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> en tant **qu’administrateur** général * ou _* Administrateur de _sécurité_**.

2. Go to **Paramètres** \> **Microsoft 365 Defender** \> **Streaming API**. Pour aller directement à la page de **l’API de** diffusion en continu, utilisez <https://security.microsoft.com/settings/mtp_settings/raw_data_export> .

3. Cliquez sur **Ajouter**.

4. Dans le **programme volant Ajouter de nouveaux paramètres d’API** de diffusion en continu qui s’affiche, configurez les paramètres suivants :
   1. **Nom**: choisissez un nom pour vos nouveaux paramètres.
   2. Sélectionnez **Les événements Forward à stockage Azure**.
   3. Dans la **Stockage’ID** de ressource de compte qui s’affiche, tapez **votre ID de ressource Stockage compte.** Pour obtenir votre ID de ressource de compte **Stockage,** ouvrez le portail Azure à l’Stockage cliquez sur les comptes Stockage pour copier le texte sous l’ID de ressource de compte <https://portal.azure.com>  \> \> **Stockage.**

      ![Image de l’ID1 de ressource du hub d’événements.](../defender-endpoint/images/storage-account-resource-id.png)

   4. De retour sur le volet Ajouter **de nouveaux paramètres d’API** de diffusion en continu, choisissez les **types** d’événements que vous souhaitez diffuser en continu.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schéma des événements dans le compte Stockage client

- Un conteneur d’objets blob est créé pour chaque type d’événement :

  ![Image de l’ID2 de ressource du hub d’événements.](../defender-endpoint/images/storage-account-event-schema.png)

- Le schéma de chaque ligne d’un objet blob est le JSON suivant :

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Chaque objet blob contient plusieurs lignes.

- Chaque ligne contient le nom de l’événement, le moment où Defender pour le point de terminaison a reçu l’événement, le client qu’il appartient (vous recevez uniquement les événements de votre client) et l’événement au format JSON dans une propriété appelée « properties ».

- Pour plus d’informations sur le schéma des événements Microsoft 365 Defender, voir [vue d’ensemble de la recherche avancée.](../defender/advanced-hunting-overview.md)

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données pour nos propriétés d’événements, vous pouvez :

1. Connectez-vous <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> et allez au **hunting** \> **advanced hunting**. Pour aller directement à la page **de** recherche avancée, utilisez <security.microsoft.com/advanced-hunting>.

2. Sous **l’onglet Requête,** exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Voici un exemple d’événement Device Info :

  ![Image de l’ID3 de ressource du hub d’événements.](../defender-endpoint/images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Sujets connexes

- [Vue d’ensemble du chasse avancée](../defender/advanced-hunting-overview.md)
- [API Microsoft 365 Defender diffusion en continu](streaming-api.md)
- [Diffuser Microsoft 365 Defender événements sur votre compte de stockage Azure](streaming-api-storage.md)
- [stockage Azure de compte d’utilisateur](/azure/storage/common/storage-account-overview)
