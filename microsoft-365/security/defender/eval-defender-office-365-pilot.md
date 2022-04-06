---
title: Pilotez Microsoft Defender pour Office 365, utilisez l’évaluation dans votre environnement de production
description: Étapes à suivre pour piloter votre évaluation avec des groupes d’utilisateurs actifs et existants afin de tester correctement les fonctionnalités de Microsoft Defender pour Office 365.
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
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: d8cd0132c8b02ae29cf49c9a700a868fa3a93554
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501352"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Piloter Microsoft Defender pour Office 365

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 3 sur 3](eval-defender-office-365-overview.md) dans le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Utilisez les étapes suivantes pour configurer et configurer le pilote de Microsoft Defender pour Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="Étapes de création du projet pilote dans le portail Microsoft Defender Office 365 web" lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [Étape 1 : Créer des groupes pilotes](#step-1-create-pilot-groups)
- [Étape 2 : Configurer la protection](#step-2-configure-protection)
- [Étape 3 : Tester les fonctionnalités : familiarisez-vous avec la simulation, la surveillance et les mesures](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

Lorsque vous évaluez Microsoft Defender pour Office 365, vous pouvez choisir de piloter des utilisateurs spécifiques avant d’activer et d’appliquer des stratégies pour l’ensemble de votre organisation. La création de groupes de distribution peut aider à gérer les processus de déploiement. Par exemple, créez des groupes tels que Defender pour les utilisateurs *Office 365 - Protection standard*, Defender pour les utilisateurs de *Office 365 - Protection stricte*, Defender pour les utilisateurs *Office 365 - Protection* personnalisée ou Defender pour les *utilisateurs Office 365 - Exceptions*.

Il n’est peut-être pas évident de comprendre pourquoi « Standard » et « Strict » sont les termes utilisés pour ces groupes, mais cela sera évident lorsque vous explorerez plus en détail les présets de sécurité de Defender for Office 365. Les groupes d’attribution de noms « personnalisé » et « exceptions » parlent d’eux-mêmes, et bien que la plupart de vos utilisateurs doivent être sous *standard* et *strict*, les groupes personnalisés et d’exceptions collecteront des données précieuses pour vous concernant la gestion des risques.

## <a name="step-1-create-pilot-groups"></a>Étape 1 : Créer des groupes pilotes

Les groupes de distribution peuvent être créés et définis directement Exchange Online ou synchronisés à partir d’Active Directory local.

1. Connectez-vous au Centre d’administration Exchange (EAC) à l’aide d’un compte qui a reçu le rôle d’administrateur des destinataires ou qui a reçu des autorisations de gestion de groupe déléguées.
2. Dans le menu de navigation, développez *Destinataires* et sélectionnez *Groupes*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" Élément de menu Groupes à cliquer" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. Dans le tableau de bord Groupes, sélectionnez « Ajouter un groupe ».

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Option Ajouter un groupe à cliquer" lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. Pour le type de groupe, *sélectionnez Distribution* , puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" Section Choisir un type de groupe" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. Donnez un nom et une description au groupe, puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Section Configurer les informations de base" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>Étape 2 : Configurer la protection

Certaines fonctionnalités de Defender pour Office 365 sont configurées et sont désactivées par défaut, mais les opérations de sécurité peuvent vouloir augmenter le niveau de protection par défaut.

Certaines fonctionnalités ne *sont pas encore* configurées. Vous avez trois options pour configurer la protection :

- **Attribuer automatiquement des stratégies** de sécurité prédéfinies : les stratégies de sécurité prédéfinies sont fournies en tant que méthode pour affecter rapidement un niveau uniforme de protection à toutes les fonctionnalités.[](../office-365-security/preset-security-policies.md) Vous pouvez choisir entre **_standard_*_ ou _*_strict_**. Une bonne approche consiste à commencer par des stratégies de sécurité prédéfinies, puis à affiner les stratégies à mesure que vous en apprendrez plus sur les fonctionnalités et votre propre environnement de menaces unique. L’avantage ici est que vous protégez les groupes d’utilisateurs aussi rapidement que possible, avec la possibilité d’ajuster la protection par la suite. (Cette méthode est recommandée.)
- **Configurez manuellement la protection** de référence : si vous préférez configurer l’environnement vous-même, vous  pouvez rapidement obtenir une ligne de base de protection en suivant les instructions de la norme [Protect against threats](../office-365-security/protect-against-threats.md). Cette approche vous permet d’en savoir plus sur les paramètres configurables. Vous pourrez également affiner les stratégies ultérieurement.
- **Configurer des *stratégies de* protection personnalisées** : vous pouvez également créer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation. Avant de commencer à personnaliser des stratégies, il est important de comprendre la priorité dans laquelle ces stratégies de protection sont appliquées et appliquées. Les opérations de sécurité doivent créer certaines stratégies même si le prédéfiny est appliqué, afin de définir des stratégies de sécurité spécifiques pour les liens Coffre et les pièces jointes Coffre données.
> [!IMPORTANT]
> Si vous devez configurer des stratégies de **protection** personnalisées, vous devez examiner les valeurs qui sont les définitions de sécurité **standard** et **stricte** ici : *[Paramètres recommandés pour EOP et Microsoft Defender](../office-365-security/recommended-settings-for-eop-and-office365.md)* pour la sécurité Office 365. Les valeurs par défaut, telles qu’elles sont visibles avant toute configuration, sont également répertoriées. Conservez une feuille de calcul de l’endroit où votre build personnalisé s’écarte.

### <a name="assign-preset-security-policies"></a>Attribuer des stratégies de sécurité prédéfines

Il est recommandé de commencer par les stratégies  de référence recommandées lors de l’évaluation de MDO, puis de les affiner selon vos besoins au cours de votre période d’évaluation.

Vous pouvez activer rapidement les stratégies de protection EOP et Defender recommandées pour Office 365 et les affecter à des utilisateurs pilotes spécifiques ou à des groupes définis dans le cadre de votre évaluation. Les stratégies prédéfines offrent un modèle de protection **standard** de référence ou un modèle de protection **strict** plus agressif, qui peut être attribué indépendamment ou combiné.

Voici les stratégies [de sécurité prédéfini dans EOP et Microsoft Defender pour](../office-365-security/preset-security-policies.md) Office 365 décrivant les étapes.

1. Connectez-vous à votre Microsoft 365 client. Utilisez un compte ayant accès au portail Microsoft 365 Defender, ajouté au rôle Gestion de l’organisation dans Office 365 ou Administrateur de la sécurité dans Microsoft 365.
2. Dans le menu de navigation, sélectionnez *Polices & sous* Email & Collaboration.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text=" L’élément de menu & stratégies à cliquer" lightbox="../../media/mdo-eval/5_mdo-eval-pilot-policies.png":::

3. Dans le tableau de bord Règles & stratégie, cliquez sur *Stratégies de menace*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text=" L’élément de menu stratégies de menace à cliquer" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. À partir du Microsoft 365 Defender, développez Gestion des menaces à partir du menu de navigation, puis sélectionnez Stratégie dans le sous-menu.
5. Dans le tableau de bord de stratégie, cliquez *sur Stratégies de sécurité prédéfines*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Types de stratégies de menace" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. Cliquez *sur Modifier* pour configurer et affecter la stratégie Standard et/ou strict.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="Les différents paramètres appliqués à différentes stratégies sur la page Stratégies de sécurité prédéfines" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. Ajoutez des conditions pour appliquer les protections ***EOP** _ de référence à des utilisateurs pilotes spécifiques ou à des groupes d’utilisateurs, si nécessaire, et sélectionnez _Next* pour continuer.

   Par exemple, une condition Defender pour Office 365 pour les évaluations pilotes peut être appliquée si les destinataires sont membres d’un groupe *Defender pour Office 365 Standard Protection* défini, puis gérés en ajoutant des comptes au groupe ou en en supprimant un compte.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="Stratégies considérées comme des protections EOP" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. Ajoutez des conditions pour appliquer des protections ***MDO** _ de référence à des utilisateurs pilotes spécifiques ou à des groupes d’utilisateurs, selon vos besoins. Cliquez sur _Next* pour continuer.

   Par exemple, une condition Defender pour Office 365 pour les évaluations pilotes peut être appliquée si les destinataires sont membres d’un groupe *Defender pour Office 365 Standard Protection* défini, puis géré en ajoutant/supprimant des comptes via le groupe.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="Les stratégies considérées comme protégées par Office 365 protection" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. Examinez et confirmez vos modifications pour attribuer des stratégies de sécurité prédéfines.
10. Les stratégies de protection prédéfinie peuvent être gérées (reconfigurées, ré-appliquées, désactivées, etc.) en revenant au portail Microsoft 365 Defender > Stratégies & règles > Stratégies contre les menaces > et en cliquant sur la vignette stratégies de sécurité prédéfinie.

### <a name="configure-custom-protection-policies"></a>Configurer des stratégies de protection personnalisées

Les modèles de stratégie *Standard* ou *Strict* Defender prédéfin Office 365 offrent à vos utilisateurs pilotes la protection de référence recommandée. Toutefois, vous pouvez également créer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation.

Il est *important de* prendre en compte la priorité que prennent ces stratégies de protection lorsqu’elles sont appliquées et appliquées, comme l’explique l’ordre et la priorité de [la protection de la messagerie Office 365](../office-365-security/how-policies-and-protections-are-combined.md).

Le tableau ci-dessous fournit des références et des instructions pour la configuration et l’affectation de stratégies de protection personnalisées :

<br>

****

|Stratégie|Description|Référence|
|:---:|---|---|
|Filtrage des connexions|Identifiez les serveurs de messagerie source bons ou mauvais par leurs adresses IP.|[Configurer la stratégie de filtrage des connexions par défaut dans EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|Logiciel anti-programme malveillant|Protéger les utilisateurs contre les programmes malveillants de messagerie, y compris les actions à prendre et les personnes à avertir si des programmes malveillants sont détectés.|[Configurer des stratégies anti-programme malveillant dans EOP](../office-365-security/configure-anti-malware-policies.md)|
|Anti-usurpation|Protéger les utilisateurs contre les tentatives d’usurpation d’informations à l’aide de la veille contre l’usurpation d’informations et de l’usurpation d’informations.|[Configurer la veille contre l’usurpation d’Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|Anti-courrier indésirable|Protéger les utilisateurs contre le courrier indésirable, y compris les actions à prendre si du courrier indésirable est détecté.|[Configurer des stratégies anti-courrier indésirable dans Defender pour Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Anti-hameçonnage|Protéger les utilisateurs contre les attaques par hameçonnage et configurer des conseils de sécurité sur les messages suspects|[Pour plus d’informations, voir Configurer les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Pièces jointes fiables|Protéger les utilisateurs contre le contenu malveillant dans les pièces jointes et les fichiers de courrier électronique SharePoint, OneDrive et Teams.|[Configurer des stratégies de pièces jointes sécurisées dans Defender pour Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Liens sûrs|Protégez les utilisateurs contre l’ouverture et le partage de liens malveillants dans des messages électroniques ou Office applications de bureau.|[Configurer des stratégies de liens sécurisés dans Defender pour Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>Étape 3 : Testez les fonctionnalités et familiarisez-vous avec la simulation, la surveillance et les mesures

Maintenant que votre pilote est configuré et configuré, il est utile de se familiariser avec les outils de rapports, de surveillance et de simulation d’attaques propres à Microsoft Defender pour Microsoft 365.

<br>

****

|Fonctionnalité|Description|Plus d’informations|
|---|---|---|
|Threat Explorer|L’Explorateur de menaces est un outil puissant en temps quasi réel qui permet aux équipes des opérations de sécurité d’examiner les menaces et de répondre aux menaces et d’afficher des informations sur les programmes malveillants et le hameçonnage suspectés dans le courrier électronique et les fichiers dans Office 365, ainsi que d’autres menaces et risques de sécurité pour votre organisation.|[Affichages dans l’Explorateur de menaces et détections en temps réel](../office-365-security/threat-explorer-views.md)|
|Simulateur d’attaques|Vous pouvez utiliser la formation sur la simulation d’attaques dans le portail Microsoft 365 Defender pour exécuter des scénarios d’attaque réalistes dans votre organisation, ce qui vous permet d’identifier et de trouver des utilisateurs vulnérables avant qu’une attaque réelle n’impacte votre environnement.|[Commencer à utiliser la formation à la simulation d’attaque](../office-365-security/attack-simulation-training-get-started.md)|
|Tableau de bord rapports|Dans le menu de navigation de gauche, cliquez sur Rapports et développez l’en-tête & collaboration. Les rapports de collaboration de l'& de messagerie permettent de détecter les tendances de sécurité. Certains d’entre eux vous permettront d’agir (via des boutons tels que « Go to submissions », et d’autres qui afficheront des tendances, comme le résumé de l’état du flux de messagerie, les principaux programmes malveillants, les détections d’usurpation d’adresse, les utilisateurs compromis, la latence de messagerie, les liens Coffre et les rapports de pièces jointes Coffre. Ces mesures sont générées automatiquement.|[Afficher les rapports](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Prochaines étapes

[Évaluer Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)
