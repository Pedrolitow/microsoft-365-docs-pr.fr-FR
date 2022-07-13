---
title: Pilotez Microsoft Defender pour Office 365, utilisez l’évaluation dans votre environnement de production
description: Étapes de pilote de votre évaluation avec des groupes d’utilisateurs actifs et existants afin de tester correctement les fonctionnalités de Microsoft Defender pour Office 365.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.custom: admindeeplinkEXCHANGE
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: fb246805ebf38cddfda6fe308d19e1dd1419531b
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748800"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365 pilote

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 3 sur 3](eval-defender-office-365-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Utilisez les étapes suivantes pour configurer et configurer le pilote pour Microsoft Defender pour Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="Étapes de création du pilote dans le portail Microsoft Defender pour Office 365" lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [Étape 1 : Créer des groupes pilotes](#step-1-create-pilot-groups)
- [Étape 2 : Configurer la protection](#step-2-configure-protection)
- [Étape 3 : Tester les fonctionnalités : familiarisez-vous avec la simulation, la surveillance et les métriques](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

Lorsque vous évaluez Microsoft Defender pour Office 365, vous pouvez choisir de piloter des utilisateurs spécifiques avant d’activer et d’appliquer des stratégies pour l’ensemble de votre organisation. La création de groupes de distribution peut aider à gérer les processus de déploiement. Par exemple, créez des groupes tels que *Defender pour Office 365 Utilisateurs - Protection standard*, *Defender pour Office 365 Utilisateurs - Protection stricte*, *utilisateurs Defender pour Office 365 - Protection personnalisée* ou *Defender pour Office 365 utilisateurs - Exceptions*.

Il n’est peut-être pas évident pourquoi « Standard » et « Strict » sont les termes utilisés pour ces groupes, mais cela deviendra clair lorsque vous explorerez plus en détail Defender pour Office 365 préréglages de sécurité. Les groupes d’affectation de noms « personnalisés » et « exceptions » parlent d’eux-mêmes, et même si la plupart de vos utilisateurs doivent être soumis à des groupes *standard* et *stricts*, personnalisés et d’exceptions collecteront des données précieuses pour vous concernant la gestion des risques.

## <a name="step-1-create-pilot-groups"></a>Étape 1 : Créer des groupes pilotes

Les groupes de distribution peuvent être créés et définis directement dans Exchange Online ou synchronisés à partir de Active Directory local.

1. Connectez-vous au Centre de Administration Exchange (EAC) à l’aide d’un compte qui a reçu le rôle Administrateur de destinataires ou qui a reçu des autorisations de gestion de groupe déléguées.
2. Dans le menu de navigation, développez *Destinataires* et sélectionnez *Groupes*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" Élément de menu Groupes à cliquer" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. Dans le tableau de bord Groupes, sélectionnez « Ajouter un groupe ».

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Option Ajouter un groupe à cliquer" lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. Pour le type de groupe, sélectionnez *Distribution* , puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" Section Choisir un type de groupe" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. Donnez un nom et une description au groupe, puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Section Configurer les notions de base" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>Étape 2 : Configurer la protection

Certaines fonctionnalités de Defender pour Office 365 sont configurées et activées par défaut, mais les opérations de sécurité peuvent vouloir augmenter le niveau de protection par rapport à la valeur par défaut.

Certaines fonctionnalités *ne sont pas encore* configurées. Vous disposez de trois options pour configurer la protection :

- **Attribuer automatiquement des stratégies de sécurité prédéfinies** : les [stratégies de sécurité prédéfinies sont fournies](../office-365-security/preset-security-policies.md) comme méthode pour affecter rapidement un niveau de protection uniforme à toutes les fonctionnalités. Vous pouvez choisir **_parmi standard_*_ ou _*_strict_**. Une bonne approche consiste à commencer par des stratégies de sécurité prédéfinies, puis à affiner les stratégies à mesure que vous en apprendrez davantage sur les fonctionnalités et votre propre environnement de menace unique. L’avantage ici est que vous protégez des groupes d’utilisateurs le plus rapidement possible, avec la possibilité d’ajuster la protection par la suite. (Cette méthode est recommandée.)
- **Configurer manuellement la protection de base** de référence : si vous préférez configurer l’environnement vous-même, vous pouvez rapidement obtenir une *base de référence* de protection en suivant les instructions de [Protection contre les menaces](../office-365-security/protect-against-threats.md). Cette approche vous permet d’en savoir plus sur les paramètres configurables. Et vous pourrez affiner les stratégies ultérieurement.
- **Configurer des stratégies de protection *personnalisées*** : vous pouvez également générer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation. Avant de commencer à personnaliser les stratégies, il est important de comprendre la priorité dans laquelle ces stratégies de protection sont appliquées et appliquées. Les opérations de sécurité doivent créer des stratégies même si la présélection est appliquée, en particulier pour définir des stratégies de sécurité pour les liens sécurisés et les pièces jointes sécurisées.
> [!IMPORTANT]
> **Si vous devez configurer des stratégies de protection personnalisées**, vous devez examiner les valeurs qui composent les définitions de sécurité **Standard** et **Strict** ici : *[Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](../office-365-security/recommended-settings-for-eop-and-office365.md)*. Les valeurs par défaut, comme indiqué avant toute configuration, sont également répertoriées. Conservez une feuille de calcul de l’endroit où votre build personnalisée dévie.

### <a name="assign-preset-security-policies"></a>Affecter des stratégies de sécurité prédéfinies

Il est recommandé de commencer par les stratégies de *base recommandées* lors de l’évaluation de MDO, puis de les affiner en fonction des besoins au cours de votre période d’évaluation.

Vous pouvez activer rapidement les stratégies de protection EOP et Defender pour Office 365 recommandées, et les affecter à des utilisateurs pilotes spécifiques ou à des groupes définis dans le cadre de votre évaluation. Les stratégies prédéfinies offrent un modèle de protection **Standard** de base ou un modèle de protection **strict** plus agressif, qui peut être attribué indépendamment ou combiné.

Voici les [stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](../office-365-security/preset-security-policies.md) article décrivant les étapes.

1. Connectez-vous à votre locataire Microsoft 365. Utilisez un compte avec accès au portail Microsoft 365 Defender, ajouté au rôle Gestion de l’organisation dans Office 365 ou rôle Administrateur de la sécurité dans Microsoft 365.
2. Dans le menu de navigation, sélectionnez *Polices & Rules* sous Email & Collaboration.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text=" Élément de menu Stratégies & règles à cliquer" lightbox="../../media/mdo-eval/5_mdo-eval-pilot-policies.png":::

3. Dans le tableau de bord Stratégie & règles, cliquez sur *Stratégies de menaces*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text=" Élément de menu Stratégies de menace à cliquer" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. Dans le portail Microsoft 365 Defender, développez Gestion des menaces dans le menu de navigation, puis sélectionnez Stratégie dans le sous-menu.
5. Dans le tableau de bord Stratégie, cliquez sur *Stratégies de sécurité prédéfinies*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Types de stratégies de menace" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. Cliquez sur *Modifier* pour configurer et affecter la stratégie Standard et/ou la stratégie stricte.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="Les différents paramètres appliqués aux différentes stratégies dans la page Stratégies de sécurité prédéfinies" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. Ajoutez des conditions pour appliquer des protections de base ***EOP** _ à des utilisateurs pilotes spécifiques ou à des groupes d’utilisateurs, si nécessaire, et sélectionnez _Next* pour continuer.

   Par exemple, une condition de Defender pour Office 365 pour les évaluations pilotes peut être appliquée si les destinataires sont *membres* d’un *groupe de protection standard Defender pour Office 365* défini, puis gérés en ajoutant des comptes au groupe ou en supprimant un compte.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="Stratégies considérées comme des protections EOP" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. Ajoutez des conditions pour appliquer des protections de base ***MDO** _ à des utilisateurs pilotes spécifiques ou à des groupes d’utilisateurs, selon les besoins. Cliquez sur _Next* pour continuer.

   Par exemple, une condition de Defender pour Office 365 pour les évaluations pilotes peut être appliquée si les destinataires sont *membres* d’un *groupe de protection standard Defender pour Office 365* défini, puis gérés en ajoutant/supprimant des comptes via le groupe.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="Les politiques considérées comme défensives de la protection Office 365" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. Passez en revue et confirmez vos modifications pour l’affectation de stratégies de sécurité prédéfinies.
10. Les stratégies de protection prédéfinies peuvent être gérées (reconfigurées, réappliées, désactivées, etc.) en retournant au portail Microsoft 365 Defender > des règles & des règles > les stratégies de menace > et en cliquant sur la vignette *Stratégies de sécurité prédéfinies*.

### <a name="configure-custom-protection-policies"></a>Configurer des stratégies de protection personnalisées

Les modèles de stratégie *Standard* ou *Strict* Defender pour Office 365 prédéfinis offrent à vos utilisateurs pilotes la protection de référence recommandée. Toutefois, vous pouvez également générer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation.

Il est *important* de connaître la priorité que ces stratégies de protection prennent lorsqu’elles sont appliquées et appliquées, comme [l’explique l’ordre et la priorité de la protection par e-mail - Office 365](../office-365-security/how-policies-and-protections-are-combined.md).

Le tableau ci-dessous fournit des références et des conseils supplémentaires pour configurer et affecter des stratégies de protection personnalisées :

<br>

****

|Stratégie|Description|Référence|
|:---:|---|---|
|Filtrage des connexions|Identifiez les serveurs de courrier source corrects ou incorrects par leurs adresses IP.|[Configurer la stratégie de filtre de connexion par défaut dans EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|Logiciel anti-programme malveillant|Protégez les utilisateurs contre les programmes malveillants par e-mail, notamment les actions à entreprendre et les personnes à notifier si des programmes malveillants sont détectés.|[Configurer des stratégies anti-programme malveillant dans EOP](../office-365-security/configure-anti-malware-policies.md)|
|Anti-usurpation d’identité|Protégez les utilisateurs contre les tentatives d’usurpation d’identité à l’aide d’informations d’usurpation d’identité et d’usurpation d’identité.|[Configurer l’intelligence par usurpation d’identité dans Defender pour Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|Anti-spam|Protégez les utilisateurs contre le courrier indésirable, y compris les actions à prendre si le courrier indésirable est détecté.|[Configurer des stratégies anti-courrier indésirable dans Defender pour Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Anti-hameçonnage|Protéger les utilisateurs contre les attaques par hameçonnage et configurer des conseils de sécurité sur les messages suspects|[Pour plus d’informations, voir Configurer les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Pièces jointes fiables|Protégez les utilisateurs contre les contenus malveillants dans les pièces jointes et les fichiers de messagerie dans SharePoint, OneDrive et Teams.|[Configurer des stratégies de pièces jointes sécurisées dans Defender pour Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Liens sûrs|Protégez les utilisateurs de l’ouverture et du partage de liens malveillants dans les messages électroniques ou les applications de bureau Office.|[Configurer des stratégies de liens sécurisés dans Defender pour Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>Étape 3 : Tester les fonctionnalités et se familiariser avec la simulation, la supervision et les métriques

Maintenant que votre pilote est configuré et configuré, il est utile de se familiariser avec les outils de création de rapports, de surveillance et de simulation d’attaques propres à Microsoft Defender pour Microsoft 365.

<br>

****

|Fonctionnalité|Description|Plus d’informations|
|---|---|---|
|Threat Explorer|L’Explorateur des menaces est un outil puissant en quasi-temps réel qui permet aux équipes des opérations de sécurité d’examiner et de répondre aux menaces et d’afficher des informations sur les programmes malveillants suspects et les hameçonnages dans les e-mails et les fichiers dans Office 365, ainsi que d’autres menaces et risques de sécurité pour votre organisation.|[Affichages dans l’Explorateur de menaces et détections en temps réel](../office-365-security/threat-explorer-views.md)|
|Simulateur d’attaques|Vous pouvez utiliser l’apprentissage de simulation d’attaque dans le portail Microsoft 365 Defender pour exécuter des scénarios d’attaque réalistes dans votre organisation, qui vous aident à identifier et à trouver des utilisateurs vulnérables avant qu’une attaque réelle n’affecte votre environnement.|[Commencer à utiliser la formation à la simulation d’attaque](../office-365-security/attack-simulation-training-get-started.md)|
|Tableau de bord rapports|Dans le menu de navigation de gauche, cliquez sur Rapports et développez l’en-tête e-mail & collaboration. Les rapports e-mail & collaboration traitent de la détection des tendances de sécurité dont certaines vous permettront d’agir (par le biais de boutons tels que « Accéder aux soumissions ») et d’autres qui afficheront des tendances, telles que le résumé de l’état du flux de courrier, les principaux programmes malveillants, les détections d’usurpation d’identité, les utilisateurs compromis, la latence du courrier, les liens sécurisés et les rapports de pièces jointes sécurisées. Ces métriques sont générées automatiquement.|[Afficher les rapports](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Prochaines étapes

[Évaluer Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
