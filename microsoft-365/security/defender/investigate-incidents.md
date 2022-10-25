---
title: Examiner les incidents dans Microsoft 365 Defender
description: Examiner les incidents liés aux appareils, aux utilisateurs et aux boîtes aux lettres.
keywords: incident, incidents, récit d’attaque, analyse, réponse, ordinateurs, appareils, utilisateurs, identités, courrier électronique, boîte aux lettres, investigation, graphe, preuve
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
ms.openlocfilehash: 41006d8c68eef16d09bc872ca3d8fc471812cb1c
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687747"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Examiner les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Microsoft 365 Defender regroupe toutes les alertes, ressources, enquêtes et preuves associées de vos appareils, utilisateurs et boîtes aux lettres dans un incident pour vous donner un aperçu complet de l’étendue d’une attaque.

Dans un incident, vous analysez les alertes qui affectent votre réseau, comprenez ce qu’elles signifient et rassemblez les preuves afin de pouvoir concevoir un plan de correction efficace.

## <a name="initial-investigation"></a>Enquête initiale

Avant de vous plonger dans les détails, jetez un coup d’œil aux propriétés et à l’histoire complète de l’attaque de l’incident.

Vous pouvez commencer par sélectionner l’incident dans la colonne coche. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Sélection d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Dans ce cas, un volet récapitulatif s’ouvre avec des informations clés sur l’incident, telles que la gravité, à qui il est attribué et les catégories [MITRE ATT&CK&trade;](https://attack.mitre.org/) pour l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Volet qui affiche les détails du résumé d’un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

À partir de là, vous pouvez sélectionner **Ouvrir la page d’incident**. Cela ouvre la page principale de l’incident dans laquelle vous trouverez les informations et les onglets complets du récit d’attaque pour les alertes, les appareils, les utilisateurs, les enquêtes et les preuves.

Vous pouvez également ouvrir la page principale d’un incident en sélectionnant le nom de l’incident dans la file d’attente des incidents.

## <a name="attack-story"></a>Histoire de l’attaque

Les récits d’attaque vous aident à examiner, examiner et corriger rapidement les attaques tout en affichant l’histoire complète de l’attaque sous le même onglet. Il vous permet également d’examiner les détails de l’entité et de prendre des mesures correctives, telles que la suppression d’un fichier ou l’isolation d’un appareil sans perdre le contexte.

:::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="L’histoire de l’attaque d’un incident" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

Dans le récit d’attaque, vous trouverez la page d’alerte et le graphique de l’incident.

La page d’alerte d’incident comprend les sections suivantes :

- Récit d’alerte, qui comprend :

   - Que s'est-il passé

   - Actions prises

   - Événements connexes

- Propriétés d’alerte dans le volet droit (état, détails, description, etc.)

Notez que toutes les alertes n’auront pas toutes les sous-sections répertoriées dans la section **Article sur les alertes** .

Le graphique montre l’étendue complète de l’attaque, la façon dont l’attaque s’est propagée sur votre réseau au fil du temps, où elle a commencé et jusqu’où l’attaquant est allé. Il connecte les différentes entités suspectes qui font partie de l’attaque à leurs ressources associées, telles que les utilisateurs, les appareils et les boîtes aux lettres.

À partir du graphique, vous pouvez :

- Lisez les alertes et les nœuds sur le graphique tels qu’ils se sont produits au fil du temps pour comprendre la chronologie de l’attaque.
  
  :::image type="content" source="../../media/investigate-incidents/play-alert-attack-story.gif" alt-text="Capture d’écran montrant la lecture des alertes et des nœuds sur la page du graphique de récit d’attaque.":::

- Ouvrez un volet d’entité, ce qui vous permet d’examiner les détails de l’entité et d’agir sur les actions de correction, telles que la suppression d’un fichier ou l’isolation d’un appareil.

  :::image type="content" source="../../media/investigate-incidents/review-entity-details-attack-story.gif" alt-text="Capture d’écran montrant l’examen des détails de l’entité sur la page du graphique de récit d’attaque.":::

- Mettez en surbrillance les alertes en fonction de l’entité à laquelle elles sont liées.

Utilisez la page **Résumé** pour évaluer l’importance relative de l’incident et accéder rapidement aux alertes associées et aux entités impactées.

## <a name="summary"></a>Résumé

La page **Résumé** vous donne un aperçu instantané des principaux éléments à remarquer concernant l’incident.

:::image type="content" source="../../media/incidents-overview/incidents-investigate-summary.png" alt-text="Capture d’écran montrant les informations récapitulatives d’un incident dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-investigate-summary.png":::

Les informations sont organisées dans ces sections.

| Section | Description |
|:-------|:-----|
| Alertes et catégories | Vue visuelle et numérique de l’avancement de l’attaque par rapport à la chaîne de destruction. Comme pour les autres produits de sécurité Microsoft, Microsoft 365 Defender est aligné sur l’infrastructure [MITRE ATT&CK&trade;](https://attack.mitre.org/). La chronologie des alertes indique l’ordre chronologique dans lequel les alertes se sont produites et, pour chacune, leur état et leur nom. |
| Portée |  Affiche le nombre d’appareils, d’utilisateurs et de boîtes aux lettres concernés, et répertorie les entités par ordre de niveau de risque et de priorité d’investigation. |
| Évidence | Affiche le nombre d’entités affectées par l’incident. |
| Informations sur l’incident | Affiche les propriétés de l’incident, telles que les balises, l’état et la gravité. |
|||

## <a name="alerts"></a>Alertes

Sous l’onglet **Alertes** , vous pouvez afficher la file d’attente des alertes liées à l’incident et d’autres informations les concernant, telles que :

- Gravité.
- Entités impliquées dans l’alerte.
- Source des alertes (Microsoft Defender pour Identity, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Defender for Cloud Apps et le module complémentaire de gouvernance des applications).
- La raison pour laquelle ils ont été liés.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Volet Alertes pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-alerts.png":::

Par défaut, les alertes sont classées par ordre chronologique pour vous permettre de voir comment l’attaque s’est jouée au fil du temps. Lorsque vous sélectionnez une alerte dans un incident, Microsoft 365 Defender affiche les informations d’alerte spécifiques au contexte de l’incident global. 

Vous pouvez voir les événements de l’alerte, les autres alertes déclenchées à l’origine de l’alerte actuelle, ainsi que toutes les entités et activités affectées impliquées dans l’attaque, y compris les appareils, les fichiers, les utilisateurs et les boîtes aux lettres.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Détails d’une alerte dans un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

Découvrez comment utiliser la file d’attente d’alertes et les pages d’alerte dans [examiner les alertes](investigate-alerts.md).

## <a name="devices"></a>Appareils

L’onglet **Appareils** répertorie tous les appareils liés à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Page Appareils pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-devices.png":::

Vous pouvez sélectionner la coche d’un appareil pour afficher les détails de l’appareil, les données d’annuaire, les alertes actives et les utilisateurs connectés. Sélectionnez le nom de l’appareil pour afficher les détails de l’appareil dans l’inventaire des appareils Defender pour point de terminaison. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Page relative à l’option Inventaire de l’appareil dans le Microsoft Defender pour point de terminaison." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

À partir de la page de l’appareil, vous pouvez collecter des informations supplémentaires sur l’appareil, telles que toutes ses alertes, une chronologie et des recommandations de sécurité. Par exemple, à partir de l’onglet **Chronologie** , vous pouvez faire défiler la chronologie de l’ordinateur et afficher tous les événements et comportements observés sur l’ordinateur dans l’ordre chronologique, entrecoupés des alertes déclenchées.

> [!TIP]
> Vous pouvez effectuer des analyses à la demande sur une page d’appareil. Dans le portail Microsoft 365 Defender, choisissez **Points de terminaison > Inventaire des appareils**. Sélectionnez un appareil qui a des alertes, puis exécutez une analyse antivirus. Les actions, telles que les analyses antivirus, sont suivies et sont visibles sur la page **Inventaire des** appareils. Pour plus d’informations, consultez [Exécuter l’analyse antivirus Microsoft Defender sur les appareils](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Utilisateurs

**L’onglet Utilisateurs** répertorie tous les utilisateurs qui ont été identifiés comme faisant partie ou liés à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Page Utilisateurs dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

Vous pouvez sélectionner la coche pour un utilisateur afin d’afficher les détails de la menace, de l’exposition et des informations de contact du compte d’utilisateur. Sélectionnez le nom d’utilisateur pour afficher des détails supplémentaires sur le compte d’utilisateur.

Découvrez comment afficher des informations supplémentaires sur les utilisateurs et gérer les utilisateurs d’un incident dans [examiner les utilisateurs](investigate-users.md).

## <a name="mailboxes"></a>Boîtes aux lettres

L’onglet **Boîtes aux lettres** répertorie toutes les boîtes aux lettres qui ont été identifiées comme faisant partie ou liées à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Page Boîtes aux lettres d’un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Vous pouvez sélectionner la coche d’une boîte aux lettres pour afficher la liste des alertes actives. Sélectionnez le nom de la boîte aux lettres pour afficher des détails supplémentaires sur la page Explorateur pour Defender pour Office 365.

## <a name="investigations"></a>Enquêtes

L’onglet **Investigations** répertorie toutes les [investigations automatisées](m365d-autoir.md) déclenchées par les alertes dans cet incident. Les investigations automatisées effectuent des actions de correction ou attendent l’approbation de l’analyste des actions, selon la façon dont vous avez configuré vos investigations automatisées pour qu’elles s’exécutent dans Defender pour point de terminaison et Defender pour Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Page Investigations d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-investigations.png":::

Sélectionnez une investigation pour accéder à sa page de détails pour obtenir des informations complètes sur l’état de l’investigation et de la correction. Si des actions sont en attente d’approbation dans le cadre de l’examen, elles s’affichent sous l’onglet **Historique des actions en attente** . Prenez des mesures dans le cadre de la correction des incidents.

Il existe également un onglet **Graphe d’investigation** qui montre :

- Connexion des alertes aux ressources affectées dans votre organisation.
- Quelles entités sont liées aux alertes et comment elles font partie de l’histoire de l’attaque.
- Alertes pour l’incident.

Le graphique d’investigation vous permet de comprendre rapidement l’étendue complète de l’attaque en connectant les différentes entités suspectes qui font partie de l’attaque à leurs ressources associées, telles que les utilisateurs, les appareils et les boîtes aux lettres. 

Pour plus d’informations, consultez [Investigation et réponse automatisées dans Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Preuve et réponse

L’onglet **Preuve et réponse** affiche tous les événements pris en charge et les entités suspectes dans les alertes de l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Page Preuve et réponse pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender examine automatiquement tous les événements pris en charge par les incidents et les entités suspectes dans les alertes, en vous fournissant des informations sur les e-mails, fichiers, processus, services, adresses IP et bien plus encore. Cela vous permet de détecter et de bloquer rapidement les menaces potentielles dans l’incident.

Chacune des entités analysées est marquée avec un verdict (Malveillant, Suspect, Propre) et un état de correction. Cela vous permet de comprendre l’état de la correction de l’incident entier et les étapes suivantes qui peuvent être effectuées.

## <a name="next-steps"></a>Prochaines étapes

Selon les besoins :

- [Examiner les alertes d’un incident](investigate-alerts.md)
- [Examiner les utilisateurs d’un incident](investigate-users.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)
