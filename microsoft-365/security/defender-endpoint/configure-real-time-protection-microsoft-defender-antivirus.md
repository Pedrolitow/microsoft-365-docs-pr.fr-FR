---
title: Activer et configurer les fonctionnalités Antivirus Microsoft Defender protection des données
description: Activer et configurer des fonctionnalités Antivirus Microsoft Defender protection en temps réel telles que l’analyse du comportement, l’heuristique et l’apprentissage automatique
keywords: antivirus, protection en temps réel, rtp, apprentissage automatique, surveillance du comportement, heuristique
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.date: 07/29/2021
manager: dansimp
ms.custom: nextgen
ms.openlocfilehash: 93a22ef86be7067c8bda955fdfd085f7ef6cbd64
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58568323"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Activer et configurer la protection antivirus Microsoft Defender pour qu’il soit toujours activé dans les stratégies de groupe


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

La protection toujours en cours se compose d’une protection en temps réel, d’une surveillance du comportement et d’une heuristique pour identifier les programmes malveillants en fonction d’activités suspectes et malveillantes connues.

Ces activités incluent des événements, tels que des processus qui modifient inhabituellement des fichiers existants, modifient ou créent des clés de Registre de démarrage automatique et des emplacements de démarrage (également appelés points d’extensibilité de démarrage automatique, ou ASEP), et d’autres modifications apportées au système de fichiers ou à la structure de fichiers.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Activer et configurer la protection toujours active dans la stratégie de groupe

Vous pouvez utiliser **l’Éditeur de stratégie** de groupe local pour activer et configurer Antivirus Microsoft Defender paramètres de protection toujours activés.

Pour activer et configurer la protection toujours active :

1. Ouvrez **l’Éditeur de stratégie de** groupe local, comme suit :

    1. Dans votre zone Windows 10 de recherche de la barre des tâches, tapez **gpedit**.

    2. Sous **La meilleure correspondance,** **sélectionnez Modifier la stratégie de** groupe pour lancer **l’Éditeur de stratégie de groupe local.**
    
       ![Résultat de recherche de la barre des tâches GPEdit.](images/gpedit-search.png)

2. Dans le volet gauche de l’Éditeur de  stratégie de groupe **local,** développez l’arborescence Modèles d’administration de configuration ordinateur \>  \> **Windows composants** \> **Antivirus Microsoft Defender**.

3. Configurez les paramètres Antivirus Microsoft Defender de service anti-programme malveillant, comme suit :

   1. Dans le **Antivirus Microsoft Defender** d’informations à droite, double-cliquez sur le paramètre de stratégie comme indiqué dans le tableau suivant :

      <br>

      ****

      |Paramètre|Valeur par défaut|
      |---|---|
      |Autoriser le démarrage du service anti-programme malveillant avec une priorité normale <p> Vous pouvez réduire la priorité du moteur Antivirus Microsoft Defender de recherche. La réduction de la priorité peut être utile dans les cas où vous souhaitez avoir un processus de démarrage aussi fin que possible ; toutefois, cette action peut affecter la protection des points de terminaison. Procédez avec précaution.|Activé
      |Autoriser le service anti-programme malveillant à rester en cours d’exécution <p> Si les mises à jour de la protection ont été désactivées, vous pouvez configurer Antivirus Microsoft Defender pour qu’elles s’exécutent toujours. La désactivation des mises à jour de la protection réduit la protection des points de terminaison.|Désactivé|
      |

   2. Configurez le paramètre comme il convient, puis sélectionnez **OK.**

   3. Répétez les étapes précédentes pour chaque paramètre du tableau.

