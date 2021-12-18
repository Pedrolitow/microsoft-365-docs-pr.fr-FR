---
title: Évaluer les règles de réduction de la surface d’attaque
description: Découvrez comment la réduction de la surface d’attaque bloquerait et empêcherait les attaques à l’aide de l’outil de démonstration personnalisé.
keywords: Réduction de la surface d’attaque, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, évaluer, tester, démonstration
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.topic: article
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 1f6479f3bbf6f636298858d50938846cfddca101
ms.sourcegitcommit: 59b1b0abfde30a8f2d8210b696aac3dc9183544e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2021
ms.locfileid: "61566638"
---
# <a name="evaluate-attack-surface-reduction-rules"></a>Évaluer les règles de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Les règles de réduction de la surface d’attaque permettent d’empêcher les actions généralement utilisées par les programmes malveillants pour compromettre les appareils ou les réseaux. Les règles de réduction de la surface d’attaque permettent de fermer la plupart des points d’entrée courants utilisés par les programmes malveillants et les ransomware.

Définissez des règles de réduction de la surface d’attaque pour les appareils exécutant l’une des éditions et versions de Windows :

- Windows 10 Professionnel, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- Windows Server 2022

> [!Note]
> Les règles de réduction de la surface d’attaque Windows Server 2012 R2 et Windows Server 2016 sont disponibles à l’aide du package de solution unifiée moderne. Pour plus d’informations, voir Nouvelle fonctionnalité dans la solution unifiée moderne pour [Windows 2012 R2 et 2016 Preview](configure-server-endpoints.md#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview) dans la rubrique Intégrer des serveurs Windows au [service Microsoft Defender for Endpoint.](configure-server-endpoints.md)
Voir aussi Microsoft Defender pour le point de terminaison : [Defender Windows Server 2012 R2 et 2016](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defending-windows-server-2012-r2-and-2016/ba-p/2783292).

Découvrez comment évaluer les règles de réduction de la surface d’attaque en [activant](audit-windows-defender.md) le mode audit pour tester la fonctionnalité directement dans votre organisation.

> [!TIP]
> Vous pouvez également consulter le site web du scénario de démonstration microsoft Defender pour point de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que la fonctionnalité fonctionne et voir comment elle fonctionne.

## <a name="use-audit-mode-to-measure-impact"></a>Utiliser le mode audit pour mesurer l’impact

Activez les règles de réduction de la surface d’attaque en mode audit pour afficher un enregistrement des applications qui auraient été bloquées si la fonctionnalité était entièrement activée. Testez le fonctionnement de la fonctionnalité dans votre organisation pour vous assurer qu’elle n’affecte pas vos applications métier. Vous pouvez également avoir une idée de la fréquence de tir des règles lors d’une utilisation normale.

Pour activer une règle de réduction de la surface d’attaque en mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Où `<rule ID>` se trouve une valeur GUID de la règle de réduction de la surface [d’attaque](attack-surface-reduction-rules-reference.md).

Pour activer toutes les règles de réduction de la surface d’attaque ajoutées en mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Si vous souhaitez auditer entièrement le fonctionnement des règles de réduction de la surface d’attaque dans votre organisation, vous devez utiliser un outil de gestion pour déployer ce paramètre sur les appareils de votre réseau.

Vous pouvez également utiliser une stratégie de groupe, Intune ou des fournisseurs de services de configuration (CSP) de gestion des périphériques mobiles (CSP) pour configurer et déployer le paramètre. En savoir plus dans l’article principal des règles de [réduction de la surface d’attaque.](attack-surface-reduction.md)

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Passer en revue les événements de réduction de la surface d’Windows l’Observateur d’événements

Pour passer en revue les applications qui auraient été bloquées, ouvrez l’Observateur d’événements et filtrez l’ID d’événement 1121 dans le journal microsoft-Windows-Windows Defender/opérationnel. Le tableau suivant répertorie tous les événements de protection réseau.

ID d’événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1121 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode blocage
 1122 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode audit

## <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

Au cours de votre évaluation, vous pouvez configurer chaque règle individuellement ou exclure certains fichiers et processus de l’évaluation par la fonctionnalité.

Voir [Personnaliser les règles de réduction de la surface](customize-attack-surface-reduction.md) d’attaque pour plus d’informations sur la configuration de la fonctionnalité à l’aide des outils de gestion, y compris la stratégie de groupe et les stratégies CSP mdM.

## <a name="see-also"></a>Voir aussi

- [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)
- [Utiliser le mode audit pour évaluer les Windows Defender](audit-windows-defender.md)
- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md)
