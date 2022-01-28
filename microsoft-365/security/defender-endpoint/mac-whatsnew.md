---
title: Nouveautés de Microsoft Defender pour Point de terminaison sur Mac
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour Endpoint sur Mac.
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
- m365initiative-defender-endpoint
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 054a684829217676df4bb3bf7d8469dbfc53a2a3
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2022
ms.locfileid: "62265690"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Nouveautés de Microsoft Defender pour Point de terminaison sur Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> À partir de la fin du mois de janvier 2022, Microsoft Defender pour endpoint (anciennement appelé Microsoft Defender ATP) sera référencé sous le nom de « Microsoft Defender » dans les expériences MDE pour l’utilisateur final sur macOS. 
> 
> Cette modification est actuellement disponible dans les canaux de mise à jour bêta (précédemment appelés Insider Fast) et Preview (précédemment appelés Insider Slow). La version minimale du produit qui inclut cette modification est 101.56.35. Pour plus d’informations, voir les notes de publication ci-dessous correspondant à cette version.
> 
> Cette modification n’a pas d’impact sur `mdatp` l’outil en ligne de commande.
>
> **Action requise**: si votre entreprise possède des configurations personnalisées qui reposent sur le nom du produit ou le chemin d’installation de l’application, ces configurations doivent être mises à jour avec les nouvelles valeurs répertoriées ci-dessus.

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- L’application a été renommée « Microsoft Defender ATP » en « Microsoft Defender ». Les utilisateurs finaux observeront les modifications suivantes :
  - Le chemin d’installation de l’application est devenu `/Application/Microsoft Defender ATP.app` `/Applications/Microsoft Defender.app` .
  - Dans l’expérience utilisateur, les occurrences de « Microsoft Defender ATP » ont été remplacées par « Microsoft Defender »
