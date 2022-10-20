---
title: Exécuter et personnaliser des analyses planifiées et à la demande
description: Personnaliser et lancer des analyses antivirus Microsoft Defender sur des points de terminaison sur votre réseau
keywords: analyse, planification, personnalisation, exclusions, exclure des fichiers, correction, résultats de l’analyse, quarantaine, suppression des menaces, analyse rapide, analyse complète, Microsoft Defender Antivirus
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.topic: conceptual
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 82cdf185f36bc337aa0c783d6d37a2fbb6e4036c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68635705"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Personnaliser, lancer et examiner les résultats des analyses et des corrections de Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vous pouvez utiliser stratégie de groupe, PowerShell et Windows Management Instrumentation (WMI) pour configurer Microsoft Defender analyses antivirus. 

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Configurer et valider les exclusions de fichiers, de dossiers et de fichiers ouverts par le processus dans les analyses antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md) | Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers des analyses à la demande, des analyses planifiées et de la surveillance et de l’analyse de la protection en temps réel always-on
[Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Vous pouvez configurer Microsoft Defender Antivirus pour inclure certains types de fichiers de stockage de messagerie, de points de sauvegarde ou d’analyse, ainsi que des fichiers archivés (tels que des fichiers .zip) dans les analyses. Vous pouvez également activer l’analyse des fichiers réseau
[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) | Configurer ce que Microsoft Defender Antivirus doit faire lorsqu’il détecte une menace et la durée pendant laquelle les fichiers mis en quarantaine doivent être conservés dans le dossier de quarantaine
[Configurer les analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Configurer des analyses périodiques (planifiées), notamment quand elles doivent s’exécuter et si elles s’exécutent en tant qu’analyses complètes ou rapides
[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md) | Exécuter et configurer des analyses à la demande à l’aide de PowerShell, de Windows Management Instrumentation ou individuellement sur des points de terminaison avec l’application Sécurité Windows
[Examiner les résultats de l’analyse](review-scan-results-microsoft-defender-antivirus.md) | Passez en revue les résultats des analyses à l’aide de Microsoft Endpoint Configuration Manager, Microsoft Intune ou l’application Sécurité Windows