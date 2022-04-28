---
title: Nouveautés de Microsoft 365 Defender
description: Répertorie les nouvelles fonctionnalités dans Microsoft 365 Defender
keywords: nouveautés de Microsoft 365 Defender, ga, généralement disponibles, fonctionnalités, disponibles, nouvelles
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 56e22e0525324c59d2d62adaf2325edc3317ccd6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096047"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Nouveautés de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

>Les fonctionnalités suivantes sont disponibles en préversion ou en disponibilité générale dans la dernière version de Microsoft 365 Defender.

Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux :

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, consultez :

- [Nouveautés de Microsoft Defender pour Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Nouveautés dans Microsoft Defender pour point de terminaison](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nouveautés de Microsoft Defender pour Identity](/defender-for-identity/whats-new)
- [Nouveautés de Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

Vous pouvez également obtenir des mises à jour de produit et des notifications importantes via le [centre de messages](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 


## <a name="april-2022"></a>Avril 2022
- (Préversion) [Des actions](advanced-hunting-take-action.md) peuvent désormais être effectuées sur les messages électroniques directement à partir des résultats de la requête de chasse. Les e-mails peuvent être déplacés vers d’autres dossiers ou supprimés définitivement. 

## <a name="march-2022"></a>Mars 2022

- (Préversion) La file d’attente d’incidents a été améliorée avec plusieurs fonctionnalités conçues pour faciliter vos investigations. Les améliorations incluent des fonctionnalités telles que la possibilité de rechercher des incidents par ID ou nom, spécifier un intervalle de temps personnalisé, etc.


## <a name="december-2021"></a>Décembre 2021

- (GA) La `DeviceTvmSoftwareEvidenceBeta` table a été ajoutée à court terme dans la chasse avancée pour vous permettre d’afficher des preuves de l’endroit où un logiciel spécifique a été détecté sur un appareil.

## <a name="november-2021"></a>Novembre 2021

- (Préversion) La fonctionnalité de module complémentaire de gouvernance des applications pour Defender pour le cloud Apps est désormais disponible dans Microsoft 365 Defender. La gouvernance des applications fournit une fonctionnalité de gestion de la sécurité et des stratégies conçue pour les applications compatibles OAuth qui accèdent à des données Microsoft 365 par le biais des API Microsoft Graph. La gouvernance des applications offre une visibilité, une correction et une gouvernance complètes sur la façon dont ces applications et leurs utilisateurs accèdent, utilisent et partagent vos données sensibles stockées dans Microsoft 365 par le biais d’insights actionnables et d’alertes et d’actions de stratégie automatisées. [En savoir plus sur la gouvernance des applications](/cloud-app-security/app-governance-manage-app-governance).
- (Préversion) La page de [chasse avancée](advanced-hunting-overview.md) dispose désormais d’une prise en charge multitab, d’un défilement intelligent, d’onglets de schéma rationalisés, d’options de modification rapide pour les requêtes, d’un indicateur d’utilisation des ressources de requête et d’autres améliorations pour rendre l’interrogation plus fluide et plus facile à affiner.
- (Préversion) Vous pouvez maintenant utiliser le [lien vers la fonctionnalité d’incident](advanced-hunting-link-to-incident.md) pour inclure des événements ou des enregistrements des résultats de la requête de repérage avancé directement dans un incident nouveau ou existant que vous examinez.

## <a name="october-2021"></a>Octobre 2021

- (GA) Dans la recherche avancée, d’autres colonnes ont été ajoutées dans la table [CloudAppEvents](advanced-hunting-cloudappevents-table.md) . Vous pouvez désormais inclure `AccountType`, `IsExternalUser`, `IsImpersonated`, `IPTags`et `IPCategory``UserAgentTags` à vos requêtes.

## <a name="september-2021"></a>Septembre 2021

- (GA) Microsoft Defender pour Office 365 données d’événement sont disponibles dans l’API de streaming d’événements Microsoft 365 Defender. Vous pouvez voir la disponibilité et l’état des types d’événements dans les [types d’événements Microsoft 365 Defender pris en charge dans l’API de streaming](supported-event-types.md).
- (GA) Microsoft Defender pour Office 365 données disponibles dans la chasse avancée sont désormais en disponibilité générale.
- (GA) Attribuer des incidents et des alertes à des comptes d’utilisateur

  Vous pouvez affecter un incident et toutes les alertes qui lui sont associées à un compte d’utilisateur de **Assign to:** dans le volet **Gérer les incidents** d’un incident ou le volet **Gérer les alertes** d’une alerte.

## <a name="august-2021"></a>Août 2021

- (Préversion) Microsoft Defender pour Office 365 données disponibles dans la chasse avancée

  Les nouvelles colonnes des tables de messagerie peuvent fournir des informations supplémentaires sur les menaces basées sur les e-mails pour des investigations plus approfondies à l’aide de la chasse avancée. Vous pouvez maintenant inclure la `AuthenticationDetails` colonne dans [EmailEvents](./advanced-hunting-emailevents-table.md), `FileSize` [dans EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md) et `ThreatTypes` `DetectionMethods` dans les tables [EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md) .

- (Préversion) Graphique des incidents

  Un nouvel onglet **Graph** sous l’onglet **Résumé** d’un incident affiche l’étendue complète de l’attaque, la façon dont l’attaque s’est propagée dans votre réseau au fil du temps, l’endroit où elle a démarré et la distance parcourue par l’attaquant.

## <a name="july-2021"></a>Juillet 2021

- [catalogue de services Professional](https://sip.security.microsoft.com/interoperability/professional_services)

  Améliorez les fonctionnalités de détection, d’investigation et de renseignement sur les menaces de la plateforme avec des connexions partenaires prises en charge.

## <a name="june-2021"></a>Juin 2021

- (Préversion) [Afficher les rapports par balises de menace](threat-analytics.md#view-reports-per-threat-tags)

  Les balises de menace vous permettent de vous concentrer sur des catégories de menaces spécifiques et d’examiner les rapports les plus pertinents.

- (Préversion) [API de diffusion en continu](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender prend en charge la diffusion en continu de tous les événements disponibles via La chasse avancée vers un event Hubs et/ou un compte de stockage Azure.

- (Préversion) [Prendre des mesures dans la chasse avancée](advanced-hunting-take-action.md)

  Contiennent rapidement des menaces ou traitent les ressources compromises que vous trouvez dans la [chasse avancée](advanced-hunting-overview.md).

- (Préversion) [Informations de référence sur le schéma dans le portail](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Obtenez des informations sur les tables de schéma de chasse avancées directement dans le centre de sécurité. Outre les descriptions de table et de colonne, cette référence inclut les types d’événements pris en charge (`ActionType` valeurs) et les exemples de requêtes.

- (Préversion) [Fonction DeviceFromIP()](advanced-hunting-devicefromip-function.md)

  Obtenez des informations sur les appareils auxquels une adresse IP spécifique a été attribuée à un intervalle de temps donné.

## <a name="may-2021"></a>Mai 2021

- [Nouvelle page d’alerte dans le portail Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Fournit des informations améliorées pour le contexte dans une attaque. Vous pouvez voir quelle autre alerte déclenchée a provoqué l’alerte actuelle et toutes les entités et activités affectées impliquées dans l’attaque, y compris les fichiers, les utilisateurs et les boîtes aux lettres. Pour plus d’informations, consultez [Examiner les alertes](/microsoft-365/security/defender/investigate-alerts) .

- [Graphique de tendance pour les incidents et les alertes dans le portail Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Déterminez s’il existe plusieurs alertes pour un seul incident ou si votre organisation est attaquée avec plusieurs incidents différents. Pour plus d’informations, consultez [Hiérarchiser les incidents](/microsoft-365/security/defender/incident-queue) .

## <a name="april-2021"></a>Avril 2021

- Microsoft 365 Defender

  Le portail [Microsoft 365 Defender](https://security.microsoft.com) amélioré est désormais disponible. Cette nouvelle expérience réunit Defender pour point de terminaison, Defender pour Office 365, Defender pour Identity et bien plus encore dans un portail unique. Il s’agit de la nouvelle maison pour gérer vos contrôles de sécurité. [Découvrir les nouveautés](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender rapport d’analyse des menaces](threat-analytics.md)

  L’analytique des menaces vous aide à répondre aux attaques actives et à les réduire. Vous pouvez également en savoir plus sur les tentatives d’attaque bloquées par Microsoft 365 Defender solutions et prendre des mesures préventives qui atténuent le risque d’exposition supplémentaire et augmentent la résilience. Dans le cadre de l’expérience de sécurité unifiée, l’analytique des menaces est désormais disponible pour Microsoft Defender pour point de terminaison et Microsoft Defender pour les titulaires de licences Office E5.

## <a name="march-2021"></a>Mars 2021

- [Table CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  Recherchez des informations sur les événements dans différentes applications et services cloud couverts par Microsoft Cloud App Security. Ce tableau inclut également des informations précédemment disponibles dans la `AppFileEvents` table.

