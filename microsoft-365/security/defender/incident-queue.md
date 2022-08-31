---
title: Hiérarchiser les incidents dans Microsoft 365 Defender
description: Découvrez comment filtrer les incidents à partir de la file d’attente d’incidents dans Microsoft 365 Defender
keywords: incident, file d’attente, vue d’ensemble, appareils, identités, utilisateurs, boîte aux lettres, courrier électronique, incidents, analyse, réponse, triage
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: b5f8968020a08197586caef09273d6b4276ff421
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67480214"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Hiérarchiser les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender applique l’analyse de corrélation et agrège les alertes associées et les investigations automatisées de différents produits dans un incident. Microsoft 365 Defender déclenche également des alertes uniques sur les activités qui ne peuvent être identifiées comme malveillantes qu’en raison de la visibilité de bout en bout dans Microsoft 365 Defender a sur l’ensemble de la suite de produits. Cette vue offre à vos analystes de sécurité l’histoire d’attaque plus large, qui les aide à mieux comprendre et à gérer les menaces complexes au sein de votre organisation.

La **file d’attente d’incidents** affiche une collection d’incidents qui ont été créés sur des appareils, des utilisateurs et des boîtes aux lettres. Il vous aide à trier les incidents pour hiérarchiser et créer une décision éclairée en matière de réponse à la cybersécurité, un processus appelé triage des incidents.

Vous accédez à la file d’attente des **incidents à partir des alertes & > incidents** lors du lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Section Incident montrant la file d’attente des incidents dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

La section **Incidents et alertes les plus récents** affiche un graphique du nombre d’alertes reçues et d’incidents créés au cours des dernières 24 heures.

Par défaut, la file d’attente d’incidents dans le portail Microsoft 365 Defender affiche les incidents observés au cours des six derniers mois. L’incident le plus récent se trouve en haut de la liste pour que vous puissiez le voir en premier.

La file d’attente d’incidents comporte des colonnes personnalisables ( **sélectionnez Choisir des colonnes**) qui vous donnent une visibilité sur les différentes caractéristiques de l’incident ou des entités affectées. Cela vous aide à prendre une décision éclairée concernant la hiérarchisation des incidents à des fins d’analyse.

Pour une visibilité supplémentaire en un coup d’œil, le nommage automatique des incidents génère des noms d’incidents basés sur des attributs d’alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.

Par exemple : *incident en plusieurs étapes sur plusieurs points de terminaison signalés par plusieurs sources.*

> [!NOTE]
> Le nom des incidents qui existaient avant le lancement de la dénomination automatique des incidents n’est pas modifié.

La file d’attente d’incidents fournit également plusieurs options de filtrage, qui, lorsqu’elles sont appliquées, vous permettent d’effectuer un large balayage de tous les incidents existants dans votre environnement ou de décider de vous concentrer sur un scénario ou une menace spécifique. L’application de filtres dans la file d’attente des incidents permet de déterminer le type d’incident nécessitant une attention immédiate. 

La liste **Filtres au-dessus** de la liste des incidents affiche les filtres actuellement appliqués.

## <a name="available-filters"></a>Filtres disponibles

Dans la file d’attente d’incidents par défaut, vous pouvez sélectionner **Filtrer** pour afficher un volet **Filtre** , à partir duquel vous spécifiez un ensemble filtré d’incidents. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Volet Filtres de la file d’attente d’incidents dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Vous pouvez également voir le volet **Filtre** en sélectionnant l’un des filtres dans la liste **Filtres au-dessus** de la liste des incidents.

Ce tableau répertorie les noms de filtre disponibles.

