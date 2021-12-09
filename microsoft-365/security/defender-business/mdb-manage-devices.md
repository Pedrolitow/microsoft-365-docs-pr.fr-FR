---
title: Gérer les appareils dans Microsoft Defender pour les entreprises
description: Découvrez comment gérer les appareils dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 12/08/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 33087884da4b3f6e011963535784b14f9c2e9175
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61375183"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Gérer les appareils dans Microsoft Defender pour les entreprises

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Dans Microsoft Defender entreprise, vous pouvez gérer les appareils comme suit :

- [Afficher la liste des appareils intégrés pour](#view-the-list-of-onboarded-devices) voir leur niveau de risque, leur niveau d’exposition et leur état d’état d’état
- [Prendre des mesures sur un appareil qui présente](#take-action-on-a-device-that-has-threat-detections) des détections de menaces
- [Intégrer un appareil à Defender for Business](#onboard-a-device)  
- [Hors-carte d’un appareil de Defender for Business](#offboard-a-device)

## <a name="view-the-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Dans le volet de navigation, choisissez **Inventaire des appareils.**

3. Sélectionnez un appareil pour ouvrir son panneau volant, où vous pouvez en savoir plus sur son état et prendre des mesures. 

   Si vous n’avez pas encore répertorié d’appareils, intégrer des appareils [à Microsoft Defender pour Entreprises](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Prendre des mesures sur un appareil qui présente des détections de menaces

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Capture d’écran d’un appareil sélectionné avec les détails et les actions disponibles":::

1. In the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), in the navigation pane, choose Device **inventory**. 

2. Sélectionnez un appareil pour ouvrir son panneau volant et examinez les informations qui s’affichent.

3. Sélectionnez les ellipses (**...**) pour ouvrir le menu Actions. 

4. Sélectionnez une action, par exemple exécuter **une analyse antivirus** ou lancer une enquête **automatisée.** 

## <a name="onboard-a-device"></a>Intégrer un appareil

Voir [Appareils intégrés à Microsoft Defender pour Les Entreprises.](mdb-onboard-devices.md)

## <a name="offboard-a-device"></a>Hors-carte d’un appareil

Voir [Offboard a device](mdb-onboard-devices.md#what-if-i-want-to-offboard-a-device).

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)

- [Créer ou modifier des groupes d’appareils](mdb-create-edit-device-groups.md)
