---
title: Diffuser en continu des événements Microsoft Defender pour point de terminaison vers votre compte de stockage
description: Découvrez comment configurer Microsoft Defender pour point de terminaison pour diffuser en continu des événements Advanced Hunting vers votre compte de stockage.
keywords: exportation de données brutes, API de streaming, API, Event Hubs, stockage Azure, compte de stockage, repérage avancé, partage de données brutes
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
ms.openlocfilehash: c94830e4f9dbfe16a8dfafba35aecb5a36efddf5
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493440"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Configurer Microsoft Defender pour point de terminaison pour diffuser en continu des événements de repérage avancé vers votre compte de stockage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Avant de commencer

1. Créez un [compte de stockage](/azure/storage/common/storage-account-overview) dans votre locataire.

2. Connectez-vous à votre [locataire Azure](https://ms.portal.azure.com/), accédez à **Abonnements > votre abonnement > fournisseurs de ressources > inscrivez-vous à Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Activer le streaming de données brutes

1. Connectez-vous à [Microsoft 365 Defender](https://security.microsoft.com) en tant qu'***administrateur général** _ ou _*_Administrateur de sécurité_**.

2. Accédez à la [page Des paramètres d’exportation de données](https://security.microsoft.com/settings/mtp_settings/raw_data_export) dans Microsoft 365 Defender.

3. Cliquez sur **Ajouter des paramètres d’exportation de données**.

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choisissez **Transférer des événements vers stockage Azure**.

6. Tapez votre **ID de ressource de compte de stockage**. Pour obtenir votre **ID de ressource de compte de stockage**, accédez à la page de votre compte de stockage [sous Portail Azure](https://ms.portal.azure.com/) \> onglet \> Propriétés, copiez le texte sous **l’ID de ressource du compte de stockage** :

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="Event Hubs avec l’ID de ressource 1" lightbox="images/storage-account-resource-id.png":::

7. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schéma des événements dans le compte de stockage

- Un conteneur d’objets blob est créé pour chaque type d’événement :

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="Event Hubs avec l’ID de ressource 2" lightbox="images/storage-account-event-schema.png":::

- Le schéma de chaque ligne d’un objet blob est le code JSON suivant :

  ```json
  {
    "time": "<The time WDATP received the event>"
    "tenantId": "<Your tenant ID>"
    "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
    "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Chaque objet blob contient plusieurs lignes.

- Chaque ligne contient le nom de l’événement, l’heure à laquelle Defender pour point de terminaison a reçu l’événement, le locataire auquel il appartient (vous obtiendrez uniquement les événements de votre locataire) et l’événement au format JSON dans une propriété appelée « properties ».

- Pour plus d’informations sur le schéma des événements Microsoft Defender pour point de terminaison, consultez [la vue d’ensemble de la chasse avancée](advanced-hunting-overview.md).

- Dans La chasse avancée, la table **DeviceInfo** a une colonne nommée **MachineGroup** qui contient le groupe de l’appareil. Ici, chaque événement sera également décoré avec cette colonne. Pour plus d’informations [, consultez Groupes](machine-groups.md) d’appareils.

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données pour nos propriétés d’événements, procédez comme suit :

1. Connectez-vous à [Microsoft 365 Defender](https://security.microsoft.com) et accédez à la [page Repérage avancé](https://security.microsoft.com/hunting-package).

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Voici un exemple d’événement Device Info :

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="Event Hubs avec l’ID de ressource 3" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de la chasse avancée](advanced-hunting-overview.md)
- [API de diffusion en continu Microsoft Defender pour point de terminaison](raw-data-export.md)
- [Diffuser en continu des événements Microsoft Defender pour point de terminaison vers votre compte de stockage Azure](raw-data-export-storage.md)
- [Documentation sur le compte de stockage Azure](/azure/storage/common/storage-account-overview)
