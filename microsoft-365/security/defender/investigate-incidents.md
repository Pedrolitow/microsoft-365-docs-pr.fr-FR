---
title: Examiner les incidents dans Microsoft 365 Defender
description: Examiner les incidents liés aux appareils, aux utilisateurs et aux boîtes aux lettres.
keywords: incident, incidents, analyse, réponse, ordinateurs, appareils, utilisateurs, identités, courrier électronique, boîte aux lettres, enquête, graphique, preuve
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
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: dcfc3bd0e06e0bdca6c834e947d7d136af47fde3
ms.sourcegitcommit: 3b9fab82d63aea41d5f544938868c5d2cbf52d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52782824"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Examiner les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Microsoft 365 Defender regroupe toutes les alertes, biens, enquêtes et preuves connexes de vos appareils, utilisateurs et boîtes aux lettres dans un incident pour vous donner une vue d’ensemble complète d’une attaque.

Au sein d’un incident, vous analysez les alertes qui affectent votre réseau, comprenez ce qu’elles signifient et rassemblez les preuves afin de pouvoir mettre au point un plan de correction efficace.

## <a name="initial-investigation"></a>Examen initial

Avant de vous plonger dans les détails, jetez un œil aux propriétés et à la synthèse de l’incident.

Vous pouvez commencer par sélectionner l’incident dans la colonne de coche. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Exemple de sélection d’un incident dans la colonne de coche":::

