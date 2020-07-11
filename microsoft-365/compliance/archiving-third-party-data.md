---
title: Archiver des données tierces
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment importer des données tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents vers des boîtes aux lettres Microsoft 365.
ms.openlocfilehash: a8dc69e7e4c7061e048fe49d1e51fd8867654454
ms.sourcegitcommit: a5ed189fa789975f8c3ed39db1d52f2ef7d671aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "45101635"
---
# <a name="archive-third-party-data"></a>Archiver des données tierces

Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents, à des boîtes aux lettres de votre organisation Microsoft 365. L’un des principaux avantages de l’utilisation des connecteurs de données pour importer et archiver des données tierces dans Microsoft 365 est que vous pouvez appliquer diverses solutions de conformité Microsoft 365 après avoir été importées. Cela vous permet de vous assurer que les données non Microsoft de votre organisation sont conformes aux réglementations qui affectent votre organisation.

## <a name="third-party-data-connectors"></a>Connecteurs de données tiers

Le tableau suivant répertorie les connecteurs de données tiers disponibles dans le centre de conformité Microsoft 365. Le tableau résume également les solutions de conformité que vous pouvez appliquer à des données tierces après l’importation et l’archivage dans Microsoft 365. Reportez-vous à la [section suivante](#overview-of-compliance-solutions-that-support-third-party-data) pour une description plus détaillée de chaque solution de conformité et sur la façon dont elle peut tirer parti des données tierces.

> [!TIP]
> Cliquez sur le lien dans la colonne de **données tierces** pour suivre les instructions pas à pas pour la création d’un connecteur pour ce type de données.

|Données tierces  |Conservation pour litige|eDiscovery  |Stratégies de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Message Bloomberg](archive-bloomberg-message-data.md)     |![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|||
|[Données RH](import-hr-data.md) ||||||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|[Conversation ICE](archive-icechat-data.md)     |![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|||
||||||||

Les données tierces indiquées dans le tableau précédent (à l’exception des données RH) sont importées dans des boîtes aux lettres utilisateur. Les solutions de conformité correspondantes qui prennent en charge les données tierces sont appliquées à la boîte aux lettres de l’utilisateur où les données sont stockées.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Vue d’ensemble des solutions de conformité qui prennent en charge les données tierces

Les sections suivantes décrivent certaines des choses que les solutions de conformité Microsoft 365 peuvent vous aider à gérer les données tierces indiquées dans le tableau précédent.

### <a name="litigation-hold"></a>Conservation pour litige

Vous placez une [conservation pour litige](create-a-litigation-hold.md) dans une boîte aux lettres utilisateur pour conserver des données tierces. Lorsque vous créez une suspension, vous pouvez spécifier une durée de conservation (également appelée *conservation basée sur l’heure*) de façon à ce que les données supprimées et modifiées tierces soient conservées pendant une période spécifiée, puis supprimées définitivement de la boîte aux lettres. Vous pouvez également conserver indéfiniment le contenu (appelé *conservation infinie*) ou jusqu’à ce que la conservation pour litige ne soit supprimée.

### <a name="ediscovery"></a>eDiscovery

Les trois principaux outils eDiscovery de Microsoft 365 sont la recherche de contenu, la découverte électronique de base et la découverte électronique avancée.

- **[Recherche de contenu](content-search.md).** Vous pouvez utiliser l’outil de recherche de contenu pour rechercher des boîtes aux lettres de données tierces que vous avez importées. Vous pouvez utiliser des requêtes et des conditions de recherche pour affiner les résultats de la recherche et exporter les résultats de la recherche.

- **[Base eDiscovery](get-started-core-ediscovery.md).** Cet outil repose sur la fonctionnalité de recherche et d’exportation de base en vous permettant de créer des cas qui vous permettent de contrôler qui peut accéder aux données de cas, de placer une conservation sur les boîtes aux lettres des utilisateurs ou le contenu de boîte aux lettres qui correspond aux critères de recherche. Cela signifie que vous pouvez placer une conservation eDiscovery sur les données tierces qui ont été importées dans des boîtes aux lettres utilisateur.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** Cet outil puissant étend la fonctionnalité de cas de découverte électronique de base en vous permettant d’ajouter des dépositaires à un cas, de placer les données du dépositaire, puis de charger les données tierces d’un dépositaire dans un examen pour une analyse plus poussée, comme les thèmes et la détection des doublons. Une fois que vous avez chargé des données tierces dans un jeu de vérification, vous pouvez les interroger et les filtrer sur un jeu de résultats étroit.

   La découverte électronique de base et la découverte électronique avancée vous permettent de gérer des données tierces susceptibles de s’intéresser aux investigations internes ou juridiques de votre organisation.

### <a name="retention-policies"></a>Stratégies de rétention

Vous pouvez appliquer une [stratégie de rétention](retention-policies.md) aux boîtes aux lettres utilisateur pour conserver, puis supprimer les données tierces (et tout autre contenu de boîte aux lettres) après l’expiration de la période de rétention. Vous pouvez également utiliser des stratégies de rétention pour supprimer des données tierces d’un certain âge ou déclencher un examen de destruction à l’expiration de la période de rétention.

### <a name="records-management"></a>Gestion des enregistrements

La fonctionnalité de [gestion des enregistrements](records-management.md) de Microsoft 365 vous permet de déclarer des données tierces sous la forme d’un enregistrement. Cela peut être réalisé manuellement par les utilisateurs qui appliquent une étiquette de rétention qui marque les données tierces de leur boîte aux lettres comme étant des enregistrements. Ou vous pouvez appliquer automatiquement des étiquettes de rétention en identifiant des informations sensibles, des mots clés ou des types de contenu dans des données tierces.

### <a name="communication-compliance"></a>Conformité des communications

Vous pouvez utiliser [la conformité des communications](communication-compliance.md) pour examiner les données tierces afin de vous assurer qu’elles sont conformes aux normes de données de votre organisation. Pour ce faire, vous pouvez détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. Par exemple, vous pouvez surveiller les données tierces que vous importez pour une langue choquante, des informations sensibles et une conformité réglementaire.

### <a name="insider-risk-management"></a>Gestion des risques internes

Les signaux provenant de données tierces, telles que les données RH sélectives, peuvent être utilisés par la solution de [gestion des risques Insider](insider-risk-management.md) pour réduire les risques internes en vous permettant de détecter, d’examiner et de traiter les activités à risque au sein de votre organisation. Par exemple, les données importées par le connecteur de données RH sont utilisées comme indicateurs de risque pour détecter les vols de données des employés.

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Utilisation d’un partenaire Microsoft pour archiver des données tierces

Une autre option pour l’importation et l’archivage de données tierces permet à votre organisation de collaborer avec un partenaire Microsoft. Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le centre de conformité Microsoft, vous pouvez collaborer avec un partenaire qui peut fournir un connecteur personnalisé qui sera configuré pour extraire régulièrement des éléments de la source de données tierce, puis se connecter à Microsoft Cloud par une API tierce et importer ces éléments dans Microsoft 365. Le connecteur partenaire convertit également le contenu d’un élément de la source de données tierce en message électronique, puis l’importe dans une boîte aux lettres dans Microsoft 365.

Pour obtenir la liste des partenaires avec lesquels vous pouvez travailler et le processus pas à pas pour cette méthode, consultez [collaborer avec un partenaire pour archiver des données tierces dans Microsoft 365](work-with-partner-to-archive-third-party-data.md).
