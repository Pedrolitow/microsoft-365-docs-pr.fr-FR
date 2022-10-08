---
title: Techniques dans la chronologie de l’appareil
description: Présentation de la chronologie des appareils dans Microsoft Defender pour point de terminaison
keywords: chronologie de l’appareil, point de terminaison, MITRE, MITRE ATT&CK, techniques, tactiques
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: b028d9d571721ee933c3caa694b4578755b9f57f
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68221387"
---
# <a name="techniques-in-the-device-timeline"></a>Techniques dans la chronologie de l’appareil

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Vous pouvez obtenir plus d’informations dans une enquête en analysant les événements qui se sont produits sur un appareil spécifique. Tout d’abord, sélectionnez l’appareil qui vous intéresse dans la [liste Des appareils](machines-view-overview.md). Dans la page de l’appareil, vous pouvez sélectionner l’onglet **Chronologie** pour afficher tous les événements qui se sont produits sur l’appareil.

## <a name="understand-techniques-in-the-timeline"></a>Comprendre les techniques dans la chronologie

> [!IMPORTANT]
> Certaines informations concernent une fonctionnalité de produit prédéfinis en préversion publique qui peut être largement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Dans Microsoft Defender pour point de terminaison, **les techniques** sont un type de données supplémentaire dans la chronologie des événements. Les techniques fournissent des informations supplémentaires sur les activités associées à [MITRE ATT&techniques ou](https://attack.mitre.org/) sous-techniques CK.

Cette fonctionnalité simplifie l’expérience d’investigation en aidant les analystes à comprendre les activités observées sur un appareil. Les analystes peuvent alors décider d’examiner plus en détail.

Pour la préversion publique, les techniques sont disponibles par défaut et affichées avec les événements lors de l’affichage de la chronologie d’un appareil.

:::image type="content" source="images/device-timeline-2.png" alt-text="Techniques dans la chronologie de l’appareil" lightbox="images/device-timeline-2.png":::

Les techniques sont mises en surbrillance en gras et apparaissent avec une icône bleue à gauche. Le MITRE ATT correspondant&ID CK et le nom de la technique apparaissent également sous forme de balises sous Informations supplémentaires.

Les options de recherche et d’exportation sont également disponibles pour les techniques.

## <a name="investigate-using-the-side-pane"></a>Examiner à l’aide du volet latéral

Sélectionnez une technique pour ouvrir son volet latéral correspondant. Vous pouvez y voir des informations et des informations supplémentaires, telles que les techniques, tactiques et descriptions att&CK associées.

Sélectionnez la *technique d’attaque* spécifique pour ouvrir la page att&technique CK associée, où vous trouverez plus d’informations à ce sujet.

Vous pouvez copier les détails d’une entité lorsque vous voyez une icône bleue à droite. Par exemple, pour copier le SHA1 d’un fichier associé, sélectionnez l’icône de page bleue.

:::image type="content" source="images/techniques-side-pane-clickable.png" alt-text="Détails de l’entité à copier" lightbox="images/techniques-side-pane-clickable.png":::

Vous pouvez faire de même pour les lignes de commande.

:::image type="content" source="images/techniques-side-pane-command.png" alt-text="Option de copie de la ligne de commande" lightbox="images/techniques-side-pane-command.png":::

## <a name="investigate-related-events"></a>Examiner les événements associés

Pour utiliser la [chasse avancée](advanced-hunting-overview.md) pour rechercher des événements liés à la technique sélectionnée, sélectionnez **Chasser pour les événements connexes**. Cela conduit à la page de chasse avancée avec une requête pour rechercher les événements liés à la technique.

:::image type="content" source="images/techniques-hunt-for-related-events.png" alt-text="Option Rechercher les événements connexes" lightbox="images/techniques-hunt-for-related-events.png":::

> [!NOTE]
> L’interrogation à l’aide du bouton **Rechercher les événements connexes** à partir d’un volet technique affiche tous les événements liés à la technique identifiée, mais n’inclut pas la technique elle-même dans les résultats de la requête.

## <a name="customize-your-device-timeline"></a>Personnaliser la chronologie de votre appareil

En haut à droite de la chronologie de l’appareil, vous pouvez choisir une plage de dates pour limiter le nombre d’événements et de techniques dans la chronologie.

Vous pouvez personnaliser les colonnes à exposer. Vous pouvez également filtrer les événements avec indicateur par type de données ou par groupe d’événements.

### <a name="choose-columns-to-expose"></a>Choisir les colonnes à exposer

Vous pouvez choisir les colonnes à exposer dans la chronologie en sélectionnant le bouton **Choisir des colonnes** .

:::image type="content" source="images/filter-customize-columns.png" alt-text="Volet dans lequel vous pouvez personnaliser les colonnes" lightbox="images/filter-customize-columns.png":::


À partir de là, vous pouvez sélectionner les informations à inclure.

### <a name="filter-to-view-techniques-or-events-only"></a>Filtrer pour afficher uniquement les techniques ou les événements

Pour afficher uniquement les événements ou techniques, sélectionnez **Filtres** dans la chronologie de l’appareil et choisissez votre type de données préféré à afficher.

:::image type="content" source="images/device-timeline-filters.png" alt-text="Volet Filtres" lightbox="images/device-timeline-filters.png":::

## <a name="see-also"></a>Voir aussi

- [Afficher et organiser la liste des appareils](machines-view-overview.md)
- [Microsoft Defender pour point de terminaison indicateurs d’événements de chronologie de l’appareil](device-timeline-event-flag.md)
