---
title: Collecte de données pour la résolution avancée des problèmes sur Windows
description: Découvrez comment utiliser l’analyseur client pour collecter des données dans des scénarios de dépannage complexes
keywords: analzyer, collecter des données, dépanner mdeclientanalyzer, résolution avancée des problèmes
ms.service: microsoft-365-security
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
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 444f28eac9243aa5aca42b8584d910fbeed94971
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68168372"
---
# <a name="data-collection-for-advanced-troubleshooting-on-windows"></a>Collecte de données pour la résolution avancée des problèmes sur Windows

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Lorsque vous collaborez avec des professionnels du support Microsoft, vous pouvez être invité à utiliser l’analyseur client pour collecter des données pour résoudre les problèmes de scénarios plus complexes. Le script de l’analyseur prend en charge d’autres paramètres à cet effet et peut collecter un jeu de journaux spécifique en fonction des symptômes observés qui doivent être étudiés.

Exécutez « **MDEClientAnalyzer.cmd /?** » pour afficher la liste des paramètres disponibles et leur description :

:::image type="content" source="images/d89a1c04cf8441e4df72005879871bd0.png" alt-text="Paramètres de MDEClientAnalyzer.cmd" lightbox="images/d89a1c04cf8441e4df72005879871bd0.png":::

> [!NOTE]
> Quand un paramètre de dépannage avancé est utilisé, l’analyseur appelle également [MpCmdRun.exe](/microsoft-365/security/defender-endpoint/command-line-arguments-microsoft-defender-antivirus) pour collecter Microsoft Defender journaux de support antivirus.

**-h** : appelle [l’enregistreur de performances Windows](/windows-hardware/test/wpt/wpr-command-line-options) pour collecter une trace générale détaillée des performances en plus du jeu de journaux standard.

**-l** : appelle des [Analyseur de performances Windows](/windows-server/remote/remote-desktop-services/rds-rdsh-performance-counters) intégrés pour collecter une trace de perfmon légère. Cela peut être utile lors du diagnostic de problèmes de dégradation des performances lents qui se produisent au fil du temps, mais difficiles à reproduire à la demande.

**-c** - Appels dans [le moniteur de processus](/sysinternals/downloads/procmon) pour une surveillance avancée du système de fichiers, du registre et de l’activité de processus/threads en temps réel. Cela est particulièrement utile lors de la résolution des différents scénarios de compatibilité des applications.

**-i** : appelle une commande [netsh.exe](/windows/win32/winsock/netsh-exe) intégrée pour démarrer une trace de pare-feu réseau et Windows qui est utile lors de la résolution de divers problèmes liés au réseau.

**-b** - Identique à '-c', mais la trace du moniteur de processus est lancée lors du démarrage suivant et arrêtée uniquement lorsque le -b est à nouveau utilisé.

**-a** - Appelle [l’enregistreur de performances Windows](/windows-hardware/test/wpt/wpr-command-line-options) pour collecter une trace détaillée des performances spécifique à l’analyse des problèmes d’UC élevés liés au processus antivirus (MsMpEng.exe).

**-v** : utilise [ l’antivirusMpCmdRun.exe argument de ligne de commande](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus) avec la plupart des indicateurs de trace détaillés.

**-t** - Démarre la trace détaillée de tous les composants côté client pertinents pour endpoint DLP. Cela est utile pour les scénarios où les [actions DLP](/microsoft-365/compliance/endpoint-dlp-learn-about#endpoint-activities-you-can-monitor-and-take-action-on) ne se produisent pas comme prévu pour les fichiers.

**-q** : appelle DLPDiagnose.ps1 script à partir du répertoire « Tools » de l’analyseur qui valide la configuration de base et les exigences pour la protection contre la perte de données du point de terminaison.

**-d** : collecte un vidage de mémoire de MsSense **S**.exe (processus de capteur sur Windows Server 2016 ou un système d’exploitation plus ancien) et des processus connexes.

- \* Cet indicateur peut être utilisé conjointement avec les indicateurs mentionnés ci-dessus.
- \*\* Pour l’instant, l’analyseur ne prend pas en charge la capture d’un vidage de mémoire de [processus protégés par PPL](/windows-hardware/drivers/install/early-launch-antimalware) tels que MsSense.exe ou MsMpEng.exe.

**-z** - Configure les clés de Registre sur l’ordinateur pour la préparer pour la collecte complète de mémoire de la machine via [CrashOnCtrlScroll](/windows-hardware/drivers/debugger/forcing-a-system-crash-from-the-keyboard). Cela serait utile pour l’analyse des problèmes de blocage de l’ordinateur.

\* Maintenez la touche CTRL la plus à droite, puis appuyez deux fois sur la touche SCROLL LOCK.

**-k** - Utilise l’outil [NotMyFault](/sysinternals/downloads/notmyfault) pour forcer le système à se bloquer et générer un vidage de mémoire de la machine. Cela serait utile pour l’analyse de divers problèmes de stabilité du système d’exploitation.

L’analyseur et tous les indicateurs de scénario ci-dessus peuvent être lancés à distance en exécutant « RemoteMDEClientAnalyzer.cmd », qui est également regroupé dans l’ensemble d’outils de l’analyseur :

:::image type="content" source="images/57cab9d82d08f672a92bf9e748ac9572.png" alt-text="Paramètres de RemoteMDEClientAnalyzer.cmd" lightbox="images/57cab9d82d08f672a92bf9e748ac9572.png":::

> [!NOTE]
>
> - Lorsque vous utilisez RemoteMDEClientAnalyzer.cmd, il appelle psexec pour télécharger l’outil à partir du partage de fichiers configuré, puis l’exécuter localement via PsExec.exe.
    Le script CMD utilise l’indicateur « -r » pour spécifier qu’il s’exécute à distance dans le contexte SYSTEM et qu’aucune invite à l’utilisateur n’est présentée.
> - Ce même indicateur peut être utilisé avec MDEClientAnalyzer.cmd pour éviter une invite à l’utilisateur qui demande à spécifier le nombre de minutes pour la collecte de données. Par exemple :
>
>    **MDEClientAnalyzer.cmd -r -i -m 5**
>
>   - **-r** : indique que l’outil est exécuté à partir d’un contexte distant (ou non interactif)
>   - **-i** - Indicateur de scénario pour la collecte de la trace réseau avec d’autres journaux associés
>   - **-M** \# - Nombre de minutes à exécuter (5 minutes dans l’exemple ci-dessus)
