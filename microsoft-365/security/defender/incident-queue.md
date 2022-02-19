---
title: Hiérarchiser les incidents dans Microsoft 365 Defender
description: Découvrez comment filtrer les incidents à partir de la file d’attente d’incidents dans Microsoft 365 Defender
keywords: incident, file d’attente, vue d’ensemble, appareils, identités, utilisateurs, boîte aux lettres, courrier électronique, incidents, analyse, réponse, triage
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.technology: m365d
ms.openlocfilehash: fafb48af3aa0c38146073a0682323496bc0431e2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62903962"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Hiérarchiser les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender l’analyse de corrélation et regroupe les alertes associées et les enquêtes automatisées de différents produits dans un incident. Microsoft 365 Defender déclenche également des alertes uniques sur les activités qui peuvent uniquement être identifiées comme malveillantes en raison de la visibilité de bout en bout dont dispose Microsoft 365 Defender sur l’ensemble de la suite de produits. Cette vue offre à vos analystes de sécurité un niveau d’attaque plus large, qui leur permet de mieux comprendre et de gérer les menaces complexes au sein de votre organisation.

La **file d’attente Incident** affiche un ensemble d’incidents qui ont été créés sur des appareils, des utilisateurs et des boîtes aux lettres. Elle vous aide à trier les incidents afin de hiérarchiser et de créer une décision de réponse cyber-sécurité. C’est également ce qu’on appelle le triage des incidents.

Vous pouvez vous rendre dans la file d’attente des **incidents à partir d’incidents & alertes > incidents** sur le lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender web</a>. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Exemple de file d’attente d’incident." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

La section **Incidents et alertes les plus récents** présente un graphique du nombre d’alertes reçues et d’incidents créés au cours des dernières 24 heures.

Par défaut, la file d’attente des incidents du portail Microsoft 365 Defender affiche les incidents observés au cours des six derniers mois. L’incident le plus récent se trouve en haut de la liste pour que vous le voyez en premier.

La file d’attente des incidents possède des colonnes personnalisables (sélectionnez Sélectionner des colonnes **) qui** vous donnent une visibilité sur les différentes caractéristiques de l’incident ou les entités impactées. Cela vous permet de prendre une décision éclairée concernant la hiérquage des incidents à analyser.

Pour une visibilité supplémentaire en un coup d’œil, l’appellation automatique des incidents génère des noms d’incident basés sur des attributs d’alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.

Par exemple : *incident en plusieurs étapes sur plusieurs points de terminaison signalés par plusieurs sources.*

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la dénomination automatique des incidents ne seront pas modifiés.

La file d’attente des incidents expose également plusieurs options de filtrage qui, lorsqu’elles sont appliquées, vous permettent d’effectuer un large éventail de tous les incidents existants dans votre environnement ou de décider de vous concentrer sur un scénario ou une menace spécifique. L’application de filtres dans la file d’attente des incidents permet de déterminer le type d’incident nécessitant une attention immédiate. 

## <a name="available-filters"></a>Filtres disponibles

Dans la file d’attente des incidents par défaut, vous pouvez sélectionner **Filtres** pour afficher un volet Filtres, à partir duquel vous pouvez afficher un ensemble filtré d’incidents. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Exemple du volet filtres de la file d’attente des incidents." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Le filtre par défaut consiste à afficher toutes les alertes et tous les incidents avec l’état **Nouveau** et **En cours** .

Ce tableau répertorie les noms de filtres disponibles.

| Nom du filtre | Description |
|:-------|:-----|
| État | **Sélectionnez Nouveau**, **En cours** ou **Résolu**. |
| Severity | La gravité d’un incident indique l’impact qu’il peut avoir sur vos ressources. Plus la gravité est élevée, plus l’impact est important et nécessite généralement l’attention la plus immédiate. **Sélectionnez Haut**, **Moyen**, **Bas** **ou Informationnel**. |
| Affectation d’incident | Sélectionnez Affecté à tout le monde, Affecté à moi ou Non attribué. |
| Plusieurs sources de service  | Spécifiez si le filtre est pour plusieurs sources de service. |
| Sources de service  | Filtrez pour voir uniquement les incidents qui contiennent des alertes de : Gouvernance des applications, Microsoft 365 Defender, Microsoft Defender pour Office 365, Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité, Microsoft Defender pour les applications cloud. |
| Balises | Sélectionnez un ou plusieurs noms de balises dans la liste. |
| Plusieurs catégories  | Spécifiez si le filtre s’agit de plusieurs catégories. |
| Catégories | Choisissez des catégories pour vous concentrer sur des tactiques, des techniques ou des composants d’attaque spécifiques. |
| Plateforme du système d’exploitation | Limitez l’affichage de la file d’attente des incidents par système d’exploitation. |
| Classification | Filtrer les incidents en fonction des classifications définies des alertes associées. Sélectionnez **Alerte vraie**, **Alertes fausses** ou Non **définies**. |
| État de l’examen | Filtrer les incidents selon l’état de l’examen automatisé.  |
| Menace associée | Filtrer les incidents par une menace nommée.  |
| Actors | Filtrer les incidents par un acteur de menace nommé.  |
| Confidentialité des données | Certaines attaques se concentrent sur le ciblage de données sensibles ou précieuses. En appliquant un filtre pour déterminer si des données confidentielles sont impliquées dans l’incident, vous pouvez rapidement déterminer si des informations sensibles ont été compromises et hiérarchiser les problèmes. <br><br>Ce filtre n’est disponible que si Protection des données Microsoft est allumé.|
|||

## <a name="save-defined-filters-as-urls"></a>Enregistrer les filtres définis en tant qu’URL

Une fois que vous avez configuré un filtre utile dans la file d’attente des incidents, vous pouvez mettre en signet l’URL de l’onglet du navigateur ou l’enregistrer en tant que lien sur une page Web, un document Word ou un lieu de votre choix. Cela vous permettra d’accéder en un seul clic aux vues clés de la file d’attente des incidents, telles que :

- Nouveaux incidents
- Incidents de gravité élevée
- Incidents non signés
- Incidents non signés de gravité élevée
- Incidents qui m’ont été attribués
- Incidents qui m’ont été attribués et pour Microsoft Defender pour le point de terminaison
- Incidents avec une ou plusieurs balises spécifiques
- Incidents avec une catégorie de menace spécifique
- Incidents avec une menace associée spécifique
- Incidents avec un acteur spécifique

Une fois que vous avez compilé et stocké votre liste d’affichages de filtre utiles en tant qu’URL, vous pouvez l’utiliser pour traiter et hiérarchiser [](manage-incidents.md) rapidement les incidents dans votre file d’attente et les gérer pour une affectation et une analyse ultérieures.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez déterminé quel incident nécessite la priorité la plus élevée, sélectionnez-le et :

- [Gérer les](manage-incidents.md) propriétés de l’incident pour les balises, l’affectation, la résolution immédiate des incidents faux positifs et les commentaires.
- Commencez vos [enquêtes](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