Lorsque vous le faites, un volet récapitulatif s’ouvre avec des informations clés sur l’incident, telles que la gravité, à qui il est affecté, et les catégories [MITRE ATT &trade;&CK](https://attack.mitre.org/) pour l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Exemple de volet récapitulatif pour un incident":::

À partir de là, vous pouvez sélectionner **Ouvrir la page Incident.** Cela ouvre la page principale de l’incident où vous trouverez des informations récapitulatifs et des onglets pour les alertes, les appareils, les utilisateurs, les enquêtes et les preuves.

Vous pouvez également ouvrir la page principale d’un incident en sélectionnant le nom de l’incident dans la file d’attente des incidents.

## <a name="summary"></a>Résumé

La page **Résumé** vous donne un aperçu instantané des principaux éléments à noter concernant l’incident.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Exemple de page Résumé d’un incident dans le centre de Microsoft 365 de sécurité":::

Les catégories d’attaques vous donnent une vue visuelle et numérique de l’avancement de l’attaque par rapport à la chaîne d’attaque. Comme avec d’autres produits de sécurité Microsoft, Microsoft 365 Defender est aligné sur l’infrastructure [MITRE ATT&&trade; CK.](https://attack.mitre.org/)

La section l'étendue fournit la liste des principales ressources affectées à cet incident. S’il existe des informations spécifiques sur cet élément (par exemple, niveau de risque, priorité d’examen, et balisage sur les éléments) qui s’affichent également dans cette section.

La chronologie des alertes fournit un aperçu de l’ordre chronologique dans lequel les alertes se sont produites, ainsi que les raisons pour lesquelles ces alertes sont liées à cet incident.

Enfin, la section preuve fournit un résumé du nombre d’artefacts différents inclus dans l’incident et de leur état de correction, afin que vous pouvez immédiatement identifier si vous avez besoin d’une action.

Cette vue d’ensemble peut vous aider dans le tri initial de l’incident en fournissant des informations sur les principales caractéristiques de l’incident que vous devez connaître.

## <a name="alerts"></a>Alertes

Sous **l’onglet** Alerte, vous pouvez afficher la file d’attente d’alertes pour les alertes liées à l’incident et d’autres informations les concernant, telles que :

- Gravité.
- Entités impliquées dans l’alerte.
- Source des alertes (Microsoft Defender pour l’identité, Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365).
- Raison pour laquelle ils ont été liés.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Exemple de page Alertes pour un incident":::

Par défaut, les alertes sont classés dans l’ordre chronologique pour vous permettre de voir comment l’incident s’est produit au fil du temps. Lorsque vous sélectionnez une alerte dans un incident, Microsoft 365 Defender affiche les informations d’alerte spécifiques au contexte de l’incident global. 

Vous pouvez voir les événements de l’alerte, dont d’autres alertes déclenchées ont provoqué l’alerte actuelle, ainsi que toutes les entités et activités concernées impliquées dans l’attaque, y compris les fichiers, les utilisateurs et les boîtes aux lettres.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Exemple de page de détails d’alerte dans un incident":::

Cette page d’alerte d’incident se compose des sections suivantes :

- Article sur l’alerte, qui inclut un résumé de ce qui s’est passé
- Événements et alertes connexes
- Détails récapitulatifs

Découvrez comment utiliser la file d’attente d’alertes et les pages d’alerte pour [examiner les alertes.](investigate-alerts.md)

## <a name="devices"></a>Appareils

**L’onglet Appareils** répertorie tous les appareils liés à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Exemple de page Appareils pour un incident":::

Vous pouvez cocher la coche d’un appareil pour voir les détails de l’appareil, les données d’annuaire, les alertes actives et les utilisateurs connectés. Sélectionnez le nom de l’appareil pour voir les détails de l’appareil dans l’inventaire des appareils Microsoft Defender pour les points de terminaison.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Exemple de page d’appareils pour Microsoft Defender pour les points de terminaison":::

Dans la page appareil, vous pouvez collecter des informations supplémentaires sur l’appareil, telles que toutes ses alertes, une chronologie et des recommandations de sécurité. Par exemple,  à partir de l’onglet Chronologie, vous pouvez parcourir la chronologie de l’ordinateur et afficher tous les événements et comportements observés sur l’ordinateur dans l’ordre chronologique, entrecoupés des alertes.

> [!TIP]
> Vous pouvez faire des analyses à la demande sur une page d’appareil. Dans le centre Microsoft 365 de sécurité, choisissez Points de **terminaison >'inventaire des appareils.** Sélectionnez un appareil qui a des alertes, puis exécutez une analyse antivirus. Les actions, telles que les analyses antivirus, sont suivis et sont visibles sur la page **d’inventaire des** appareils. Pour plus d’informations, voir [Exécuter Antivirus Microsoft Defender’analyse sur les appareils.](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices)

## <a name="users"></a>Utilisateurs

**L’onglet** Utilisateurs répertorie tous les utilisateurs identifiés comme faisant partie ou associés à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Exemple de page Utilisateurs pour un incident":::

Vous pouvez cocher la coche d’un utilisateur pour voir les détails de la menace, de l’exposition et des informations de contact du compte d’utilisateur. Sélectionnez le nom d’utilisateur pour voir les détails supplémentaires du compte d’utilisateur.

Découvrez comment afficher des informations utilisateur supplémentaires et gérer les utilisateurs d’un incident dans [l’examen des utilisateurs.](investigate-users.md)


## <a name="mailboxes"></a>Boîtes aux lettres

**L’onglet Boîtes** aux lettres répertorie toutes les boîtes aux lettres qui ont été identifiées comme faisant partie ou associées à l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Exemple de page Boîtes aux lettres pour un incident":::

Vous pouvez cocher la coche d’une boîte aux lettres pour voir la liste des alertes actives. Sélectionnez le nom de la boîte aux lettres pour voir des détails supplémentaires sur la page Explorateur de Microsoft Defender pour Office 365.

## <a name="investigations"></a>Examens

**L’onglet** Enquêtes répertorie toutes les [enquêtes](m365d-autoir.md) automatisées déclenchées par les alertes dans cet incident. Les enquêtes effectuent des actions de correction ou attendent l’approbation par un analyste des actions, selon la façon dont vous avez configuré vos enquêtes automatisées pour qu’ils s’exécutent dans Microsoft Defender pour Endpoint et Defender pour Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Exemple de page Investigations pour un incident":::

Sélectionnez un examen pour accéder à la page Détails de l’examen pour obtenir des informations complètes sur l’état l’examen et de la correction. Si des actions sont en attente d’approbation dans le cadre de l’examen, elles apparaissent dans l’onglet Actions en attente. Prendre des mesures dans le cadre de la correction des incidents.

Pour plus d’informations, voir [Examen automatisé et réponse dans Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Preuve et réponse

**L’onglet Preuve et réponse** affiche tous les événements pris en charge et entités suspectes dans les alertes de l’incident. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Exemple de page Preuve et réponse pour un incident":::

Microsoft 365 Defender examine automatiquement tous les événements pris en charge par les incidents et les entités suspectes dans les alertes, en vous fournissant des informations sur les messages électroniques, fichiers, processus, services, adresses IP et bien plus encore. Cela vous permet de détecter et de bloquer rapidement les menaces potentielles dans l’incident.

Chacune des entités analysées est marquée avec un verdict (malveillant, suspect, propre) et un état de correction. Cela vous permet de comprendre l’état de correction de l’intégralité de l’incident et les étapes suivantes qui peuvent être prises.

## <a name="graph-in-preview"></a>Graph (en prévisualisation)

Avec le nouvel **onglet Graph** (en prévisualisation), vous pouvez voir :

- La connexion des alertes aux biens touchés dans votre organisation.
- Les entités liées aux alertes et à la façon dont elles font partie de l’article de l’attaque.
- Alertes pour l’incident.

Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-graph.png" alt-text="Exemple de page de Graph pour un incident":::

Le graphique d’incident vous permet de comprendre rapidement l’étendue complète de l’attaque en connectant les différentes entités suspectes faisant partie de l’attaque avec leurs biens connexes tels que les utilisateurs, les périphériques et les boîtes aux lettres. 

Vous pouvez maintenant comprendre comment l’attaque s’est propagée sur votre réseau au fil du temps, où elle a commencé et jusqu’où l’attaque s’est étendue.

## <a name="next-steps"></a>Prochaines étapes

Selon les besoins :

- [Examiner les alertes d’un incident](investigate-alerts.md)
- [Examiner les utilisateurs d’un incident](investigate-users.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)

