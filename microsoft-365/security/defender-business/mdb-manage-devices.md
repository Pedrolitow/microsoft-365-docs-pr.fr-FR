---
title: Gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation)
description: Découvrez comment gérer les appareils dans Microsoft Defender entreprise (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 498fa3824ec1e022cbf0abcb0c7789e5e236262e
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62879191"
---
# <a name="manage-devices-in-microsoft-defender-for-business-preview"></a>Gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Dans Microsoft Defender entreprise (prévisualisation), vous pouvez gérer les appareils comme suit :

- [Afficher la liste des appareils intégrés pour](#view-the-list-of-onboarded-devices) voir leur niveau de risque, leur niveau d’exposition et leur état d’état d’état
- [Prendre des mesures sur un appareil qui présente](#take-action-on-a-device-that-has-threat-detections) des détections de menaces
- [Intégrer un appareil à Defender for Business (prévisualisation)](#onboard-a-device)  
- [Hors-carte d’un appareil de Defender for Business (prévisualisation)](#offboard-a-device)

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="view-the-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez Inventaire **des appareils**.

3. Sélectionnez un appareil pour ouvrir son panneau volant, où vous pouvez en savoir plus sur son état et prendre des mesures. 

   Si vous n’avez pas encore répertorié d’appareils, intégrer des appareils [à Microsoft Defender pour Entreprises (prévisualisation)](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Prendre des mesures sur un appareil qui présente des détections de menaces

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Capture d’écran d’un appareil sélectionné avec les détails et les actions disponibles":::

1. Dans le Microsoft 365 Defender web ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Inventaire des appareils**. 

2. Sélectionnez un appareil pour ouvrir son panneau volant et examinez les informations qui s’affichent.

3. Sélectionnez les ellipses (**...**) pour ouvrir le menu Actions. 

4. Sélectionnez une action, telle que **Exécuter une analyse antivirus** **ou Lancer une enquête automatisée**. 

## <a name="onboard-a-device"></a>Intégrer un appareil

Voir [Appareils intégrés à Microsoft Defender pour Entreprises (prévisualisation).](mdb-onboard-devices.md)

## <a name="offboard-a-device"></a>Hors-carte d’un appareil

Voir [Laboarding d’un appareil](mdb-onboard-devices.md#offboarding-a-device).

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Créer ou modifier des groupes d’appareils](mdb-create-edit-device-groups.md)
