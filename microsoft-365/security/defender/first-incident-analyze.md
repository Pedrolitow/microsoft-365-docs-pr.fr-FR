---
title: Étape 1. Trier et analyser votre premier incident
description: Comment trier et commencer l’analyse de votre premier incident dans Microsoft 365 Defender.
keywords: incidents, alertes, récit d’attaque, investigation, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
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
- m365-security
- m365solution-firstincident
- highpri
- tier1
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 2b3b31019b641f45f50fce229d4b7cced1002c25
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688325"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Étape 1. Trier et analyser votre premier incident

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

À mesure que vous passez du temps à établir, implémenter et gérer des mesures de sécurité conformément aux normes de l’organisation, vous pouvez configurer des solutions de sécurité pour vous aider à identifier rapidement les risques et les menaces de sécurité. Microsoft 365 Defender vous permet de détecter, de trier et d’examiner les incidents par le biais de son expérience à volet unique, où vous pouvez trouver les informations dont vous avez besoin pour prendre des décisions en temps voulu.

Une fois qu’un incident de sécurité est détecté, Microsoft 365 Defender présente les détails que vous devez trier ou hiérarchiser un ou plusieurs incidents par rapport à d’autres. Après avoir déterminé la hiérarchisation, les analystes peuvent alors concentrer leur énergie sur l’examen des cas qui leur sont assignés.

## <a name="detection-by-microsoft-365-defender"></a>Détection par Microsoft 365 Defender

Microsoft 365 Defender reçoit des alertes et des événements de plusieurs plateformes de sécurité Microsoft en tant que sources de détection pour créer une image holistique et un contexte d’activité malveillante. Les sources de détection possibles sont les suivantes :

- [Microsoft Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md) est une solution de détection et de réponse de point de terminaison (EDR) qui utilise Microsoft Defender antivirus et une protection avancée contre les menaces compatible avec le cloud à l’aide de Microsoft Security Graph. Defender pour point de terminaison est une plateforme unifiée pour la protection préventive, la détection post-violation, l’investigation automatisée et la réponse. Il protège les points de terminaison contre les cybermenaces, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la posture de sécurité.
- [Microsoft Defender pour Identity](/defender-for-identity/what-is) est une solution de sécurité basée sur le cloud qui utilise vos signaux Active Directory local Domain Services (AD DS) pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) agit comme un gardien pour répartir l’accès en temps réel entre les utilisateurs de votre entreprise et les ressources cloud qu’ils utilisent, où que vos utilisateurs se trouvent et quel que soit l’appareil qu’ils utilisent.
- [Microsoft Defender pour Office 365](/microsoft-365/office-365-security/overview) protège votre organisation contre les menaces malveillantes dans les e-mails, les liens (URL) et les outils de collaboration.
- [Azure Security Center](/azure/security-center/security-center-introduction) est un système unifié de gestion de la sécurité de l’infrastructure qui renforce la posture de sécurité de vos centres de données et fournit une protection avancée contre les menaces pour vos charges de travail hybrides dans le cloud et localement.


Dans Microsoft 365 Defender, [les incidents sont identifiés](incidents-overview.md) en corrélatant les alertes de ces différentes sources de détection. Au lieu de dépenser des ressources en chaîne ou de distinguer plusieurs alertes dans leurs incidents respectifs, vous pouvez commencer par la file d’attente des incidents dans Microsoft 365 Defender immédiatement. Cette approche vous permet de trier efficacement les incidents entre les points de terminaison, les identités, les e-mails et les applications, et de réduire les dommages causés par une attaque.

## <a name="triage-your-incidents"></a>Trier vos incidents

La réponse aux incidents dans Microsoft 365 Defender commence une fois que vous triez la liste des incidents à l’aide de la méthode recommandée de hiérarchisation de votre organisation. Le triage signifie attribuer un niveau d’importance ou d’urgence aux incidents, qui détermine ensuite l’ordre dans lequel ils seront examinés.

