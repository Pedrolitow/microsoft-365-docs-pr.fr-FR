---
title: Utiliser des connecteurs de données pour importer et archiver des données tierces dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment importer et archiver des données tierces à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents pour Microsoft 365 boîtes aux lettres.
ms.openlocfilehash: 06833acd3ea29e30d8789fbb05e0a081309c7f2b
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2022
ms.locfileid: "62055015"
---
# <a name="learn-about-connectors-for-third-party-data"></a>En savoir plus sur les connecteurs pour les données tierces

Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données tierces non Microsoft à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents, vers des boîtes aux lettres de votre organisation Microsoft 365. L’un des principaux avantages de l’utilisation de connecteurs de données pour importer et archiver des données tierces dans Microsoft 365 est que vous pouvez appliquer différentes solutions de conformité Microsoft 365 aux données après leur importation. Cela vous permet de vous assurer que les données non Microsoft de votre organisation sont conformes aux réglementations et normes qui affectent votre organisation.

Regardez ce guide interactif qui montre comment créer des connecteurs de données pour importer et archiver des données tierces et des exemples d’application de solutions de conformité aux données après leur importation dans Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Connecteurs de données tiers

Le Centre de conformité Microsoft 365 fournit des connecteurs de données tiers natifs de Microsoft pour importer des données à partir de différentes sources de données, telles que LinkedIn, Instant Bloomberg et Twitter, ainsi que des connecteurs de données qui assurent la prise en charge de la solution de gestion des risques internes. En plus de ces connecteurs de données, Microsoft collabore avec les partenaires suivants pour fournir de nombreux autres connecteurs de données tiers dans le Centre de conformité Microsoft 365. Votre organisation collabore avec ces partenaires pour configurer leur service d’archivage avant de créer un connecteur de données correspondant dans le Centre de conformité Microsoft 365.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

Les données tierces répertoriées dans les sections suivantes (à l’exception des données RH et des données de mauvaise gestion physiques utilisées pour la solution de gestion des risques internes Microsoft 365) sont importées dans les boîtes aux lettres des utilisateurs. Les Microsoft 365 de conformité qui permettent de prendre en charge des données tierces sont appliquées à la boîte aux lettres de l’utilisateur dans laquelle les données sont stockées.

### <a name="microsoft-data-connectors"></a>Connecteurs de données Microsoft

