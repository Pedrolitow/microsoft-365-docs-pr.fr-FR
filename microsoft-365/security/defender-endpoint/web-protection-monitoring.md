---
title: Surveillance de la sécurité de navigation web dans Microsoft Defender pour point de terminaison
description: Utiliser la protection web dans Microsoft Defender pour point de terminaison pour surveiller la sécurité de la navigation web
keywords: protection web, protection contre les menaces web, navigation web, surveillance, rapports, cartes, liste de domaines, sécurité, hameçonnage, programmes malveillants, exploit, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web
search.appverid: met150
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
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: ec3cadaa674311f19a08d1455293649c84e84962
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233461"
---
# <a name="monitor-web-browsing-security"></a>Surveiller la sécurité de la navigation web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

La protection web vous permet de surveiller la sécurité de la navigation web de votre organisation par le biais de rapports sous **Rapports > protection web** dans le portail Microsoft 365 Defender. Le rapport contient des cartes qui fournissent des statistiques de détection des menaces web.

- **Détections de protection contre les menaces web au fil du temps** : cette carte de tendance affiche le nombre de menaces web détectées par type pendant la période sélectionnée (30 derniers jours, 3 derniers mois, 6 derniers mois)

  :::image type="content" source="images/wtp-blocks-over-time.png" alt-text="Carte affichant les détections de protection contre les menaces web au fil du temps" lightbox="images/wtp-blocks-over-time.png":::

- **Résumé de la protection contre les menaces web** : cette carte affiche le nombre total de détections de menaces web au cours des 30 derniers jours, montrant la distribution entre les différents types de menaces web. La sélection d’une tranche ouvre la liste des domaines qui ont été trouvés avec des sites web malveillants ou indésirables.

  :::image type="content" source="images/wtp-summary.png" alt-text="Carte affichant le résumé de la protection contre les menaces web"  lightbox="images/wtp-summary.png":::

> [!NOTE]
> Il peut prendre jusqu’à 12 heures avant qu’un bloc ne soit reflété dans les cartes ou la liste de domaines.

## <a name="types-of-web-threats"></a>Types de menaces web

La protection web classe les sites web malveillants et indésirables comme suit :

- **Hameçonnage** : sites web contenant des formulaires web usurpés et d’autres mécanismes de hameçonnage conçus pour inciter les utilisateurs à divulguer des informations d’identification et d’autres informations sensibles
- **Malveillants** : sites web hébergeant des programmes malveillants et exploitant du code
- **Indicateur personnalisé** : sites web dont vous avez ajouté des URL ou des domaines à votre [liste d’indicateurs personnalisés](manage-indicators.md) à des fins de blocage

## <a name="view-the-domain-list"></a>Afficher la liste des domaines

Sélectionnez une catégorie de menace web spécifique dans la carte **récapitulative** de la protection contre **les menaces** web pour ouvrir la page Domaines. Cette page affiche la liste des domaines sous cette catégorie de menace. La page fournit les informations suivantes pour chaque domaine :

- **Nombre d’accès** : nombre de demandes d’URL dans le domaine
- **Blocs** : nombre de fois où les demandes ont été bloquées
- **Tendance d’accès** : modification du nombre de tentatives d’accès
- **Catégorie de menace** - type de menace web
- **Appareils** : nombre d’appareils ayant des tentatives d’accès

Sélectionnez un domaine pour afficher la liste des appareils qui ont tenté d’accéder aux URL de ce domaine et la liste des URL.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Filtrage du contenu web](web-content-filtering.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Répondre aux menaces web](web-protection-response.md)
