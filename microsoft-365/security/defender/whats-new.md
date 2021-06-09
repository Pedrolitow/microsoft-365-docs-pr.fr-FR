---
title: Nouveautés de Microsoft 365 Defender
description: Répertorie les nouvelles fonctionnalités de Microsoft 365 Defender
keywords: nouveautés de Microsoft 365 Defender, ga, généralement disponibles, fonctionnalités, disponibles, nouvelles
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: c974701b83fbb6dbcac1cc597578a97144b2b482
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52845593"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Nouveautés de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Les fonctionnalités suivantes sont généralement disponibles dans la dernière version de Microsoft 365 Defender.

Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et en coller l’URL suivante dans votre lecteur de flux :
```http
/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

## <a name="april-2021"></a>Avril 2021
- Centre de sécurité Microsoft 365 amélioré <br> Le [Centre de sécurité Microsoft 365](https://security.microsoft.com) est à présent disponible en préversion publique. Cette nouvelle expérience introduit Defender pour point de terminaison, Defender pour Office 365, Microsoft 365 Defender et bien plus encore dans le Centre de sécurité Microsoft 365. Il s’agit du nouvel accueil pour gérer vos contrôles de sécurité. [Découvrir les nouveautés](./overview-security-center.md).

- [Microsoft 365 Rapport d’analyse des menaces Defender](threat-analytics.md)<br>
 L’analyse des menaces vous permet de répondre et de minimiser l’impact des attaques actives. Vous pouvez également en savoir plus sur les tentatives d’attaques bloquées par les solutions Microsoft 365 Defender et prendre des mesures préventives qui atténuent les risques d’exposition supplémentaire et augmentent la résilience. Dans le cadre de l’expérience de sécurité unifiée, l’analyse des menaces est désormais disponible pour Microsoft Defender pour Endpoint et Microsoft Defender pour les titulaires Office licence E5.

## <a name="march-2021"></a>9 mars 2021
- [Table CloudAppEvents](advanced-hunting-cloudappevents-table.md) <br>Trouvez des informations sur les événements dans différents services et applications cloud couverts par Microsoft Cloud App Security. Ce tableau inclut également des informations précédemment disponibles dans `AppFileEvents` .
## <a name="february-2021"></a>Février 2021
- (Aperçu) Le centre [de sécurité Microsoft 365 https://security.microsoft.com) amélioré (est](https://security.microsoft.com) désormais disponible en prévisualisation publique). Cette nouvelle expérience place Defender pour Point de terminaison et Defender pour Office 365 au centre. [Découvrez les modifications](./overview-security-center.md).

## <a name="september-2020"></a>Septembre 2020
- [Table IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) <br> Rechercher les événements impliquant un contrôleur de domaine local exécutant Active Directory (AD). Ce [tableau de schéma de](advanced-hunting-overview.md) recherche avancé couvre une plage d’événements liés à l’identité et d’événements système sur le contrôleur de domaine.
- [Fonction AssignedIPAddresses()](advanced-hunting-assignedipaddresses-function.md) <br> Utilisez cette fonction dans vos requêtes de recherche avancées pour obtenir rapidement les dernières adresses IP attribuées à un appareil ou les adresses IP les plus récentes à partir d’une heure spécifique.

## <a name="july-2020"></a>Juillet 2020
- [Fonction FileProfile()](advanced-hunting-fileprofile-function.md) <br> Utilisez cette fonction dans vos requêtes de recherche avancées pour enrichir les résultats avec des informations complètes sur les fichiers.
- [Tables d’identité et d’application](advanced-hunting-schema-tables.md)<br> Obtenez une visibilité sur les événements d’authentification, les requêtes Active Directory et l’activité liée aux applications avec les tables [IdentityLogonEvents,](advanced-hunting-identitylogonevents-table.md) [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)et [AppFileEvents](advanced-hunting-appfileevents-table.md) dans le schéma de recherche avancé.
- [Accédez à la recherche](advanced-hunting-go-hunt.md)<br> Faites rapidement pivoter de l’investigation d’un incident à l’inspection d’un événement spécifique, d’un utilisateur, d’un appareil ou d’autres types d’entités sur le chasse avancée.

## <a name="june-2020"></a>Juin 2020
- Flux Twitter <br> Obtenez les dernières recherches sur la sécurité, l’intelligence des menaces, les actualités sur les produits, etc. directement dans le tableau de bord.
- [Table de schéma EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) <br> Incorporez des informations sur les actions de post-remise prises sur les messages électroniques dans vos requêtes de recherche avancées.
- [Inspecter les enregistrements dans le hunting avancé](advanced-hunting-query-results.md#drill-down-from-query-results) <br> Examinez rapidement les enregistrements dans les résultats de votre requête avec le nouveau panneau d’informations.

## <a name="may-2020"></a>Mai 2020
- [Détections personnalisées](custom-detections-overview.md) <br> Utilisez des requêtes de repérage avancé pour créer des règles de détection personnalisées qui surveillent automatiquement les événements de sécurité et les états système et y répondent.

## <a name="february-2020"></a>Février 2020
- [Incidents](incidents-overview.md) <br> Connaissez exactement l’endroit où une attaque a commencé et d’autres détails pour vous aider à voir l’étendue de l’attaque.
- [Examen et réponse automatisés](m365d-autoir.md) <br> AIR permet à l’équipe en charge des opérations de sécurité d’augmenter considérablement la capacité de votre organisation à gérer les alertes et incidents de sécurité.
- [Améliorations avancées du chasse](advanced-hunting-overview.md) <br> Recherchez de manière proactive les menaces dans l’espace de travail moderne avec kusto query Language et un schéma optimisé pour la sécurité.

## <a name="march-2019"></a>Mars 2019
- Repérage avancé <br> Page d’accueil de différentes fonctionnalités de recherche qui vous permet de rechercher de manière proactive les menaces qui affectent le courrier électronique, les données, les appareils et les identités.
- [Niveau de sécurité Microsoft](microsoft-secure-score.md) <br> Mesure de la posture de sécurité d’une organisation, avec un nombre plus élevé indiquant d’autres actions d’amélioration prises. En suivant les recommandations du Score de sécurité, vous pouvez protéger votre organisation contre les menaces. 
- [Rapports](overview-security-center.md) <br>  Propose une série de cartes couvrant différents domaines que les analystes et les administrateurs de sécurité s’en sentent dans le cadre de leurs opérations quotidiennes.
