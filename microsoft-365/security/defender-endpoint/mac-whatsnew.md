---
title: Nouveautés de Microsoft Defender pour point de terminaison sur Mac
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, macos, whatsnew
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: 32145a10aa908bb5395f0129f307ac3837a92d42
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66798058"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Nouveautés de Microsoft Defender pour point de terminaison sur Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pour plus d’informations sur les Microsoft Defender pour point de terminaison sur d’autres systèmes d’exploitation : 
- [Nouveautés de Microsoft Defender pour point de terminaison sur Linux](linux-whatsnew.md) 
- [Nouveautés de Microsoft Defender pour point de terminaison sur iOS](ios-whatsnew.md)</br>

<details>
  <summary>Juin-2022 (Build : 101.71.18 | Version de version : 20.122052.17118.0)</summary>

&ensp;Publication : **7 juillet 2022**<br/>
&ensp;Date de publication : **7 juillet 2022**<br/>
&ensp;Build : **101.71.18**<br/>
&ensp;Version de version : **20.122052.17118.0**<br/>

**Nouveautés**

- `mdatp connectivity test` a été étendu avec une URL supplémentaire dont le produit a besoin pour fonctionner correctement. La nouvelle URL est [https://go.microsoft.com/fwlink/?linkid=2144709](https://go.microsoft.com/fwlink/?linkid=2144709).
- Jusqu’à présent, le niveau du journal des produits n’était pas conservé entre les redémarrages du produit. À partir de cette version, il existe un nouveau commutateur d’outil de ligne de commande qui conserve le niveau du journal. La nouvelle commande est `mdatp log level persist --level <level>`.
- Correction d’un bogue dans le package d’installation du produit qui, dans de rares cas, pouvait entraîner une perte d’état du produit pendant les mises à jour
- Améliorations des performances pour les opérations de copie de fichiers et les applications macOS intégrées
- Correctifs de bogue

<br/>
</details>

<details>
  <summary>Juin-2022 (Build : 101.70.19 | Version de version : 20.122051.17019.0)</summary>

&ensp;Publication : **14 juin 2022**<br/>
&ensp;Publication : **14 juin 2022**<br/>
&ensp;Build : **101.70.19**<br/>
&ensp;Version de version : **20.122051.17019.0**<br/>

**Nouveautés**

- Correction d’un bogue dans lequel les notifications liées aux menaces n’étaient pas toujours présentées à l’utilisateur final.
- Améliorations des performances & d’autres correctifs de bogues

<br/>
</details>


<details>
  <summary>Juin-2022 (Build : 101.70.18 | Version de version : 20.122042.17018.0)</summary>

&ensp;Publication : **2 juin 2022**<br/>
&ensp;Date de publication : **2 juin 2022**<br/>
&ensp;Build : **101.70.18**<br/>
&ensp;Version de version : **20.122042.17018.0**<br/>

**Nouveautés**

- Correction d’un bogue dans lequel le package d’installation était parfois suspendu indéfiniment pendant les mises à jour du produit
- Correction d’un bogue dans lequel le produit détectait parfois incorrectement les fichiers à l’intérieur du dossier de quarantaine
- Améliorations des performances & d’autres correctifs de bogues

<br/>
</details>

<details>
  <summary>Mai-2022 (Build : 101.66.54 | Version de version : 20.122041.16654.0) </summary>

&ensp;Publication : **11 mai 2022**<br/>
&ensp;Date de publication : **11 mai 2022**<br/>
&ensp;Build : **101.66.54**<br/>
&ensp;Version de version : **20.122041.16654.0**<br/>


**Nouveautés**

- Résolution d’un problème où `mdatp diagnostic real-time-protection-statistics` l’impression du chemin d’accès au processus n’était pas correcte dans certains cas.
- Correctifs de bogue

<br/>
</details>

<details>
  <summary>Avr 2022 (Build : 101.64.15 | Version de version : 20.122032.16415.0)</summary>

&ensp;Publication : **26 avril 2022**<br/>
&ensp;Publication : **26 avril 2022**<br/>
&ensp;Build : **101.64.15**<br/>
&ensp;Version de version : **20.122032.16415.0**<br/>

**Nouveautés**

- Correction d’une régression introduite dans la version 101.61.69 où l’icône de menu État affichait parfois une icône d’erreur, même si aucune action n’était requise de la part de l’utilisateur final
- Amélioration du `conflicting_applications` champ pour `mdatp health` afficher uniquement les 10 processus les plus récents et inclure les noms des processus. Cela facilite l’identification des processus potentiellement en conflit avec Microsoft Defender pour point de terminaison pour Mac.
- Correction d’un bogue dans `mdatp device-control removable-media policy list` lequel l’ID du fournisseur et l’ID de produit étaient affichés en tant que décimaux au lieu de hexadécimals
- Améliorations des performances & d’autres correctifs de bogues

<br/>
</details>

<details>
  <summary>Mar-2022 (Build : 101.61.69 | Version de version : 20.122022.16169.0) </summary>

&ensp;Publication : **25 mars 2022**<br/>
&ensp;Date de publication : **25 mars 2022**<br/>
&ensp;Build : **101.61.69**<br/>
&ensp;Version de version : **20.122022.16169.0**<br/>

**Nouveautés**

- Correctifs de bogue

<br/>
</details>

<details>
  <summary>Mar-2022 (Build : 101.60.91 | Version de version : 20.122021.16091.0)</summary>

&ensp;Publication : **8 mars 2022**<br/>
&ensp;Date de publication : **8 mars 2022**<br/>
&ensp;Build : **101.60.91**<br/>
&ensp;Version de version : **20.122021.16091.0**<br/>

**Nouveautés**

- Cette version contient une mise à jour de sécurité pour [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

<br/>
</details>

<details>
  <summary>Février-2022 (Build : 101.59.50 | Version de version : 20.122021.15950.0) </summary>

&ensp;Publication : **28 février 2022**<br/>
&ensp;Publication : **28 février 2022**<br/>
&ensp;Build : **101.59.50**<br/>
&ensp;Version de version : **20.122021.15950.0**<br/>

**Nouveautés**

- Cette version ajoute la prise en charge de macOS 12.3. À compter de macOS 12.3, [Apple supprime Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Aucune version de Python n’est préinstallée sur macOS par défaut. **ACTION NÉCESSAIRE** : 
  - Les utilisateurs doivent mettre à jour Microsoft Defender pour point de terminaison pour Mac vers la version 101.59.50 (ou ultérieure) avant de mettre à jour leurs appareils vers macOS Monterey 12.3 (ou version ultérieure). Cette version minimale 101.59.50 est un prérequis pour éliminer les problèmes liés à Python avec Microsoft Defender pour point de terminaison pour Mac sur macOS Monterey.
  - Pour les déploiements à distance, les configurations MDM existantes doivent être mises à jour pour Microsoft Defender pour point de terminaison pour Mac version 101.59.50 (ou ultérieure). L’envoi (push) via GPM d’une ancienne version de Microsoft Defender pour point de terminaison pour Mac vers macOS Monterey 12.3 (ou version ultérieure) entraîne un échec d’installation.

<br/>
</details>

<details>
  <summary>Février-2022 (Build : 101.59.10 | Version de version : 20.122012.15910.0)</summary>

&ensp;Publication : **22 février 2022**<br/>
&ensp;Publication : **22 février 2022**<br/>
&ensp;Build : **101.59.10**<br/>
&ensp;Version de version : **20.122012.15910.0**<br/>

**Nouveautés**

- L’outil de ligne de commande prend désormais en charge la restauration des fichiers mis en quarantaine à un emplacement autre que celui où le fichier a été détecté à l’origine. Cela peut être fait par le biais `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`de .
- Contrôle d’appareil étendu pour gérer les appareils connectés via Thunderbolt 3
- Amélioration de la gestion des stratégies de contrôle d’appareil contenant des ID de fournisseur et des ID de produit non valides. Avant cette version, si la stratégie contenait un ou plusieurs ID non valides, la stratégie entière était ignorée. À partir de cette version, seules les parties non valides de la stratégie sont ignorées. Les problèmes liés à la stratégie sont exposés via `mdatp device-control removable-media policy list`.
- Correctifs de bogue

<br/>
</details>

<details>
  <summary>Février-2022 (Build : 101.56.62 | Version de version : 20.121122.15662.0)</summary>

&ensp;Publication : **7 février 2022**<br/>
&ensp;Publication : **7 février 2022**<br/>
&ensp;Build : **101.56.62**<br/>
&ensp;Version de version : **20.121122.15662.0**<br/>

**Nouveautés**

- Correctifs de bogue 

<br/>
</details>

<details>
  <summary> Jan-2022 (Build : 101.56.35 | Version de version : 20.121121.15635.0)</summary>

&ensp;Publication : **30 janvier 2022**<br/>
&ensp;Date de publication : **30 janvier 2022**<br/>
&ensp;Build : **101.56.35**<br/>
&ensp;Version de version : **20.121121.15635.0**<br/>

**Nouveautés**

- L’application a été renommée « Microsoft Defender ATP » en « Microsoft Defender ». Les utilisateurs finaux observeront les modifications suivantes :
- Le chemin d’installation de l’application a été remplacé par `/Application/Microsoft Defender ATP.app` `/Applications/Microsoft Defender.app`.
- Dans l’expérience utilisateur, les occurrences de « Microsoft Defender ATP » ont été remplacées par « Microsoft Defender »
- Résolution d’un problème où certaines applications VPN ne pouvaient pas se connecter en raison du filtre de contenu réseau distribué avec Microsoft Defender pour point de terminaison pour Mac
- Résolution d’un problème détecté dans macOS 12.2 beta 2 où le package d’installation n’a pas pu être ouvert en raison d’une modification du système d’exploitation qui empêche l’installation de packages présentant certaines caractéristiques. Bien qu’il semble que ce changement de système d’exploitation ne soit pas inclus dans la version finale de macOS 12.2, il est probable qu’il sera réintroduit dans une prochaine version de macOS. Par conséquent, nous encourageons tous les administrateurs d’entreprise à actualiser le package Microsoft Defender pour point de terminaison dans leur console de gestion vers cette version de produit (ou une version plus récente).
- Résolution d’un problème rencontré sur certains appareils M1 où le produit était bloqué avec des définitions de logiciel anti-programme malveillant non valides et n’a pas pu être mis à jour avec succès vers un ensemble de définitions fonctionnel.
- `mdatp health`La sortie a été étendue avec un attribut supplémentaire appelé `full_disk_access_enabled` qui peut être utilisé pour déterminer si l’accès au disque complet a été accordé à tous les composants de Microsoft Defender pour point de terminaison pour Mac.
- Améliorations des performances & correctifs de bogues

<br/>
</details>

<details>
  <summary>Jan-2022 (Build : 101.54.16 | Version de version : 20.121111.15416.0) </summary>

&ensp;Publication : **12 janvier 2022**<br/>
&ensp;Date de publication : **12 janvier 2022**<br/>
&ensp;Build : **101.54.16**<br/>
&ensp;Version de version : **20.121111.15416.0**<br/>

**Nouveautés**

- macOS 10.14 (Mojave) n’est plus pris en charge
- Une fois qu’un paramètre de produit cesse d’être géré par l’administrateur par le biais de GPM, il revient maintenant à la valeur qu’il avait avant d’être géré (valeur configurée localement par l’utilisateur final ou, si aucune valeur locale de ce type n’a été fournie explicitement, valeur par défaut utilisée par le produit). Avant cette modification, après l’arrêt de la gestion d’un paramètre, sa valeur managée persistait et était toujours utilisée par le produit.
- Améliorations des performances & correctifs de bogues
    
<br/>
</details>

<details><summary>Versions 2021 </summary><blockquote>
    <details><summary>(Build : 101.49.25 | Version de version : 20.121092.14925.0)</summary>

&ensp;Build: **101.49.25**<br/>
&ensp;Version de version : **20.121092.14925.0** <br/>

**Nouveautés**

- Ajout d’un nouveau commutateur à l’outil de ligne de commande pour contrôler si les archives sont analysées pendant les analyses à la demande. Cela peut être configuré via `mdatp config scan-archives --value [enabled/disabled]`. Par défaut, cette option est activée. 
- Correctifs de bogue  

<br/>
</details>
 
<details><summary>(Build : 101.47.27 | Version de version : 20.121082.14727.0)</summary>

&ensp;Build: **101.47.27**<br/>
&ensp;Version de version : **20.121082.14727.0** <br/>

**Nouveautés**
- Correction d’un blocage du système lors de l’arrêt sur macOS Mojave et macOS Catalina. 

<br/>
</details>

<details><summary>(Build : 101.43.84 | Version de version : 20.121082.14384.0)</summary>

&ensp;Build: **101.43.84**<br/>
&ensp;Version de version : **20.121082.14384.0** <br/>

**Nouveautés**
- Build candidate pour macOS 12 (Monterey) 
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.41.10 | Version de version : 20.121072.14110.0)</summary>

&ensp;Build: **101.41.10**<br/>
&ensp;Version de version : **20.121072.14110.0** <br/>

**Nouveautés**
- Ajout de nouveaux commutateurs à l’outil de ligne de commande : 
    - Degré de contrôle du parallélisme pour les analyses à la demande. Cela peut être configuré via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Par défaut, un degré de parallélisme de 2 est utilisé. 
    - Déterminez si les analyses après les mises à jour du renseignement de sécurité sont activées ou désactivées. Cela peut être configuré via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Par défaut, cette option est activée. 
- La modification du niveau du journal des produits nécessite désormais une élévation. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.40.84 | Version de version : 20.121071.14084.0)</summary>

&ensp;Build: **101.40.84**<br/>
&ensp;Version de version : **20.121071.14084.0** <br/>

**Nouveautés**
- Prise en charge native de la puce M1 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.37.97 | Version de version : 20.121062.13797.0)</summary>

