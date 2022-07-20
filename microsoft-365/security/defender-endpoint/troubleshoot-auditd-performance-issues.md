---
title: Résoudre les problèmes de performances AuditD liés à Microsoft Defender pour point de terminaison sur Linux
ms.reviewer: ''
description: Décrit comment résoudre les problèmes de performances liés à AuditD que vous pouvez rencontrer avec Microsoft Defender pour Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, dépannage, AuditD, XMDEClientAnalyzer, installation, déploiement, désinstallation
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 31aaf297fd3622eede2e1532ad60a20666d1bd07
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66882856"
---
# <a name="troubleshoot-auditd-performance-issues-with-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes de performances AuditD liés à Microsoft Defender pour point de terminaison sur Linux 

Cet article fournit des conseils sur la résolution des problèmes de performances liés à AuditD que vous pouvez rencontrer avec Microsoft Defender pour point de terminaison sur Linux. 

**Fond:** 

- Microsoft Defender pour point de terminaison sur les distributions de système d’exploitation Linux utilise l’infrastructure AuditD pour collecter certains types d’événements de télémétrie. 

- Les événements système capturés par les règles ajoutées à `/etc/audit/rules.d/` ajoutent à audit.log(s) et peuvent affecter l’audit de l’hôte et la collecte en amont.  

- Les événements ajoutés par Microsoft Defender pour point de terminaison sur Linux sont marqués avec `mdatp` une clé. 

- Si le service AuditD est mal configuré ou hors connexion, certains événements peuvent être manquants. Pour résoudre ce problème, [reportez-vous à : Résoudre les problèmes d’événements manquants ou d’alertes pour Microsoft Defender pour point de terminaison sur Linux.](linux-support-events.md)

Dans certaines charges de travail de serveur, deux problèmes peuvent être observés : 

- **Consommation élevée des ressources processeur** à partir **_d’mdatp_audisp_plugin_** processus. 

- ***/var/log/audit/audit.log*** devient volumineux ou pivote fréquemment. 

Ces problèmes peuvent se produire sur les serveurs avec de nombreux événements inondant AuditD.  

Cela peut se produire s’il existe plusieurs consommateurs pour AuditD, ou trop de règles avec la combinaison de Microsoft Defender pour point de terminaison et de consommateurs tiers, ou une charge de travail élevée qui génère un grand nombre d’événements. 

Pour résoudre ces problèmes, commencez par [collecter les journaux MDEClientAnalyzer](run-analyzer-macos-linux.md) sur l’exemple de serveur affecté. 

> [!NOTE]
> En règle générale, il est recommandé de mettre à jour [l’agent Microsoft Defender pour point de terminaison vers la dernière version disponible](linux-whatsnew.md) et de confirmer que le problème persiste avant d’approfondir l’examen.


## <a name="xmdeclientanalyzer"></a>XMDEClientAnalyzer 

Lorsque vous utilisez XMDEClientAnalyzer, les fichiers suivants affichent une sortie qui fournit des insights pour vous aider à résoudre les problèmes.
- auditd_info.txt
- auditd_log_analysis.txt


### <a name="auditd_infotxt"></a>auditd_info.txt

Contient la configuration AuditD générale et affiche :

- Processus inscrits en tant que consommateurs AuditD. 

- **Sortie Auditctl -s** avec **enabled=2**  

    - Suggère que l’audit est en mode immuable (nécessite un redémarrage pour que toutes les modifications de configuration prennent effet). 

- **Sortie Auditctl -l**  

    - Affiche les règles actuellement chargées dans le noyau (ce qui peut être différent de ce qui existe sur le disque dans « /etc/auditd/rules.d/mdatp.rules »). 
    
    - Indique quelles règles sont liées à Microsoft Defender pour point de terminaison. 
    
### <a name="auditd_log_analysistxt"></a>auditd_log_analysis.txt

Contient des informations agrégées importantes qui sont utiles lors de l’examen des problèmes de performances AuditD.  

- Quel composant possède les événements les plus signalés (Microsoft Defender pour point de terminaison événements seront marqués avec `key=mdatp`). 

- Les principaux initiateurs de création de rapports. 

- Appels système les plus courants (événements réseau ou système de fichiers, etc.). 

- Quels sont les chemins d’accès de système de fichiers les plus bruyants? 

**Pour atténuer la plupart des problèmes de performances AuditD, vous pouvez implémenter l’exclusion AuditD. **

> [!NOTE]
> Les exclusions doivent être effectuées uniquement pour les initiateurs ou chemins à faible menace et à bruit élevé. Par exemple, n’excluez pas /bin/bash qui risque de créer un grand angle mort.
> [Erreurs courantes à éviter lors de la définition d’exclusions](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).



## <a name="exclusion-types"></a>Types d’exclusion 

L’outil de prise en charge de XMDEClientAnalyzer contient une syntaxe qui peut être utilisée pour ajouter des règles de configuration d’exclusion AuditD : 

Exclusion AuditD : aide sur la syntaxe de l’outil de support :

:::image type="content" source="images/auditd-exclusion-support-tool-syntax-help.png" alt-text="syntaxe qui peut être utilisée pour ajouter des règles de configuration d’exclusion AuditD" lightbox="images/auditd-exclusion-support-tool-syntax-help.png":::

**Par initiateur** 

- **-e/ -exe** chemin binaire complet > supprime tous les événements par cet initiateur 

**Par chemin d’accès** 

- **-d / -dir** chemin d’accès complet à un répertoire > Supprime les événements de système de fichiers ciblant ce répertoire 

Exemples : 

Si «`/opt/app/bin/app` » écrit dans « »,`/opt/app/cfg/logs/1234.log` vous pouvez utiliser l’outil de support pour exclure avec différentes options : 

`-e /opt/app/bin/app`

`-d /opt/app/cfg`

`-x /usr/bin/python /etc/usercfg` 

`-d /usr/app/bin/`

Autres exemples : 

`./mde_support_tool.sh exclude -p <process id>`

`./mde_support_tool.sh exclude -e <process name>`

Pour exclure plusieurs éléments, concatènez les exclusions en une seule ligne : 

`./mde_support_tool.sh exclude -e <process name> -e <process name 2> -e <process name3>`
 
L’indicateur -x est utilisé pour exclure l’accès aux sous-répertoires par des initiateurs spécifiques, par exemple : 

`./mde_support_tool.sh exclude -x /usr/sbin/mv /tmp`

Ce qui précède exclut la surveillance du sous-dossier /tmp, lorsqu’il est accessible par le processus mv. 

 
> [!NOTE]
> Contactez le support Microsoft si vous avez besoin d’aide pour analyser et atténuer les problèmes de performances liés à AuditD ou pour déployer des exclusions AuditD à grande échelle. 


