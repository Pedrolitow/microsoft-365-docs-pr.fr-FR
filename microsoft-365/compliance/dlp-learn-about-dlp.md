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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Découvrez comment protéger vos informations sensibles à l’aide de Microsoft Purview stratégies et outils de protection contre la perte de données et effectuer une visite guidée du cycle de vie de la protection contre la perte de données.
ms.openlocfilehash: 1d05eb2ae7b7071a79448596832eb6594ab680ef
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669691"
---
# <a name="learn-about-data-loss-prevention"></a>En savoir plus sur la protection contre la perte de données

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Les organisations disposent d’informations sensibles sous leur contrôle, telles que les données financières, les données propriétaires, les numéros de carte de crédit, les dossiers de santé ou les numéros de sécurité sociale. Pour protéger ces données sensibles et réduire les risques, ils ont besoin d’un moyen d’empêcher leurs utilisateurs de les partager de manière inappropriée avec des personnes qui ne devraient pas les avoir. Cette pratique est appelée protection contre la perte de données (DLP).

Dans Microsoft Purview, vous implémentez la protection contre la perte de données en définissant et en appliquant des stratégies DLP. Avec une stratégie DLP, vous pouvez identifier, surveiller et protéger automatiquement les éléments sensibles dans :

- Microsoft 365 services tels que Teams, Exchange, SharePoint et OneDrive
- Office applications telles que Word, Excel et PowerPoint
- points de terminaison Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures)
- applications cloud autres que Microsoft
- partages de fichiers locaux et SharePoint locaux.

DLP détecte les éléments sensibles à l’aide d’une analyse de contenu approfondie, et pas seulement par une simple analyse de texte. Le contenu est analysé pour les correspondances de données primaires avec des mots clés, par l’évaluation des expressions régulières, par la validation de fonction interne et par les correspondances de données secondaires qui se trouvent à proximité de la correspondance de données primaires. En outre, DLP utilise également des algorithmes d’apprentissage automatique et d’autres méthodes pour détecter le contenu qui correspond à vos stratégies DLP.

## <a name="dlp-is-part-of-the-larger-microsoft-purview-offering"></a>DLP fait partie de l’offre de Microsoft Purview plus grande

DLP n’est qu’un des outils Microsoft Purview que vous utiliserez pour protéger vos éléments sensibles où qu’ils vivent ou voyagent. Vous devez comprendre les autres outils de l’ensemble d’outils Microsoft Purview, comment ils interrelissent et fonctionnent mieux ensemble.  Consultez [Microsoft Purview outils](protect-information.md) pour en savoir plus sur le processus de protection des informations.

## <a name="protective-actions-of-dlp-policies"></a>Actions de protection des stratégies DLP

Les stratégies DLP vous permettent de surveiller les activités que les utilisateurs effectuent sur les éléments sensibles au repos, les éléments sensibles en transit ou les éléments sensibles utilisés et prennent des mesures de protection. Par exemple, lorsqu’un utilisateur tente d’effectuer une action interdite, comme copier un élément sensible vers un emplacement non approuvé ou partager des informations médicales dans un e-mail ou d’autres conditions énoncées dans une stratégie, DLP peut :

- afficher un conseil de stratégie contextuel à l’utilisateur qui l’avertit qu’il tente peut-être de partager un élément sensible de manière inappropriée
- bloquer le partage et, via un conseil de stratégie, permettre à l’utilisateur de remplacer le bloc et de capturer la justification des utilisateurs
- bloquer le partage sans l’option de remplacement
- pour les données au repos, les éléments sensibles peuvent être verrouillés et déplacés vers un emplacement de quarantaine sécurisé
- pour Teams conversation, les informations sensibles ne s’affichent pas

Toutes les activités surveillées par DLP sont enregistrées dans le [journal d’audit Microsoft 365](search-the-audit-log-in-security-and-compliance.md) par défaut et routées vers [l’Explorateur d’activités](data-classification-activity-explorer.md). Lorsqu’un utilisateur effectue une action qui répond aux critères d’une stratégie DLP et que vous avez configuré des alertes, DLP fournit des alertes dans le [tableau de bord de gestion des alertes DLP](dlp-configure-view-alerts-policies.md).

## <a name="dlp-lifecycle"></a>Cycle de vie DLP

Une implémentation DLP suit généralement ces phases majeures.