&ensp;Build: **101.37.97**<br/>
&ensp;Version de version : **20.121062.13797.0** <br/>

**Nouveautés**
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.34.28 | Version de version : 20.121061.13428.0)</summary>

&ensp;Build: **101.34.28**<br/>
&ensp;Version de version : **20.121061.13428.0** <br/>

**Nouveautés**
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.34.27 | Version de version : 20.121052.13427.0)</summary>

&ensp;Build: **101.34.27**<br/>
&ensp;Version de version : **20.121052.13427.0** <br/>

**Nouveautés**
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.34.20 | Version de version : 20.121051.13420.0)</summary>

&ensp;Build: **101.34.20**<br/>
&ensp;Version de version : **20.121051.13420.0** <br/>

**Nouveautés**
- [Contrôle d’appareil pour macOS](mac-device-control-overview.md)  est désormais en disponibilité générale. 
- Nous avons résolu un problème où une analyse rapide n’a pas pu être démarrée à partir du menu d’état sur macOS 11 (Big Sur). 
- Autres correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.32.69 | Version de version : 20.121042.13269.0)</summary>

&ensp;Build: **101.32.69**<br/>
&ensp;Version de version : **20.121042.13269.0** <br/>

**Nouveautés**
- Résolution d’un problème où l’accès simultané au trousseau à partir de Microsoft Defender pour point de terminaison et d’autres applications peut entraîner une altération du trousseau.

