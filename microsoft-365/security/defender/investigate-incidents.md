---
title: Examiner les incidents dans Microsoft 365 Defender
description: Examinez les incidents liés aux appareils, aux utilisateurs et aux boîtes aux lettres.
keywords: incidents, incidents, analyse, réponse, machines, appareils, utilisateurs, identités, courrier électronique, boîte aux lettres, investigation, graphe, preuve
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
- m365-security
- tier1
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 2dbc3bc965a1c975b354a5698b3fa0c67e2cd39c
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68055433"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Examiner les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Microsoft 365 Defender regroupe toutes les alertes, ressources, investigations et preuves connexes de l’ensemble de vos appareils, utilisateurs et boîtes aux lettres dans un incident pour vous donner un aperçu complet de l’étendue complète d’une attaque.

Dans un incident, vous analysez les alertes qui affectent votre réseau, comprenez ce qu’elles signifient et collez les preuves afin de pouvoir concevoir un plan de correction efficace.

## <a name="initial-investigation"></a>Enquête initiale

Avant de vous plonger dans les détails, examinez les propriétés et le résumé de l’incident.

Vous pouvez commencer par sélectionner l’incident à partir de la colonne de coche. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Sélection d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Dans ce cas, un volet récapitulatif s’ouvre avec des informations clés sur l’incident, telles que la gravité, à qui il est affecté, et les catégories [MITRE ATT&CK&trade;](https://attack.mitre.org/) pour l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Volet qui affiche les détails récapitulatifs d’un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

À partir de là, vous pouvez sélectionner **ouvrir la page d’incident**. La page principale de l’incident s’ouvre et vous trouverez plus d’informations récapitulatives et d’onglets pour les alertes, les appareils, les utilisateurs, les enquêtes et les preuves.

Vous pouvez également ouvrir la page principale d’un incident en sélectionnant le nom de l’incident dans la file d’attente des incidents.

## <a name="summary"></a>Résumé

La page **Résumé** vous donne un aperçu instantané des principales choses à remarquer sur l’incident.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Informations récapitulatives d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Les informations sont organisées dans ces sections.

| Section | Description |
|:-------|:-----|
| Alertes et catégories | Vue visuelle et numérique de la progression de l’attaque contre la chaîne de destruction. Comme avec d’autres produits de sécurité Microsoft, Microsoft 365 Defender est aligné sur l’infrastructure [MITRE ATT&CK&trade;](https://attack.mitre.org/). La chronologie des alertes montre l’ordre chronologique dans lequel les alertes se sont produites et pour chacune d’elles, leur état et leur nom. |
| Portée |  Affiche le nombre d’appareils, d’utilisateurs et de boîtes aux lettres impactés, et répertorie les entités par ordre de niveau de risque et de priorité d’investigation. |
| Évidence | Affiche le nombre d’entités affectées par l’incident. |
| Informations sur l’incident | Affiche les propriétés de l’incident, telles que les balises, l’état et la gravité. |
|||

Utilisez la page **Résumé** pour évaluer l’importance relative de l’incident et accéder rapidement aux alertes associées et aux entités affectées.

## <a name="alerts"></a>Alertes

Sous l’onglet **Alertes** , vous pouvez afficher la file d’attente des alertes pour les alertes liées à l’incident et d’autres informations les concernant, telles que :

- Gravité.
- Entités impliquées dans l’alerte.
- Source des alertes (Microsoft Defender pour Identity, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Defender pour Cloud Apps et le module complémentaire de gouvernance des applications).
- La raison pour laquelle ils étaient liés.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Volet Alertes pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-alerts.png":::

Par défaut, les alertes sont classées chronologiquement pour vous permettre de voir comment l’attaque s’est produite au fil du temps. Lorsque vous sélectionnez une alerte dans un incident, Microsoft 365 Defender affiche les informations d’alerte spécifiques au contexte de l’incident global. 

Vous pouvez voir les événements de l’alerte, que d’autres alertes déclenchées ont provoqué l’alerte actuelle, ainsi que toutes les entités et activités affectées impliquées dans l’attaque, y compris les appareils, les fichiers, les utilisateurs et les boîtes aux lettres.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Détails d’une alerte dans un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

La page d’alerte d’incident comprend les sections suivantes :

- L’histoire de l’alerte, qui inclut :

   - Que s'est-il passé

   - Actions prises

   - Événements connexes

- Propriétés d’alerte dans le volet droit (état, détails, description, etc.)

Toutes les alertes ne comportent pas toutes les sous-sections répertoriées dans la section **Histoire de l’alerte** .

Découvrez comment utiliser la file d’attente d’alertes et les pages d’alerte dans [examiner les alertes](investigate-alerts.md).

## <a name="devices"></a>Appareils

L’onglet **Appareils** répertorie tous les appareils liés à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Page Appareils pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-devices.png":::

Vous pouvez sélectionner la coche d’un appareil pour afficher les détails de l’appareil, les données d’annuaire, les alertes actives et les utilisateurs connectés. Sélectionnez le nom de l’appareil pour afficher les détails de l’appareil dans l’inventaire des appareils Defender pour point de terminaison. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Page relative aux options d’inventaire des appareils dans le Microsoft Defender pour point de terminaison." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

À partir de la page de l’appareil, vous pouvez collecter des informations supplémentaires sur l’appareil, telles que toutes ses alertes, une chronologie et des recommandations de sécurité. Par exemple, à partir de l’onglet **Chronologie** , vous pouvez faire défiler la chronologie de l’ordinateur et afficher tous les événements et comportements observés sur l’ordinateur dans l’ordre chronologique, entrecoupés des alertes déclenchées.

> [!TIP]
> Vous pouvez effectuer des analyses à la demande sur une page d’appareil. Dans le portail Microsoft 365 Defender, choisissez Points de **terminaison > Inventaire des appareils**. Sélectionnez un appareil qui contient des alertes, puis exécutez une analyse antivirus. Les actions, telles que les analyses antivirus, sont suivies et sont visibles sur la page **d’inventaire des appareils** . Pour en savoir plus, consultez [Exécuter Microsoft Defender Analyse antivirus sur les appareils](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Utilisateurs

**L’onglet Utilisateurs** répertorie tous les utilisateurs qui ont été identifiés pour faire partie de l’incident ou y être associés. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Page Utilisateurs dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

Vous pouvez sélectionner la coche d’un utilisateur pour afficher les détails de la menace, de l’exposition et des informations de contact du compte d’utilisateur. Sélectionnez le nom d’utilisateur pour afficher des détails supplémentaires sur le compte d’utilisateur.

Découvrez comment afficher des informations utilisateur supplémentaires et gérer les utilisateurs d’un incident lors de [l’examen des utilisateurs](investigate-users.md).


## <a name="mailboxes"></a>Boîtes aux lettres

L’onglet **Boîtes aux lettres répertorie** toutes les boîtes aux lettres qui ont été identifiées comme faisant partie ou associées à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Page Boîtes aux lettres pour un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Vous pouvez sélectionner la coche d’une boîte aux lettres pour afficher une liste d’alertes actives. Sélectionnez le nom de la boîte aux lettres pour afficher des détails supplémentaires sur la page Explorateur pour Defender pour Office 365.

## <a name="investigations"></a>Enquêtes

**L’onglet Investigations** répertorie toutes les [investigations automatisées déclenchées](m365d-autoir.md) par les alertes dans cet incident. Les enquêtes automatisées effectuent des actions de correction ou attendent l’approbation des actions par l’analyste, selon la façon dont vous avez configuré vos investigations automatisées pour qu’elles s’exécutent dans Defender pour point de terminaison et Defender pour Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Page Investigations pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-investigations.png":::

Sélectionnez une enquête pour accéder à sa page de détails pour obtenir des informations complètes sur l’état de l’examen et de la correction. Si des actions sont en attente d’approbation dans le cadre de l’enquête, elles apparaissent dans l’onglet **Historique des actions en attente** . Prenez des mesures dans le cadre de la correction des incidents.

Il existe également un onglet **Graphique d’investigation** qui montre :

- Connexion d’alertes aux ressources affectées dans votre organisation.
- Quelles entités sont liées aux alertes et à la façon dont elles font partie de l’histoire de l’attaque.
- Alertes pour l’incident.

Le graphique d’investigation vous aide à comprendre rapidement l’étendue complète de l’attaque en connectant les différentes entités suspectes qui font partie de l’attaque avec leurs ressources associées, telles que les utilisateurs, les appareils et les boîtes aux lettres. 

Pour plus d’informations, consultez [Examen automatisé et réponse dans Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Preuve et réponse

L’onglet **Preuve et réponse** affiche tous les événements pris en charge et les entités suspectes dans les alertes de l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Page Preuves et réponses pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender examine automatiquement tous les événements pris en charge par les incidents et les entités suspectes dans les alertes, en vous fournissant des informations sur les e-mails, fichiers, processus, services, adresses IP importants, etc. Cela vous permet de détecter et de bloquer rapidement les menaces potentielles dans l’incident.

Chacune des entités analysées est marquée avec un verdict (malveillant, suspect, propre) et un état de correction. Cela vous aide à comprendre l’état de correction de l’ensemble de l’incident et les étapes suivantes qui peuvent être effectuées.

## <a name="graph-preview"></a>Graph (préversion)

L’onglet **Graph** indique l’étendue complète de l’attaque, la façon dont l’attaque s’est propagée dans votre réseau au fil du temps, l’endroit où elle a démarré et la distance parcourue par l’attaquant. Il connecte les différentes entités suspectes qui font partie de l’attaque avec leurs ressources associées, telles que les utilisateurs, les appareils et les boîtes aux lettres. 

Sous l’onglet **Graph** , vous pouvez :

1. Lisez les alertes et les nœuds du graphique tels qu’ils se sont produits au fil du temps pour comprendre la chronologie de l’attaque.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="Lecture des alertes et des nœuds sur la page Graph":::
 

2. Ouvrez un volet d’entité, ce qui vous permet d’examiner les détails de l’entité et d’agir sur des actions de correction, telles que la suppression d’un fichier ou l’isolation d’un appareil.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="Volet d’entité sur la page Graph dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. Mettez en surbrillance les alertes en fonction de l’entité à laquelle elles sont liées.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="Mise en surbrillance d’alerte sur la page Graph" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>Prochaines étapes

Si nécessaire :

- [Examiner les alertes d’un incident](investigate-alerts.md)
- [Examiner les utilisateurs d’un incident](investigate-users.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)
