---
title: Étape 1. Trier et analyser votre premier incident
description: Comment trier et commencer l’analyse de votre premier incident dans Microsoft 365 Defender.
keywords: incidents, alertes, examen, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 596966c7c1975ebb8f20b306be5e4ab0a34bd99e
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893636"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Étape 1. Trier et analyser votre premier incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Lorsque vous passez du temps à établir, implémenter et maintenir des mesures de sécurité conformément aux normes de l’organisation, vous pouvez configurer des solutions de sécurité pour vous aider à identifier rapidement les risques et menaces de sécurité. Microsoft 365 Defender vous permet de détecter, de trier et d’examiner les incidents par le biais de son expérience à volet unique où vous pouvez trouver les informations dont vous avez besoin pour prendre des décisions en temps opportun.

Une fois qu’un incident de sécurité est détecté, Microsoft 365 Defender présente les détails dont vous aurez besoin pour trier ou hiérarchiser un incident ou des incidents par rapport à d’autres. Après avoir déterminé la définition des priorités, les analystes peuvent alors concentrer leur énergie sur l’examen des cas qui leur sont attribués.

## <a name="detection-by-microsoft-365-defender"></a>Détection par Microsoft 365 Defender

Microsoft 365 Defender reçoit des alertes et des événements de plusieurs plateformes de sécurité Microsoft en tant que sources de détection pour créer une image holistique et un contexte d’activité malveillante. Les sources de détection possibles sont les suivantes :

- [Microsoft Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md) est une solution de détection et de réponse de point de terminaison (EDR) qui utilise l’antivirus Microsoft Defender et la protection avancée contre les menaces compatible avec le cloud à l’aide de Microsoft Security Graph. Defender pour point de terminaison est une plateforme unifiée pour la protection préventive, la détection post-violation, l’investigation automatisée et la réponse. Il protège les points de terminaison contre les cybermenaces, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la posture de sécurité.
- [Microsoft Defender pour Identity](/defender-for-identity/what-is) est une solution de sécurité basée sur le cloud qui utilise vos signaux AD DS (Domain Services) Active Directory local pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) agit en tant que gardien pour répartit l’accès en temps réel entre vos utilisateurs d’entreprise et les ressources cloud qu’ils utilisent, où que vos utilisateurs se trouvent et quel que soit l’appareil qu’ils utilisent.
- [Microsoft Defender pour Office 365](../office-365-security/overview.md) protège votre organisation contre les menaces malveillantes dans les e-mails, les liens (URL) et les outils de collaboration.
- [Azure Security Center](/azure/security-center/security-center-introduction) est un système unifié de gestion de la sécurité de l’infrastructure qui renforce la posture de sécurité de vos centres de données et fournit une protection avancée contre les menaces sur vos charges de travail hybrides dans le cloud et localement.


Dans Microsoft 365 Defender, [les incidents sont identifiés](incidents-overview.md) en mettant en corrélation les alertes provenant de ces différentes sources de détection. Au lieu de regrouper des ressources ou de distinguer plusieurs alertes dans leurs incidents respectifs, vous pouvez commencer par la file d’attente d’incidents dans Microsoft 365 Defender immédiatement. Cette approche vous permet de trier efficacement les incidents entre les points de terminaison, les identités, les e-mails et les applications, et de réduire les dommages causés par une attaque.

## <a name="triage-your-incidents"></a>Trier vos incidents

La réponse aux incidents dans Microsoft 365 Defender démarre une fois que vous avez trié la liste des incidents à l’aide de la méthode recommandée de hiérarchisation de votre organisation. Trier signifie affecter un niveau d’importance ou d’urgence aux incidents, qui détermine ensuite l’ordre dans lequel ils seront examinés.

Un exemple de guide utile pour déterminer l’incident à hiérarchiser dans Microsoft 365 Defender peut être résumé par la formule : *Gravité + Impact = Priorité*.

- **La gravité** est le niveau désigné par Microsoft 365 Defender et ses composants de sécurité intégrés.
- **L’impact** est déterminé par l’organisation et inclut généralement, sans s’y limiter, un nombre seuil d’utilisateurs, d’appareils, de services affectés (ou une combinaison) et même un type d’alerte.

Les analystes lancent ensuite des investigations en fonction des critères **de priorité** définis par l’organisation.

La définition des priorités d’incident peut varier en fonction de l’organisation. NIST recommande également de prendre en compte l’impact fonctionnel et informationnel de l’incident et la capacité de récupération.

Une approche de triage est décrite ci-dessous :

