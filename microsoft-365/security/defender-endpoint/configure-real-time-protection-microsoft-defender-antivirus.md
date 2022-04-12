---
title: Activer et configurer des fonctionnalités de protection Antivirus Microsoft Defender
description: Activer et configurer Antivirus Microsoft Defender fonctionnalités de protection en temps réel telles que la surveillance du comportement, l’heuristique et le Machine Learning
keywords: antivirus, protection en temps réel, rtp, machine learning, surveillance du comportement, heuristiques
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.date: 10/22/2021
manager: dansimp
ms.custom: nextgen
ms.collection: M365-security-compliance
ms.openlocfilehash: 744aaa887bfbfafd29b9e3bedb8dc49791b43137
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790171"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Activer et configurer la protection antivirus Microsoft Defender pour qu’il soit toujours activé dans les stratégies de groupe

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

La protection always on se compose de protection en temps réel, de surveillance du comportement et d’heuristiques pour identifier les programmes malveillants basés sur des activités suspectes et malveillantes connues.

Ces activités incluent des événements, tels que des processus qui apportent des modifications inhabituelles aux fichiers existants, la modification ou la création de clés de Registre de démarrage automatique et d’emplacements de démarrage (également appelés points d’extensibilité de démarrage automatique, ou ASEPS), et d’autres modifications apportées au système de fichiers ou à la structure de fichiers.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Activer et configurer la protection always on dans stratégie de groupe

Vous pouvez utiliser **l’éditeur de stratégie de groupe local** pour activer et configurer Antivirus Microsoft Defender paramètres de protection always on.

Pour activer et configurer la protection always on :

1. Ouvrez **l’éditeur de stratégie de groupe local**, comme suit :

    1. Dans votre Windows 10 ou Windows 11 zone de recherche de barre des tâches, tapez **gpedit**.

    2. Sous **Correspondance optimale**, **sélectionnez Modifier la stratégie de groupe** pour lancer **l’éditeur de stratégie de groupe local**.
    
       :::image type="content" source="images/gpedit-search.png" alt-text="Résultat de la recherche dans la barre des tâches GPEdit dans le panneau de configuration" lightbox="images/gpedit-search.png":::

2. Dans le volet gauche de **l’Éditeur de stratégie de groupe local**, développez l’arborescence sur **Modèles** \> d’administration de **configuration** \> par **ordinateur Windows composants** \> **Antivirus Microsoft Defender**.

3. Configurez le paramètre de stratégie de service anti-programme malveillant Antivirus Microsoft Defender.

   Dans le **volet d’informations Antivirus Microsoft Defender** à droite, double-cliquez sur Autoriser le **démarrage du service anti-programme malveillant avec une priorité normale** et **définissez-le sur Activé**.

   Puis sélectionnez **OK**.

