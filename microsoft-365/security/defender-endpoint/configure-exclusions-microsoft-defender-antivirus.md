---
title: Configurer des exclusions pour les analyses de l'Antivirus Microsoft Defender
description: Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers d'être analysés par Microsoft Defender AV. Validez vos exclusions avec PowerShell.
keywords: ''
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 47db9b4451a885c92ca4fda0f87f0150415d3338
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690729"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Configurer et valider des exclusions pour les analyses de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez exclure certains fichiers, dossiers, processus et fichiers ouverts par le processus des analyses de l'Antivirus Microsoft Defender. Ces exclusions s'appliquent aux analyses [programmées,](scheduled-catch-up-scans-microsoft-defender-antivirus.md)aux analyses à la demande [et](run-scan-microsoft-defender-antivirus.md)à la protection et à la surveillance en temps réel toujours en [temps réel.](configure-real-time-protection-microsoft-defender-antivirus.md) Les exclusions pour les fichiers ouverts par le processus s'appliquent uniquement à la protection en temps réel.

## <a name="configure-and-validate-exclusions"></a>Configurer et valider des exclusions

Pour configurer et valider des exclusions, consultez les procédures suivantes :

- [Configurez et validez les exclusions en fonction du nom de fichier, de l'extension et de l'emplacement du dossier.](configure-extension-file-exclusions-microsoft-defender-antivirus.md) Cela vous permet d'exclure des fichiers des analyses de l'Antivirus Microsoft Defender en fonction de leur extension de fichier, nom de fichier ou emplacement.

- [Configurez et validez les exclusions pour les fichiers ouverts par des processus.](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) Cela vous permet d'exclure des fichiers des analyses qui ont été ouvertes par un processus spécifique.

## <a name="recommendations-for-defining-exclusions"></a>Recommandations pour définir des exclusions

La définition d'exclusions réduit la protection offerte par l'Antivirus Microsoft Defender. Vous devez toujours évaluer les risques associés à l'implémentation d'exclusions, et vous devez exclure uniquement les fichiers dont vous êtes certain qu'ils ne sont pas malveillants.

Voici une liste de recommandations que vous devez garder à l'esprit lors de la définition d'exclusions :  

- Les exclusions sont techniquement un écart de protection ; envisagez toujours d'autres atténuations lors de la définition d'exclusions. Des atténuations supplémentaires peuvent être aussi simples que de s'assurer que l'emplacement exclu dispose des listes de contrôle d'accès (ACA) appropriées, de la stratégie d'audit, est traitée par un logiciel à jour, etc.

- Examinez régulièrement les exclusions. Ré-vérifiez et appliquez de ré-appliquer les atténuations dans le cadre du processus de révision.

- Dans l'idéal, évitez de définir des exclusions proactives. Par exemple, n'excluez pas quelque chose simplement parce que vous pensez qu'il pourrait s'agir d'un problème à l'avenir. Utilisez des exclusions uniquement pour des problèmes spécifiques, principalement autour des performances, ou parfois autour de la compatibilité des applications que les exclusions peuvent atténuer.

- Auditez les modifications apportées à la liste d'exclusions. L'administrateur de sécurité doit conserver suffisamment de contexte sur la raison pour laquelle une certaine exclusion a été ajoutée. Vous devriez être en mesure de fournir une réponse avec un raisonnement spécifique quant à la raison pour laquelle un certain chemin d'accès a été exclu.

## <a name="related-articles"></a>Articles connexes

- [Exclusions de l'Antivirus Microsoft Defender sur Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d'exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)