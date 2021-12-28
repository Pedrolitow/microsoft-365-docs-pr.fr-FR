---
title: Comprendre les paramètres de configuration de la protection nouvelle génération dans Microsoft Defender pour Entreprises (prévisualisation)
description: Comprendre les paramètres de configuration pour la protection nouvelle génération dans Microsoft Defender entreprise (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/27/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 287097aac61817347b6d4a56eadda8dd7a5a2c46
ms.sourcegitcommit: b51e58f42a68b42f3e0b43564415dc5c1e9effb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/28/2021
ms.locfileid: "61614289"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business-preview"></a>Comprendre les paramètres de configuration nouvelle génération dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

La protection nouvelle génération dans Defender for Business (prévisualisation) inclut une protection antivirus et anti-programme malveillant robuste. Vos stratégies par défaut sont conçues pour protéger vos appareils et vos utilisateurs sans entraver la productivité . Toutefois, vous pouvez également personnaliser vos stratégies en fonction des besoins de votre entreprise. Et, si vous utilisez Microsoft Endpoint Manager, vous pouvez l’utiliser pour gérer vos stratégies et paramètres de sécurité.

**Cet article décrit**:

- [Options et paramètres de protection nouvelle génération](#next-generation-protection-settings-and-options)
- [Autres paramètres préconfigurés dans Defender for Business (aperçu)](#other-preconfigured-settings-in-defender-for-business) 
- [Paramètres et paramètres par défaut de Defender for Business Microsoft Endpoint Manager](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>Options et paramètres de protection nouvelle génération

Le tableau suivant répertorie vos paramètres et options :<br/><br/>

| Setting | Description |
|:---|:---|
| **Protection en temps réel**  |  |
| **Activer la protection en temps réel** | Activée par défaut, la protection en temps réel localise et arrête l’exécution des programmes malveillants sur les appareils. *Nous vous recommandons de maintenir la protection en temps réel allumée.*<br/><br/>Lorsque la protection en temps réel est désactivée, elle configure les paramètres suivants :<br/>- La surveillance du comportement est désactivée ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- Tous les fichiers et pièces jointes téléchargés sont analysés ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- Les scripts utilisés dans les navigateurs Microsoft sont analysés ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **Bloquer à la première consultation** | Activé par défaut, bloquer à la première vue bloque les programmes malveillants dans les secondes suivant la détection, augmente le temps (en secondes) à envoyer des exemples de fichiers pour analyse et définit votre niveau de détection sur Élevé. *Nous vous recommandons de garder bloquer à la première vue.*<br/><br/>Lorsque la fonction Bloquer à la première vue est désactivée, elle configure les paramètres suivants pour Antivirus Microsoft Defender : <br/>- Le blocage et l’analyse des fichiers suspects sont définies sur le niveau de blocage élevé ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>- Le nombre de secondes de blocage et de vérification d’un fichier est de 50 secondes ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**IMPORTANT**: si bloquer à la première vue est désactivé, cela affecte `CloudBlockLevel` et `CloudExtendedTimeout` Antivirus Microsoft Defender.  |
| **Activer la protection du réseau** | Lorsqu’elle est désactivée, la protection du réseau permet de se protéger contre les tentatives d’hameçonnage, les sites d’hébergement d’attaques et le contenu malveillant sur Internet. Cela empêche également les utilisateurs de éteindre la protection réseau.<br/><br/>La protection réseau peut être définie sur l’un des modes suivants :<br/>- **Mode blocage** (paramètre par défaut), qui empêche les utilisateurs de visiter des sites considérés comme non sécurisés. *Nous vous recommandons de conserver la protection réseau définie sur le mode Blocage.*<br/>- **Mode audit,** qui permet aux utilisateurs de visiter des sites potentiellement dangereux et de suivre l’activité réseau vers/depuis ces sites <br/>- **Mode désactivé,** qui empêche les utilisateurs de visiter des sites potentiellement dangereux, ni de suivre l’activité réseau vers/depuis ces sites |
| **Correction**  |  |
| **Action à prendre sur les applications potentiellement indésirables (PUA)** | PuA peut inclure des logiciels publicitaires, des logiciels de regroupement qui offrent d’installer d’autres logiciels non signés et des logiciels espions qui tentent d’éviter les fonctionnalités de sécurité. Bien que puA ne soit pas nécessairement un virus, un programme malveillant ou un autre type de menace, puA peut affecter les performances de l’appareil.<br/><br/>La protection PUA bloque les éléments détectés comme PUA. Vous pouvez définir la protection PUA sur l’un des paramètres suivants : <br/>- **Activé** (ce paramètre est le paramètre par défaut), qui bloque les éléments détectés comme PUA sur les appareils. *Nous vous recommandons de maintenir la protection PUA activée.*<br/>- **Mode audit,** qui n’a aucune action sur les éléments détectés comme PUA <br/>- **Désactivé,** qui ne détecte pas les éléments qui peuvent être puA ou n’y prennent aucune action |
| **Analyser**   |  |
| **Type d’analyse programmée** | Envisagez d’exécutez une analyse antivirus hebdomadaire sur vos appareils. Vous pouvez choisir parmi les options de type d’analyse suivantes : <br/>- **Quickscan vérifie les emplacements,** tels que les clés de Registre et les dossiers de démarrage, où les programmes malveillants peuvent être enregistrés pour démarrer avec un appareil. *Nous vous recommandons d’utiliser l’option quickscan.* <br/>- **Fullscan** vérifie tous les fichiers et dossiers sur un appareil <br/>- **Désactivée** signifie qu’aucune analyse programmée n’aura lieu. Les utilisateurs peuvent toujours exécuter des analyses sur leurs propres appareils. (En règle générale, nous vous déconseillons de désactiver vos analyses programmées.) <br/><br/> [En savoir plus sur les types d’analyse.](../defender-endpoint/schedule-antivirus-scans.md) |
| **Jour de la semaine pour exécuter une analyse programmée** | Sélectionnez un jour pour que vos analyses antivirus hebdomadaires régulières s’exécutent. |
| **Heure de la journée pour exécuter une analyse programmée** | Sélectionnez un moment pour exécuter vos analyses antivirus régulièrement programmées. |
| **Utiliser des performances faibles** | Ce paramètre est désactivé par défaut. *Nous vous recommandons de conserver ce paramètre désactivé.* Toutefois, vous pouvez activer ce paramètre pour limiter la mémoire et les ressources de l’appareil utilisées lors des analyses programmées. <br/><br/>**IMPORTANT** Si vous turn **Use low performance** on, il configure les paramètres suivants pour Antivirus Microsoft Defender : <br/>- Les fichiers d’archivage ne sont pas analysés ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>- Une faible priorité du processeur est attribuée aux analyses ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- Si une analyse antivirus complète est manquée, aucune analyse de rattrapage ne s’exécutera ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- Si une analyse antivirus rapide est manquée, aucune analyse de rattrapage ne s’exécutera ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- Réduit le facteur de charge moyenne du processeur pendant une analyse antivirus de 50 % à 20 % ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **Expérience utilisateur**   |  |
| **Autoriser les utilisateurs à accéder à l Sécurité Windows appl;** | Activez ce paramètre pour permettre aux utilisateurs d’ouvrir l’Sécurité Windows sur leurs appareils. Les utilisateurs ne pourront pas remplacer les paramètres que vous configurez dans Microsoft Defender pour Entreprise (prévisualisation), mais ils pourront exécuter une analyse rapide si nécessaire ou afficher les menaces détectées. |
| **Exclusions antivirus** | Les exclusions sont des processus, des fichiers ou des dossiers ignorés par Antivirus Microsoft Defender analyses. *En règle générale, il n’est pas nécessaire de définir des exclusions.* Antivirus Microsoft Defender inclut de nombreuses exclusions automatiques basées sur les comportements connus du système d’exploitation et les fichiers de gestion classiques.<br/><br/>[En savoir plus sur les exclusions](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **Exclusions de processus** | Les exclusions de processus empêchent les fichiers ouverts par des processus spécifiques d’être analysés par Antivirus Microsoft Defender. <br/><br/>[En savoir plus sur les exclusions de processus](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **Exclusions d’extension de fichier** | Les exclusions d’extension de fichier empêchent l’analyse des fichiers avec des extensions spécifiques par Antivirus Microsoft Defender.<br/><br/>[En savoir plus sur les exclusions d’extension de fichier](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **Exclusions de fichiers et de dossiers** | Les exclusions de fichiers et de dossiers empêchent les fichiers qui se contiennent dans des dossiers spécifiques d’être analysés par Antivirus Microsoft Defender. <br/><br/>[En savoir plus sur les exclusions de fichiers et de dossiers](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>Autres paramètres préconfigurés dans Defender for Business

Les paramètres de sécurité suivants sont préconfigurés dans Defender pour Entreprise (prévisualisation) :

- L’analyse des lecteurs amovibles est allumée ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))
- Les analyses rapides quotidiennes n’ont pas de temps prédéfini ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))
- Les mises à jour des informations de sécurité sont vérifiées avant l’analyse antivirus ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))
- Les vérifications des informations de sécurité ont lieu toutes les quatre heures ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>Paramètres et paramètres par défaut de Defender for Business Microsoft Endpoint Manager

Le tableau suivant décrit les paramètres préconfigurés pour Defender pour Entreprise (prévisualisation) et comment ces paramètres correspondent à ce que vous pouvez voir dans Microsoft Endpoint Manager (ou Microsoft Intune). Si vous utilisez le processus de configuration simplifié dans [Defender pour Entreprises](mdb-simplified-configuration.md) (prévisualisation), vous n’avez pas besoin de modifier ces paramètres.
<br/><br/>

| Setting  | Description  |
|---------|---------|
| [Protection cloud](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | Parfois appelée protection cloud ou Microsoft Advanced Protection Service (MAPS), la protection cloud fonctionne avec Antivirus Microsoft Defender et le cloud Microsoft pour identifier les nouvelles menaces, parfois même avant qu’un seul appareil ne soit affecté. La protection cloud est désactivée par défaut. <br/><br/>[En savoir plus sur la protection cloud.](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md)         |
| [Surveillance des fichiers entrants et sortants](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | Pour surveiller les fichiers entrants et sortants, [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) est définie pour surveiller tous les fichiers.         |
| [Analyser les fichiers réseau](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | Par défaut, [AllowScanningNetworkFiles n’est](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) pas activé et les fichiers réseau ne sont pas analysés. |
| [Analyser les messages électroniques](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | Par défaut, [AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) n’est pas activé et les messages électroniques ne sont pas analysés. |
| [Nombre de jours (0-90) pour conserver les programmes malveillants mis en quarantaine](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | Par défaut, [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) ce paramètre est définie sur zéro (0) jours. Artifacts que la mise en quarantaine n’est pas supprimée automatiquement.  |
| [Envoyer le consentement des exemples](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | Par défaut, [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) est et envoie automatiquement des échantillons sécurisés. Les exemples d’exemples sécurisés incluent , et les fichiers qui ne contiennent pas `.bat` `.scr` `.dll` `.exe` d’informations d’identification personnelle (PII). Si un fichier ne contient pas d’informations d’pii, l’utilisateur reçoit une demande pour autoriser l’envoi de l’exemple.<br/><br/>[En savoir plus sur la protection cloud et l’envoi d’exemples](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [Analyser les lecteurs amovibles](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | Par défaut, [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) est configuré pour analyser les lecteurs amovibles, tels que les lecteurs USB sur les appareils.<br/><br/>[En savoir plus sur les paramètres de stratégie anti-programme malveillant](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [Exécuter le temps d’analyse rapide quotidien](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | Par défaut, [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) est définie sur 2:00 AM.<br/><br/>[En savoir plus sur les paramètres d’analyse.](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings)   |
| [Vérifier les mises à jour des signatures avant d’exécution de l’analyse](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | Par défaut, [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) est configuré pour vérifier les mises à jour de l’intelligence de sécurité avant l’exécution des analyses antivirus/anti-programme malveillant.<br/><br/>[En savoir plus sur les paramètres d’analyse](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) et [les mises à jour de l’intelligence de sécurité.](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates)   |
| [Fréquence (0 à 24 heures) de vérification des mises à jour des informations de sécurité](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | Par défaut, [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) est configuré pour vérifier les mises à jour des informations de sécurité toutes les quatre heures.<br/><br/>[En savoir plus sur les paramètres d’analyse](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) et [les mises à jour de l’intelligence de sécurité.](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates) |


## <a name="next-steps"></a>Étapes suivantes

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)


## <a name="see-also"></a>Voir aussi

- [Visitez le portail Microsoft 365 Defender web](mdb-get-started.md)

- [Gérer les paramètres de pare-feu dans Microsoft Defender entreprise (aperçu)](mdb-custom-rules-firewall.md)

- [CSP Stratégie - Defender](/windows/client-management/mdm/policy-csp-defender)