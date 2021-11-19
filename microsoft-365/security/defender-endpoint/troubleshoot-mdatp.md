---
title: Résoudre des problèmes de service avec Microsoft Defender pour point de terminaison
description: Trouvez des solutions et des solutions de contournement aux problèmes connus, tels que les erreurs de serveur lors de la tentative d’accès au service.
keywords: résoudre les problèmes de Microsoft Defender pour le point de terminaison, erreur de serveur, accès refusé, informations d’identification non valides, aucune donnée, portail de tableau de bord, autoriser, observateur d’événements
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: e79fbc82faada816d3499d6f05f285c544002b20
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111230"
---
# <a name="troubleshoot-service-issues"></a>Résoudre des problèmes de service

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft Defender for Endpoint.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Erreur de serveur : l’accès est refusé en raison d’informations d’identification non valides

Si vous rencontrez une erreur de serveur lors de la tentative d’accès au service, vous devez modifier les paramètres de cookie de votre navigateur.
Configurez votre navigateur pour autoriser les cookies.

## <a name="elements-or-data-missing-on-the-portal"></a>Éléments ou données manquants sur le portail

Si certains éléments ou données sont manquants sur Microsoft 365 Defender il est possible que les paramètres proxy le bloquent.

Assurez-vous `*.security.microsoft.com` qu’elle est incluse dans la liste d’attente du proxy.

> [!NOTE]
> Vous devez utiliser le protocole HTTPS lors de l’ajout des points de terminaison suivants.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Le service Microsoft Defender for Endpoint affiche les journaux des événements ou des erreurs dans l’Observateur d’événements

Consultez [la liste des](event-error-codes.md) événements et des erreurs à l’aide de l’Observateur d’événements pour obtenir la liste des ID d’événement signalés par le service Microsoft Defender for Endpoint. L’article contient également les étapes de résolution des erreurs d’événement.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Le service Microsoft Defender for Endpoint ne parvient pas à démarrer après un redémarrage et affiche l’erreur 577

Si l’intégration des appareils se termine correctement, mais que Microsoft Defender pour le point de terminaison ne démarre pas après un redémarrage et affiche l’erreur 577, vérifiez que Windows Defender n’est pas désactivé par une stratégie.

Pour plus d’informations, [voir s’assurer Antivirus Microsoft Defender n’est pas désactivé par la stratégie.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

## <a name="known-issues-with-regional-formats"></a>Problèmes connus avec les formats régionaux

### <a name="date-and-time-formats"></a>Formats de date et d'heure

Il existe des problèmes connus avec les formats d’heure et de date.

Les formats de date suivants sont pris en charge :

- MM/j j/aaie
- dd/MM/yyyy

Les formats de date et d’heure suivants ne sont actuellement pas pris en charge :

- Date au format aaa/MM/j j/j/j j
- Format de date j/MM/aa
- Format de date avec aa. Affiche uniquement yyyy.
- Le format d’heure HH:mm:ss n’est pas pris en charge (le format 12 heures AM/PM n’est pas pris en charge). Seul le format 24 heures est pris en charge.

### <a name="use-of-comma-to-indicate-thousand"></a>Utilisation de virgule pour indiquer un millier

La prise en charge de l’utilisation de la virgule comme séparateur dans les nombres n’est pas prise en charge. Les régions où un nombre est séparé par une virgule pour indiquer un millier ne voient que l’utilisation d’un point comme séparateur. Par exemple, 15 500 000 sont affichés en tant que 15,5 000.

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Le client Microsoft Defender pour point de terminaison a été créé automatiquement en Europe

Lorsque vous utilisez Microsoft Defender pour le Cloud pour surveiller les serveurs, un client Microsoft Defender pour endpoint est automatiquement créé. Les données de Microsoft Defender pour point de terminaison sont stockées en Europe par défaut.

## <a name="related-topics"></a>Sujets connexes

- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
- [Passer en revue les événements et les erreurs à l’aide de l’Observateur d’événements](event-error-codes.md)
