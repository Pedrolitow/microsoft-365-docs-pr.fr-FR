---
title: Microsoft Defender pour point de terminaison connexion d’API à Power BI
ms.reviewer: ''
description: Créez un rapport Power Business Intelligence (BI) en plus de Microsoft Defender pour point de terminaison API.
keywords: api, api prises en charge, Power BI, rapports
ms.service: microsoft-365-security
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
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 3a2365dbc2e58d33b11c75faeca7e8f3fb39dfb8
ms.sourcegitcommit: d0557f757cfa48330ed57e966033891d10f03688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2022
ms.locfileid: "68492613"
---
# <a name="create-custom-reports-using-power-bi"></a>Créer des rapports personnalisés à l’aide de Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> [!NOTE]
>**Avant de commencer** : vous devez d’abord [créer une application](/microsoft-365/security/defender-endpoint/apis-intro).

Dans cette section, vous allez apprendre à créer un rapport Power BI sur les API Defender pour point de terminaison.

Le premier exemple montre comment connecter Power BI à l’API de repérage avancé, et le deuxième exemple montre une connexion à nos API OData, telles que des actions de machine ou des alertes.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>Connecter Power BI à l’API de repérage avancé

1. Ouvrez Microsoft Power BI.

2. Sélectionnez Obtenir une **requête vide** de **données**\>.
   :::image type="content" source="images/power-bi-create-blank-query.png" alt-text="Option Requête vide sous l’élément de menu Obtenir des données" lightbox="images/power-bi-create-blank-query.png":::

3. Sélectionnez **Éditeur avancé**.
   :::image type="content" source="images/power-bi-open-advanced-editor.png" alt-text="Élément de menu Éditeur avancé" lightbox="images/power-bi-open-advanced-editor.png":::

4. Copiez ce qui suit et collez-le dans l’éditeur :

   ```
       let
           AdvancedHuntingQuery = "DeviceEvents | where ActionType contains 'Anti' | limit 20",
   
           HuntingUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries",
   
           Response = Json.Document(Web.Contents(HuntingUrl, [Query=[key=AdvancedHuntingQuery]])),
   
           TypeMap = #table(
               { "Type", "PowerBiType" },
               {
                   { "Double",   Double.Type },
                   { "Int64",    Int64.Type },
                   { "Int32",    Int32.Type },
                   { "Int16",    Int16.Type },
                   { "UInt64",   Number.Type },
                   { "UInt32",   Number.Type },
                   { "UInt16",   Number.Type },
                   { "Byte",     Byte.Type },
                   { "Single",   Single.Type },
                   { "Decimal",  Decimal.Type },
                   { "TimeSpan", Duration.Type },
                   { "DateTime", DateTimeZone.Type },
                   { "String",   Text.Type },
                   { "Boolean",  Logical.Type },
                   { "SByte",    Logical.Type },
                   { "Guid",     Text.Type }
               }),
   
           Schema = Table.FromRecords(Response[Schema]),
           TypedSchema = Table.Join(Table.SelectColumns(Schema, {"Name", "Type"}), {"Type"}, TypeMap , {"Type"}),
           Results = Response[Results],
           Rows = Table.FromRecords(Results, Schema[Name]),
           Table = Table.TransformColumnTypes(Rows, Table.ToList(TypedSchema, (c) => {c{0}, c{2}}))
   
       in Table
   ```

5. Sélectionnez **Terminé**.

6. Sélectionnez **Modifier les informations d’identification**.

   :::image type="content" source="images/power-bi-edit-credentials.png" alt-text="Élément de menu Modifier les informations d’identification" lightbox="images/power-bi-edit-credentials.png":::

7. Sélectionnez **Connexion au** compte \> **d’organisation**.

   :::image type="content" source="images/power-bi-set-credentials-organizational.png" alt-text="Option De connexion dans l’élément de menu Compte professionnel" lightbox="images/power-bi-set-credentials-organizational.png":::

8. Entrez vos informations d’identification et attendez d’être connecté.

9. Sélectionnez **Connexion**.

   :::image type="content" source="images/power-bi-set-credentials-organizational-cont.png" alt-text="Message de confirmation de connexion dans l’élément de menu Compte professionnel" lightbox="images/power-bi-set-credentials-organizational-cont.png":::

À présent, les résultats de votre requête s’affichent sous forme de tableau et vous pouvez commencer à créer des visualisations dessus !

Vous pouvez dupliquer cette table, la renommer et modifier la requête Advanced Hunting à l’intérieur pour obtenir toutes les données souhaitées.

## <a name="connect-power-bi-to-odata-apis"></a>Connecter Power BI aux API OData

La seule différence par rapport à l’exemple précédent est la requête à l’intérieur de l’éditeur. Suivez les étapes 1 à 3 ci-dessus.

À l’étape 4, au lieu du code de cet exemple, copiez le code ci-dessous et collez-le dans l’éditeur pour extraire toutes les **actions** de machine de votre organisation :

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

Vous pouvez faire de même pour **les alertes et les** **machines**.
Vous pouvez également utiliser des requêtes OData pour les filtres de requêtes, voir [Utilisation des requêtes OData](exposed-apis-odata-samples.md).

## <a name="power-bi-dashboard-samples-in-github"></a>Exemples de tableau de bord Power BI dans GitHub

Pour plus d’informations, consultez les [modèles de rapport Power BI](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI).

## <a name="sample-reports"></a>Exemples de rapports

Affichez les Microsoft Defender pour point de terminaison exemples de rapport Power BI. Pour plus d’informations, consultez [Les exemples de code Parcourir](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>Voir aussi

- [API Defender pour point de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Utilisation des requêtes OData](exposed-apis-odata-samples.md)
