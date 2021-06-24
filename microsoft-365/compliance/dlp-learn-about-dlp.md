---
title: En savoir plus sur la protection contre la perte de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Découvrez comment protéger vos informations sensibles à l’aide Microsoft 365 stratégies et outils de protection contre la perte de données et faire une visite guidée du cycle de vie DLP.
ms.openlocfilehash: 9b449886e0856f7407fcd49b83192dd0c01474bd
ms.sourcegitcommit: ebb1c3b4d94058a58344317beb9475c8a2eae9a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53108258"
---
# <a name="learn-about-data-loss-prevention"></a>En savoir plus sur la protection contre la perte de données

Les organisations ont sous leur contrôle des informations sensibles telles que des données financières, des données propriétaires, des numéros de carte de crédit, des dossiers de santé ou des numéros de sécurité sociale. Pour protéger ces données sensibles et réduire les risques, ils ont besoin d’un moyen d’empêcher leurs utilisateurs de les partager de manière inappropriée avec des personnes qui ne devraient pas en avoir. Cette pratique est appelée protection contre la perte de données (DLP).

Dans Microsoft 365, vous implémentez la protection contre la perte de données en définissant et en appliquant des stratégies DLP. Avec une stratégie DLP, vous pouvez identifier, surveiller et protéger automatiquement les éléments sensibles dans :

- Microsoft 365 services tels que Teams, Exchange, SharePoint et OneDrive
- Office applications telles que Word, Excel et PowerPoint
- Windows 10 de terminaison
- applications cloud non-Microsoft
- partages de fichiers locaux et partages de fichiers SharePoint.

Microsoft 365 détecte les éléments sensibles à l’aide d’une analyse approfondie du contenu, et pas simplement par une simple analyse de texte. Le contenu est analysé pour les correspondances de données principales avec les mots clés, par l’évaluation des expressions régulières, par la validation de fonction interne et par les correspondances de données secondaires à proximité de la correspondance de données principale. En outre, la DLP utilise également des algorithmes d’apprentissage automatique et d’autres méthodes pour détecter le contenu qui correspond à vos stratégies DLP.
  
## <a name="dlp-is-part-of-the-larger-microsoft-365-compliance-offering"></a>La DLP fait partie de l’offre plus Microsoft 365 conformité

Microsoft 365 DLP n’est qu’un des outils de conformité Microsoft 365 que vous utiliserez pour protéger vos éléments sensibles où qu’ils habitent ou se déplacent. Vous devez comprendre les autres outils de l’ensemble Microsoft 365 conformité, la façon dont ils s’interaraient et fonctionnent mieux ensemble.  Consultez les [Microsoft 365 conformité pour](protect-information.md) en savoir plus sur le processus de protection des informations.

## <a name="protective-actions-of-dlp-policies"></a>Actions de protection des stratégies DLP

Microsoft 365 Les stratégies DLP sont la manière dont vous surveillez les activités que les utilisateurs prennent sur les éléments sensibles au repos, les éléments sensibles en transit ou les éléments sensibles en cours d’utilisation et vous prenez des mesures de protection. Par exemple, lorsqu’un utilisateur tente d’agir de la sorte, par exemple en copiant un élément sensible vers un emplacement non approbé ou en partageant des informations médicales dans un e-mail ou dans d’autres conditions d’une stratégie, la DLP peut :

- afficher un conseil de stratégie de fenêtre pop-up à l’utilisateur l’avertissant qu’il essaie peut-être de partager un élément sensible de manière inappropriée ;
- bloquer le partage et, via un conseil de stratégie, permettre à l’utilisateur de remplacer le bloc et de capturer la justification des utilisateurs ;
- bloquer le partage sans l’option de remplacement
- pour les données au repos, les éléments sensibles peuvent être verrouillés et déplacés vers un emplacement de mise en quarantaine sécurisé
- pour Teams conversation instantanée, les informations sensibles ne seront pas affichées

Toutes les activités surveillées par DLP sont enregistrées dans le [journal Microsoft 365 audit](search-the-audit-log-in-security-and-compliance.md) par défaut et acheminées vers [l’Explorateur d’activités.](data-classification-activity-explorer.md) Lorsqu’un utilisateur effectue une action qui répond aux critères d’une stratégie DLP et que des alertes sont configurées, DLP fournit des alertes dans le tableau de bord de gestion des alertes [DLP.](dlp-configure-view-alerts-policies.md)

