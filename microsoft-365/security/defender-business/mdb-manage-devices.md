---
title: Gérer les appareils dans Microsoft Defender pour les PME
description: Découvrez comment gérer des appareils dans Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 453cce2c52902116bc3eaa71f5e6c998ab4164a1
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862827"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Gérer les appareils dans Microsoft Defender pour les PME

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 

Dans Microsoft Defender pour les PME, vous pouvez gérer les appareils comme suit :

- [Afficher la liste des appareils intégrés](#view-the-list-of-onboarded-devices) pour voir leur niveau de risque, leur niveau d’exposition et leur état d’intégrité
- [Prendre des mesures sur un appareil](#take-action-on-a-device-that-has-threat-detections) qui a des détections de menaces
- [Intégrer un appareil à Defender pour Entreprises](#onboard-a-device)  
- [Déconnecter un appareil de Defender entreprise](#offboard-a-device)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="view-the-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Inventaire des appareils**.

3. Sélectionnez un appareil pour ouvrir son panneau volant, où vous pouvez en savoir plus sur son état et prendre des mesures. 

   Si vous n’avez pas encore d’appareils répertoriés, [intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Prendre des mesures sur un appareil qui a des détections de menaces

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Capture d’écran d’un appareil sélectionné avec les détails et les actions disponibles":::

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Inventaire des appareils**. 

2. Sélectionnez un appareil pour ouvrir son panneau volant et passez en revue les informations affichées.

3. Sélectionnez les points de suspension (**...**) pour ouvrir le menu Actions. 

4. Sélectionnez une action, telle que **Exécuter l’analyse antivirus** ou **Lancer une investigation automatisée**. 

## <a name="onboard-a-device"></a>Intégrer un appareil

Consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Désintégrage d’un appareil

Voir [Désintégrage d’un appareil](mdb-offboard-devices.md).

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)
- [Créer ou modifier des groupes d’appareils](mdb-create-edit-device-groups.md)