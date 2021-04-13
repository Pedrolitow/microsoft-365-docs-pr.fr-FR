---
title: Diffuser des événements Microsoft Defender for Endpoint vers votre compte de stockage
description: Découvrez comment configurer Microsoft Defender pour le point de terminaison pour diffuser des événements de recherche avancée vers votre compte de stockage.
keywords: exportation de données brutes, API de diffusion en continu, API, Hubs d'événements, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.openlocfilehash: 19fe0c9c3dc6f2e4226a4aa9a6cd983bc95bae3a
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51688788"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Configurer Microsoft Defender pour le point de terminaison pour diffuser des événements de recherche avancée vers votre compte de stockage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l'expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configuresiem-abovefoldlink) 

## <a name="before-you-begin"></a>Avant de commencer :

1. Créez [un compte de stockage](https://docs.microsoft.com/azure/storage/common/storage-account-overview) dans votre client.

2. Connectez-vous à votre client [Azure,](https://ms.portal.azure.com/)allez à Abonnements > Votre abonnement > fournisseurs de ressources **> s'inscrire à Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Activer la diffusion en continu des données brutes :

1. Connectez-vous [au portail Microsoft Defender pour points](https://securitycenter.windows.com) de terminaison en tant qu'administrateur * Administrateur **général** _ ou _*_Administrateur_ de sécurité **.

2. Go to [Data export settings page](https://securitycenter.windows.com/interoperability/dataexport) on Microsoft Defender Security Center.

3. Cliquez sur **Ajouter des paramètres d'exportation de données.**

4. Choisissez un nom pour vos nouveaux paramètres.

5. Choose **Forward events to Azure Storage**.

6. Tapez votre **ID de ressource de compte de stockage.** Pour obtenir votre **ID** de ressource de compte de stockage, allez à la page de votre compte de stockage sur l'onglet Propriétés du portail [Azure](https://ms.portal.azure.com/) > > copiez le texte sous **L'ID** de ressource du compte de stockage :

   ![Image de l'ID1 de ressource du hub d'événements](images/storage-account-resource-id.png)

7. Choisissez les événements que vous souhaitez diffuser en continu, puis cliquez sur **Enregistrer.**

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schéma des événements dans le compte de stockage :

- Un conteneur d'objets blob est créé pour chaque type d'événement : 

  ![Image de l'ID2 de ressource du hub d'événements](images/storage-account-event-schema.png)

- Le schéma de chaque ligne d'un objet blob est le JSON suivant : 

  ```
  {
          "time": "<The time WDATP received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <WDATP Advanced Hunting event as Json> }
  }               
  ```

- Chaque objet blob contient plusieurs lignes.

- Chaque ligne contient le nom de l'événement, le moment où Defender pour le point de terminaison a reçu l'événement, le client qu'il appartient (vous recevez uniquement les événements de votre client) et l'événement au format JSON dans une propriété appelée « properties ».

- Pour plus d'informations sur le schéma des événements De Microsoft Defender pour point de [terminaison, voir vue d'ensemble de la recherche avancée.](advanced-hunting-overview.md)

- Dans la recherche avancée, la table **DeviceInfo** comporte une colonne nommée **MachineGroup** qui contient le groupe de l'appareil. Ici, chaque événement est également décorée avec cette colonne. Pour plus [d'informations,](machine-groups.md) voir Groupes d'appareils.

## <a name="data-types-mapping"></a>Mappage des types de données :

Pour obtenir les types de données pour nos propriétés d'événements, vous pouvez :

1. Connectez-vous [au Centre de](https://securitycenter.windows.com) sécurité Microsoft Defender et allez à la page Recherche [avancée.](https://securitycenter.windows.com/hunting-package)

2. Exécutez la requête suivante pour obtenir le mappage des types de données pour chaque événement : 

   ```
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Voici un exemple d'événement Device Info : 

  ![Image de l'ID3 de ressource du hub d'événements](images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Voir aussi
- [Vue d'ensemble du chasse avancée](advanced-hunting-overview.md)
- [API de diffusion en continu microsoft Defender pour point de terminaison](raw-data-export.md)
- [Diffuser des événements Microsoft Defender for Endpoint vers votre compte de stockage Azure](raw-data-export-storage.md)
- [Documentation du compte de stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview)
