---
title: Solutions d’audit Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- m365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Découvrez comment auditer les activités des utilisateurs et administrateurs de votre organisation Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fbd00bdff46bebb73535f2b24c1b0bfa997dd55a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60163431"
---
# <a name="auditing-solutions-in-microsoft-365"></a>Audit de solutions dans Microsoft 365

Les solutions d'audit de Microsoft 365 fournissent une solution intégrée pour aider les organisations à répondre efficacement aux événements de sécurité, aux enquêtes d’audit, aux enquêtes internes et aux obligations de conformité. Des milliers d’opérations utilisateur et administrateur effectuées dans des dizaines de services et solutions Microsoft 365 sont capturées, enregistrées et conservées dans le journal d’audit unifié de votre organisation. Les enregistrements d'audit de ces événements peuvent être utilisables dans une recherchepar les responsables de la sécurité, les administrateurs informatiques, les équipes chargées de la lutte contre le risque interne et les enquêteurs chargés de la conformité et de la législation au sein de votre organisation. Cette fonctionnalité permet de gagner en visibilité sur les activités effectuées au sein de votre organisation Microsoft 365.

## <a name="microsoft-365-auditing-solutions"></a>Solutions d’audit Microsoft 365

Microsoft 365 propose deux solutions d’audit : l’audit de base et l’audit avancé.

![Principales fonctionnalités de l’audit de base et de l’audit avancé.](..\media\AuditingSolutionsComparison.png)

### <a name="basic-audit"></a>Audit de base

L’audit de base vous offre la possibilité de journaliser et de rechercher des activités auditées, et de mettre en place les enquêtes d’audit, informatiques, de conformité et juridiques.

- **Activé par défaut**. L’audit de base est désactivé par défaut pour toutes les organisations ayant l’abonnement approprié. Cela signifie que les enregistrements des activités auditées seront capturés et peuvent faire l’objet de recherches. La seule configuration requise consiste à attribuer les autorisations nécessaires pour accéder à l'outil de recherche des journaux d'audit (et à la cmdlet correspondante) et à s'assurer que les utilisateurs disposent de la bonne licence pour les fonctionnalités d'audit avancé.
- **Des milliers d’événements d’audit peuvent faire l’objet de recherches**. Vous pouvez rechercher un large éventail d'activités auditées qui se produisent dans la plupart des services Microsoft 365 au sein de votre organisation. Pour obtenir une liste partielle des activités que vous pouvez rechercher, consultez [Activités auditées](search-the-audit-log-in-security-and-compliance.md#audited-activities). Pour obtenir la liste des services et fonctionnalités qui prennent en charge les activités auditées, consultez[Type d’enregistrement du journal d’audit](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **Outil de recherche d’audit dans le Centre de conformité Microsoft 365**. Utilisez l’outil de recherche dans le journal d’audit dans le Centre de conformité Microsoft 365 pour rechercher des enregistrements d’audit. Vous pouvez rechercher des activités spécifiques, des activités effectuées par des utilisateurs spécifiques et des activités effectuées avec une plage de dates. Voici une capture d’écran de l’Outil de recherche d’audit dans le Centre de conformité.

   ![Outil de recherche dans le journal d’audit dans le Centre de conformité Microsoft 365.](../media/AuditLogSearchToolMCC.png)

- **Applet de commande Search-UnifiedAuditLog**. Vous pouvez également utiliser **l'applet de commande Search-UnifiedAuditLog** dans Exchange Online PowerShell (l'applet de commande sous-jacente de l'outil de recherche) pour rechercher des événements d'audit ou à utiliser dans un script. Pour plus d'informations, consultez :

  - [Référence de la cmdlet Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)
  - [Utiliser un script PowerShell pour effectuer une recherche dans le journal d’audit](audit-log-search-script.md)

