---
title: Évaluer l’antivirus Microsoft Defender
description: Les entreprises de toutes tailles peuvent utiliser ce guide pour évaluer et tester la protection offerte Antivirus Microsoft Defender dans Windows 10.
keywords: Antivirus Microsoft Defender, protection cloud, cloud, logiciel anti-programme malveillant, sécurité, defender, évaluer, tester, protection, comparer, protection en temps réel
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: f0e7d008d7a51666a4d9a27c187b74b609f38577
ms.sourcegitcommit: 6968594dc8cf8b30a4c958df6d65dfd0cd2cfae1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59491468"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Évaluer l’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Utilisez ce guide pour déterminer dans quelle mesure Antivirus Microsoft Defender vous protège contre les virus, les programmes malveillants et les applications potentiellement indésirables.

> [!TIP]
>Vous pouvez également consulter le site web de démonstration microsoft Defender pour points de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités suivantes fonctionnent et voir comment elles fonctionnent :
>
> - Protection fournie par le cloud
> - Apprentissage rapide (y compris Bloquer à la première vue)
> - Blocage d’applications potentiellement indésirables

Il explique les fonctionnalités importantes de protection nouvelle génération de Antivirus Microsoft Defender disponibles pour les petites et grandes entreprises, et comment elles augmentent la détection et la protection contre les programmes malveillants sur votre réseau.

Vous pouvez choisir de configurer et d’évaluer chaque paramètre indépendamment, ou tous en même temps. Nous avons regroupé des paramètres similaires basés sur des scénarios d’évaluation classiques et incluons des instructions d’utilisation de PowerShell pour activer les paramètres.

Le guide est disponible au format PDF pour l’affichage hors connexion :

- [Télécharger le guide au format PDF](https://www.microsoft.com/download/details.aspx?id=54795)

Vous pouvez également télécharger un PowerShell qui active automatiquement tous les paramètres décrits dans le guide. Vous pouvez obtenir le script en même temps que le téléchargement PDF ci-dessus, ou individuellement à partir de la galerie PowerShell :

- [Télécharger le script PowerShell pour configurer automatiquement les paramètres](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Le guide est actuellement destiné à l’évaluation de la Antivirus Microsoft Defender. L’activation de tous les paramètres de ce guide peut ne pas convenir pour un déploiement réel.
>
> Pour obtenir les dernières recommandations pour le déploiement et la surveillance réels des Antivirus Microsoft Defender sur un réseau, voir [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md).

## <a name="related-topics"></a>Sujets associés

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)