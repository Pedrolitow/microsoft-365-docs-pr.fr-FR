---
title: Évaluer la protection du réseau
description: Découvrez comment fonctionne la protection du réseau en testant les scénarios courants contre qui elle est protégée.
keywords: Protection du réseau, attaques, site web malveillant, ip, domaine, domaines, évaluer, tester, démonstration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 2176fd78f5c355dcb734f2a360ba917c6d130c03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60166503"
---
# <a name="evaluate-network-protection"></a>Évaluer la protection du réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- - [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[La protection du](network-protection.md) réseau empêche les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux qui peuvent héberger des tentatives d’hameçonnage, des attaques et d’autres contenus malveillants sur Internet.

Cet article vous aide à évaluer la protection du réseau en activant la fonctionnalité et en vous guidant vers un site de test. Les sites de cet article d’évaluation ne sont pas malveillants. Ce sont des sites web spécialement créés qui prétendent être malveillants. Le site réplique le comportement qui se produit si un utilisateur a visité un site ou un domaine malveillant.

> [!TIP]
> Vous pouvez également visiter le site Web Microsoft Defender Testground [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour voir comment fonctionnent les autres fonctionnalités de protection.

## <a name="enable-network-protection-in-audit-mode"></a>Activer la protection réseau en mode audit

Activez la protection réseau en mode audit pour voir les adresses IP et les domaines qui auraient été bloqués. Vous pouvez vous assurer qu’elle n’affecte pas les applications métiers ou qu’elle vous donne une idée de la fréquence des blocages.

1. Tapez **powershell** dans la menu Démarrer, cliquez avec le bouton **droit** sur Windows PowerShell puis **sélectionnez Exécuter en tant qu’administrateur**
2. Entrez l’cmdlet suivante :

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Visiter un (faux) domaine malveillant

1. Ouvrez Internet Explorer, Google Chrome ou tout autre navigateur de votre choix.

2. Accédez à [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

La connexion réseau est autorisée et un message de test s’affiche.

![Exemple de notification qui indique connexion bloquée : votre administrateur informatique a Sécurité Windows bloquer cette connexion réseau. Contactez votre service d’aide aux informations.](images/np-notif.png)

> [!NOTE]
> Les connexions réseau peuvent être réussies même si un site est bloqué par la protection réseau. Pour plus d’informations, voir Protection du réseau et protocole d’accès [triple TCP.](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Passer en revue les événements de protection réseau dans Windows’observateur d’événements

Pour passer en revue les applications qui auraient été bloquées, ouvrez l’Observateur d’événements et filtrez l’ID d’événement 1125 dans le journal Microsoft-Windows-Windows-Defender/Opérationnel. Le tableau suivant répertorie tous les événements de protection réseau.

| ID d’événement | Fournir/Source | Description |
|---|---|---|
| 5007 | Windows Defender (opérationnel) | Événement lorsque les paramètres sont modifiés |
| 1125 | Windows Defender (opérationnel) | Événement lors de l’audit d’une connexion réseau |
| 1126 | Windows Defender (opérationnel) | Événement lors du blocage d’une connexion réseau |

## <a name="see-also"></a>Voir aussi

- [Protection du réseau](network-protection.md)

- [Protection du réseau et protocole d’auto-transport TCP triple](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Activer la protection réseau](enable-network-protection.md)

- [Résoudre les problèmes de protection du réseau](troubleshoot-np.md)
