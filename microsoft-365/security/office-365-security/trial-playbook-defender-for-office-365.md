---
title: Manuel d’Office 365 Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: Manuel de solutions de Microsoft Defender pour Office 365
ms.openlocfilehash: f23c45d117735997c219278621be7f314602cd8f
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130689"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Livre d’essai : Microsoft Defender pour Office 365

Bienvenue dans Microsoft Defender pour Office 365 d’essai Ce manuel vous aidera à mettre à jour votre version d’essai gratuite de 90 jours en vous enseignant à protéger votre organisation avec Defender pour Office 365. À l'aide des recommandations de Microsoft Corporation, vous apprendrez comment Defender for Office 365 peut vous aider à définir des politiques de protection, à analyser les menaces qui pèsent sur votre organisation et à répondre aux attaques.

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="Représentation graphique de tous les composants de Microsoft Defender pour Office 365." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

Ces actions sont des recommandations de l’équipe Microsoft Defender sur les fonctionnalités clés à essayer dans votre version d’essai de 90 jours.

## <a name="step-1-getting-started"></a>Étape 1 : mise en place

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Démarrer votre version d’Office 365 Microsoft Defender

Une fois que vous avez lancé la version d’évaluation et terminé le processus d’installation, l’application des modifications peut prendre jusqu’à 2 heures.

Nous avons configuré automatiquement des stratégies de sécurité [prédéfinies](preset-security-policies.md) dans votre environnement. Ces stratégies représentent un profil de protection de référence adapté à la plupart des utilisateurs. La protection standard inclut :

- Liens fiables, pièces jointes fiables et stratégies anti-hameçonnage qui s’appliquent à l’ensemble du locataire ou au sous-ensemble d’utilisateurs que vous avez peut-être choisis pendant le processus de configuration de l’évaluation.
- Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.
- Protection des liens fiables pour les applications Office 365 prises en charge.

