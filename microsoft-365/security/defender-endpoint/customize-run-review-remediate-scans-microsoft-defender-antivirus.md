---
title: Exécutez et personnalisez des analyses programmées et à la demande.
description: Personnaliser et lancer Antivirus Microsoft Defender analyses sur les points de terminaison sur votre réseau
keywords: analyser, planifier, personnaliser, exclusions, exclure des fichiers, correction, résultats de l’analyse, mise en quarantaine, supprimer une menace, analyse rapide, analyse complète, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 85e09ab22ffe440861656ee2ce4e2635639b251c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60184856"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser la stratégie de groupe, PowerShell et Windows Management Instrumentation (WMI) pour configurer Antivirus Microsoft Defender analyses. 

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Configurer et valider des exclusions de fichiers, de dossiers et de fichiers ouverts par processus dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md) | Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers des analyses à la demande, des analyses programmées et de l’analyse et de l’analyse de la protection en temps réel toujours en temps réel
[Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Vous pouvez configurer des Antivirus Microsoft Defender pour inclure certains types de fichiers de stockage de courrier électronique, des points de stockage ou d’analyse, ainsi que des fichiers archivés (tels que des fichiers .zip) dans les analyses. Vous pouvez également activer l’analyse des fichiers réseau
[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) | Configurer ce que Antivirus Microsoft Defender doit faire lorsqu’il détecte une menace et combien de temps les fichiers mis en quarantaine doivent être conservés dans le dossier de mise en quarantaine
[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Configurer des analyses périodiques (programmées), notamment quand elles doivent s’exécuter et s’ils s’exécutent en tant qu’analyses complètes ou rapides
[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md) | Exécuter et configurer des analyses à la demande à l’aide de PowerShell, Windows Management Instrumentation ou individuellement sur les points de terminaison avec l Sécurité Windows app.
[Passer en revue les résultats de l’analyse](review-scan-results-microsoft-defender-antivirus.md) | Passer en revue les résultats des analyses à l’aide Microsoft Endpoint Configuration Manager, Microsoft Intune ou l’Sécurité Windows de données