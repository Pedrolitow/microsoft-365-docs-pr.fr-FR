---
title: guide de l’utilisateur de Microsoft Defender pour Office 365 d’évaluation
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security
ms.localizationpriority: high
ms.service: microsoft-365-security
search.appverid:
- MOE150
- MET150
description: guide de l’utilisateur d’essai des solutions Microsoft Defender pour Office 365.
ms.subservice: mdo
ms.custom: trial-playbook
ms.openlocfilehash: 145ebc155b2ae10bfdd2b6cdb05e35746969ad2f
ms.sourcegitcommit: 7828a1e78c3e6bd8d10289f1ad6c8b6769da0966
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2022
ms.locfileid: "68495163"
---
# <a name="trial-user-guide-microsoft-defender-for-office-365"></a>Guide de l’utilisateur d’évaluation : Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bienvenue dans le guide de l’utilisateur Microsoft Defender pour Office 365 version d’évaluation ! Ce guide utilisateur vous aidera à tirer le meilleur parti de votre version d’évaluation gratuite en vous apprenant à protéger votre organisation contre les menaces malveillantes posées par les e-mails, les liens (URL) et les outils de collaboration.

## <a name="what-is-defender-for-office-365"></a>Qu’est-ce que Defender pour Office 365 ?

Defender pour Office 365 aide les organisations à sécuriser leur entreprise en offrant une gamme complète de fonctionnalités, notamment des stratégies de protection contre les menaces, des rapports, des fonctionnalités d’investigation et de réponse aux menaces, ainsi que des fonctionnalités automatisées d’investigation et de réponse.

:::image type="content" source="../../media/microsoft-defender-for-office-365.png" alt-text="Microsoft Defender pour Office 365 diagramme conceptuel." lightbox="../../media/microsoft-defender-for-office-365.png":::

Outre la détection des menaces avancées, la vidéo suivante montre comment les fonctionnalités SecOps de Defender pour Office 365 peuvent aider votre équipe à répondre aux menaces :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMmIe]

### <a name="audit-mode-vs-blocking-mode-for-defender-for-office-365"></a>Mode audit et mode de blocage pour Defender pour Office 365

Voulez-vous que votre expérience Defender pour Office 365 soit active ou passive ? Voici les deux modes que vous pouvez sélectionner :

