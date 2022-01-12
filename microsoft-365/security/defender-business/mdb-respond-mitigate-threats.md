---
title: Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)
description: Lorsque des menaces sont détectées, vous pouvez prendre des mesures pour y répondre et atténuer ces menaces.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 12/13/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 6ed538eac8d60acbd8ff2947207c79dfb7d9e482
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61937039"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business-preview"></a>Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Le portail Microsoft 365 Defender permet à votre équipe de sécurité de répondre aux menaces détectées et de les atténuer. Cet article vous présente un exemple d’utilisation de Defender pour Entreprises (prévisualisation).

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise.</a> Vos commentaires sont les bienvenus.
>

## <a name="view-detected-threats"></a>Afficher les menaces détectées

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Cartes d’avis sur la page d’accueil. Les cartes vous indiquent en un coup d’œil le nombre de menaces détectées, ainsi que le nombre de comptes d’utilisateurs, de points de terminaison (appareils) et d’autres ressources affectées. L’image suivante est un exemple de cartes que vous pouvez voir :

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Capture d’écran des cartes dans le portail Microsoft 365 Defender web":::

3. Sélectionnez un bouton ou un lien sur la carte pour afficher plus d’informations et prendre des mesures. Par exemple, notre carte **Appareils à risque** inclut un bouton Afficher les **détails.** La sélection de ce bouton nous permet d’utiliser la page **Inventaire** des appareils, comme illustré dans l’image suivante :

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

   La page **Inventaire des appareils** répertorie les appareils de l’entreprise, ainsi que leur niveau de risque et leur niveau d’exposition.

4. Sélectionnez un élément, tel qu’un appareil. Un volet volant s’ouvre et affiche plus d’informations sur les alertes et les incidents générés pour cet élément, comme illustré dans l’image suivante :  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Capture d’écran du volet volant d’un appareil sélectionné":::

5. Dans le volant, affichez les informations qui s’affichent. Sélectionnez les ellipses (...) pour ouvrir un menu qui répertorie les actions disponibles, comme illustré dans l’image suivante : 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Capture d’écran des actions disponibles pour un appareil sélectionné":::

6. Sélectionnez une action disponible. Par exemple, vous pouvez choisir Exécuter **l’analyse antivirus,** ce qui Antivirus Microsoft Defender démarrer une analyse rapide sur l’appareil. Vous pouvez également sélectionner Lancer **une enquête automatisée** pour déclencher une enquête automatisée sur l’appareil.

## <a name="next-steps"></a>Prochaines étapes

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation)](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)
