---
title: Diffuser en continu des événements Microsoft 365 Defender vers votre compte de stockage
description: Découvrez comment configurer Microsoft 365 Defender pour diffuser en continu des événements de chasse avancée vers votre compte de stockage.
keywords: exportation de données brutes, API de streaming, API, Event Hubs, Stockage Azure, compte de stockage, Repérage avancé, partage de données brutes
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
ms.openlocfilehash: 73428378c3229765b5e9ea3783dfdde7021fabaf
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727254"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Configurer Microsoft 365 Defender pour diffuser en continu des événements de chasse avancée vers votre compte de stockage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Avant de commencer

1. Créez un [compte de stockage](/azure/storage/common/storage-account-overview) dans votre locataire.

2. Connectez-vous à votre [locataire Azure](https://ms.portal.azure.com/), accédez à **Abonnements > Votre abonnement > Fournisseurs de ressources > Inscrivez-vous à Microsoft.Insights**.

### <a name="add-contributor-permissions"></a>Ajouter des autorisations de contributeur

Une fois le compte de stockage créé, vous devez :

1. Définissez l’utilisateur qui se connectera à Microsoft 365 Defender en tant que Contributeur.

    Accédez à **Compte de stockage > Contrôle d’accès (IAM) > Ajouter** et vérifier sous **Attributions de rôles**.

## <a name="enable-raw-data-streaming"></a>Activer la diffusion en continu de données brutes

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> en tant **qu’administrateur général** ou _*_administrateur de la sécurité_**.

2. Accédez à **Paramètres** \> **Microsoft 365 Defender** \> **API de streaming**. Pour accéder directement à la page de **l’API de streaming** , utilisez <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. Cliquez sur **Ajouter**.

4. Dans le menu volant **Ajouter de nouveaux paramètres d’API de streaming** qui s’affiche, configurez les paramètres suivants :
   1. **Nom** : choisissez un nom pour vos nouveaux paramètres.
   2. Sélectionnez **Transférer des événements vers stockage Azure**.
4. Pour afficher l’ID de ressource Azure Resource Manager pour un compte de stockage dans le Portail Azure, procédez comme suit :

   1. Accédez à votre compte de stockage dans le Portail Azure.
   2. Dans la page **Vue d’ensemble** , dans la section **Essentials** , sélectionnez le lien **Affichage JSON** .
   3. L’ID de ressource du compte de stockage s’affiche en haut de la page. Copiez le texte sous **ID de ressource du compte de stockage**.

   4. De retour dans le menu volant **Ajouter de nouveaux paramètres d’API de streaming** , choisissez les **types d’événements** que vous souhaitez diffuser en continu.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schéma des événements dans le compte de stockage

- Un conteneur d’objets blob est créé pour chaque type d’événement :

  :::image type="content" source="../defender-endpoint/images/storage-account-event-schema.png" alt-text="Exemple de conteneur d’objets blob" lightbox="../defender-endpoint/images/storage-account-event-schema.png":::

- Le schéma de chaque ligne d’un objet blob est le code JSON suivant :

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Chaque objet blob contient plusieurs lignes.

- Chaque ligne contient le nom de l’événement, l’heure à laquelle Defender pour point de terminaison a reçu l’événement, le locataire auquel il appartient (vous obtiendrez uniquement les événements de votre locataire) et l’événement au format JSON dans une propriété appelée « properties ».

- Pour plus d’informations sur le schéma des événements Microsoft 365 Defender, consultez [Vue d’ensemble de la chasse avancée](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Mappage des types de données

Pour obtenir les types de données de nos propriétés d’événements, procédez comme suit :

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> et accédez à **Chasse** \> **avancée**. Pour accéder directement à la page **Repérage avancé** , utilisez <security.microsoft.com/advanced-hunting>.

2. Sous l’onglet **Requête** , exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement :

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Voici un exemple pour l’événement Device Info :

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Exemple de requête d’informations sur l’appareil" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="monitoring-created-resources"></a>Surveillance des ressources créées

Vous pouvez surveiller les ressources créées par l’API de streaming à l’aide **d’Azure Monitor**. Pour plus d’informations, consultez [Surveiller les destinations - Azure Monitor | Microsoft Docs](/azure/azure-monitor/logs/logs-data-export?tabs=portal#monitor-destinations).

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la chasse avancée](../defender/advanced-hunting-overview.md)
- [API de streaming Microsoft 365 Defender](streaming-api.md)
- [Diffuser en continu des événements Microsoft 365 Defender vers votre compte de stockage Azure](streaming-api-storage.md)
- [Documentation sur le compte de stockage Azure](/azure/storage/common/storage-account-overview)