- **Exporter des enregistrements d’audit dans un fichier CSV**. Après avoir exécuté l’outil de recherche dans le journal d’audit dans le Centre de conformité, vous pouvez exporter les enregistrements d’audit renvoyés par la recherche dans un fichier CSV. Vous pouvez ainsi trier et filtrer des fichiers Microsoft Excel sur différentes propriétés d’enregistrement d’audit. Vous pouvez également utiliser la fonctionnalité de transformation de Power Query d’Excel pour diviser chaque propriété de l’objet JSON AuditData dans sa propre colonne. Cela vous permet d’afficher et de comparer efficacement des données similaires pour différents événements. Pour plus d’informations, consultez [Exporter, configurer et afficher des enregistrements du journal d’audit](export-view-audit-log-records.md).

- **Accès aux journaux d’audit via l’API Activité de gestion d’Office 365**. Une troisième méthode pour accéder et récupérer des enregistrements d’audit consiste à utiliser l’API Activité de gestion d’Office 365. Cela permet aux organisations de conserver les données d’audit pendant des périodes plus longues que les 90 jours par défaut, et de les importer dans une solution SIEM. Pour plus d’informations, consultez [Référence de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

- **Rétention du journal d’audit de 90**. Lorsqu’une activité auditée est effectuée par un utilisateur ou un administrateur, un enregistrement d’audit est généré et stocké dans le journal d’audit pour votre organisation. Dans le cadre de l’audit de base, les enregistrements sont conservés pendant 90 jours, ce qui signifie que vous pouvez rechercher des activités qui se sont produites au cours des trois derniers mois.

### <a name="advanced-audit"></a>Audit avancé

L’Audit avancé s’appuie sur les fonctionnalités de l’audit de base en fournissant des stratégies de rétention du journal d’audit, une rétention plus longue des enregistrements d’audit, des événements essentiels à forte valeur ajoutée et un accès plus large à l’API Activité de gestion Office 365.

- **Stratégies de rétention du journal d'audit**. Vous pouvez créer des stratégies de rétention personnalisées pour conserver les enregistrements d’audit pendant une durée maximale d’un an (et jusqu’à 10 ans pour les utilisateurs titulaires d’une licence de module complémentaire requise). Vous pouvez créer une stratégie de rétention des enregistrements d’audit en fonction du service sur lequel se produisent les activités auditées, des activités d’audit spécifiques ou de l’utilisateur qui effectue une activité auditée.

- **Rétention plus longue des enregistrements d’audit**. Les enregistrements d'audit Exchange, SharePoint et Azure Active Directory sont conservés par défaut pendant un an. Par défaut, les enregistrements d’audit pour toutes les autres activités sont conservés pendant 90 jours. Vous pouvez utiliser des stratégies de rétention du journal d’audit pour configurer des périodes de rétention plus longues.

- **Événements d’audit avancé importants et essentiels**. Des enregistrements d’audit pour des événements essentiels peuvent aider votre organisation à mener des recherches de sécurité et de conformité en fournissant une visibilité à des événements tels que le moment où les éléments de courrier ont été accédés, ou les moments où des éléments de courrier ont été répondus et envoyés, ou quand et ce qu’un utilisateur a recherché dans Exchange Online et SharePoint Online. Ces événements importants peuvent vous aider à identifier les violations possibles et déterminer l’étendue de la compromission.

- **Bande passante supérieure à l’API Activité de gestion Office 365**. L’audit avancé offre aux organisations davantage de bande passante pour accéder aux journaux d’audit via l’API Activité de gestion Office 365. Si toutes les organisations (qui disposent d'un audit de base ou d'un audit avancé) se voient initialement attribuer une base de référence de 2 000 demandes par minute, cette limite augmentera de manière dynamique en fonction du nombre de sièges de l'organisation et de son abonnement aux licences. Ainsi, les organisations disposant d'un Audit avancé obtiennent environ deux fois plus de bande passante que les organisations disposant d'un audit de base.

Pour plus d’informations sur les fonctionnalités d’Audit avancé, consultez [Audit avancé dans Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>Comparaison des principales fonctionnalités

Le tableau suivant compare les principales fonctionnalités disponibles dans les fonctionnalités d’Audit de base et d’Audit avancé. Toutes les fonctionnalités d’Audit de base sont incluses dans Audit avancé.

|Fonctionnalité|Audit de base|Audit avancé|
|:------|:-------------|:-------------|
|Activé par défaut|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)|
|Des milliers d’événements d’audit peuvent faire l’objet de recherches.|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)|
|Outil de recherche d’audit dans le Centre de conformité Microsoft 365.|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)|
|Cmdlet Search-UnifiedAuditLog.|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)|
|Exporter des enregistrements d’audit dans un fichier CSV.|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)|
|Accès aux journaux d’audit via l’API Activité de gestion Office 365<sup>1</sup>.|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)</sup>|
|Rétention du journal d’audit de 90|![Pris en charge.](../media/check-mark.png)|![Pris en charge.](../media/check-mark.png)|
|Rétention du journal d’audit d’un an||![Pris en charge.](../media/check-mark.png)|
|Rétention du journal d’audit de 10 ans <sup>2</sup>||![Pris en charge](../media/check-mark.png)|
|Stratégies de rétention du journal d'audit||![Pris en charge](../media/check-mark.png)|
|Événements importants et essentiels.||![Pris en charge](../media/check-mark.png)|
||||
> [!NOTE]
> <sup>1</sup> Audit avancé inclut un accès plus large à l’API Activité de gestion Office 365, qui offre un accès plus rapide aux données d’audit.<br/><sup>2</sup> En plus des licences requises pour l’Audit avancé (décrites dans la section suivante), une licence rétention du journal d’audit de 10 ans doit être attribuée à un utilisateur pour conserver ses enregistrements d’audit pendant 10 ans.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Les sections suivantes identifient les licences requises pour l’Audit de base et l’Audit avancé. La fonctionnalité d’Audit de base est incluse dans la fonctionnalité Audit avancé.

