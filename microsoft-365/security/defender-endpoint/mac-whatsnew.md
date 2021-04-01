---
title: Nouveautés de Microsoft Defender pour Endpoint pour Mac
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour Endpoint pour Mac.
keywords: microsoft, defender, atp, mac, installation, macos, whatsnew
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 16d78cf014e775ecb98a59d90b5734836eb3cbf2
ms.sourcegitcommit: 7b8104015a76e02bc215e1cf08069979c70650ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51476624"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-for-mac"></a>Nouveautés de Microsoft Defender pour Endpoint pour Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!IMPORTANT]
> Sur macOS 11 (Big Sur), Microsoft Defender for Endpoint nécessite des profils de configuration supplémentaires. Si vous êtes un client existant en cours de mise à niveau à partir de versions antérieures de macOS, veillez à déployer les profils de configuration supplémentaires répertoriés sur [cette page.](mac-sysext-policies.md)

> [!IMPORTANT]
> La prise en charge de macOS 10.13 (High Sierra) a été interrompue le 15 février 2021.

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

- Ajout d’un nouveau commutateur de ligne de commande pour désactiver l’extension réseau : `mdatp system-extension network-filter disable` . Cette commande peut être utile pour résoudre les problèmes réseau qui peuvent être liés à Microsoft Defender pour Point de terminaison pour Mac
- Améliorations des performances & résolutions de bogues

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Résolutions de bogues

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Amélioration de la fiabilité de l’agent lors de l’exécution sur macOS 11 Big Sur
- Ajout d’un nouveau commutateur de ligne de commande ( ) pour ignorer les exclusions antivirus lors des `--ignore-exclusions` analyses personnalisées ( `mdatp scan custom` )
- Améliorations des performances & résolutions de bogues

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Conditions supprimées lorsque Microsoft Defender pour le point de terminaison déclenchant un bogue macOS 11 (Big Sur) qui se manifeste en noyau
- Correction d’une fuite de mémoire dans l’extension du système de sécurité des points de terminaison lors de l’exécution sur mac 11 (Big Sur)
- Résolutions de bogues

## <a name="1011072"></a>101.10.72

- Résolutions de bogues

## <a name="1010961"></a>101.09.61