| Nom du filtre | Description |
|:-------|:-----|
| État | Sélectionnez **Nouveau**, **En cours** ou **Résolu**. |
| Severity | La gravité d’un incident indique l’impact qu’il peut avoir sur vos ressources. Plus la gravité est élevée, plus l’impact est important et nécessite généralement une attention immédiate. Sélectionnez **Haut**, **Moyen**, **Bas** ou **Informationnel**. |
| Affectation d’incident | Sélectionnez l’utilisateur ou les utilisateurs affectés. |
| Plusieurs sources de service  | Spécifiez si le filtre concerne plusieurs sources de service. |
| Sources de service  | Spécifiez les incidents qui contiennent des alertes à partir de : Gouvernance des applications, Microsoft 365 Defender, Microsoft Defender pour Office 365, Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity, Microsoft Defender for Cloud Apps. |
| Balises | Sélectionnez un ou plusieurs noms de balises dans la liste. |
| Plusieurs catégories  | Spécifiez si le filtre est destiné à plusieurs catégories. |
| Categories | Choisissez des catégories pour vous concentrer sur des tactiques, des techniques ou des composants d’attaque spécifiques vus. |
| Entités | Spécifiez le nom d’une ressource telle qu’un utilisateur, un appareil, une boîte aux lettres ou un nom d’application. |
| Confidentialité des données | Certaines attaques se concentrent sur le ciblage de données sensibles ou précieuses. En appliquant un filtre pour des étiquettes de confidentialité spécifiques, vous pouvez rapidement déterminer si des informations sensibles ont potentiellement été compromises et hiérarchiser la résolution de ces incidents. <br><br> Ce filtre affiche des informations uniquement lorsque vous avez appliqué [des étiquettes de confidentialité à partir de Protection des données Microsoft Purview](../../compliance/sensitivity-labels.md). |
| Groupes d'appareils | Spécifiez un nom [de groupe d’appareils](/windows/security/threat-protection/microsoft-defender-atp/machine-groups) . |
| Plateforme du système d’exploitation | Spécifiez les systèmes d’exploitation des appareils. |
| Classification | Spécifiez l’ensemble des classifications des alertes associées. |
| État d’investigation automatisé | Spécifiez l’état de l’investigation automatisée.  |
| Menace associée | Spécifiez une menace nommée.  |
| Actors | Spécifiez un acteur de menace nommé.  |
|||

Le filtre par défaut consiste à afficher toutes les alertes et incidents dont l’état est **Nouveau** et **En cours** et dont la gravité est **Faible**, **Moyenne** ou **Élevée**.

Vous pouvez supprimer rapidement un filtre en sélectionnant le **X** dans le nom d’un filtre dans la liste **Filtres** . 

## <a name="save-custom-filters-as-urls"></a>Enregistrer des filtres personnalisés en tant qu’URL

Une fois que vous avez configuré un filtre utile dans la file d’attente d’incidents, vous pouvez marquer l’URL de l’onglet du navigateur ou l’enregistrer sous forme de lien sur une page Web, un document Word ou un emplacement de votre choix. Cela vous permet d’accéder en un seul clic aux vues clés de la file d’attente d’incidents, par exemple :

- Nouveaux incidents
- Incidents de gravité élevée
- Incidents non attribués
- Incidents de gravité élevée et non attribués
- Incidents qui m’ont été attribués
- Incidents qui m’ont été attribués et pour Microsoft Defender pour point de terminaison
- Incidents avec une balise ou des balises spécifiques
- Incidents avec une catégorie de menace spécifique
- Incidents avec une menace associée spécifique
- Incidents avec un acteur spécifique

Une fois que vous avez compilé et stocké votre liste de vues de filtre utiles en tant qu’URL, vous pouvez l’utiliser pour traiter et hiérarchiser rapidement les incidents dans votre file d’attente et les [gérer](manage-incidents.md) pour l’affectation et l’analyse suivantes.

## <a name="search-for-incidents"></a>Rechercher des incidents

Dans la zone **Rechercher un nom ou un ID** au-dessus de la liste des incidents, vous pouvez taper l’ID d’incident ou le nom de l’incident. Lorsque vous sélectionnez un incident dans la liste des résultats de la recherche, le portail Microsoft 365 Defender ouvre un nouvel onglet avec les propriétés de l’incident, à partir duquel vous pouvez démarrer votre [enquête](investigate-incidents.md).

## <a name="search-for-impacted-assets"></a>Rechercher les ressources impactées

Vous pouvez nommer une ressource&mdash;telle qu’un utilisateur, un appareil, une boîte aux lettres ou un nom&mdash;d’application et rechercher tous les incidents associés. 

## <a name="specify-a-time-range"></a>Spécifier un intervalle de temps

La liste par défaut des incidents concerne ceux qui se sont produits au cours des six derniers mois. Vous pouvez spécifier un nouvel intervalle de temps à partir de la zone de liste déroulante en regard de l’icône de calendrier en sélectionnant :

 - 1 jour
 - 3 jours
 - 1 semaine
 - 30 jours
 - 30 jours
 - 6 mois
 - Plage personnalisée dans laquelle vous pouvez spécifier des dates et des heures

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez déterminé l’incident qui requiert la priorité la plus élevée, sélectionnez-le et :

- [Gérez](manage-incidents.md) les propriétés de l’incident pour les balises, l’affectation, la résolution immédiate des incidents faux positifs et les commentaires.
- Commencez vos [investigations](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
