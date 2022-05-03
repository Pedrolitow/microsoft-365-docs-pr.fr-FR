---
title: Comprendre les paramètres de configuration de la protection de nouvelle génération dans Microsoft Defender pour les PME
description: Comprendre les paramètres de protection antivirus et de nouvelle génération dans Defender entreprise, sécurité des points de terminaison pour les petites et moyennes entreprises.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 34cbd422cafe5c171f47e8e6470c4b12f9e1700d
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174473"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>Comprendre les paramètres de configuration de nouvelle génération dans Microsoft Defender pour les PME

La protection de nouvelle génération dans Defender entreprise inclut une protection antivirus et anti-programme malveillant robuste. Vos stratégies par défaut sont conçues pour protéger vos appareils et vos utilisateurs sans entraver la productivité; toutefois, vous pouvez également personnaliser vos stratégies en fonction des besoins de votre entreprise. De plus, si vous utilisez Microsoft Intune, vous pouvez utiliser le centre d’administration Microsoft Endpoint Manager pour gérer vos stratégies de sécurité.

**Cet article décrit**:

- [Paramètres et options de protection de nouvelle génération](#next-generation-protection-settings-and-options)
- [Autres paramètres préconfigurés dans Defender entreprise](#other-preconfigured-settings-in-defender-for-business) 
- [Paramètres et Microsoft Intune par défaut de Defender entreprise](#defender-for-business-default-settings-and-microsoft-intune)

## <a name="next-generation-protection-settings-and-options"></a>Paramètres et options de protection de nouvelle génération

Le tableau suivant répertorie vos paramètres et options :

| Paramètre | Description |
|:---|:---|
| **Protection en temps réel**  |  |
| **Activer la protection en temps réel** | Activée par défaut, la protection en temps réel localise et empêche les programmes malveillants de s’exécuter sur les appareils. *Nous vous recommandons de maintenir la protection en temps réel activée.*<br/><br/>Lorsque la protection en temps réel est activée, elle configure les paramètres suivants :<br/>- La surveillance du comportement est activée ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- Tous les fichiers et pièces jointes téléchargés sont analysés ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- Les scripts utilisés dans les navigateurs Microsoft sont analysés ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **Bloquer à la première consultation** | Activé par défaut, bloquer à la première consultation bloque les programmes malveillants dans les secondes qui suivent la détection, augmente le temps (en secondes) autorisé à envoyer des exemples de fichiers à des fins d’analyse et définit votre niveau de détection sur Élevé. *Nous vous recommandons de maintenir le blocage à la première consultation activé.*<br/><br/>Lorsque le blocage à la première consultation est activé, il configure les paramètres suivants pour Antivirus Microsoft Defender : <br/>- Le blocage et l’analyse des fichiers suspects sont définis sur le niveau de blocage élevé ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>- Le nombre de secondes pendant lesquelles un fichier doit être bloqué et archivé est défini sur 50 secondes ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**IMPORTANT** : Si le bloc à la première consultation est désactivé, il affecte `CloudBlockLevel` et `CloudExtendedTimeout` pour Antivirus Microsoft Defender.  |
| **Activer la protection du réseau** | Lorsqu’elle est activée, la protection réseau permet de se protéger contre les escroqueries par hameçonnage, les sites d’exploitation et le contenu malveillant sur Internet. Il empêche également les utilisateurs de désactiver la protection réseau.<br/><br/>La protection réseau peut être définie sur l’un des modes suivants :<br/>- **Mode de blocage** (ce paramètre est la valeur par défaut), ce qui empêche les utilisateurs de visiter des sites considérés comme non sécurisés. *Nous vous recommandons de conserver la protection réseau définie sur le mode Bloquer.*<br/>- **Mode Audit**, qui permet aux utilisateurs de visiter des sites potentiellement dangereux et de suivre l’activité réseau vers/depuis ces sites <br/>- **Mode désactivé**, qui empêche les utilisateurs de visiter des sites potentiellement dangereux ni de suivre l’activité réseau vers/à partir de ces sites |
| **Assainissement**  |  |
| **Action à prendre sur les applications potentiellement indésirables (PUA)** | PUA peut inclure des logiciels publicitaires, des logiciels de regroupement qui offrent d’installer d’autres logiciels non signés et des logiciels d’évasion qui tentent d’échapper aux fonctionnalités de sécurité. Bien que puA n’est pas nécessairement un virus, des programmes malveillants ou d’autres types de menaces, PUA peut affecter les performances de l’appareil.<br/><br/>La protection PUA bloque les éléments détectés comme PUA. Vous pouvez définir la protection PUA sur l’un des paramètres suivants : <br/>- **Activé** (ce paramètre est la valeur par défaut), qui bloque les éléments détectés comme PUA sur les appareils. *Nous vous recommandons de maintenir la protection PUA activée.*<br/>- **Mode Audit**, qui n’effectue aucune action sur les éléments détectés comme PUA <br/>- **Désactivé**, qui ne détecte pas ou ne prend pas d’action sur les éléments qui peuvent être PUA |
| **Analyser**   |  |
| **Type d’analyse planifiée** | Envisagez d’exécuter une analyse antivirus hebdomadaire sur vos appareils. Vous pouvez choisir parmi les options de type d’analyse suivantes : <br/>- **Quickscan** vérifie les emplacements, tels que les clés de Registre et les dossiers de démarrage, où les programmes malveillants peuvent être inscrits pour démarrer avec un appareil. *Nous vous recommandons d’utiliser l’option quickscan.* <br/>- **Fullscan** vérifie tous les fichiers et dossiers sur un appareil <br/>- **Désactivé** signifie qu’aucune analyse planifiée n’aura lieu. Les utilisateurs peuvent toujours exécuter des analyses sur leurs propres appareils. (En général, nous vous déconseillons de désactiver vos analyses planifiées.) <br/><br/> [En savoir plus sur les types d’analyse](../defender-endpoint/schedule-antivirus-scans.md). |
| **Jour de la semaine pour exécuter une analyse planifiée** | Sélectionnez un jour pour que vos analyses antivirus hebdomadaires régulières s’exécutent. |
| **Heure de la journée d’exécution d’une analyse planifiée** | Sélectionnez une heure pour exécuter vos analyses antivirus planifiées régulièrement à exécuter. |
| **Utiliser des performances faibles** | Ce paramètre est désactivé par défaut. *Nous vous recommandons de désactiver ce paramètre.* Toutefois, vous pouvez activer ce paramètre pour limiter la mémoire et les ressources de l’appareil utilisées lors des analyses planifiées. <br/><br/>**IMPORTANT** Si vous **activez Utiliser des performances faibles**, les paramètres suivants sont configurés pour Antivirus Microsoft Defender : <br/>- Les fichiers d’archive ne sont pas analysés ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>- Une faible priorité du processeur est affectée aux analyses ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Si une analyse antivirus complète est manquée, aucune analyse de rattrapage ne s’exécutera ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Si une analyse antivirus rapide est manquée, aucune analyse de rattrapage ne s’exécutera ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- Réduit le facteur de charge du processeur moyen pendant une analyse antivirus de 50 % à 20 % ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Expérience utilisateur**   |  |
| **Autoriser les utilisateurs à accéder à l’application Sécurité Windows** | Activez ce paramètre pour permettre aux utilisateurs d’ouvrir l’application Sécurité Windows sur leurs appareils. Les utilisateurs ne pourront pas remplacer les paramètres que vous configurez dans Microsoft Defender pour les PME, mais ils pourront exécuter une analyse rapide si nécessaire ou afficher les menaces détectées. |
| **Exclusions antivirus** | Les exclusions sont des processus, des fichiers ou des dossiers ignorés par Antivirus Microsoft Defender analyses. *En général, vous ne devez pas avoir besoin de définir des exclusions.* Antivirus Microsoft Defender inclut de nombreuses exclusions automatiques basées sur des comportements connus du système d’exploitation et des fichiers de gestion classiques.<br/><br/>[En savoir plus sur les exclusions](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **Exclusions de processus** | Les exclusions de processus empêchent les fichiers ouverts par des processus spécifiques d’être analysés par Antivirus Microsoft Defender. <br/><br/>[En savoir plus sur les exclusions de processus](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Exclusions d’extensions de fichier** | Les exclusions d’extension de fichier empêchent les fichiers avec des extensions spécifiques d’être analysés par Antivirus Microsoft Defender.<br/><br/>[En savoir plus sur les exclusions d’extension de fichier](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Exclusions de fichiers et de dossiers** | Les exclusions de fichiers et de dossiers empêchent les fichiers qui se trouvent dans des dossiers spécifiques d’être analysés par Antivirus Microsoft Defender. <br/><br/>[En savoir plus sur les exclusions de fichiers et de dossiers](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Autres paramètres préconfigurés dans Defender entreprise

Les paramètres de sécurité suivants sont préconfigurés dans Defender entreprise :

- L’analyse des lecteurs amovibles est activée ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))
- Les analyses rapides quotidiennes n’ont pas d’heure prédéfinies ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))
- Les mises à jour du renseignement de sécurité sont vérifiées avant l’exécution d’une analyse antivirus ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))
- Les vérifications de sécurité se produisent toutes les quatre heures ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-intune"></a>Paramètres et Microsoft Intune par défaut de Defender entreprise

Le tableau suivant décrit les paramètres préconfigurés pour Defender entreprise et comment ces paramètres correspondent à ce que vous pouvez voir dans Intune (géré dans le centre d’administration Microsoft Endpoint Manager). Si vous utilisez le [processus de configuration simplifié dans Defender entreprise](mdb-simplified-configuration.md), vous n’avez pas besoin de modifier ces paramètres.

| Paramètre  | Description  |
|---------|---------|
| [Protection cloud](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Parfois appelée protection fournie par le cloud ou Microsoft Advanced Protection Service (MAPS), la protection cloud fonctionne avec Antivirus Microsoft Defender et le cloud Microsoft pour identifier les nouvelles menaces, parfois même avant qu’un seul appareil ne soit affecté. Par défaut, [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) est activé. <br/><br/>[En savoir plus sur la protection cloud](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [Surveillance des fichiers entrants et sortants](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | Pour surveiller les fichiers entrants et sortants, [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) est défini pour surveiller tous les fichiers.         |
| [Analyser les fichiers réseau](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Par défaut, [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) n’est pas activé et les fichiers réseau ne sont pas analysés. |
| [Analyser les messages électroniques](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Par défaut, [AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) n’est pas activé et les e-mails ne sont pas analysés. |
| [Nombre de jours (0 à 90) pour conserver les programmes malveillants mis en quarantaine](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Par défaut, [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) , ce paramètre est défini sur zéro (0) jours. Artifacts que les mises en quarantaine ne sont pas supprimées automatiquement.  |
| [Envoyer le consentement d’exemples](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | Par défaut, [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) est défini pour envoyer automatiquement des échantillons sécurisés. Les exemples d’exemples fiables incluent `.bat`, `.scr``.dll`et `.exe` les fichiers qui ne contiennent pas d’informations d’identification personnelle (PII). Si un fichier contient des informations personnelles, l’utilisateur reçoit une demande d’autorisation de la soumission de l’exemple.<br/><br/>[En savoir plus sur la protection cloud et l’envoi d’exemples](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Analyser les lecteurs amovibles](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | Par défaut, [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) est configuré pour analyser les lecteurs amovibles, tels que les lecteurs usb sur les appareils.<br/><br/>[En savoir plus sur les paramètres de stratégie anti-programme malveillant](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Exécuter le temps d’analyse rapide quotidien](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Par défaut, [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) est défini sur 2h00.<br/><br/>[En savoir plus sur les paramètres d’analyse](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [Rechercher les mises à jour des signatures avant d’exécuter l’analyse](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Par défaut, [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) est configuré pour rechercher les mises à jour du renseignement de sécurité avant d’exécuter des analyses antivirus/anti-programme malveillant.<br/><br/>[En savoir plus sur les paramètres d’analyse et les](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [mises à jour du renseignement de sécurité](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [Fréquence (0 à 24 heures) pour rechercher les mises à jour du renseignement de sécurité](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | Par défaut, [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) est configuré pour rechercher les mises à jour du renseignement de sécurité toutes les quatre heures.<br/><br/>[En savoir plus sur les paramètres d’analyse et les](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [mises à jour du renseignement de sécurité](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Voir aussi

- [Visitez le portail Microsoft 365 Defender](mdb-get-started.md)
- [Gérer les paramètres de pare-feu dans Microsoft Defender pour les PME](mdb-custom-rules-firewall.md)
- [Fournisseur CSP de stratégie - Defender](/windows/client-management/mdm/policy-csp-defender)