- Résolution d’un problème : certaines applications VPN ne pouvaient pas se connecter en raison du filtre de contenu réseau distribué avec Microsoft Defender pour endpoint pour Mac
- Nous avons résolu un problème détecté dans macOS 12.2 bêta 2 dans lequel le package d’installation n’a pas pu être ouvert en raison d’une modification du système d’exploitation qui empêche l’installation de packages avec certaines caractéristiques. Bien qu’il semble que cette modification du système d’exploitation ne soit pas incluse dans la version finale de macOS 12.2, il est probable qu’elle sera réintroduite dans une prochaine version de macOS. En tant que tel, nous encourageons tous les administrateurs d’entreprise à actualiser le package Microsoft Defender pour Endpoint dans leur console de gestion vers cette version du produit (ou une version plus récente).
- Nous avons résolu un problème sur certains appareils M1 où le produit était bloqué avec des définitions de logiciel anti-programme malveillant non valides et n’a pas pu être mis à jour avec succès vers un ensemble de définitions de travail.
- `mdatp health` la sortie a été étendue avec un attribut supplémentaire appelé qui peut être utilisé pour déterminer si l’accès disque total a été accordé à tous les composants de `full_disk_access_enabled` Microsoft Defender pour Endpoint pour Mac.
- Améliorations des performances & résolutions de bogues

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) n’est plus pris en charge
- Une fois qu’un paramètre de produit cesse d’être géré par l’administrateur via la gestion des données de gestion des données, il revient à la valeur qu’il avait avant d’être géré (valeur configurée localement par l’utilisateur final ou, si aucune valeur locale n’a été explicitement fournie, la valeur par défaut utilisée par le produit). Avant cette modification, après l’arrêt de la gestion d’un paramètre, sa valeur gérée persistait et était toujours utilisée par le produit.
- Améliorations des performances & résolutions de bogues

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- Ajout d’un nouveau commutateur à l’outil en ligne de commande pour contrôler si les archives sont analysées pendant les analyses à la demande. Cela peut être configuré via `mdatp config scan-archives --value [enabled/disabled]` . Par défaut, cette valeur est définie sur `enabled` .
- Correctifs de bogue

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- Correction d’un blocage du système lors de l’arrêt sur macOS Mojave et macOS Contrôlez

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- Build candidate pour macOS 12 (Monterey)
- Correctifs de bogue

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Ajout de nouveaux commutateurs à l’outil en ligne de commande :
  - Contrôler le degré de parallélisme pour les analyses à la demande. Cela peut être configuré via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]` . Par défaut, un degré de parallélisme `2` est utilisé.
  - Contrôler si les analyses après l’actualisation des informations de sécurité sont activées ou désactivées. Cela peut être configuré via `mdatp config scan-after-definition-update --value [enabled/disabled]` . Par défaut, cette valeur est définie sur `enabled` .
- La modification du niveau du journal des produits nécessite désormais une élévation
- Améliorations des performances & résolutions de bogues

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- Prise en charge native de la puce M1
- Améliorations des performances & résolutions de bogues

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Améliorations des performances & résolutions de bogues

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Correctifs de bogue

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Correctifs de bogue

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [Le contrôle d’appareil pour macOS](mac-device-control-overview.md) est désormais disponible en général
- Nous avons résolu un problème dans lequel une analyse rapide n’a pas pu être démarrée à partir du menu d’état sur macOS 11 (Big Sur)
- Autres correctifs de bogue

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Nous avons résolu un problème dans lequel l’accès simultané auchain de Microsoft Defender pour le point de terminaison et d’autres applications peut entraîner une altération duchain.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- À partir de cette version, les menaces détectées lors des analyses antivirus à la demande déclenchées via le client de ligne de commande sont automatiquement corrigés. Les menaces détectées lors des analyses déclenchées via l’interface utilisateur nécessitent toujours une action manuelle.
- `mdatp diagnostic real-time-protection-statistics` prend désormais en charge deux commutateurs supplémentaires :
  - `--sort`: trie la sortie décroit par nombre total de fichiers analysés
  - `--top N`: affiche les N premiers résultats (fonctionne uniquement si `--sort` elle est également spécifiée)
- Améliorations des performances (en particulier lorsque LAXX est utilisée) & résolutions de bogues

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- Correctif à prendre en compte pour l’expiration du certificat Apple pour macOS 2013 et les version antérieures. Ce correctif restaure la fonctionnalité gestion & menaces et vulnérabilités (TVM).

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Microsoft Defender pour le point de terminaison sur macOS est désormais disponible en prévisualisation pour les clients du gouvernement des États-Unis. Pour plus d’informations, [voir Microsoft Defender for Endpoint for US Government customers](gov.md).
- Améliorations des performances (en particulier pour la situation d’utilisation de l’application Simulateur XCode) & résolutions de bogues.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Ajout d’une nouvelle option à l’outil en ligne de commande pour afficher les informations sur la dernière analyse à la demande. Pour afficher des informations sur la dernière analyse à la demande, exécutez `mdatp health --details antivirus`
- Améliorations des performances & résolutions de bogues

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Améliorations des performances & résolutions de bogues

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Améliorations des performances & résolutions de bogues

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> L’ancienne syntaxe de l’outil de ligne de commande a été dépréciée avec cette version. Pour plus d’informations sur la nouvelle syntaxe, voir [Resources](mac-resources.md#configuring-from-the-command-line).

- Ajout d’un nouveau commutateur de ligne de commande pour désactiver l’extension réseau : `mdatp system-extension network-filter disable` . Cette commande peut être utile pour résoudre les problèmes réseau qui peuvent être liés à Microsoft Defender pour Endpoint sur Mac
- Améliorations des performances & résolutions de bogues

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Correctifs de bogue

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Amélioration de la fiabilité de l’agent lors de l’exécution sur macOS 11 Big Sur
- Ajout d’un nouveau commutateur de ligne de commande ( ) pour ignorer les exclusions av lors `--ignore-exclusions` des analyses personnalisées ( `mdatp scan custom` )
- Améliorations des performances & résolutions de bogues

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Conditions supprimées lorsque Microsoft Defender pour le point de terminaison déclenchant un bogue macOS 11 (Big Sur) qui se manifeste en noyau
- Correction d’une fuite de mémoire dans l’extension système de sécurité des points de terminaison lors de l’exécution sur mac 11 (Big Sur)
- Correctifs de bogue

## <a name="1011072"></a>101.10.72

- Correctifs de bogue

## <a name="1010961"></a>101.09.61

- Ajout d’une nouvelle préférence gérée pour [désactiver l’option d’envoi de commentaires](mac-preferences.md#show--hide-option-to-send-feedback)
- L’icône du menu État affiche désormais un état sain lorsque les paramètres du produit sont gérés. Auparavant, l’icône du menu d’état affichait un état d’avertissement ou d’erreur, même si les paramètres du produit étaient gérés par l’administrateur.
- Améliorations des performances & résolutions de bogues

## <a name="1010950"></a>101.09.50

- Cette version du produit a été validée sur macOS Big Sur 11 bêta 9

- La nouvelle syntaxe de `mdatp` l’outil en ligne de commande est désormais la syntaxe par défaut. Pour plus d’informations sur la nouvelle syntaxe, voir [Resources for Microsoft Defender for Endpoint on macOS](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > L’ancienne syntaxe de l’outil de ligne de commande sera supprimée du produit le **1er janvier 2021.**

- Étendu avec un nouveau paramètre ( ) qui permet d’enregistrer les journaux de diagnostic dans `mdatp diagnostic create` `--path [directory]` un autre répertoire
- Améliorations des performances & résolutions de bogues

## <a name="1010949"></a>101.09.49

- Améliorations apportées à l’interface utilisateur pour différencier les exclusions gérées par l’administrateur informatique des exclusions définies par l’utilisateur local
- Amélioration de l’utilisation du processeur lors des analyses à la demande
- Améliorations des performances & résolutions de bogues

## <a name="1010723"></a>101.07.23

- Ajout de nouveaux champs à la sortie de la vérification de l’état du mode passif et de `mdatp --health` l’ID PEPT groupe

  > [!NOTE]
  > `mdatp --health` sera remplacé par `mdatp health` dans une prochaine mise à jour du produit.

- Correction d’un bogue dans lequel l’envoi automatique d’échantillons n’a pas été marqué comme géré dans l’interface utilisateur
- Ajout de nouveaux paramètres pour contrôler la rétention des éléments dans l’historique d’analyse antivirus. Vous pouvez maintenant [spécifier le nombre](mac-preferences.md#antivirus-scan-history-retention-in-days) de jours de rétention des éléments dans l’historique d’analyse et spécifier le nombre maximal d’éléments [dans l’historique d’analyse.](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Correctifs de bogue

## <a name="1010663"></a>101.06.63

- Nous avons résolu une régression des performances introduite dans la version `101.05.17` . La régression a été introduite avec le correctif pour éliminer les noyaux observés par certains clients lors de l’accès aux partages SMB. Nous avons revenir à ce changement de code et nous sommes en train d’examiner d’autres façons d’éliminer les noyaux.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Nous travaillons sur une syntaxe nouvelle et améliorée pour `mdatp` l’outil en ligne de commande. La nouvelle syntaxe est actuellement la valeur par défaut dans les canaux de mise à jour Insider Fast et Insider Slow. Nous vous encourageons à vous familiariser avec cette nouvelle syntaxe.
>
> Nous continuerons à la prise en charge de l’ancienne syntaxe parallèlement à la nouvelle syntaxe et nous fournirons une meilleure communication autour du plan de désaprétation de l’ancienne syntaxe dans les mois à venir.

- Nous avons résolu un problème de noyau qui se produisait parfois lors de l’accès aux partages de fichiers SMB
- Améliorations des performances & résolutions de bogues

## <a name="1010516"></a>101.05.16

- Améliorations apportées à la logique d’analyse rapide pour réduire considérablement le nombre de fichiers analysés
- Ajout de la prise en charge [de lacompletion](mac-resources.md#how-to-enable-autocompletion) automatique pour l’outil en ligne de commande
- Correctifs de bogue

## <a name="1010312"></a>101.03.12

- Améliorations des performances & résolutions de bogues

## <a name="1010154"></a>101.01.54

- Améliorations en matière de compatibilité avec Time Machine
- Améliorations apportées à l’accessibilité
- Améliorations des performances & résolutions de bogues

## <a name="1010031"></a>101.00.31

- Amélioration de [l’expérience d’intégration de produit pour les utilisateurs d’Intune](/mem/intune/apps/apps-advanced-threat-protection-macos)
- Les [exclusions antivirus désormais prise en charge les caractères génériques](mac-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de déclencher des analyses antivirus à partir du menu contextuel macOS. Vous pouvez maintenant cliquer avec le bouton droit sur un fichier ou un dossier dans finder et sélectionner Analyser **avec Microsoft Defender pour le point de terminaison**
- Les rétrogradations de produits sur place sont désormais explicitement interdits par le programme d’installation. Si vous devez rétrograder, désinstallez d’abord la version existante et reconfigurez votre appareil.
- Autres améliorations en matière de performances & résolutions de bogues

## <a name="1009027"></a>100.90.27

- Vous pouvez désormais [définir un canal](mac-updates.md#set-the-channel-name) de mise à jour pour Microsoft Defender pour point de terminaison sur macOS qui est différent du canal de mise à jour à l’échelle du système
- Icône Nouveau produit
- Autres améliorations de l’expérience utilisateur
- Correctifs de bogue

## <a name="1008692"></a>100.86.92

- Améliorations en matière de compatibilité avec Time Machine
- Nous avons résolu un problème dans lequel le produit n’était parfois pas en train de nettoyer tous les fichiers pendant `/Library/Application Support/Microsoft/Defender` la désinstallation
- Réduction de l’utilisation processeur du produit lorsque les produits Microsoft sont mis à jour via la mise à jour automatique Microsoft
- Autres améliorations en matière de performances & résolutions de bogues

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> Pour garantir la protection la plus complète pour vos appareils macOS et en adéquation avec l’arrêt par Apple des mises à jour de sécurité natives macOS aux versions de système d’exploitation antérieures à [actuel - 2], le déploiement et les mises à jour MDATP pour Mac ne seront plus pris en charge sur macOS Sierra [10.12]. Les mises à jour et améliorations de MDATP pour Mac seront apportées aux appareils exécutant les versions Derline [10.15], Mojave [10.14] et High Sierra [10.13].
>
> Si vous avez déjà déployé MDATP pour Mac sur vos appareils Sierra [10.12], veuillez mettre à niveau vers la dernière version de macOS afin d’éliminer les risques de perte de protection.

- Améliorations des performances & résolutions de bogues

## <a name="1008373"></a>100.83.73

- Ajout de contrôles pour les administrateurs informatiques autour de la gestion des [exclusions,](mac-preferences.md#exclusion-merge-policy)de la gestion des [paramètres](mac-preferences.md#threat-type-settings-merge-policy)de type de menace et des actions contre [les menaces non prises en charge](mac-preferences.md#disallowed-threat-actions)
- Lorsque l’accès disque total n’est pas activé sur l’appareil, un avertissement s’affiche désormais dans le menu d’état
- Améliorations des performances & résolutions de bogues

## <a name="1008260"></a>100.82.60

- Nous avons résolu un problème dans lequel le produit ne parvient pas à démarrer à la suite d’une mise à jour de définition.

## <a name="1008042"></a>100.80.42

- Correctifs de bogue

## <a name="1007942"></a>100.79.42

- Correction d’un problème dans lequel Microsoft Defender pour point de terminaison sur Mac interfère parfois avec Time Machine
- Ajout d’un nouveau commutateur à l’utilitaire de ligne de commande pour tester la connectivité avec le service back-end

  ```bash
  mdatp connectivity test
  ```

- Possibilité supplémentaire d’afficher l’historique complet des menaces dans l’interface utilisateur (accessible à partir de l’affichage Historique **de la** protection)
- Améliorations des performances & résolutions de bogues

## <a name="1007215"></a>100.72.15

- Correctifs de bogue

## <a name="1007099"></a>100.70.99

- Nous avons résolu un problème qui a une incidence sur la capacité de certains utilisateurs à mettre à niveau vers macOS Ils sont activés lorsque la protection en temps réel est activée. Ce problème ponctuel a été provoqué par microsoft Defender pour le verrouillage des fichiers de point de terminaison dans le package de mise à niveau De base lors de l’analyse des menaces, ce qui a entraîné des échecs dans la séquence de mise à niveau.

## <a name="1006899"></a>100.68.99

- Ajout de la possibilité de configurer la fonctionnalité antivirus pour qu’elle s’exécute [en mode passif](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Améliorations des performances & résolutions de bogues

## <a name="1006528"></a>100.65.28

- Prise en charge supplémentaire de macOS

  > [!CAUTION]
  > macOS 10.15 (Contrôle) contient de nouvelles améliorations en matière de sécurité et de confidentialité. À partir de cette version, par défaut, les applications ne peuvent pas accéder à certains emplacements sur disque (par exemple, Documents, Téléchargements, Bureau, etc.) sans consentement explicite. En l’absence de ce consentement, Microsoft Defender pour le point de terminaison n’est pas en mesure de protéger entièrement votre appareil.
  >
  > Le mécanisme d’octroi de ce consentement dépend de la façon dont vous avez déployé Microsoft Defender pour endpoint :
  >
  > - Pour les déploiements manuels, consultez les instructions mises à jour dans la [rubrique Déploiement](mac-install-manually.md#how-to-allow-full-disk-access) manuel.
  > - Pour les déploiements gérés, consultez les instructions mises à jour dans les rubriques sur le déploiement basé sur [JAMF](mac-install-with-jamf.md) [et Microsoft Intune](mac-install-with-intune.md#create-system-configuration-profiles) de déploiement basé sur jamf.

- Améliorations des performances & résolutions de bogues
