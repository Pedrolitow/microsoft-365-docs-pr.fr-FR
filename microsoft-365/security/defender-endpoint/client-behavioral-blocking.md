---
title: Blocage comportemental du client
description: Le blocage du comportement client fait partie des fonctionnalités de blocage et de blocage du comportement dans Microsoft Defender pour point de terminaison
keywords: blocage comportemental, protection rapide, comportement du client, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.custom:
- next-gen
- edr
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: 9a2fa36d7902c66e1ac40f0ecd07c0db38752e8d
ms.sourcegitcommit: 346c1332e1e9eebb5c90d6b8553dd70fcabf530a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53567499"
---
# <a name="client-behavioral-blocking"></a>Blocage comportemental du client

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Présentation

Le blocage du comportement client est un composant [des](behavioral-blocking-containment.md) fonctionnalités de blocage et de blocage du comportement dans Defender pour point de terminaison. Lorsque des comportements suspects sont détectés sur des appareils (également appelés clients ou points de terminaison), les artefacts (tels que les fichiers ou applications) sont bloqués, vérifiés et corrigés automatiquement. 

:::image type="content" alt-text="Protection du cloud et du client" source="images/pre-execution-and-post-execution-detection-engines.png" lightbox="images/pre-execution-and-post-execution-detection-engines.png":::

La protection antivirus fonctionne mieux lorsqu’elle est couplée à la protection cloud.

## <a name="how-client-behavioral-blocking-works"></a>Fonctionnement du blocage du comportement client

[Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md) détecter des comportements suspects, du code malveillant, des attaques sans fichier et en mémoire, et bien plus encore sur un appareil. Lorsque des comportements suspects sont détectés, Antivirus Microsoft Defender surveille et envoie ces comportements suspects et leurs arbre de processus au service de protection cloud. L’apprentissage automatique différencie les applications malveillantes et les comportements de qualité en millisecondes et classifie chaque artefact. En temps quasi réel, dès qu’un artefact est trouvé malveillant, il est bloqué sur l’appareil. 

Chaque fois qu’un comportement [](alerts-queue.md) suspect est détecté, une alerte est générée et visible dans le portail [Microsoft 365 Defender](microsoft-defender-security-center.md) (anciennement Microsoft 365 Defender).

Le blocage du comportement client est efficace, car il permet non seulement d’empêcher le démarrage d’une attaque, mais également d’arrêter une attaque qui a commencé à s’exécuter. En outre, avec [le blocage de boucle de](feedback-loop-blocking.md) commentaires (autre fonctionnalité de blocage et de blocage du comportement), les attaques sont empêchées sur d’autres appareils de votre organisation.

## <a name="behavior-based-detections"></a>Détections basées sur le comportement

Les détections basées sur le comportement sont nommées en fonction de la matrice [MITRE ATT&CK pour Enterprise](https://attack.mitre.org/matrices/enterprise). La convention d’attribution de noms permet d’identifier la phase d’attaque où le comportement malveillant a été observé :

|Tactique | Nom de la menace de détection |
|----|----|
|Accès initial | `Behavior:Win32/InitialAccess.*!ml` |
|Exécution | `Behavior:Win32/Execution.*!ml` |
|Persistance | `Behavior:Win32/Persistence.*!ml` |
|Réaffectation des privilèges | `Behavior:Win32/PrivilegeEscalation.*!ml` |
|Fraude à la défense | `Behavior:Win32/DefenseEvasion.*!ml` |
|Accès informations d'identification | `Behavior:Win32/CredentialAccess.*!ml` |
|Discovery | `Behavior:Win32/Discovery.*!ml` |
|Mouvement latéral | `Behavior:Win32/LateralMovement.*!ml` |
|Collection | `Behavior:Win32/Collection.*!ml` |
|Commande et contrôle | `Behavior:Win32/CommandAndControl.*!ml` |
|Exfiltration | `Behavior:Win32/Exfiltration.*!ml` |
|Impact | `Behavior:Win32/Impact.*!ml` |
|Non catégorisé | `Behavior:Win32/Generic.*!ml` |

> [!TIP]
> Pour en savoir plus sur les menaces spécifiques, consultez **[l’activité récente des menaces globales.](https://www.microsoft.com/wdsi/threats)**

## <a name="configuring-client-behavioral-blocking"></a>Configuration du blocage du comportement client

Si votre organisation utilise Defender pour endpoint, le blocage du comportement client est activé par défaut. Toutefois, pour bénéficier de toutes les fonctionnalités de Defender pour point de terminaison, y compris le blocage du comportement et le [contenu,](behavioral-blocking-containment.md)assurez-vous que les fonctionnalités et fonctionnalités suivantes de Defender pour point de terminaison sont activées et configurées :

- [Lignes de base de Defender pour les points de terminaison](configure-machines-security-baseline.md)

- [Appareils intégrés à Defender pour le point de terminaison](onboard-configure.md)

- [PEPT en mode blocage](edr-in-block-mode.md)

- [Réduction de la surface d’attaque](attack-surface-reduction.md)

- [Protection nouvelle génération](configure-microsoft-defender-antivirus-features.md) (antivirus, logiciel anti-programme malveillant et autres fonctionnalités de protection contre les menaces)
