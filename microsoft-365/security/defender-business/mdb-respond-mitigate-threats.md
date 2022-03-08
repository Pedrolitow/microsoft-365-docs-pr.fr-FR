---
title: Répondre aux menaces et les atténuer dans Microsoft Defender entreprise
description: Lorsque des menaces sont détectées, vous pouvez prendre des mesures pour y répondre et atténuer ces menaces.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 50a759c4f84aee72b376ff9126c54d381f4a373f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327782"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Répondre aux menaces et les atténuer dans Microsoft Defender entreprise

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Le portail Microsoft 365 Defender permet à votre équipe de sécurité de répondre aux menaces détectées et de les atténuer. Cet article vous présente un exemple d’utilisation de Defender pour Entreprises.

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="view-detected-threats"></a>Afficher les menaces détectées

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Cartes d’avis sur la page d’accueil. Les cartes vous indiquent en un coup d’œil le nombre de menaces détectées, ainsi que le nombre de comptes d’utilisateurs, de points de terminaison (appareils) et d’autres ressources affectées. L’image suivante est un exemple de cartes que vous pouvez voir :

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Capture d’écran des cartes dans le Microsoft 365 Defender web":::

3. Sélectionnez un bouton ou un lien sur la carte pour afficher plus d’informations et prendre des mesures. Par exemple, notre carte **Appareils à risque** inclut un bouton **Afficher les détails** . La sélection de ce bouton nous permet d’utiliser la page **Inventaire** des appareils, comme illustré dans l’image suivante :

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

   La page **Inventaire des appareils** répertorie les appareils de l’organisation, ainsi que leur niveau de risque et leur niveau d’exposition.

4. Sélectionnez un élément, tel qu’un appareil. Un volet volant s’ouvre et affiche plus d’informations sur les alertes et les incidents générés pour cet élément, comme illustré dans l’image suivante :  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Capture d’écran du volet volant d’un appareil sélectionné":::

5. Dans le volant, affichez les informations qui s’affichent. Sélectionnez les ellipses (...) pour ouvrir un menu qui répertorie les actions disponibles, comme illustré dans l’image suivante : 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Capture d’écran des actions disponibles pour un appareil sélectionné":::

6. Sélectionnez une action disponible. Par exemple, vous pouvez choisir Exécuter **l’analyse antivirus**, ce qui Antivirus Microsoft Defender démarrer une analyse rapide sur l’appareil. Vous pouvez également sélectionner Lancer **une enquête automatisée** pour déclencher une enquête automatisée sur l’appareil.

## <a name="next-steps"></a>Étapes suivantes

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)