---
title: Utiliser des connecteurs de données pour importer et archiver des données tierces dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
description: Découvrez comment importer et archiver des données tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents vers des boîtes aux lettres Microsoft 365.
ms.openlocfilehash: 7653e51940c741ccc2f288c11428024f44022073
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67819466"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Découvrez les connecteurs pour les données tierces

Microsoft 365 permet aux administrateurs d’utiliser des connecteurs de données pour importer et archiver des données non-Microsoft tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration de documents dans des boîtes aux lettres de votre organisation Microsoft 365. L’un des principaux avantages de l’utilisation de connecteurs de données pour importer et archiver des données tierces dans Microsoft 365 est que vous pouvez appliquer différentes solutions Microsoft Purview aux données après leur importation. Cela vous permet de vous assurer que les données non Microsoft de votre organisation sont conformes aux réglementations et aux normes qui affectent votre organisation.

Regardez ce guide interactif qui montre comment créer des connecteurs de données pour importer et archiver des données tierces et des exemples d’application de solutions de conformité aux données après leur importation dans Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Connecteurs de données tiers

Le portail de conformité Microsoft Purview fournit des connecteurs de données tiers natifs de Microsoft pour importer des données à partir de différentes sources de données, telles que LinkedIn, Instant Bloomberg et Twitter, ainsi que des connecteurs de données qui prennent en charge la solution de gestion des risques Insider. En plus de ces connecteurs de données, Microsoft collabore avec les partenaires suivants pour fournir de nombreux connecteurs de données en troisième partie dans le portail de conformité. Votre organisation travaille avec ces partenaires pour configurer leur service d’archivage avant de créer un connecteur de données correspondant dans le portail de conformité.

