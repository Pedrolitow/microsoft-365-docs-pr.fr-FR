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
ms.openlocfilehash: 4071d3a76430dd34776b2d4df3eae2b32e350a11
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62034844"
---
# <a name="device-status-report"></a>Rapport d’état de l’appareil

Ce rapport regroupe l’état de tous vos appareils inscrits pour afficher votre utilisation du service Microsoft Manged Desktop client. Nous classons les appareils en fonction de leur activité au cours des 28 derniers jours et de notre capacité à maintenir l’appareil à jour. Pour être mis à jour par Windows Update dès que possible, un appareil doit être connecté à Internet et ne doit pas être mis en veille prolongée ou suspendue pendant au moins six heures, dont deux doivent être en continu. Bien qu’il soit possible qu’un appareil qui ne réponde pas à ces exigences soit mis à jour, les appareils qui les répondent ont la probabilité la plus élevée d’être mis à jour.

:::image type="content" source="../../media/mmd-device-status.png" alt-text="Rapport montrant le graphique de donut de l’état de l’activité de l’appareil en haut à gauche, afficher les filtres en haut à droite avec un bouton pour générer le rapport et le tableau des détails le long du bas":::

Nous signalons l’état de l’appareil à l’aide des étiquettes ci-après : 

- **Prêt pour l’utilisateur**: appareils qui ont été correctement inscrits auprès de notre service et qui sont prêts à être attribués à un utilisateur 
- **Actif**: appareils utilisés et qui ont satisfait aux critères d’activité (six heures, deux en continu) pour la dernière version de mise à jour de sécurité et qui ont été enregistrés avec Microsoft Intune au moins une fois au cours des cinq derniers jours. 
- **Synchronisé :** appareils en cours d’utilisation et ayant été enregistrés avec Intune au cours des 28 derniers jours 
- **Non synchronisé :** appareils utilisés mais qui n’ont pas été enregistrés avec Intune au cours des 28 derniers jours 
- **Autre :** la catégorie regroupe plusieurs états d’erreur qui peuvent se produire, généralement pendant l’inscription de l’appareil. Pour plus d’informations, voir [Résolution des problèmes d’inscription de l’appareil.](../get-started/register-devices-self.md#troubleshooting-device-registration)