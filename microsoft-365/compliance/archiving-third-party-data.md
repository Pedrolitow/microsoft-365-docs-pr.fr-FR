---
title: Archiver des données tierces
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365solution-mig
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment importer des données tierces à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents dans Microsoft 365 boîtes aux lettres.
ms.openlocfilehash: 17172daa60721523bbfb97ab81f7a57078eb1b1c
ms.sourcegitcommit: 50908a93554290ff1157b58d0a868a33e012513c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52822152"
---
# <a name="archive-third-party-data"></a>Archiver des données tierces

Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données tierces à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents, vers des boîtes aux lettres de votre organisation Microsoft 365. L’un des principaux avantages de l’utilisation de connecteurs de données pour importer et archiver des données tierces dans Microsoft 365 est que vous pouvez y appliquer diverses solutions de conformité Microsoft 365 après leur importation. Cela vous permet de vous assurer que les données non Microsoft de votre organisation sont conformes aux réglementations et normes qui affectent votre organisation.

## <a name="third-party-data-connectors"></a>Connecteurs de données tiers

Le tableau suivant répertorie les connecteurs de données tiers disponibles dans le centre Microsoft 365 conformité. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après l’importation et l’archivage dans Microsoft 365. Consultez [la section suivante](#overview-of-compliance-solutions-that-support-third-party-data) pour obtenir une description plus détaillée de chaque solution de conformité et pour savoir comment elle peut bénéficier de données tierces.

> [!TIP]
> Cliquez sur le lien dans **la** colonne de données tierces pour suivre les instructions pas à pas pour créer un connecteur pour ce type de données.

|Données tierces  |Attente pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android <sup>1</sup>](archive-android-archiver-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[AT&T Network <sup>1</sup>](archive-att-network-archiver-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau Bell <sup>1</sup>](archive-bell-network-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Message Bloomberg](archive-bloomberg-message-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[CellTrust <sup>2</sup>](archive-celltrust-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber sur MS SQL <sup>2</sup>](archive-ciscojabberonmssql-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber sur Oracle <sup>2</sup>](archive-ciscojabberonoracle-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber sur PostgreSQL <sup>2</sup>](archive-ciscojabberonpostgresql-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[EML <sup>2</sup>](archive-eml-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Enterprise Numéro <sup>1</sup>](archive-enterprise-number-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[FX Connecter <sup>2</sup>](archive-fxconnect-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Ressources humaines (RH)](import-hr-data.md) ||||||![Coche](../media/checkmark.png)
|[Conversation ICE](archive-icechat-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Jive <sup>2</sup>](archive-jive-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[MS SQL Database <sup>2</sup>](archive-mssqldatabaseimporter-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[O2 Network <sup>1</sup>](archive-o2-network-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Badging physique](import-physical-badging-data.md) ||||||![Coche](../media/checkmark.png)|
|[Pivot <sup>2</sup>](archive-pivot-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Redtail Speak <sup>2</sup>](archive-redtailspeak-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Reuters Dealing <sup>2</sup>](archive-reutersdealing-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Reuters Eikon <sup>2</sup>](archive-reuterseikon-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Reuters FX <sup>2</sup>](archive-reutersfx-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[SalesforceForceForce <sup>2</sup>](archive-salesforcechatter-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[ServiceNow <sup>2</sup>](archive-servicenow-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Slack eDiscovery <sup>2</sup>](archive-slack-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Édition <sup>2</sup>](archive-symphony-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[RÉSEAU DE DISTRIBUTION <sup>1</sup>](archive-telus-network-data.md)    |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Délimité par du texte <sup>2</sup>](archive-text-delimited-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Verizon Network <sup>1</sup>](archive-verizon-network-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Webex Teams <sup>2</sup>](archive-webexteams-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Pages Web <sup>2</sup>](archive-webpagecapture-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[WhatsApp <sup>1</sup>](archive-whatsapp-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Espace de travail à partir de Facebook <sup>2</sup>](archive-workplacefromfacebook-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[XIP <sup>2</sup>](archive-xip-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[XSLT/XML <sup>2</sup>](archive-xslt-xml-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Yieldbroker <sup>2</sup>](archive-yieldbroker-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Zoomer les réunions <sup>2</sup>](archive-zoommeetings-data.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

> [!NOTE]
> <sup>1 Connecteur</sup> de données fourni par TeleMessage. Avant de pouvoir archiver des données dans Microsoft 365, vous devez utiliser TeleMessage pour configurer son service d’archivage pour votre organisation. Pour plus d’informations, consultez la section des conditions préalables dans les instructions pas à pas pour ce type de données. Les connecteurs de données TeleMessage sont également disponibles dans Cloud de la communauté du secteur public environnements dans Microsoft 365 cloud du gouvernement américain. Pour plus d’informations, voir les connecteurs de données dans la section cloud du gouvernement des [États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article. <br/><br/><sup>2 Connecteur</sup> de données fourni par Veritas. Avant de pouvoir archiver des données dans Microsoft 365, vous devez travailler avec Veritas pour configurer leur service d’archivage pour votre organisation. Pour plus d’informations, consultez la section des conditions préalables dans les instructions pas à pas pour ce type de données.

Les données tierces répertoriées dans le tableau précédent (à l’exception des données RH et des données de mauvaise gestion physique) sont importées dans les boîtes aux lettres des utilisateurs. Les solutions de conformité correspondantes qui permettent de prendre en charge des données tierces sont appliquées à la boîte aux lettres de l’utilisateur dans laquelle les données sont stockées.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Vue d’ensemble des solutions de conformité qui permettent la prise en charge des données tierces

Les sections suivantes décrivent certains des éléments que les solutions de conformité Microsoft 365 peuvent vous aider à gérer les données tierces répertoriées dans le tableau précédent.

### <a name="litigation-hold"></a>Attente pour litige

Vous placez une boîte [aux lettres d’utilisateur](create-a-litigation-hold.md) en attente pour litige pour conserver des données tierces. Lorsque vous créez une attente, vous pouvez spécifier une durée de la rétention (également appelée « attente basée sur le temps *)* afin que les données tierces supprimées et modifiées sont conservées pendant une période spécifiée, puis supprimées définitivement de la boîte aux lettres. Vous pouvez également conserver le contenu indéfiniment (appelé « attente infinie *»* ou jusqu’à ce que la attente pour litige soit supprimée.

### <a name="ediscovery"></a>eDiscovery

Les trois principaux outils eDiscovery dans Microsoft 365 sont la recherche de contenu, core eDiscovery et Advanced eDiscovery.

- **[Recherche de contenu](content-search.md).** Vous pouvez utiliser l’outil de recherche de contenu pour rechercher des données tierces importées dans les boîtes aux lettres. Vous pouvez utiliser des requêtes et des conditions de recherche pour affiner vos résultats de recherche et exporter les résultats de la recherche.

- **[Core eDiscovery](get-started-core-ediscovery.md).** Cet outil s’appuie sur les fonctionnalités de recherche et d’exportation de base en vous permettant de créer des cas qui vous permettent de contrôler qui peut accéder aux données de cas, de placer en attente des boîtes aux lettres utilisateur ou du contenu de boîte aux lettres qui correspond aux critères de recherche. Cela signifie que vous pouvez placer une boîte aux lettres eDiscovery en attente sur les données tierces qui ont été importées dans les boîtes aux lettres des utilisateurs.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** Cet outil puissant développe les fonctionnalités de cas de core eDiscovery en vous permettant d’ajouter des dépositaires à un cas, de placer les données du dépositaire en conservation, puis de charger les données tierces d’un dépositaire dans un examen pour une analyse plus approfondie, telle que les thèmes et la détection des doublons. Après avoir chargé des données tierces dans un jeu à réviser, vous pouvez les interroger et les filtrer dans un jeu de résultats étroit.

   Core eDiscovery et Advanced eDiscovery vous permet de gérer des données tierces qui peuvent être pertinentes pour les enquêtes juridiques ou internes de votre organisation.

### <a name="retention-settings"></a>Paramètres de rétention

Vous pouvez [](retention.md) appliquer une stratégie de rétention aux boîtes aux lettres des utilisateurs pour conserver, puis supprimer des données tierces (et d’autres contenus de boîte aux lettres) après l’expiration de la période de rétention. Vous pouvez également utiliser des stratégies de rétention pour supprimer des données tierces d’un certain âge ou utiliser des étiquettes de rétention pour déclencher une révision de [suppression](disposition.md) à l’expiration de la période de rétention des données tierces.

### <a name="records-management"></a>Gestion des enregistrements

La [fonctionnalité de gestion](records-management.md) des enregistrements Microsoft 365 vous permet de déclarer des données tierces en tant qu’enregistrement. Cela peut être effectué manuellement par les utilisateurs qui appliquent une étiquette de rétention qui marque des données tierces dans leur boîte aux lettres comme enregistrement. Vous pouvez également appliquer automatiquement des étiquettes de rétention en identifiant des informations sensibles, des mots clés ou des types de contenu dans des données tierces.

### <a name="communication-compliance"></a>Conformité des communications

Vous pouvez utiliser [la conformité des communications](communication-compliance.md) pour examiner des données tierces afin de vous assurer qu’elles sont conformes aux normes de données de votre organisation. Pour ce faire, vous pouvez détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. Par exemple, vous pouvez surveiller les données tierces que vous importez pour le langage choquant, les informations sensibles et la conformité réglementaire.

### <a name="insider-risk-management"></a>Gestion des risques internes

Les signaux provenant de données tierces, tels que les données RH sélectives, peuvent être utilisés par la [solution](insider-risk-management.md) de gestion des risques internes pour minimiser les risques internes en vous permettant de détecter, d’examiner et d’agir sur les activités à risque dans votre organisation. Par exemple, les données importées par le connecteur de données RH sont utilisées comme indicateurs de risque pour vous aider à détecter le vol de données de l’employé qui quitte l’entreprise.

## <a name="data-connectors-in-the-us-government-cloud"></a>Connecteurs de données dans le cloud du gouvernement des États-Unis

Comme mentionné précédemment, les connecteurs de données fournis par TeleMessage sont disponibles dans le cloud du gouvernement des États-Unis. Le tableau suivant indique les environnements spécifiques au secteur public qui supportent chaque connecteur de données TeleMessage. Pour plus d’informations sur les clouds pour le gouvernement des États-Unis, [voir Microsoft 365 gouvernement américain.](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy)

|Connecteur de données TeleMessage  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|Archiveur Android | Oui | Non | Non |
|AT&T SMS/MMS Network Archiver | Oui | Non | Non |
|Archiveur réseau SMS/MMS | Oui | Non | Non |
|Enterprise Archiveur de nombres | Oui | Non | Non |
|Archiveur SMS réseau vocal et O2 | Oui         | Non | Non |
|ARCHIVEur réseau DE DISTRIBUTION SMS | Oui | Non | Non |
|Verizon SMS/MMS Network Archiver | Oui | Non | Non |
|Archiveur WhatsApp | Oui | Non | Non |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Collaborer avec un partenaire Microsoft pour archiver des données tierces

Pour importer et archiver des données tierces, votre organisation peut également travailler avec un partenaire Microsoft. Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le Centre de conformité Microsoft, vous pouvez travailler avec un partenaire qui peut fournir un connecteur personnalisé qui sera configuré pour extraire régulièrement des éléments de la source de données tierces, puis vous connecter au cloud Microsoft par une API tierce et importer ces éléments dans Microsoft 365. Le connecteur partenaire convertit également le contenu d’un élément de la source de données tierce en message électronique, puis l’importe dans une boîte aux lettres dans Microsoft 365.

Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, voir Travailler avec un partenaire pour archiver des données tierces [dans Microsoft 365](work-with-partner-to-archive-third-party-data.md).
