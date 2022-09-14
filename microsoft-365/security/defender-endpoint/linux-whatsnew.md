---
title: Nouveautés de Microsoft Defender pour point de terminaison sur Linux
description: Liste des modifications majeures pour Microsoft Defender pour point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, whatsnew, release
ms.service: microsoft-365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6c85535f5b79bef0bdc2782daf9111a307b648b0
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67691120"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Nouveautés de Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Cet article est fréquemment mis à jour pour vous informer des nouveautés des dernières versions de Microsoft Defender pour point de terminaison sur Linux. 

- [Nouveautés de Defender pour point de terminaison sur macOS](mac-whatsnew.md)
- [Nouveautés de Defender pour point de terminaison sur iOS](ios-whatsnew.md)

<details>
  <summary>Sep-2022 (build : 101.80.97 | Version de version : 30.122072.18097.0)</summary>

&ensp;Publication : **14 septembre 2022**<br/>
&ensp;Date de publication : **14 septembre 2022**<br/>
&ensp;Build : **101.80.97**<br/>
&ensp;Version de version : **30.122072.18097.0**<br/>
&ensp;Version du moteur : **1.1.19300.3**<br/>
&ensp;Version de signature : **1.369.395.0**<br/>

**Nouveautés**

- Corrige un blocage du noyau observé sur certaines charges de travail client exécutant mdatp version 101.75.43. Après l’analyse de la cause première, cela a été attribué à une condition de concurrence lors de la libération de la propriété d’un descripteur de fichier de capteur. La condition de concurrence a été exposée en raison d’un changement récent du produit dans le chemin d’arrêt. Les clients sur les versions de noyau plus récentes (5.1+) ne sont pas affectés par ce problème.
</br>

<br/><br/>
</details>

<details>
  <summary>Août 2022 (Build : 101.75.43 | Version de version : 30.122071.17543.0)</summary>

&ensp;Publication : **2 août 2022**<br/>
&ensp;Publication : **2 août 2022**<br/>
&ensp;Build : **101.75.43**<br/>
&ensp;Version de version : **30.122071.17543.0**<br/>
&ensp;Version du moteur : **1.1.19300.3**<br/>
&ensp;Version de signature : **1.369.395.0**<br/>

**Nouveautés**

- Ajout de la prise en charge de Red Hat Enterprise Linux version 9.0
- Ajout d’un nouveau champ dans la sortie de `mdatp health` celui-ci peut être utilisé pour interroger le niveau d’application de la fonctionnalité de protection réseau. Le nouveau champ est appelé `network_protection_enforcement_level` et peut prendre l’une des valeurs suivantes : `audit`, `block`ou `disabled`.
- Résolution d’un bogue de produit où plusieurs détections du même contenu pouvaient entraîner des entrées en double dans l’historique des menaces
- Résolution d’un problème où l’un des processus générés par le produit (`mdatp_audisp_plugin`) n’était parfois pas correctement terminé lorsque le service était arrêté
- Autres correctifs de bogues
</br>

<br/><br/>
</details>

<details>
  <summary>Jul-2022 (Build : 101.73.77 | Version de version : 30.122062.17377.0)</summary>

&ensp;Publication : **21 juillet 2022**<br/>
&ensp;Publication : **21 juillet 2022**<br/>
&ensp;Build : **101.73.77**<br/>
&ensp;Version de version : **30.122062.17377.0**<br/>
&ensp;Version du moteur : **1.1.19200.3**<br/>
&ensp;Version de signature : **1.367.1011.0**<br/>


**Nouveautés**