- [Planifier la DLP](#plan-for-dlp)
- [Préparer la protection contre la perte de données](#prepare-for-dlp)
- [Déployer vos stratégies en production](#deploy-your-policies-in-production)


<!--ADD DIAGRAM OF THE DLP LIFECYCLE WORK ON WITH MAS-->

### <a name="plan-for-dlp"></a>Planifier la DLP

La surveillance et la protection DLP sont natives pour les applications que les utilisateurs utilisent chaque jour. Cela permet de protéger les éléments sensibles de votre organisation contre les activités risquées, même si vos utilisateurs ne sont pas habitués à la réflexion et aux pratiques de protection contre la perte de données. Si votre organisation et vos utilisateurs débutent avec les pratiques de protection contre la perte de données, l’adoption de la protection contre la perte de données peut nécessiter une modification de vos processus métier et un changement de culture s’impose à vos utilisateurs. Toutefois, avec une planification, des tests et un réglage appropriés, vos stratégies DLP protègent vos éléments sensibles tout en réduisant les interruptions potentielles des processus métier.

**Planification de la technologie pour DLP**

N’oubliez pas que DLP en tant que technologie peut surveiller et protéger vos données au repos, les données en cours d’utilisation et les données en mouvement sur Microsoft 365 services, Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures), les partages de fichiers locaux et les SharePoint locaux. Il existe des implications de planification pour les différents emplacements, le type de données que vous souhaitez surveiller et protéger, ainsi que les actions à entreprendre lorsqu’une correspondance de stratégie se produit.

**Planification des processus métier pour DLP**

Les stratégies DLP peuvent bloquer les activités interdites, telles que le partage inapproprié d’informations sensibles par e-mail. Lorsque vous planifiez vos stratégies DLP, vous devez identifier les processus métier qui touchent vos éléments sensibles. Les propriétaires de processus métier peuvent vous aider à identifier les comportements utilisateur appropriés qui doivent être autorisés et les comportements utilisateur inappropriés qui doivent être protégés contre. Vous devez d’abord planifier vos stratégies et les déployer en mode test et évaluer leur impact via [l’Explorateur d’activités](data-classification-activity-explorer.md) , avant de les appliquer dans des modes plus restrictifs.

**Planification de la culture organisationnelle pour DLP**

Une implémentation DLP réussie dépend autant de la formation et de l’adaptation de vos utilisateurs aux pratiques de protection contre la perte de données que des stratégies bien planifiées et adaptées. Étant donné que vos utilisateurs sont fortement impliqués, veillez également à planifier leur formation. Vous pouvez utiliser stratégiquement des conseils de stratégie pour sensibiliser vos utilisateurs avant de changer l’application de la stratégie du mode test à des modes plus restrictifs.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>Préparer la protection contre la perte de données

Vous pouvez appliquer des stratégies DLP aux données au repos, aux données en cours d’utilisation et aux données en mouvement dans des emplacements, par exemple :

- e-mail Exchange Online
- Sites SharePoint Online
- Comptes OneDrive
- conversation et messages de canal Teams
- Microsoft Cloud App Security
- Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures)
- Référentiels locaux
- Sites PowerBI

Chacun a des prérequis différents. Les éléments sensibles dans certains emplacements, comme Exchange en ligne, peuvent être placés sous le parapluie DLP en configurant simplement une stratégie qui s’applique à eux. D’autres, comme les référentiels de fichiers locaux, nécessitent un déploiement d’un scanneur Azure Information Protection (AIP). Vous devez préparer votre environnement, les stratégies de brouillon de code et les tester minutieusement avant d’activer les actions de blocage.

### <a name="deploy-your-policies-in-production"></a>Déployer vos stratégies en production

#### <a name="design-your-policies"></a>Concevoir vos stratégies

Commencez par définir vos objectifs de contrôle et la façon dont ils s’appliquent à chaque charge de travail respective. Rédigez une stratégie qui incarne vos objectifs. N’hésitez pas à commencer avec une charge de travail à la fois, ou sur toutes les charges de travail. Il n’y a pas encore d’impact.

#### <a name="implement-policy-in-test-mode"></a>Implémenter une stratégie en mode test

Évaluez l’impact des contrôles en les implémentant avec une stratégie DLP en mode test. Il est possible d’appliquer la stratégie à toutes les charges de travail en mode test, afin d’obtenir l’étendue complète des résultats, mais vous pouvez commencer par une charge de travail si nécessaire.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Surveiller les résultats et affiner la stratégie

En mode test, surveillez les résultats de la stratégie et ajustez-la afin qu’elle réponde à vos objectifs de contrôle tout en vous assurant que vous n’avez pas d’impact négatif ou involontaire sur les flux de travail et la productivité des utilisateurs valides. Voici quelques exemples de choses à affiner :

- ajustement des emplacements et des personnes/lieux qui sont dans ou hors de portée
- paramétrer les conditions et les exceptions utilisées pour déterminer si un élément et ce qui est fait avec lui correspond à la stratégie
- définition/s d’informations sensibles
- actions
- niveau de restrictions
- ajouter de nouveaux contrôles
- ajouter de nouvelles personnes
- ajouter de nouvelles applications restreintes
- ajouter de nouveaux sites restreints

> [!NOTE]
> _L’arrêt du traitement d’autres règles_ ne fonctionne pas en mode test, même lorsqu’il est activé.

#### <a name="enable-the-control-and-tune-your-policies"></a>Activer le contrôle et paramétrer vos stratégies

Une fois que la stratégie atteint tous vos objectifs, activez-la. Continuez à surveiller les résultats de l’application de stratégie et à régler en fonction des besoins. 

> [!NOTE]
> En général, les stratégies prennent effet environ une heure après avoir été activées.

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>Vue d’ensemble de la configuration de la stratégie DLP

Vous disposez d’une certaine flexibilité dans la façon dont vous créez et configurez vos stratégies DLP. Vous pouvez commencer à partir d’un modèle prédéfini et créer une stratégie en quelques clics ou vous pouvez concevoir la vôtre à partir de zéro. Quel que soit votre choix, toutes les stratégies DLP nécessitent les mêmes informations de votre part.

1. **Choisissez ce que vous souhaitez surveiller** : DLP est fourni avec de nombreux modèles de stratégie prédéfinis pour vous aider à commencer ou à créer une stratégie personnalisée.
    - Modèle de stratégie prédéfini : données financières, données médicales et médicales, données de confidentialité pour différents pays et régions.
    - Stratégie personnalisée qui utilise les types d’informations sensibles, les étiquettes de rétention et les étiquettes de confidentialité disponibles.
2. **Choisissez l’emplacement à surveiller** . Vous choisissez un ou plusieurs emplacements que vous souhaitez que DLP surveille pour les informations sensibles. Vous pouvez surveiller :

emplacement | Inclure/exclure par|
|---------|---------|
|e-mail Exchange| groupes de distribution|
|sites SharePoint |sites |
|comptes OneDrive |comptes ou groupes de distribution |
|conversation et messages de canal Teams |compte ou groupe de distribution |
|Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures) |utilisateurs ou groupe |
|Microsoft Cloud App Security |instance |
|Référentiels locaux| chemin d’accès au fichier de référentiel|

