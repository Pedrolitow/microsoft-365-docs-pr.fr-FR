---
title: Rapport d’état de l’appareil
description: Explique l’état de l’appareil
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: be685d39bbda3b96f689c13a3bc3485c011f1ec8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319878"
---
# <a name="device-status-report"></a>Rapport d’état de l’appareil

Ce rapport regroupe l’état de tous vos appareils inscrits pour afficher votre utilisation du service Microsoft Manged Desktop client.

Nous classons les appareils en fonction de leur activité au cours des 28 derniers jours et de notre capacité à maintenir la mise à jour de l’appareil.

Pour être mis à jour par Windows mise à jour dès que possible, un appareil doit :

- Être connecté à Internet.
- Ne pas mettre en veille prolongée.
- Non suspendue pendant au moins six heures, dont deux doivent être continues.

Bien qu’il soit possible qu’un appareil qui ne répond pas à ces exigences soit mis à jour. Les appareils qui les répondent ont la plus grande probabilité d’être mis à jour.

:::image type="content" source="../../media/mmd-device-status.png" alt-text="Rapport montrant le graphique de donut de l’état de l’activité de l’appareil en haut à gauche, afficher les filtres en haut à droite avec un bouton pour générer le rapport et le tableau des détails le long du bas":::

## <a name="device-status-labels"></a>Étiquettes d’état de l’appareil

Nous signalons l’état de l’appareil à l’aide des étiquettes suivantes :

| Étiquette d’état de l’appareil | Description |
| ------ | ------ |
| Prêt pour l’utilisateur | Appareils qui ont été enregistrés avec succès auprès de notre service et prêts à être attribués à un utilisateur.|
| Actif | Appareils en cours d’utilisation. <ul><li>Ils ont satisfait aux critères d’activité (six heures, deux en continu) pour la dernière version de mise à jour de sécurité.</li> <li>Ils ont vérifié avec Microsoft Intune au moins une fois au cours des cinq derniers jours.</li></ul> |
| Synchronisé | Appareils utilisés et qui ont été enregistrés avec Intune au cours des 28 derniers jours.
| Synchronisation non synchronisée | Appareils en cours d’utilisation, mais qui n’ont pas été enregistrés avec Intune au cours des 28 derniers jours. |
| Autre | L’étiquette regroupe plusieurs états d’erreur qui peuvent se produire, généralement lors de l’inscription de l’appareil. Pour plus d’informations, voir [Troubleshooting device registration](../get-started/manual-registration.md#troubleshooting-device-registration). |
