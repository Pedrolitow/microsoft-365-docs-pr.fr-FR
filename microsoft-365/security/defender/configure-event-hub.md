---
title: Configurer vos hubs d’événements
description: Découvrez comment configurer vos hubs d’événements
keywords: event hub, configure, insights
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.openlocfilehash: 1af62c9618b3212d15d7d81af2c8297505851721
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679688"
---
# <a name="configure-your-event-hubs"></a>Configurer vos hubs d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Découvrez comment configurer vos hubs d’événements afin qu’il puisse ingérer des événements à partir de Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hubs-subscription"></a>Configurer le fournisseur de ressources requis dans l’abonnement Event Hubs

1. Connectez-vous au [Portail Azure](https://portal.azure.com).
1. Sélectionnez **Abonnements** > **{ Sélectionnez l’abonnement que les hubs d’événements seront déployés sur }** > **Fournisseurs de ressources**.
1. Vérifiez si le fournisseur **Microsoft.Insights** est inscrit. Sinon, inscrivez-le.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="Page liste des fournisseurs de services dans microsoft Portail Azure" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>Configurer l’inscription d’application Azure Active Directory

> [!NOTE]
> Vous devez avoir le rôle Administrateur ou Azure Active Directory (AAD) doit être défini pour permettre aux non-administrateurs d’inscrire des applications. Vous devez également disposer d’un rôle Propriétaire ou Administrateur de l’accès utilisateur pour attribuer un rôle au principal de service. Pour plus d’informations, consultez [Créer une application Azure AD & principal de service dans le portail - Plateforme d'identités Microsoft \| Microsoft Docs](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Créez une inscription (qui crée par nature un principal de service) dans **Azure Active Directory** \> **inscriptions d'applications** \> **Nouvelle inscription.**

1. Remplissez le formulaire avec uniquement le nom (aucun URI de redirection n’est requis).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="Section d’affichage du nom de l’application dans microsoft Portail Azure" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="Section Informations sur la vue d’ensemble dans microsoft Portail Azure" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. Créez un secret en cliquant sur **Certificats & secrets** \> **Nouveau secret client** :

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="Section Clé secrète client dans microsoft Portail Azure" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::

Cette valeur de clé secrète client est utilisée par les API Microsoft Graph pour authentifier cette application en cours d’inscription.

> [!WARNING]
> **Vous ne pourrez plus accéder à la clé secrète client. Veillez donc à l’enregistrer**.

## <a name="set-up-event-hubs-namespace"></a>Configurer l’espace de noms Event Hubs

1. Créez un espace de noms Event Hubs :

    Accédez **à Event Hub \> Ajouter** et sélectionnez le niveau tarifaire, les unités de débit et la majoration automatique (nécessite une tarification standard et sous les fonctionnalités) appropriés pour la charge que vous attendez. Pour plus d’informations, consultez [Tarification - Event Hubs \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/).

    > [!NOTE]
    > Vous pouvez utiliser un hub d’événements existant, mais le débit et la mise à l’échelle sont définis au niveau de l’espace de noms. Il est donc recommandé de placer un hub d’événements dans son propre espace de noms.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="Section Event Hubs dans Microsoft Portail Azure" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. Vous aurez également besoin de l’ID de ressource de cet espace de noms Event Hubs. Accédez à vos propriétés de page \> d’espace de noms Azure Event Hubs. Copiez le texte sous l’ID de ressource et enregistrez-le pour l’utiliser dans la section Configuration de Microsoft 365 ci-dessous.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="Section propriétés event hubs dans microsoft Portail Azure" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::

### <a name="add-permissions"></a>Ajouter des autorisations

Vous devez ajouter des autorisations aux rôles suivants aux entités impliquées dans la gestion des données Event Hubs :

- **Contributeur** : les autorisations associées à ce rôle sont ajoutées à l’entité qui se connecte au portail Microsoft 365 Defender.
- **Lecteur** et **récepteur de données Azure Event Hub** : les autorisations liées à ces rôles sont attribuées à l’entité qui dispose déjà du rôle d’un **principal de service** et se connecte à l’application Azure Active Directory.

Pour vous assurer que ces rôles ont été ajoutés, effectuez l’étape suivante :

Accédez à l’espace de noms **Event Hub** \> **Access Control (IAM)** \> **Ajouter** et vérifier sous **Attributions de rôles**.

:::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="Section principal du service d’inscription d’application dans microsoft Portail Azure" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hubs"></a>Configurer Event Hubs

**Option 1 :**

Vous pouvez créer un Event Hubs dans votre espace de noms et **tous les** types d’événements (tables) que vous sélectionnez pour exporter seront écrits dans ce **hub d’événements** .

**Option 2 :**

Au lieu d’exporter tous les types d’événements (tables) dans un hub d’événements, vous pouvez exporter chaque table dans différents hubs d’événements à l’intérieur de votre espace de noms Event Hubs (un Event Hub par type d’événement).

Dans cette option, Microsoft 365 Defender crée Event Hubs pour vous.

> [!NOTE]
> Si vous utilisez un espace de noms Event Hub qui **ne fait pas** partie d’un cluster Event Hub, vous pouvez uniquement choisir jusqu’à 10 types d’événements (tables) à exporter dans chaque paramètre d’exportation que vous définissez, en raison d’une limitation Azure de 10 Event Hub par espace de noms Event Hub.

Par exemple :

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="Section Event Hubs dans Microsoft Portail Azure" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

Si vous choisissez cette option, vous pouvez passer à la section [Configurer Microsoft 365 Defender pour envoyer des tables de courrier](#configure-microsoft-365-defender-to-send-email-tables).

Créez Event Hubs dans votre espace de noms en sélectionnant **Event Hub** \> **+ Event Hub**.

Le nombre de partitions permet d’augmenter le débit via le parallélisme. Il est donc recommandé d’augmenter ce nombre en fonction de la charge attendue. Les valeurs de rétention et de capture des messages par défaut de 1 et désactivées sont recommandées.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="Section de création de hubs d’événements dans microsoft Portail Azure" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::

Pour ces hubs d’événements (et non l’espace de noms), vous devez configurer une stratégie d’accès partagé avec Envoyer, Écouter les revendications. Cliquez sur vos stratégies \> **d’accès partagé** **Event Hub** \> **+ Ajouter**, puis donnez-lui un nom de stratégie (non utilisé ailleurs) et cochez **Envoyer** et **écouter**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="Page Stratégies d’accès partagé dans Microsoft Portail Azure" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>Configurer Microsoft 365 Defender pour envoyer des tables de courrier électronique

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hubs"></a>Configurer Microsoft 365 Defender envoyer Email tables à Splunk via Event Hubs

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> avec un compte qui répond à toutes les exigences de rôle suivantes :

    - Rôle contributeur au *niveau de la* ressource de l’espace de noms Event Hubs ou supérieur pour les hubs d’événements vers lequel vous allez exporter. Sans cette autorisation, vous obtenez une erreur d’exportation lorsque vous essayez d’enregistrer les paramètres.

    - Rôle de Administration de sécurité ou de Administration global sur le locataire lié à Microsoft 365 Defender et Azure.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="Page Paramètres du portail Microsoft 365 Defender" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. Cliquez sur **Exportation de données brutes \> +Ajouter**.

    Vous allez maintenant utiliser les données que vous avez enregistrées ci-dessus.

    **Nom** : cette valeur est locale et doit être ce qui fonctionne dans votre environnement.

    **Transférer des événements au hub d’événements** : activez cette case à cocher.

    **ID de ressource Event-Hub** : cette valeur est l’ID de ressource d’espace de noms Event Hubs que vous avez enregistré lors de la configuration d’Event Hubs.

    **Nom du hub d’événements** : si vous avez créé un Event Hubs à l’intérieur de votre espace de noms Event Hubs, collez le nom Event Hubs que vous avez enregistré ci-dessus.

    Si vous choisissez de laisser Microsoft 365 Defender créer event hubs par types d’événements (tables) pour vous, laissez ce champ vide.

    **Types d’événements** : sélectionnez les tables Advanced Hunting que vous souhaitez transférer vers Event Hubs, puis vers votre application personnalisée. Les tables d’alerte proviennent de Microsoft 365 Defender, les tables d’appareils proviennent de Microsoft Defender pour point de terminaison (EDR) et Email tables proviennent de Microsoft Defender pour Office 365. Email Events enregistre toutes les transactions Email. L’URL (liens sécurisés), la pièce jointe (pièces jointes sécurisées) et les événements de remise (ZAP) sont également enregistrés et peuvent être joints aux événements Email sur le champ NetworkMessageId.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="Page Paramètres de l’API de diffusion en continu dans microsoft Portail Azure" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. Veillez à cliquer sur **Envoyer**.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hubs"></a>Vérifier que les événements sont exportés vers Event Hubs

Vous pouvez vérifier que les événements sont envoyés aux hubs d’événements en exécutant une requête de recherche avancée de base. Sélectionnez **Hunting** \> **Advanced Hunting** \> **Query** et entrez la requête suivante :

```console
EmailEvents
|join kind=fullouter EmailAttachmentInfo on NetworkMessageId
|join kind=fullouter EmailUrlInfo on NetworkMessageId
|join kind=fullouter EmailPostDeliveryEvents on NetworkMessageId
|where Timestamp > ago(1h)
|count
```

Cette requête vous montre le nombre d’e-mails reçus au cours de la dernière heure joints à toutes les autres tables. Il vous indique également si vous voyez des événements qui peuvent être exportés vers les hubs d’événements. Si ce nombre indique 0, aucune donnée ne s’affiche dans Event Hubs.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="Page de chasse avancée dans microsoft Portail Azure" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

Une fois que vous avez vérifié qu’il y a des données à exporter, vous pouvez afficher la page Event Hubs pour vérifier que les messages sont entrants. Ce processus peut prendre jusqu’à une heure.

1. Dans Azure, accédez à **Event Hub** \> En cliquant sur l’espace de **noms** \> **Event Hub**\>, cliquez sur le **hub d’événements**.
1. Sous **Vue d’ensemble**, faites défiler vers le bas et, dans le graphique Messages, vous devez voir les messages entrants. Si vous ne voyez aucun résultat, il n’y aura aucun message à ingérer pour votre application personnalisée.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="Page Vue d’ensemble dans microsoft 365 Portail Azure" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