4. Configurez les paramètres Antivirus Microsoft Defender stratégie de protection en temps réel, comme suit :

    1. Dans le **Antivirus Microsoft Defender** d’informations, double-cliquez sur **Protection en temps réel.** Ou, dans **l’arborescence Antivirus Microsoft Defender** sur le volet gauche, sélectionnez **Protection en temps réel**.

    2. Dans le **volet** d’informations Protection en temps réel à droite, double-cliquez sur le paramètre de stratégie comme spécifié dans les [paramètres](#real-time-protection-policy-settings) de stratégie de protection en temps réel (plus loin dans cet article).

    3. Configurez le paramètre comme il convient, puis sélectionnez **OK.**

    4. Répétez les étapes précédentes pour chaque paramètre du tableau.

5. Configurez le paramètre de stratégie Antivirus Microsoft Defender’analyse, comme suit :

    1. Dans **l’arborescence Antivirus Microsoft Defender** sur le volet gauche, sélectionnez **Analyse.**
    
       ![Antivirus Microsoft Defender Options d’analyse.](images/gpedit-windows-defender-antivirus-scan.png)

      ![Antivirus Microsoft Defender Options d’analyse](images/gpedit-windows-defender-antivirus-scan.png)

   2. Dans le **volet** Détails de l’analyse à droite, double-cliquez sur le paramètre de stratégie comme indiqué dans le tableau suivant :


      <br>

      ****

      |Paramètre|Valeur par défaut|
      |---|---|
      |Activer l’heuristique <p> La protection heuristique désactive ou bloque les activités suspectes immédiatement avant que le moteur Antivirus Microsoft Defender à détecter l’activité.|Activé|
      |

   3. Configurez le paramètre comme il convient, puis sélectionnez **OK.**

6. Fermez **l’Éditeur de stratégie de groupe local.**

### <a name="real-time-protection-policy-settings"></a>Paramètres de stratégie de protection en temps réel

<br>

****

|Paramètre|Valeur par défaut|
|---|---|
|Activer l’analyse du comportement <p> Le moteur antivirus surveillera les processus de fichiers, les modifications de fichier et de Registre, ainsi que d’autres événements sur vos points de terminaison pour les activités malveillantes suspectes et connues.|Activé|
|Analyser tous les fichiers et pièces jointes téléchargés <p> Les fichiers et pièces jointes téléchargés sont automatiquement analysés. Cette analyse fonctionne en plus du filtre Windows Defender SmartScreen, qui analyse les fichiers avant et pendant le téléchargement.|Activé|
|Surveiller l’activité des fichiers et des programmes sur votre ordinateur <p> Le moteur Antivirus Microsoft Defender prend note des modifications apportées aux fichiers (écritures de fichiers, telles que déplacements, copies ou modifications) et de l’activité générale des programmes (programmes ouverts ou en cours d’exécution et qui entraînent l’exécution d’autres programmes).|Activé|
|Activer les notifications d’écriture de volume brut <p> Les informations sur les écritures de volume brutes seront analysées par la surveillance du comportement.|Activé|
|Activer l’analyse des processus chaque fois que la protection en temps réel est activée <p> Vous pouvez activer indépendamment le moteur de Antivirus Microsoft Defender pour analyser les processus en cours d’exécution pour y trouver des modifications ou des comportements suspects. Cela est utile si vous avez temporairement désactivé la protection en temps réel et que vous souhaitez analyser automatiquement les processus démarrés alors qu’il était désactivé.|Activé|
|Définir la taille maximale des fichiers et pièces jointes téléchargés à scanner <p> Vous pouvez définir la taille en kilo-octets.|Activé|
|Configurer le remplacement de paramètre local pour activer l’analyse du comportement <p> Configurez une substitution locale pour la configuration de la surveillance du comportement. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement de paramètre local pour l’analyse de tous les fichiers et pièces jointes téléchargés <p> Configurez une substitution locale pour la configuration de l’analyse de tous les fichiers et pièces jointes téléchargés. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement des paramètres locaux pour surveiller l’activité des fichiers et des programmes sur votre ordinateur <p> Configurez une substitution locale pour la configuration de la surveillance de l’activité des fichiers et des programmes sur votre ordinateur. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement de paramètre local pour activer la protection en temps réel <p> Configurez une substitution locale pour la configuration afin d’activer la protection en temps réel. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement de paramètre local pour la surveillance de l’activité des fichiers entrants et sortants <p> Configurez une substitution locale pour la configuration de la surveillance de l’activité des fichiers entrants et sortants. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence locale.|Activé|
|Configurer la surveillance pour l’activité des fichiers et des programmes entrants et sortants <p> Spécifiez si la surveillance doit se produire sur les directions entrantes, sortantes, à la fois ou non. Cette action est pertinente pour les installations de Windows Server où vous avez défini des serveurs ou des rôles serveur spécifiques qui voient de grandes quantités de modifications de fichiers dans un seul sens et que vous souhaitez améliorer les performances du réseau. Les points de terminaison (et serveurs) entièrement mis à jour sur un réseau ne voient que peu d’impact sur les performances, quel que soit le nombre ou la direction des modifications apportées aux fichiers.|Activé (dans les deux directions)|
|

## <a name="disable-real-time-protection-in-group-policy"></a>Désactiver la protection en temps réel dans la stratégie de groupe

> [!WARNING]
> La désactivation de la protection en temps réel réduit considérablement la protection sur vos points de terminaison et n’est pas recommandée.

La fonctionnalité de protection en temps réel principale est activée par défaut, mais vous pouvez la désactiver à l’aide de l’Éditeur de stratégie de **groupe local.**

### <a name="to-disable-real-time-protection-in-group-policy"></a>Pour désactiver la protection en temps réel dans la stratégie de groupe

1. Ouvrez **l’Éditeur de stratégie de groupe local.**

   1. Dans votre zone Windows 10 de recherche de la barre des tâches, tapez **gpedit**.
   2. Sous **La meilleure correspondance,** **sélectionnez Modifier la stratégie de** groupe pour lancer **l’Éditeur de stratégie de groupe local.**

2. Dans le volet gauche de l’Éditeur de  stratégie de groupe **local,** développez l’arborescence modèles d’administration de configuration ordinateur \>  \> **Windows composants** Antivirus Microsoft Defender \>  \> **protection en temps réel**.

3. Dans le **volet d’informations Protection** en temps réel à droite, double-cliquez sur Désactiver **la protection en temps réel.**

   ![Désactiver la protection en temps réel.](images/gpedit-turn-off-real-time-protection.png)

4. Dans la **fenêtre Désactiver le paramètre de protection en** temps réel, définissez l’option sur **Activé.**

   ![Désactiver la protection en temps réel activée.](images/gpedit-turn-off-real-time-protection-enabled.png)
   
5. sélectionnez **OK**.

6. Fermez **l’Éditeur de stratégie de groupe local.**

## <a name="see-also"></a>Voir aussi

- [Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
