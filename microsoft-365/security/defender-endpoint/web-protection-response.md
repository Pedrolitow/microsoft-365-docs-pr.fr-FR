---
title: Répondre aux menaces web dans Microsoft Defender pour point de terminaison
description: Répondez aux alertes liées à des sites web malveillants et indésirables. Comprendre comment la protection contre les menaces web informe les utilisateurs finaux par le biais de leurs navigateurs web et notifications Windows
keywords: protection web, protection contre les menaces web, navigation web, alertes, réponse, sécurité, hameçonnage, programmes malveillants, exploit, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web, notifications, utilisateurs finaux, notifications Windows, page de blocage,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: d46400787d98cf3bf7620ae9003b9fd47e581381
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68644150"
---
# <a name="respond-to-web-threats"></a>Répondre aux menaces web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

La protection web dans Microsoft Defender pour point de terminaison vous permet d’examiner et de répondre efficacement aux alertes liées aux sites web malveillants dans votre liste d’indicateurs personnalisés.

## <a name="view-web-threat-alerts"></a>Afficher les alertes de menace web

Microsoft Defender pour point de terminaison génère les [alertes suivantes pour une](manage-alerts.md) activité web malveillante ou suspecte :

- **Connexion suspecte bloquée par la protection réseau** : cette alerte est générée lorsqu’une tentative d’accès à un site web malveillant ou à un site web dans votre liste d’indicateurs personnalisés est *arrêtée* par la protection réseau en mode *bloc*
- **Connexion suspecte détectée par la protection réseau** : cette alerte est générée lorsqu’une tentative d’accès à un site web malveillant ou à un site web dans votre liste d’indicateurs personnalisés est détectée par la protection réseau en mode *audit uniquement*

Chaque alerte fournit les informations suivantes :

- Appareil qui a tenté d’accéder au site web bloqué
- Application ou programme utilisé pour envoyer la requête web
- URL ou URL malveillante dans la liste des indicateurs personnalisés
- Actions recommandées pour les répondeurs

:::image type="content" source="images/wtp-alert.png" alt-text="Alerte liée à la protection contre les menaces web" lightbox="images/wtp-alert.png":::

> [!NOTE]
> Pour réduire le volume d’alertes, Microsoft Defender pour point de terminaison consolide les détections de menaces web pour le même domaine sur le même appareil chaque jour en une seule alerte. Une seule alerte est générée et comptabilisée dans le [rapport de protection web](web-protection-monitoring.md).

## <a name="inspect-website-details"></a>Inspecter les détails du site web

Vous pouvez approfondir votre travail en sélectionnant l’URL ou le domaine du site web dans l’alerte. Cette opération ouvre une page sur cette URL ou domaine particulier avec diverses informations, notamment :

- Appareils qui ont tenté d’accéder au site web
- Incidents et alertes liés au site web
- Fréquence d’affichage du site web dans les événements de votre organisation

  :::image type="content" source="images/wtp-website-details.png" alt-text="Page de détails de l’entité de domaine ou d’URL" lightbox="images/wtp-website-details.png":::

[En savoir plus sur les pages d’URL ou d’entité de domaine](investigate-domain.md)

## <a name="inspect-the-device"></a>Inspecter l’appareil

Vous pouvez également vérifier l’appareil qui a tenté d’accéder à une URL bloquée. La sélection du nom de l’appareil sur la page d’alerte ouvre une page contenant des informations complètes sur l’appareil.

[En savoir plus sur les pages d’entité d’appareil](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>Navigateur web et notifications Windows pour les utilisateurs finaux

Avec la protection web dans Microsoft Defender pour point de terminaison, vos utilisateurs finaux ne peuvent pas visiter des sites web malveillants ou indésirables à l’aide de Microsoft Edge ou d’autres navigateurs. Étant donné que le blocage est effectué par [la protection réseau](network-protection.md), une erreur générique s’affiche à partir du navigateur web. Ils verront également une notification de Windows.

:::image type="content" source="images/wtp-browser-blocking-page.png" alt-text="Microsoft Edge affichant une erreur 403 et la notification Windows" lightbox="images/wtp-browser-blocking-page.png":::

*Menace web bloquée sur Microsoft Edge*

:::image type="content" source="images/wtp-chrome-browser-blocking-page.png" alt-text="Navigateur web Chrome affichant un avertissement de connexion sécurisée et la notification Windows" lightbox="images/wtp-chrome-browser-blocking-page.png":::
*Menace web bloquée sur Chrome*

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Filtrage du contenu web](web-content-filtering.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
