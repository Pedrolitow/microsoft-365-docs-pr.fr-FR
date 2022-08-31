---
title: Blocage comportemental du client
description: Le blocage comportemental du client fait partie des fonctionnalités de blocage comportemental et d’endiguement à Microsoft Defender pour point de terminaison
keywords: blocage comportemental, protection rapide, comportement du client, Microsoft Defender pour point de terminaison
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.collection: m365-security-compliance
ms.subservice: mde
ms.openlocfilehash: 3947d29b4115c2f08e57aab26de951b733762c07
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67480622"
---
# <a name="client-behavioral-blocking"></a>Blocage comportemental du client

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateforme**
- Windows

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Vue d’ensemble

Le blocage comportemental du client est un composant des [fonctionnalités de blocage comportemental et d’endiguement](behavioral-blocking-containment.md) dans Defender pour point de terminaison. Lorsque des comportements suspects sont détectés sur les appareils (également appelés clients ou points de terminaison), les artefacts (tels que les fichiers ou les applications) sont bloqués, vérifiés et corrigés automatiquement.

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="Protection du cloud et du client" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

La protection antivirus fonctionne mieux lorsqu’elle est associée à la protection cloud.

## <a name="how-client-behavioral-blocking-works"></a>Fonctionnement du blocage comportemental du client

[L’Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) peut détecter les comportements suspects, le code malveillant, les attaques sans fichier et en mémoire, et bien plus encore sur un appareil. Lorsque des comportements suspects sont détectés, l’Antivirus Microsoft Defender surveille et envoie ces comportements suspects et leurs arborescences de processus au service de protection cloud. Le Machine Learning fait la distinction entre les applications malveillantes et les bons comportements en quelques millisecondes, et classifie chaque artefact. En quasi temps réel, dès qu’un artefact est détecté comme malveillant, il est bloqué sur l’appareil.

Chaque fois qu’un comportement suspect est détecté, une [alerte](alerts-queue.md) est générée et est visible pendant que l’attaque a été détectée et arrêtée ; Les alertes, telles qu’une « alerte d’accès initial », sont déclenchées et apparaissent dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) (anciennement Microsoft 365 Defender).

Le blocage comportemental du client est efficace, car il permet non seulement d’empêcher le démarrage d’une attaque, mais aussi d’arrêter une attaque qui a commencé à s’exécuter. De plus, avec le [blocage de boucle de commentaires](feedback-loop-blocking.md) (une autre fonctionnalité de blocage comportemental et d’endiguement), les attaques sont empêchées sur d’autres appareils de votre organisation.

## <a name="behavior-based-detections"></a>Détections basées sur le comportement

Les détections basées sur le comportement sont nommées en fonction du [MITRE ATT&matrice CK pour Entreprise](https://attack.mitre.org/matrices/enterprise). La convention d’affectation de noms permet d’identifier l’étape d’attaque où le comportement malveillant a été observé :

|Tactique|Nom de la menace de détection|
|---|---|
|Accès initial|`Behavior:Win32/InitialAccess.*!ml`|
|Exécution|`Behavior:Win32/Execution.*!ml`|
|Persistance|`Behavior:Win32/Persistence.*!ml`|
|Réaffectation des privilèges|`Behavior:Win32/PrivilegeEscalation.*!ml`|
|Fraude à la défense|`Behavior:Win32/DefenseEvasion.*!ml`|
|Accès informations d'identification|`Behavior:Win32/CredentialAccess.*!ml`|
|Discovery|`Behavior:Win32/Discovery.*!ml`|
|Mouvement latéral|`Behavior:Win32/LateralMovement.*!ml`|
|Collection|`Behavior:Win32/Collection.*!ml`|
|Commande et contrôle|`Behavior:Win32/CommandAndControl.*!ml`|
|Exfiltration|`Behavior:Win32/Exfiltration.*!ml`|
|Impact|`Behavior:Win32/Impact.*!ml`|
|Uncategorized|`Behavior:Win32/Generic.*!ml`|

> [!TIP]
> Pour en savoir plus sur des menaces spécifiques, consultez **[l’activité récente sur les menaces globales](https://www.microsoft.com/wdsi/threats)**.

## <a name="configuring-client-behavioral-blocking"></a>Configuration du blocage comportemental du client

Si votre organisation utilise Defender pour point de terminaison, le blocage comportemental du client est activé par défaut. Toutefois, pour tirer parti de toutes les fonctionnalités de Defender pour point de terminaison, y compris le [blocage comportemental et l’endiguement](behavioral-blocking-containment.md), assurez-vous que les fonctionnalités et fonctionnalités suivantes de Defender pour point de terminaison sont activées et configurées :

- [Lignes de base de Defender pour point de terminaison](configure-machines-security-baseline.md)
- [Appareils intégrés à Defender pour point de terminaison](onboard-configure.md)
- [PEPT en mode blocage](edr-in-block-mode.md)
- [Réduction de la surface d’attaque](attack-surface-reduction.md)
- [Protection de nouvelle génération](configure-microsoft-defender-antivirus-features.md) (antivirus, logiciel anti-programme malveillant et autres fonctionnalités de protection contre les menaces)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
