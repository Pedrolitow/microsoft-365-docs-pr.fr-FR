---
title: Gérer les appareils dans Microsoft Defender pour entreprises
description: Découvrez comment ajouter, supprimer et gérer des appareils dans Defender entreprise, endpoint protection pour les petites et moyennes entreprises.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 09/14/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: bb774fdc3b6fb2eac29c3fc09ec48cfc4841df7a
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67710650"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>Gérer les appareils dans Microsoft Defender pour entreprises

Dans Defender entreprise, vous pouvez gérer les appareils comme suit :

- [Afficher la liste des appareils intégrés](#view-the-list-of-onboarded-devices) pour voir leur niveau de risque, leur niveau d’exposition et leur état d’intégrité
- [Prendre des mesures sur un appareil](#take-action-on-a-device-that-has-threat-detections) qui a des détections de menaces
- [Intégrer un appareil à Defender pour Entreprises](#onboard-a-device)  
- [Déconnecter un appareil de Defender entreprise](#offboard-a-device)


## <a name="view-the-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d'écran de l'inventaire des appareils":::

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, accédez à **Périphériques multimédias** > .

3. Sélectionnez un appareil pour ouvrir son panneau volant, où vous pouvez en savoir plus sur son état et prendre des mesures. 

   Si vous n’avez pas encore d’appareils répertoriés, [intégrer des appareils à Defender entreprise](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>Prendre des mesures sur un appareil qui a des détections de menaces

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="Capture d’écran d’un appareil sélectionné avec les détails et les actions disponibles":::

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, accédez à **Assets** > **Devices**. 

2. Sélectionnez un appareil pour ouvrir son panneau volant et passez en revue les informations affichées.

3. Sélectionnez les points de suspension (**...**) pour ouvrir le menu Actions. 

4. Sélectionnez une action, telle que **Exécuter l’analyse antivirus** ou **Lancer une investigation automatisée**. 

## <a name="onboard-a-device"></a>Intégrer un appareil

Consultez [Intégrer des appareils à Defender pour Entreprises](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>Annuler l’intégration d’un appareil

Voir [Désintégrage d’un appareil](mdb-offboard-devices.md).

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Defender entreprise](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)
- [Créer ou modifier des groupes d’appareils](mdb-create-edit-device-groups.md)