<br/>
</details>

<details><summary>(Build : 101.29.64 | Version de version : 20.121042.12964.0)</summary>

&ensp;Build: **101.29.64**<br/>
&ensp;Version de version : **20.121042.12964.0** <br/> 

**Nouveautés**
- À compter de cette version, les menaces détectées lors des analyses antivirus à la demande déclenchées via le client de ligne de commande sont automatiquement corrigées. Les menaces détectées lors des analyses déclenchées via l’interface utilisateur nécessitent toujours une action manuelle. 
- `mdatp diagnostic real-time-protection-statistics` prend désormais en charge deux commutateurs supplémentaires : 
    - `--sort`: trie la sortie en fonction du nombre total de fichiers analysés 
    - `--top N`: affiche les N premiers résultats (ne fonctionne que si `--sort` elle est également spécifiée) 
- Améliorations des performances (en particulier pour quand `YARN` est utilisé) & correctifs de bogues

<br/>
</details>

<details><summary>(Build : 101.27.50 | Version de version : 20.121022.12750.0)</summary>

&ensp;Build: **101.27.50**<br/>
&ensp;Version de version : **20.121022.12750.0** <br/> 

**Nouveautés**
- Correctif pour prendre en charge l’expiration du certificat Apple pour macOS Catalina et versions antérieures. Ce correctif restaure les fonctionnalités de gestion des vulnérabilités & des menaces (TVM).  

