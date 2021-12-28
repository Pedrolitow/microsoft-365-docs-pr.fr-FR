---
title: Nouveautés de Microsoft 365 Defender
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: f7c41ff83bffaa6c0e982f4dc0dd3c36e614c0fb
ms.sourcegitcommit: f8fbabf1ec7421cd7ad36aa52b8856fb863cf284
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/28/2021
ms.locfileid: "61620455"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Nouveautés de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> Voulez-vous faire l'expérience de Microsoft 365 Defender? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Les fonctionnalités suivantes sont en prévisualisation ou généralement disponibles dans la dernière version de Microsoft 365 Defender.

Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et en coller l’URL suivante dans votre lecteur de flux :
```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Pour plus d’informations sur les nouveautés des autres produits de sécurité Microsoft Defender, voir :

- [Nouveautés de Microsoft Defender pour Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Nouveautés dans Microsoft Defender pour point de terminaison](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nouveautés de Microsoft Defender pour l’identité](/defender-for-identity/whats-new)
- [Nouveautés de la Microsoft Cloud App Security](/cloud-app-security/release-notes)

## <a name="december-2021"></a>Décembre 2021
- (Aperçu) `DeviceTvmSoftwareEvidentBeta` a été ajoutée dans le hunting avancé pour vous permettre d’afficher la preuve de l’endroit où un logiciel spécifique a été détecté sur un appareil. 
 
## <a name="november-2021"></a>Novembre 2021

- (Aperçu) La fonctionnalité de module de gouvernance des applications de Defender pour les applications cloud est désormais disponible dans Microsoft 365 Defender. La gouvernance des applications fournit une fonctionnalité de gestion de la sécurité et des stratégies conçue pour les applications activées pour OAuth qui accèdent aux données Microsoft 365 via les API Microsoft Graph. La gouvernance des applications offre une visibilité, une correction et une gouvernance complètes sur la façon dont ces applications et leurs utilisateurs accèdent, utilisent et partagent vos données sensibles stockées dans Microsoft 365 par le biais d’insights actionnables et d’alertes et d’actions de stratégie automatisées. [En savoir plus sur la gouvernance des applications.](/cloud-app-security/app-governance-manage-app-governance)
- (Aperçu) La [page](advanced-hunting-overview.md) de recherche avancée dispose désormais d’une prise en charge multitab, d’un défilement intelligent, d’onglets de schéma simplifiés, d’options de modification rapide pour les requêtes, d’un indicateur d’utilisation des ressources de requête et d’autres améliorations pour rendre les requêtes plus fluides et plus faciles à affiner.
- (Aperçu) Vous pouvez désormais utiliser la fonctionnalité de lien vers [l’incident](advanced-hunting-link-to-incident.md) pour inclure des événements ou des enregistrements provenant des résultats de la requête de recherche avancée directement dans un incident nouveau ou existant que vous examinez. 
## <a name="october-2021"></a>Octobre 2021
- (GA) Dans le hunting avancé, d’autres colonnes ont été ajoutées dans la table [CloudAppEvents.](advanced-hunting-cloudappevents-table.md) Vous pouvez désormais `AccountType` inclure , , , et à vos `IsExternalUser` `IsImpersonated` `IPTags` `IPCategory` `UserAgentTags` requêtes. 

## <a name="september-2021"></a>Septembre 2021
- (GA) Microsoft Defender for Office 365 event data is available in the Microsoft 365 Defender event streaming API. Vous pouvez voir la disponibilité et l’état des types d’événements dans les types d’Microsoft 365 Defender pris en charge [dans l’API de diffusion en continu.](supported-event-types.md)
- (GA) Microsoft Defender pour Office 365 données disponibles dans le recherche avancée est désormais généralement disponible.
- (Aperçu) Affecter des incidents et des alertes aux comptes d’utilisateurs <br> Vous pouvez affecter un incident, ainsi que toutes les alertes qui lui sont associées, à un compte d’utilisateur de **Assign to:** on the **Manage incident** pane of an incident or the **Manage alert** pane of an alert.


## <a name="august-2021"></a>Août 2021
- (Aperçu) Microsoft Defender pour les Office 365 disponibles dans le recherche avancée
<br>Les nouvelles colonnes des tables de courrier électronique peuvent fournir plus d’informations sur les menaces basées sur le courrier électronique pour des examens plus approfondis à l’aide d’un recherche avancée. Vous pouvez désormais inclure la colonne dans `AuthenticationDetails` [EmailEvents,](./advanced-hunting-emailevents-table.md) `FileSize` [dans EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md)et dans les `ThreatTypes` tables `DetectionMethods` [EmailPostDeliveryEvents.](./advanced-hunting-emailpostdeliveryevents-table.md) 

- (Aperçu) Graphique d’incident <br>  Un nouvel **onglet Graph** sous  l’onglet Résumé d’un incident affiche l’étendue complète de l’attaque, la façon dont l’attaque s’est propagée sur votre réseau au fil du temps, où elle a commencé et jusqu’à quel point l’attaquant est passé.

## <a name="july-2021"></a>Juillet 2021
- [catalogue Professional services de transport](https://sip.security.microsoft.com/interoperability/professional_services)<br>Améliorer les fonctionnalités de détection, d’examen et d’intelligence contre les menaces de la plateforme avec les connexions partenaires pris en charge.

## <a name="june-2021"></a>Juin 2021
- (Aperçu) [Afficher les rapports par balise de menace](threat-analytics.md#view-reports-per-threat-tags)<br> Les balises de menace vous aident à vous concentrer sur des catégories de menaces spécifiques et à examiner les rapports les plus pertinents.
- (Aperçu) [API de diffusion en continu](../defender-endpoint/raw-data-export.md)<br> Microsoft 365 Defender prend en charge la diffusion en continu de tous les événements disponibles via la recherche avancée vers un hub d’événements et/ou un compte de stockage Azure.
- (Aperçu) [Prendre des mesures dans le recherche avancée](advanced-hunting-take-action.md)<br> Contenir rapidement des menaces ou traiter les biens compromis que vous trouvez dans le [recherche avancée.](advanced-hunting-overview.md)
- (Aperçu) [Référence du schéma dans le portail](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)<br> Obtenez des informations sur les tableaux de schéma de recherche avancée directement dans le centre de sécurité. Outre les descriptions de tableau et de colonne, cette référence inclut les types d’événements pris en charge (valeurs) et `ActionType` les exemples de requêtes.
- (Aperçu) [Fonction DeviceFromIP()](advanced-hunting-devicefromip-function.md)<br> Obtenir des informations sur les appareils qui ont été affectés à une ou plusieurs adresses IP spécifiques à une plage de temps donnée.
    

## <a name="may-2021"></a>Mai 2021

- [Nouvelle page d’alerte dans le portail Microsoft 365 Defender web](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243) <br> Fournit des informations améliorées pour le contexte d’une attaque. Vous pouvez voir quelle autre alerte déclenchée a provoqué l’alerte actuelle, ainsi que toutes les entités et activités concernées par l’attaque, y compris les fichiers, les utilisateurs et les boîtes aux lettres. Pour [plus d’informations, voir](/microsoft-365/security/defender/investigate-alerts) Examiner les alertes.
- [Graphique de tendance pour les incidents et les alertes dans le portail Microsoft 365 Defender web](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425) <br> Déterminez s’il existe plusieurs alertes pour un incident unique ou si votre organisation fait l’objet d’attaques avec plusieurs incidents différents. Pour plus [d’informations, voir](/microsoft-365/security/defender/incident-queue) Hiérarchiser les incidents.


## <a name="april-2021"></a>Avril 2021
- Microsoft 365 Defender<br> Le portail [d’Microsoft 365 Defender](https://security.microsoft.com) amélioré est désormais disponible. Cette nouvelle expérience regroupe Defender pour point de terminaison, Defender pour Office 365, Defender pour identité et bien plus encore dans un portail unique. Il s’agit du nouvel accueil pour gérer vos contrôles de sécurité. [Découvrir les nouveautés](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender d’analyse des menaces](threat-analytics.md)<br>
 L’analyse des menaces vous permet de répondre et de minimiser l’impact des attaques actives. Vous pouvez également en savoir plus sur les tentatives d’attaques bloquées par Microsoft 365 Defender solutions et prendre des mesures préventives qui atténuent les risques d’exposition supplémentaire et augmentent la résilience. Dans le cadre de l’expérience de sécurité unifiée, l’analyse des menaces est désormais disponible pour Microsoft Defender pour Endpoint et Microsoft Defender pour les titulaires Office licence E5.

## <a name="march-2021"></a>Mars 2021
- [Table CloudAppEvents](advanced-hunting-cloudappevents-table.md) <br>Trouvez des informations sur les événements dans différents services et applications cloud couverts par Microsoft Cloud App Security. Ce tableau inclut également des informations précédemment disponibles dans le `AppFileEvents` tableau.
## <a name="february-2021"></a>Février 2021
- (Aperçu) Le portail [Microsoft 365 Defender amélioré https://security.microsoft.com) (](https://security.microsoft.com) est désormais disponible en prévisualisation publique. Cette nouvelle expérience place Defender pour Point de terminaison et Defender pour Office 365 au centre. [Découvrez les modifications](microsoft-365-defender.md#the-microsoft-365-defender-portal).
- **[(Aperçu) Microsoft 365 Defender API](api-overview.md)** : les API de Microsoft 365 Defender de niveau supérieur vous permettent d’automatiser les flux de travail en fonction de l’incident partagé et des tables de recherche avancées. 
