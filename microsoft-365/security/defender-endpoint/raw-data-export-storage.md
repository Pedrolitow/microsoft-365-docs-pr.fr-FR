---
title: Diffuser Microsoft 365 événements Defender à votre compte Stockage client
description: Découvrez comment configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée sur Stockage compte.
keywords: exportation de données brutes, API de diffusion en continu, API, Hubs d’événements, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.openlocfilehash: 9ec8c286828fd6b551bf76c8340b58c9a1407bba
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52778208"
---
# <a name="configure--microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée vers Stockage compte

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="before-you-begin"></a>Avant de commencer :

1. Créez [un Stockage dans](/azure/storage/common/storage-account-overview) votre client.

2. Connectez-vous à votre client [Azure,](https://ms.portal.azure.com/)allez à Abonnements > Votre abonnement > fournisseurs de ressources **> s’inscrire à Microsoft.Insights**.

## <a name="enable-raw-data-streaming"></a>Activez la diffusion en continu des données brutes :

1. Connectez-vous [Microsoft 365 centre de sécurité Defender](https://security.microsoft.com) en tant qu’administrateur général * ou _*_administrateur_ de sécurité **.

2. Go to [Data export settings page](https://security.microsoft.com/settings/mtp_settings/raw_data_export) in Centre de sécurité Microsoft Defender.

3. Cliquez sur **Ajouter des paramètres d’exportation de données.**

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choose **Forward events to stockage Azure**.

6. Tapez votre **ID Stockage de ressource de compte.** Pour obtenir votre ID de ressource de compte **Stockage,** go to your Stockage account page on [Azure portal](https://ms.portal.azure.com/) > properties tab > copy the text under Stockage Account Resource **ID:**

   ![Image de l’ID1 de ressource du hub d’événements](images/storage-account-resource-id.png)

7. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer.**

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schéma des événements dans le compte Stockage :

- Un conteneur d’objets blob est créé pour chaque type d’événement : 

  ![Image de l’ID2 de ressource du hub d’événements](images/storage-account-event-schema.png)

- Le schéma de chaque ligne d’un objet blob est le JSON suivant : 

  ```
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


## <a name="data-types-mapping"></a>Mappage des types de données :

Pour obtenir les types de données pour nos propriétés d’événements, vous pouvez :

1. Connectez-vous [Microsoft 365 centre de sécurité et](https://security.microsoft.com) allez à la page Recherche [avancée.](https://security.microsoft.com/hunting-package)

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement : 

   ```
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Voici un exemple d’événement Device Info : 

  ![Image de l’ID3 de ressource du hub d’événements](images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du chasse avancée](../defender/advanced-hunting-overview.md)
- [Microsoft 365 API de diffusion en continu defender](raw-data-export.md)
- [Diffuser Microsoft 365 événements Defender sur votre compte de stockage Azure](raw-data-export-storage.md)
- [stockage Azure Documentation du compte](/azure/storage/common/storage-account-overview)
