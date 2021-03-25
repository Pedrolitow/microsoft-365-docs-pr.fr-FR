---
title: Surveillance de la sécurité de navigation web dans Microsoft Defender ATP
description: Utiliser la protection web dans Microsoft Defender ATP pour surveiller la sécurité de navigation web
keywords: protection web, protection contre les menaces web, navigation web, surveillance, rapports, cartes, liste de domaines, sécurité, hameçonnage, programme malveillant, attaque, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 326e508fbf5a0e968e890f5727a6ae542de437c2
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186004"
---
# <a name="monitor-web-browsing-security"></a>Surveiller la sécurité de navigation web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

La protection Web vous permet de surveiller la sécurité de navigation web de votre organisation via des rapports sous Rapports > **protection Web** dans le Centre de sécurité Microsoft Defender. Le rapport contient des cartes qui fournissent des statistiques sur la détection des menaces web.

- Détections de protection contre les **menaces web** au fil du temps : cette carte tendance affiche le nombre de menaces web détectées par type au cours de la période sélectionnée (30 derniers jours, 3 derniers mois, 6 derniers mois)
 
    ![Image de la carte montrant les détections de protection contre les menaces web au fil du temps](images/wtp-blocks-over-time.png)

- **Résumé de la protection** contre les menaces web : cette carte affiche le nombre total de détections de menaces web au cours des 30 derniers jours, montrant la répartition entre les différents types de menaces web. La sélection d’une tranche ouvre la liste des domaines qui ont été trouvés avec des sites web malveillants ou indésirables.

    ![Image de la carte montrant le résumé de la protection contre les menaces web](images/wtp-summary.png)

>[!Note]
>La réflexion d’un bloc dans les cartes ou la liste de domaines peut prendre jusqu’à 12 heures.

## <a name="types-of-web-threats"></a>Types de menaces web

La protection web classe les sites web malveillants et indésirables comme :

- **Hameçonnage :** sites web qui contiennent des formulaires web usurpés et d’autres mécanismes de hameçonnage conçus pour leurre les utilisateurs à divulguer des informations d’identification et d’autres informations sensibles
- **Malveillant :** sites web hébergeant des programmes malveillants et du code d’exploitation
- **Indicateur personnalisé** : sites web dont vous avez ajouté les URL ou les domaines à votre liste d’indicateurs personnalisés [pour](manage-indicators.md) le blocage

## <a name="view-the-domain-list"></a>Afficher la liste des domaines

Sélectionnez une catégorie de menaces web spécifique dans la carte **récapitulative de la protection web** contre les menaces pour ouvrir la page **Domaines.** Cette page affiche la liste des domaines de cette catégorie de menaces. La page fournit les informations suivantes pour chaque domaine :

- **Nombre d’accès** : nombre de demandes d’URL dans le domaine
- **Blocs :** nombre de fois que les demandes ont été bloquées
- **Tendance d’accès** : changement du nombre de tentatives d’accès
- **Catégorie de menace** : type de menace web
- **Appareils** : nombre d’appareils avec tentatives d’accès

Sélectionnez un domaine pour afficher la liste des périphériques qui ont tenté d’accéder aux URL de ce domaine et la liste des URL.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la protection Web](web-protection-overview.md)
- [Filtrage de contenu Web](web-content-filtering.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Répondre aux menaces web](web-protection-response.md)
