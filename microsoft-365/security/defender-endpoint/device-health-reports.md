---
title: Rapports sur l’intégrité des appareils dans Microsoft Defender pour point de terminaison
description: Utilisez le rapport d’intégrité de l’appareil pour suivre l’intégrité de l’appareil, l’état et les versions de l’antivirus, les plateformes de système d’exploitation et les versions Windows 10.
keywords: état d’intégrité, antivirus, plateforme de système d’exploitation, version windows 10, version, intégrité, conformité, état
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
ms.date: 09/06/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
ms.reviewer: mkaminska
ms.openlocfilehash: b309a55f00957da8fdc3f9f5f283191fa7ac55c5
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68634253"
---
# <a name="device-health-reports-in-microsoft-defender-for-endpoint"></a>Rapports d’intégrité des appareils dans Microsoft Defender pour point de terminaison

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le rapport Intégrité des appareils fournit des informations sur les appareils de votre organisation. Le rapport inclut des informations de tendance indiquant l’état d’intégrité du capteur, l’état de l’antivirus, les plateformes de système d’exploitation, les versions Windows 10 et Microsoft Defender versions de mise à jour antivirus.

> [!IMPORTANT]
> Pour que Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 apparaissent dans les rapports d’intégrité des appareils, ces appareils doivent être intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).

Dans le panneau de navigation du tableau de bord Sécurité Microsoft 365, sélectionnez **Rapports**, puis ouvrez **Intégrité et conformité de l’appareil**.
Le tableau de bord Intégrité et conformité de l’appareil est structuré sous deux onglets :

- [L’onglet **Intégrité du capteur & système d’exploitation**](device-health-sensor-health-os.md#sensor-health--os-tab) fournit des informations générales sur le système d’exploitation, divisées en trois cartes qui affichent les attributs d’appareil suivants :
  - [Carte d’intégrité du capteur](device-health-sensor-health-os.md#sensor-health-card)
  - [Carte des systèmes d’exploitation et des plateformes](device-health-sensor-health-os.md#operating-systems-and-platforms-card)
  - [Carte des versions de Windows](device-health-sensor-health-os.md#windows-versions-card)

- [**L’onglet intégrité de Microsoft Defender Antivirus**](device-health-microsoft-defender-antivirus-health.md#microsoft-defender-antivirus-health-tab) comporte huit cartes qui signalent les aspects de Microsoft Defender Antivirus :
  - [Carte en mode Antivirus](device-health-microsoft-defender-antivirus-health.md#antivirus-mode-card)
  - [Carte de version du moteur antivirus](device-health-microsoft-defender-antivirus-health.md#antivirus-engine-version-card)
  - [Carte de version du renseignement de sécurité antivirus](device-health-microsoft-defender-antivirus-health.md#antivirus-security-intelligence-version-card)
  - [Carte de version de la plateforme antivirus](device-health-microsoft-defender-antivirus-health.md#antivirus-platform-version-card)
  - [Carte des résultats de l’analyse antivirus récente](device-health-microsoft-defender-antivirus-health.md#recent-antivirus-scan-results-card)
  - [Carte des mises à jour du moteur antivirus](device-health-microsoft-defender-antivirus-health.md#antivirus-engine-updates-card)
  - [Carte des mises à jour du renseignement de sécurité](device-health-microsoft-defender-antivirus-health.md#security-intelligence-updates-card)
  - [Carte des mises à jour de la plateforme antivirus](device-health-microsoft-defender-antivirus-health.md#antivirus-platform-updates-card)

## <a name="report-access-permissions"></a>Autorisations d’accès aux rapports

Pour accéder au rapport de conformité de l’intégrité des appareils et des antivirus dans le tableau de bord Sécurité Microsoft 365, les autorisations suivantes sont requises :

| Nom de l’autorisation | Type d’autorisation |
|:---|:---|
| Afficher les données | Gestion des menaces et des vulnérabilités (TVM) |

Pour attribuer ces autorisations :

1. Connectez-vous à Microsoft 365 Defender à l’aide <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">d’un</a> compte avec un rôle d’administrateur de sécurité ou de Administrateur général attribué.
1. Dans le volet de navigation, sélectionnez **Paramètres des rôles** \> **de points de terminaison** \> (sous **Autorisations**).
1. Sélectionnez le rôle que vous souhaitez modifier.
1. Sélectionnez **Modifier**.
1. Dans **Modifier le rôle**, sous l’onglet **Général** , dans **le nom** du rôle, tapez un nom pour le rôle.
1. Dans **Description** , tapez un bref résumé du rôle.
1. Dans **Autorisations**, sélectionnez **Afficher les données**, puis sous **Afficher les données** , sélectionnez **Gestion des menaces et des vulnérabilités** (TVM).

## <a name="see-also"></a>Voir aussi

- [Créez et gérez des rôles pour le contrôle d’accès en fonction du rôle](user-roles.md).
- [Exporter les méthodes et propriétés de l’API des détails d’intégrité de l’antivirus de l’appareil](device-health-api-methods-properties.md)
