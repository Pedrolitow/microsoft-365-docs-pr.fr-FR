---
title: Configurer des exclusions pour Antivirus Microsoft Defender analyses
description: Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers d’être analysés par Antivirus Microsoft Defender. Validez vos exclusions avec PowerShell.
keywords: ''
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.openlocfilehash: 6f3c44ba70debfdf4ecebb089f2015214e92f4b2cef037da5bdf5f7ad0e99c40
ms.sourcegitcommit: 9410944dab4a34c38ee420e66b14c58ca037f31c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2021
ms.locfileid: "57803631"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Configurer et valider des exclusions pour Antivirus Microsoft Defender analyses

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez exclure certains fichiers, dossiers, processus et fichiers ouverts par le processus de Antivirus Microsoft Defender analyses. Ces exclusions s’appliquent [aux analyses programmées,](scheduled-catch-up-scans-microsoft-defender-antivirus.md)aux analyses à la demande [et](run-scan-microsoft-defender-antivirus.md)à la protection et à la surveillance en temps réel toujours en [temps réel.](configure-real-time-protection-microsoft-defender-antivirus.md) Les exclusions pour les fichiers ouverts par le processus s’appliquent uniquement à la protection en temps réel.

## <a name="configure-and-validate-exclusions"></a>Configurer et valider des exclusions

Pour configurer et valider des exclusions, consultez les procédures suivantes :

- [Configurez et validez les exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier.](configure-extension-file-exclusions-microsoft-defender-antivirus.md) Vous pouvez exclure des fichiers des Antivirus Microsoft Defender en fonction de leur extension de fichier, de leur nom de fichier ou de leur emplacement.

- [Configurez et validez les exclusions pour les fichiers ouverts par des processus.](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) Vous pouvez exclure des fichiers des analyses qui ont été ouvertes par un processus spécifique.

## <a name="recommendations-for-defining-exclusions"></a>Recommandations définition des exclusions

> [!IMPORTANT]
> Antivirus Microsoft Defender inclut de nombreuses exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d’entreprise, la gestion des bases de données et d’autres scénarios et situations d’entreprise.  
> 
> La définition d’exclusions réduit la protection offerte par Antivirus Microsoft Defender. Vous devez toujours évaluer les risques associés à l’implémentation d’exclusions, et vous devez exclure uniquement les fichiers dont vous êtes certain qu’ils ne sont pas malveillants.

Gardez les points suivants à l’esprit lorsque vous définissez des exclusions :  

- Les exclusions sont techniquement un écart de protection. Prenez en compte toutes vos options lors de la définition d’exclusions. D’autres options peuvent être aussi simples que de s’assurer que l’emplacement exclu dispose des listes de contrôle d’accès appropriées ou de définir des stratégies en mode audit au début.

- Examinez régulièrement les exclusions. Revérifiez et appliquez de nouveau les atténuations dans le cadre de votre processus de révision.

- Dans l’idéal, évitez de définir des exclusions afin d’être proactives. Par exemple, n’excluez pas quelque chose simplement parce que vous pensez qu’il pourrait s’agir d’un problème à l’avenir. Utilisez des exclusions uniquement pour des problèmes spécifiques, tels que ceux relatifs aux performances ou à la compatibilité des applications que les exclusions peuvent atténuer.

- Examiner et auditer les modifications apportées à votre liste d’exclusions. Votre équipe de sécurité doit conserver le contexte sur la raison pour laquelle une certaine exclusion a été ajoutée afin d’éviter toute confusion ultérieurement. Votre équipe de sécurité doit être en mesure de fournir des réponses spécifiques aux questions sur la raison de l’existence d’exclusions.

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender exclusions sur Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