- Ajout d’une option pour [configurer le calcul de hachage de fichier](linux-preferences.md#configure-file-hash-computation-feature)
- À partir de cette build, le produit aura le nouveau moteur anti-programme malveillant par défaut
- Améliorations des performances pour les opérations de copie de fichiers
- Correctifs de bogue
</br>

<br/><br/>
</details>

<details>
  <summary>Juin-2022 (Build : 101.71.18 | Version de version : 30.122052.17118.0)</summary>

&ensp;Publication : **24 juin 2022**<br/>
&ensp;Date de publication : **24 juin 2022**<br/>
&ensp;Build : **101.71.18**<br/>
&ensp;Version de version : **30.122052.17118.0**<br/>


**Nouveautés**

- Correctif pour prendre en charge le stockage de définitions dans des emplacements non standard (en dehors de /var) pour les mises à jour de définition v2
- Correction d’un problème dans le capteur de produit utilisé sur RHEL 6 qui pouvait entraîner un blocage du système d’exploitation
- `mdatp connectivity test` a été étendu avec une URL supplémentaire dont le produit a besoin pour fonctionner correctement. La nouvelle URL est [https://go.microsoft.com/fwlink/?linkid=2144709](https://go.microsoft.com/fwlink/?linkid=2144709).
- Jusqu’à présent, le niveau du journal des produits n’était pas conservé entre les redémarrages du produit. À partir de cette version, il existe un nouveau commutateur d’outil de ligne de commande qui conserve le niveau du journal. La nouvelle commande est `mdatp log level persist --level <level>`.
- Suppression de la dépendance `python` du package d’installation du produit
- Améliorations des performances pour les opérations de copie de fichiers et le traitement des événements réseau provenant de `auditd`
- Correctifs de bogue
</br>

<br/><br/>
</details>


<details>
  <summary>Mai-2022 (Build : 101.68.80 | Version de version : 30.122042.16880.0)</summary>

&ensp;Publication : **23 mai 2022**<br/>
&ensp;Publication : **23 mai 2022**<br/>
&ensp;Build : **101.68.80**<br/>
&ensp;Version de version : **30.122042.16880.0**<br/>

**Nouveautés** 

- Ajout de la prise en charge de la version `2.6.32-754.47.1.el6.x86_64` du noyau lors de l’exécution sur RHEL 6
- Sur RHEL 6, le produit peut désormais être installé sur les appareils exécutant un noyau d’entreprise incassable (UEK)
- Correction d’un problème où le nom du processus s’affichait parfois de manière incorrecte comme `unknown` lors de l’exécution `mdatp diagnostic real-time-protection-statistics`
- Correction d’un bogue dans lequel le produit détectait parfois incorrectement les fichiers à l’intérieur du dossier de quarantaine
- Correction d’un problème où l’outil `mdatp` de ligne de commande ne fonctionnait pas quand `/opt` il était monté en tant que liaison réversible
- Améliorations des performances & correctifs de bogues
</br>

<br/><br/>
</details>

<details>
<summary>Mai-2022 (Build : 101.65.77 | Version de version : 30.122032.16577.0)</summary>

&ensp;Publication : **2 mai 2022**<br/>
&ensp;Publication : **2 mai 2022**<br/>
&ensp;Build : **101.65.77**<br/>
&ensp;Version de version : **30.122032.16577.0**<br/>


**Nouveautés**

- Amélioration du `conflicting_applications` champ pour `mdatp health` afficher uniquement les 10 processus les plus récents et inclure les noms des processus. Cela facilite l’identification des processus potentiellement en conflit avec Microsoft Defender pour point de terminaison pour Linux.
- Correctifs de bogue


<br/><br/>
</details><details>
<summary>Mar-2022 (Build : 101.62.74 | Version de version : 30.122022.16274.0)</summary>

&ensp;Publication : **24 mars 2022**<br/>
&ensp;Date de publication : **24 mars 2022**<br/>
&ensp;Build : **101.62.74**<br/>
&ensp;Version de version : **30.122022.16274.0**<br/>


**Nouveautés**

- Résolution d’un problème où le produit bloquait incorrectement l’accès aux fichiers de taille supérieure à 2 Go lors de l’exécution sur des versions antérieures du noyau
- Correctifs de bogue


<br/><br/>
</details><details>
<summary>Mar-2022 (Build : 101.60.93 | Version de version : 30.122012.16093.0)</summary>

&ensp;Publication : **9 mars 2022**<br/>
&ensp;Date de publication : **9 mars 2022**<br/>
&ensp;Build : **101.60.93**<br/>
&ensp;Version de version : **30.122012.16093.0**<br/>

**Nouveautés**

- Cette version contient une mise à jour de sécurité pour [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)


<br/><br/>
</details><details>
<summary>Mar-2022 (Build : 101.60.05 | Version de version : 30.122012.16005.0)</summary>

&ensp;Publication : **3 mars 2022**<br/>
&ensp;Date de publication : **3 mars 2022**<br/>
&ensp;Build : **101.60.05**<br/>
&ensp;Version de version : **30.122012.16005.0**<br/>

**Nouveautés**

- Ajout de la prise en charge du noyau version 2.6.32-754.43.1.el6.x86_64 pour RHEL 6.10
- Correctifs de bogue


<br/><br/>
</details><details>
<summary>Février-2022 (Build : 101.58.80 | Version de version : 30.122012.15880.0)</summary>

&ensp;Publication : **20 février 2022**<br/>
&ensp;Publication : **20 février 2022**<br/>
&ensp;Build : **101.58.80**<br/>
&ensp;Version de version : **30.122012.15880.0**<br/>

**Nouveautés**

- L’outil de ligne de commande prend désormais en charge la restauration des fichiers mis en quarantaine à un emplacement autre que celui où le fichier a été détecté à l’origine. Cela peut être fait par le biais `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`de .
- À compter de cette version, la protection réseau pour Linux peut être évaluée à la demande
- Correctifs de bogue



<br/><br/>
</details><details>
<summary>Jan-2022 (Build : 101.56.62 | Version de version : 30.121122.15662.0)</summary>

&ensp;Publication : **26 janvier 2022**<br/>
&ensp;Date de publication : **26 janvier 2022**<br/>
&ensp;Build : **101.56.62**<br/>
&ensp;Version de version : **30.121122.15662.0**<br/>

**Nouveautés**

- Correction d’un incident de produit introduit dans la version 101.53.02 et qui a eu un impact sur plusieurs clients


<br/><br/>
</details><details>
<summary>Jan-2022 (Build : 101.53.02 | Version de version : (30.121112.15302.0)</summary>

&ensp;Publication : **8 janvier 2022**<br/>
&ensp;Date de publication : **8 janvier 2022**<br/>
&ensp;Build : **101.53.02**<br/>
&ensp;Version de publication : **30.121112.15302.0**<br/>

**Nouveautés**

- Améliorations des performances & correctifs de bogues



</details>

<details><summary> Versions 2021</summary><blockquote>
  <details><summary>(Build : 101.52.57 | Version de version : 30.121092.15257.0)</summary>
   
  <p><b> Build : 101.52.57 <br>
Version de version : 30.121092.15257.0</b></p>
   
  <p><b> Nouveautés </b></p>

   - Ajout d’une fonctionnalité permettant de détecter les fichiers jar log4j vulnérables utilisés par les applications Java. La machine est régulièrement inspectée pour l’exécution de processus Java avec des fichiers jar log4j chargés. Les informations sont signalées au backend Microsoft Defender pour point de terminaison et sont exposées dans la zone Gestion des vulnérabilités du portail.
   
   </details>

  <details><summary>(Build : 101.47.76 | Version de version : 30.121092.14776.0)</summary>
   
  <p><b> Build : 101.47.76 <br>
Version de version : 30.121092.14776.0</b></p>
   
  <p><b>Nouveautés</b></p>

   - Ajout d’un nouveau commutateur à l’outil de ligne de commande pour contrôler si les archives sont analysées pendant les analyses à la demande. Cela peut être configuré via mdatp config scan-archives --value [activé/désactivé]. Par défaut, cette option est activée.

   - Correctifs de bogue

   </details>

   <details><summary>(Build : 101.45.13 | Version de version : 30.121082.14513.0)</summary>
   
  <p> 
  Build : <b>101.45.13 </b>  <br>
Version de version :<b> 30.121082.14513.0 </b></p>
   
  <p><b>Nouveautés</b></p>

  - À compter de cette version, nous apportons Microsoft Defender pour point de terminaison prise en charge aux distributions suivantes :

    - Versions RHEL6.7-6.10 et CentOS6.7-6.10.
    - Amazon Linux 2
    - Fedora 33 ou version ultérieure

  - Correctifs de bogue

   </details>


   <details><summary>(Build : 101.45.00 | Version de version : 30.121072.14500.0)</summary>
   
   <p> 
   Build :<b> 101.45.00</b> <br>
Version de version : <b>30.121072.14500.0</b></p>
   
   <p><b>Nouveautés</b></p>
      

  - Ajout de nouveaux commutateurs à l’outil de ligne de commande :
    - Degré de contrôle du parallélisme pour les analyses à la demande. Cela peut être configuré via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Par défaut, un degré de parallélisme `2` est utilisé.
    - Déterminez si les analyses après les mises à jour du renseignement de sécurité sont activées ou désactivées. Cela peut être configuré via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Par défaut, cette valeur est définie sur `enabled`.
  - La modification du niveau du journal des produits nécessite désormais une élévation
  - Correctifs de bogue

   </details>

   <details><summary>(Build : 101.39.98 | Version de version : 30.121062.13998.0)</summary>
   
   <p> 
   Build : <b>101.39.98 </b><br>
Version de version : <b>30.121062.13998.0</b></p>
   
   <p><b>Nouveautés</b></p>

  - Améliorations des performances & correctifs de bogues
  
   </details>

   <details><summary>(Build : 101.34.27 | Version de version : 30.121052.13427.0)</summary>
   
   <p> 
   Build :<b> 101.34.27</b> <br>
Version de version : <b>30.121052.13427.0</b></p>
   
   <p><b>Nouveautés</b></p>

   - Améliorations des performances & correctifs de bogues
  
   </details>

   <details><summary>(Build : 101.29.64 | Version de version : 30.121042.12964.0)</summary>
   
   <p> 
   Build :<b> 101.29.64 </b><br>
Version de version :<b> 30.121042.12964.0</b></p>
   
   <p><b>Nouveautés</b></p>

   - À compter de cette version, les menaces détectées lors des analyses antivirus à la demande déclenchées via le client de ligne de commande sont automatiquement corrigées. Les menaces détectées lors des analyses déclenchées via l’interface utilisateur nécessitent toujours une action manuelle.
   - `mdatp diagnostic real-time-protection-statistics` prend désormais en charge deux commutateurs supplémentaires :
     - `--sort`: trie la sortie en fonction du nombre total de fichiers analysés
     - `--top N`: affiche les N premiers résultats (ne fonctionne que si `--sort` elle est également spécifiée)
   - Améliorations des performances & correctifs de bogues
  
   </details>

   <details><summary>(Build : 101.25.72 | Version de version : 30.121022.12563.0)</summary>
   
   <p> 
   Build :<b> 101.25.72</b> <br>
Version de version : <b>30.121022.12563.0</b></p>
   
   <p><b>Nouveautés</b></p>

   - Microsoft Defender pour point de terminaison sur Linux est désormais disponible en préversion pour les clients du gouvernement des États-Unis. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis](gov.md).
   - Correction d’un problème où l’utilisation de Microsoft Defender pour point de terminaison sur Linux sur des systèmes avec des systèmes de fichiers FUSE entraînait un blocage du système d’exploitation
   - Améliorations des performances & d’autres correctifs de bogues
  
   </details>

   
   <details><summary>(Build : 101.25.63 | Version de version : 30.121022.12563.0)</summary>
   
   <p> 
   Build :<b> 101.25.63</b> <br>
Version de version : <b>30.121022.12563.0</b></p>
   
   <p><b>Nouveautés</b></p>

   - Améliorations des performances & correctifs de bogues
  
   </details>

   <details><summary>(Build : 101.23.64 | Version de version : 30.121021.12364.0)</summary>
   
   <p>
Build :<b> 101.23.64 </b><br>
Version de version : 30.121021.12364.0</b></p>
   
   <p><b>Nouveautés</b></p>

   - Amélioration des performances pour la situation où un point de montage entier est ajouté à la liste d’exclusion antivirus. Avant cette version, l’activité de fichier provenant du point de montage était toujours traitée par le produit. À compter de cette version, l’activité de fichier pour les points de montage exclus est supprimée, ce qui améliore les performances du produit.
   - Ajout d’une nouvelle option à l’outil de ligne de commande pour afficher des informations sur la dernière analyse à la demande. Pour afficher des informations sur la dernière analyse à la demande, exécutez `mdatp health --details antivirus`
   - Autres améliorations des performances & correctifs de bogues
  
   </details>

   <details><summary>(Build : 101.18.53)</summary>
   
    <p> 
    Build :<b> 101.18.53 </b><br>
        
    <p>Nouveautés</b></p>

   - EDR pour Linux est désormais [en disponibilité générale](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
   - Ajout d’un nouveau commutateur de ligne de commande (`--ignore-exclusions`) pour ignorer les exclusions av pendant les analyses personnalisées (`mdatp scan custom`)
   - Étendue `mdatp diagnostic create` avec un nouveau paramètre (`--path [directory]`) qui permet d’enregistrer les journaux de diagnostic dans un autre répertoire
    - Améliorations des performances & correctifs de bogues
    
   </details>





</blockquote></details>

