---
title: Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base
description: Gérez la façon dont Antivirus Microsoft Defender reçoit les mises à jour de protection et de produit.
keywords: mises à jour, bases de référence de sécurité, protection, mises à jour de planification, mises à jour de force, mises à jour mobiles, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.date: 04/07/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 346f806129afc30ec5543c99bce3709af60cee73
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64730637"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base

**S’applique à :**
- [Microsoft Defender pour point de terminaison plans 1 et 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

Il est essentiel de maintenir Antivirus Microsoft Defender à jour pour vous assurer que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque. Veillez à mettre à jour votre protection antivirus, même si Antivirus Microsoft Defender s’exécute en [mode passif](microsoft-defender-antivirus-compatibility.md). Il existe deux types de mises à jour liées à la mise à jour des Antivirus Microsoft Defender :

- Mises à jour du renseignement de sécurité
- Mises à jour du produit

> [!TIP]
> Pour connaître le moteur, la plateforme et la date de signature les plus actuels, consultez les [mises à jour du renseignement de sécurité pour Antivirus Microsoft Defender et d’autres logiciels anti-programme malveillant Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Mises à jour du renseignement de sécurité

Antivirus Microsoft Defender utilise la [protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md) (également appelée Microsoft Advanced Protection Service ou MAPS) et télécharge régulièrement des mises à jour de renseignement de sécurité dynamiques pour fournir une protection supplémentaire. Ces mises à jour dynamiques ne remplacent pas les mises à jour régulières du renseignement de sécurité via la mise à jour du renseignement de sécurité KB2267602.

> [!NOTE]
> Les mises à jour sont publiées sous les bases de connaissances suivantes :
> - Antivirus Microsoft Defender : KB2267602
> - System Center Endpoint Protection : KB2461484

La protection fournie par le cloud est toujours activée et nécessite une connexion active à Internet pour fonctionner. Les mises à jour du renseignement de sécurité se produisent à une cadence planifiée (configurable via une stratégie). Pour plus d’informations, consultez [Utiliser la protection fournie par le cloud microsoft dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

Pour obtenir la liste des mises à jour récentes du renseignement de sécurité, consultez [les mises à jour du renseignement de sécurité pour Antivirus Microsoft Defender et d’autres logiciels anti-programme malveillant Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Les mises à jour du moteur sont incluses avec les mises à jour du renseignement de sécurité et sont publiées à une cadence mensuelle.

## <a name="product-updates"></a>Mises à jour du produit

Antivirus Microsoft Defender nécessite des [mises à jour mensuelles (KB4052623)](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) appelées *mises à jour de plateforme*.

Vous pouvez gérer la distribution des mises à jour via l’une des méthodes suivantes :

- [Windows Server Update Service (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- Méthode habituelle que vous utilisez pour déployer Microsoft et Windows mises à jour sur les points de terminaison de votre réseau.

Pour plus d’informations, consultez [Gérer les sources pour les mises à jour de protection Antivirus Microsoft Defender](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Les mises à jour mensuelles sont publiées par phases, ce qui entraîne l’affichage de plusieurs packages dans windows [Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).
> - Cet article répertorie les modifications incluses dans le canal de mise en production à grande échelle. [Consultez la dernière version de canal général ici](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Pour en savoir plus sur le processus de déploiement progressif et pour plus d’informations sur la prochaine version, consultez [Gérer le processus de déploiement progressif pour les mises à jour de Microsoft Defender](manage-gradual-rollout.md).
> - Pour en savoir plus sur les mises à jour du renseignement de sécurité, consultez [les mises à jour du renseignement de sécurité pour Antivirus Microsoft Defender et d’autres logiciels anti-programme malveillant Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Si vous recherchez une liste des processus Microsoft Defender, **[téléchargez le classeur mde-urls](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)**, puis sélectionnez la feuille de calcul **Processus Microsoft Defender** . Le classeur mde-urls répertorie également les services et leurs URL associées auxquels votre réseau doit pouvoir se connecter, comme décrit dans [Activer l’accès aux URL de service Microsoft Defender pour point de terminaison dans le serveur proxy](configure-proxy-internet.md).

## <a name="monthly-platform-and-engine-versions"></a>Versions mensuelles de la plateforme et du moteur

Pour plus d’informations sur la mise à jour ou l’installation de la mise à jour de la plateforme, consultez [Mise à jour pour Windows Defender plateforme anti-programme malveillant](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Toutes nos mises à jour contiennent

- Améliorations en termes de performances
- Améliorations de la facilité de service
- Améliorations de l’intégration (cloud, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Mars-2022 (Plateforme : 4.18.2203.5 | Moteur : 1.1.19100.5)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.361.1449.0**<br/>
&ensp;Publication : **7 mars 2022**<br/>
&ensp;Plateforme : **4.18.2203.5**<br/>
&ensp;Moteur : **1.1.19100.5**<br/>
&ensp;Phase de support : **Mises à jour de sécurité et critiques**<br/>

Version du moteur : 1.1.19100.5 <br/>
Version de la mise à jour du renseignement de sécurité : 1.361.1449.0<br/>

### <a name="whats-new"></a>Nouveautés

- Ajout d’un correctif pour une [règle de réduction de la surface d’attaque](attack-surface-reduction.md) qui bloquait un complément Outlook 
- Ajout d’un correctif pour le problème [de performances de surveillance du comportement](configure-protection-features-microsoft-defender-antivirus.md) lié aux processus en direct courts 
- Ajout d’un correctif pour l’exclusion [AMSI](/windows/win32/amsi/antimalware-scan-interface-portal) 
- Amélioration des fonctionnalités de [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) 
- Ajout d’un correctif pour la [désactivation de la protection en temps réel](configure-protection-features-microsoft-defender-antivirus.md) dans certains cas lors de l’utilisation `SharedSignaturesPath` de la configuration (pour plus d’informations sur le `SharedSignaturesPath` paramètre, consultez [Set-MpPreference](/powershell/module/defender/set-mppreference)).

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details><details>
<summary>Février-2022 (Plateforme : 4.18.2202.4 | Moteur : 1.1.19000.8)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.361.14.0**<br/>
&ensp;Publication : **14 mars 2022**<br/>
&ensp;Plateforme : **4.18.2202.4**<br/>
&ensp;Moteur : **1.1.19000.8**<br/>
&ensp;Phase de support : **Mises à jour de sécurité et critiques**<br/>

Version du moteur : 1.1.19000.8 <br/>
Version de la mise à jour du renseignement de sécurité : 1.361.14.0 <br/>

### <a name="whats-new"></a>Nouveautés

- Améliorations apportées à la logique de détection et de surveillance du comportement
- Correction des détections de réduction de la surface d’attaque déclenchées par un faux positif
- Ajout d’un correctif qui améliore la fidélité des alertes de détection de PEPT et de repérage avancé
- Defender ne prend plus en charge les notifications personnalisées sur les fenêtres contextuelles toast. Objet de stratégie de groupe/Intune/SCCM modifié et documentation pour refléter cette modification.
- Améliorations apportées à la capture des informations et à la copie des fichiers écrits dans un stockage amovible. Pour plus d’informations, consultez Microsoft Defender pour point de terminaison support de [stockage amovible Stockage Access Control](device-control-removable-storage-access-control.md) de contrôle d’appareil.
- Amélioration de la sortie du trafic lorsque le service SmartScreen est inaccessible 
- Améliorations de la connectivité pour les clients utilisant des proxys avec des exigences d’authentification
- Correction d’un bogue de mise à jour d’appareil VDI pour les partages de fichiers réseau 
- PEPT en mode bloc prend désormais en charge le ciblage granulaire des appareils avec les nouveaux CSP. Consultez [la détection et la réponse des points de terminaison (PEPT) en mode bloc](edr-in-block-mode.md).

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details><details>
<summary>Janvier-2022 (Plateforme : 4.18.2201.10 | Moteur : 1.1.18900.2)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.357.8.0**<br/>
&ensp;Publication : **9 février 2022**<br/>
&ensp;Plateforme : **4.18.2201.10**<br/>
&ensp;Moteur : **1.1.18900.2**<br/>
&ensp;Phase de support : **Mises à jour de sécurité et critiques**<br/>

Version du moteur : 1.1.18900.2 <br/>
Version de la mise à jour du renseignement de sécurité : 1.357.8.0 <br/>

### <a name="whats-new"></a>Nouveautés

- Améliorations de la surveillance du comportement dans les performances de filtrage
- Renforcement de TrustedInstaller
- Améliorations apportées à la protection contre les falsifications
- Remplacé par `ScanScheduleTime` une nouvelle `ScanScheduleOffest` applet de commande dans [Set-MpPreference](/powershell/module/defender/set-mppreference). Cette stratégie configure le nombre de minutes après minuit pour effectuer une analyse planifiée.
- Ajout du `-ServiceHealthReportInterval` paramètre à [Set-MpPreference](/powershell/module/defender/set-mppreference). Cette stratégie configure l’intervalle de temps (en minutes) pour effectuer une analyse planifiée.
- Ajout du `AllowSwitchToAsyncInspection` paramètre à [Set-MpPreference](/powershell/module/defender/set-mppreference). Cette stratégie permet une optimisation des performances, qui permet aux flux réseau inspectés de manière synchrone, de basculer vers l’inspection asynchrone une fois qu’ils ont été vérifiés et validés.
- Analyseur de performances mises à jour v2 : Prise en charge de PowerShell à distance et PowerShell 7.x ajoutées. Consultez [l’analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md).
- Correction d’un bogue de paquets en double potentiel dans Antivirus Microsoft Defender pilote système d’inspection réseau.

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Mises à jour de versions précédentes : prise en charge de la mise à niveau technique uniquement

Une fois qu’une nouvelle version de package est publiée, la prise en charge des deux versions précédentes est réduite au support technique uniquement. Les versions antérieures à celles répertoriées dans cette section sont fournies uniquement pour la prise en charge de la mise à niveau technique.<br/><br/>

<details>
<summary>Novembre-2021 (Plateforme : 4.18.2111.5 | Moteur : 1.1.18800.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.355.2.0**<br/>
&ensp;Publication : **9 décembre 2021**<br/>
&ensp;Plateforme : **4.18.2111.5**<br/>
&ensp;Moteur : **1.1.18800.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

Version du moteur : 1.1.18800.4 Version de mise à jour du renseignement de sécurité : 1.355.2.0

### <a name="whats-new"></a>Nouveautés

- Amélioration de l’efficacité de l’utilisation du processeur de certains scénarios intensifs sur Exchange serveurs
- Ajout de nouveaux champs d’état de contrôle d’appareil sous Get-MpComputerStatus dans le module Defender PowerShell. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison Stockage Access Control amovibles du contrôle d’appareil](device-control-removable-storage-access-control.md).
- Correction d’un bogue dans lequel `SharedSignatureRoot` la valeur n’a pas pu être supprimée lorsqu’elle est définie avec PowerShell
- Correction d’un bogue dans lequel [la protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) n’était pas activée, même si Microsoft Defender pour point de terminaison indiquant que la protection contre les falsifications était activée
- Ajout de correctifs de prise en charge et de bogues à l’analyseur de performances pour Antivirus Microsoft Defender outil. Pour plus d’informations, consultez [l’analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md).   
   - Prise en charge de PowerShell ISE ajoutée pour `New-MpPerformanceRecording`
   - Correction des erreurs de bogue pour `Get-MpPerformanceReport -TopFilesPerProcess`
   - Correction d’une fuite de session d’enregistrement des performances lors de l’utilisation `New-MpPerformanceRecording` dans PowerShell 7.x, les sessions distantes et PowerShell ISE


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Octobre-2021 (Plateforme : 4.18.2110.6 | Moteur : 1.1.18700.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.353.3.0**<br/>
&ensp;Publication : **28 octobre 2021**<br/>
&ensp;Plateforme : **4.18.2110.6**<br/>
&ensp;Moteur : **1.1.18700.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

Version du moteur : 1.1.18700.4 Version de mise à jour du renseignement de sécurité : 1.353.3.0

### <a name="whats-new"></a>Nouveautés

- Améliorations apportées à la couverture du trafic réseau FTP (File Transfer Protocol)
- Correctif pour réduire l’utilisation du processeur Microsoft Defender dans Exchange Server en cours d’exécution sur Windows Server 2016
- Correction des interruptions d’analyse
- Correction des alertes sur les tentatives de falsification bloquées qui n’apparaissent pas dans Security Center
- Améliorations apportées à la résilience des falsifications dans le service Microsoft Defender

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Septembre-2021 (Plateforme : 4.18.2109.6 | Moteur : 1.1.18600.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.351.7.0**<br/>
&ensp;Publication : **7 octobre 2021**<br/>
&ensp;Plateforme : **4.18.2109.6**<br/>
&ensp;Moteur : **1.1.18600.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

Version du moteur : 1.1.18600.4 Version de mise à jour du renseignement de sécurité : 1.351.7.0

### <a name="whats-new"></a>Nouveautés
- Nouvel anneau de délai pour Antivirus Microsoft Defender mises à jour du moteur et de la plateforme. Les appareils qui optent pour cet anneau recevront des mises à jour avec un délai de 48 heures. Le nouvel anneau de délai est suggéré uniquement pour les environnements critiques. Consultez [Gérer le processus de déploiement progressif pour les mises à jour de Microsoft Defender](manage-gradual-rollout.md).
- Améliorations apportées au processus de déploiement progressif des mises à jour de Microsoft Defender

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Août-2021 (Plateforme : 4.18.2108.7 | Moteur : 1.1.18500.10)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.349.22.0**<br/>
&ensp;Publication : **2 septembre 2021**<br/>
&ensp;Plateforme : **4.18.2108.7**<br/>
&ensp;Moteur : **1.1.18500.10**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Améliorations apportées au moteur de surveillance du comportement
- Publication d’un nouvel [analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md)
- Antivirus Microsoft Defender renforcée contre le chargement de DLL malveillantes
- Antivirus Microsoft Defender renforcé contre le contournement trustedInstaller
- Extension des notifications de modification de fichier pour inclure plus de données pour Human-Operated Ransomware (HumOR)

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Juillet-2021 (Plateforme : 4.18.2107.4 | Moteur : 1.1.18400.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.345.13.0**<br/>
&ensp;Publication : **5 août 2021**<br/>
&ensp;Plateforme : **4.18.2107.4**<br/>
&ensp;Moteur : **1.1.18400.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Prise en charge du contrôle d’appareil ajoutée pour les appareils portables Windows
- La protection des applications potentiellement indésirables (PUA) est activée par défaut pour les consommateurs (voir [les applications potentiellement indésirables seront bloquées par défaut](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- Les analyses planifiées pour les systèmes managés par objet stratégie de groupe respectent le temps d’analyse configuré par l’utilisateur
- Améliorations apportées au moteur de surveillance du comportement

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu

<br/>
</details><details>
<summary> Juin-2021 (Plateforme : 4.18.2106.5 | Moteur : 1.1.18300.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.343.17.0**<br/>
&ensp;Publication : **28 juin 2021**<br/>
&ensp;Plateforme : **4.18.2106.5**<br/>
&ensp;Moteur : **1.1.18300.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Nouveaux contrôles pour la gestion du processus de déploiement progressif des mises à jour de Microsoft Defender. Consultez [Gérer le processus de déploiement progressif pour les mises à jour de Microsoft Defender](manage-gradual-rollout.md).
- Amélioration du moteur de surveillance du comportement
- Améliorations apportées au déploiement des définitions de logiciel anti-programme malveillant
- Inspections des événements réseau Edge étendus

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Mai-2021 (Plateforme : 4.18.2105.4 | Moteur : 1.1.18200.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.341.8.0**<br/>
&ensp;Publication : **3 juin 2021**<br/>
&ensp;Plateforme : **4.18.2105.4**<br/>
&ensp;Moteur : **1.1.18200.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Améliorations apportées à la [surveillance du comportement](client-behavioral-blocking.md)
- Correction de la fonctionnalité de filtrage des notifications de [protection réseau](network-protection.md)

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Avril-2021 (Plateforme : 4.18.2104.14 | Moteur : 1.1.18100.5)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.337.2.0**<br/>
&ensp;Publication : **26 avril 2021**  (Moteur : 1.1.18100.6 publiée le 5 mai 2021)<br/>
&ensp;Plateforme : **4.18.2104.14**<br/>
&ensp;Moteur : **1.1.18100.5**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Plus de logique de surveillance du comportement
- Amélioration de la détection de l’enregistreur d’événements de clé en mode noyau
- Ajout de nouveaux contrôles pour gérer le processus de déploiement progressif des [mises à jour de Microsoft Defender](manage-gradual-rollout.md)


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Mars-2021 (Plateforme : 4.18.2103.7 | Moteur : 1.1.18000.5)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.335.36.0**<br/>
&ensp;Publication : **2 avril 2021**<br/>
&ensp;Plateforme : **4.18.2103.7**<br/>
&ensp;Moteur : **1.1.18000.5**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration du moteur de surveillance du comportement
- Atténuations des attaques par force brute et par force réseau étendues
- Génération d’événements de tentative de falsification ayant échoué lorsque [la protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) est activée

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Février-2021 (Plateforme : 4.18.2102.3 | Moteur : 1.1.17900.7)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.333.7.0**<br/>
&ensp;Publication : **9 mars 2021**<br/>
&ensp;Plateforme : **4.18.2102.3**<br/>
&ensp;Moteur : **1.1.17900.7**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration de la récupération de service par le biais de la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md)
- Étendre l’étendue de la protection contre les falsifications

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Janvier-2021 (Plateforme : 4.18.2101.9 | Moteur : 1.1.17800.5)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.327.1854.0**<br/>
&ensp;Publication : **2 février 2021**<br/>
&ensp;Plateforme : **4.18.2101.9**<br/>
&ensp;Moteur : **1.1.17800.5**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Améliorations de la détection d’attaque shellcode
- Visibilité accrue des tentatives de vol d’informations d’identification
- Améliorations apportées aux fonctionnalités d’antitampering dans les services Antivirus Microsoft Defender
- Prise en charge améliorée de l’émulation ARM x64
- Correctif : PEPT notification de blocage reste dans l’historique des menaces après la détection initiale de la protection en temps réel

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Novembre-2020 (Plateforme : 4.18.2011.6 | Moteur : 1.1.17700.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.327.1854.0**<br/>
&ensp;Publication : **3 décembre 2020**<br/>
&ensp;Plateforme : **4.18.2011.6**<br/>
&ensp;Moteur : **1.1.17700.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Journalisation améliorée de la prise en charge de l’état [SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Octobre-2020 (Plateforme : 4.18.2010.7 | Moteur : 1.1.17600.5)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.327.7.0**<br/>
&ensp;Publication : **29 octobre 2020**<br/>
&ensp;Plateforme : **4.18.2010.7**<br/>
&ensp;Moteur : **1.1.17600.5**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Nouvelles descriptions pour les catégories de menaces spéciales
- Amélioration des fonctionnalités d’émulation
- Amélioration des fonctionnalités d’autorisation/de blocage de l’adresse hôte
- Nouvelle option dans defender CSP pour ignorer la fusion des exclusions d’utilisateurs locaux

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu
<br/>
</details><details>
<summary> Septembre-2020 (Plateforme : 4.18.2009.7 | Moteur : 1.1.17500.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.325.10.0**<br/>
&ensp;Publication : **1er octobre 2020**<br/>
&ensp;Plateforme : **4.18.2009.7**<br/>
&ensp;Moteur : **1.1.17500.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Des autorisations d’administrateur sont requises pour restaurer des fichiers en quarantaine
- Les événements au format XML sont désormais pris en charge
- Prise en charge du fournisseur de solutions Cloud pour ignorer les fusions d’exclusion
- Nouvelles interfaces de gestion pour :
   - UDP Inspection
   - Protection réseau sur server 2019
   - Exclusions d’adresse IP pour la protection réseau
- Amélioration de la visibilité des mesures TPM
- Amélioration de l’analyse du module VBA Office

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu
<br/>
</details>
<details>
<summary> Août-2020 (Plateforme : 4.18.2008.9 | Moteur : 1.1.17400.5)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.323.9.0**<br/>
&ensp;Publication : **27 août 2020**<br/>
&ensp;Plateforme : **4.18.2008.9**<br/>
&ensp;Moteur : **1.1.17400.5**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Ajouter d’autres événements de télémétrie
- Amélioration de la télémétrie des événements d’analyse
- Amélioration de la surveillance du comportement pour les analyses de mémoire
- Amélioration de l’analyse des flux de macro
- Ajouté `AMRunningMode` à Get-MpComputerStatus cmdlet PowerShell
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) est ignoré. Antivirus Microsoft Defender se désactive automatiquement lorsqu’il détecte un autre programme antivirus.


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Juillet-2020 (Plateforme : 4.18.2007.8 | Moteur : 1.1.17300.4)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.321.30.0**<br/>
&ensp;Publication : **28 juillet 2020**<br/>
&ensp;Plateforme : **4.18.2007.8**<br/>
&ensp;Moteur : **1.1.17300.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration de la télémétrie pour BITS
- Amélioration de la validation du certificat de signature de code Authenticode

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Juin-2020 (Plateforme : 4.18.2006.10 | Moteur : 1.1.17200.2)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.319.20.0**<br/>
&ensp;Publication : **22 juin 2020**<br/>
&ensp;Plateforme : **4.18.2006.10**<br/>
&ensp;Moteur : **1.1.17200.2**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Possibilité de spécifier [l’emplacement des journaux de support](./collect-diagnostic-data.md)
- Ignorer l’analyse de rattrapage agressive en mode passif.
- Autoriser Defender à mettre à jour les connexions limitées
- Correction du réglage des performances lors de la désactivation de la mise en cache
- Requête de Registre fixe
- Correction de la randomisation du temps d’analyse dans ADMX

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Mai-2020 (Plateforme : 4.18.2005.4 | Moteur : 1.1.17100.2)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.317.20.0**<br/>
&ensp;Publication : **26 mai 2020**<br/>
&ensp;Plateforme : **4.18.2005.4**<br/>
&ensp;Moteur : **1.1.17100.2**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Journalisation améliorée des événements d’analyse
- Amélioration de la gestion des incidents en mode utilisateur.
- Ajout du suivi d’événements pour la protection contre les falsifications
- Correction de l’envoi d’un exemple AMSI
- Correction du blocage du cloud AMSI
- Journal d’installation des mises à jour de sécurité fixes

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Avril-2020 (Plateforme : 4.18.2004.6 | Moteur : 1.1.17000.2)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.315.12.0**<br/>
&ensp;Publication : **30 avril 2020**<br/>
&ensp;Plateforme : **4.18.2004.6**<br/>
&ensp;Moteur : **1.1.17000.2**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Améliorations de WDfilter
- Ajouter d’autres données d’événements actionnables aux événements de détection de réduction de la surface d’attaque
- Correction des informations de version dans les données de diagnostic et WMI
- Correction d’une version incorrecte de la plateforme dans l’interface utilisateur après la mise à jour de la plateforme
- Informations d’URL dynamiques pour la protection contre les menaces sans fichier
- Fonctionnalité d’analyse UEFI
- Étendre la journalisation pour les mises à jour

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Mars-2020 (Plateforme : 4.18.2003.8 | Moteur : 1.1.16900.2)</summary>

&ensp;Version de la mise à jour du renseignement de sécurité : **1.313.8.0**<br/>
&ensp;Publication : **24 mars 2020**<br/>
&ensp;Plateforme : **4.18.2003.8**<br/>
&ensp;Moteur : **1.1.16900.4**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Option de limitation du processeur ajoutée à [MpCmdRun](./command-line-arguments-microsoft-defender-antivirus.md)
- Améliorer la fonctionnalité de diagnostic
- réduire le délai d’expiration du renseignement de sécurité (5 min)
- Étendre la fonctionnalité de journal interne du moteur AMSI
- Améliorer la notification pour le blocage des processus

### <a name="known-issues"></a>Problèmes connus
[**Résolu**] Antivirus Microsoft Defender ignore les fichiers lors de l’exécution d’une analyse.

<br/>
</details>

<details>

<summary> Février-2020 (Plateforme : - | Moteur : 1.1.16800.2)</summary>


&ensp;Version de la mise à jour du renseignement de sécurité : **1.311.4.0**<br/>
&ensp;Publication : **25 février 2020**<br/>
&ensp;Plateforme/client : **-**<br/>
&ensp;Moteur : **1.1.16800.2**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Janvier-2020 (Plateforme : 4.18.2001.10 | Moteur : 1.1.16700.2)</summary>


Version de la mise à jour du renseignement de sécurité : **1.309.32.0**<br/>
Publication : **30 janvier 2020**<br/>
Plateforme/client : **4.18.2001.10**<br/>
Moteur : **1.1.16700.2**<br/>
&ensp;Phase de support : **Prise en charge de la mise à niveau technique (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Correction de BSOD sur WS2016 avec Exchange
- Prise en charge des mises à jour de la plateforme lorsque TMP est redirigé vers le chemin d’accès réseau
- Les versions de plateforme et de moteur sont ajoutées à [WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- étendre la mise à jour de signature d’urgence en [mode passif](./microsoft-defender-antivirus-compatibility.md)
- Correctif 4.18.1911.3 blocage

### <a name="known-issues"></a>Problèmes connus

[**Résolu**] Les appareils utilisant le [mode de secours moderne](/windows-hardware/design/device-experiences/modern-standby) peuvent rencontrer un blocage avec le pilote de filtre Windows Defender qui entraîne un écart de protection.  Les ordinateurs affectés semblent ne pas avoir été mis à jour vers la dernière plateforme anti-programme malveillant.
<br/>
> [!IMPORTANT]
> Cette mise à jour est la suivante :
> - nécessaires aux appareils RS1 exécutant une version inférieure de la plateforme pour prendre en charge SHA2 ;
> - a un indicateur de redémarrage pour les systèmes qui ont des problèmes de suspension ;
> - est re-publié en avril 2020 et ne sera pas remplacé par des mises à jour plus récentes pour maintenir la disponibilité future;
> - est classé comme une mise à jour en raison de l’exigence de redémarrage ; Et
> - n’est offert qu’avec [Windows Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> Novembre-2019 (Plateforme : 4.18.1911.3 | Moteur : 1.1.16600.7)</summary>

Version de la mise à jour du renseignement de sécurité : **1.307.13.0**<br/>
Publication : **7 décembre 2019**<br/>
Plateforme : **4.18.1911.3**<br/>
Moteur : **1.1.17000.7**<br/>
Phase de support : **Aucune prise en charge**<br/>

### <a name="whats-new"></a>Nouveautés

- Correction du niveau de traçage MpCmdRun
- Correction des informations de version de WDFilter
- Améliorer les notifications (PUA)
- ajouter des journaux MRT pour prendre en charge les fichiers

### <a name="known-issues"></a>Problèmes connus
Lorsque cette mise à jour est installée, l’appareil a besoin du package de saut 4.18.2001.10 pour pouvoir effectuer la mise à jour vers la dernière version de la plateforme.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>prise en charge de la plateforme Antivirus Microsoft Defender

Les mises à jour de plateforme et de moteur sont fournies à une cadence mensuelle. Pour être entièrement pris en charge, restez à jour avec les dernières mises à jour de la plateforme. Notre structure de support est dynamique et évolue en deux phases en fonction de la disponibilité de la dernière version de la plateforme :

- **Phase de maintenance des mises à jour critiques et de sécurité** : lors de l’exécution de la dernière version de la plateforme, vous pouvez recevoir des mises à jour de sécurité et critiques pour la plateforme anti-programme malveillant.

- **Phase de support technique (uniquement)** : une fois qu’une nouvelle version de plateforme est publiée, la prise en charge des versions antérieures (N-2) sera réduit au support technique uniquement. Les versions de plateforme antérieures à N-2 ne seront plus prises en charge.*

\*Le support technique continuera d’être fourni pour les mises à niveau de la version de version Windows 10 (voir [Version de la plateforme incluse dans Windows 10 versions](#platform-version-included-with-windows-10-releases)) vers la dernière version de la plateforme.

Au cours de la phase de support technique (uniquement), les incidents de support commercialement raisonnables seront fournis par le biais du service clientèle Microsoft & support et des offres de support managé de Microsoft (telles que le support Premier). Si un incident de support nécessite une escalade vers le développement pour obtenir des conseils supplémentaires, nécessite une mise à jour non liée à la sécurité ou une mise à jour de sécurité, les clients sont invités à effectuer une mise à niveau vers la dernière version de la plateforme ou une mise à jour intermédiaire (*).

> [!NOTE]
> Si vous déployez manuellement Antivirus Microsoft Defender Platform Update, ou si vous utilisez un script ou un produit de gestion non Microsoft pour déployer Antivirus Microsoft Defender Platform Update, assurez-vous que cette version `4.18.2001.10` est installée à partir du [catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10) avant l’installation de la dernière version de Platform Update (N-2).

### <a name="platform-version-included-with-windows-10-releases"></a>Version de plateforme incluse avec les versions Windows 10

Le tableau ci-dessous fournit les versions de plateforme et de moteur Antivirus Microsoft Defender fournies avec les dernières versions Windows 10 :<br/><br/>

|version Windows 10  |Version de la plateforme  |Version du moteur |Phase de support |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Prise en charge de la mise à niveau technique (uniquement) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Prise en charge de la mise à niveau technique (uniquement) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Prise en charge de la mise à niveau technique (uniquement) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Prise en charge de la mise à niveau technique (uniquement) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Prise en charge de la mise à niveau technique (uniquement) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Prise en charge de la mise à niveau technique (uniquement) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Prise en charge de la mise à niveau technique (uniquement) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Prise en charge de la mise à niveau technique (uniquement) |

Pour obtenir Windows 10 informations de publication, consultez la feuille d’informations [sur le cycle de vie Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Mises à jour pour la maintenance et la gestion des images de déploiement (DISM)

Nous vous recommandons de mettre à jour vos Windows 10 (éditions Enterprise, Pro et Home), Windows Server 2019, Windows Server 2022 et Windows Server 2016 images d’installation du système d’exploitation avec les dernières mises à jour antivirus et anti-programme malveillant. La mise à jour des images d’installation de votre système d’exploitation permet d’éviter un manque de protection.

Pour plus d’informations, consultez [la mise à jour de Microsoft Defender pour Windows images d’installation du système d’exploitation](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

<details>
<summary>20220321.1</summary>

&ensp;Version du package : **20220321.1**<br/>
&ensp;Version de la plateforme : **4.18.2202.4**<br/>
&ensp;Version du moteur : **1.1.19000.8**<br/>
&ensp;Version de signature : **1.351.337.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220305.1</summary>

&ensp;Version du package : **20220305.1**<br/>
&ensp;Version de la plateforme : **4.18.2201.10**<br/>
&ensp;Version du moteur : **1.1.18900.3**<br/>
&ensp;Version de signature : **1.359.1405.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220203.1</summary>

&ensp;Version du package : **20220203.1**<br/>
&ensp;Version de la plateforme : **4.18.2111.5**<br/>
&ensp;Version du moteur : **1.1.18900.2**<br/>
&ensp;Version de signature : **1.357.32.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>20220105.1</summary>

&ensp;Version du package : **20220105.1**<br/>
&ensp;Version de la plateforme : **4.18.2111.5**<br/>
&ensp;Version du moteur : **1.1.18800.4**<br/>
&ensp;Version de signature : **1.355.1482.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2112.01</summary>

&ensp;Version du package : **1.1.2112.01**<br/>
&ensp;Version de la plateforme : **4.18.2110.6**<br/>
&ensp;Version du moteur : **1.1.18700.4**<br/>
&ensp;Version de signature : **1.353.2283.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2111.02</summary>

&ensp;Version du package : **1.1.2111.02**<br/>
&ensp;Version de la plateforme : **4.18.2110.6**<br/>
&ensp;Version du moteur : **1.1.18700.4**<br/>
&ensp;Version de signature : **1.353.613.0**<br/>

### <a name="fixes"></a>Correctifs
- Correction d’un problème lié aux fichiers de localisation

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2110.01</summary>

&ensp;Version du package : **1.1.2110.01**<br/>
&ensp;Version de la plateforme : **4.18.2109.6**<br/>
&ensp;Version du moteur : **1.1.18500.10**<br/>
&ensp;Version de signature : **1.349.2103.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2109.01</summary>

&ensp;Version du package : **1.1.2109.01**<br/>
&ensp;Version de la plateforme : **4.18.2107.4**<br/>
&ensp;Version du moteur : **1.1.18400.5**<br/>
&ensp;Version de signature : **1.347.891.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2108.01</summary>

&ensp;Version du package : **1.1.2108.01**<br/>
&ensp;Version de la plateforme : **4.18.2107.4**<br/>
&ensp;Version du moteur : **1.1.18300.4**<br/>
&ensp;Version de signature : **1.343.2244.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2107.02</summary>

&ensp;Version du package : **1.1.2107.02**<br/>
&ensp;Version de la plateforme : **4.18.2105.5**<br/>
&ensp;Version du moteur : **1.1.18300.4**<br/>
&ensp;Version de signature : **1.343.658.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2106.01</summary>

&ensp;Version du package : **1.1.2106.01**<br/>
&ensp;Version de la plateforme : **4.18.2104.14**<br/>
&ensp;Version du moteur : **1.1.18100.6**<br/>
&ensp;Version de signature : **1.339.1923.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2105.01</summary>

&ensp;Version du package : **1.1.2105.01**<br/>
&ensp;Version de la plateforme : **4.18.2103.7**<br/>
&ensp;Version du moteur : **1.1.18100.6**<br/>
&ensp;Version de signature : **1.339.42.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2104.01</summary>

&ensp;Version du package : **1.1.2104.01**<br/>
&ensp;Version de la plateforme : **4.18.2102.4**<br/>
&ensp;Version du moteur : **1.1.18000.5**<br/>
&ensp;Version de signature : **1.335.232.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2103.01</summary>

&ensp;Version du package : **1.1.2103.01**<br/>
&ensp;Version de la plateforme : **4.18.2101.9**<br/>
&ensp;Version du moteur : **1.1.17800.5**<br/>
&ensp;Version de signature : **1.331.2302.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2102.03</summary>

&ensp;Version du package : **1.1.2102.03**<br/>
&ensp;Version de la plateforme : **4.18.2011.6**<br/>
&ensp;Version du moteur : **1.1.17800.5**<br/>
&ensp;Version de signature : **1.331.174.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2101.02</summary>

&ensp;Version du package : **1.1.2101.02**<br/>
&ensp;Version de la plateforme : **4.18.2011.6**<br/>
&ensp;Version du moteur : **1.1.17700.4**<br/>
&ensp;Version de signature : **1.329.1796.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2012.01</summary>

&ensp;Version du package : **1.1.2012.01**<br/>
&ensp;Version de la plateforme : **4.18.2010.7**<br/>
&ensp;Version du moteur : **1.1.17600.5**<br/>
&ensp;Version de signature : **1.327.1991.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2011.02</summary>

&ensp;Version du package : **1.1.2011.02**<br/>
&ensp;Version de la plateforme : **4.18.2010.7**<br/>
&ensp;Version du moteur : **1.1.17600.5**<br/>
&ensp;Version de signature : **1.327.658.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Signatures Antivirus Microsoft Defender actualisées
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Version du package : **1.1.2011.01**<br/>
&ensp;Version de la plateforme : **4.18.2009.7**<br/>
&ensp;Version du moteur : **1.1.17600.5**<br/>
&ensp;Version de signature : **1.327.344.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2009.10</summary>

&ensp;Version du package : **1.1.2011.01**<br/>
&ensp;Version de la plateforme : **4.18.2008.9**<br/>
&ensp;Version du moteur : **1.1.17400.5**<br/>
&ensp;Version de signature : **1.327.2216.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Ajout de la prise en charge des images d’installation de système d’exploitation Windows 10 RS1 ou version ultérieure.
<br/>
</details>

## <a name="more-resources"></a>Plus de ressources

| Article | Description  |
|:---|:---|
|[Mise à jour de Microsoft Defender pour Windows images d’installation du système d’exploitation](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Passez en revue les packages de mise à jour anti-programme malveillant pour vos images d’installation du système d’exploitation (fichiers WIM et VHD). Obtenez Antivirus Microsoft Defender mises à jour pour Windows 10 (éditions Enterprise, Pro et Home), Windows Server 2019, Windows Server 2022 et Windows Server 2016 images d’installation.  |
|[Gérer la façon dont les mises à jour de protection sont téléchargées et appliquées](manage-protection-updates-microsoft-defender-antivirus.md) | Les mises à jour de protection peuvent être fournies par le biais de nombreuses sources. |
|[Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Vous pouvez planifier le téléchargement des mises à jour de protection. |
|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Si un point de terminaison manque une mise à jour ou une analyse planifiée, vous pouvez forcer une mise à jour ou une analyse la prochaine fois qu’un utilisateur se connecte. |
|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) | Vous pouvez définir des mises à jour de protection à télécharger au démarrage ou après certains événements de protection fournis par le cloud. |
|[Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Vous pouvez spécifier des paramètres, par exemple si des mises à jour doivent se produire sur la batterie, qui sont particulièrement utiles pour les appareils mobiles et les machines virtuelles. |
| [mise à jour Microsoft Defender pour point de terminaison pour le capteur PEPT](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | Vous pouvez mettre à jour le capteur PEPT (MsSense.exe) inclus dans le nouveau package de solution unifiée Microsoft Defender pour point de terminaison publié en 2021.   |
