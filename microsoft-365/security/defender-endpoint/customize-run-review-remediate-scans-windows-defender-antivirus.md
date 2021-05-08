---
title: Exécuter et personnaliser des analyses programmées et à la demande
description: Personnalisez et lancez Antivirus Microsoft Defender analyses sur les points de terminaison sur votre réseau.
keywords: analyser, planifier, personnaliser, exclusions, exclure des fichiers, correction, résultats de l’analyse, mise en quarantaine, supprimer une menace, analyse rapide, analyse complète, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: f3e0cc7ffccf02e24b9746d539a44d3a72810ead
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2021
ms.locfileid: "52286184"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans--remediation"></a>Personnaliser, lancer et passer en revue les résultats de Antivirus Microsoft Defender analyses & correction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser la stratégie de groupe, PowerShell et Windows Management Instrumentation (WMI) pour configurer Antivirus Microsoft Defender analyses. 

## <a name="in-this-section"></a>Contenu de cette section

| Article | Description |
|:---|:---|
|[Configurer et valider des exclusions de fichiers, de dossiers et de fichiers ouverts par processus dans Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md) | Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers des analyses à la demande, des analyses programmées et de l’analyse et de l’analyse de la protection en temps réel toujours en temps réel |
|[Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Vous pouvez configurer Antivirus Microsoft Defender pour inclure certains types de fichiers de stockage de courrier électronique, des points de stockage ou d’analyse, ainsi que des fichiers archivés (tels que des fichiers .zip) dans les analyses. Vous pouvez également activer l’analyse des fichiers réseau |
|[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) | Configurer ce que Antivirus Microsoft Defender doit faire lorsqu’il détecte une menace et combien de temps les fichiers mis en quarantaine doivent être conservés dans le dossier de mise en quarantaine |
|[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Configurer des analyses périodiques (programmées), notamment quand elles doivent s’exécuter et s’ils s’exécutent en tant qu’analyses complètes ou rapides |
|[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md) | Exécuter et configurer des analyses à la demande à l’aide de PowerShell, Windows Management Instrumentation ou individuellement sur les points de terminaison avec l Sécurité Windows appl. |
|[Passer en revue les résultats de l’analyse](review-scan-results-microsoft-defender-antivirus.md) | Passer en revue les résultats des analyses à l’aide Microsoft Endpoint Configuration Manager, Microsoft Intune ou l’application Sécurité Windows de données |