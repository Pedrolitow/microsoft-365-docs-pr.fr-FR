---
title: Techniques dans la chronologie de l’appareil
description: Présentation de la chronologie de l’appareil dans Microsoft Defender pour le point de terminaison
keywords: chronologie de périphérique, point de terminaison, MITRE, MITRE ATT&CK, techniques, tactiques
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d724b7663bd4484c630e97362eb5766490e1fa8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465902"
---
# <a name="techniques-in-the-device-timeline"></a>Techniques dans la chronologie de l’appareil

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Vous pouvez obtenir plus d’informations dans une enquête en analysant les événements qui se sont produit sur un appareil spécifique. Tout d’abord, sélectionnez l’appareil qui vous intéresse dans la liste [Appareils](machines-view-overview.md). Dans la page Appareil, vous pouvez sélectionner l’onglet **Chronologie pour** afficher tous les événements qui se sont produits sur l’appareil.

## <a name="understand-techniques-in-the-timeline"></a>Comprendre les techniques dans la chronologie

> [!IMPORTANT]
> Certaines informations concernent une fonctionnalité de produit pré-publiée en prévisualisation publique qui peut être considérablement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Dans Microsoft Defender pour point de terminaison, **les techniques** sont un type de données supplémentaire dans la chronologie des événements. Les techniques fournissent plus d’informations sur les activités associées à [MITRE ATT&techniques ou](https://attack.mitre.org/) sous-techniques CK.

Cette fonctionnalité simplifie l’examen en aidant les analystes à comprendre les activités observées sur un appareil. Les analystes peuvent ensuite décider d’examiner plus en détail.

Pour la prévisualisation publique, les techniques sont disponibles par défaut et affichées avec les événements lorsque la chronologie d’un appareil est affichée.

:::image type="content" source="images/device-timeline-2.png" alt-text="Techniques dans la chronologie de l’appareil" lightbox="images/device-timeline-2.png":::

Les techniques sont mises en évidence en gras et apparaissent avec une icône bleue à gauche. L’ID MITRE ATT&et le nom de technique CK correspondants apparaissent également en tant que balises sous Informations supplémentaires.

Les options de recherche et d’exportation sont également disponibles pour les techniques.

## <a name="investigate-using-the-side-pane"></a>Examiner l’utilisation du volet latéral

Sélectionnez une technique pour ouvrir son volet latéral correspondant. Vous y verrez des informations et des informations supplémentaires, telles que des techniques, des tactiques et des descriptions att&CK associées.

Sélectionnez la *technique d’attaque* spécifique pour ouvrir la page de technique att&CK associée dans laquelle vous trouverez plus d’informations à ce sujet.

Vous pouvez copier les détails d’une entité lorsque vous voyez une icône bleue à droite. Par exemple, pour copier le sha1 d’un fichier associé, sélectionnez l’icône de page bleue.

:::image type="content" source="images/techniques-side-pane-clickable.png" alt-text="Détails de l’entité à copier" lightbox="images/techniques-side-pane-clickable.png":::

Vous pouvez faire de même pour les lignes de commande.

:::image type="content" source="images/techniques-side-pane-command.png" alt-text="Option de copie de ligne de commande" lightbox="images/techniques-side-pane-command.png":::

## <a name="investigate-related-events"></a>Examiner les événements connexes

Pour utiliser la [recherche avancée pour](advanced-hunting-overview.md) rechercher des événements liés à la technique sélectionnée, sélectionnez **Rechercher les événements connexes**. Cela conduit à la page de recherche avancée avec une requête pour rechercher les événements liés à la technique.

:::image type="content" source="images/techniques-hunt-for-related-events.png" alt-text="Option De recherche d’événements connexes" lightbox="images/techniques-hunt-for-related-events.png":::

> [!NOTE]
> L’interrogation à l’aide du bouton Recherche d’événements connexes à partir d’un volet latéral Technique affiche tous les événements liés à la technique identifiée, mais n’inclut pas la technique elle-même dans les résultats de la requête.

## <a name="customize-your-device-timeline"></a>Personnaliser la chronologie de votre appareil

Dans la partie supérieure droite de la chronologie de l’appareil, vous pouvez choisir une plage de dates pour limiter le nombre d’événements et de techniques dans la chronologie.

Vous pouvez personnaliser les colonnes à exposer. Vous pouvez également filtrer les événements marqués par type de données ou par groupe d’événements.

### <a name="choose-columns-to-expose"></a>Choisir les colonnes à exposer

Vous pouvez choisir les colonnes à exposer dans la chronologie en sélectionnant le bouton Choisir **les colonnes** .

:::image type="content" source="images/filter-customize-columns.png" alt-text="Volet dans lequel vous pouvez personnaliser des colonnes" lightbox="images/filter-customize-columns.png":::


À partir de là, vous pouvez sélectionner l’ensemble d’informations à inclure.

### <a name="filter-to-view-techniques-or-events-only"></a>Filtre pour afficher les techniques ou les événements uniquement

Pour afficher uniquement les événements ou les techniques, sélectionnez **Filtres** dans la chronologie de l’appareil et choisissez votre type de données préféré à afficher.

:::image type="content" source="images/device-timeline-filters.png" alt-text="Volet Filtres" lightbox="images/device-timeline-filters.png":::

## <a name="see-also"></a>Voir aussi

- [Afficher et organiser la liste des appareils](machines-view-overview.md)
- [Indicateurs d’événement de chronologie d’appareil Microsoft Defender pour point de terminaison](device-timeline-event-flag.md)
