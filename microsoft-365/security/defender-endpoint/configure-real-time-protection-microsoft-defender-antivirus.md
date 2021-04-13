---
title: Activer et configurer les fonctionnalités de protection de l'Antivirus Microsoft Defender
description: Activer et configurer les fonctionnalités de protection en temps réel de l'Antivirus Microsoft Defender, telles que la surveillance du comportement, l'heuristique et l'apprentissage automatique
keywords: antivirus, protection en temps réel, rtp, apprentissage automatique, surveillance du comportement, heuristique
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 12/16/2019
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.openlocfilehash: 7fa4f90282bf87c1def1917037e090b213cad3db
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690327"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Activer et configurer la protection toujours active de l'Antivirus Microsoft Defender dans la stratégie de groupe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

La protection toujours en cours se compose d'une protection en temps réel, d'une surveillance du comportement et d'une heuristique pour identifier les programmes malveillants en fonction d'activités suspectes et malveillantes connues.

Ces activités incluent des événements, tels que des processus qui modifient inhabituellement des fichiers existants, modifient ou créent des clés de Registre de démarrage automatique et des emplacements de démarrage (également appelés points d'extensibilité de démarrage automatique, ou ASEP), et d'autres modifications apportées au système de fichiers ou à la structure de fichiers.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Activer et configurer la protection toujours active dans la stratégie de groupe

Vous pouvez utiliser **l'Éditeur de stratégie** de groupe local pour activer et configurer les paramètres de protection toujours active de l'Antivirus Microsoft Defender.

Pour activer et configurer la protection toujours active :

1. Ouvrez **l'Éditeur de stratégie de groupe local.** Pour ce faire :  

    1. Dans votre zone de recherche de la barre des tâches Windows 10, tapez **gpedit**.
    
    1. Sous **Meilleure correspondance,** cliquez **sur Modifier la stratégie de** groupe pour lancer **l'Éditeur de stratégie de groupe local.**
    
       ![Résultat de recherche de la barre des tâches GPEdit](images/gpedit-search.png)

2. Dans le volet gauche de l'Éditeur de stratégie de groupe **local,** développez l'arborescence Modèles d'administration de **configuration** ordinateur  >    >  **Composants**  >  **Microsoft Defender Antivirus .** 

3. Configurez les paramètres de stratégie du service anti-programme malveillant de l'Antivirus Microsoft Defender. Pour ce faire :  

    1. Dans le **volet d'informations** de l'Antivirus Microsoft Defender à droite, double-cliquez sur le paramètre de stratégie comme indiqué dans le tableau suivant :

       | Paramètre | Description | Valeur par défaut |
       |-----------------------------|------------------------|-------------------------------|
       | Autoriser le démarrage du service anti-programme malveillant avec une priorité normale | Vous pouvez réduire la priorité du moteur antivirus Microsoft Defender, ce qui peut être utile dans les déploiements légers dans lesquels vous souhaitez avoir un processus de démarrage aussi léger que possible. Cela peut avoir un impact sur la protection sur le point de terminaison. | Activé
       | Autoriser le service anti-programme malveillant à rester toujours en cours d'exécution | Si les mises à jour de la protection ont été désactivées, vous pouvez configurer l'Antivirus Microsoft Defender pour qu'il s'exécute toujours. Cela réduit la protection sur le point de terminaison. | Désactivé |
    
    1. Configurez le paramètre selon le cas, puis cliquez sur **OK.**
    
    1. Répétez les étapes précédentes pour chaque paramètre du tableau.

4. Configurez les paramètres de stratégie de protection en temps réel de l'Antivirus Microsoft Defender. Pour ce faire :

    1. Dans le **volet d'informations** de l'Antivirus Microsoft Defender, double-cliquez sur **Protection en temps réel.** Sinon, dans **l'arborescence de l'Antivirus Microsoft Defender** dans le volet gauche, cliquez sur Protection en temps **réel.**
    
    1. Dans le **volet d'informations Protection** en temps réel à droite, double-cliquez sur le paramètre de stratégie comme indiqué dans le tableau suivant :  

       | Paramètre | Description | Valeur par défaut |
       |-----------------------------|------------------------|-------------------------------|
       | Activer l'analyse du comportement | Le moteur antivirus surveille les processus de fichiers, les modifications de fichier et de Registre, ainsi que d'autres événements sur vos points de terminaison pour les activités malveillantes suspectes et connues. | Activé |
       | Analyser tous les fichiers et pièces jointes téléchargés | Les fichiers et pièces jointes téléchargés sont automatiquement analysés. Cela s'ajoute au filtre Windows Defender SmartScreen, qui analyse les fichiers avant et pendant le téléchargement. | Activé |
       | Surveiller l'activité des fichiers et des programmes sur votre ordinateur | Le moteur de l'Antivirus Microsoft Defender prend note des modifications apportées aux fichiers (écritures de fichiers, telles que déplacements, copies ou modifications) et de l'activité générale des programmes (programmes ouverts ou en cours d'exécution et qui entraînent l'exécution d'autres programmes). | Activé |
       | Activer les notifications d'écriture de volume brut | Les informations sur les écritures de volume brutes seront analysées par la surveillance du comportement. | Activé |
       | Activer l'analyse des processus chaque fois que la protection en temps réel est activée | Vous pouvez activer indépendamment le moteur antivirus Microsoft Defender pour analyser les processus en cours d’exécution pour y trouver des modifications ou des comportements suspects. Cela est utile si vous avez temporairement désactivé la protection en temps réel et que vous souhaitez analyser automatiquement les processus démarrés alors qu’il était désactivé. | Activé |
       | Définir la taille maximale des fichiers et pièces jointes téléchargés à scanner | Vous pouvez définir la taille en kilo-octets. | Activé |
       | Configurer le remplacement de paramètre local pour activer l’analyse du comportement | Configurez une substitution locale pour la configuration de la surveillance du comportement. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence local.| Activé |
       | Configurer le remplacement de paramètre local pour l’analyse de tous les fichiers et pièces jointes téléchargés | Configurez une substitution locale pour la configuration de l’analyse de tous les fichiers et pièces jointes téléchargés. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence local.| Activé |
       | Configurer le remplacement des paramètres locaux pour surveiller l’activité des fichiers et des programmes sur votre ordinateur | Configurez une substitution locale pour la configuration de la surveillance de l’activité des fichiers et des programmes sur votre ordinateur. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence local.| Activé |
       | Configurer le remplacement de paramètre local pour activer la protection en temps réel | Configurez une substitution locale pour la configuration afin d'activer la protection en temps réel. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence local.| Activé |
       | Configurer le remplacement de paramètre local pour la surveillance de l'activité des fichiers entrants et sortants | Configurez une substitution locale pour la configuration de la surveillance de l'activité des fichiers entrants et sortants. Ce paramètre ne peut être définie que par la stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence local sera prioritaire sur la stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, la stratégie de groupe sera prioritaire sur le paramètre de préférence locale. | Activé |
       | Configurer la surveillance de l'activité des fichiers et des programmes entrants et sortants | Spécifiez si la surveillance doit se produire sur les directions entrantes, sortantes, à la fois ou non. Cela est pertinent pour les installations De Windows Server où vous avez défini des serveurs ou des rôles serveur spécifiques qui voient de grandes quantités de modifications de fichiers dans un seul sens et que vous souhaitez améliorer les performances du réseau. Les points de terminaison (et serveurs) entièrement mis à jour sur un réseau n'auront que peu d'impact sur les performances, quel que soit le nombre ou la direction des modifications de fichier. | Activé (dans les deux directions) |

    1. Configurez le paramètre comme il convient, puis cliquez sur **OK**.
    
    1. Répétez les étapes précédentes pour chaque paramètre du tableau.

