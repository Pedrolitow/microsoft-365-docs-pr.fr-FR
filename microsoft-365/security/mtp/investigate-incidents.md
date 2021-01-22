---
title: Examiner les incidents dans Microsoft 365 Defender
description: Analyser les incidents liés aux appareils, aux utilisateurs et aux boîtes aux lettres.
keywords: incident, incidents, ordinateurs, appareils, utilisateurs, identités, courrier, courrier électronique, boîte aux lettres, investigation, graphique, preuves
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
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
ms.openlocfilehash: 6a3bd6be81b4ea4ef11a366267d7a36d45e622b9
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49926893"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Examiner les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**

- Microsoft 365 Defender

Microsoft 365 Defender regroupe toutes les alertes, biens, enquêtes et preuves connexes sur vos appareils, utilisateurs et boîtes aux lettres pour vous donner une vue d’ensemble complète d’une attaque.

Examinez les alertes qui affectent votre réseau, déterminez leur signification et rassemblez des preuves associées aux incidents pour mettre en place une formule corrective efficace.

## <a name="investigate-an-incident"></a>Examiner un incident

1. Sélectionnez un incident dans la file d’attente des incidents. <BR> Un panneau latéral s’ouvre et donne un aperçu des informations importantes telles que l’état, la gravité, les catégories et les entités impactées.

    ![Image du volet latéral de l’incident](../../media/incident-side-panel.png)

2. Sélectionnez **Ouvrir la page incident**. <BR> Cette action ouvre la page incident dans laquelle vous trouverez plus d’informations sur les incidents, les commentaires et les actions, les onglets (vue d’ensemble, alertes, appareils, utilisateurs, enquêtes, preuves).

3. Examinez les alertes, les appareils, les utilisateurs et les autres entités impliquées dans l’incident.

## <a name="incident-overview"></a>Présentation de l’incident

La page de présentation vous permet d’accéder à un instantané de l’événement.

![Image de la page de présentation des incidents](../../media/incidents-overview.png)

Les catégories d’attaques vous donnent une vue visuelle et numérique de l’avancement de l’attaque par rapport à la chaîne d’attaque. Comme avec d’autres produits de sécurité Microsoft, Microsoft 365 Defender est aligné sur l’infrastructure [MITRE ATT&&trade; CK.](https://attack.mitre.org/)

La section l'étendue fournit la liste des principales ressources affectées à cet incident. S’il existe des informations spécifiques sur cet élément (par exemple, niveau de risque, priorité d’examen, et balisage sur les éléments) qui s’affichent également dans cette section.

La chronologie des alertes fournit un aperçu de l’ordre chronologique dans lequel les alertes se sont produites, ainsi que les raisons pour lesquelles ces alertes sont liées à cet incident.

Enfin, la section preuves fournit un résumé du nombre d’artefacts différents qui ont été inclus dans l’incident et de leur état de correction, pour que vous puissiez identifier immédiatement toute action nécessaire à la fin de l’opération.

Cette vue d’ensemble peut vous aider à procéder au triage initial de l’incident en fournissant un aperçu des principales caractéristiques de l’incident que vous devez connaître.

## <a name="alerts"></a>Alertes

Vous pouvez afficher toutes les alertes liées à l’incident et d’autres informations les concernant, telles que la gravité, les entités impliquées dans l’alerte, la source des alertes (Microsoft Defender pour l’identité, Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365) et la raison pour laquelle elles ont été liées.

![Image de la page alertes d’incident](../../media/incident-alerts.png)

Par défaut, les alertes sont classées par ordre chronologique, pour vous permettre de consulter d’abord l’attaque au fil du temps. Cliquez sur chaque alerte pour vous diriger vers la page d’alerte pertinente où vous pouvez effectuer un examen approfondi de cette alerte.

## <a name="devices"></a>Appareils

L’onglet appareils répertorie tous les appareils pour lesquels des alertes liées à l’incident sont affichées.

En cliquant sur le nom de l’ordinateur sur lequel l’attaque a eu lieu, vous d’accéder à la page de l’ordinateur dans laquelle vous pouvez voir les alertes qui ont été déclenchées et les événements connexes fournis pour simplifier l’examen.

![Image de l’onglet ordinateurs d’un incident](../../media/incident-machines.png)

La sélection de l’onglet chronologie vous permet de faire défiler la chronologie de l’ordinateur et d’afficher tous les événements et comportements observés sur l’ordinateur dans l’ordre chronologique, accompagnés des alertes générées.

## <a name="users"></a>Utilisateurs

Consultez la liste des utilisateurs qui ont été identifiés comme faisant partie d'un incident donné ou y étant liés.

En cliquant sur le nom d'utilisateur, vous accédez à la page Cloud App Security de l'utilisateur où un examen plus approfondie peut être effectuée.

![Image de l’onglet utilisateurs d’un incident](../../media/incident-users.png)

## <a name="mailboxes"></a>Boîtes aux lettres

Examinez les boîtes aux lettres qui ont été identifiés comme faisant partie d'un incident ou y étant liés. Pour poursuivre l’examen, la sélection de l’alerte liée à la messagerie ouvre Microsoft Defender pour Office 365 où vous pouvez prendre des mesures correctives.

![Image de l’onglet boîte aux lettres d’un incident](../../media/incident-mailboxes.png)

## <a name="investigations"></a>Examens

Sélectionnez **Examens** pour voir toutes les enquêtes automatisées déclenchées par des alertes dans cet incident. Les enquêtes effectueront des actions de correction ou attendront l’approbation par un analyste des actions, selon la façon dont vous avez configuré vos enquêtes automatisées pour qu’ils s’exécutent dans Microsoft Defender pour Endpoint et Defender pour Office 365.

![Image de l’onglet examens d’un incident](../../media/incident-investigations.png)

Sélectionnez un examen pour accéder à la page Détails de l’examen pour obtenir des informations complètes sur l’état l’examen et de la correction. Si des actions sont en attente d’approbation dans le cadre de l’examen, elles apparaissent dans l’onglet Actions en attente. Prendre des mesures dans le cadre de la correction des incidents.

## <a name="evidence"></a>Évidence

Microsoft 365 Defender examine automatiquement tous les événements pris en charge par les incidents et les entités suspectes dans les alertes, en vous fournissant des réponse automatiques et des informations sur les fichiers, processus, services, e-mails et bien plus encore. Cela permet de détecter et de bloquer rapidement les menaces potentielles dans l’incident.

![Image de l’onglet preuve d’un incident](../../media/incident-evidence.png)

Chacune des entités analysées est signalée par un verdict (malveillant, Suspect, Sain) ainsi qu’un état de correction. Cela vous permet de comprendre l’état de la correction de l’ensemble de l’incident et les prochaines étapes à suivre pour la correction.

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)

