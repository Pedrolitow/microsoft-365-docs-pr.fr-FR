---
title: Évaluer l’antivirus Microsoft Defender
description: Les entreprises de toutes tailles peuvent utiliser ce guide pour évaluer et tester la protection offerte Antivirus Microsoft Defender dans Windows.
keywords: Antivirus Microsoft Defender, protection cloud, cloud, logiciel anti-programme malveillant, sécurité, defender, évaluer, tester, protection, comparer, protection en temps réel
ms.prod: m365-security
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
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 4dd25a599f144a60bfd2ebeb3e9bb8b1876bd3c6
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62807415"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Évaluer l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Utilisez ce guide pour déterminer dans quelle mesure Antivirus Microsoft Defender vous protège contre les virus, les programmes malveillants et les applications potentiellement indésirables.

> [!TIP]
>Vous pouvez également consulter le site web de démonstration microsoft Defender pour points de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités suivantes fonctionnent et voir comment elles fonctionnent :
>
> - Protection fournie par le cloud
> - Apprentissage rapide (y compris Bloquer à la première vue)
> - Blocage d’applications potentiellement indésirables

> [!NOTE]
> Le site de démonstration Defender for Endpoint demo.wd.microsoft.com est supprimé et sera supprimé à l’avenir.

Il explique les fonctionnalités importantes de protection nouvelle génération de Antivirus Microsoft Defender disponibles pour les petites et grandes entreprises, et comment elles augmentent la détection et la protection contre les programmes malveillants sur votre réseau.

Vous pouvez choisir de configurer et d’évaluer chaque paramètre indépendamment, ou tous en même temps. Nous avons regroupé des paramètres similaires basés sur des scénarios d’évaluation classiques et incluons des instructions d’utilisation de PowerShell pour activer les paramètres.

Le guide est disponible au format PDF pour l’affichage hors connexion :

- [Télécharger le guide au format PDF](https://www.microsoft.com/download/details.aspx?id=54795)

Vous pouvez également télécharger un PowerShell qui active automatiquement tous les paramètres décrits dans le guide. Vous pouvez obtenir le script en même temps que le téléchargement PDF ci-dessus, ou individuellement à partir de la galerie PowerShell :

- [Télécharger le script PowerShell pour configurer automatiquement les paramètres](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Le guide est actuellement destiné à l’évaluation de la Antivirus Microsoft Defender. L’activation de tous les paramètres de ce guide peut ne pas convenir pour un déploiement réel.
>
> Pour obtenir les dernières recommandations pour le déploiement et la surveillance réels des Antivirus Microsoft Defender sur un réseau, voir [Deploy Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md).

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)