---
title: Résoudre des problèmes de service avec Microsoft Defender pour point de terminaison
description: Recherchez des solutions et des solutions de contournement aux problèmes connus tels que les erreurs de serveur lors de la tentative d’accès au service.
keywords: résoudre les problèmes Microsoft Defender pour point de terminaison, erreur de serveur, accès refusé, informations d’identification non valides, aucune donnée, portail de tableau de bord, autoriser, observateur d’événements
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: troubleshooting
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 94e4fc6130e35097c7cae1f01ef00b5b706977d7
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233791"
---
# <a name="troubleshoot-service-issues"></a>Résoudre des problèmes de service

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Cette section traite des problèmes qui peuvent survenir lorsque vous utilisez le service Microsoft Defender pour point de terminaison.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Erreur du serveur : l’accès est refusé en raison d’informations d’identification non valides

Si vous rencontrez une erreur de serveur lors de la tentative d’accès au service, vous devez modifier les paramètres de cookie de votre navigateur.
Configurez votre navigateur pour autoriser les cookies.

## <a name="elements-or-data-missing-on-the-portal"></a>Éléments ou données manquants sur le portail

Si certains éléments ou données sont manquants sur Microsoft 365 Defender il est possible que les paramètres de proxy le bloquent.

Assurez-vous qu’il `*.security.microsoft.com` est inclus dans la liste verte du proxy.

> [!NOTE]
> Vous devez utiliser le protocole HTTPS lors de l’ajout des points de terminaison suivants.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Microsoft Defender pour point de terminaison service affiche les journaux des événements ou des erreurs dans le observateur d'événements

Consultez [Vérifier les événements et les erreurs à l’aide de observateur d'événements](event-error-codes.md) pour obtenir la liste des ID d’événements signalés par le service Microsoft Defender pour point de terminaison. L’article contient également des étapes de résolution des erreurs d’événement.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Microsoft Defender pour point de terminaison service ne démarre pas après un redémarrage et affiche l’erreur 577

Si l’intégration des appareils se termine correctement, mais que Microsoft Defender pour point de terminaison ne démarre pas après un redémarrage et affiche l’erreur 577, vérifiez que Windows Defender n’est pas désactivé par une stratégie.

Pour plus d’informations, consultez [Vérifier que Microsoft Defender Antivirus n’est pas désactivé par la stratégie](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="known-issues-with-regional-formats"></a>Problèmes connus avec les formats régionaux

### <a name="date-and-time-formats"></a>Formats de date et d'heure

Il existe des problèmes connus avec les formats d’heure et de date.

Les formats de date suivants sont pris en charge :

- MM/dd/aaaa
- dd/MM/aaaa

Les formats de date et d’heure suivants ne sont actuellement pas pris en charge :

- Format de date aaaa/MM/jj
- Format de date dd/MM/yy
- Format de date avec yy. Affichera seulement yyyyy.
- Le format heure HH:mm:ss n’est pas pris en charge (le format 12 heures AM/PM n’est pas pris en charge). Seul le format 24 heures est pris en charge.

### <a name="use-of-comma-to-indicate-thousand"></a>Utilisation de virgules pour indiquer des milliers

La prise en charge de l’utilisation de virgules comme séparateur dans les nombres n’est pas prise en charge. Les régions où un nombre est séparé par une virgule pour indiquer mille, verront uniquement l’utilisation d’un point comme séparateur. Par exemple, 15,5 K s’affiche sous la forme de 15,5 K.

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Microsoft Defender pour point de terminaison locataire a été automatiquement créé en Europe

Lorsque vous utilisez Microsoft Defender pour le cloud pour surveiller les serveurs, un locataire Microsoft Defender pour point de terminaison est automatiquement créé. Les données Microsoft Defender pour point de terminaison sont stockées en Europe par défaut.

## <a name="related-topics"></a>Voir aussi

- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
- [Examiner les événements et les erreurs à l’aide de observateur d'événements](event-error-codes.md)