- **Mode d’audit** : des *stratégies d’évaluation* spéciales sont créées pour l’anti-hameçonnage (qui inclut la protection de l’emprunt d’identité), les pièces jointes sécurisées et les liens fiables. Ces stratégies d’évaluation sont configurées pour *détecter les* menaces uniquement. Defender pour Office 365 détecte les messages dangereux à signaler, mais les messages ne sont pas traités (par exemple, les messages détectés ne sont pas mis en quarantaine). Les paramètres de ces stratégies d’évaluation sont décrits dans la section [Stratégies en mode audit](try-microsoft-defender-for-office-365.md#policies-in-audit-mode) plus loin dans cet article.

  Le mode Audit permet d’accéder aux rapports personnalisés pour les menaces détectées par Defender pour Office 365 sur la page **mode Évaluation** à l’adresse <https://security.microsoft.com/atpEvaluation>.

- **Mode de blocage** : le modèle Standard pour les [stratégies de sécurité prédéfinies](preset-security-policies.md) est activé et utilisé pour la version d’évaluation, et les utilisateurs que vous spécifiez inclure dans l’essai sont ajoutés à la stratégie de sécurité prédéfinies Standard. Defender pour Office 365 détecte et *prend des mesures sur* *les* messages dangereux (par exemple, les messages détectés sont mis en quarantaine).

  La sélection par défaut et recommandée consiste à étendre ces stratégies Defender pour Office 365 à tous les utilisateurs de l’organisation. Toutefois, pendant ou après la configuration de votre version d’évaluation, vous pouvez modifier l’attribution de stratégie à des utilisateurs, groupes ou domaines de messagerie spécifiques dans le portail Microsoft 365 Defender ou dans [les paramètres de stratégie associés à Defender pour Office 365 essais](try-microsoft-defender-for-office-365.md#policy-settings-associated-with-defender-for-office-365-trials)

  Le mode de blocage ne fournit pas de rapports personnalisés pour les menaces détectées par Defender pour Office 365. Au lieu de cela, les informations sont disponibles dans les rapports réguliers et les fonctionnalités d’enquête de Defender pour Office 365 Plan 2.

Un facteur clé en mode audit et en mode de blocage est la façon dont le courrier électronique est remis à votre organisation Microsoft 365 :

- Les messages provenant d’Internet circulent directement dans Microsoft 365, mais votre abonnement actuel n’a que [Exchange Online Protection (EOP)](exchange-online-protection-overview.md) ou [Defender pour Office 365 Plan 1](overview.md#microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

  ![Le courrier électronique transite à partir d’Internet vers Microsoft 365, avec protection contre EOP et/ou Defender pour Office 365 Plan 1.](../../media/mdo-trial-mail-flow.png)

  Dans ces environnements, vous pouvez sélectionner **le mode audit** ou **le mode de blocage**.

- Vous utilisez actuellement un service ou un appareil tiers pour la protection par e-mail de vos boîtes aux lettres Microsoft 365. Le courrier provenant d’Internet transite par le service de protection avant la remise dans votre organisation Microsoft 365. La protection Microsoft 365 est aussi faible que possible (elle n’est jamais complètement désactivée ; par exemple, la protection contre les programmes malveillants est toujours appliquée).

  ![Le courrier électronique circule à partir d’Internet via le service ou l’appareil de protection tiers avant la remise dans Microsoft 365.](../../media/mdo-migration-before.png)

  Dans ces environnements, vous pouvez sélectionner le **mode audit** uniquement. Vous n’avez pas besoin de modifier votre flux de messagerie (enregistrements MX).

Mettons-nous au travail.

## <a name="blocking-mode"></a>Mode blocage

### <a name="step-1-getting-started-in-blocking-mode"></a>Étape 1 : démarrer en mode blocage

#### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Démarrer votre version d’Office 365 Microsoft Defender

Une fois que vous avez lancé la version d’évaluation et terminé le [processus d’installation](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-or-trial-in-blocking-mode), l’application des modifications peut prendre jusqu’à 2 heures.

Nous avons configuré automatiquement des [Stratégies de sécurité prédéfinies](preset-security-policies.md) dans votre environnement. Ces stratégies représentent un profil de protection de référence adapté à la plupart des utilisateurs. La protection standard inclut :

- Liens fiables, pièces jointes fiables et stratégies anti-hameçonnage qui s’appliquent à l’ensemble du locataire ou au sous-ensemble d’utilisateurs que vous avez peut-être choisis pendant le processus de configuration de l’évaluation.
- Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.
- Protection des liens fiables pour les applications Office 365 prises en charge.

Regardez cette vidéo pour en savoir plus : Protégez-vous contre les liens malveillants avec Coffre liens dans [Microsoft Defender pour Office 365 - YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

#### <a name="enable-users-to-report-suspicious-content-in-blocking-mode"></a>Permettre aux utilisateurs de signaler du contenu suspect en mode blocage

Microsoft Defender pour Office 365 permet aux utilisateurs de signaler des messages à leurs équipes de sécurité et permet aux administrateurs de soumettre des messages à Microsoft Corporation pour analyse.

- Déployez [le macro complémentaire Message de rapport ou le module de signalement du hameçonnage.](enable-the-report-message-add-in.md)
- Établir un flux de travail pour [signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- Utilisez le [portail soumissions.](admin-submission.md)

Regardez cette vidéo pour en savoir plus : Découvrez comment utiliser le portail Soumissions pour soumettre des messages pour analyse [- YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-blocking-mode"></a>Examiner des rapports pour comprendre le paysage des menaces en mode blocage

Utilisez les fonctionnalités de rapport dans Defender pour Office 365 pour obtenir plus de détails sur votre environnement.

- Comprendre les menaces reçues dans les outils de collaboration et de messagerie à l’aide du rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)
- Découvrez où les menaces sont bloquées avec le [rapport d’état du flux de messagerie.](view-email-security-reports.md#mailflow-status-report)
- [Consultez les](view-reports-for-mdo.md#url-protection-report) liens qui ont été vus par les utilisateurs ou bloqués par le système.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="Rapports de messagerie et de collaboration dans le portail Microsoft 365 Defender" lightbox="../../media/mdo-trial-playbook-reporting.png":::

### <a name="step-2-intermediate-steps-in-blocking-mode"></a>Étape 2 : étapes intermédiaires en mode blocage

#### <a name="prioritize-focus-on-your-most-targeted-users"></a>Hiérarchiser le focus sur vos utilisateurs les plus ciblés

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

#### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Utiliser l’Explorateur de menaces pour examiner les e-mails malveillants

Defender for Office 365 enables you to investigate activities that put people in your organization at risk and to take action to protect your organization. You can do this using [Threat Explorer](threat-explorer.md).

- [Rechercher les messages suspects](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered)qui ont été remis : recherchez et supprimez des messages, identifiez l’adresse IP d’un expéditeur de courrier malveillant ou démarrez un incident pour un examen plus approfondie.
- [Vérifiez l’action de remise et l’emplacement](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): cette vérification vous permet de connaître l’emplacement des messages électroniques problématiques.
- [Afficher la chronologie de votre courrier électronique](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): recherchez simplement votre équipe des opérations de sécurité.

#### <a name="see-campaigns-targeting-your-organization"></a>Afficher les campagnes ciblant votre organisation

Affichez une image plus globale des affichages campagne dans Defender pour Office 365, ce qui vous donne une vue d’ensemble des campagnes d’attaque ciblant votre organisation et de l’impact qu’elles ont sur vos utilisateurs.

- [Identifiez les campagnes](campaigns.md#what-is-a-campaign) ciblant vos utilisateurs.
- [Visualisez l’étendue](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) de l’attaque.
- [Suivre l’interaction des](campaigns.md#campaign-details) utilisateurs avec ces messages

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="Détails de la campagne dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

Regardez cette vidéo pour en savoir plus : [Vues de campagne dans Microsoft Defender pour Office 365 - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

#### <a name="use-automation-to-remediate-risks"></a>Utiliser l’automatisation pour corriger les risques

Répondre efficacement à l’aide de l’examen et de la réponse automatisés (AIR) pour examiner, hiérarchiser et répondre aux menaces

- [En savoir plus](automated-investigation-response-office.md) sur les guides utilisateur d’investigation.
- [Afficher les détails et les résultats d’une](email-analysis-investigations.md) enquête
- Éliminer les menaces en [approuvant les actions de correction](air-remediation-actions.md)

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="Résultats de l’examen" lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

### <a name="step-3-advanced-content-in-blocking-mode"></a>Étape 3 : contenu avancé en mode blocage

#### <a name="dive-deep-into-data-with-query-based-hunting"></a>Entrer en profondeur dans les données avec le hunting basé sur une requête

Use Advanced hunting to write custom detection rules, proactively inspect events in your environment, and locate threat indicators. Explore raw data in your environment.

- [Créer des règles de détection personnalisées](../defender/custom-detections-overview.md)
- [Accéder aux requêtes partagées créées](../defender/advanced-hunting-shared-queries.md) par d’autres personnes

Regardez cette vidéo pour en savoir plus : [recherche de menaces avec Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

#### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Former les utilisateurs à repérer les menaces en simulant des attaques

Former vos utilisateurs avec les connaissances adéquates pour identifier les menaces et signaler les messages suspects avec une formation de simulation d’attaque dans Defender Office 365.

- [Simuler des menaces réalistes pour](attack-simulation-training.md) identifier les utilisateurs vulnérables
- [Affecter une formation aux](attack-simulation-training.md#assign-training) utilisateurs en fonction des résultats de simulation
- [Suivre l’avancement](attack-simulation-training-insights.md) de votre organisation dans les simulations et l’achèvement de la formation

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Les informations d’entraînement de simulation d’attaque dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="auditing-mode"></a>Mode audit

### <a name="step-1-get-started-in-auditing-mode"></a>Étape 1 : démarrer en mode audit

#### <a name="start-your-defender-for-office-365-evaluation"></a>Démarrez votre version d’évaluation Defender pour Office 365

Une fois le [processus d’installation](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-or-trial-in-audit-mode) terminé, l’application des modifications peut prendre jusqu’à 2 heures. Nous avons configuré automatiquement des stratégies d’évaluation prédéfinies dans votre environnement.

Les stratégies d’évaluation garantissent qu’aucune action n’est effectuée sur des courriers détectés par Defender pour Office 365.

#### <a name="enable-users-to-report-suspicious-content-in-auditing-mode"></a>Permettre aux utilisateurs de signaler du contenu suspect en mode audit

Microsoft Defender pour Office 365 permet aux utilisateurs de signaler des messages à leurs équipes de sécurité et permet aux administrateurs de soumettre des messages à Microsoft Corporation pour analyse.

- Déployez [le macro complémentaire Message de rapport ou le module de signalement du hameçonnage.](enable-the-report-message-add-in.md)
- Établir un flux de travail pour [signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- Utilisez le [portail soumissions.](admin-submission.md)

Regardez cette vidéo pour en savoir plus : Découvrez comment utiliser le portail Soumissions pour soumettre des messages pour analyse [- YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-auditing-mode"></a>Examiner des rapports pour comprendre le paysage des menaces en mode audit

Utilisez les fonctionnalités de rapport dans Defender pour Office 365 pour obtenir plus de détails sur votre environnement.

- Le [Tableau de bord d’évaluation](try-microsoft-defender-for-office-365.md#reports-for-audit-mode) fournit une vue facile des menaces détectées par Defender pour Office 365 lors de l’évaluation.
- Comprendre les menaces reçues dans les outils de collaboration et de messagerie à l’aide du rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)

### <a name="step-2-intermediate-steps-in-auditing-mode"></a>Étape 2 : étapes intermédiaires en mode audit

#### <a name="use-threat-explorer-to-investigate-malicious-email-in-auditing-mode"></a>Utiliser l’Explorateur de menaces pour examiner les e-mails malveillants en mode audit

Defender for Office 365 enables you to investigate activities that put people in your organization at risk and to take action to protect your organization. You can do this using [Threat Explorer](threat-explorer.md).

- [Rechercher les messages suspects](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered)qui ont été remis : recherchez et supprimez des messages, identifiez l’adresse IP d’un expéditeur de courrier malveillant ou démarrez un incident pour un examen plus approfondie.
- [Vérifiez l’action de remise et l’emplacement](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): cette vérification vous permet de connaître l’emplacement des messages électroniques problématiques.
- [Afficher la chronologie de votre courrier électronique](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): recherchez simplement votre équipe des opérations de sécurité.

#### <a name="convert-to-standard-protection-at-the-end-of-evaluation-period"></a>Convertir en protection standard à la fin de la période d’évaluation

Lorsque vous êtes prêt à activer des stratégies Defender pour Office 365 en production, vous pouvez utiliser « Convertir en protection standard » dans l’expérience de gestion des évaluations pour passer facilement à la protection Standard dans les [stratégies de sécurité prédéfinies](preset-security-policies.md).

1. Dans la page **Évaluation Microsoft Defender pour Office 365** sur <https://security.microsoft.com/atpEvaluation>, cliquez sur **Gérer**.

   :::image type="content" source="../../media/mdo-trial-playbook-mdo-evaluation-page.png" alt-text="Cliquez sur Gérer dans la page d’évaluation Defender pour Office 365 dans le Portail Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-mdo-evaluation-page.png":::

2. Dans le menu volant qui s’ouvre, cliquez sur **Convertir en protection standard**

   :::image type="content" source="../../media/mdo-trial-playbook-manage-flyout.png" alt-text="Cliquez sur Convertir en protection standard dans le menu volant Gérer de la page d’évaluation Defender pour Office 365." lightbox="../../media/mdo-trial-playbook-manage-flyout.png":::

3. Dans la boîte de dialogue **Convertir en protection standard** qui s’ouvre, cliquez sur **Continuer** pour lancer l’installation.

#### <a name="migrate-from-a-third-party-protection-service-or-device-to-defender-for-office-365"></a>Migrer d'un service ou d'un dispositif de protection tiers vers Defender for Office 365

Si vous disposez déjà d’un service ou d’un appareil de protection tiers existant devant Microsoft 365, vous pouvez migrer votre protection vers Microsoft Defender pour Office 365 afin de bénéficier des avantages d’une expérience de gestion consolidée, de coûts potentiellement réduits (à l’aide de produits que vous payez déjà) et d’un produit mature avec une protection de sécurité intégrée.

Pour en savoir plus, voir [Migrer d'un service ou d'un dispositif de protection tiers vers Defender for Office 365](migrate-to-defender-for-office-365.md).

### <a name="step-3-advanced-content-in-auditing-mode"></a>Étape 3 : contenu avancé en mode audit

#### <a name="train-users-to-spot-threats-by-simulating-attacks-in-auditing-mode"></a>Former les utilisateurs à repérer des menaces en simulant des attaques en mode audit

Former vos utilisateurs avec les connaissances adéquates pour identifier les menaces et signaler les messages suspects avec une formation de simulation d’attaque dans Defender Office 365.

- [Simuler des menaces réalistes pour](attack-simulation-training.md) identifier les utilisateurs vulnérables
- [Affecter une formation aux](attack-simulation-training.md#assign-training) utilisateurs en fonction des résultats de simulation
- [Suivre l’avancement](attack-simulation-training-insights.md) de votre organisation dans les simulations et l’achèvement de la formation

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Les informations d’entraînement de simulation d’attaque dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>Ressources supplémentaires

- **Guide interactif**: Vous ne connaissez pas Defender pour Office 365? Examinez [le guide interactif](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) pour comprendre comment commencer.
- **Guide de prise en main accéléré*** : [Microsoft Defender pour Office 365](https://go.microsoft.com/fwlink/p/?linkid=2197415)
- **Microsoft Defender pour Office 365 documentation** : obtenez des informations détaillées sur le fonctionnement de Defender pour Office 365 et sur la meilleure façon de l’implémenter pour votre organisation. Visitez la [documentation Microsoft Defender pour Office 365](defender-for-office-365.md).
- **Éléments inclus :** pour obtenir la liste complète des fonctionnalités de sécurité Office 365 courrier électronique répertoriées par niveau de produit, consultez la [matrice des fonctionnalités.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability)
- **Pourquoi Microsoft Defender pour Office 365**: The [Defender for Office 365 Datasheet](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) affiche les 10 principales raisons pour lesquelles les clients choisissent Microsoft Corporation.
