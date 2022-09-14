---
title: Évaluer l’antivirus Microsoft Defender
description: Les entreprises de toutes tailles peuvent utiliser ce guide pour évaluer et tester la protection offerte par l’antivirus Microsoft Defender dans Windows.
keywords: Antivirus Microsoft Defender, protection cloud, cloud, logiciel anti-programme malveillant, sécurité, defender, évaluer, tester, protection, comparer, protection en temps réel
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection: m365-security-compliance
search.appverid: met150
ms.openlocfilehash: 0e4c156f5091a21532c64b344329fc9219670643
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67695558"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Évaluer l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

**Plateformes**
- Windows

Utilisez ce guide pour déterminer la façon dont l’Antivirus Microsoft Defender vous protège contre les virus, les programmes malveillants et les applications potentiellement indésirables. Il explique les fonctionnalités de protection de nouvelle génération importantes de l’antivirus Microsoft Defender disponibles pour les petites et grandes entreprises, ainsi que la façon dont elles augmentent la détection et la protection des programmes malveillants sur votre réseau.

Vous pouvez choisir de configurer et d’évaluer chaque paramètre indépendamment, ou tout à la fois. Nous avons regroupé des paramètres similaires basés sur des scénarios d’évaluation classiques et incluons des instructions pour utiliser PowerShell pour activer les paramètres.

Le guide est disponible au format PDF pour l’affichage hors connexion :

- [Télécharger le guide au format PDF](https://www.microsoft.com/download/details.aspx?id=54795)

Vous pouvez également télécharger un PowerShell qui active automatiquement tous les paramètres décrits dans le guide. Vous pouvez obtenir le script en même temps que le téléchargement PDF ci-dessus, ou individuellement à partir de PowerShell Gallery :

- [Télécharger le script PowerShell pour configurer automatiquement les paramètres](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Le guide est actuellement destiné à l’évaluation sur une seule machine de l’antivirus Microsoft Defender. L’activation de tous les paramètres de ce guide peut ne pas convenir au déploiement réel.
>
> Pour obtenir les dernières recommandations en matière de déploiement et de surveillance réels de l’antivirus Microsoft Defender sur un réseau, consultez [Déployer l’antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer l’antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)