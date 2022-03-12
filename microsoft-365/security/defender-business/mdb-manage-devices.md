---
title: Gérer les appareils dans Microsoft Defender pour les entreprises
description: Découvrez comment gérer les appareils dans Microsoft Defender entreprise
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
ms.openlocfilehash: f229574461e4aa11efc8595270c0a92dcb91add2
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449188"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Gérer les appareils dans Microsoft Defender pour les entreprises

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Dans Microsoft Defender entreprise, vous pouvez gérer les appareils comme suit :

- [Afficher la liste des appareils intégrés pour](#view-the-list-of-onboarded-devices) voir leur niveau de risque, leur niveau d’exposition et leur état d’état d’état

- [Prendre des mesures sur un appareil qui présente](#take-action-on-a-device-that-has-threat-detections) des détections de menaces

- [Intégrer un appareil à Defender for Business](#onboard-a-device)  

- [Hors-carte d’un appareil de Defender for Business](#offboard-a-device)

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="view-the-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez Inventaire **des appareils**.

3. Sélectionnez un appareil pour ouvrir son panneau volant, où vous pouvez en savoir plus sur son état et prendre des mesures. 

   Si vous n’avez pas encore répertorié d’appareils, intégrer des appareils [à Microsoft Defender pour Entreprises](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Prendre des mesures sur un appareil qui présente des détections de menaces

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Capture d’écran d’un appareil sélectionné avec les détails et les actions disponibles":::

1. Dans le Microsoft 365 Defender web ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Inventaire des appareils**. 

2. Sélectionnez un appareil pour ouvrir son panneau volant et examinez les informations qui s’affichent.

3. Sélectionnez les ellipses (**...**) pour ouvrir le menu Actions. 

4. Sélectionnez une action, telle que **Exécuter une analyse antivirus** **ou Lancer une enquête automatisée**. 

## <a name="onboard-a-device"></a>Intégrer un appareil

[Consultez Les appareils intégrés à Microsoft Defender pour Entreprises](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Hors-carte d’un appareil

Voir [Laboarding d’un appareil](mdb-onboard-devices.md#offboarding-a-device).

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Créer ou modifier des groupes d’appareils](mdb-create-edit-device-groups.md)