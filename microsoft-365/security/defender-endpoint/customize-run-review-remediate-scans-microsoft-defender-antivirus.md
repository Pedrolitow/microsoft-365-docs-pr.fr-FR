---
title: Exécutez et personnalisez les analyses planifiées et à la demande.
description: Personnaliser et lancer des analyses antivirus Microsoft Defender sur des points de terminaison sur votre réseau
keywords: analyse, planification, personnalisation, exclusions, exclure des fichiers, correction, résultats de l’analyse, quarantaine, suppression des menaces, analyse rapide, analyse complète, Antivirus Microsoft Defender
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
ms.topic: article
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 8b0e34ece48091b3abfd6cedb6dba12b791e3625
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67694867"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l’Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vous pouvez utiliser stratégie de groupe, PowerShell et Windows Management Instrumentation (WMI) pour configurer les analyses antivirus Microsoft Defender. 

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Configurer et valider les exclusions de fichiers, de dossiers et de fichiers ouverts par le processus dans les analyses antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md) | Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers des analyses à la demande, des analyses planifiées et de la surveillance et de l’analyse de la protection en temps réel always-on
[Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Vous pouvez configurer l’Antivirus Microsoft Defender pour inclure certains types de fichiers de stockage de messagerie, de points de sauvegarde ou d’analyse, ainsi que des fichiers archivés (tels que des fichiers .zip) dans les analyses. Vous pouvez également activer l’analyse des fichiers réseau
[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) | Configurer ce que l’Antivirus Microsoft Defender doit faire lorsqu’il détecte une menace et la durée pendant laquelle les fichiers mis en quarantaine doivent être conservés dans le dossier de quarantaine
[Configurer les analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Configurer des analyses périodiques (planifiées), notamment quand elles doivent s’exécuter et si elles s’exécutent en tant qu’analyses complètes ou rapides
[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md) | Exécuter et configurer des analyses à la demande à l’aide de PowerShell, de Windows Management Instrumentation ou individuellement sur des points de terminaison avec l’application Sécurité Windows
[Examiner les résultats de l’analyse](review-scan-results-microsoft-defender-antivirus.md) | Passez en revue les résultats des analyses à l’aide de Microsoft Endpoint Configuration Manager, Microsoft Intune ou l’application Sécurité Windows