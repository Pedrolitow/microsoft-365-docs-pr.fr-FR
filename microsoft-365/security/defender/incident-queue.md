---
title: Hiérarchiser les incidents dans Microsoft 365 Defender
description: Découvrez comment filtrer les incidents à partir de la file d'attente des incidents dans Microsoft 365 Defender
keywords: incident, file d’attente, vue d’ensemble, appareils, identités, utilisateurs, boîte aux lettres, e-mail, incidents
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: cd571414512ce876e730199b21bf755e4c4b733f
ms.sourcegitcommit: 2655bb0ccd66279c35be2fadbd893c937d084109
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51876198"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Hiérarchiser les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender applique l'analyse de corrélation et regroupe les alertes associées et les enquêtes automatisées de différents produits dans un incident. Microsoft 365 Defender déclenche également des alertes uniques sur les activités qui peuvent uniquement être identifiées comme malveillantes en raison de la visibilité de bout en bout de Microsoft 365 Defender sur l'ensemble de la suite de produits. Cette vue offre à vos analystes de sécurité un niveau d'attaque plus large, qui les aide à mieux comprendre et traiter les menaces complexes au sein de votre organisation.

La **file d'attente Incident** affiche un ensemble d'incidents qui ont été créés sur plusieurs appareils, utilisateurs et boîtes aux lettres. Elle vous aide à trier les incidents afin de hiérarchiser et de créer une décision de réponse cyber-sécurité. 

Vous pouvez vous rendre dans la file d'attente des incidents à partir d'incidents **& alertes** > Incidents dans le lancement rapide du Centre de sécurité Microsoft 365 ([security.microsoft.com](https://security.microsoft.com)).

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Exemple de file d'attente d'incident":::

Par défaut, la file d'attente des incidents dans le Centre de sécurité Microsoft 365 affiche les incidents observés au cours des six derniers mois. L'incident le plus récent se trouve en haut de la liste pour que vous le voyez en premier.

La file d'attente des incidents possède des colonnes personnalisables (sélectionnez Sélectionner des colonnes) qui vous donnent une visibilité sur les différentes caractéristiques de l'incident ou les entités impactées. Cela vous permet de prendre une décision éclairée concernant la hiérquage des incidents à analyser.

Pour une visibilité supplémentaire en un coup d'œil, l'appellation automatique des incidents génère des noms d'incident basés sur des attributs d'alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l'étendue de l'incident.

Par exemple : incident en plusieurs étapes sur plusieurs points de *terminaison signalés par plusieurs sources.*

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la dénomination automatique des incidents ne seront pas modifiés.

La file d'attente des incidents expose également plusieurs options de filtrage qui, lorsqu'elles sont appliquées, vous permettent d'effectuer un large éventail de tous les incidents existants dans votre environnement ou de décider de vous concentrer sur un scénario ou une menace spécifique. L’application de filtres dans la file d’attente des incidents permet de déterminer le type d’incident nécessitant une attention immédiate. 

## <a name="available-filters"></a>Filtres disponibles

Dans la file d'attente des incidents par défaut, vous pouvez sélectionner **Filtres** pour afficher un volet Filtres, à partir duquel vous pouvez afficher un ensemble filtré d'incidents. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Exemple du volet filtres de la file d'attente des incidents":::

Ce tableau répertorie les noms de filtres disponibles.

| Nom du filtre | Description |
|:-------|:-----|
| Affectée à | Vous pouvez choisir d'afficher les alertes qui vous sont affectées ou celles gérées par l'automatisation. |
| Catégories | Choisissez des catégories pour vous concentrer sur des tactiques, des techniques ou des composants d'attaque spécifiques. |
| Classification | Filtrer les incidents en fonction des classifications définies des alertes associées. Les valeurs incluent des alertes vraies, des alertes fausses ou non définies. |
| Confidentialité des données | Certaines attaques se concentrent sur le ciblage de données sensibles ou précieuses. En appliquant un filtre pour déterminer si des données confidentielles sont impliquées dans l’incident, vous pouvez rapidement déterminer si des informations sensibles ont été compromises et hiérarchiser les problèmes. <br><br> Applicable uniquement si la protection des informations Microsoft est activée.|
| Groupe d'appareils | Filtrer par groupes d'appareils définis. |
| État de l'examen | Filtrer les incidents selon l'état de l'examen automatisé.  |
| Plusieurs catégories | Vous pouvez choisir de ne voir que les incidents qui ont été mappés à plusieurs catégories et qui peuvent donc potentiellement causer davantage de dommages. |
| Plusieurs sources de service  | Filtrez pour voir uniquement les incidents qui contiennent des alertes provenant de différentes sources (Microsoft Defender pour endpoint, Microsoft Cloud App Security, Microsoft Defender pour l'identité, Microsoft Defender pour Office 365). |
| Plateforme du système d'exploitation | Limitez l'affichage de la file d'attente des incidents par système d'exploitation. |
| Sources de service | En sélectionnant une source spécifique, vous pouvez vous concentrer sur les incidents qui contiennent au moins une alerte de la source choisie. |
| Severity | La gravité d'un incident indique l'impact qu'il peut avoir sur vos ressources. Plus la gravité est élevée, plus l'impact est important et nécessite généralement l'attention la plus immédiate. |
| Statut | Vous pouvez choisir de limiter la liste des incidents affichés en fonction de leur état pour identifier ceux qui sont actifs ou résolus. |
|||

## <a name="incident-response-workflow"></a>Flux de travail de réponse aux incidents

Voici le flux de travail classique pour répondre aux incidents :

1. Identifier et trier les incidents les plus prioritaires pour l'examen et la résolution.
2. Pour chaque incident prioritaire, lancez une [enquête](investigate-incidents.md):

   a. Affichez le résumé de l'incident pour comprendre sa portée et sa gravité, ainsi que les entités concernées (onglet **Résumé).**

   b. Commencez à regarder les alertes pour comprendre leur origine, leur étendue et leur gravité (onglet **Alertes).**

   c. Si nécessaire, rassemblez des informations sur les appareils, les utilisateurs et les boîtes aux lettres touchés (onglets **Appareils,** Utilisateurs et Boîtes **aux lettres).**

   d. Découvrez comment Microsoft 365 Defender a résolu automatiquement certaines alertes (onglet **Enquêtes).**
   
   e. Si nécessaire, utilisez les informations du jeu de données pour l'incident pour plus d'informations (onglet Preuve **et** réponse).

   À mesure que vous examinez, vous devez être concerné par :

   - Containment : réduction de tout impact supplémentaire sur votre client.
   - Éradication : suppression de la menace de sécurité.
   - Récupération : restauration des ressources de votre client à l'état où elles se sont trouver avant l'attaque.

3. Après avoir résolu l'incident, prenez le temps de :

   - Comprendre le type de l'attaque et son impact.
   - Recherchez une tendance d'attaques de sécurité dans la communauté de la sécurité.
   - Rappelez-vous du flux de travail que vous avez utilisé pour résoudre l'incident et mettre à jour vos flux de travail et playbooks standard selon vos besoins.
   - Déterminez si des modifications de votre posture de sécurité sont nécessaires et prenez les mesures nécessaires pour les implémenter.

Voici un résumé du processus de base.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-process.png" alt-text="Processus de base pour l'examen des incidents":::

## <a name="next-step"></a>Étape suivante

Une fois que vous avez déterminé quel incident nécessite la priorité la plus élevée, sélectionnez-le et commencez votre [enquête.](investigate-incidents.md)

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