5. Configurez le paramètre de stratégie d'analyse de l'Antivirus Microsoft Defender. Pour ce faire :  

    1. Dans **l'arborescence de l'Antivirus Microsoft Defender** dans le volet gauche, cliquez sur **Analyser.**
    
       ![Options d'analyse antivirus Microsoft Defender](images/gpedit-windows-defender-antivirus-scan.png)

    1. Dans le **volet** Détails de l'analyse à droite, double-cliquez sur le paramètre de stratégie comme indiqué dans le tableau suivant :

       | Paramètre | Description | Valeur par défaut |
       |-----------------------------|------------------------|-------------------------------|    
       | Activer l'heuristique | La protection heuristique désactive ou bloque les activités suspectes immédiatement avant que le moteur antivirus Microsoft Defender ne soit invité à détecter l'activité. | Activé |

    1. Configurez le paramètre selon le cas, puis cliquez sur **OK.**
    
6. Fermez **l'Éditeur de stratégie de groupe local.**


## <a name="disable-real-time-protection-in-group-policy"></a>Désactiver la protection en temps réel dans la stratégie de groupe

> [!WARNING]
> La désactivation de la protection en temps réel réduit considérablement la protection sur vos points de terminaison et n'est pas recommandée.

La fonctionnalité de protection en temps réel principale est activée par défaut, mais vous pouvez la désactiver à l'aide de l'Éditeur de stratégie de groupe **local.**

Pour désactiver la protection en temps réel dans la stratégie de groupe :

1. Ouvrez **l'Éditeur de stratégie de groupe local.**

   1. Dans votre zone de recherche de la barre des tâches Windows 10, tapez **gpedit**.
   
   1. Sous **Meilleure correspondance,** cliquez **sur Modifier la stratégie de** groupe pour lancer **l'Éditeur de stratégie de groupe local.**

2.  Dans le volet gauche de l'Éditeur de stratégie de groupe **local,** développez l'arborescence Modèles d'administration de **configuration** ordinateur  >    >  **Composants**  >  **Microsoft Defender Antivirus**  >  **Real-time Protection**.

3. Dans le **volet d'informations Protection** en temps réel à droite, double-cliquez sur Désactiver **la protection en temps réel.**

   ![Désactiver la protection en temps réel](images/gpedit-turn-off-real-time-protection.png)

4. Dans la **fenêtre Désactiver le paramètre de protection en** temps réel, définissez l'option sur **Activé.**

   ![Désactiver la protection en temps réel activée](images/gpedit-turn-off-real-time-protection-enabled.png)
   
5. Cliquez sur **OK**.

6. Fermez **l'Éditeur de stratégie de groupe local.**

## <a name="related-articles"></a>Articles connexes

- [Configurer la protection comportementale, heuristique et en temps réel](configure-protection-features-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)