---
title: Collecte de données pour la résolution avancée des problèmes sur Windows
description: Découvrez comment utiliser l’analyseur client pour collecter des données pour des scénarios de dépannage complexes
keywords: analzyer, collecter des données, dépannage de mdeclientanalyzer, résolution avancée des problèmes
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1e65133ba8bdfd969fcca9bd9dd66d1f8340bf80
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58258599"
---
#  <a name="data-collection-for-advanced-troubleshooting-on-windows"></a>Collecte de données pour la résolution avancée des problèmes sur Windows

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

Lorsque vous collaborez avec des professionnels du support technique Microsoft, vous pouvez être invité à utiliser l’analyseur client pour collecter des données afin de résoudre les problèmes de scénarios plus complexes. Le script de l’analyseur prend en charge d’autres paramètres à cet effet et peut collecter un ensemble de journaux spécifique en fonction des symptômes observés qui doivent être examinés.

Exécuter '**MDEClientAnalyzer.cmd /?**' pour voir la liste des paramètres disponibles et leur description :

![Image des paramètres de l’analyseur client dans la ligne de commande](images/d89a1c04cf8441e4df72005879871bd0.png)

> [!NOTE]
> Lorsqu’un paramètre de dépannage avancé est [](/windows/security/threat-protection/microsoft-defender-antivirus/collect-diagnostic-data-update-compliance) utilisé, l’analyseur appelle égalementMpCmdRun.exepour collecter Antivirus Microsoft Defender journaux de support associés.

**-h** : appelle [l’enregistreur Windows performance](/windows-hardware/test/wpt/wpr-command-line-options) pour collecter un suivi détaillé des performances générales en plus du jeu de journaux standard.

**-l** - Appels dans l’Windows [Performance Monitor](/windows-server/remote/remote-desktop-services/rds-rdsh-performance-counters) pour collecter un suivi perfmon léger. Cela peut être utile lors du diagnostic des problèmes de dégradation des performances lents qui se produisent au fil du temps mais qui sont difficiles à reproduire à la demande.

**-c** - Appels dans le [moniteur](/sysinternals/downloads/procmon) de processus pour la surveillance avancée de l’activité en temps réel du système de fichiers, du Registre et des processus/threads. Cela est particulièrement utile lors du dépannage de différents scénarios de compatibilité d’application.

**-i** : appelle une [](/windows/win32/winsock/netsh-exe) commandenetsh.exeintégrée pour démarrer un suivi du réseau et du pare-feu Windows qui est utile lors de la résolution de divers problèmes liés au réseau.  
  
**-b** - Identique à '-c', mais la trace du moniteur de processus sera lancée lors du prochain démarrage et arrêtée uniquement lorsque le -b est de nouveau utilisé.

**-a** - Appelle l’Enregistreur de [performances Windows](/windows-hardware/test/wpt/wpr-command-line-options) pour collecter un suivi des performances détaillée spécifique à l’analyse des problèmes de processeur élevés liés au processus antivirus (MsMpEng.exe).

**-v** - Utilise l’antivirus [MpCmdRun.exe'argument](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus) de ligne de commande avec la plupart des indicateurs de suivi détaillées.

**-t** : démarre la trace détaillée de tous les composants côté client pertinents pour le point de terminaison DLP. Cela est utile dans les scénarios où les [actions DLP](/microsoft-365/compliance/endpoint-dlp-learn-about#endpoint-activities-you-can-monitor-and-take-action-on) ne se produisent pas comme prévu pour les fichiers.

**-q** - Appelle un script DLPDiagnose.ps1'analyseur à partir du répertoire « Tools » qui valide la configuration de base et les conditions requises pour le point de terminaison DLP.

**-d** - Collecte un vidage mémoire de MsSense **S**.exe (processus de capteur sur Windows Server 2016 ou un système d’exploitation plus ancien) et des processus associés.  
\* Cet indicateur peut être utilisé conjointement avec les indicateurs mentionnés ci-dessus.  
\*\* La capture d’un vidage mémoire de processus protégés par [PPL](/windows-hardware/drivers/install/early-launch-antimalware) tels que MsSense.exe ou MsMpEng.exe n’est pas prise en charge par l’analyseur pour le moment.

**-z** - Configure les clés de Registre sur l’ordinateur pour la préparer à la collecte de vidage mémoire complète de l’ordinateur via [CrashOnCtrlScroll](/windows-hardware/drivers/debugger/forcing-a-system-crash-from-the-keyboard).
Cela serait utile pour l’analyse des problèmes de blocage de l’ordinateur.  
\* Maintenez la touche Ctrl la plus à droite, puis appuyez deux fois sur la touche DE VERROUILLAGE DE DÉFILEMENT.

**-k** - Utilise [l’outil NotMyFault](/sysinternals/downloads/notmyfault) pour forcer le système à se crasher et générer un vidage de mémoire de l’ordinateur. Cela serait utile pour l’analyse de divers problèmes de stabilité du système d’exploitation.

L’analyseur et tous les indicateurs de scénario ci-dessus peuvent être lancés à distance en exécutant « RemoteMDEClientAnalyzer.cmd » qui est également regroupé dans l’ensemble d’outils de l’analyseur :

![Image de la ligne de commande avec des informations de l’analyseur](images/57cab9d82d08f672a92bf9e748ac9572.png)

>[!NOTE]
> -   Lorsque vous utilisez RemoteMDEClientAnalyzer.cmd, il appelle psexec pour télécharger l’outil à partir du partage de fichiers configuré, puis l’exécuter localement via PsExec.exe.
    Le script CMD utilise l’indicateur « -r » pour spécifier qu’il est en cours d’exécution à distance dans le contexte SYSTÈME et qu’aucune invite ne sera donc présentée à l’utilisateur.
>-   Ce même indicateur peut être utilisé avec MDEClientAnalyzer.cmd pour éviter une invite à l’utilisateur qui demande de spécifier le nombre de minutes pour la collecte de données. Par exemple :  
    **MDEClientAnalyzer.cmd -r -i -m 5**
    <br> **-r** : indique que l’outil est exécuté à partir d’un contexte distant (ou non interactif)  
    **-i** - Indicateur de scénario pour la collecte de suivi réseau avec d’autres journaux associés  
>   **-m** \# - Nombre de minutes d’exécuter (5 minutes dans l’exemple ci-dessus)