<br/>
</details>

<details><summary>(Build : 101.25.69 | Version de version : 20.121022.12569.0)</summary>

&ensp;Build: **101.25.69**<br/>
&ensp;Version de version : **20.121022.12569.0** <br/> 

**Nouveautés**
- Microsoft Defender pour point de terminaison sur macOS est désormais disponible en préversion pour les clients du gouvernement des États-Unis. Pour plus d’informations, consultez  [Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis](gov.md). 
- Les améliorations des performances (en particulier pour la situation où l’application XCode Simulator est utilisée) & des correctifs de bogues. 

<br/>
</details>

<details><summary>(Build : 101.23.64 | Version de version : 20.121021.12364.0)</summary>

&ensp;Build: **101.23.64**<br/>
&ensp;Version de version : **20.121021.12364.0** <br/> 

**Nouveautés**
- Ajout d’une nouvelle option à l’outil de ligne de commande pour afficher des informations sur la dernière analyse à la demande. Pour afficher des informations sur la dernière analyse à la demande, exécutez `mdatp health --details antivirus`. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

</details>

<details><summary>Versions antérieures </summary><blockquote>
<details><summary>(Build : 101.22.79 | Version de version : 20.121012.12279.0)</summary>

&ensp;Build : **101.22.79** <br> &ensp;Version de version : **20.121012.12279.0**<br>

