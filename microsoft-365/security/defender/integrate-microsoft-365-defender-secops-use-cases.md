---
title: Étape 5. Développer et tester des cas d’utilisation
description: Les principes de base du développement et du test des cas d’utilisation lors de l’intégration Microsoft 365 Defender vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyber-attaque, secops, opérations de sécurité, soc
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
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 6e8073fe0d2dcbce28745eaeb8e8881c1f3b7a93
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53622345"
---
# <a name="step-5-develop-and-test-use-cases"></a>Étape 5. Développer et tester des cas d’utilisation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les méthodes recommandées pour déployer des Microsoft 365 Defender dans votre centre des opérations de sécurité (SOC) dépendent de l’ensemble actuel d’outils, de processus et de compétences de l’équipe SOC. La maintenance de la cybersécurité sur plusieurs plateformes peut être difficile en raison de la grande quantité de données provenant de dizaines voire de centaines de sources de sécurité. 

Les outils de sécurité sont interdépendants. L’activer dans une technologie de sécurité ou modifier un processus peut à son tour en rompre une autre. Pour cette raison, Microsoft recommande à votre équipe SOC de formaliser une méthode de définition et de définition des priorités des cas d’utilisation. Les cas d’utilisation permettent de définir les exigences et les processus de test pour les opérations SOC au sein de différentes équipes. Il crée une méthodologie pour capturer des mesures afin de déterminer si les rôles et la combinaison de tâches qui s’offrent à vous sont alignés sur la bonne équipe avec les compétences requises. 

## <a name="develop-and-formalize-use-case-process"></a>Développer et formaliser le processus de cas d’utilisation

Le SOC doit définir une norme et un processus de haut niveau pour le développement de cas d’utilisation, qui seraient réglementés par l’équipe de supervision SOC. L’équipe de supervision SOC doit travailler avec votre entreprise, votre service juridique, vos ressources humaines et d’autres groupes afin de hiérarchiser les cas d’utilisation du SOC qui finiront par se rendre dans les runbooks et les playbooks de l’équipe SOC. Les cas de priorité d’utilisation sont basés sur des objectifs, tels que la conformité ou la confidentialité.

Les activités de supervision SOC liées au développement de cas d’utilisation sont les suivantes : 

- Conditions requises
- Besoins en personnel ou en formation
- Licences logicielles
- Contrat du fournisseur
- Gestion du plan
- Maintenance du Registre des cas d’utilisation
- Maintenance/mise à jour des modèles

Pour faciliter les processus de création de runbook et de playbook, créez un arbre de décision de cas d’utilisation. Cette figure montre un exemple.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Processus de décision de cas d’utilisation":::

Une fois qu’une norme de cas d’utilisation de haut niveau a été définie et approuvée, l’étape suivante consiste à créer et tester un cas d’utilisation réel. Les sections suivantes utilisent des scénarios d’analyse anti-hameçonnage et contre les menaces et les vulnérabilités comme exemples.

## <a name="use-case-example-1-new-phishing-variant"></a>Exemple de cas d’utilisation 1 : Nouvelle variante de hameçonnage

La première étape de la création d’un cas d’utilisation consiste à décrire le flux de travail à l’aide d’un story board. Voici un exemple d’article de haut niveau pour une nouvelle notification d’attaque par hameçonnage à une équipe Threat Intelligence.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Exemple d’utilisation d’un flux de travail de cas pour une campagne anti-hameçonnage":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Appeler le flux de travail de cas d’utilisation par exemple 1

Une fois l’article approuvé, l’étape suivante consiste à appeler le flux de travail de cas d’utilisation. Voici un exemple de processus pour une campagne anti-hameçonnage. 
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="Exemple de flux de travail de cas d’utilisation détaillé pour une campagne anti-hameçonnage":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Exemple d’utilisation 2 : analyse des menaces et des vulnérabilités

Un autre scénario dans lequel un cas d’utilisation peut être utilisé est l’analyse des menaces et des vulnérabilités. Dans cet exemple, le SOC exige que les menaces et les vulnérabilités soient corrigés contre les biens via des processus approuvés qui incluent l’analyse des biens. 

Voici un exemple de storyboard de haut niveau pour la Gestion des menaces et des vulnérabilités ressources.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="Exemple d’utilisation du flux de travail de cas pour Gestion des menaces et des vulnérabilités":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Appeler le flux de travail de cas d’utilisation par exemple 2

Voici un exemple de processus pour l’analyse des menaces et des vulnérabilités.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="Exemple de flux de travail de cas d’utilisation détaillé pour Gestion des menaces et des vulnérabilités":::
 
### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Analyser la sortie du cas d’utilisation et les leçons apprises

Une fois qu’un cas d’utilisation a été approuvé et testé, les lacunes entre vos équipes de sécurité doivent être identifiées, ainsi que les personnes, les processus et les technologies Microsoft 365 Defender impliquées. Microsoft 365 Defender technologies doivent être analysées pour déterminer si elles sont capables d’obtenir les résultats souhaités. Celles-ci peuvent être suivis via une liste de contrôle ou une matrice. 

Par exemple, dans l’exemple de scénario anti-hameçonnage, les équipes SOC auraient pu faire les découvertes de ce tableau.


| Équipe SOC | Conditions requises | Personnes pour répondre aux exigences | Processus pour répondre aux exigences | Technologie pertinente | Intervalle identifié | Utiliser le journal des changements de cas | Exempt (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| Équipe Threat Intelligence et Analytics | Les sources de données alimentent correctement les moteurs d’intelligence des menaces. | Analyste/ingénieur threat intelligence | Exigences de flux de données établies, déclencheurs d’intelligence des menaces provenant de sources approuvées | Microsoft Defender pour l’identité, Microsoft Defender pour le point de terminaison | L’équipe Threat Intelligence n’a pas utilisé de script d’automatisation pour lier Microsoft 365 Defender API aux moteurs Intel contre les menaces | Ajouter des Microsoft 365 Defender en tant que sources de données aux moteurs de menaces <BR> <BR> Mettre à jour le carnet d’exemples d’utilisation | N |
| Équipe de surveillance | Les sources de données alimentent correctement les tableaux de bord de surveillance | Analyste SOC de niveau 1,2 – Surveillance & alertes | Workflow for reporting Security & Compliance Center Secure Score | [Alertes dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/alerts)  <br><br> Surveillance du score de sécurisation  | Aucun mécanisme pour les analystes SOC permettant de signaler la détection réussie d’une nouvelle variante d’hameçonnage pour améliorer le score de sécurisation <br><br> [Reporting in Security & Compliance Center](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance)| Ajouter un processus de suivi de l’amélioration du score de sécurité aux flux de travail de création de rapports | N | 
| Ingénierie et équipe SecOps | Les mises à jour des contrôles de modification sont réalisées dans les runbooks d’équipe SOC | Ingénieur SOC de niveau 2 | Procédure de notification de contrôle des changements pour les runbooks d’équipe SOC | Modifications approuvées apportées aux appareils de sécurité | Les modifications apportées Microsoft 365 Defender la connectivité à la technologie de sécurité SOC nécessitent une approbation | Ajouter Microsoft Cloud App Security, Defender pour l’identité, Defender pour le point de terminaison, Centre de sécurité & conformité aux runbooks SOC | v |
|||||||||

En outre, les équipes SOC auraient pu faire les découvertes décrites dans le tableau ci-dessous en ce qui concerne Gestion des menaces et des vulnérabilités scénario décrit ci-dessus :

| Équipe SOC | Conditions requises | Personnes pour répondre aux exigences | Processus pour répondre aux exigences | Technologie pertinente | Intervalle identifié | Utiliser le journal des changements de cas | Exempt (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| Supervision SOC | Tous les biens connectés à des réseaux approuvés sont identifiés et catégorisés | Supervision SOC, propriétaires de la bu, propriétaires d’applications, propriétaires de biens, etc. | Système de gestion des biens centralisé pour découvrir et lister les catégories et attributs des biens en fonction des risques. | ServiceNow ou d’autres ressources. <br><br>[Microsoft 365 Inventaire des appareils](/security/defender-endpoint/device-discovery) | Seuls 70 % des biens ont été découverts. Microsoft 365 Defender correction effective uniquement pour les ressources connues | Des services de gestion du cycle de vie des biens Microsoft 365 Defender une couverture de 100 % | N |
| Engineering & SecOps Teams | Les ressources dont l’impact est élevé et les vulnérabilités critiques sont corrigés conformément à la stratégie | Ingénieurs SecOps, analystes SOC : Conformité des &, Ingénierie de la sécurité | Processus défini pour catégoriser les vulnérabilités à risque élevé et critique | [Tableaux de bord de gestion des menaces et des vulnérabilités](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) | Defender pour le point de terminaison a identifié un impact élevé, des périphériques d’alerte élevés sans plan de correction ou implémentation de l’activité recommandée par Microsoft | Ajoutez un flux de travail pour avertir les propriétaires de biens lorsque l’activité de correction est requise dans un délai de 30 jours par stratégie . Implémenter un système de gestion des tickets pour informer les propriétaires de biens des étapes de correction. | N |
| Analyse Teams | L’état des menaces et des vulnérabilités est signalé via le portail intranet de l’entreprise | Analyste SOC de niveau 2 | Rapports générés automatiquement à partir de Microsoft 365 Defender la progression de la correction des biens | [Alertes dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/alerts) <br><br> Surveillance du score de sécurisation | Aucun affichage ou rapport de tableau de bord n’est communiqué aux propriétaires de biens concernant l’état des menaces et des vulnérabilités des biens. | Créez un script d’automatisation pour remplir l’état de correction des vulnérabilités de ressources critiques et à risque élevé pour l’organisation. | N |
|||||||||

Dans ces exemples d’utilisation, le test a révélé plusieurs lacunes dans les exigences de l’équipe SOC qui ont été établies en tant que lignes de base pour les responsabilités de chaque équipe. La liste de vérification des cas d’utilisation peut être aussi complète que nécessaire pour s’assurer que l’équipe SOC est prête pour l’intégration Microsoft 365 Defender aux exigences soc nouvelles ou existantes. Étant donné qu’il s’agit d’un processus itératif, le processus de développement de cas d’utilisation et le contenu de sortie de cas d’utilisation serviront naturellement à mettre à jour et à faire la maturité des runbooks soc avec les leçons apprises.

## <a name="update-production-runbooks-and-playbooks"></a>Mettre à jour les runbooks et les playbooks de production

Une fois que les tests de cas d’utilisation ont été corrigés pour toutes les lacunes, les leçons apprises et les mesures collectées dans ces derniers peuvent être incorporées dans les runbooks de production (processus d’exploitation) et les manuels de votre équipe SOC (réponses aux incidents et procédures d’escalade). 

La maintenance des runbooks et des manuels d’équipe SOC peut être organisée de nombreuses façons. Chaque équipe SOC peut être responsable de sa propre version, ou il peut y avoir une version centralisée unique que toutes les équipes peuvent partager dans un référentiel central. La gestion des runbooks et des playbooks pour des organisations individuelles est basée sur la taille, les jeux de compétences, les rôles et la répartition des tâches. Une fois qu’un runbook a été mis à jour, le processus de mise à jour du manuel doit suivre. 

## <a name="use-a-standard-framework-for-escalation"></a>Utiliser une infrastructure standard pour l’escalade

Les playbooks sont les étapes que les équipes SOC doivent suivre lorsqu’un événement réel se produit, en fonction de l’intégration et du test réussis du cas d’utilisation. Par conséquent, il est impératif que la SOC suive une approche formelle de la réponse aux incidents, telle que la norme de réponse aux incidents [NIST](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) qui est devenue l’une des principales normes du secteur pour la réponse aux incidents.

Le processus de réponse aux incidents en quatre étapes du NIST comprend quatre phases :

1.  Préparation
2.  Détection et analyse
3.  Limitation, éradication et récupération
4.  Activité post-incident

### <a name="example-tracking-preparation-phase-activity"></a>Exemple : suivi de l’activité de phase de préparation

L’une des bases fondamentales d’un manuel d’escalade consiste à s’assurer qu’il existe peu d’ambiguïté quant à ce que chaque équipe SOC est supposée faire avant, pendant et après un événement ou un incident. Par conséquent, il est bon de lister des instructions étape par étape. 

Par exemple, la phase de préparation peut inclure une matrice if/then ou XoR de tâches. Dans le cas du nouvel exemple d’utilisation de variante de hameçonnage, une telle matrice peut ressembler à ceci :

| Pourquoi l’escalade est-elle justifié ? | Étape suivante |
|:-------|:-----|
| Alerte dans soc monitoring rated as **critical** triggered > **500/hour** | Go to Playbook A, Section 2, Activity 5 (with a link to the playbook section) |
| eCommerce a signalé une attaque DDoS potentielle | Appeler playbook B-Section C, Activity 19 (avec un lien vers la section playbook) |
| Un cadre a signalé un e-mail suspect comme une tentative de harponnage | Go to Playbook 5, Section 2, Activity 5 (with a link to the playbook section) |
|||

Après l’exécution de la phase de préparation, les organisations doivent appeler les phases restantes comme indiqué par NIST :

- Détection et analyse
- Limitation, éradication et récupération
- Activité post-incident 

## <a name="next-step"></a>Étape suivante

[Étape 6. Identifier les tâches de maintenance SOC](integrate-microsoft-365-defender-secops-tasks.md)

