---
title: Connexion des API Microsoft Defender for Endpoint Power BI
ms.reviewer: ''
description: Créez un rapport d’aide à la création de rapports Power Business Intelligence (BI) en plus des API Microsoft Defender pour les points de terminaison.
keywords: api, api pris en charge, Power BI, rapports
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4cad6fd5188745773ce561d1db697989598a1dc5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472152"
---
# <a name="create-custom-reports-using-power-bi"></a>Créer des rapports personnalisés à l’aide Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Dans cette section, vous allez apprendre à créer un rapport Power BI sur les API Defender for Endpoint.

Le premier exemple montre comment connecter des Power BI à l’API de recherche avancée et le deuxième exemple illustre une connexion à nos API OData, telles que les actions de l’ordinateur ou les alertes.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>Connecter Power BI à l’API de recherche avancée

- Ouvrez Microsoft Power BI.

- Cliquez **sur Obtenir une** \> **requête vide de données**.

  :::image type="content" source="images/power-bi-create-blank-query.png" alt-text="Option Requête vide sous l’élément de menu Obtenir les données" lightbox="images/power-bi-create-blank-query.png":::

- Cliquez sur **Éditeur avancé**.

  :::image type="content" source="images/power-bi-open-advanced-editor.png" alt-text="Élément de menu De l’Éditeur avancé" lightbox="images/power-bi-open-advanced-editor.png":::

- Copiez le texte ci-dessous et collez-le dans l’éditeur :

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

- Cliquez sur **Terminé**.

- Cliquez sur **Modifier les informations d’identification**.

    :::image type="content" source="images/power-bi-edit-credentials.png" alt-text="Élément de menu Modifier les informations d’identification" lightbox="images/power-bi-edit-credentials.png":::
    

- Sélectionnez **Compte d’organisation** \> **Connectez-vous**.

    :::image type="content" source="images/power-bi-set-credentials-organizational.png" alt-text="Option De se connecter dans l’élément de menu Compte d’organisation" lightbox="images/power-bi-set-credentials-organizational.png":::

- Entrez vos informations d’identification et attendez d’être connexion.

- Cliquez sur **Connecter**.

    :::image type="content" source="images/power-bi-set-credentials-organizational-cont.png" alt-text="Message de confirmation de la signature dans l’élément de menu Compte d’organisation" lightbox="images/power-bi-set-credentials-organizational-cont.png":::

- À présent, les résultats de votre requête s’affichent sous la mesure d’une table et vous pouvez commencer à créer des visualisations par-dessus !

- Vous pouvez dupliquer cette table, la renommer et modifier la requête de recherche avancée à l’intérieur pour obtenir les données que vous souhaitez.

## <a name="connect-power-bi-to-odata-apis"></a>Connecter Power BI aux API OData

- La seule différence par rapport à l’exemple ci-dessus est la requête à l’intérieur de l’éditeur.

- Copiez le texte ci-dessous et collez-le dans l’éditeur pour tirer toutes les **actions de** l’ordinateur de votre organisation :

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

- Vous pouvez faire de même pour les **alertes et** les **ordinateurs**.
- Vous pouvez également utiliser des requêtes OData pour les filtres de requêtes, voir [Utilisation de requêtes OData](exposed-apis-odata-samples.md).

## <a name="power-bi-dashboard-samples-in-github"></a>Power BI exemples de tableau de bord dans GitHub

Pour plus d’informations, [voir Power BI modèles de rapport.](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI)

## <a name="sample-reports"></a>Exemples de rapports

Affichez les exemples de rapport microsoft Defender pour Power BI de point de terminaison. Pour plus d’informations, voir [Parcourir les exemples de code](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>Sujets associés

- [API Defender pour les points de terminaison](apis-intro.md)
- [API de recherche avancée de menaces](run-advanced-query-api.md)
- [Utilisation des requêtes OData](exposed-apis-odata-samples.md)