**Nouveautés**
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.19.88 | Version de version : 20.121011.11988.0)</summary>

&ensp;Build:**101.19.88**<br>
&ensp;Version de version : **20.121011.11988.0**<br>

**Nouveautés**
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.19.48 | Version de version : 20.120121.11948.0)</summary>

&ensp;Build : **101.19.48**<br>
&ensp;Version de version : **20.120121.11948.0**<br>

**Nouveautés**
> [!NOTE]
> L’ancienne syntaxe de l’outil en ligne de commande a été déconseillée avec cette version. Pour plus d’informations sur la nouvelle syntaxe, consultez [Ressources](mac-resources.md#configuring-from-the-command-line). 
- Ajout d’un nouveau commutateur de ligne de commande pour désactiver l’extension réseau : `mdatp system-extension network-filter disable`. Cette commande peut être utile pour résoudre les problèmes de mise en réseau qui peuvent être liés à Microsoft Defender pour point de terminaison sur Mac. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.19.21 | Version de version : 20.120101.11921.0)</summary>

&ensp;Build : **101.19.21**<br>
&ensp;Version de version : **20.120101.11921.0** <br>

**Nouveautés**
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.15.26 | Version de version : 20.120102.11526.0)</summary>

&ensp;Build : **101.15.26**<br>
&ensp;Version de version : **20.120102.11526.0**<br>

**Nouveautés**
- Amélioration de la fiabilité de l’agent lors de l’exécution sur macOS 11 Big Sur. 
- Ajout d’un nouveau commutateur de ligne de commande (`--ignore-exclusions`) pour ignorer les exclusions av pendant les analyses personnalisées (`mdatp scan custom`). 
- Améliorations des performances & correctifs de bogues

