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
ms.custom: trial-playbook
ms.openlocfilehash: 6f19499a3c00fc1520d8bffb64336a789c017d28
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687743"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Livre d’essai : Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bienvenue dans le manuel de la version d’évaluation Microsoft Defender pour Office 365 ! Ce manuel vous aidera à mettre à jour votre version d’essai gratuite de 90 jours en vous enseignant à protéger votre organisation avec Defender pour Office 365.

Vous avez désormais la possibilité d’essayer Defender pour Office 365 des deux façons suivantes :

- **Mode blocage (recommandé)** : si votre enregistrement d’échangeur de messages (MX) pointe vers Microsoft 365, vous pouvez évaluer les fonctionnalités Defender pour Office 365 en mode blocage. Defender pour Office 365 applique automatiquement les paramètres standard de [stratégie de sécurité prédéfinie](preset-security-policies.md).

  Tout au long de la période d’évaluation, vous pouvez choisir à tout moment d’opter pour un modèle de protection plus élevé (nos paramètres de stratégie de sécurité prédéfinie stricts) ou de créer vos propres stratégies de protection individuelle pour répondre à vos besoins.

- **Mode audit** : si votre enregistrement MX pointe ailleurs que vers Microsoft 365 (par exemple, une passerelle de messagerie tierce), vous pouvez évaluer Defender pour Office 365 en mode audit. Defender pour Office 365 n’effectuera pas d’action de blocage sur les messages que nous jugeons dangereux.

  Ces menaces seront consignées et disponibles pour votre examen via le [Rapport d’état sur la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) qui vous fournit des informations détaillées sur les types de menaces détectées, les personnes ciblées par les menaces et bien plus encore. Ces autres « captures » indiquent les fonctionnalités de protection supplémentaires de Defender pour Office 365 par rapport aux fonctionnalités standard d’Exchange Online Protection (EOP) ou aux fonctionnalités d’autres passerelles de messagerie tierces. Une fois que vous êtes satisfait et prêt à utiliser Defender pour Office 365, vous pouvez [migrer vers Defender pour Office 365](migrate-to-defender-for-office-365.md).

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="Représentation graphique de tous les composants de Microsoft Defender pour Office 365." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

À l'aide des recommandations de ce guide, vous apprendrez comment Defender pour Office 365 peut vous aider à définir des politiques de protection, à analyser les menaces qui pèsent sur votre organisation et à répondre aux attaques.

Mettons-nous au travail.

## <a name="blocking-mode"></a>Mode blocage

### <a name="step-1-getting-started-in-blocking-mode"></a>Étape 1 : démarrer en mode blocage

#### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Démarrer votre version d’Office 365 Microsoft Defender

Une fois que vous avez lancé la version d’évaluation et terminé le [processus d’installation](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-in-blocking-mode), l’application des modifications peut prendre jusqu’à 2 heures.

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

Defender pour Office 365 vous permet d’examiner les activités qui exposent des personnes de votre organisation à des risques et de prendre des mesures pour protéger votre organisation. Pour ce faire, utilisez l’[Explorateur de menaces](threat-explorer.md).

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

- [En savoir plus](automated-investigation-response-office.md) sur les manuels d’investigation
- [Afficher les détails et les résultats d’une](email-analysis-investigations.md) enquête
- Éliminer les menaces en [approuvant les actions de correction](air-remediation-actions.md)

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="Résultats de l’examen" lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

### <a name="step-3-advanced-content-in-blocking-mode"></a>Étape 3 : contenu avancé en mode blocage

#### <a name="dive-deep-into-data-with-query-based-hunting"></a>Entrer en profondeur dans les données avec le hunting basé sur une requête

Utilisez la chasse avancée pour rédiger des règles de détection personnalisées, inspecter de manière proactive les événements dans votre environnement et localiser les indicateurs de menace. Explorez les données brutes de votre environnement.

- [Créer des règles de détection personnalisées](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting)
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

Une fois le [processus d’installation](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-in-audit-mode) terminé, l’application des modifications peut prendre jusqu’à 2 heures. Nous avons configuré automatiquement des stratégies d’évaluation prédéfinies dans votre environnement.

Les stratégies d’évaluation garantissent qu’aucune action n’est effectuée sur des courriers détectés par Defender pour Office 365.

#### <a name="enable-users-to-report-suspicious-content-in-auditing-mode"></a>Permettre aux utilisateurs de signaler du contenu suspect en mode audit

Microsoft Defender pour Office 365 permet aux utilisateurs de signaler des messages à leurs équipes de sécurité et permet aux administrateurs de soumettre des messages à Microsoft Corporation pour analyse.

- Déployez [le macro complémentaire Message de rapport ou le module de signalement du hameçonnage.](enable-the-report-message-add-in.md)
- Établir un flux de travail pour [signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
- Utilisez le [portail soumissions.](admin-submission.md)

Regardez cette vidéo pour en savoir plus : Découvrez comment utiliser le portail Soumissions pour soumettre des messages pour analyse [- YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-auditing-mode"></a>Examiner des rapports pour comprendre le paysage des menaces en mode audit

Utilisez les fonctionnalités de rapport dans Defender pour Office 365 pour obtenir plus de détails sur votre environnement.

- Le [Tableau de bord d’évaluation](try-microsoft-defender-for-office-365.md#reporting-in-audit-mode) fournit une vue facile des menaces détectées par Defender pour Office 365 lors de l’évaluation.
- Comprendre les menaces reçues dans les outils de collaboration et de messagerie à l’aide du rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)

### <a name="step-2-intermediate-steps-in-auditing-mode"></a>Étape 2 : étapes intermédiaires en mode audit

#### <a name="use-threat-explorer-to-investigate-malicious-email-in-auditing-mode"></a>Utiliser l’Explorateur de menaces pour examiner les e-mails malveillants en mode audit

Defender pour Office 365 vous permet d’examiner les activités qui exposent des personnes de votre organisation à des risques et de prendre des mesures pour protéger votre organisation. Pour ce faire, utilisez l’[Explorateur de menaces](threat-explorer.md).

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
- **Microsoft docs**: Obtenez des informations détaillées sur le fonctionnement de Defender pour Office 365 et sur la meilleure façon de le mettre en œuvre pour votre organisation. Visitez [Docs](overview.md).
- **Éléments inclus :** pour obtenir la liste complète des fonctionnalités de sécurité Office 365 courrier électronique répertoriées par niveau de produit, consultez la [matrice des fonctionnalités.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability)
- **Pourquoi Microsoft Defender pour Office 365**: The [Defender for Office 365 Datasheet](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) affiche les 10 principales raisons pour lesquelles les clients choisissent Microsoft Corporation.