Regardez cette vidéo pour en savoir plus : Protégez-vous contre les liens malveillants avec Coffre liens dans [Microsoft Defender pour Office 365 - YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>Permettre aux utilisateurs de signaler du contenu suspect

Microsoft Defender pour Office 365 permet aux utilisateurs de signaler des messages à leurs équipes de sécurité et permet aux administrateurs de soumettre des messages à Microsoft Corporation pour analyse.

- Déployez [le macro complémentaire Message de rapport ou le module de signalement du hameçonnage.](enable-the-report-message-add-in.md)
- Établir un flux de travail pour [signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- Utilisez le [portail soumissions.](admin-submission.md)

Regardez cette vidéo pour en savoir plus : Découvrez comment utiliser le portail Soumissions pour soumettre des messages pour analyse [- YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>Examiner les rapports pour comprendre le paysage des menaces

Utilisez les fonctionnalités de rapport dans Defender pour Office 365 pour obtenir plus de détails sur votre environnement.

- Comprendre les menaces reçues dans les outils de collaboration et de messagerie à l’aide du rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)
- Découvrez où les menaces sont bloquées avec le [rapport d’état du flux de messagerie.](view-email-security-reports.md#mailflow-status-report)
- [Consultez les](view-reports-for-mdo.md#url-protection-report) liens qui ont été vus par les utilisateurs ou bloqués par le système.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="Rapports de messagerie et de collaboration dans le portail Microsoft 365 Defender" lightbox="../../media/mdo-trial-playbook-reporting.png":::

## <a name="step-2-intermediate-steps"></a>Étape 2 : Étapes intermédiaires

### <a name="prioritize-focus-on-your-most-targeted-users"></a>Hiérarchiser le focus sur vos utilisateurs les plus ciblés

Protégez vos utilisateurs les plus ciblés et les plus visibles avec la protection de compte prioritaire dans Defender pour Office 365, ce qui vous permet de hiérarchiser votre flux de travail pour garantir la sécurité de ces utilisateurs.

- Identifiez vos utilisateurs les plus ciblés ou les plus visibles.
- [Marquez ces utilisateurs](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) en tant que comptes prioritaires.
- Suivre les menaces qui pèsent sur le compte prioritaire dans l’ensemble du portail

Regardez cette vidéo pour en savoir plus : Protection des comptes de priorité dans [Microsoft Defender pour Office 365 - YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

:::image type="content" source="../../media/mdo-trial-playbook-alerts.png" alt-text="Alertes dans le portail Microsoft 365 Defender" lightbox="../../media/mdo-trial-playbook-alerts.png":::

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Éviter les violations coûteuses en empêchant la compromission de l’utilisateur

Recevez des alertes sur les compromissions potentielles et limitez automatiquement l’impact de ces menaces afin d’empêcher les personnes malveillantes d’obtenir un accès plus approfondi à votre environnement.

- Passer en [revue les alertes utilisateur compromises](address-compromised-users-quickly.md#compromised-user-alerts)
- [Examiner les utilisateurs](address-compromised-users-quickly.md) compromis et y répondre

:::image type="content" source="../../media/mdo-trial-playbook-investigation.png" alt-text="Examen des utilisateurs compromis" lightbox="../../media/mdo-trial-playbook-investigation.png":::

Regardez cette vidéo pour en savoir plus : détecter les compromissions et y répondre dans [Microsoft Defender Office 365 - YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Utiliser l’Explorateur de menaces pour examiner les e-mails malveillants

Defender pour Office 365 vous permet d’examiner les activités qui exposent des personnes de votre organisation à des risques et de prendre des mesures pour protéger votre organisation. Pour ce faire, utilisez l’[Explorateur de menaces](threat-explorer.md).

- [Rechercher les messages suspects](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered)qui ont été remis : recherchez et supprimez des messages, identifiez l’adresse IP d’un expéditeur de courrier malveillant ou démarrez un incident pour un examen plus approfondie.
- [Vérifiez l’action de remise et l’emplacement](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): cette vérification vous permet de connaître l’emplacement des messages électroniques problématiques.
- [Afficher la chronologie de votre courrier électronique](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): recherchez simplement votre équipe des opérations de sécurité.

### <a name="see-campaigns-targeting-your-organization"></a>Afficher les campagnes ciblant votre organisation

Affichez une image plus globale des affichages campagne dans Defender pour Office 365, ce qui vous donne une vue d’ensemble des campagnes d’attaque ciblant votre organisation et de l’impact qu’elles ont sur vos utilisateurs.

- [Identifiez les campagnes](campaigns.md#what-is-a-campaign) ciblant vos utilisateurs.
- [Visualisez l’étendue](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) de l’attaque.
- [Suivre l’interaction des](campaigns.md#campaign-details) utilisateurs avec ces messages

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="Détails de la campagne dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

Regardez cette vidéo pour en savoir plus : [Vues de campagne dans Microsoft Defender pour Office 365 - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>Utiliser l’automatisation pour corriger les risques

Répondre efficacement à l’aide de l’examen et de la réponse automatisés (AIR) pour examiner, hiérarchiser et répondre aux menaces

- [En savoir plus](automated-investigation-response-office.md) sur les manuels d’investigation
- [Afficher les détails et les résultats d’une](email-analysis-investigations.md) enquête
- Éliminer les menaces en [approuvant les actions de correction](air-remediation-actions.md)

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="Résultats de l’examen" lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

## <a name="step-3-advanced-content"></a>Étape 3 : Contenu avancé

### <a name="dive-deep-into-data-with-query-based-hunting"></a>Entrer en profondeur dans les données avec le hunting basé sur une requête

Utilisez la chasse avancée pour rédiger des règles de détection personnalisées, inspecter de manière proactive les événements dans votre environnement et localiser les indicateurs de menace. Explorez les données brutes de votre environnement.

- [Créer des règles de détection personnalisées](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting)
- [Accéder aux requêtes partagées créées](../defender/advanced-hunting-shared-queries.md) par d’autres personnes

Regardez cette vidéo pour en savoir plus : [recherche de menaces avec Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Former les utilisateurs à repérer les menaces en simulant des attaques

Former vos utilisateurs avec les connaissances adéquates pour identifier les menaces et signaler les messages suspects avec une formation de simulation d’attaque dans Defender Office 365.

- [Simuler des menaces réalistes pour](attack-simulation-training.md) identifier les utilisateurs vulnérables
- [Affecter une formation aux](attack-simulation-training.md#assign-training) utilisateurs en fonction des résultats de simulation
- [Suivre l’avancement](attack-simulation-training-insights.md) de votre organisation dans les simulations et l’achèvement de la formation

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Les informations d’entraînement de simulation d’attaque dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>Ressources supplémentaires

- **Guide interactif**: Vous ne connaissez pas Defender pour Office 365? Examinez [le guide interactif](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) pour comprendre comment commencer.
- **Microsoft docs**: Obtenez des informations détaillées sur le fonctionnement de Defender pour Office 365 et sur la meilleure façon de le mettre en œuvre pour votre organisation. Visitez [Docs](overview.md).
- **Éléments inclus :** pour obtenir la liste complète des fonctionnalités de sécurité Office 365 courrier électronique répertoriées par niveau de produit, consultez la [matrice des fonctionnalités.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability)
- **Pourquoi Microsoft Defender pour Office 365**: The [Defender for Office 365 Datasheet](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) affiche les 10 principales raisons pour lesquelles les clients choisissent Microsoft Corporation.