<br/> 
</details>

<details><summary>(Build : 101.13.75 | Version de version : 20.120101.11375.0)</summary>

&ensp;Build : **101.13.75**<br>
&ensp;Version de version : **20.120101.11375.0**<br>

**Nouveautés** 
- Conditions supprimées lorsque Microsoft Defender pour point de terminaison déclenchant un bogue macOS 11 (Big Sur) qui se manifeste dans une panique du noyau. 
- Correction d’une fuite de mémoire dans l’extension système Endpoint Security lors de l’exécution sur mac 11 (Big Sur). 
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.10.72)</summary>

&ensp;Build : **101.10.72** <br>

**Nouveautés** 
- Correctifs de bogue  

<br/>
</details>

<details><summary>(Build : 101.09.61)</summary>

&ensp;Build : **101.09.61**<br>

**Nouveautés** 
- Ajout d’une nouvelle préférence [managée pour désactiver l’option d’envoi de commentaires](mac-preferences.md#show--hide-option-to-send-feedback). 
- L’icône du menu État affiche désormais un état sain lorsque les paramètres du produit sont gérés. Auparavant, l’icône du menu État affichait un état d’avertissement ou d’erreur, même si les paramètres du produit étaient gérés par l’administrateur. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.09.50)</summary>

&ensp;Build : **101.09.50**<br>

**Nouveautés** 
- Cette version de produit a été validée sur macOS Big Sur 11 beta 9. 
- La nouvelle syntaxe de l’outil en ligne de commande mdatp est désormais celle par défaut. Pour plus d’informations sur la nouvelle syntaxe, consultez [Ressources pour Microsoft Defender pour point de terminaison sur macOS](mac-resources.md#configuring-from-the-command-line). 
> [!NOTE]
> L’ancienne syntaxe de l’outil en ligne de commande sera supprimée du produit le **1er janvier 2021**.
- Étendue `mdatp diagnostic create` avec un nouveau paramètre (`--path [directory]`) qui permet d’enregistrer les journaux de diagnostic dans un autre répertoire. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.09.49)</summary>

&ensp;Build : **101.09.49**<br>

**Nouveautés** 
- Améliorations de l’interface utilisateur pour différencier les exclusions gérées par l’administrateur informatique et les exclusions définies par l’utilisateur local. 
- Amélioration de l’utilisation du processeur pendant les analyses à la demande. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.07.23)</summary>

&ensp;Build : **101.07.23**<br>

**Nouveautés** 
- Ajout de nouveaux champs à la sortie de la vérification de `mdatp --health` l’état du mode passif et de l’ID de groupe EDR. 
> [!NOTE]
> `mdatp --health` sera remplacé par `mdatp health` une prochaine mise à jour du produit. 
- Correction d’un bogue dans lequel la soumission automatique d’exemples n’était pas marquée comme gérée dans l’interface utilisateur. 
- Ajout de nouveaux paramètres pour contrôler la rétention des éléments dans l’historique d’analyse antivirus. Vous pouvez maintenant [spécifier le nombre de jours pendant lesquels conserver les éléments dans l’historique](mac-preferences.md#antivirus-scan-history-retention-in-days)  [d’analyse et spécifier le nombre maximal d’éléments dans l’historique des analyses](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history). 
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.06.63)</summary>

&ensp;Build : **101.06.63**<br>

**Nouveautés** 
- Résolution d’une régression des performances introduite dans la version `101.05.17`. La régression a été introduite avec le correctif pour éliminer les paniques de noyau observées par certains clients lors de l’accès aux partages SMB. Nous avons rétabli ce changement de code et étudions d’autres façons d’éliminer les paniques du noyau. 

<br/>
</details>

<details><summary>(Build : 101.05.17)</summary>

&ensp;Build : **101.05.17**<br> 