- [Veritas](#veritas-data-connectors)

- [Telemessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

Les données tierces répertoriées dans les sections suivantes (à l’exception des données RH et des données de badging physiques utilisées pour la solution Gestion des risques internes Microsoft Purview) sont importées dans les boîtes aux lettres des utilisateurs. Les solutions Microsoft Purview qui prennent en charge les données tierces sont appliquées à la boîte aux lettres utilisateur où les données sont stockées.

### <a name="microsoft-data-connectors"></a>Connecteurs de données Microsoft

Le tableau suivant répertorie les connecteurs de données tiers natifs disponibles dans le portail de conformité. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer après avoir importé et archivé des données tierces dans Microsoft 365. Consultez la [vue d’ensemble des solutions de conformité qui prennent en charge la section des données tierces](#overview-of-compliance-solutions-that-support-third-party-data) pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Cliquez sur le lien dans la colonne de **données tierces** pour suivre les instructions pas à pas pour créer un connecteur pour ce type de données.

|Données tierces  |Conservation pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Message Bloomberg](archive-bloomberg-message-data.md)     |![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)||
|[Soins de santé Epic EHR](import-epic-data.md) ||||||![Coche](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Soins de santé DSE génériques](import-healthcare-data.md) ||||||![Coche](../media/checkmark.png)|
|[Ressources humaines (RH)](import-hr-data.md) ||||||![Coche](../media/checkmark.png)|
|[Conversation ICE](archive-icechat-data.md)     |![Coche.](../media/checkmark.png)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Badging physique](import-physical-badging-data.md) ||||||![Coche](../media/checkmark.png)|
|[Découverte électronique de marge](archive-slack-data-microsoft.md)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Connecteurs de données Veritas

Le tableau de cette section répertorie les connecteurs de données tiers disponibles en partenariat avec Veritas. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer à des données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la [vue d’ensemble des solutions de conformité qui prennent en charge la section des données tierces](#overview-of-compliance-solutions-that-support-third-party-data) pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez travailler avec Veritas pour configurer leur service d’archivage (appelé *Merge1*) pour votre organisation. Pour plus d’informations, cliquez sur le lien dans la colonne de **données tierces** pour suivre les instructions pas à pas pour créer un connecteur pour ce type de données.

|Données tierces  |Conservation pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
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
|[YouTube](archive-youtube-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|||
|[Réunions Zoom](archive-zoommeetings-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>Connecteurs de données de TeleMessage

Le tableau de cette section répertorie les connecteurs de données tiers disponibles en partenariat avec TeleMessage. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer à des données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la [vue d’ensemble des solutions de conformité qui prennent en charge la section des données tierces](#overview-of-compliance-solutions-that-support-third-party-data) pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez travailler avec TeleMessage pour configurer leur service d’archivage pour votre organisation. Pour plus d’informations, cliquez sur le lien dans la colonne de **données tierces** pour suivre les instructions pas à pas pour créer un connecteur pour ce type de données.

Les connecteurs de données TeleMessage sont également disponibles dans les environnements GCC dans le cloud Microsoft 365 US Government. Pour plus d’informations, consultez les [connecteurs de données dans la section cloud du gouvernement des États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article.

|Données tierces  |Conservation pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[RÉSEAU AT&T](archive-att-network-archiver-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau Bell](archive-bell-network-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Numéro d'entreprise](archive-enterprise-number-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau O2](archive-o2-network-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau Rogers](archive-rogers-network-archiver-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Signal](archive-signal-archiver-data.md)|![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Télégramme](archive-telegram-archiver-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau TELUS](archive-telus-network-data.md)    |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Réseau Verizon](archive-verizon-network-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[WhatsApp](archive-whatsapp-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>Connecteurs de données 17a-4

Le tableau de cette section répertorie les connecteurs de données tiers disponibles en partenariat avec 17a-4 LLC. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer à des données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la [vue d’ensemble des solutions de conformité qui prennent en charge la section des données tierces](#overview-of-compliance-solutions-that-support-third-party-data) pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez travailler avec 17a-4 LLC pour configurer leur service d’archivage (appelé *DataParser*) pour votre organisation. Pour plus d’informations, cliquez sur le lien dans la colonne de **données tierces** pour suivre les instructions pas à pas pour créer un connecteur pour ce type de données.

Les connecteurs de données 17a-4 sont également disponibles dans les environnements GCC dans le cloud Microsoft 365 US Government. Pour plus d’informations, consultez les [connecteurs de données dans la section cloud du gouvernement des États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article.

|Données tierces  |Conservation pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[BlackBerry](archive-17a-4-blackberry-data.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[FX Connect](archive-17a-4-fxconnect-data.md)    |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Conversation ICE](archive-17a-4-ice-im-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[LivePerson Conversational Cloud](archive-17a-4-liveperson-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Refinitiv Ekono Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
[Skype Entreprise Server](archive-17a-4-skype-for-business-server-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Slack](archive-17a-4-slack-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Symphony](archive-17a-4-symphony-data.md)    |![Marque de vérification.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
|[Zoom](archive-17a-4-zoom-data.md)    |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>Connecteurs de données CellTrust

Le tableau de cette section répertorie le connecteur de données tiers disponible en partenariat avec CellTrust. Le tableau récapitule également les solutions de conformité que vous pouvez appliquer à des données tierces après les avoir importées et archivées dans Microsoft 365. Consultez la [vue d’ensemble des solutions de conformité qui prennent en charge la section des données tierces](#overview-of-compliance-solutions-that-support-third-party-data) pour obtenir une description plus détaillée de chaque solution de conformité et de la façon dont elle prend en charge les données tierces.

Avant de pouvoir archiver des données tierces dans Microsoft 365, vous devez utiliser CellTrust pour configurer son service d’archivage (appelé *CellTrust SL2*) pour votre organisation. Pour plus d’informations, cliquez sur le lien dans la colonne de **données tierces** pour suivre les instructions pas à pas pour créer un connecteur CellTrust SL2.

|Données tierces  |Conservation pour litige|eDiscovery  |Paramètres de rétention  |Gestion des enregistrements  |Conformité des communications  |Gestion des risques internes  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Coche.](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||
||||||||

Le connecteur de données CellTrust SL2 est également disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Pour plus d’informations, consultez les [connecteurs de données dans la section cloud du gouvernement des États-Unis](#data-connectors-in-the-us-government-cloud) dans cet article.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Vue d’ensemble des solutions de conformité qui prennent en charge les données tierces

Les sections suivantes décrivent certaines des choses que les solutions Microsoft Purview peuvent vous aider à gérer les données tierces répertoriées dans le tableau précédent.

### <a name="litigation-hold"></a>Conservation pour litige

Vous placez une [conservation des litiges](create-a-litigation-hold.md) sur une boîte aux lettres d’utilisateur pour conserver les données tierces. Lorsque vous créez une conservation, vous pouvez spécifier une durée de conservation (également appelée *conservation basée sur le temps*) afin que les données tierces supprimées et modifiées soient conservées pendant une période spécifiée, puis supprimées définitivement de la boîte aux lettres. Ou vous pouvez simplement conserver le contenu indéfiniment (appelé *conservation infinie*) ou jusqu’à ce que la conservation litige soit supprimée.

### <a name="ediscovery"></a>eDiscovery

Les trois principaux outils eDiscovery dans Microsoft 365 sont La recherche de contenu, Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium).

- **[Recherche de contenu](content-search.md).** Vous pouvez utiliser l’outil de recherche de contenu pour rechercher des données tierces que vous avez importées dans les boîtes aux lettres. Vous pouvez utiliser des requêtes et des conditions de recherche pour affiner vos résultats de recherche et exporter les résultats de la recherche.

- **[eDiscovery (Standard).](get-started-core-ediscovery.md)** Cet outil s’appuie sur la fonctionnalité de recherche et d’exportation de base en vous permettant de créer des cas qui vous permettent de contrôler qui peut accéder aux données de cas, de bloquer les boîtes aux lettres utilisateur ou le contenu de boîte aux lettres qui correspond aux critères de recherche. Cela signifie que vous pouvez placer une conservation eDiscovery sur les données tierces qui ont été importées dans des boîtes aux lettres utilisateur.

- **[eDiscovery (Premium).](overview-ediscovery-20.md)** Cet outil puissant étend les fonctionnalités de cas d’eDiscovery (Standard) en vous permettant d’ajouter des consignats à un cas, de mettre les données du consignateur en attente, puis de charger les données tierces d’un dépositaire dans une révision pour une analyse plus approfondie, telle que les thèmes et la détection des doublons. Une fois que vous avez chargé des données tierces dans un jeu de révision, vous pouvez les interroger et les filtrer sur un jeu de résultats étroit.

   EDiscovery (Standard) et eDiscovery (Premium) vous permettent de gérer des données tierces qui peuvent être pertinentes pour les enquêtes légales ou internes de votre organisation.

### <a name="retention-settings"></a>Paramètres de rétention

Vous pouvez appliquer une [stratégie de rétention](retention.md) aux boîtes aux lettres des utilisateurs pour conserver, puis supprimer des données tierces (et d’autres contenus de boîte aux lettres) après expiration de la période de rétention. Vous pouvez également utiliser des stratégies de rétention pour supprimer des données tierces d’un certain âge ou [utiliser des étiquettes de rétention pour déclencher une révision de suppression](disposition.md) lorsque la période de rétention des données tierces expire.

### <a name="records-management"></a>Gestion des enregistrements

La fonctionnalité [de gestion des enregistrements](records-management.md) dans Microsoft 365 vous permet de déclarer des données tierces en tant qu’enregistrement. Cela peut être fait manuellement par les utilisateurs qui appliquent une étiquette de rétention qui marque les données tierces dans leur boîte aux lettres comme enregistrement. Vous pouvez également appliquer automatiquement des étiquettes de rétention en identifiant des informations sensibles, des mots clés ou des types de contenu dans des données tierces.

### <a name="communication-compliance"></a>Conformité des communications

Vous pouvez utiliser [la conformité des communications](communication-compliance.md) pour examiner les données tierces afin de vous assurer qu’elles sont conformes aux normes de données de votre organisation. Pour ce faire, vous pouvez détecter, capturer et prendre des mesures de correction pour les messages inappropriés dans votre organisation. Par exemple, vous pouvez surveiller les données tierces que vous importez pour détecter le langage offensant, les informations sensibles et la conformité réglementaire.

### <a name="insider-risk-management"></a>Gestion des risques internes

Les signaux provenant de données tierces, telles que des données RH sélectives, peuvent être utilisés par la solution de [gestion des risques Insider](insider-risk-management.md) pour réduire les risques internes en vous permettant de détecter, d’examiner et d’agir sur les activités à risque au sein de votre organisation. Par exemple, les données importées par le connecteur de données RH sont utilisées comme indicateurs de risque pour aider à détecter le vol de données des employés sortants.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Utilisation des outils eDiscovery pour rechercher des données tierces

Après avoir utilisé des connecteurs de données pour importer et archiver des données tierces dans des boîtes aux lettres utilisateur, vous pouvez utiliser les outils eDiscovery de Microsoft 365 pour rechercher des données tierces. Vous pouvez également utiliser les outils eDiscovery pour créer des conservations basées sur des requêtes associées à des cas eDiscovery (Standard) et eDiscovery (Premium) afin de conserver les données tierces. Pour plus d’informations sur les outils eDiscovery, consultez [les solutions eDiscovery dans Microsoft 365](ediscovery.md).

Pour rechercher (ou mettre en attente) tout type de données tierces que vous avez importées dans des boîtes aux lettres utilisateur à l’aide d’un connecteur de données, vous pouvez utiliser la requête de recherche suivante. Veillez à étendre la recherche aux boîtes aux lettres des utilisateurs.

```powershell
kind:externaldata
```

Vous pouvez utiliser cette requête dans la zone **Mots clés** pour une recherche de contenu, une recherche associée à un cas eDiscovery (Standard) ou une collection dans eDiscovery (Premium).

![Requête pour rechercher des données tierces.](..\media\SearchThirdPartyData1.png)

Vous pouvez également utiliser la `kind:externaldata` paire propriété:valeur pour limiter l’étendue des recherches aux données tierces. Par exemple, pour rechercher des éléments importés à partir d’une source de données tierce qui contient le mot *contoso* dans la propriété **Subject** de l’élément importé, utilisez la requête suivante dans la zone **Mots clés** :

```powershell
subject:contoso AND kind:externaldata
```

Vous pouvez également utiliser la condition **de type Message** pour configurer la même requête.

![Utilisez la condition de type Message pour limiter les recherches aux données tierces.](..\media\SearchThirdPartyData2.png)

Pour rechercher un type spécifique de données tierces archivées, utilisez la propriété de boîte aux **lettres itemclass** dans une requête de recherche. Utilisez le format property:value suivant :

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Chaque élément importé par un connecteur de données tiers inclut la propriété **itemclass** avec une valeur qui correspond au type de données tiers. Par exemple, pour rechercher des données Facebook qui contiennent le mot *contoso*, dans la propriété **Subject** de l’élément importé, utilisez la requête suivante :

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Voici quelques exemples de valeurs **itemclass** pour différents types de données tierces.

| **Type de données tiers** | **Valeur de la propriété itemclass**   |
|---------------------------|-------------------------------------|
| Message Bloomberg         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| Archiveur WhatsApp         | ipm.externaldata.whatsapparchiver* |
|||

Les valeurs de la propriété *itemclass* ne respectent pas la casse. En général, utilisez le nom du type de données tiers (sans espaces) suivi d’un caractère générique ( * ).

Pour plus d’informations sur la création de requêtes de recherche eDiscovery, consultez requêtes de mots [clés et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>Connecteurs de données dans le cloud us government

Certains connecteurs de données sont disponibles dans le cloud us government. Les sections suivantes indiquent les environnements gouvernementaux spécifiques qui prennent en charge les connecteurs de données tiers. Pour plus d’informations sur les clouds US Government, consultez [Microsoft 365 US Government](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>Connecteurs de données Veritas dans le cloud US Government (préversion)

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

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>Connecteurs de données TeleMessage dans le cloud us government

|Connecteur de données  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|Archiveur Android | Oui | Non | Non |
|Archiveur réseau AT&T SMS/MMS | Oui | Non | Non |
|Archiveur réseau SMS/MMS Bell | Oui | Non | Non |
|Archiveur de numéros d’entreprise | Oui | Non | Non |
|Archiveur de réseaux vocaux et SMS O2 | Oui         | Non | Non |
|Archiveur réseau de Lars | Oui         | Non | Non |
|Archiveur de signal | Oui | Non | Non |
|Archiveur de télégramme | Oui | Non | Non |
|Archiveur réseau SMS TELUS | Oui | Non | Non |
|Archiveur réseau SMS/MMS Verizon | Oui | Non | Non |
|Archiveur WeChat | Oui | Non | Non |
|Archiveur WhatsApp | Oui | Non | Non |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>Connecteurs de données 17a-4 dans le cloud us government

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

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>Connecteurs de données CellTrust dans le cloud us government

|Connecteur de données  |GCC  |GCC High  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Oui | Non | Non |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Utilisation d’un partenaire Microsoft pour archiver des données tierces

Une autre option permettant d’importer et d’archiver des données tierces consiste à permettre à votre organisation de travailler avec un partenaire Microsoft. Si un type de données tiers n’est pas pris en charge par les connecteurs de données disponibles dans le Centre de conformité Microsoft, vous pouvez travailler avec un partenaire qui peut fournir un connecteur personnalisé qui sera configuré pour extraire régulièrement des éléments de la source de données tierce, puis se connecter au cloud Microsoft par une API tierce et importer ces éléments dans Microsoft 365. Le connecteur partenaire convertit également le contenu d’un élément de la source de données tierce en message électronique, puis l’importe dans une boîte aux lettres dans Microsoft 365.

Pour obtenir la liste des partenaires avec qui vous pouvez travailler et le processus pas à pas pour cette méthode, consultez [Travailler avec un partenaire pour archiver des données tierces dans Microsoft 365](work-with-partner-to-archive-third-party-data.md).