Un exemple de guide utile pour déterminer l’incident à hiérarchiser dans Microsoft 365 Defender peut être résumé par la formule : *Gravité + Impact = Priorité*.

- **La gravité** est le niveau désigné par Microsoft 365 Defender et ses composants de sécurité intégrés.
- **L’impact** est déterminé par l’organisation et inclut généralement, mais sans s’y limiter, un nombre seuil d’utilisateurs, d’appareils, de services affectés (ou une combinaison de ces derniers), et même le type d’alerte.

Les analystes lancent ensuite des enquêtes basées sur les critères **de priorité** définis par l’organisation.

La hiérarchisation des incidents peut varier en fonction de l’organisation. Le NIST recommande également de prendre en compte l’impact fonctionnel et informationnel de l’incident et la possibilité de récupération.

Une approche du triage est décrite ci-dessous :

1. Accédez à la page [des incidents](incidents-overview.md) pour lancer le tri. Ici, vous pouvez voir une liste des incidents affectant votre organisation. Par défaut, ils sont organisés de l’incident le plus récent au plus ancien. À partir de là, vous pouvez également voir différentes colonnes pour chaque incident montrant leur gravité, leur catégorie, le nombre d’alertes actives et les entités impactées, entre autres. Vous pouvez personnaliser l’ensemble de colonnes et trier la file d’attente des incidents en fonction de certaines de ces colonnes en sélectionnant le nom de la colonne. Vous pouvez également filtrer la file d’attente des incidents en fonction de vos besoins. Pour obtenir la liste complète des filtres disponibles, consultez [Hiérarchiser les incidents](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Les incidents dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    Un exemple de la façon dont vous pouvez effectuer le triage pour cet ensemble d’incidents consiste à hiérarchiser les incidents qui affectaient un plus grand nombre d’utilisateurs et d’appareils. Dans cet exemple, vous pouvez hiérarchiser l’ID d’incident 6769, car il a affecté le plus grand nombre d’entités : sept appareils, six utilisateurs et deux boîtes aux lettres. En outre, l’incident semble contenir des alertes de Microsoft Defender pour Identity, qui indiquent une alerte basée sur l’identité et un éventuel vol d’informations d’identification.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Page Incidents** montrant un exemple d’incident à fort impact dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. Sélectionnez le cercle en regard du nom de l’incident pour passer en revue les détails. Un volet latéral s’affiche sur le côté droit, qui contient des informations supplémentaires qui peuvent vous aider à effectuer un tri.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Page Incidents montrant un exemple de volet latéral d’incident dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   Par exemple, en examinant les tactiques [MITRE ATT&CK](https://attack.mitre.org/) utilisées par l’attaquant en fonction des catégories de l’incident, vous pouvez hiérarchiser cet incident, car l’attaquant a utilisé des informations d’identification volées, établi la commande et le contrôle, effectué un mouvement latéral et exfiltré certaines données. Ces actions suggèrent que l’attaquant a déjà approfondi le réseau et éventuellement volé des informations confidentielles.

   En outre, si votre organisation a implémenté l’infrastructure Confiance nulle, vous considérez l’accès aux informations d’identification comme une violation de sécurité importante qui mérite d’être hiérarchisé.

   En faisant défiler le volet latéral, vous verrez les entités concernées spécifiques, telles que les utilisateurs, les appareils et les boîtes aux lettres. Vous pouvez vérifier le niveau d’exposition de chaque appareil et les propriétaires des boîtes aux lettres affectées.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Détails du volet latéral de l’incident" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. Plus bas dans le volet latéral, vous trouverez les alertes associées. Microsoft 365 Defender a déjà effectué la corrélation de ces alertes en un seul incident, ce qui vous permet d’économiser du temps et des ressources pour mieux corriger l’attaque. Les alertes sont suspectes et, par conséquent, des événements système potentiellement malveillants qui suggèrent la présence d’un attaquant sur un réseau.

   Dans cet exemple, 87 alertes individuelles ont été déterminées comme faisant partie d’un incident de sécurité. Vous pouvez afficher toutes les alertes pour obtenir un aperçu rapide de la façon dont l’attaque s’est jouée.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Alertes dans le volet latéral d’un incident dans le portail de sécurité Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>Analyser votre premier incident

Il est tout aussi important de comprendre le contexte qui entoure les alertes. Souvent, une alerte n’est pas un seul événement indépendant. Il existe une chaîne de processus, de commandes et d’actions qui ne se sont peut-être pas produites en même temps. Par conséquent, un analyste doit rechercher la première et la dernière activité de l’entité suspecte dans les chronologies de l’appareil pour comprendre le contexte des alertes.

Il existe plusieurs façons de lire et d’analyser les données à l’aide de Microsoft 365 Defender mais l’objectif final des analystes est de répondre aux incidents le plus rapidement possible. Bien que Microsoft 365 Defender puissent réduire considérablement le temps moyen de [correction (MTTR) grâce à](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) la fonctionnalité d’investigation [et de réponse automatisée](m365d-autoir.md) de pointe, il existe toujours des cas qui nécessitent une analyse manuelle.

Voici un exemple :

1. Une fois que la priorité de triage a été déterminée, un analyste commence une analyse approfondie en sélectionnant le nom de l’incident. Cette page affiche **l’article d’attaque** où les données sont affichées dans des onglets pour faciliter l’analyse. Sous l’onglet **Article des alertes** , les types d’alertes s’affichent. Les analystes peuvent cliquer sur chaque alerte pour explorer la source de détection correspondante.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Capture d’écran montrant l’histoire de l’attaque d’un incident." lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    Pour obtenir un guide rapide sur le domaine couvert par chaque source de détection, consultez la section [Détecter](#detection-by-microsoft-365-defender) de cet article.

2. À partir de l’onglet **Alertes** , vous pouvez effectuer un pivot vers la source de détection pour effectuer une investigation et une analyse plus approfondies. Par exemple, en sélectionnant Détection des programmes malveillants avec Microsoft Defender for Cloud Apps comme source de détection, l’analyste est alors chargé d’accéder à la page d’alerte correspondante.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Page Incidents qui montre un exemple de sélection d’une alerte d’incident." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Page correspondante dans le Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. Pour approfondir notre exemple, faites défiler vers le bas de la page pour afficher les **utilisateurs affectés**. Pour voir l’activité et le contexte entourant la détection des programmes malveillants, sélectionnez la page utilisateur d’Annette Hill.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Une page utilisateur" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. La page utilisateur répertorie les événements par ordre chronologique, en commençant par une alerte connexion *risquée à partir d’une alerte d’adresse IP réseau TOR* . Bien que la suspicion d’une activité dépend de la nature de la façon dont une organisation mène ses activités, dans la plupart des cas, l’utilisation de The Onion Router (TOR), un réseau qui permet aux utilisateurs de parcourir le web de manière anonyme, dans un environnement d’entreprise peut être considéré comme hautement improbable et inutile pour les opérations en ligne régulières.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Liste chronologique des événements d’un utilisateur" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. Chaque alerte peut être sélectionnée pour obtenir plus d’informations sur l’activité. Par exemple, la sélection **de l’activité à partir d’une alerte Adresse IP Tor** vous mène à la page de cette alerte. Annette est administrateur de Office 365, ce qui indique des privilèges élevés et que l’incident source peut avoir conduit à l’accès à des informations confidentielles.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Détails des alertes pour le Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. En sélectionnant d’autres alertes, vous pouvez obtenir une image complète de l’attaque.

## <a name="next-step"></a>Étape suivante

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="L’option Corriger dans la page Répondre à votre premier incident" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

Découvrez comment [corriger les incidents](first-incident-remediate.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
