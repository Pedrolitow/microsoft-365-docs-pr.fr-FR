---
title: Configurer des exclusions pour Antivirus Microsoft Defender analyses
description: Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers d’être analysés par Antivirus Microsoft Defender. Validez vos exclusions avec PowerShell.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 6ef9cfcec1c54cf9754d7152c098d7ef5b67b456
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330550"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Configurer et valider des exclusions pour Antivirus Microsoft Defender analyses

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Vous pouvez exclure certains fichiers, dossiers, processus et fichiers ouverts par processus de Antivirus Microsoft Defender analyses. Ces exclusions s’appliquent [aux analyses programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)[, aux](run-scan-microsoft-defender-antivirus.md) analyses à la demande et à la protection et à la [surveillance en temps réel toujours en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md). Les exclusions pour les fichiers ouverts par le processus s’appliquent uniquement à la protection en temps réel.

## <a name="configure-and-validate-exclusions"></a>Configurer et valider des exclusions

Pour configurer et valider des exclusions, consultez les procédures suivantes :

- [Configurez et validez les exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Vous pouvez exclure des fichiers des Antivirus Microsoft Defender en fonction de leur extension de fichier, de leur nom de fichier ou de leur emplacement.

- [Configurez et validez les exclusions pour les fichiers ouverts par des processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Vous pouvez exclure des fichiers des analyses qui ont été ouvertes par un processus spécifique.

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
