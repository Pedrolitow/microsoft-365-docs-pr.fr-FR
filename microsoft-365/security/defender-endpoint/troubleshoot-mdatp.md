---
title: Résoudre des problèmes de service avec Microsoft Defender pour point de terminaison
description: Trouvez des solutions et des solutions de contournement aux problèmes connus, tels que les erreurs de serveur lors de la tentative d'accès au service.
keywords: résoudre les problèmes de Microsoft Defender pour le point de terminaison, erreur de serveur, accès refusé, informations d'identification non valides, aucune donnée, portail de tableau de bord, autoriser, observateur d'événements
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 81f1b4154de25f6186679adc5b1f24f78f302415
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933756"
---
# <a name="troubleshoot-service-issues"></a>Résoudre des problèmes de service

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l'expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft Defender - Menace avancée.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Erreur de serveur : l'accès est refusé en raison d'informations d'identification non valides
Si vous rencontrez une erreur de serveur lors de la tentative d'accès au service, vous devez modifier les paramètres de cookie de votre navigateur.
Configurez votre navigateur pour autoriser les cookies.

## <a name="elements-or-data-missing-on-the-portal"></a>Éléments ou données manquants sur le portail
Si certains éléments ou données sont manquants dans le Centre de sécurité Microsoft Defender, il est possible que les paramètres proxy les bloquent.

Assurez-vous `*.securitycenter.windows.com` qu'elle est incluse dans la liste d'attente du proxy.


> [!NOTE]
> Vous devez utiliser le protocole HTTPS lors de l'ajout des points de terminaison suivants.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Le service Microsoft Defender for Endpoint affiche les journaux des événements ou des erreurs dans l'Observateur d'événements

Consultez [la liste](event-error-codes.md) des événements et des erreurs à l'aide de l'Observateur d'événements pour obtenir la liste des ID d'événement signalés par le service Microsoft Defender for Endpoint. L'article contient également les étapes de résolution des erreurs d'événement.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Le service Microsoft Defender for Endpoint ne parvient pas à démarrer après un redémarrage et affiche l'erreur 577

Si l'intégration des appareils se termine correctement, mais que Microsoft Defender pour le point de terminaison ne démarre pas après un redémarrage et affiche l'erreur 577, vérifiez que Windows Defender n'est pas désactivé par une stratégie.

Pour plus d'informations, [voir s'assurer que l'Antivirus Microsoft Defender n'est pas désactivé par la stratégie.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

## <a name="known-issues-with-regional-formats"></a>Problèmes connus avec les formats régionaux

**Formats de date et d'heure**<br>
Il existe des problèmes connus avec les formats d'heure et de date. 

Les formats de date suivants sont pris en charge :
- MM/j j/aaie
- dd/MM/yyyy

Les formats de date et d'heure suivants ne sont actuellement pas pris en charge :
- Date au format aaa/MM/j/s
- Format de date j/MM/aa
- Format de date avec yy. Affiche uniquement yyyy.
- Le format d'heure HH:mm:ss n'est pas pris en charge (le format 12 heures AM/PM n'est pas pris en charge). Seul le format 24 heures est pris en charge.

**Utilisation de la virgule pour indiquer un millier**<br>
La prise en charge de l'utilisation de la virgule comme séparateur dans les nombres n'est pas prise en charge. Les régions où un nombre est séparé par une virgule pour indiquer un millier ne voient que l'utilisation d'un point comme séparateur. Par exemple, 15 500 000 sont affichés en tant que 15,5 000.

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Le client Microsoft Defender pour point de terminaison a été créé automatiquement en Europe
Lorsque vous utilisez Azure Defender pour surveiller les serveurs, un client Microsoft Defender pour Endpoint est automatiquement créé. Les données de Microsoft Defender pour point de terminaison sont stockées en Europe par défaut.





## <a name="related-topics"></a>Voir aussi
- [Résoudre les problèmes d'intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
- [Passer en revue les événements et les erreurs à l'aide de l'Observateur d'événements](event-error-codes.md)