1. Accédez à la page [incidents](incidents-overview.md) pour lancer le triage. Vous pouvez voir ici une liste d’incidents affectant votre organisation. Par défaut, ils sont organisés de l’incident le plus récent au plus ancien. À partir de là, vous pouvez également voir différentes colonnes pour chaque incident montrant leur gravité, leur catégorie, le nombre d’alertes actives et les entités affectées, entre autres. Vous pouvez personnaliser l’ensemble de colonnes et trier la file d’attente d’incidents en fonction de certaines de ces colonnes en sélectionnant le nom de colonne. Vous pouvez également filtrer la file d’attente d’incidents en fonction de vos besoins. Pour obtenir la liste complète des filtres disponibles, consultez [Hiérarchiser les incidents](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Incidents dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    Un exemple de la façon dont vous pouvez effectuer le triage pour cet ensemble d’incidents consiste à hiérarchiser les incidents qui ont affecté davantage d’utilisateurs et d’appareils. Dans cet exemple, vous pouvez hiérarchiser l’ID d’incident 6769, car il a affecté le plus grand nombre d’entités : sept appareils, six utilisateurs et deux boîtes aux lettres. En outre, l’incident semble contenir des alertes de Microsoft Defender pour Identity, qui indiquent une alerte basée sur l’identité et un vol d’informations d’identification possible.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Page Incidents** montrant un exemple d’incident à fort impact dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. Sélectionnez le cercle en regard du nom de l’incident pour passer en revue les détails. Un volet latéral s’affiche sur le côté droit, qui contient des informations supplémentaires susceptibles d’aider votre triage.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Page Incidents montrant un exemple de volet côté incident dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   Par exemple, en examinant les tactiques [MITRE ATT&CK](https://attack.mitre.org/) utilisées par l’attaquant en fonction des catégories de l’incident, vous pouvez hiérarchiser cet incident, car l’attaquant a utilisé des informations d’identification volées, établi la commande et le contrôle, effectué un mouvement latéral et exfiltré certaines données. Ces actions suggèrent que l’attaquant a déjà approfondi le réseau et peut-être volé des informations confidentielles.

   En outre, si votre organisation a implémenté l’infrastructure Confiance nulle, vous considéreriez l’accès aux informations d’identification comme une violation importante de la sécurité qui mérite d’être prioritaire.

   En faisant défiler le volet latéral, vous verrez les entités concernées spécifiques, telles que les utilisateurs, les appareils et les boîtes aux lettres. Vous pouvez vérifier le niveau d’exposition de chaque appareil et des propriétaires des boîtes aux lettres concernées.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Détails du volet côté incident" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. Plus loin dans le volet latéral, vous trouverez les alertes associées. Microsoft 365 Defender a déjà effectué la corrélation de ces alertes en un seul incident, ce qui vous permet de gagner du temps et des ressources pour résoudre l’attaque. Les alertes sont suspectes et peuvent donc être des événements système malveillants qui suggèrent la présence d’un attaquant sur un réseau.

   Dans cet exemple, 87 alertes individuelles ont été déterminées comme faisant partie d’un incident de sécurité. Vous pouvez afficher toutes les alertes pour obtenir un aperçu rapide de la façon dont l’attaque s’est produite.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Alertes dans un volet côté incident dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>Analyser votre premier incident

Il est tout aussi important de comprendre le contexte qui entoure les alertes. Souvent, une alerte n’est pas un seul événement indépendant. Il existe une chaîne de processus créés, de commandes et d’actions qui n’ont peut-être pas eu lieu en même temps. Par conséquent, un analyste doit rechercher la première et la dernière activité de l’entité suspecte dans les chronologies de l’appareil pour comprendre le contexte des alertes.

Il existe plusieurs façons de lire et d’analyser des données à l’aide de Microsoft 365 Defender, mais l’objectif final pour les analystes est de répondre aux incidents le plus rapidement possible. Bien que Microsoft 365 Defender puisse réduire considérablement le [temps moyen de correction (MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) par le biais de la fonctionnalité d’investigation [et de réponse automatisée](m365d-autoir.md) de pointe, il existe toujours des cas qui nécessitent une analyse manuelle.

Voici un exemple :

1. Une fois la priorité de triage déterminée, un analyste commence une analyse approfondie en sélectionnant le nom de l’incident. Cette page affiche le **résumé des incidents** dans lequel les données sont affichées sous des onglets pour faciliter l’analyse. Sous l’onglet **Alertes** , les types d’alertes sont affichés. Les analystes peuvent cliquer sur chaque alerte pour explorer la source de détection correspondante.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Onglet Résumé d’un incident" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    Pour obtenir un guide rapide sur le domaine couvert par chaque source de détection, consultez la section [Détecter](#detection-by-microsoft-365-defender) de cet article.

2. À partir de l’onglet Alertes, vous pouvez pivoter vers la source de détection pour effectuer une investigation et une analyse plus **approfondies** . Par exemple, la sélection de la détection des programmes malveillants avec Microsoft Defender for Cloud Apps comme source de détection amène l’analyste à sa page d’alerte correspondante.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Page Incidents qui montre un exemple de sélection d’une alerte d’incident." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Page correspondante dans le Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. Pour approfondir notre exemple, faites défiler vers le bas de la page pour afficher les **utilisateurs affectés**. Pour voir l’activité et le contexte entourant la détection des programmes malveillants, sélectionnez la page utilisateur d’Annette Hill.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Page utilisateur" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. La page utilisateur répertorie les événements chronologiquement, en commençant par une connexion *risquée à partir d’une alerte d’adresse IP réseau TOR* . Bien que la suspectité d’une activité dépend de la nature de la façon dont une organisation mène son activité, dans la plupart des cas, l’utilisation de The Onion Router (TOR), un réseau qui permet aux utilisateurs de parcourir le web de manière anonyme, dans un environnement d’entreprise peut être considéré comme hautement peu probable et inutile pour les opérations en ligne régulières.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Liste chronologique des événements pour un utilisateur" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. Chaque alerte peut être sélectionnée pour obtenir plus d’informations sur l’activité. Par exemple, si vous sélectionnez **Activité à partir d’une alerte d’adresse IP Tor** , vous accédez à la propre page de cette alerte. Annette est administrateur de Office 365, ce qui indique des privilèges élevés et que l’incident source peut avoir conduit à l’accès à des informations confidentielles.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Détails des alertes pour le Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. En sélectionnant d’autres alertes, vous pouvez obtenir une image complète de l’attaque.

## <a name="next-step"></a>Étape suivante

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="Option Corriger dans la page Répondre à votre premier incident" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

Découvrez comment [corriger les incidents](first-incident-remediate.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