- Ajout d’une nouvelle préférence gérée pour [désactiver l’option d’envoi de commentaires](mac-preferences.md#show--hide-option-to-send-feedback)
- L’icône du menu État affiche désormais un état sain lorsque les paramètres du produit sont gérés. Auparavant, l’icône du menu d’état affichait un état d’avertissement ou d’erreur, même si les paramètres du produit étaient gérés par l’administrateur.
- Améliorations des performances & résolutions de bogues

## <a name="1010950"></a>101.09.50

- Cette version du produit a été validée sur macOS Big Sur 11 bêta 9

- La nouvelle syntaxe de `mdatp` l’outil en ligne de commande est désormais la syntaxe par défaut. Pour plus d’informations sur la nouvelle syntaxe, voir [Resources for Microsoft Defender for Endpoint for Mac](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > L’ancienne syntaxe de l’outil de ligne de commande sera supprimée du produit le **1er janvier 2021.**

- Étendu avec un nouveau paramètre ( ) qui permet d’enregistrer les journaux de diagnostic dans `mdatp diagnostic create` `--path [directory]` un autre répertoire
- Améliorations des performances & résolutions de bogues

## <a name="1010949"></a>101.09.49

- Améliorations apportées à l’interface utilisateur pour différencier les exclusions gérées par l’administrateur informatique des exclusions définies par l’utilisateur local
- Amélioration de l’utilisation du processeur lors des analyses à la demande
- Améliorations des performances & résolutions de bogues

## <a name="1010723"></a>101.07.23

- Ajout de nouveaux champs à la sortie de la vérification de l’état du mode passif et de l’ID de groupe `mdatp --health` EDR

  > [!NOTE]
  > `mdatp --health` sera remplacé par `mdatp health` dans une prochaine mise à jour du produit.

- Correction d’un bogue dans lequel l’envoi automatique d’échantillons n’a pas été marqué comme géré dans l’interface utilisateur
- Ajout de nouveaux paramètres pour contrôler la rétention des éléments dans l’historique d’analyse antivirus. Vous pouvez désormais [spécifier le nombre](mac-preferences.md#antivirus-scan-history-retention-in-days) de jours de rétention des éléments dans l’historique d’analyse et spécifier le nombre maximal d’éléments [dans l’historique d’analyse.](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Résolutions de bogues

## <a name="1010663"></a>101.06.63

- Nous avons résolu une régression des performances introduite dans la `101.05.17` version. La régression a été introduite avec le correctif pour éliminer les noyaux que certains clients ont observés lors de l’accès aux partages SMB. Nous avons revenir à ce changement de code et nous sommes en train d’examiner d’autres façons d’éliminer les noyaux.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Nous travaillons sur une syntaxe nouvelle et améliorée pour `mdatp` l’outil en ligne de commande. La nouvelle syntaxe est actuellement la valeur par défaut dans les canaux de mise à jour Insider Fast et Insider Slow. Nous vous encourageons à vous familiariser avec cette nouvelle syntaxe.
> 
> Nous continuerons à assurer la prise en charge de l’ancienne syntaxe parallèlement à la nouvelle syntaxe et nous fournirons davantage de communication autour du plan de désaprétation de l’ancienne syntaxe dans les mois à venir.

- Nous avons résolu un problème de noyau qui se produisait parfois lors de l’accès aux partages de fichiers SMB
- Améliorations des performances & résolutions de bogues

## <a name="1010516"></a>101.05.16

- Améliorations apportées à la logique d’analyse rapide pour réduire considérablement le nombre de fichiers analysés
- Ajout de la prise en charge [de lacompletion](mac-resources.md#how-to-enable-autocompletion) automatique pour l’outil en ligne de commande
- Résolutions de bogues

## <a name="1010312"></a>101.03.12

- Améliorations des performances & résolutions de bogues

## <a name="1010154"></a>101.01.54

- Améliorations en matière de compatibilité avec Time Machine
- Améliorations en matière d’accessibilité
- Améliorations des performances & résolutions de bogues

## <a name="1010031"></a>101.00.31

- Amélioration de [l’expérience d’intégration de produit pour les utilisateurs d’Intune](https://docs.microsoft.com/mem/intune/apps/apps-advanced-threat-protection-macos)
- Les [exclusions antivirus désormais prise en charge les caractères génériques](mac-exclusions.md#supported-exclusion-types)
- Ajout de la possibilité de déclencher des analyses antivirus à partir du menu contextuel macOS. Vous pouvez maintenant cliquer avec le bouton droit sur un fichier ou un dossier dans finder et sélectionner **Analyser avec Microsoft Defender pour le point de terminaison**
- Les rétrogradations de produits sur place sont désormais explicitement interdits par le programme d’installation. Si vous devez rétrograder, désinstallez d’abord la version existante et reconfigurez votre appareil.
- Autres améliorations en matière de performances & résolutions de bogues

## <a name="1009027"></a>100.90.27

- Vous pouvez désormais [définir un canal de mise](mac-updates.md#set-the-channel-name) à jour pour Microsoft Defender pour Point de terminaison pour Mac différent du canal de mise à jour à l’échelle du système
- Icône Nouveau produit
- Autres améliorations de l’expérience utilisateur
- Résolutions de bogues

## <a name="1008692"></a>100.86.92

- Améliorations en matière de compatibilité avec Time Machine
- Nous avons résolu un problème dans lequel le produit n’était parfois pas en train de nettoyer tous les fichiers pendant `/Library/Application Support/Microsoft/Defender` la désinstallation
- Réduction de l’utilisation processeur du produit lorsque les produits Microsoft sont mis à jour via la mise à jour automatique Microsoft
- Autres améliorations en matière de performances & résolutions de bogues

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> Pour garantir la protection la plus complète pour vos appareils macOS et en adéquation avec l’arrêt par Apple de la distribution de mises à jour de sécurité natives macOS aux versions de système d’exploitation antérieures à [actuel – 2], le déploiement et les mises à jour MDATP pour Mac ne seront plus pris en charge sur macOS Sierra [10.12]. Les mises à jour et améliorations de MDATP pour Mac seront apportées aux appareils exécutant les versions Derline [10.15], Mojave [10.14] et High Sierra [10.13]. 
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

- Résolutions de bogues

## <a name="1007942"></a>100.79.42

- Correction d’un problème dans lequel Microsoft Defender pour point de terminaison pour Mac interfère parfois avec Time Machine
- Ajout d’un nouveau commutateur à l’utilitaire de ligne de commande pour tester la connectivité avec le service back-end
  ```bash
  mdatp connectivity test
  ```
- Possibilité supplémentaire d’afficher l’historique complet des menaces dans l’interface utilisateur (accessible à partir de l’affichage Historique **de la** protection)
- Améliorations des performances & résolutions de bogues

## <a name="1007215"></a>100.72.15

- Résolutions de bogues

## <a name="1007099"></a>100.70.99

- Nous avons résolu un problème qui a un impact sur la capacité de certains utilisateurs à mettre à niveau vers macOS Ils sont activés lorsque la protection en temps réel est activée. Ce problème ponctuel a été provoqué par microsoft Defender pour le verrouillage des fichiers de point de terminaison dans le package de mise à niveau De base lors de l’analyse des menaces, ce qui a entraîné des échecs dans la séquence de mise à niveau.

## <a name="1006899"></a>100.68.99

- Ajout de la possibilité de configurer la fonctionnalité antivirus pour qu’elle s’exécute en [mode passif](mac-preferences.md#enable--disable-passive-mode)
- Améliorations des performances & résolutions de bogues

## <a name="1006528"></a>100.65.28

- Prise en charge supplémentaire de macOS

  > [!CAUTION]
  > macOS 10.15 (Contrôle) contient de nouvelles améliorations en matière de sécurité et de confidentialité. À partir de cette version, par défaut, les applications ne peuvent pas accéder à certains emplacements sur le disque (par exemple, Documents, Téléchargements, Bureau, etc.) sans consentement explicite. En l’absence de ce consentement, Microsoft Defender pour le point de terminaison n’est pas en mesure de protéger entièrement votre appareil.
  >
  > Le mécanisme d’octroi de ce consentement dépend de la façon dont vous avez déployé Microsoft Defender pour endpoint :
  >
  > - Pour les déploiements manuels, consultez les instructions mises à jour dans la [rubrique Déploiement](mac-install-manually.md#how-to-allow-full-disk-access) manuel.
  > - Pour les déploiements gérés, consultez les instructions mises à jour dans les rubriques sur le déploiement basé sur [JAMF](mac-install-with-jamf.md) et [microsoft Intune.](mac-install-with-intune.md#create-system-configuration-profiles)

- Améliorations des performances & résolutions de bogues
