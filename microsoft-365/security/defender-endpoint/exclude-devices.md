---
title: Exclure des appareils dans Microsoft Defender pour le point de terminaison
description: Exclure des appareils de la liste d’inventaire des appareils
keywords: exclude
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c17bea7b6a3decdb1cf20f21067c316366c2afed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63331084"
---
# <a name="exclude-devices"></a>Exclure des appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-threat-and-vulnerability-management"></a>Exclure des appareils des Gestion des menaces et des vulnérabilités

L’exclusion des appareils inactifs, dupliqués ou hors de portée vous permet de vous concentrer sur la découverte et la hiérérisation des risques sur vos appareils actifs. Cette action peut également vous aider à refléter un score d’Gestion des menaces et des vulnérabilités plus précis, car les appareils exclus ne seront pas visibles dans vos rapports Gestion des menaces et des vulnérabilités données.

Une fois les appareils exclus, vous ne pourrez pas afficher les informations mises à jour ou pertinentes sur les vulnérabilités et les logiciels installés sur ces appareils. Elle affecte toutes les pages Gestion des menaces et des vulnérabilités, les rapports et les tables associées dans le recherche avancée.

Même si la fonctionnalité d’exclusion d’appareil supprime les données de l’appareil des pages et des rapports gestion des vulnérabilités, les appareils restent connectés au réseau et peuvent toujours être un risque pour l’organisation. Vous pourrez annuler l’exclusion de l’appareil à tout moment.

## <a name="how-to-exclude-a-device"></a>Comment exclure un appareil

Vous pouvez choisir d’exclure un ou plusieurs appareils en même temps.

### <a name="exclude-a-single-device"></a>Exclure un seul appareil

1. Go to the **Device inventory** page and select the device to exclude.
2. **Sélectionnez Exclure** de la barre d’action de la page d’inventaire des appareils ou du menu Actions du menu volant de l’appareil.

![Image de l’option de menu Exclure l’appareil.](images/exclude-devices-menu.png)

 3. Sélectionnez une justification :

    - Appareil inactif
    - Dispositif en double
    - L’appareil n’existe pas
    - Non compris  
    - Autre

4. Tapez une note et sélectionnez **Exclure l’appareil**.

![Image de l’appareil d’exclusion.](images/exclude-device.png)

Vous pouvez également exclure un appareil de sa page d’appareil.

> [!NOTE]
> L’exclusion des appareils actifs n’est pas recommandée, car il est particulièrement risqué de ne pas avoir de visibilité sur leurs informations de vulnérabilité. Si un appareil est actif et que vous essayez de l’exclure, vous recevrez un message d’avertissement et une fenêtre de confirmation vous demandant si vous êtes sûr de vouloir exclure un appareil actif.

L’exclusion complète d’un appareil des vues et des données d’un appareil peut prendre jusqu’à gestion des vulnérabilités 10 heures.

Les appareils exclus sont toujours visibles dans la liste d’inventaire des appareils. Vous pouvez gérer votre affichage des appareils exclus en :

- Ajout de la colonne **d’état Exclusion** à l’affichage d’inventaire des appareils.
- Utilisation du filtre  **d’étatExclusion**  pour afficher la liste des appareils appropriés.

![Image de l’état d’exclusion.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Exclusion d’appareils en bloc

Vous pouvez également choisir d’exclure plusieurs appareils en même temps :

1. Go to the **Device inventory** page and select the devices to exclude.

2. Dans la barre d’actions, sélectionnez **Exclure**.

3. Choisissez une justification et sélectionnez **Exclure l’appareil**.

Si vous sélectionnez plusieurs appareils dans la liste des appareils avec différents statuts d’exclusion, le volant exclure les appareils sélectionnés vous fournira des détails sur le nombre d’appareils sélectionnés qui sont déjà exclus. Vous pouvez à nouveau exclure les appareils, mais la justification et les remarques seront indessérables.

![Image d’exclusion en bloc](images/exclude-device-bulk.png)

Une fois qu’un appareil est exclu, si vous allez sur la page d’appareil d’un appareil exclu, vous ne pourrez pas voir les données pour les vulnérabilités découvertes, l’inventaire logiciel ou les recommandations de sécurité. Les données ne s’afficheront pas non plus dans les pages gestion des vulnérabilités, les tableaux de recherche avancés associés et le rapport des appareils vulnérables.

## <a name="stop-excluding-a-device"></a>Arrêter l’exclusion d’un appareil

Vous pourrez arrêter d’exclure un appareil à tout moment. Une fois que les appareils ne sont plus exclus, leurs données de vulnérabilité sont visibles dans gestion des vulnérabilités pages, rapports et dans le recherche avancée. L’application des modifications peut prendre jusqu’à 8 heures.

1. Go to the Device inventory, select the excluded device to open the flyout, and then select **Exclusion details**
2. Sélectionner **Arrêter l’exclusion**

![Image des détails d’exclusion](images/exclusion-details.png)

## <a name="see-also"></a>Voir aussi

- [Inventaire des appareils](machines-view-overview.md)