4. Configurez les Antivirus Microsoft Defender paramètres de stratégie de protection en temps réel, comme suit :

    1. Dans le **volet d’informations Antivirus Microsoft Defender**, double-cliquez sur **Protection en temps réel**. Ou, dans **l’arborescence Antivirus Microsoft Defender** du volet gauche, sélectionnez **Protection en temps réel**.

    2. Dans le volet Détails de **la protection en temps réel** à droite, double-cliquez sur le paramètre de stratégie spécifié dans [les paramètres de stratégie de protection en temps réel](#real-time-protection-policy-settings) (plus loin dans cet article).

    3. Configurez le paramètre comme il convient, puis sélectionnez **OK**.

    4. Répétez les étapes précédentes pour chaque paramètre du tableau.

5. Configurez le paramètre de stratégie d’analyse Antivirus Microsoft Defender, comme suit :

    1. Dans **l’arborescence Antivirus Microsoft Defender** du volet gauche, sélectionnez **Analyser**.
    
   2. Dans le volet **Détails** de l’analyse à droite, double-cliquez **sur Activer l’heuristique** et **définissez-la sur Activé**. 

   3. Sélectionnez **OK**.

6. Fermez **l’éditeur de stratégie de groupe local**.

### <a name="real-time-protection-policy-settings"></a>Paramètres de stratégie de protection en temps réel

|Paramètres|Valeur par défaut|
|---|---|
|Activer la surveillance du comportement <p> Le moteur antivirus surveille les processus de fichiers, les modifications apportées aux fichiers et au Registre, ainsi que d’autres événements sur vos points de terminaison, en cas d’activité malveillante suspecte et connue.|Activé|
|Analyser tous les fichiers et pièces jointes téléchargés <p> Les fichiers téléchargés et les pièces jointes sont analysés automatiquement. Cette analyse s’ajoute au filtre SmartScreen Windows Defender, qui analyse les fichiers avant et pendant le téléchargement.|Activé|
|Surveiller l’activité des fichiers et des programmes sur votre ordinateur <p> Le moteur de Antivirus Microsoft Defender prend note des modifications apportées aux fichiers (écritures de fichiers, telles que les déplacements, les copies ou les modifications) et de l’activité générale du programme (programmes ouverts ou en cours d’exécution qui entraînent l’exécution d’autres programmes).|Activé|
|Activer les notifications d’écriture de volume brut <p> Les informations sur les écritures de volume brut sont analysées par analyse du comportement.|Activé|
|Activer l’analyse des processus chaque fois que la protection en temps réel est activée <p> Vous pouvez activer indépendamment le moteur Antivirus Microsoft Defender pour analyser les processus en cours d’exécution à la recherche de modifications ou de comportements suspects. Cela est utile si vous avez temporairement désactivé la protection en temps réel et que vous souhaitez analyser automatiquement les processus qui ont démarré alors qu’ils étaient désactivés.|Activé|
|Définir la taille maximale des fichiers téléchargés et des pièces jointes à analyser <p> Vous pouvez définir la taille en kilo-octets.|Activé|
|Configurer le remplacement des paramètres locaux pour activer la surveillance du comportement <p> Configurez un remplacement local pour la configuration de la surveillance du comportement. Ce paramètre ne peut être défini que par stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence locale est prioritaire sur stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, stratégie de groupe aurez la priorité sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement des paramètres locaux pour l’analyse de tous les fichiers téléchargés et pièces jointes <p> Configurez un remplacement local pour la configuration de l’analyse de tous les fichiers et pièces jointes téléchargés. Ce paramètre ne peut être défini que par stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence locale est prioritaire sur stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, stratégie de groupe aurez la priorité sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement des paramètres locaux pour surveiller l’activité de fichier et de programme sur votre ordinateur <p> Configurez un remplacement local pour la configuration de la surveillance de l’activité de fichier et de programme sur votre ordinateur. Ce paramètre ne peut être défini que par stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence locale est prioritaire sur stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, stratégie de groupe aurez la priorité sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement de paramètre local pour activer la protection en temps réel <p> Configurez un remplacement local pour que la configuration active la protection en temps réel. Ce paramètre ne peut être défini que par stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence locale est prioritaire sur stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, stratégie de groupe aurez la priorité sur le paramètre de préférence locale.|Activé|
|Configurer le remplacement des paramètres locaux pour la surveillance de l’activité de fichier entrante et sortante <p> Configurez un remplacement local pour la configuration de la surveillance pour l’activité de fichier entrante et sortante. Ce paramètre ne peut être défini que par stratégie de groupe. Si vous activez ce paramètre, le paramètre de préférence locale est prioritaire sur stratégie de groupe. Si vous désactivez ou ne configurez pas ce paramètre, stratégie de groupe aurez la priorité sur le paramètre de préférence locale.|Activé|
|Configurer la supervision pour l’activité de fichier et de programme entrante et sortante <p> Spécifiez si la surveillance doit se produire sur les directions entrantes, sortantes, les deux ou aucune. Cette action est pertinente pour Windows installations de serveur où vous avez défini des serveurs ou des rôles de serveur spécifiques qui voient de grandes quantités de modifications de fichiers dans une seule direction et que vous souhaitez améliorer les performances réseau. Les points de terminaison (et serveurs) entièrement mis à jour sur un réseau verront peu d’impact sur les performances, quel que soit le nombre ou la direction des modifications apportées aux fichiers.|Activé (dans les deux sens)|

## <a name="disable-real-time-protection-in-group-policy"></a>Désactiver la protection en temps réel dans stratégie de groupe

> [!WARNING]
> La désactivation de la protection en temps réel réduit considérablement la protection sur vos points de terminaison et n’est pas recommandée.

La principale fonctionnalité de protection en temps réel est activée par défaut, mais vous pouvez la désactiver à l’aide de **l’éditeur de stratégie de groupe local**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Pour désactiver la protection en temps réel dans la stratégie de groupe

1. Ouvrez **l’éditeur de stratégie de groupe local**.

   1. Dans votre Windows 10 ou Windows 11 zone de recherche de barre des tâches, tapez **gpedit**.
   2. Sous **Correspondance optimale**, **sélectionnez Modifier la stratégie de groupe** pour lancer **l’éditeur de stratégie de groupe local**.

2. Dans le volet gauche de **l’Éditeur de stratégie de groupe local**, développez l’arborescence sur **Modèles** \> d’administration de **configuration** \> par ordinateur **Windows composants** \> **Antivirus Microsoft Defender** \> **protection en temps réel**.

3. Dans le volet Détails de **la protection en temps** réel à droite, double-cliquez sur **Désactiver la protection en temps réel**.

4. Dans la fenêtre Désactiver le paramètre de **protection en temps réel** , définissez l’option **sur Activé**.
   
5. Sélectionnez **OK**.

6. Fermez **l’éditeur de stratégie de groupe local**.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
