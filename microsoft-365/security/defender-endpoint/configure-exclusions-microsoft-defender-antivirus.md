---
title: Configurer des exclusions pour les analyses antivirus Microsoft Defender
description: Vous pouvez exclure les fichiers (y compris les fichiers modifiés par des processus spécifiés) et les dossiers d’être analysés par l’Antivirus Microsoft Defender. Validez vos exclusions avec PowerShell.
keywords: ''
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.subservice: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 354cb5e08845d275cf6517ec8badf4fb2c3635f8
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481523"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Configurer et valider les exclusions pour les analyses antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez exclure certains fichiers, dossiers, processus et fichiers ouverts par processus des analyses antivirus Microsoft Defender. Ces exclusions s’appliquent aux [analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md), aux [analyses à la demande](run-scan-microsoft-defender-antivirus.md) et à [la protection et à la surveillance en temps réel en permanence](configure-real-time-protection-microsoft-defender-antivirus.md). Les exclusions pour les fichiers ouverts par le processus s’appliquent uniquement à la protection en temps réel.

## <a name="configure-and-validate-exclusions"></a>Configurer et valider des exclusions

Pour configurer et valider les exclusions, consultez les rubriques suivantes :

- [Configurez et validez les exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Vous pouvez exclure des fichiers des analyses de l’Antivirus Microsoft Defender en fonction de leur extension de fichier, nom de fichier ou emplacement.

- [Configurez et validez les exclusions pour les fichiers ouverts par les processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Vous pouvez exclure les fichiers des analyses qui ont été ouvertes par un processus spécifique.

## <a name="recommendations-for-defining-exclusions"></a>Recommandations pour la définition des exclusions

> [!IMPORTANT]
> L’Antivirus Microsoft Defender inclut de nombreuses exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d’entreprise, la gestion des bases de données et d’autres scénarios et situations d’entreprise.
>
> La définition d’exclusions réduit la protection offerte par l’antivirus Microsoft Defender. Vous devez toujours évaluer les risques associés à l’implémentation d’exclusions, et vous ne devez exclure que les fichiers dont vous êtes certain qu’ils ne sont pas malveillants.

Gardez à l’esprit les points suivants lorsque vous définissez des exclusions :

- Les exclusions sont techniquement un écart de protection. Tenez compte de toutes vos options lors de la définition d’exclusions. D’autres options peuvent être aussi simples que de s’assurer que l’emplacement exclu dispose des listes de contrôle d’accès appropriées (ACL) ou de définir des stratégies en mode audit dans un premier temps.

- Passez régulièrement en revue les exclusions. Revérifier et appliquer à nouveau les atténuations dans le cadre de votre processus d’examen.

- Dans l’idéal, évitez de définir des exclusions dans le but d’être proactif. Par exemple, n’excluez pas quelque chose simplement parce que vous pensez qu’il pourrait s’agir d’un problème à l’avenir. Utilisez des exclusions uniquement pour des problèmes spécifiques, tels que ceux liés aux performances ou à la compatibilité des applications que les exclusions peuvent atténuer.

- Passez en revue et auditez les modifications apportées à votre liste d’exclusions. Votre équipe de sécurité doit conserver le contexte autour de la raison pour laquelle une certaine exclusion a été ajoutée pour éviter toute confusion ultérieure. Votre équipe de sécurité doit être en mesure de fournir des réponses spécifiques aux questions sur la raison pour laquelle des exclusions existent.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Exclusions de l’Antivirus Microsoft Defender sur Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
