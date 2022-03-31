---
title: Lier les résultats d'une requête à un incident
description: Lier les résultats d'une requête à un incident
keywords: advanced hunting, incident, pivot, entity, go hunt, relevant events, threat hunting, cyber threat hunting, search, query, telemetry, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: c81b0b0850686242c675629cf99fa2c4b3a18496
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755492"
---
# <a name="link-query-results-to-an-incident"></a>Lier les résultats d'une requête à un incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Vous pouvez utiliser le lien vers la fonctionnalité d’incident pour ajouter des résultats de requête de recherche avancée à un incident nouveau ou existant en cours d’examen. Cette fonctionnalité vous permet de capturer facilement des enregistrements à partir d’activités de recherche avancées, ce qui vous permet de créer une chronologie plus riche ou un contexte d’événements concernant un incident. 

## <a name="link-results-to-new-or-existing-incidents"></a>Lier les résultats à des incidents nouveaux ou existants

1. Dans la page requête de recherche avancée, entrez d’abord votre requête dans le champ de requête fourni, puis sélectionnez Exécuter la **requête pour obtenir** vos résultats.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Page Requête dans le portail Microsoft 365 Defender web" lightbox="../../media/link-to-incident-1.png":::

2. Dans la page Résultats, sélectionnez les événements ou les enregistrements liés à un examen nouveau ou en cours sur qui vous travaillez, puis sélectionnez Lien **vers l’incident**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Option Lien vers l’incident de l’onglet Résultats dans le portail Microsoft 365 Defender web" lightbox="../../media/link-to-incident-1b.png":::

3. Recherchez **la section Détails** de l’alerte dans le volet Lien vers **l’incident** , puis sélectionnez Créer un incident pour convertir les événements en alertes et les grouper en un nouvel incident :

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Section Détails de l’alerte dans le volet Lien vers l’incident du portail Microsoft 365 Defender web" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Ou **sélectionnez Lien vers un incident existant** pour ajouter les enregistrements sélectionnés à un incident existant. Choisissez l’incident connexe dans la liste des incidents existants. Vous pouvez également entrer les premiers caractères du nom ou de l’ID de l’incident pour rechercher l’incident existant. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Section Détails de l’alerte dans le portail Microsoft 365 Defender web" lightbox="../../media/link-to-incident-3-link-to-existing.png":::

4. Pour l’une ou l’autre des sélections, fournissez les détails suivants, puis sélectionnez **Suivant** :
      - **Titre de l’alerte** : fournissez un titre descriptif pour les résultats que vos répondeurs aux incidents peuvent comprendre. Ce titre descriptif devient le titre de l’alerte.
      - **Gravité :** choisissez la gravité applicable au groupe d’alertes.
      - **Catégorie** : choisissez la catégorie de menace appropriée pour les alertes.
      - **Description** : donnez une description utile des alertes groupées.
      - **Actions recommandées** : fournir des actions de correction.

5. Dans la section **Entités concernées** , sélectionnez l’entité principale affectée ou concernée. Seules les entités applicables basées sur les résultats de la requête apparaissent dans cette section. Dans notre exemple, nous avons utilisé une requête pour rechercher les événements liés à un éventuel incident d’exfiltration de courrier électronique, par conséquent l’expéditeur est l’entité impactée. S’il existe quatre expéditeurs différents, par exemple, quatre alertes sont créées et liées à l’incident choisi.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Entité impactée dans la section Lien vers l’incident du portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. Sélectionnez **Suivant**.
1. Examinez les détails que vous avez fournis dans la section **Résumé** .
   :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Page des résultats dans la section Lien vers l’incident du portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. Sélectionnez **Terminé**.

## <a name="view-linked-records-in-the-incident"></a>Afficher les enregistrements liés dans l’incident

Vous pouvez sélectionner le nom de l’incident pour afficher l’incident lié aux événements.
:::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Écran détails de l’événement dans l’onglet Résumé du portail Microsoft 365 Defender web" lightbox="../../media/link-to-incident-6-incident-pg.png":::

Dans notre exemple, les quatre alertes, représentant les quatre événements sélectionnés, ont été liées avec succès à un nouvel incident. 

Dans chacune des pages d’alerte, vous pouvez trouver les informations complètes sur l’événement ou les événements dans l’affichage chronologie (si disponible) et les résultats de la requête.
:::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Détails complets d’un événement dans l’onglet Chronologie du portail Microsoft 365 Defender web" lightbox="../../media/link-to-incident-7-alert-story.png":::

Vous pouvez également sélectionner l’événement pour ouvrir le **volet Inspecter l’enregistrement** .
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="Détails de l’enregistrement d’inspection d’un événement dans l’onglet Chronologie du portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Filtre des événements ajoutés à l’aide du chasse avancée
Vous pouvez afficher les alertes générées à partir d’un repérage avancé en filtrant la file d’attente Incidents et la file d’attente d’alertes par source **de** détection manuelle.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Filtrage manuel de la file d’attente Incidents et alertes dans la page Filtres du portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-8-filter.png":::