**Nouveautés** 
> [!IMPORTANT]
> Nous travaillons sur une syntaxe nouvelle et améliorée pour l’outil `mdatp` en ligne de commande. La nouvelle syntaxe est actuellement la valeur par défaut dans les canaux Insider Fast et Insider Slow Update. Nous vous encourageons à vous famliliarize avec cette nouvelle syntaxe. Nous continuerons de soutenir l’ancienne syntaxe en parallèle avec la nouvelle syntaxe et fournirons plus de communication autour du plan de dépréciation de l’ancienne syntaxe dans les mois à venir. 
- Résolution d’une panique du noyau qui se produisait parfois lors de l’accès aux partages de fichiers SMB. 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.05.16)</summary>

&ensp;Build : **101.05.16**<br>

**Nouveautés** 
- Améliorations apportées à la logique d’analyse rapide pour réduire considérablement le nombre de fichiers analysés. 
- Ajout de la [prise en charge](mac-resources.md#how-to-enable-autocompletion) de la saisie semi-automatique pour l’outil en ligne de commande. 
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 101.03.12)</summary>

&ensp;Build : **101.03.12**<br>

**Nouveautés** 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.01.54)</summary>

&ensp;Build : **101.01.54**<br>

**Nouveautés** 
- Améliorations apportées à la compatibilité avec Time Machine 
- Améliorations apportées à l’accessibilité 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 101.00.31)</summary>

&ensp;Build : **101.00.31** <br>

**Nouveautés** 
- Amélioration de [l’expérience d’intégration de produits pour les utilisateurs Intune](/mem/intune/apps/apps-advanced-threat-protection-macos) 
- Les [exclusions antivirus prennent désormais en charge les caractères génériques](mac-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de déclencher des analyses antivirus à partir du menu contextuel macOS. Vous pouvez maintenant cliquer avec le bouton droit sur un fichier ou un dossier dans Finder et sélectionner **Analyser avec Microsoft Defender pour point de terminaison**. 
- Les rétrogradations des produits sur place sont désormais explicitement interdites par le programme d’installation. Si vous avez besoin d’une rétrogradation, commencez par désinstaller la version existante et reconfigurez votre appareil. 
- Autres améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 100.90.27)</summary>

&ensp;Build : **100.90.27** <br>   

**Nouveautés** 
- Vous pouvez maintenant [définir un canal](mac-updates.md#set-the-channel-name) de mise à jour pour Microsoft Defender pour point de terminaison sur macOS qui est différent du canal de mise à jour à l’échelle du système. 
- Icône Nouveau produit 
- Autres améliorations de l’expérience utilisateur 
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 100.86.92)</summary>

&ensp;Build : **100.86.92**<br>

**Nouveautés** 
- Améliorations apportées à la compatibilité avec Time Machine 
- Résolution d’un problème où le produit ne nettoyait parfois pas tous les fichiers pendant `/Library/Application Support/Microsoft/Defender` la désinstallation. 
- Réduction de l’utilisation du processeur du produit lorsque les produits Microsoft sont mis à jour via Microsoft AutoUpdate. 
- Autres améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 100.86.91)</summary>

&ensp;Build : **100.86.91**<br>

**Nouveautés**
> [!CAUTION]
> Pour garantir la protection la plus complète pour vos appareils macOS et conformément à l’arrêt par Apple de la remise des mises à jour de sécurité natives macOS aux versions du système d’exploitation antérieures à [actuel - 2], le déploiement et les mises à jour MDATP pour Mac ne seront plus pris en charge sur macOS Sierra [10.12]. Les mises à jour et améliorations MDATP pour Mac seront fournies aux appareils exécutant les versions Catalina [10.15], Mojave [10.14] et High Sierra [10.13].
>
> Si vous avez déjà déployé MDATP pour Mac sur vos appareils Sierra [10.12], effectuez une mise à niveau vers la dernière version de macOS pour éliminer les risques de perte de protection.

-  Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 100.83.73)</summary>

&ensp;Build : **100.83.73**<br>