Le tableau suivant répertorie les connecteurs de données tiers natifs disponibles dans le Centre de conformité Microsoft 365. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer après avoir importé et archivé des données tierces dans Microsoft 365. Consultez la section Vue d’ensemble des [solutions](#overview-of-compliance-solutions-that-support-third-party-data) de conformité qui prend en charge les données tierces pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Cliquez sur le lien dans **la** colonne de données tierces pour suivre les instructions pas à pas pour créer un connecteur pour ce type de données.

|Données tierces  |Attente pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Message Bloomberg](archive-bloomberg-message-data.md)     |![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)||
|[Ehr santé](import-epic-data.md) ||||||![Coche](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Coche.](../media/checkmark.png)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Soins de santé EHR génériques](import-healthcare-data.md) ||||||![Coche](../media/checkmark.png)|
|[Ressources humaines (RH)](import-hr-data.md) ||||||![Coche](../media/checkmark.png)|
|[Conversation ICE](archive-icechat-data.md)     |![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Badging physique](import-physical-badging-data.md) ||||||![Coche](../media/checkmark.png)|
|[Découverte électronique de marge](archive-slack-data-microsoft.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Connecteurs de données Veritas

Le tableau de cette section répertorie les connecteurs de données tiers disponibles en partenariat avec Veritas. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la section Vue d’ensemble des [solutions](#overview-of-compliance-solutions-that-support-third-party-data) de conformité qui prend en charge les données tierces pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez utiliser Veritas pour configurer son service d’archivage (appelé *Merge1)* pour votre organisation. Pour plus d’informations,  cliquez sur le lien dans la colonne de données tierces pour suivre les instructions détaillées de création d’un connecteur pour ce type de données.

|Données tierces  |Attente pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber sur MS SQL](archive-ciscojabberonmssql-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber sur Oracle](archive-ciscojabberonoracle-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber sur PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[FX Connect](archive-fxconnect-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Coche.](../media/checkmark.png)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Base de données MS SQL](archive-mssqldatabaseimporter-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Tableau croisé dynamique](archive-pivot-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Gestion de Reuters](archive-reutersdealing-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Salesforce Chatter](archive-salesforcechatter-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Skype Entreprise](archive-skypeforbusiness-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Découverte électronique de marge](archive-slack-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Symphony](archive-symphony-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Délimité par le texte](archive-text-delimited-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Pages web](archive-webpagecapture-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Espace de travail sur Facebook](archive-workplacefromfacebook-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Réunions Zoom](archive-zoommeetings-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>Connecteurs de données de TeleMessage

Le tableau de cette section répertorie les connecteurs de données tiers disponibles en partenariat avec TeleMessage. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la section Vue d’ensemble des [solutions](#overview-of-compliance-solutions-that-support-third-party-data) de conformité qui prend en charge les données tierces pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez utiliser TeleMessage pour configurer son service d’archivage pour votre organisation. Pour plus d’informations,  cliquez sur le lien dans la colonne de données tierces pour suivre les instructions détaillées de création d’un connecteur pour ce type de données.

Les connecteurs de données TeleMessage sont également disponibles dans Cloud de la communauté du secteur public environnements dans Microsoft 365 cloud du gouvernement américain. Pour plus d’informations, voir les connecteurs de données dans la section cloud du gouvernement des [États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article.

|Données tierces  |Attente pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[AT&T Network](archive-att-network-archiver-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau Bell](archive-bell-network-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Numéro d'entreprise](archive-enterprise-number-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau O2](archive-o2-network-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau DeNte](archive-rogers-network-archiver-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Signal](archive-signal-archiver-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Pays-De-La](archive-telegram-archiver-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau TELUS](archive-telus-network-data.md)    |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau Verizon](archive-verizon-network-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[WhatsApp](archive-whatsapp-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>Connecteurs de données 17a-4

Le tableau de cette section répertorie les connecteurs de données tiers disponibles en partenariat avec 17a-4 LLC. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la section Vue d’ensemble des [solutions](#overview-of-compliance-solutions-that-support-third-party-data) de conformité qui prend en charge les données tierces pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez utiliser 17a-4 LLC pour configurer son service d’archivage (appelé *DataParser)* pour votre organisation. Pour plus d’informations,  cliquez sur le lien dans la colonne de données tierces pour suivre les instructions détaillées de création d’un connecteur pour ce type de données.

Les connecteurs de données 17a-4 sont également disponibles dans les environnements Cloud de la communauté du secteur public dans le cloud Microsoft 365 gouvernement américain. Pour plus d’informations, voir les connecteurs de données dans la section cloud du gouvernement des [États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article.

|Données tierces  |Attente pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[BlackBerry](archive-17a-4-blackberry-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[FX Connect](archive-17a-4-fxconnect-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Conversation ICE](archive-17a-4-ice-im-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[LivePerson Conversational Cloud](archive-17a-4-liveperson-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
[Skype Entreprise Server](archive-17a-4-skype-for-business-server-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Slack](archive-17a-4-slack-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Symphony](archive-17a-4-symphony-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Zoom](archive-17a-4-zoom-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>Connecteurs de données CellTrust

Le tableau de cette section répertorie le connecteur de données tiers disponible en partenariat avec CellTrust. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer aux données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la section Vue d’ensemble des [solutions](#overview-of-compliance-solutions-that-support-third-party-data) de conformité qui prend en charge les données tierces pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez utiliser CellTrust pour configurer son service d’archivage (appelé *CellTrust SL2)* pour votre organisation. Pour plus d’informations,  cliquez sur le lien dans la colonne de données tierces pour suivre les instructions détaillées de création d’un connecteur CellTrust SL2.

|Données tierces  |Attente pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

Le connecteur de données CellTrust SL2 est également disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 gouvernement américain. Pour plus d’informations, voir les connecteurs de données dans la section cloud du gouvernement des [États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Vue d’ensemble des solutions de conformité qui permettent la prise en charge des données tierces

Les sections suivantes décrivent certains des éléments que les solutions de conformité Microsoft 365 peuvent vous aider à gérer les données tierces répertoriées dans le tableau précédent.

### <a name="litigation-hold"></a>Attente pour litige

Vous placez une boîte [aux lettres d’utilisateur](create-a-litigation-hold.md) en attente pour litige pour conserver des données tierces. Lorsque vous créez une attente, vous pouvez spécifier une durée de la rétention (également appelée « attente basée sur le temps *)* afin que les données tierces supprimées et modifiées sont conservées pendant une période spécifiée, puis supprimées définitivement de la boîte aux lettres. Sinon, vous pouvez simplement conserver le contenu indéfiniment (appelé une attente *infinie)* ou jusqu’à ce que la attente pour litige soit supprimée.

### <a name="ediscovery"></a>eDiscovery

Les trois principaux outils eDiscovery Microsoft 365 sont la recherche de contenu, core eDiscovery et Advanced eDiscovery.

- **[Recherche de contenu](content-search.md).** Vous pouvez utiliser l’outil de recherche de contenu pour rechercher des données tierces importées dans les boîtes aux lettres. Vous pouvez utiliser des requêtes et des conditions de recherche pour affiner vos résultats de recherche et exporter les résultats de la recherche.

- **[Core eDiscovery](get-started-core-ediscovery.md).** Cet outil s’appuie sur les fonctionnalités de recherche et d’exportation de base en vous permettant de créer des cas qui vous permettent de contrôler qui peut accéder aux données de cas, de placer en attente des boîtes aux lettres utilisateur ou du contenu de boîte aux lettres qui correspond aux critères de recherche. Cela signifie que vous pouvez placer une boîte aux lettres eDiscovery en attente sur les données tierces qui ont été importées dans les boîtes aux lettres des utilisateurs.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** Cet outil puissant développe les fonctionnalités de cas de core eDiscovery en vous permettant d’ajouter des dépositaires à un cas, de placer les données du dépositaire en conservation, puis de charger les données tierces d’un dépositaire dans un examen pour une analyse plus approfondie, telle que les thèmes et la détection des doublons. Après avoir chargé des données tierces dans un jeu à réviser, vous pouvez les interroger et les filtrer dans un jeu de résultats étroit.

   Core eDiscovery et Advanced eDiscovery vous permet de gérer des données tierces qui peuvent être pertinentes pour les enquêtes juridiques ou internes de votre organisation.

### <a name="retention-settings"></a>Paramètres de rétention

Vous pouvez [](retention.md) appliquer une stratégie de rétention aux boîtes aux lettres des utilisateurs pour conserver, puis supprimer des données tierces (et d’autres contenus de boîte aux lettres) après l’expiration de la période de rétention. Vous pouvez également utiliser des stratégies de rétention pour supprimer des données tierces d’un certain âge ou utiliser des étiquettes de rétention pour déclencher une révision de [suppression](disposition.md) à l’expiration de la période de rétention des données tierces.

### <a name="records-management"></a>Gestion des enregistrements

La [fonctionnalité de gestion](records-management.md) des enregistrements Microsoft 365 vous permet de déclarer des données tierces en tant qu’enregistrement. Cette procédure peut être effectuée manuellement par les utilisateurs qui appliquent une étiquette de rétention qui marque des données tierces dans leur boîte aux lettres en tant qu’enregistrement. Vous pouvez également appliquer automatiquement des étiquettes de rétention en identifiant des informations sensibles, des mots clés ou des types de contenu dans des données tierces.

### <a name="communication-compliance"></a>Conformité des communications

Vous pouvez utiliser [la conformité des communications](communication-compliance.md) pour examiner des données tierces afin de vous assurer qu’elles sont conformes aux normes de données de votre organisation. Pour ce faire, vous pouvez détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. Par exemple, vous pouvez surveiller les données tierces que vous importez pour le langage choquant, les informations sensibles et la conformité réglementaire.

### <a name="insider-risk-management"></a>Gestion des risques internes

Les signaux provenant de données tierces, tels que les données RH sélectives, peuvent être utilisés par la [solution](insider-risk-management.md) de gestion des risques internes pour minimiser les risques internes en vous permettant de détecter, d’examiner et d’agir sur les activités à risque dans votre organisation. Par exemple, les données importées par le connecteur de données RH sont utilisées comme indicateurs de risque pour vous aider à détecter le vol de données de l’employé qui quitte l’entreprise.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Utilisation des outils eDiscovery pour rechercher des données tierces

Après avoir utilisé des connecteurs de données pour importer et archiver des données tierces dans des boîtes aux lettres utilisateur, vous pouvez utiliser les outils eDiscovery Microsoft 365 pour rechercher des données tierces. Vous pouvez également utiliser des outils eDiscovery pour créer des conservations basées sur des requêtes associées à core eDiscovery et Advanced eDiscovery cas pour conserver des données tierces. Pour plus d’informations sur les outils eDiscovery, voir [les solutions eDiscovery dans Microsoft 365](ediscovery.md).

Pour rechercher (ou mettre en attente) tout type de données tierces que vous avez importées dans des boîtes aux lettres utilisateur à l’aide d’un connecteur de données, vous pouvez utiliser la requête de recherche suivante. Assurez-vous d’étendue de la recherche aux boîtes aux lettres des utilisateurs.

```powershell
kind:externaldata
```

Vous pouvez utiliser cette  requête dans la zone Mots clés pour une recherche de contenu, une recherche associée à un cas eDiscovery principal ou une collection dans Advanced eDiscovery.

![Interroger pour rechercher des données tierces.](..\media\SearchThirdPartyData1.png)

Vous pouvez également utiliser la paire propriété:valeur pour restreindre l’étendue des recherches à `kind:externaldata` des données tierces. Par exemple, pour rechercher des éléments importés à partir d’une source de données tierce contenant le mot *contoso* dans la propriété  **Subject** de l’élément importé, utilisez la requête suivante dans la zone Mots clés :

```powershell
subject:contoso AND kind:externaldata
```

Vous pouvez également utiliser la condition type **message** pour configurer la même requête.

![Utilisez la condition de type message pour restreindre les recherches à des données tierces.](..\media\SearchThirdPartyData2.png)

Pour rechercher un type spécifique de données tierces archivées, utilisez la propriété de boîte aux lettres **itemclass** dans une requête de recherche. Utilisez le format property:value suivant :

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Chaque élément importé par un connecteur de données tiers inclut la propriété **itemclass** avec une valeur qui correspond au type de données tiers. Par exemple, pour rechercher des données Facebook qui contiennent le mot *contoso*, dans la propriété **Subject** de l’élément importé, utilisez la requête suivante :

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Voici quelques exemples de valeurs **de classe** d’éléments pour différents types de données tierces.

| **Type de données tiers** | **Valeur de la propriété itemclass**   |
|---------------------------|-------------------------------------|
| Message Bloomberg         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| Archiveur WhatsApp         | ipm.externaldata.whatsapparchiver* |
|||

Les valeurs de *la propriété itemclass* ne sont pas sensibles à la cas. En règle générale, utilisez le nom du type de données tiers (sans espaces) suivi d’un caractère générique ( * ).

Pour plus d’informations sur la création de requêtes de recherche eDiscovery, voir Requêtes par mot clé et conditions de recherche [pour eDiscovery.](keyword-queries-and-search-conditions.md)

## <a name="data-connectors-in-the-us-government-cloud"></a>Connecteurs de données dans le cloud pour le gouvernement des États-Unis

Certains connecteurs de données sont disponibles dans le cloud du gouvernement des États-Unis. Les sections suivantes indiquent les environnements secteur public spécifiques qui supportent des connecteurs de données tiers. Pour plus d’informations sur les clouds du gouvernement des États-Unis, [voir Microsoft 365 gouvernement américain.](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy)

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>Connecteurs de données Veritas dans le cloud pour le gouvernement des États-Unis (prévisualisation)

|Connecteur de données  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust| Oui | Non | Non |
|Cisco Jabber sur MS SQL| Oui | Non | Non |
|Cisco Jabber sur Oracle| Oui | Non | Non |
|Cisco Jabber sur PostgreSQL| Oui | Non | Non |
|EML| Oui | Non | Non |
|FX Connect| Oui | Non | Non |
|Jive| Oui | Non | Non |
|Base de données MS SQL| Oui | Non | Non |
|Pivot| Oui | Non | Non |
|Redtail Speak| Oui | Non | Non |
|Gestion de Reuters| Oui | Non | Non |
|Reuters Eikon| Oui | Non | Non |
|Reuters FX| Oui | Non | Non |
|RingCentral| Oui | Non | Non |
|Salesforce Chatter| Oui | Non | Non |
|ServiceNow| Oui | Non | Non |
|Skype Entreprise| Oui | Non | Non |
|Découverte électronique de marge| Oui | Non | Non |
|Symphony| Oui | Non | Non |
|Délimité par le texte| Oui | Non | Non |
|Twitter| Oui | Non | Non |
|Webex Teams| Oui | Non | Non |
|Pages web| Oui | Non | Non |
|Espace de travail sur Facebook| Oui | Non | Non |
|XIP| Oui | Non | Non |
|XSLT/XML| Oui | Non | Non |
|Yieldbroker| Oui | Non | Non |
|YouTube| Non | Non | Non |
|Réunions Zoom| Oui | Non | Non |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>Connecteurs de données TeleMessage dans le cloud du gouvernement des États-Unis

|Connecteur de données  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|Archiveur Android | Oui | Non | Non |
|Archiveur réseau AT&T SMS/MMS | Oui | Non | Non |
|Archiveur réseau SMS/MMS Bell | Oui | Non | Non |
|Archiveur de numéros d’entreprise | Oui | Non | Non |
|O2 SMS et Voice Network Archiver | Oui         | Non | Non |
|Archiveur réseau de Lars | Oui         | Non | Non |
|Archiveur de signal | Oui | Non | Non |
|Archiveur de télégramme | Oui | Non | Non |
|ARCHIVEUR RÉSEAU SMS SMS | Oui | Non | Non |
|Archiveur réseau SMS/MMS Verizon | Oui | Non | Non |
|Archiveur WeChat | Oui | Non | Non |
|Archiveur WhatsApp | Oui | Non | Non |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>17a-4 connecteurs de données dans le cloud du gouvernement des États-Unis

|Connecteur de données  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|Analyseur de données BlackBerry | Oui | Non | Non |
|Analyseur de données Bloomberg  | Oui | Non | Non |
|Cisco Jabber DataParser  | Oui | Non | Non |
|Cisco Webex DataParser  | Oui | Non | Non |
|FactSet DataParser  | Oui | Non | Non |
|Fuze DataParser  | Oui | Non | Non |
|FX Connect DataParser  | Oui | Non | Non |
|ICE DataParser  | Oui | Non | Non |
|InvestEdge DataParser  | Oui | Non | Non |
|LivePerson Conversational Cloud DataParser  | Oui | Non | Non |
|Quip DataParser  | Oui | Non | Non |
|Refinitiv Eikon Messenger DataParser  | Oui | Non | Non |
|ServiceNow DataParser  | Oui | Non | Non |
|Analyseur de données Skype Entreprise Server | Oui | Non | Non |
|Slack DataParser | Oui | Non | Non |
|SQL DataParser  | Oui | Non | Non |
|Symphony DataParser | Oui | Non | Non |
|Zoom DataParser | Oui | Non | Non |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>Connecteurs de données CellTrust dans le cloud du gouvernement des États-Unis

|Connecteur de données  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Oui | Non | Non |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Collaborer avec un partenaire Microsoft pour archiver des données tierces

Pour importer et archiver des données tierces, votre organisation peut également travailler avec un partenaire Microsoft. Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le Centre de conformité Microsoft, vous pouvez travailler avec un partenaire qui peut fournir un connecteur personnalisé qui sera configuré pour extraire des éléments de la source de données tierces régulièrement, puis vous connecter au cloud Microsoft par une API tierce et importer ces éléments dans Microsoft 365. Le connecteur partenaire convertit également le contenu d’un élément de la source de données tierce en message électronique, puis l’importe dans une boîte aux lettres dans Microsoft 365.

Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, voir Travailler avec un partenaire pour archiver des données tierces [dans Microsoft 365](work-with-partner-to-archive-third-party-data.md).
