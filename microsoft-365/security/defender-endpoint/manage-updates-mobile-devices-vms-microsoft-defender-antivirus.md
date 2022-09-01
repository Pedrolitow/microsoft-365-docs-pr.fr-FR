---
title: Définir la façon dont les appareils mobiles sont mis à jour par l’Antivirus Microsoft Defender
description: Gérez la façon dont les appareils mobiles, tels que les ordinateurs portables, doivent être mis à jour avec les mises à jour de protection antivirus Microsoft Defender.
keywords: mises à jour, protection, planification des mises à jour, batterie, appareil mobile, ordinateur portable, notebook, opt-in, microsoft update, wsus, override
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 97e8d573e6d03e25ecec4d9e038f831687443524
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67514338"
---
# <a name="manage-updates-for-mobile-devices-and-virtual-machines-vms"></a>Gérer les mises à jour pour les appareils mobiles et les machines virtuelles

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Les appareils mobiles et les machines virtuelles peuvent nécessiter davantage de configuration pour garantir que les performances ne sont pas affectées par les mises à jour.

Deux paramètres sont utiles pour ces appareils :

- Accepter Microsoft Update sur les ordinateurs mobiles sans connexion WSUS
- Empêcher les mises à jour du renseignement de sécurité lors de l’exécution sur batterie

Les articles suivants peuvent également être utiles dans les situations suivantes :
- [Configuration des analyses planifiées et de rattrapage](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Guide de déploiement de l’antivirus Microsoft Defender dans un environnement VDI (Virtual Desktop Infrastructure)](deployment-vdi-microsoft-defender-antivirus.md)

## <a name="opt-in-to-microsoft-update-on-mobile-computers-without-a-wsus-connection"></a>Accepter Microsoft Update sur les ordinateurs mobiles sans connexion WSUS

Vous pouvez utiliser Microsoft Update pour maintenir les informations de sécurité sur les appareils mobiles exécutant l’Antivirus Microsoft Defender à jour lorsqu’ils ne sont pas connectés au réseau d’entreprise ou n’ont pas de connexion WSUS.

Cela signifie que les mises à jour de protection peuvent être remises aux appareils (via Microsoft Update) même si vous avez défini WSUS pour remplacer Microsoft Update.

Vous pouvez choisir Microsoft Update sur l’appareil mobile de l’une des manières suivantes :

- Modifiez le paramètre avec stratégie de groupe.
- Utilisez un VBScript pour créer un script, puis exécutez-le sur chaque ordinateur de votre réseau.
- Choisissez manuellement chaque ordinateur de votre réseau via le menu **Paramètres** .

### <a name="use-group-policy-to-opt-in-to-microsoft-update"></a>Utiliser stratégie de groupe pour choisir Microsoft Update

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Sélectionnez **Stratégies** , puis **Modèles d’administration**.

4. Développez l’arborescence sur **les composants** \> Windows Mises à jour **de signature** **antivirus** \> Microsoft Defender.

5. Définissez **Autoriser les mises à jour du renseignement de sécurité de Microsoft Update** sur **Activé**, puis sélectionnez  **OK**.

### <a name="use-a-vbscript-to-opt-in-to-microsoft-update"></a>Utiliser un VBScript pour choisir Microsoft Update

1. Suivez les instructions de l’article MSDN [Sur l’acceptation de Microsoft Update](/windows/win32/wua_sdk/opt-in-to-microsoft-update) pour créer VBScript.

2. Exécutez le VBScript que vous avez créé sur chaque ordinateur de votre réseau.

### <a name="manually-opt-in-to-microsoft-update"></a>Accepter manuellement Microsoft Update

1. Ouvrez **Windows Update** dans **Mettre à jour &** paramètres de sécurité sur l’ordinateur sur lequel vous souhaitez participer.

2. Sélectionnez **Options avancées** .

3. Activez la case à cocher **Donner des mises à jour pour d’autres produits Microsoft lorsque je met à jour Windows**.

## <a name="prevent-security-intelligence-updates-when-running-on-battery-power"></a>Empêcher les mises à jour du renseignement de sécurité lors de l’exécution sur batterie

Vous pouvez configurer l’antivirus Microsoft Defender pour télécharger uniquement les mises à jour de protection lorsque le PC est connecté à une source d’alimentation câblée.

### <a name="use-group-policy-to-prevent-security-intelligence-updates-on-battery-power"></a>Utiliser stratégie de groupe pour empêcher les mises à jour du renseignement de sécurité sur la batterie

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), choisissez l’objet stratégie de groupe que vous souhaitez configurer et ouvrez-le pour modification.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Sélectionnez **Stratégies** , puis **Modèles d’administration**.

4. Développez l’arborescence sur **les composants** \> Windows microsoft **Defender Antivirus** \> **Signature Mises à jour**, puis **définissez Autoriser les mises à jour du renseignement de sécurité lors de l’exécution sur batterie sur** **Désactivé**. Puis sélectionnez **OK**.

Cette action empêche le téléchargement des mises à jour de protection lorsque le PC est sous batterie.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Mettre à jour et gérer l’antivirus Microsoft Defender dans Windows 10](deploy-manage-report-microsoft-defender-antivirus.md)