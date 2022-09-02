---
title: Évaluer la protection du réseau
description: Découvrez le fonctionnement de la protection réseau en testant les scénarios courants auxquels elle protège.
keywords: Protection réseau, exploits, site web malveillant, ip, domaine, domaines, évaluer, tester, démonstration
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection:
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: e5de5ac54678d6c56dbcd190ddd6e06381a758c9
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67523223"
---
# <a name="evaluate-network-protection"></a>Évaluer la protection du réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[La protection réseau](network-protection.md) permet d’empêcher les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet.

Cet article vous aide à évaluer la protection réseau en activant la fonctionnalité et en vous guidant vers un site de test. Les sites de cet article d’évaluation ne sont pas malveillants. Ce sont des sites web spécialement créés qui prétendent être malveillants. Le site répliquera le comportement qui se produirait si un utilisateur visitait un site ou un domaine malveillant.

## <a name="enable-network-protection-in-audit-mode"></a>Activer la protection réseau en mode audit

Activez la protection réseau en mode audit pour voir quelles adresses IP et domaines auraient été bloqués. Vous pouvez vous assurer qu’il n’affecte pas les applications métier ou vous faire une idée de la fréquence à laquelle les blocs se produisent.

1. Tapez **PowerShell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**
2. Entrez l’applet de commande suivante :

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Visiter un (faux) domaine malveillant

1. Ouvrez Internet Explorer, Google Chrome ou tout autre navigateur de votre choix.

2. Accédez à [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

    La connexion réseau est autorisée et un message de test s’affiche.
    
    :::image type="content" source="images/np-notif.png" alt-text="Notification de blocage de connexion" lightbox="images/np-notif.png":::

> [!NOTE]
> Les connexions réseau peuvent réussir même si un site est bloqué par la protection réseau. Pour plus d’informations, consultez [la protection réseau et l’établissement d’une liaison TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake) triple.

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans Windows observateur d'événements

Pour examiner les applications qui auraient été bloquées, ouvrez observateur d'événements et filtrez l’ID d’événement 1125 dans le journal Microsoft-Windows-Windows Defender/Operational. Le tableau suivant répertorie tous les événements de protection réseau.

| ID d’événement | Fournir/Source | Description |
|---|---|---|
| 5007 | Windows Defender (opérationnel) | Événement lorsque les paramètres sont modifiés |
| 1125 | Windows Defender (opérationnel) | Événement lors de l’audit d’une connexion réseau |
| 1126 | Windows Defender (opérationnel) | Événement lorsqu’une connexion réseau est bloquée |

## <a name="see-also"></a>Voir aussi

- [Protection du réseau](network-protection.md)

- [Protection réseau et liaison TCP triple](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Activer la protection réseau](enable-network-protection.md)

- [Résoudre les problèmes de protection réseau](troubleshoot-np.md)