### <a name="basic-audit"></a>Audit de base

- Abonnement Microsoft 365 Entreprise E3
- Microsoft 365 Business Premium
- Abonnement Microsoft 365 Éducation A3
- Abonnement Microsoft 365 pour le gouvernement américain G3
- Abonnement Microsoft 365 pour le gouvernement américain G1
- Abonnement Microsoft 365 Première ligne F1 ou F3 ou module complémentaire Sécurité F5
- Abonnement Office 365 Entreprise E3
- Abonnement Office 365 Entreprise E1
- Abonnement Office 365 Éducation A1
- Abonnement Office 365 Éducation A3

### <a name="advanced-audit"></a>Audit avancé

- Abonnement Microsoft 365 Entreprise E5
- Abonnement Microsoft 365 Entreprise E3 + module complémentaire Microsoft 365 E5 Conformité
- Abonnement Microsoft 365 Entreprise E3 + module complémentaire Microsoft 365 E5 eDiscovery et Audit
- Abonnement Microsoft 365 Éducation A5
- Abonnement Microsoft 365 Éducation A3 + module complémentaire Microsoft 365 A5 Conformité
- Abonnement Microsoft 365 Éducation A3 + module complémentaire Microsoft 365 A5 eDiscovery et Audit
- Microsoft 365 pour le gouvernement américain G5
- Abonnement Microsoft 365 pour le gouvernement américain G5 + module complémentaire Microsoft 365 G5 Conformité
- Abonnement Microsoft 365 pour le gouvernement américain G5 + module complémentaire Microsoft 365 G5 eDiscovery et Audit
- Microsoft 365 Première ligne F5 Conformité ou F5 Sécurité et module complémentaire Conformité
- Abonnement Office 365 Entreprise E5
- Abonnement Office 365 Éducation A5
- Abonnement Office 365 Entreprise E3 + module complémentaire de Conformité avancée Office 365 (désormais indisponible pour les nouveaux abonnements)