**Nouveautés**
- Ajout de contrôles supplémentaires pour les administrateurs informatiques concernant [la gestion des exclusions](mac-preferences.md#exclusion-merge-policy),  [la gestion des paramètres de type de menace et les](mac-preferences.md#threat-type-settings-merge-policy)  [actions de menace non autorisées](mac-preferences.md#disallowed-threat-actions). 
- Lorsque l’accès au disque complet n’est pas activé sur l’appareil, un avertissement s’affiche maintenant dans le menu d’état. 
- Améliorations des performances & correctifs de bogues
 
<br/>
</details>

<details><summary>(Build : 100.82.60)</summary>

&ensp;Build : **100.82.60** <br>

**Nouveautés**
- Résolution d’un problème où le produit ne parvient pas à démarrer à la suite d’une mise à jour de définition.

<br/> 
</details>

<details><summary>(Build : 100.80.42)</summary>

&ensp;Build : **100.80.42**<br>

**Nouveautés**
- Correctifs de bogue

<br/> 
</details>

<details><summary>(Build : 100.79.42)</summary>

&ensp;Build : **100.79.42**<br>

**Nouveautés**
- Correction d’un problème où Microsoft Defender pour point de terminaison sur Mac interfère parfois avec Time Machine. 
- Ajout d’un nouveau commutateur à l’utilitaire de ligne de commande pour tester la connectivité avec le service principal
 
  ```bash
  mdatp connectivity test
  ```
- Ajout de la possibilité d’afficher l’historique complet des menaces dans l’interface utilisateur (accessible à partir de la vue **Historique de** protection). 
- Améliorations des performances & correctifs de bogues

<br/>
</details>

<details><summary>(Build : 100.72.15)</summary> 

&ensp;Build : **100.72.15**<br>

**Nouveautés**
- Correctifs de bogue 

<br/>
</details>

<details><summary>(Build : 100.70.99)</summary> 

&ensp;Build : **100.70.99**<br>

**Nouveautés**
- Résolution d’un problème qui affecte la capacité de certains utilisateurs à effectuer une mise à niveau vers macOS Catalina lorsque la protection en temps réel est activée. Ce problème sporadique a été provoqué par Microsoft Defender pour point de terminaison verrouillage des fichiers dans le package de mise à niveau Catalina lors de l’analyse des menaces, ce qui a entraîné des échecs dans la séquence de mise à niveau.

<br/>
</details> 

<details><summary>(Build : 100.68.99)</summary> 

&ensp;Build : **100.68.99**<br>

**Nouveautés**
- Ajout de la possibilité de configurer la fonctionnalité antivirus pour qu’elle s’exécute en [mode passif](mac-preferences.md#enforcement-level-for-antivirus-engine). 
- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<details><summary>(Build : 100.65.28)</summary> 

&ensp;Build : **100.65.28**<br>

**Nouveautés**
- Ajout de la prise en charge de macOS Catalina. 
> [!CAUTION]
> macOS 10.15 (Catalina) contient de nouvelles améliorations en matière de sécurité et de confidentialité. À compter de cette version, par défaut, les applications ne peuvent pas accéder à certains emplacements sur le disque (tels que Documents, Téléchargements, Bureau, etc.) sans consentement explicite. En l’absence de ce consentement, Microsoft Defender pour point de terminaison ne peut pas protéger entièrement votre appareil.
> 
> Le mécanisme d’octroi de ce consentement dépend de la façon dont vous avez déployé Microsoft Defender pour point de terminaison :
> 
> - Pour les déploiements manuels, consultez les instructions mises à jour dans la [rubrique Déploiement manuel](mac-install-manually.md#how-to-allow-full-disk-access).
> - Pour les déploiements managés, consultez les instructions mises à jour dans les rubriques sur le [déploiement basé sur JAMF](mac-install-with-jamf.md)et  [le déploiement](mac-install-with-intune.md#create-system-configuration-profiles)  basé sur Microsoft Intune. 

- Améliorations des performances & correctifs de bogues 

<br/>
</details>

<br/><br/>
</details>