3. **Choisissez les conditions qui doivent être mises en correspondance pour qu’une stratégie soit appliquée à un élément** . Vous pouvez accepter des conditions préconfigurées ou définir des conditions personnalisées. En voici quelques exemples :

- contient un type spécifié d’informations sensibles qui est utilisé dans un certain contexte. Par exemple, 95 numéros de sécurité sociale sont envoyés par e-mail au destinataire en dehors de votre organisation.
- l’élément a une étiquette de confidentialité spécifiée
- l’élément avec des informations sensibles est partagé en interne ou en externe

4. **Choisissez l’action à entreprendre lorsque les conditions de stratégie sont remplies** . Les actions dépendent de l’emplacement où l’activité se produit.  En voici quelques exemples :

- SharePoint/Exchange/OneDrive : bloquez l’accès au contenu aux personnes extérieures à votre organisation. Affichez un conseil à l’utilisateur et envoyez-lui une notification par e-mail indiquant qu’il effectue une action interdite par la stratégie DLP.
- Teams conversation et canal : empêcher le partage d’informations sensibles dans la conversation ou le canal
- Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures) : Auditer ou restreindre la copie d’un élément sensible sur un périphérique USB amovible
- Office Apps : affichez une fenêtre contextuelle indiquant à l’utilisateur qu’il s’engage dans un comportement risqué et bloque ou bloque, mais autorise le remplacement.
- Partages de fichiers locaux : déplacer le fichier de l’emplacement où il est stocké vers un dossier de quarantaine