## <a name="set-up-microsoft-365-auditing-solutions"></a>Configurer des solutions d’audit Microsoft 365

Pour commencer à utiliser les solutions d’audit dans Microsoft 365, consultez les instructions de configuration suivantes.

### <a name="set-up-basic-audit"></a>Configurer l’Audit de base

La première étape consiste à configurer l’audit de base, puis à lancer des recherches dans le journal d’audit.

![Flux de travail pour configurer l’Audit avancé.](../media/BasicAuditingWorkflow.png)

1. Vérifiez que votre organisation dispose d’un abonnement qui prend en charge l’Audit de base et, le cas échéant, un abonnement qui prend en charge l’Audit avancé.

2. Attribuez des autorisations dans Exchange Online aux personnes de votre organisation qui utiliseront l’outil de recherche dans le journal d’audit dans le Centre de conformité Microsoft 365 ou utilisez la cmdlet **Search-UnifiedAuditLog**. Plus précisément, les utilisateurs doivent avoir le rôle Journaux d’audit en affichage seul ou Journaux d’audit dans Exchange Online.

3. Effectuer une recherche dans le journal d’audit. À l’issue des étapes 1 et 2, les utilisateurs de votre organisation peuvent utiliser l’outil de recherche dans le journal d’audit (ou cmdlet correspondante) pour rechercher des activités auditées.

Pour obtenir des instructions plus détaillées, voir [Configurer l’audit de base](set-up-basic-audit.md).

### <a name="set-up-advanced-audit"></a>Configurer l’audit avancé

Si votre organisation a un abonnement qui prend en charge l’Audit avancé, suivez les étapes pour configurer et utiliser les fonctionnalités supplémentaires d’Audit avancé.

![Flux de travail pour configurer l’Audit avancé.](../media/AdvancedAuditWorkflow.png)

1. Configurer l’audit avancé pour les utilisateurs. Cette étape comprend les tâches suivantes :

   - Vérification de l’utilisation de la licence ou de la licence de module approprié pour l’Audit avancé.
  
   - L'activation de l'application/du plan de service d'audit avancé doit concerner ces utilisateurs.
  
   - L'activation de l'audit des événements essentiels, puis l'activation de l'application/du plan de service d'audit avancé pour ces utilisateurs.

2. Permettre que des événements d’audit avancé soient journalisés lorsque les utilisateurs effectuent des recherches dans Exchange Online et SharePoint Online.

3. Configurer des stratégies de rétention du journal d'audit. En plus de la stratégie par défaut qui conserve les enregistrements d’audit Exchange, SharePoint et Azure AD pendant un an, vous pouvez créer des stratégies de rétention supplémentaires pour le journal d’audit afin de répondre aux exigences des équipes de sécurité, informatique et de conformité de votre organisation.

4. Recherchez des événements d’audit avancé essentiels et d’autres activités lors d’enquêtes. À l’issue des étapes 1 et 2, vous pouvez rechercher des événements d’audit avancé et d’autres activités dans le journal d’audit lors d’enquêtes approfondies sur des comptes compromis et d’autres types d’enquêtes de sécurité ou de conformité.

Pour obtenir des instructions plus détaillées, voir [Configurer l’audit avancé](set-up-advanced-audit.md).

## <a name="training"></a>Formation

La formation de l'équipe en charge des opérations de sécurité, des administrateurs informatiques et des enquêteurs de conformité aux principes fondamentaux de l'audit de base et de l'audit avancé peut aider votre organisation à utiliser plus rapidement l'audit dans le cadre de ses enquêtes. Microsoft 365 fournit la ressource suivante pour aider ces utilisateurs de votre organisation à démarrer l’audit: [Décrire les fonctionnalités eDiscovery et d’audit de Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
