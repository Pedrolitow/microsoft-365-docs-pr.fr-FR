---
title: Étape 5. Développer et tester des cas d’utilisation
description: Principes de base du développement et du test des cas d’usage lors de l’intégration de Microsoft 365 Defender dans vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque, étendues, opérations de sécurité, soc
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
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: c4caee1bd0904cecd941789e891b93a378080eed
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483297"
---
# <a name="step-5-develop-and-test-use-cases"></a>Étape 5. Développer et tester des cas d’utilisation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les méthodes recommandées pour déployer Microsoft 365 Defender dans votre Centre des opérations de sécurité (SOC) dépendent de l’ensemble actuel d’outils, de processus et d’ensembles de compétences de l’équipe SOC. Le maintien de la cyber-hygiène entre les plateformes peut être difficile en raison de la grande quantité de données provenant de dizaines, voire de centaines de sources de sécurité.

Les outils de sécurité sont interdépendants. L’activation d’une fonctionnalité dans une technologie de sécurité ou la modification d’un processus peut à son tour en interrompre une autre. Pour cette raison, Microsoft recommande à votre équipe SOC de formaliser une méthode pour définir et hiérarchiser les cas d’usage. Les cas d’utilisation permettent de définir les exigences et les processus de test pour les opérations SOC au sein de différentes équipes. Il crée une méthodologie de capture des métriques pour déterminer si les rôles appropriés et la combinaison de tâches sont alignés sur l’équipe appropriée avec les bons ensembles de compétences.

## <a name="develop-and-formalize-use-case-process"></a>Développer et formaliser le processus de cas d’usage

La SOC devrait définir une norme et un processus de haut niveau pour l’élaboration des cas d’usage, qui seraient réglementés par l’équipe de supervision de la SOC. L’équipe de supervision SOC doit travailler avec votre entreprise, l’informatique, les services juridiques, les rh et d’autres groupes pour hiérarchiser les cas d’utilisation pour le SOC qui finiront par faire leur chemin dans les runbooks et les playbooks de l’équipe SOC. La priorité des cas d’usage est basée sur des objectifs tels que la conformité ou la confidentialité.

Les activités de supervision SOC liées au développement de cas d’usage sont les suivantes :

- Conditions requises
- Besoins en personnel ou en formation
- Licences logicielles
- Sous-traitance du fournisseur
- Gestion du plan
- Gestion du registre des cas d’usage
- Maintenance/mise à jour des modèles

Pour faciliter les processus de création de runbook et de playbook, créez un arbre de décision de cas d’usage. Cette figure montre un exemple.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Processus de décision de cas d’usage" lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Une fois qu’une norme de cas d’usage de haut niveau a été définie et approuvée, l’étape suivante consiste à créer et tester un cas d’usage réel. Les sections suivantes utilisent des scénarios d’analyse des menaces et des vulnérabilités et anti-hameçonnage comme exemples.

## <a name="use-case-example-1-new-phishing-variant"></a>Exemple de cas d’usage 1 : Nouvelle variante d’hameçonnage

La première étape de la création d’un cas d’usage consiste à décrire le flux de travail à l’aide d’un story board. Voici un exemple de story board de haut niveau pour une nouvelle notification d’attaque par hameçonnage à une équipe Threat Intelligence.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Flux de travail d’un cas d’usage pour une campagne anti-hameçonnage" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Appeler le workflow de cas d’usage par exemple 1

Une fois que le story board a été approuvé, l’étape suivante consiste à appeler le workflow de cas d’usage. Voici un exemple de processus pour une campagne anti-hameçonnage.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="Flux de travail de cas d’usage détaillé pour une campagne anti-hameçonnage" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Exemple de cas d’usage 2 : Analyse des menaces et des vulnérabilités

Un autre scénario dans lequel un cas d’usage peut être utilisé est l’analyse des menaces et des vulnérabilités. Dans cet exemple, le SOC exige que les menaces et les vulnérabilités soient corrigées contre les ressources par le biais de processus approuvés qui incluent l’analyse des ressources.

Voici un exemple de storyboard de haut niveau pour la Gestion des vulnérabilités Microsoft Defender des ressources.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="Flux de travail de cas d’usage pour Gestion des menaces et des vulnérabilités" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Appeler le workflow de cas d’usage par exemple 2

Voici un exemple de processus pour l’analyse des menaces et des vulnérabilités.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="Workflow de cas d’usage détaillé pour Gestion des menaces et des vulnérabilités" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::

### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Analyser la sortie du cas d’usage et les leçons apprises