> [!NOTE]
> Les conditions et les actions à entreprendre sont définies dans un objet appelé Règle.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft Purview center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Après avoir créé une stratégie DLP dans le Centre de conformité, elle est stockée dans un magasin de stratégies central, puis synchronisée avec les différentes sources de contenu, notamment :

- Depuis Exchange Online vers Outlook sur le web et Outlook.
- Sites OneDrive Entreprise.
- Sites SharePoint Online.
- Programmes de bureau Office (Excel, PowerPoint et Word).
- Canaux et messages de conversations Microsoft Teams.

Une fois la stratégie synchronisée avec les emplacements adéquats, elle commence à évaluer le contenu et à mettre en place des actions.

## <a name="viewing-policy-application-results"></a>Affichage des résultats de l’application de stratégie

DLP signale une grande quantité d’informations dans Microsoft Purview de la surveillance, des correspondances et des actions de stratégie, et des activités des utilisateurs. Vous devez utiliser et agir sur ces informations pour ajuster vos stratégies et trier les actions effectuées sur les éléments sensibles. La télémétrie passe d’abord dans les [journaux d’audit portail de conformité Microsoft Purview](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-portal), est traitée et fait son chemin vers différents outils de création de rapports. Chaque outil de création de rapports a un objectif différent.

### <a name="dlp-alerts-dashboard"></a>Tableau de bord des alertes DLP

Lorsque DLP effectue une action sur un élément sensible, vous pouvez être averti de cette action par le biais d’une alerte configurable. Au lieu de placer ces alertes dans une boîte aux lettres à parcourir, le Centre de conformité les rend disponibles dans le [tableau de bord de gestion des alertes DLP](dlp-configure-view-alerts-policies.md). Utilisez le tableau de bord Alertes DLP pour configurer les alertes, les examiner, les trier et suivre la résolution des alertes DLP. Voici un exemple d’alertes générées par des correspondances de stratégie et des activités provenant d’appareils Windows 10.

> [!div class="mx-imgBorder"]
> ![Information d’alerte.](../media/Alert-info-1.png)

Vous pouvez également afficher les détails de l’événement associé avec des métadonnées complètes dans le même tableau de bord

> [!div class="mx-imgBorder"]
> ![Informations sur un événement.](../media/Event-info-1.png)

### <a name="reports"></a>Rapports

Les [rapports DLP](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) montrent des tendances générales au fil du temps et fournissent des insights spécifiques sur :

- **La stratégie DLP correspond** au fil du temps et filtre par plage de dates, emplacement, stratégie ou action
- Les **correspondances d’incident DLP** affichent également des correspondances au fil du temps, mais elles pivotent sur les éléments plutôt que sur les règles de stratégie.
- **Les faux positifs et remplacements DLP** indiquent le nombre de faux positifs et, s’ils sont configurés, les remplacements utilisateur, ainsi que la justification de l’utilisateur.

### <a name="dlp-activity-explorer"></a>Explorateur d’activités DLP

L’onglet Explorateur d’activités de la page DLP contient le filtre *d’activité* prédéffré sur *DLPRuleMatch*. Utilisez cet outil pour passer en revue les activités liées au contenu qui contient des informations sensibles ou auxquels des étiquettes sont appliquées, telles que les étiquettes qui ont été modifiées, les fichiers modifiés et une règle correspondante.

![capture d’écran de l’explorateur d’activités délimitée DLPRuleMatch.](../media/dlp-activity-explorer.png)

Pour plus d’informations, consultez [Démarrage avec l’Explorateur d’activités](data-classification-activity-explorer.md)

Pour en savoir plus sur Microsoft Purview DLP, consultez :

- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préversion)](dlp-teams-default-policy.md)
- [En savoir plus sur le scanner local de prévention des pertes de données](dlp-on-premises-scanner-learn.md)
- [En savoir plus sur l’extension de la conformité Microsoft.](dlp-chrome-learn-about.md)
- [En savoir plus sur le tableau de bord des alertes de protection contre la perte de données](dlp-alerts-dashboard-learn.md)

Pour savoir comment utiliser la protection contre la perte de données pour se conformer aux réglementations de confidentialité des données, consultez [Déployer la protection des informations pour les réglementations de confidentialité des données avec Microsoft Purview](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

## <a name="licensing-and-subscriptions"></a>Licences et abonnements

Consultez les [exigences de licence pour Information Protection](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) pour plus d’informations sur les abonnements qui prennent en charge DLP.
