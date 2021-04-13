---
title: Exécuter et personnaliser des analyses programmées et à la demande
description: Personnalisez et lancez des analyses de l'Antivirus Microsoft Defender sur les points de terminaison sur votre réseau.
keywords: analyser, planifier, personnaliser, exclusions, exclure des fichiers, correction, résultats de l'analyse, mise en quarantaine, supprimer une menace, analyse rapide, analyse complète, Antivirus Microsoft Defender
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
ms.openlocfilehash: 8aa735cf7490a451a5758c3799bd08dff61f8063
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690285"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez utiliser la stratégie de groupe, PowerShell et Windows Management Instrumentation (WMI) pour configurer les analyses de l'Antivirus Microsoft Defender. 

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Configurer et valider des exclusions de fichiers, de dossiers et de fichiers ouverts par processus dans les analyses de l'Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md) | Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers des analyses à la demande, des analyses programmées et de l'analyse et de l'analyse de la protection en temps réel toujours en temps réel
[Configurer les options d'analyse de l'Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Vous pouvez configurer l'Antivirus Microsoft Defender pour inclure certains types de fichiers de stockage de courrier électronique, les points de stockage ou d'analyse, ainsi que les fichiers archivés (tels que les fichiers .zip) dans les analyses. Vous pouvez également activer l'analyse des fichiers réseau
[Configurer la correction pour les analyses](configure-remediation-microsoft-defender-antivirus.md) | Configurer ce que l'Antivirus Microsoft Defender doit faire lorsqu'il détecte une menace et la durée de rétention des fichiers mis en quarantaine dans le dossier de mise en quarantaine
[Configurer des analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Configurer des analyses périodiques (programmées), notamment quand elles doivent s'exécuter et s'ils s'exécutent en tant qu'analyses complètes ou rapides
[Configurer et exécuter des analyses](run-scan-microsoft-defender-antivirus.md) | Exécuter et configurer des analyses à la demande à l'aide de PowerShell, Windows Management Instrumentation ou individuellement sur les points de terminaison avec l'application Sécurité Windows
[Passer en revue les résultats de l'analyse](review-scan-results-microsoft-defender-antivirus.md) | Passer en revue les résultats des analyses à l'aide de Microsoft Endpoint Configuration Manager, Microsoft Intune ou l'application sécurité Windows