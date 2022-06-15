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
ms.openlocfilehash: 8cf11c82abf23d8041a8a7453e3e58082777a040
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089235"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Nouveautés de Microsoft Defender pour point de terminaison sur Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1017019-20122051170190"></a>101.70.19 (20.122051.17019.0)

- Correction d’un bogue dans lequel les notifications liées aux menaces n’étaient pas toujours présentées à l’utilisateur final.
- Améliorations des performances & d’autres correctifs de bogues

## <a name="1017018-20122042170180"></a>101.70.18 (20.122042.17018.0)

- Correction d’un bogue dans lequel le package d’installation était parfois suspendu indéfiniment pendant les mises à jour du produit
- Correction d’un bogue dans lequel le produit détectait parfois incorrectement les fichiers à l’intérieur du dossier de quarantaine
- Améliorations des performances & d’autres correctifs de bogues

## <a name="1016654-20122041166540"></a>101.66.54 (20.122041.16654.0)

- Résolution d’un problème où `mdatp diagnostic real-time-protection-statistics` l’impression du chemin d’accès au processus n’était pas correcte dans certains cas.
- Correctifs de bogue

## <a name="1016415-20122032164150"></a>101.64.15 (20.122032.16415.0)

- Correction d’une régression introduite dans la version 101.61.69 où l’icône de menu État affichait parfois une icône d’erreur, même si aucune action n’était requise de la part de l’utilisateur final
- Amélioration du `conflicting_applications` champ pour `mdatp health` afficher uniquement les 10 processus les plus récents et inclure les noms des processus. Cela facilite l’identification des processus potentiellement en conflit avec Microsoft Defender pour point de terminaison pour Mac.
- Correction d’un bogue dans `mdatp device-control removable-media policy list` lequel l’ID du fournisseur et l’ID de produit étaient affichés en tant que décimaux au lieu de hexadécimals
- Améliorations des performances & d’autres correctifs de bogues

## <a name="1016169-20122022161690"></a>101.61.69 (20.122022.16169.0)

- Correctifs de bogue

## <a name="1016091-20122021160910"></a>101.60.91 (20.122021.16091.0)

