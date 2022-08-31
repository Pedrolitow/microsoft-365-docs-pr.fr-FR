---
title: Lier les résultats d'une requête à un incident
description: Lier les résultats d'une requête à un incident
keywords: repérage avancé, incident, tableau croisé dynamique, entité, chasse, événements pertinents, chasse aux menaces, repérage de cybermenaces, recherche, requête, télémétrie, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.openlocfilehash: 3e4682e7c1fb2cc0496bbf4c737b106e7c17fed1
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483187"
---
# <a name="link-query-results-to-an-incident"></a>Lier les résultats d'une requête à un incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Vous pouvez utiliser le lien vers la fonctionnalité d’incident pour ajouter des résultats de requête de chasse avancés à un incident nouveau ou existant en cours d’investigation. Cette fonctionnalité vous permet de capturer facilement des enregistrements à partir d’activités de chasse avancées, ce qui vous permet de créer une chronologie ou un contexte plus riche d’événements concernant un incident. 

## <a name="link-results-to-new-or-existing-incidents"></a>Lier les résultats à des incidents nouveaux ou existants

1. Dans la page de requête de repérage avancé, entrez d’abord votre requête dans le champ de requête fourni, puis sélectionnez **Exécuter la requête** pour obtenir vos résultats.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Page Requête dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-1.png":::

2. Dans la page Résultats, sélectionnez les événements ou enregistrements liés à une enquête nouvelle ou en cours sur laquelle vous travaillez, puis sélectionnez **Lier à l’incident**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Option Lien vers un incident de l’onglet Résultats dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-1b.png":::

3. Recherchez la section **Détails de l’alerte** dans le volet Lien vers un incident, puis **sélectionnez Créer un incident** pour convertir les événements en alertes et les regrouper en nouvel incident :

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Section Détails de l’alerte dans le volet Lien vers un incident dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Ou sélectionnez **Lier à un incident existant** pour ajouter les enregistrements sélectionnés à un incident existant. Choisissez l’incident associé dans la liste déroulante des incidents existants. Vous pouvez également entrer les premiers caractères du nom ou de l’ID de l’incident pour rechercher l’incident existant. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Section Détails de l’alerte dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-3-link-to-existing.png":::

4. Pour l’une ou l’autre sélection, fournissez les détails suivants, puis sélectionnez **Suivant** :
      - **Titre de l’alerte** : fournissez un titre descriptif pour les résultats que vos répondeurs d’incidents peuvent comprendre. Ce titre descriptif devient le titre de l’alerte.
      - **Gravité** : choisissez la gravité applicable au groupe d’alertes.
      - **Catégorie** : choisissez la catégorie de menace appropriée pour les alertes.
      - **Description** : fournissez une description utile pour les alertes groupées.
      - **Actions recommandées** : fournissez des actions de correction.

5. Dans la section **Entités impactées** , sélectionnez l’entité principale affectée ou affectée. Seules les entités applicables basées sur les résultats de la requête apparaissent dans cette section. Dans notre exemple, nous avons utilisé une requête pour rechercher des événements liés à un incident d’exfiltration de messagerie possible. Par conséquent, l’expéditeur est l’entité concernée. S’il existe quatre expéditeurs différents, par exemple, quatre alertes sont créées et liées à l’incident choisi.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Entité concernée dans la section Lien vers un incident dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. Sélectionnez **Suivant**.
1. Passez en revue les détails que vous avez fournis dans la section **Résumé** .
   :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Page de résultats dans la section Lien vers l’incident dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. Sélectionnez **Terminé**.

## <a name="view-linked-records-in-the-incident"></a>Afficher les enregistrements liés dans l’incident

Vous pouvez sélectionner le nom de l’incident auquel afficher l’incident auquel les événements sont liés.
:::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Écran détails de l’événement sous l’onglet Résumé dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-6-incident-pg.png":::

Dans notre exemple, les quatre alertes représentant les quatre événements sélectionnés ont été liées avec succès à un nouvel incident. 

Dans chacune des pages d’alerte, vous pouvez trouver les informations complètes sur l’événement ou les événements en mode chronologie (le cas échéant) et en mode résultats de requête.
:::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Les détails complets d’un événement sous l’onglet Chronologie dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-alert-story.png":::

Vous pouvez également sélectionner l’événement pour ouvrir le volet **Inspecter les enregistrements** .
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="Détails de l’enregistrement d’inspection d’un événement sous l’onglet Chronologie dans le portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Filtrer les événements ajoutés à l’aide de la chasse avancée
Vous pouvez afficher les alertes générées à partir de la chasse avancée en filtrant la file d’attente Incidents et la file d’attente d’alertes par source de détection **manuelle** .

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Filtrage manuel de la file d’attente Incidents et Alertes dans la page Filtres du portail Microsoft 365 Defender" lightbox="../../media/link-to-incident-8-filter.png":::
