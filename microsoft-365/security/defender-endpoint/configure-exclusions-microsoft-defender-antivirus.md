---
title: Configurer des exclusions pour les analyses antivirus Microsoft Defender
description: Vous pouvez exclure les fichiers (y compris les fichiers modifiés par les processus spécifiés) et les dossiers d’être analysés par Microsoft Defender Antivirus. Validez vos exclusions avec PowerShell.
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
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 94addada13ca9b22a0d2b5bef6377dae175e7299
ms.sourcegitcommit: 55672e44de74209f2e23b4bd9ca74a2ee7e88cd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2022
ms.locfileid: "68319031"
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

- [Configurez et validez les exclusions en fonction du nom de fichier, de l’extension et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Vous pouvez exclure des fichiers des analyses antivirus Microsoft Defender en fonction de leur extension de fichier, nom de fichier ou emplacement.

- [Configurez et validez les exclusions pour les fichiers ouverts par les processus](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Vous pouvez exclure les fichiers des analyses qui ont été ouvertes par un processus spécifique.

## <a name="recommendations-for-defining-exclusions"></a>Recommandations pour la définition des exclusions

> [!IMPORTANT]
> Microsoft Defender Antivirus inclut de nombreuses exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques, tels que ceux utilisés dans la gestion d’entreprise, la gestion des bases de données et d’autres scénarios et situations d’entreprise.
>
> La définition d’exclusions réduit la protection offerte par Microsoft Defender Antivirus. Vous devez toujours évaluer les risques associés à l’implémentation d’exclusions, et vous ne devez exclure que les fichiers dont vous êtes certain qu’ils ne sont pas malveillants.

Gardez à l’esprit les points suivants lorsque vous définissez des exclusions :

- Les exclusions sont techniquement un écart de protection. Tenez compte de toutes vos options lors de la définition d’exclusions. D’autres options peuvent être aussi simples que de s’assurer que l’emplacement exclu dispose des listes de contrôle d’accès appropriées (ACL) ou de définir des stratégies en mode audit dans un premier temps.

- Passez régulièrement en revue les exclusions. Revérifier et appliquer à nouveau les atténuations dans le cadre de votre processus d’examen.

- Dans l’idéal, évitez de définir des exclusions dans le but d’être proactif. Par exemple, n’excluez pas quelque chose simplement parce que vous pensez qu’il pourrait s’agir d’un problème à l’avenir. Utilisez des exclusions uniquement pour des problèmes spécifiques, tels que ceux liés aux performances ou à la compatibilité des applications que les exclusions peuvent atténuer.

- Passez en revue et auditez les modifications apportées à votre liste d’exclusions. Votre équipe de sécurité doit conserver le contexte autour de la raison pour laquelle une certaine exclusion a été ajoutée pour éviter toute confusion ultérieure. Votre équipe de sécurité doit être en mesure de fournir des réponses spécifiques aux questions sur la raison pour laquelle des exclusions existent.

## <a name="audit-antivirus-exclusions"></a>Auditer les exclusions antivirus

Exchange prend en charge l’intégration à l’interface d’analyse anti-programme malveillant (AMSI) depuis le Mises à jour trimestriel de juin 2021 pour Exchange. Il est fortement recommandé de s’assurer que ces mises à jour sont installées et AMSI utilise les conseils fournis par l’équipe Exchange, car cette intégration permettra à l’antivirus Defender de détecter et de bloquer l’exploitation d’Exchange.  

De nombreuses organisations excluent les répertoires Exchange des analyses antivirus pour des raisons de performances. Microsoft recommande d’auditer les exclusions av sur les systèmes Exchange et d’évaluer si elles peuvent être supprimées sans impacter les performances dans votre environnement pour garantir le niveau de protection le plus élevé. Les exclusions peuvent être gérées à l’aide d’stratégie de groupe, de PowerShell ou d’outils de gestion de systèmes tels que Microsoft Endpoint Configuration Manager.

Pour auditer les exclusions av sur un Exchange Server l’exécution de Defender Antivirus, **exécutez la commande Get-MpPreference** à partir d’une invite PowerShell avec élévation de privilèges.

Si les exclusions ne peuvent pas être supprimées pour les processus et dossiers Exchange, l’exécution d’une analyse rapide dans l’Antivirus Defender analyse les répertoires et fichiers Exchange, quelles que soient les exclusions.

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

- [exclusions antivirus Microsoft Defender sur Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Erreurs courantes à éviter lors de la définition d’exclusions](common-exclusion-mistakes-microsoft-defender-antivirus.md)