## <a name="dlp-lifecycle"></a>Cycle de vie DLP

Une implémentation DLP suit généralement ces phases principales.

- [Planifier la DLP](#plan-for-dlp)
- [Préparer la DLP](#prepare-for-dlp)
- [Déployer vos stratégies en production](#deploy-your-policies-in-production)


<!--ADD DIAGRAM OF THE DLP LIFECYCLE WORK ON WITH MAS-->

### <a name="plan-for-dlp"></a>Planifier la DLP

Microsoft 365 La surveillance et la protection DLP sont natives aux applications que les utilisateurs utilisent tous les jours. Cela permet de protéger les éléments sensibles de votre organisation contre les activités risquées, même si vos utilisateurs ne sont pas habitués aux pratiques et aux pratiques de protection contre la perte de données. Si votre organisation et vos utilisateurs sont nouveaux dans les pratiques de protection contre la perte de données, l’adoption de la protection contre la perte de données peut nécessiter une modification de vos processus d’entreprise et vos utilisateurs auront un changement de culture. Toutefois, avec une planification, des tests et un réglage appropriés, vos stratégies DLP protègent vos éléments sensibles tout en réduisant les perturbations potentielles des processus d’entreprise.

**Planification de la technologie pour la DLP**

N’oubliez pas que la DLP en tant que technologie peut surveiller et protéger vos données au repos, les données en cours d’utilisation et les données en mouvement sur les services Microsoft 365, les appareils Windows 10, les partages de fichiers locaux et les SharePoint locaux. Il existe des implications en matière de planification pour les différents emplacements, le type de données que vous souhaitez surveiller et protéger, ainsi que les actions à prendre lorsqu’une correspondance de stratégie se produit.  

**Planification des processus métiers pour la DLP**

Les stratégies DLP peuvent bloquer les activités interdites, telles que le partage inapproprié d’informations sensibles par courrier électronique. Lorsque vous planifiez vos stratégies DLP, vous devez identifier les processus métiers qui touchent vos éléments sensibles. Les propriétaires de processus d’entreprise peuvent vous aider à identifier les comportements utilisateur appropriés qui doivent être autorisés et les comportements inappropriés des utilisateurs qui doivent être protégés contre. Vous devez d’abord planifier vos stratégies et [](data-classification-activity-explorer.md) les déployer en mode test, puis évaluer leur impact via l’Explorateur d’activités avant de les appliquer dans des modes plus restrictifs.

**Planification de la culture organisationnelle pour la DLP**

Une implémentation réussie de la protection contre la perte de données dépend autant de la formation et de l’familiarisation de vos utilisateurs aux pratiques de protection contre la perte de données que de la mise en place de stratégies bien planifiées et bien mises au point. Étant donné que vos utilisateurs sont très impliqués, n’oubliez pas de planifier leur formation. Vous pouvez utiliser stratégiquement les conseils de stratégie pour sensibiliser vos utilisateurs avant de modifier l’application de la stratégie du mode test à des modes plus restrictifs.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for Microsoft 365 data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>Préparer la DLP

Vous pouvez appliquer des stratégies DLP aux données au repos, aux données en cours d’utilisation et aux données en mouvement à des emplacements, tels que :

- Exchange Online courrier électronique
- Sites SharePoint Online
- Comptes OneDrive
- conversation et messages de canal Teams
- Microsoft Cloud App Security
- Appareils Windows 10
- Référentiels locaux

Chacune d’elles a des conditions préalables différentes. Les éléments sensibles dans certains emplacements, tels que Exchange en ligne, peuvent être placés sous le cadre de la DLP en configurant simplement une stratégie qui s’applique à eux. D’autres, telles que les référentiels de fichiers locaux, nécessitent un déploiement du scanneur Azure Information Protection (AIP). Vous devez préparer votre environnement, les stratégies de brouillon de code et les tester minutieusement avant d’activer les actions de blocage.

### <a name="deploy-your-policies-in-production"></a>Déployer vos stratégies en production

#### <a name="design-your-policies"></a>Concevoir vos stratégies

Commencez par définir vos objectifs de contrôle et la façon dont ils s’appliquent à chaque charge de travail respective. Rédigez une stratégie qui reflète vos objectifs. N’hésitez pas à commencer avec une charge de travail à la fois, ou sur toutes les charges de travail, il n’y a pas encore d’impact.

#### <a name="implement-policy-in-test-mode"></a>Implémenter une stratégie en mode test

Évaluez l’impact des contrôles en les implémentant avec une stratégie DLP en mode test. Il est possible d’appliquer la stratégie à toutes les charges de travail en mode test, afin de pouvoir obtenir l’ensemble des résultats, mais vous pouvez commencer par une charge de travail si nécessaire.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Surveiller les résultats et affiner la stratégie

En mode test, surveillez les résultats de la stratégie et afinez-la afin qu’elle réponde à vos objectifs de contrôle tout en vous assurant que vous n’avez pas d’impact négatif ou involontaire sur les flux de travail et la productivité des utilisateurs valides. Voici quelques exemples d’éléments à affiner :

- ajustement des emplacements et des personnes/lieux qui sont dans ou hors de l’étendue
- régler les conditions et les exceptions utilisées pour déterminer si un élément et ce qui est fait avec lui correspond à la stratégie
- définition/s d’informations sensibles
- les actions
- niveau de restrictions
- ajouter de nouveaux contrôles
- ajouter de nouvelles personnes
- ajouter de nouvelles applications restreintes
- ajouter de nouveaux sites restreints

#### <a name="enable-the-control-and-tune-your-policies"></a>Activer le contrôle et régler vos stratégies

Une fois que la stratégie atteint tous vos objectifs, allumez-la. Continuez à surveiller les résultats de l’application de stratégie et à régler selon vos besoins. En règle générale, les stratégies prennent effet environ une heure après avoir été désactivées. 

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>Vue d’ensemble de la configuration des stratégies DLP

Vous avez la flexibilité nécessaire pour créer et configurer vos stratégies DLP. Vous pouvez commencer à partir d’un modèle prédéféré et créer une stratégie en quelques clics ou vous pouvez concevoir votre propre modèle de base. Quelle que soit votre choix, toutes les stratégies DLP nécessitent les mêmes informations de votre part.

1. **Choisissez ce que vous souhaitez** surveiller : Microsoft 365 est livré avec de nombreux modèles de stratégie prédéfincis pour vous aider à commencer ou vous pouvez créer une stratégie personnalisée.
    - Modèle de stratégie prédéféré : données financières, données médicales et médicales, données de confidentialité pour différents pays et régions.
    - Une stratégie personnalisée qui utilise les types d’informations sensibles disponibles, les étiquettes de rétention et les étiquettes de confidentialité.
2. **Choisissez l’emplacement à surveiller :** sélectionnez un ou plusieurs emplacements que DLP doit surveiller pour les informations sensibles. Vous pouvez surveiller :
    
emplacement | Inclure/exclure par|
|---------|---------|
|e-mail Exchange| groupes de distribution|
|sites SharePoint |sites |
|comptes OneDrive |comptes ou groupes de distribution |
|conversation et messages de canal Teams |comptes |
|appareils Windows 10 |utilisateurs ou groupe |
|Microsoft Cloud App Security |instance |
|Référentiels locaux| chemin d’accès au fichier de référentiel|

3. **Choisissez les conditions qui doivent correspondre** pour qu’une stratégie soit appliquée à un élément : vous pouvez accepter des conditions pré-configurées ou définir des conditions personnalisées. En voici quelques exemples :

- contient un type spécifié d’informations sensibles qui est utilisé dans un certain contexte. Par exemple, 95 numéros de sécurité sociale envoyés par courrier électronique à un destinataire extérieur à votre organisation.
- l’élément possède une étiquette de sensibilité spécifiée
- l’élément avec des informations sensibles est partagé en interne ou en externe

4. **Choisissez l’action à prendre lorsque les conditions de stratégie sont** remplies : les actions dépendent de l’emplacement où l’activité se produit.  En voici quelques exemples :

- SharePoint/Exchange/OneDrive : bloquer l’accès au contenu aux personnes extérieures à votre organisation. Affichez un conseil à l’utilisateur et envoyez-lui une notification par courrier électronique lui avertissant qu’il prend une action qui est interdite par la stratégie DLP.
- Teams Conversation et canal : empêcher le partage d’informations sensibles dans la conversation ou le canal
- Windows 10 Appareils : auditer ou restreindre la copie d’un élément sensible sur un périphérique USB à supprimer 
- Office Applications : affichez une fenêtre popup pour avertir l’utilisateur qu’il s’engage dans un comportement risqué et bloquer ou bloquer, mais autoriser le remplacement.
- Partages de fichiers locaux : déplacer le fichier de l’endroit où il est stocké vers un dossier de mise en quarantaine

> [!NOTE]
> Les conditions et les actions à prendre sont définies dans un objet appelé Règle.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft 365 Compliance center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Après avoir créé une stratégie DLP dans le Centre de conformité, elle est stockée dans un magasin central de stratégies, puis synchronisée avec les différentes sources de contenu, notamment :
  
- Depuis Exchange Online vers Outlook sur le web et Outlook.
- Sites OneDrive Entreprise.
- Sites SharePoint Online.
- Programmes de bureau Office (Excel, PowerPoint et Word).
- Canaux et messages de conversations Microsoft Teams.
    
Une fois la stratégie synchronisée avec les emplacements adéquats, elle commence à évaluer le contenu et à mettre en place des actions.

## <a name="viewing-policy-application-results"></a>Affichage des résultats de l’application de stratégie

DLP signale une grande quantité d’informations dans les Microsoft 365 de la surveillance, des correspondances et des actions de stratégie, ainsi que des activités des utilisateurs. Vous devez utiliser ces informations et agir sur ces informations pour régler vos stratégies et les actions de tri prises sur les éléments sensibles. La télémétrie est d’abord Microsoft 365 [journaux d’audit](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-center) du Centre de conformité, est traitée et permet d’utiliser différents outils de création de rapports. Chaque outil de rapports a un objectif différent.  

### <a name="dlp-alerts-dashboard"></a>Tableau de bord des alertes DLP

Lorsque DLP effectue une action sur un élément sensible, vous pouvez être averti de cette action via une alerte configurable. Au lieu d’empiler ces alertes dans une boîte aux lettres pour que vous les parliez, le centre de conformité les rend disponibles dans le tableau de bord de gestion des [alertes DLP.](dlp-configure-view-alerts-policies.md) Utilisez le tableau de bord alertes DLP pour configurer les alertes, les examiner, les trier et suivre la résolution des alertes DLP. Voici un exemple d’alertes générées par les correspondances de stratégie et les activités de Windows 10 appareils.

> [!div class="mx-imgBorder"]
> ![Information d’alerte](../media/Alert-info-1.png)

Vous pouvez également afficher les détails de l’événement associé avec des métadonnées complètes dans le même tableau de bord

> [!div class="mx-imgBorder"]
> ![Informations sur un événement](../media/Event-info-1.png)

### <a name="reports"></a>Rapports

Les rapports [DLP montrent](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) de larges tendances au fil du temps et donnent des informations spécifiques sur :

- **Correspondances de stratégies DLP** au fil du temps et filtrage par plage de dates, emplacement, stratégie ou action
- **Les correspondances d’incident DLP** montrent également des correspondances au fil du temps, mais s’pivotent sur les éléments plutôt que sur les règles de stratégie.
- **Les remplacements** et faux positifs DLP indiquent le nombre de faux positifs et, s’ils sont configurés, les remplacements par l’utilisateur, ainsi que la justification de l’utilisateur.

### <a name="dlp-activity-explorer"></a>Explorateur d’activités DLP

L’onglet Explorateur d’activités de  la page DLP a le filtre Activité prédéfinie *sur DLPRuleMatch*. Utilisez cet outil pour passer en revue l’activité liée au contenu qui contient des informations sensibles ou qui comporte des étiquettes appliquées, telles que les étiquettes qui ont été modifiées, les fichiers modifiés et une règle.

![Capture d’écran de l’explorateur d’activités d’étendue DLPRuleMatch ](../media/dlp-activity-explorer.png)

Pour plus d’informations, voir [La mise en place de l’Explorateur d’activités](data-classification-activity-explorer.md)

Pour en savoir plus sur Microsoft 365 DLP, voir :

- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](endpoint-dlp-learn-about.md)
- [En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préversion)](dlp-teams-default-policy.md)
- [En savoir plus sur le scanneur local de protection contre la perte de données Microsoft 365 (préversion)](dlp-on-premises-scanner-learn.md)
- [En savoir plus sur l’extension de la conformité Microsoft (préversion).](dlp-chrome-learn-about.md)
- [En savoir plus sur le tableau de bord des alertes de protection contre la perte de données](dlp-alerts-dashboard-learn.md)

Pour découvrir comment utiliser la protection contre la perte de données pour se conformer aux réglementations en matière de confidentialité des données, voir [Deploy information protection for data privacy regulations with Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).