---
title: Évaluer les règles de réduction de la surface d’attaque
description: Découvrez comment la réduction de la surface d’attaque bloquerait et empêcherait les attaques à l’aide de l’outil de démonstration personnalisé.
keywords: Réduction de la surface d’attaque, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, évaluer, tester, démonstration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 07573fd92643ce5fdf3e9140031bf5f15ae8f7aa
ms.sourcegitcommit: 6e5c00f84b5201422aed094f2697016407df8fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51570338"
---
# <a name="evaluate-attack-surface-reduction-rules"></a>Évaluer les règles de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)

Les règles de réduction de la surface d’attaque permettent d’empêcher les actions généralement utilisées par les programmes malveillants pour compromettre les appareils ou les réseaux. Définissez des règles de réduction de la surface d’attaque pour les appareils exécutant l’une des éditions et versions suivantes de Windows :

- Windows 10 Professionnel, [version 1709 ou](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

Découvrez comment évaluer les règles de réduction de la surface d’attaque en activant le mode audit pour tester la fonctionnalité directement dans votre organisation.

> [!TIP]
> Vous pouvez également consulter le site web du scénario de démonstration microsoft Defender pour point de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que la fonctionnalité fonctionne et voir comment elle fonctionne.

## <a name="use-audit-mode-to-measure-impact"></a>Utiliser le mode audit pour mesurer l’impact

Activez les règles de réduction de la surface d’attaque en mode audit pour afficher un enregistrement des applications qui auraient été bloquées si la fonctionnalité était entièrement activée. Testez le fonctionnement de la fonctionnalité dans votre organisation pour vous assurer qu’elle n’affecte pas vos applications métier. Vous pouvez également avoir une idée de la fréquence de tir des règles lors d’une utilisation normale.

Pour activer une règle de réduction de la surface d’attaque en mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Où `<rule ID>` se trouve une valeur GUID de la règle de réduction de la surface [d’attaque](attack-surface-reduction.md#attack-surface-reduction-rules).

Pour activer toutes les règles de réduction de la surface d’attaque ajoutées en mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Si vous souhaitez auditer complètement le fonctionnement des règles de réduction de la surface d’attaque dans votre organisation, vous devez utiliser un outil de gestion pour déployer ce paramètre sur les appareils de votre réseau.

Vous pouvez également utiliser une stratégie de groupe, Intune ou des fournisseurs de services de configuration (CSP) de gestion des périphériques mobiles (CSP) pour configurer et déployer le paramètre. En savoir plus dans l’article principal des règles de [réduction de la surface d’attaque.](attack-surface-reduction.md)

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Passer en revue les événements de réduction de la surface d’attaque dans l’Observateur d’événements Windows

Pour passer en revue les applications qui auraient été bloquées, ouvrez l’Observateur d’événements et filtrez l’ID d’événement 1121 dans le journal microsoft-windows-Windows Defender/opérationnel. Le tableau suivant répertorie tous les événements de protection réseau.

ID de l'événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1121 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode blocage
 1122 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode audit

## <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

Au cours de votre évaluation, vous pouvez configurer chaque règle individuellement ou exclure certains fichiers et processus de l’évaluation par la fonctionnalité.

Voir [Personnaliser les règles de réduction de la surface](customize-attack-surface-reduction.md) d’attaque pour plus d’informations sur la configuration de la fonctionnalité avec les outils de gestion, y compris la stratégie de groupe et les stratégies CSP mdM.

## <a name="see-also"></a>Voir aussi

* [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)
* [Utiliser le mode audit pour évaluer les Windows Defender](audit-windows-defender.md)
* [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md).