Une fois qu’un cas d’usage a été approuvé et testé, les lacunes entre vos équipes de sécurité doivent être identifiées, ainsi que les personnes, les processus et les technologies Microsoft 365 Defender impliquées. Microsoft 365 Defender technologies doivent être analysées pour déterminer si elles sont capables d’atteindre les résultats souhaités. Ceux-ci peuvent être suivis par le biais d’une liste de vérification ou d’une matrice.

Par exemple, dans l’exemple de scénario anti-hameçonnage, les équipes SOC auraient pu effectuer les découvertes dans ce tableau.

|Équipe SOC|Conditions requises|Personnes pour répondre aux exigences|Processus pour répondre aux exigences|Technologie pertinente|Écart identifié|Journal des modifications de cas d’usage|Exempt (Y/N)|
|---|---|---|---|---|---|---|---|
|Équipe Threat Intelligence and Analytics|Les sources de données alimentent correctement les moteurs de renseignement sur les menaces.|Analyste/ingénieur Threat Intelligence|Exigences de flux de données établies, déclencheurs de renseignement sur les menaces provenant de sources approuvées|Microsoft Defender pour Identity, Microsoft Defender pour point de terminaison|L’équipe Threat Intelligence n’a pas utilisé de script Automation pour lier Microsoft 365 Defender API à des moteurs Intel de menaces|Ajouter Microsoft 365 Defender en tant que sources de données aux moteurs de menaces <p> Mettre à jour le run book de cas d’usage|N|
|Équipe de supervision|Les sources de données alimentent correctement les tableaux de bord de surveillance|Analyste SOC de niveau 1,2 – Surveillance des alertes &|Flux de travail pour la création de rapports sur le degré de sécurité & le degré de sécurisation du Centre de conformité|[Alertes dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/alerts) <p> Surveillance du degré de sécurisation|Aucun mécanisme permettant aux analystes SOC de signaler la réussite d’une nouvelle détection de variante d’hameçonnage pour améliorer le degré de sécurisation <p> [Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender](/microsoft-365/security/office-365-security/view-email-security-reports)|Ajouter un processus de suivi de l’amélioration du degré de sécurisation aux workflows de création de rapports|N|
|Ingénierie et SecOps Team|Les mises à jour du contrôle de modification sont effectuées dans les runbooks d’équipe SOC|Ingénieur SOC de niveau 2|Procédure de notification change control pour les runbooks d’équipe SOC|Modifications approuvées des appareils de sécurité|Les modifications apportées à Microsoft 365 Defender connectivité à la technologie de sécurité SOC nécessitent une approbation|Ajouter Microsoft Defender for Cloud Apps, Defender pour Identity, Defender pour point de terminaison, Security & Compliance Center aux runbooks SOC|v|

En outre, les équipes SOC auraient pu effectuer les découvertes décrites dans le tableau ci-dessous en ce qui concerne le scénario de gestion des vulnérabilités Defender décrit ci-dessus :

|Équipe SOC|Conditions requises|Personnes pour répondre aux exigences|Processus pour répondre aux exigences|Technologie pertinente|Écart identifié|Journal des modifications de cas d’usage|Exempt (Y/N)|
|---|---|---|---|---|---|---|---|
|Surveillance SOC|Toutes les ressources connectées à des réseaux approuvés sont identifiées et classées|Surveillance SOC, propriétaires de bu, propriétaires d’applications, propriétaires d’actifs informatiques, etc.|Système centralisé de gestion des actifs pour découvrir et répertorier les catégories et attributs d’actifs en fonction des risques.|ServiceNow ou d’autres ressources. <br><br>[Inventaire des appareils Microsoft 365](/microsoft-365/security/defender-endpoint/device-discovery)|Seuls 70 % des actifs ont été découverts. Microsoft 365 Defender suivi des corrections uniquement efficace pour les ressources connues|Services de gestion du cycle de vie des actifs matures pour garantir Microsoft 365 Defender dispose d’une couverture à 100 %|N|
|Ingénierie & SecOps Teams|L’impact élevé et les vulnérabilités critiques dans les ressources sont corrigées en fonction de la stratégie|Ingénieurs SecOps, analystes SOC : Vulnérabilité & Conformité, Ingénierie de la sécurité|Processus défini pour catégoriser les vulnérabilités critiques et à risque élevé|[tableaux de bord Gestion des vulnérabilités Microsoft Defender](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)|Defender pour point de terminaison a identifié des appareils à fort impact et à haute alerte sans plan de correction ni implémentation de l’activité recommandée par Microsoft|Ajoutez un flux de travail pour avertir les propriétaires de biens lorsque l’activité de correction est requise dans les 30 jours par stratégie ; Implémentez un système de tickets pour informer les propriétaires de biens des étapes de correction.|N|
|Surveillance des équipes|L’état des menaces et des vulnérabilités est signalé via le portail intranet de l’entreprise|Analyste SOC de niveau 2|Rapports générés automatiquement à partir de Microsoft 365 Defender indiquant la progression de la correction des ressources|[Alertes dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/alerts) <p> Surveillance du degré de sécurisation|Aucun affichage ou rapport de tableau de bord n’est communiqué aux propriétaires d’actifs concernant l’état des menaces et des vulnérabilités des ressources.|Créez un script d’automatisation pour remplir l’état de correction des vulnérabilités des ressources critiques et à risque élevé pour l’organisation.|N|