- Cette version contient une mise à jour de sécurité pour [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Cette version ajoute la prise en charge de macOS 12.3. À compter de macOS 12.3, [Apple supprime Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Aucune version de Python n’est préinstallée sur macOS par défaut. **ACTION NÉCESSAIRE** : 
  - Les utilisateurs doivent mettre à jour Microsoft Defender pour point de terminaison pour Mac vers la version 101.59.50 (ou ultérieure) avant de mettre à jour leurs appareils vers macOS Monterey 12.3 (ou version ultérieure). Cette version minimale 101.59.50 est un prérequis pour éliminer les problèmes liés à Python avec Microsoft Defender pour point de terminaison pour Mac sur macOS Monterey.
  - Pour les déploiements à distance, les configurations MDM existantes doivent être mises à jour pour Microsoft Defender pour point de terminaison pour Mac version 101.59.50 (ou ultérieure). L’envoi (push) via GPM d’une ancienne version de Microsoft Defender pour point de terminaison pour Mac à macOS Monterey 12.3 (ou version ultérieure) entraîne un échec d’installation.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- L’outil de ligne de commande prend désormais en charge la restauration des fichiers mis en quarantaine à un emplacement autre que celui où le fichier a été détecté à l’origine. Cela peut être fait par le biais `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`de .
- Contrôle d’appareil étendu pour gérer les appareils connectés via Thunderbolt 3
- Amélioration de la gestion des stratégies de contrôle d’appareil contenant des ID de fournisseur et des ID de produit non valides. Avant cette version, si la stratégie contenait un ou plusieurs ID non valides, la stratégie entière était ignorée. À partir de cette version, seules les parties non valides de la stratégie sont ignorées. Les problèmes liés à la stratégie sont exposés via `mdatp device-control removable-media policy list`.
- Correctifs de bogue

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Correctifs de bogue

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- L’application a été renommée « Microsoft Defender ATP » en « Microsoft Defender ». Les utilisateurs finaux observeront les modifications suivantes :
  - Le chemin d’installation de l’application a été remplacé par `/Application/Microsoft Defender ATP.app` `/Applications/Microsoft Defender.app`.
  - Dans l’expérience utilisateur, les occurrences de « Microsoft Defender ATP » ont été remplacées par « Microsoft Defender »
- Résolution d’un problème où certaines applications VPN ne pouvaient pas se connecter en raison du filtre de contenu réseau distribué avec Microsoft Defender pour point de terminaison pour Mac
- Résolution d’un problème détecté dans macOS version 12.2 bêta 2 où le package d’installation n’a pas pu être ouvert en raison d’une modification du système d’exploitation qui empêche l’installation de packages présentant certaines caractéristiques. Bien qu’il semble que ce changement de système d’exploitation ne soit pas inclus dans la version finale de macOS 12.2, il est probable qu’il sera réintroduit dans une version macOS ultérieure. Par conséquent, nous encourageons tous les administrateurs d’entreprise à actualiser le package Microsoft Defender pour point de terminaison dans leur console de gestion vers cette version de produit (ou une version plus récente).
- Résolution d’un problème rencontré sur certains appareils M1 où le produit était bloqué avec des définitions de logiciel anti-programme malveillant non valides et n’a pas pu être mis à jour avec succès vers un ensemble de définitions fonctionnel.
- `mdatp health`La sortie a été étendue avec un attribut supplémentaire appelé `full_disk_access_enabled` qui peut être utilisé pour déterminer si l’accès au disque complet a été accordé à tous les composants de Microsoft Defender pour point de terminaison pour Mac.
- Améliorations des performances & correctifs de bogues

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) n’est plus pris en charge
- Une fois qu’un paramètre de produit cesse d’être géré par l’administrateur par le biais de GPM, il revient maintenant à la valeur qu’il avait avant d’être géré (valeur configurée localement par l’utilisateur final ou, si aucune valeur locale de ce type n’a été fournie explicitement, valeur par défaut utilisée par le produit). Avant cette modification, après l’arrêt de la gestion d’un paramètre, sa valeur managée persistait et était toujours utilisée par le produit.
- Améliorations des performances & correctifs de bogues

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- Ajout d’un nouveau commutateur à l’outil de ligne de commande pour contrôler si les archives sont analysées pendant les analyses à la demande. Cela peut être configuré via `mdatp config scan-archives --value [enabled/disabled]`. Par défaut, cette valeur est définie sur `enabled`.
- Correctifs de bogue

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- Correction d’un blocage du système lors de l’arrêt sur macOS Mojave et macOS Catalina

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- Build candidate pour macOS 12 (Monterey)
- Correctifs de bogue

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Ajout de nouveaux commutateurs à l’outil de ligne de commande :
  - Degré de contrôle du parallélisme pour les analyses à la demande. Cela peut être configuré via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Par défaut, un degré de parallélisme `2` est utilisé.
  - Déterminez si les analyses après les mises à jour du renseignement de sécurité sont activées ou désactivées. Cela peut être configuré via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Par défaut, cette valeur est définie sur `enabled`.
- La modification du niveau du journal des produits nécessite désormais une élévation
- Améliorations des performances & correctifs de bogues

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- Prise en charge native de la puce M1
- Améliorations des performances & correctifs de bogues

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Améliorations des performances & correctifs de bogues

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Correctifs de bogue

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Correctifs de bogue

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [Le contrôle d’appareil pour macOS](mac-device-control-overview.md) est désormais en disponibilité générale
- Résolution d’un problème où une analyse rapide n’a pas pu être démarrée à partir du menu d’état sur macOS 11 (Big Sur)
- Autres correctifs de bogues

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Résolution d’un problème où l’accès simultané au trousseau à partir de Microsoft Defender pour point de terminaison et d’autres applications peut entraîner une altération du trousseau.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- À compter de cette version, les menaces détectées lors des analyses antivirus à la demande déclenchées via le client de ligne de commande sont automatiquement corrigées. Les menaces détectées lors des analyses déclenchées via l’interface utilisateur nécessitent toujours une action manuelle.
- `mdatp diagnostic real-time-protection-statistics` prend désormais en charge deux commutateurs supplémentaires :
  - `--sort`: trie la sortie en fonction du nombre total de fichiers analysés
  - `--top N`: affiche les N premiers résultats (ne fonctionne que si `--sort` elle est également spécifiée)
- Améliorations des performances (en particulier lors de l’utilisation de YARN) & des correctifs de bogues

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- Correctif pour prendre en charge l’expiration du certificat Apple pour macOS Catalina et versions antérieures. Ce correctif restaure les fonctionnalités de gestion des vulnérabilités & des menaces (TVM).

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Microsoft Defender pour point de terminaison sur macOS est désormais disponible en préversion pour les clients du gouvernement des États-Unis. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis](gov.md).
- Les améliorations des performances (en particulier pour la situation où l’application XCode Simulator est utilisée) & des correctifs de bogues.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Ajout d’une nouvelle option à l’outil de ligne de commande pour afficher des informations sur la dernière analyse à la demande. Pour afficher des informations sur la dernière analyse à la demande, exécutez `mdatp health --details antivirus`
- Améliorations des performances & correctifs de bogues

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Améliorations des performances & correctifs de bogues

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Améliorations des performances & correctifs de bogues

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> L’ancienne syntaxe de l’outil en ligne de commande a été déconseillée avec cette version. Pour plus d’informations sur la nouvelle syntaxe, consultez [Ressources](mac-resources.md#configuring-from-the-command-line).

- Ajout d’un nouveau commutateur de ligne de commande pour désactiver l’extension réseau : `mdatp system-extension network-filter disable`. Cette commande peut être utile pour résoudre les problèmes de mise en réseau liés à Microsoft Defender pour point de terminaison sur Mac
- Améliorations des performances & correctifs de bogues

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Correctifs de bogue

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Amélioration de la fiabilité de l’agent lors de l’exécution sur macOS 11 Big Sur
- Ajout d’un nouveau commutateur de ligne de commande (`--ignore-exclusions`) pour ignorer les exclusions av pendant les analyses personnalisées (`mdatp scan custom`)
- Améliorations des performances & correctifs de bogues

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Conditions supprimées quand Microsoft Defender pour point de terminaison déclenchant un bogue macOS 11 (Big Sur) qui se manifeste dans une panique du noyau
- Correction d’une fuite de mémoire dans l’extension système Endpoint Security lors de l’exécution sur mac 11 (Big Sur)
- Correctifs de bogue

## <a name="1011072"></a>101.10.72

- Correctifs de bogue

## <a name="1010961"></a>101.09.61

- Ajout d’une nouvelle préférence [managée pour désactiver l’option d’envoi de commentaires](mac-preferences.md#show--hide-option-to-send-feedback)
- L’icône du menu État affiche désormais un état sain lorsque les paramètres du produit sont gérés. Auparavant, l’icône du menu État affichait un état d’avertissement ou d’erreur, même si les paramètres du produit étaient gérés par l’administrateur.
- Améliorations des performances & correctifs de bogues

## <a name="1010950"></a>101.09.50

- Cette version de produit a été validée sur macOS Big Sur 11 beta 9

- La nouvelle syntaxe de l’outil `mdatp` en ligne de commande est désormais celle par défaut. Pour plus d’informations sur la nouvelle syntaxe, consultez [Ressources pour Microsoft Defender pour point de terminaison sur macOS](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > L’ancienne syntaxe de l’outil en ligne de commande sera supprimée du produit le **1er janvier 2021**.

- Étendue `mdatp diagnostic create` avec un nouveau paramètre (`--path [directory]`) qui permet d’enregistrer les journaux de diagnostic dans un autre répertoire
- Améliorations des performances & correctifs de bogues

## <a name="1010949"></a>101.09.49

- Améliorations apportées à l’interface utilisateur pour différencier les exclusions gérées par l’administrateur informatique et les exclusions définies par l’utilisateur local
- Amélioration de l’utilisation du processeur pendant les analyses à la demande
- Améliorations des performances & correctifs de bogues

## <a name="1010723"></a>101.07.23

- Ajout de nouveaux champs à la sortie de la vérification de `mdatp --health` l’état du mode passif et de l’ID de groupe PEPT

  > [!NOTE]
  > `mdatp --health` sera remplacé par `mdatp health` une prochaine mise à jour du produit.

- Correction d’un bogue dans lequel la soumission automatique d’exemples n’était pas marquée comme gérée dans l’interface utilisateur
- Ajout de nouveaux paramètres pour contrôler la rétention des éléments dans l’historique d’analyse antivirus. Vous pouvez maintenant [spécifier le nombre de jours pendant lesquels conserver les éléments dans l’historique d’analyse](mac-preferences.md#antivirus-scan-history-retention-in-days) et [spécifier le nombre maximal d’éléments dans l’historique des analyses](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Correctifs de bogue

## <a name="1010663"></a>101.06.63

- Résolution d’une régression des performances introduite dans la version `101.05.17`. La régression a été introduite avec le correctif pour éliminer les paniques de noyau observées par certains clients lors de l’accès aux partages SMB. Nous avons rétabli ce changement de code et étudions d’autres façons d’éliminer les paniques du noyau.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Nous travaillons sur une syntaxe nouvelle et améliorée pour l’outil `mdatp` en ligne de commande. La nouvelle syntaxe est actuellement la valeur par défaut dans les canaux Insider Fast et Insider Slow Update. Nous vous encourageons à vous famliliarize avec cette nouvelle syntaxe.
>
> Nous continuerons de soutenir l’ancienne syntaxe en parallèle avec la nouvelle syntaxe et fournirons plus de communication autour du plan de dépréciation de l’ancienne syntaxe dans les mois à venir.

- Résolution d’une panique du noyau qui se produisait parfois lors de l’accès aux partages de fichiers SMB
- Améliorations des performances & correctifs de bogues

## <a name="1010516"></a>101.05.16

- Améliorations apportées à la logique d’analyse rapide pour réduire considérablement le nombre de fichiers analysés
- Ajout de la [prise en charge](mac-resources.md#how-to-enable-autocompletion) de la saisie semi-automatique pour l’outil en ligne de commande
- Correctifs de bogue

## <a name="1010312"></a>101.03.12

- Améliorations des performances & correctifs de bogues

## <a name="1010154"></a>101.01.54

- Améliorations apportées à la compatibilité avec Time Machine
- Améliorations apportées à l’accessibilité
- Améliorations des performances & correctifs de bogues

## <a name="1010031"></a>101.00.31

- Amélioration de [l’expérience d’intégration de produits pour les utilisateurs Intune](/mem/intune/apps/apps-advanced-threat-protection-macos)
- Les [exclusions antivirus prennent désormais en charge les caractères génériques](mac-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de déclencher des analyses antivirus à partir du menu contextuel macOS. Vous pouvez maintenant cliquer avec le bouton droit sur un fichier ou un dossier dans Finder et sélectionner **Analyser avec Microsoft Defender pour point de terminaison**
- Les rétrogradations des produits sur place sont désormais explicitement interdites par le programme d’installation. Si vous avez besoin d’une rétrogradation, commencez par désinstaller la version existante et reconfigurez votre appareil
- Autres améliorations des performances & correctifs de bogues

## <a name="1009027"></a>100.90.27

- Vous pouvez maintenant [définir un canal de mise à jour](mac-updates.md#set-the-channel-name) pour Microsoft Defender pour point de terminaison sur macOS qui est différent du canal de mise à jour à l’échelle du système
- Icône Nouveau produit
- Autres améliorations de l’expérience utilisateur
- Correctifs de bogue

## <a name="1008692"></a>100.86.92

- Améliorations apportées à la compatibilité avec Time Machine
- Résolution d’un problème où le produit ne nettoyait parfois pas tous les fichiers pendant `/Library/Application Support/Microsoft/Defender` la désinstallation
- Réduction de l’utilisation du processeur du produit lorsque les produits Microsoft sont mis à jour via Microsoft AutoUpdate
- Autres améliorations des performances & correctifs de bogues

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> Pour garantir la protection la plus complète de vos appareils macOS et en conformité avec l’arrêt par Apple de la remise de macOS mises à jour de sécurité natives sur les versions de système d’exploitation antérieures à [actuelle - 2], le déploiement et les mises à jour MDATP pour Mac ne seront plus pris en charge sur macOS Sierra [10.12]. Les mises à jour et améliorations MDATP pour Mac seront fournies aux appareils exécutant les versions Catalina [10.15], Mojave [10.14] et High Sierra [10.13].
>
> Si vous avez déjà déployé MDATP pour Mac sur vos appareils Sierra [10.12], effectuez une mise à niveau vers la dernière version macOS afin d’éliminer les risques de perte de protection.

- Améliorations des performances & correctifs de bogues

## <a name="1008373"></a>100.83.73

- Ajout de contrôles supplémentaires pour les administrateurs informatiques concernant [la gestion des exclusions](mac-preferences.md#exclusion-merge-policy), [la gestion des paramètres de type de menace](mac-preferences.md#threat-type-settings-merge-policy) et les [actions de menace non autorisées](mac-preferences.md#disallowed-threat-actions)
- Lorsque l’accès au disque complet n’est pas activé sur l’appareil, un avertissement s’affiche maintenant dans le menu d’état.
- Améliorations des performances & correctifs de bogues

## <a name="1008260"></a>100.82.60

- Résolution d’un problème où le produit ne parvient pas à démarrer à la suite d’une mise à jour de définition.

## <a name="1008042"></a>100.80.42

- Correctifs de bogue

## <a name="1007942"></a>100.79.42

- Résolution d’un problème où Microsoft Defender pour point de terminaison sur Mac interfère parfois avec Time Machine
- Ajout d’un nouveau commutateur à l’utilitaire de ligne de commande pour tester la connectivité avec le service principal

  ```bash
  mdatp connectivity test
  ```

- Ajout de la possibilité d’afficher l’historique complet des menaces dans l’interface utilisateur (accessible à partir de la vue **Historique de** protection)
- Améliorations des performances & correctifs de bogues

## <a name="1007215"></a>100.72.15

- Correctifs de bogue

## <a name="1007099"></a>100.70.99

- Résolution d’un problème qui affecte la capacité de certains utilisateurs à effectuer une mise à niveau vers macOS Catalina lorsque la protection en temps réel est activée. Ce problème sporadique a été provoqué par Microsoft Defender pour point de terminaison verrouillage des fichiers dans le package de mise à niveau Catalina lors de l’analyse des menaces, ce qui a entraîné des échecs dans la séquence de mise à niveau.

## <a name="1006899"></a>100.68.99

- Ajout de la possibilité de configurer la fonctionnalité antivirus pour qu’elle s’exécute en [mode passif](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Améliorations des performances & correctifs de bogues

## <a name="1006528"></a>100.65.28

- Ajout de la prise en charge de macOS Catalina

  > [!CAUTION]
  > macOS 10.15 (Catalina) contient de nouvelles améliorations en matière de sécurité et de confidentialité. À compter de cette version, par défaut, les applications ne peuvent pas accéder à certains emplacements sur le disque (tels que Documents, Téléchargements, Bureau, etc.) sans consentement explicite. En l’absence de ce consentement, Microsoft Defender pour point de terminaison ne peut pas protéger entièrement votre appareil.
  >
  > Le mécanisme d’octroi de ce consentement dépend de la façon dont vous avez déployé Microsoft Defender pour point de terminaison :
  >
  > - Pour les déploiements manuels, consultez les instructions mises à jour dans la rubrique [Déploiement manuel](mac-install-manually.md#how-to-allow-full-disk-access) .
  > - Pour les déploiements managés, consultez les instructions mises à jour dans les rubriques de [déploiement basée sur JAMF](mac-install-with-jamf.md) et de [déploiement basé sur Microsoft Intune](mac-install-with-intune.md#create-system-configuration-profiles).

- Améliorations des performances & correctifs de bogues