Dans ces exemples de cas d’usage, les tests ont révélé plusieurs lacunes dans les exigences de l’équipe SOC qui ont été établies comme lignes de base pour les responsabilités de chaque équipe. La liste de vérification des cas d’usage peut être aussi complète que nécessaire pour s’assurer que l’équipe SOC est préparée pour l’intégration Microsoft 365 Defender aux exigences nouvelles ou existantes de SOC. Étant donné qu’il s’agit d’un processus itératif, le processus de développement de cas d’usage et le contenu de sortie de cas d’usage serviront naturellement à mettre à jour et à faire évoluer les runbooks du SOC avec les leçons apprises.

## <a name="update-production-runbooks-and-playbooks"></a>Mettre à jour les runbooks de production et les playbooks

Une fois que les tests de cas d’utilisation ont été corrigés pour toutes les lacunes, les leçons apprises et les métriques collectées peuvent être incorporées dans les runbooks de production (processus d’exploitation) et les playbooks de votre équipe SOC (réponses aux incidents et procédures d’escalade).

La maintenance des runbooks et des playbooks de l’équipe SOC peut être organisée de plusieurs façons. Chaque équipe SOC peut être responsable de sa propre version, ou il peut y avoir une seule version centralisée pour toutes les équipes à partager dans un référentiel central. La gestion des runbooks et des playbooks pour chaque organisation est basée sur la taille, les ensembles de compétences, les rôles et la séparation des tâches. Une fois qu’un runbook a été mis à jour, le processus de mise à jour du playbook doit suivre.

## <a name="use-a-standard-framework-for-escalation"></a>Utiliser un framework standard pour l’escalade

Les playbooks sont les étapes que les équipes SOC doivent suivre lorsqu’un événement réel se produit, en fonction de l’intégration et du test réussis du cas d’usage. Par conséquent, il est impératif que le SOC suive une approche formalisée de la réponse aux incidents, telle que la [norme de réponse aux incidents NIST](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) qui est devenue l’une des principales normes du secteur pour la réponse aux incidents.

Le processus de réponse aux incidents en quatre étapes du NIST comprend quatre phases :

1. Préparation
2. Détection et analyse
3. Limitation, éradication et récupération
4. Activité post-incident

### <a name="example-tracking-preparation-phase-activity"></a>Exemple : Suivi de l’activité de phase de préparation

L’une des bases principales d’un playbook d’escalade consiste à s’assurer qu’il y a peu d’ambiguïté quant à ce que chaque équipe SOC est censée faire avant, pendant et après un événement ou un incident. Par conséquent, il est recommandé de répertorier les instructions pas à pas.

Par exemple, la phase de préparation peut inclure une matrice if/then ou XoR de tâches. Dans le cas du nouveau cas d’utilisation de variante de hameçonnage, une telle matrice peut ressembler à ceci :

|Pourquoi l’escalade est-elle justifiée ?|Étape suivante|
|---|---|
|Alerte dans la surveillance SOC évaluée comme **critique** déclenchée > **500/heure**|Accédez au Playbook A, section 2, Activité 5 (avec un lien vers la section playbook)|
|eCommerce a signalé une attaque DDoS potentielle|Appeler le Playbook B-Section C, Activité 19 (avec un lien vers la section playbook)|
|L’exécutif a signalé un e-mail suspect comme tentative d’hameçonnage par lance|Accédez au Playbook 5, section 2, Activité 5 (avec un lien vers la section playbook)|

Après avoir exécuté la phase de préparation, les organisations doivent appeler les phases restantes comme indiqué par NIST :

- Détection et analyse
- Limitation, éradication et récupération
- Activité post-incident

## <a name="next-step"></a>Étape suivante

[Étape 6. Identifier les tâches de maintenance SOC](integrate-microsoft-365-defender-secops-tasks.md)
