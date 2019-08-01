---
title: Demandes des personnes concernées pour Dynamics 365 concernant le RGPD
description: Guide expliquant comment utiliser les produits, services et outils d’administration Microsoft pour aider les clients de notre entité de contrôle à rechercher des données personnelles et à prendre des mesures pour répondre aux DPC.
keywords: Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365, RGPD
localization_priority: Priority
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: GDPR
ms.openlocfilehash: 72277ec2dfe7681aa5f596e655d5e275bbb64dd1
ms.sourcegitcommit: 5615e790dc53ccc74f3c475ca43d69ca56be348a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "36041178"
---
# <a name="dynamics-365-data-subject-requests-for-the-gdpr"></a>Demandes des personnes concernées par le traitement des données pour Dynamics 365 concernant le RGPD

Le [Règlement général sur la protection des données (RGPD)](https://ec.europa.eu/justice/data-protection/reform/index_en.htm) de l’UE permet aux utilisateurs (désignés dans le règlement comme *personnes concernées*) de gérer les données à caractère personnel collectées par un employeur ou tout autre type d’organisme ou d’organisation (*responsable du traitement des données* ou *responsable du traitement*). Les données à caractère personnel sont définies de manière générale dans le cadre du RGPD comme correspondant aux données associées à une personne physique identifiée ou identifiable. Le RGPD octroie aux personnes concernées des droits spécifiques sur leurs données à caractère personnel. Ces droits incluent l’obtention de copies des données à caractère personnel, les demandes de changements de ces dernières, la restriction de leur traitement, leur suppression ou leur réception dans un format électronique afin de les transférer à un autre responsable du traitement. Toute demande formelle effectuée par une personne concernée à un responsable du traitement au sujet de la prise de mesure sur ses données à caractère personnel est appelée dans ce document *demande de droits de personne concernée* ou DPC.

Le guide explique comment utiliser les outils d’administration, les services et les produits de Microsoft pour aider nos clients responsables du traitement à rechercher des données à caractère personnel et à agir dessus pour répondre à des DPC. Plus précisément, il décrit comment rechercher des données à caractère personnel stockées dans le cloud de Microsoft, y accéder et agir dessus. Voici un aperçu des processus décrits dans ce guide :

- **Découvrir :** utilisez les outils de recherche et de découverte pour rechercher plus facilement des données client qui peuvent faire l’objet d’une DPC. Lorsque vous avez collecté les documents pouvant être utiles, vous pouvez effectuer une ou plusieurs des actions DPC décrites dans les étapes suivantes pour répondre à la demande. Par ailleurs, vous pouvez déterminer que la demande ne respecte pas les instructions de votre organisation pour répondre à des DPC.
- **Accéder :** récupérez des données à caractère personnel qui résident dans le cloud Microsoft et, si nécessaire, effectuez-en une copie pour la personne concernée.
- **Rectifier :** modifiez ou mettez en œuvre d’autres actions demandées sur les données à caractère personnel, le cas échéant.
- **Limiter** : limitez le traitement des données à caractère personnel en supprimant les licences de différents services en ligne ou en désactivant les services souhaités lorsque c’est possible.
- **Supprimer :** supprimez définitivement des données à caractère personnel qui résidaient dans le cloud de Microsoft.
- **Exporter :** fournissez une copie électronique (dans un format lisible par un ordinateur) des données à caractère personnel à la personne concernée.

Chaque section de ce guide décrit les procédures techniques qu’une organisation de contrôleur des données peut suivre pour répondre à une demande DSR pour des données personnelles dans le cloud de Microsoft.

### <a name="gdpr-terminology"></a>Terminologie RGPD

Vous trouverez ci-dessous des définitions de termes utilisés dans ce guide :

- **Responsable du traitement des données :** la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui, seul ou conjointement avec d’autres, détermine les finalités et les moyens du traitement des données à caractère personnel ; lorsque les finalités et les moyens du traitement sont déterminés par la législation de l’Union ou des États membres, le responsable du traitement peut être désigné, ou les critères spécifiques relatifs à sa nomination être définis, par la législation de l’Union ou des États membres.
- **Données personnelles et personne concernée par le traitement des données :** informations relatives à une personne physique identifiée ou identifiable (« la personne concernée par le traitement des données ») ; une personne physique identifiable est une personne qui peut être identifiée, directement ou indirectement, notamment par référence à un identificateur par exemple, un nom, un numéro d’identification, des données de localisation, un identificateur en ligne, ou un ou plusieurs facteurs spécifiques de l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne physique.
- **Sous-traitant de données :** la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui traite des données à caractère personnel pour le compte du responsable du traitement.
- **Données client :** toutes les données, y compris tous les fichiers texte, son, vidéo ou image et les logiciels qui ont été fournis à Microsoft par le client ou pour son compte dans le cadre du service d’entreprise. Les données client incluent à la fois les (1) informations d’identification personnelle des utilisateurs finaux (par exemple, les noms d’utilisateur et les informations de contact dans Azure Active Directory) et le contenu client chargé ou créé par un client dans des services spécifiques (par exemple, le contenu client dans un compte de stockage Azure, le contenu client d’une base de données Azure SQL ou l’image de la machine virtuelle d’un client dans des machines virtuelles Azure).
- **Journaux générés par le système :** journaux et données associées générés par Microsoft qui permettent à Microsoft de fournir des services d’entreprise aux utilisateurs. Les journaux générés par le système contiennent essentiellement des données pseudonymes, généralement un numéro généré par le système qui ne permet pas, en soi, d’identifier une personne individuelle, mais qui est utilisé pour fournir les services d’entreprise aux utilisateurs. Les journaux générés par le système peuvent également contenir des informations d’identification personnelle sur les utilisateurs finaux, telles qu’un nom d’utilisateur.

### <a name="how-this-guide-can-help-you-meet-your-controller-responsibilities"></a>Assumer vos responsabilités de contrôleur grâce à ce guide

Le guide, divisé en deux parties, explique comment utiliser les produits, services et outils d’administration Dynamics 365 pour rechercher et manipuler les données dans le cloud Microsoft en réponse aux demandes des personnes concernées qui exercent leurs droits en vertu du GDPR. La première partie traite des données à caractère personnel incluses dans les données client. Elle est suivie d’une partie traitant des autres données à caractère personnel pseudonymes, consignées dans des journaux générés par le système.

- **Partie 1 : Répondre à des demandes de droits de la personne concernée (DPC) pour des données à caractère personnel incluses dans des données client.** La première partie de ce guide explique comment accéder à des données à caractère personnel, les rectifier, limiter, supprimer et exporter à partir d’applications Dynamics 365 (software as a service – SaaS), qui sont traitées avec les données client que vous avez fournies au service en ligne.
- **Partie 2 : Répondre à des demandes de droits de la personne concernée pour des données pseudonymes** : lorsque vous utilisez les services d’entreprise Dynamics 365, Microsoft génère des informations (référencées dans ce document en tant que *journaux générés par le système*) pour fournir le service, qui sont limitées à l’utilisation des utilisateurs finaux pour identifier leurs actions dans le système. Bien que ces données ne puissent pas permettre d’identifier précisément une personne concernée par le traitement des données sans utiliser d’informations supplémentaires, certaines d’entre elles peuvent être considérées comme personnelles en vertu du RGPD. La deuxième partie de ce guide décrit la consultation, la suppression et l’exportation des journaux générés par le système obtenus par Dynamics 365.

### <a name="preparing-for-data-subject-rights-investigations"></a>Préparation des examens de droits des personnes concernées par le traitement des données

Lorsque des personnes associées aux données exercent leurs droits et effectuent des demandes, tenez compte des points suivants :

- Identifiez correctement la personne et le rôle (par exemple, employé, client, fournisseur) à l’aide des informations fournies par la personne concernée par le traitement des données dans le cadre de sa demande. Ces informations peuvent être un nom, un ID d’employé ou un numéro de client, ou un autre identificateur.
- Enregistrez la date et l’heure de la demande. (Vous avez 30 jours pour effectuer la demande.)
- Vérifiez que la demande répond aux exigences de votre organisation pour honorer ou refuser la demande d’une personne concernée. Par exemple, vous devez vous assurer que l’exécution de la demande n’entre pas en conflit avec d’autres obligations réglementaires, juridiques ou financières que vous avez ou qu’elle n’enfreint pas les droits et les libertés d’autres individus.
- Vérifiez que vous disposez des informations liées à la demande.

## <a name="part-1-responding-to-data-subject-rights-requests-for-personal-data-included-in-customer-data"></a>Partie 1 : Répondre aux demandes de droits des personnes concernées relatives aux données à caractère personnel dans les données client

Dans les articles ci-dessous, vous trouverez des informations qui vous aideront à préparer des DPC et à y répondre pour des données personnelles incluses dans des données client traitées dans Dynamics 365. Il est important de noter que des données personnelles peuvent être présentes dans d’autres catégories de données traitées par Microsoft au cours du service d’un abonnement à des services en ligne (comme, par exemple, des données administrateur ou des données de support définies dans la déclaration de confidentialité de Microsoft). Ce document n’a pour but que de vous aider dans la découverte et la gestion des DPC qui concernent les données personnelles présentes dans les données client que vous avez fournies à Dynamics 365.

Dynamics 365 est un service en ligne qui propose plusieurs fonctionnalités de traitement des données comme un service SaaS. Ainsi, Dynamics 365 offre un large éventail de fonctionnalités conçues pour traiter une collection diversifiée de données, pouvant varier par nature, objectif ou autres attributs spécifiques (données de ventes, transactions, données financières, informations de RH, etc.). Compte tenu de cette diversité, Dynamics 365 propose plusieurs formulaires, champs, schémas, points de terminaison et logiques pour traiter les données client, et ceci se reflète aussi dans les différentes façons qui permettent de traiter des demandes DSR dans chaque application. Lorsque des applications Dynamics 365 proposent plusieurs méthodes pour traiter des demandes DSR spécifiques, nous les noterons dans ce guide en pointant vers les descriptions techniques offertes par chaque application.

### <a name="dynamics-365"></a>Dynamics 365

#### <a name="finding-customer-data"></a>Consultation des données client

La première étape pour répondre à une demande de droits de la personne concernée consiste à rechercher et identifier les données client faisant l’objet de la demande.

La classification appropriée des données client est à la base de la gestion des données personnelles dans les applications métier Dynamics 365 Customer Engagement. Dynamics 365 for Customer Engagement permet de créer une extension d’application autour de la classification des données avec une grande souplesse. La classification vous permet d’identifier les informations comme données personnelles, et ainsi de les localiser et les récupérer lorsque vous répondez aux demandes d’une personne concernée. Elle permet également d’assurer la conformité avec les exigences réglementaires et législatives pour la collecte et la gestion des données personnelles.

Microsoft offre des fonctionnalités qui vous aident à répondre aux demandes de droits de la personne concernée par le traitement des données, et par conséquent d’accéder aux données client. Toutefois, il est de votre responsabilité de vérifier que les données personnelles sont localisées et classées de façon appropriée.

L’offre ***Dynamics 365 for Customer Engagement*** fournit plusieurs méthodes qui vous permettent de rechercher des données personnelles dans des enregistrements, telles que : la recherche avancée, la recherche selon la pertinence et la recherche d’enregistrements. Toutes ces fonctions vous permettent d’identifier (rechercher) des données personnelles.

- [Recherche avancée](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)
- [Recherche selon la pertinence](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results), qui peut être enregistrée pour référence ultérieure à l’aide de tableaux de bord
- [Recherche d’enregistrements](https://docs.microsoft.com/dynamics365/customer-engagement/basics/search-records) dans plusieurs types d’enregistrements

Dans Dynamics 365 for Marketing, vous disposez des fonctionnalités supplémentaires suivantes :

1. [Générer des rapports Power BI](https://docs.microsoft.com/power-bi/service-connect-to-microsoft-dynamics-crm) afin de filtrer et identifier des données client.
2. Utilisez les affichages Insight sur les contacts et les objets de l’exécution marketing pour identifier des points de données supplémentaires pouvant contenir des données client.

***Dynamics 365 Customer Service Insights*** propose une liste de ressources destinée à vous aider à [trouver des données client](https://docs.microsoft.com/dynamics365/ai/customer-service-insights/gdpr-discovery) afin de répondre aux demandes RGPD des clients. 

L’offre ***Dynamics 365 for Finance and Operations*** permet de rechercher des données client de plusieurs façons. En tant qu’administrateur client, vous pouvez rechercher des données client en effectuant les opérations suivantes :

- Organisez vos données client de façon à découvrir rapidement des données personnelles ; à cette fin, apprenez à [classifier l’inventaire des données](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#detailed-inventory).
- Utilisez le [rapport de recherche de données personnelles](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) pour rechercher et collecter des données personnelles.
- [Étendez le rapport de recherche de données personnelles](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-extend-person-search-report) en créant une entité ou en étendant une entité existante.
- Utilisez les fonctionnalités de recherche et de filtre pour rechercher des données personnelles spécifiques et les exporter à l’aide de la fonctionnalité Exporter de Microsoft Office ou imprimez ces informations dans un fichier .pdf à l’aide d’extensions de navigateur.
- Créez un formulaire personnalisé qui localise et exporte les données personnelles.
- Créez un portail externe ou un site web qui permet à un client authentifié d’afficher ses données personnelles.

***Dynamics 365 Business Central*** offre plusieurs façons de rechercher des données client. Pour plus d’informations, consultez [Recherche, filtrage et tri de données](https://docs.microsoft.com/dynamics365/business-central/ui-enter-criteria-filters).

****** Dynamics 365 for Talent fournit des fonctionnalités de recherche et de filtre avancées permettant de rechercher des données personnelles spécifiques ainsi que la fonctionnalité Exporter de Microsoft Office pour exporter ou imprimer ces informations dans un fichier .pdf à l’aide d’extensions de navigateur.

- Utilisez le [rapport de recherche de données personnelles](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#the-person-search-report) pour rechercher et collecter des données client.
- [Étendez le rapport de recherche de données personnelles](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-extend-person-search-report) en créant une entité ou en étendant une entité existante.

### <a name="providing-a-copy-of-customer-data"></a>Fourniture d’une copie des données client

Les données client contenues dans ***Dynamics 365 for Customer Engagement*** peuvent être exportées à l’aide des fonctionnalités d’exportation d’entités complètes. Les données client peuvent être exportées dans un fichier Excel statique pour faciliter une demande de portabilité des données. En utilisant Excel, vous pouvez alors modifier les données personnelles à inclure dans la demande de portabilité et les enregistrer ensuite dans un format courant lisible par un ordinateur comme .csv ou .xml.

En outre, pour Dynamics 365 for Marketing, une [API dédiée](https://docs.microsoft.com/dynamics365/customer-engagement/marketing/developer/retrieve-interactions-contact) est fournie pour permettre au client de générer des extensions qui récupèrent des enregistrements supplémentaires des interactions client capturées pouvant contenir des données personnelles. L’API charge toutes les informations pertinentes à partir du système principal et les assemble dans un document unique portable.

***Dynamics 365 Customer Service Insights*** vous permet de [fournir une copie des données client](https://docs.microsoft.com/dynamics365/ai/customer-service-insights/gdpr-export) via l’exportation de données.

Les données client contenues dans ***Dynamics 365 for Finance and Operations*** peuvent être exportées à l’aide des fonctionnalités d’exportation d’entités complètes. Grâce aux [*entités d’intégration et de gestion de données*](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-management-integration-data-entity), l’administrateur client peut utiliser des entités fournies, en créer de nouvelles ou développer des entités existantes en vue de définir une exportation de données personnelles renouvelable vers Excel ou dans d’autres formats courants au moyen de [*tâches d’importation et d’exportation de données*](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-import-export-job).  De nombreuses listes peuvent aussi être exportées dans un fichier Excel statique pour faciliter une demande de portabilité des données. Une fois que les données client sont exportées dans Excel, vous pouvez modifier les données personnelles à inclure dans la demande de portabilité et enregistrer ensuite le fichier dans un format courant lisible par un ordinateur comme .csv ou .xml. Vous pouvez aussi envisager d’utiliser le * rapport de recherche de données personnelles * pour fournir à la personne concernée les données que vous avez classifiées en tant que données personnelles.

Dans ***Dynamics 365 Business Central***, vous pouvez utiliser deux fonctionnalités pour fournir une copie des données client à une personne concernée :

Vous pouvez exporter les données client dans un fichier Excel. Dans Excel, vous pouvez ensuite modifier les données client à inclure dans la demande de portabilité et les enregistrer dans un format courant lisible par un ordinateur comme .csv ou .xml. Pour plus d’informations, consultez [Exportation de vos données métier dans Excel.](https://docs.microsoft.com/fr-FR/dynamics365/business-central/about-export-data)

Dans ***Dynamics 365 for Talent***, vous pouvez utiliser [Étendre le rapport de recherche des données personnelles](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-extend-person-search-report) pour collecter des informations et répondre à une demande de copie des données personnelles de la personne concernée.

### <a name="rectifying-customer-data"></a>Rectification des données client

L’offre ***Dynamics 365 for Customer Engagement*** propose les méthodes suivantes pour corriger des données client inexactes ou incorrectes, ou effacer des données client :

- Recherchez des données client à l’aide des fonctionnalités mentionnées dans « Consultation des données client » et modifiez directement les données dans les formulaires Customer Engagement. Les modifications peuvent être effectuées au niveau d’une ligne unique ou plusieurs lignes peuvent être modifiées directement.
- Grâce à la modification en bloc de plusieurs enregistrements Customer Engagement, vous pouvez utiliser le complément Microsoft Office pour exporter des données vers Microsoft Excel, apporter vos changements puis importer ces données modifiées dans Dynamics 365 for Customer Engagement.

En outre, pour Dynamics 365 for Marketing, vous pouvez aussi :

- Mettre à jour la page d’accueil de vos données en modifiant une ou plusieurs lignes directement
- Préparez une page de [centres d’abonnement](https://docs.microsoft.com/dynamics365/customer-engagement/marketing/set-up-subscription-center) comportant autant de champs de contact modifiables que possible. Ceci permet à un utilisateur final de mettre à jour ses informations autant que possible.

***Dynamics 365 Customer Service Insights*** offre également des fonctionnalités qui permettent aux organisations de [rectifier ou d’apporter des modifications aux données client](https://docs.microsoft.com/dynamics365/ai/customer-service-insights/gdpr-summary#a=note-about-requests-to-rectify-personal-data).

Dans ***Dynamics 365 for Finance and Operations***, vous pouvez aussi utiliser les [*outils de personnalisation*](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/dev-tools/developer-home-page), mais la décision et l’implémentation relèvent de votre responsabilité.

L’offre ***Dynamics 365 Business Central*** propose deux façons de corriger des données client inexactes ou incomplètes.

Pour modifier en bloc plusieurs enregistrements Business Central, vous pouvez exporter des listes vers Excel à l’aide du [complément Excel de Business Central](https://docs.microsoft.com/fr-FR/dynamics365/business-central/finance-analyze-excel#the--excel-add-in) afin de corriger plusieurs enregistrements, puis publier les données modifiées dans Excel dans Business Central. Pour plus d’informations, consultez la section [Exportation de vos données métiers dans Excel](https://docs.microsoft.com/fr-FR/dynamics365/business-central/about-export-data).

Vous pouvez modifier les données client stockées dans un champ (par exemple, les informations sur un client dans sa fiche) en changeant manuellement l’élément de données contenant les données à caractère personnel cibles. Pour plus d’informations, consultez [Entrée de données](https://docs.microsoft.com/dynamics365/business-central/ui-enter-data).

#### <a name="brief-note-about-modifying-entries-in-business-transactions"></a>Remarque sur la modification des entrées dans les transactions commerciales

Les enregistrements de transaction tels que les entrées de comptabilité grand livre, client et générale sont essentiels pour l’intégrité du système de planification des ressources d’une entreprise. Les données personnelles faisant partie d’une transaction financière ou autre sont conservées « telles quelles » à des fins de conformité avec les lois financières (législation fiscale, par exemple), prévention contre les fraudes (piste d’audit de sécurité) ou conformité avec les certifications de l’industrie. Par conséquent, Dynamics 365 for Finance and Operations et Dynamics 365 Business Central limitent la modification des données dans les enregistrements de ce type.

Si vous stockez des données personnelles dans des enregistrements de transaction commerciale, la seule façon de corriger, supprimer ou limiter le traitement des données personnelles pour honorer la demande d’une personne concernée est d’utiliser les [fonctionnalités de personnalisation](https://docs.microsoft.com/dynamics365/business-central/dev-itpro/index) de Dynamics 365 Business Central. L[](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/gdpr-guide#reasons-why-certain-personal-data-may-not-be-modified-or-deleted)a décision d’honorer la demande de modification et d’implémentation d’une personne concernée relève de votre responsabilité.

### <a name="restricting-the-processing-of-customer-data"></a>Restriction du traitement des données client

Quand vous recevez une demande d’une personne concernée pour limiter le traitement de données client, vous pouvez facilement extraire les données client en question du service en ligne et les stocker dans un conteneur distinct (stockage local ou service web distinct doté de fonctionnalités d’isolation des données) isolé des fonctions de traitement offertes par les applications cloud.

Un mécanisme de substitution comme le blocage du traitement des données est proposé par ***Dynamics 365 Business Central***, qui permet aux utilisateurs de bloquer l’enregistrement d’une personne concernée par le traitement des données. Pour plus d’informations, consultez [Restreindre le traitement des données pour un sujet données](https://docs.microsoft.com/dynamics365/business-central/admin-responding-to-requests-about-personal-data#restrict-data-processing-for-a-data-subject). Quand un enregistrement est marqué comme étant bloqué, Dynamics 365 Business Central interrompt le traitement des données de la personne concernée. Vous ne pouvez pas créer des transactions qui utilisent un enregistrement bloqué ; par exemple, vous ne pouvez pas créer une facture pour un client, du moment que ledit client ou le commercial est bloqué.

### <a name="deleting-customer-data"></a>Suppression des données client

Quand une personne concernée vous demande de supprimer ses données client, vous pouvez le faire de plusieurs façons :

- Grâce à la modification en bloc de plusieurs enregistrements Dynamics 365, vous pouvez utiliser le complément Microsoft Office pour exporter des données vers Microsoft Excel, apporter vos changements puis importer ces données modifiées d’Excel dans le service en ligne.
- Vous pouvez supprimer des données client stockées dans un champ en localisant les données à supprimer puis en supprimant manuellement l’élément de données contenant les données client cibles (par exemple, en supprimant définitivement l’enregistrement de contact représentant la personne concernée et d’autres enregistrements contenant des données personnelles).

Par ailleurs, dans le cas de Dynamics 365 Marketing, la suppression d’un contact s’accompagne de la suppression des données d’interaction avec les informations personnelles. Pour les entités ou les champs personnalisés, vous devez personnaliser votre système pour faire en sorte qu’il supprime toutes les données client des enregistrements connexes et/ou les dissocie de l’enregistrement de contact afin que toutes les informations personnelles soient supprimées. Pour plus d’informations, consultez le [Guide du développeur (Marketing)](https://docs.microsoft.com/dynamics365/customer-engagement/marketing/developer/marketing-developer-guide).

***Dynamics 365 Customer Service Insights*** dote également les organisations de fonctionnalités permettant de [supprimer les données client](https://docs.microsoft.com/dynamics365/ai/customer-service-insights/gdpr-delete).

Vous pouvez aussi utiliser ***Dynamics 365 for Finance and Operations*** et ses [*outils de personnalisation*](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/dev-tools/developer-home-page) pour effacer/modifier des données client.

Dans ***Dynamics 365 Business Central***, quand une personne concernée vous demande de supprimer ses données personnelles qui se trouvent dans vos données client, vous pouvez satisfaire cette demande de différentes façons :

- Pour modifier en bloc plusieurs enregistrements Business Central, vous pouvez exporter des données vers Excel à l’aide du [complément Excel de Business Central](https://docs.microsoft.com/fr-FR/dynamics365/business-central/finance-analyze-excel#the--excel-add-in) afin de supprimer plusieurs enregistrements, puis publier ces changements d’Excel dans Business Central. Pour plus d’informations, consultez la section [Exportation de vos données métiers dans Excel](https://docs.microsoft.com/fr-FR/dynamics365/business-central/about-export-data).
- Vous pouvez supprimer les données client stockées dans un champ en supprimant manuellement l’élément de données contenant les données client cibles. Pour plus d’informations, consultez [Entrée de données](https://docs.microsoft.com/dynamics365/business-central/ui-enter-data).
- Vous pouvez supprimer des données client directement, par exemple en supprimant un contact et en exécutant ensuite le traitement par lot Supprimer les écritures journal d’interaction annulées pour supprimer les interactions pour ce contact.
- Vous pouvez [supprimer des documents](https://docs.microsoft.com/dynamics365/business-central/admin-manage-documents) contenant des données client (par exemple, des mémos, des ventes enregistrées et des factures d’achat).

Outre la suppression en bloc ou individuelle d’enregistrements distincts, veuillez noter que seuls les travailleurs licenciés peuvent être totalement supprimés de ***Dynamics 365 for Talent***. [Suivez ces étapes pour supprimer des travailleurs licenciés](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/gdpr/respond-dsr-request-talent#additional-notes-that-apply-to-requests-for-personal-data).

### <a name="exporting-customer-data"></a>Exportation des données client

Pour répondre à une demande de portabilité des données, les données client contenues dans ***Dynamics 365 for Customer Engagement*** peuvent être exportées à l’aide des fonctionnalités d’exportation d’entités complètes. Les données client peuvent être exportées dans un fichier Excel statique pour faciliter une demande de portabilité des données. En utilisant Excel, vous pouvez alors modifier les données personnelles à inclure dans la demande de portabilité et les enregistrer ensuite dans un format courant lisible par un ordinateur comme .csv ou .xml.

En outre, pour Dynamics 365 for Marketing, une [API dédiée](https://docs.microsoft.com/dynamics365/customer-engagement/marketing/developer/retrieve-interactions-contact) est fournie pour permettre au client de générer des extensions qui récupèrent des enregistrements supplémentaires des interactions client capturées pouvant contenir des données personnelles. L’API charge toutes les informations pertinentes à partir du système principal et les assemble dans un document unique portable.

Pour ***Dynamics 365 Customer Service Insights***, vous devez [exporter les données clients](https://docs.microsoft.com/dynamics365/ai/customer-service-insights/gdpr-export) via le portail de gestion Azure.

******[Dynamics 365 for Finance and Operations](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-management-integration-data-entity) offre des [entités d’intégration et de gestion de données](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-import-export-job), ce qui permet aux entités étendues de faire l’objet d’une exportation de données personnelles renouvelable vers Excel ou dans divers autres formats courants via des tâches d’importation et d’exportation de données.  De nombreuses listes peuvent aussi être exportées dans un fichier Excel statique pour faciliter une demande de portabilité des données. Quand les données client sont exportées dans Excel de cette façon, vous pouvez modifier les données personnelles à inclure dans la demande de portabilité et enregistrer ensuite le fichier dans un format courant lisible par un ordinateur comme .csv ou .xml.

Dynamics 365 for Finance and Operations et ***Dynamics 365 for Talent*** fournissent un rapport de recherche des données personnelles pour fournir les données que vous avez classées comme données personnelles à la personne concernée par le traitement des données. 

L’offre ***Dynamics 365 Business Central*** propose les fonctionnalités suivantes :

- Vous pouvez exporter les données client dans un fichier Excel. Dans Excel, vous pouvez ensuite modifier les données client à inclure dans la demande de portabilité et les enregistrer dans un format courant lisible par un ordinateur comme .csv ou .xml. Pour plus d’informations, consultez [Exportation de vos données métier dans Excel](https://docs.microsoft.com/dynamics365/business-central/about-export-data).
- Vous pouvez exporter les données client dans un fichier Excel. Dans Excel, vous pouvez ensuite modifier les données client à inclure dans la demande de portabilité et les enregistrer dans un format courant lisible par un ordinateur comme .csv ou .xml. Pour plus d’informations, consultez [Exportation de vos données métier dans Excel](https://docs.microsoft.com/fr-FR/dynamics365/business-central/about-export-data).

### <a name="microsoft-social-engagement"></a>Microsoft Social Engagement

Étant donné que Microsoft Social Engagement traite des données personnelles qui sont susceptibles de figurer parmi des données client et du contenu de réseaux sociaux, cette application offre un moyen unique de répondre aux demandes DSR, car elle a un rapport avec les données personnelles récupérées sur les réseaux sociaux. Le contenu social est du contenu disponible publiquement collecté à partir de réseaux sociaux (par exemple, Twitter, Facebook et YouTube) et de services d’agrégation et d’indexation de données en réponse aux requêtes de recherche du client exécutées dans Microsoft Social Engagement. Le contenu des réseaux sociaux ne correspond pas à des données client. Des restrictions supplémentaires sur le traitement, l’utilisation et le stockage de contenu de réseaux sociaux sont décrites dans les Conditions d’utilisation des services en ligne Microsoft.

### <a name="finding-personal-data"></a>Recherche de données personnelles

La première étape pour répondre à la demande d’une personne concernée consiste à rechercher et identifier les données personnelles qui sont l’objet de cette demande. Microsoft Social Engagement stocke les données suivantes :

#### <a name="for-social-media-users"></a>Pour les utilisateurs de réseaux sociaux

- Données d’utilisateurs de réseaux sociaux (appelées *auteur* dans Social Engagement) que Social Engagement acquiert à partir de plateformes sociales. Elles peuvent inclure le nom, le nom d’utilisateur, l’image de profil, l’emplacement, le site web et la biographie si elle est fournie par l’auteur.
- Balises d’auteur utilisées pour regrouper et classifier les auteurs (par exemple, influenceurs, concurrents ou admirateurs).

#### <a name="for-employees"></a>Pour les employés

- Profils utilisateur qui incluent le nom de l’employé, les informations de contact et l’image de profil et qui sont gérés dans Office 365.
- Adresses e-mail fournies par des employés qui ont créé des alertes de post et des alertes de tendance.
- Comptes de réseaux sociaux (appelés *profils sociaux* dans Social Engagement) qui sont authentifiés dans Social Engagement par les employés pour s’engager auprès d’autres personnes sur une plateforme sociale. Ils peuvent appartenir à un employé ou à l’organisation et incluent des données fournies par les employés lorsqu’ils enregistrent un compte sur une plateforme sociale. Ces profils représentent l’organisation sur les médias sociaux et sont utilisés pour interagir avec des posts pour le compte de l’organisation à partir de l’application Social Engagement.
- Noms d’utilisateur dans Power BI si votre organisation utilise le [pack de contenu Social Engagement](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/get-content-pack-for-power-bi) pour Power BI pour analyser les performances de l’équipe sur les médias sociaux.

Cette première étape consistant à rechercher et à réviser les données à caractère personnel en question vous permet de déterminer si une demande de personne concernée répond aux besoins de votre organisation en matière de respect ou de refus de celle-ci. Par exemple, après avoir trouvé et consulté les données à caractère personnel , vous pouvez déterminer si la demande ne respecte pas les exigences de votre organisation, car cela peut nuire aux droits et libertés d’autres personnes.

#### <a name="social-media-users-authors"></a>Utilisateurs de réseaux sociaux (auteurs)

- Pour rechercher leurs données personnelles, suivez les quatre premières étapes de la section [Rechercher et supprimer un auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-authors#find-and-delete-an-author).
- Les employés peuvent créer des règles Social Engagement qui recherchent un certain contenu défini sur les plateformes sociales ; ces règles de recherche peuvent contenir des noms d’auteur. Pour être sûr de trouver ces règles, revoyez les règles de recherche de compte social pour le compte approprié ([Twitter](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/add-rules-search-topic#add-a-twitter-rule), [Instagram](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/add-rules-search-topic#add-an-instagram-rule) et [YouTube](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/add-rules-search-topic#add-a-includetnyoutubeincludestn-youtubemd-rule), par exemple).
- Pour rechercher les balises d’un auteur, commencez par [filtrer les posts](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/use-filters#add-edit-or-remove-a-filter) par [auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/understand-filters#authors), puis [affichez les balises d’auteur](https://go.microsoft.com/fwlink/?linkid=864795).

##### <a name="your-employees"></a>Vos employés

Pour trouver :

- Un profil utilisateur, accédez au [Centre d’administration](https://portal.office.com/adminportal/home). Dans le **Centre d’administration**, sélectionnez **Utilisateurs**. Dans la page **Utilisateurs actifs**, recherchez l’utilisateur dans la liste. Dans Social Engagement, accédez à **Paramètres \> Gestion des utilisateurs** pour afficher les informations synchronisées automatiquement à partir d’Office 365.
- le destinataire d’une alerte, suivez les deux premières étapes de la section [Gérer les destinataires d’alerte en tant qu’administrateur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#manage-alert-recipients-as-administrator).
- des données de profils sociaux entrées par des employés, accédez à **Paramètres \> Profils sociaux**. (Pour plus d’informations, consultez la section [Gérer les profils sociaux](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-social-profiles).)
- des noms d’utilisateur dans Power BI, ouvrez le tableau de bord Power BI de Social Engagement et filtrez par nom d’employé.

### <a name="providing-a-copy-of-personal-data"></a>Fourniture d’une copie des données personnelles

Le RGPD donne aux personnes concernées le droit d’obtenir une copie de leurs données personnelles sur demande. Une fois que vous avez trouvé le contenu client avec les données pouvant répondre à la demande, vous et votre organisation devez décider de fournir ou non une copie à la personne concernée.

#### <a name="social-media-users-authors"></a>Utilisateurs de réseaux sociaux (auteurs)

- Pour exporter des données personnelles d’auteurs, suivez les étapes de la section [Exporter des informations d’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-authors#export-author-information) pour exporter les données vers un fichier Excel.
- Pour extraire les balises d’auteur qui ont été ajoutées à un auteur spécifique, vous pouvez [exporter les données de balise d’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/author-tags#export-author-tags-data).

##### <a name="your-employees"></a>Vos employés

Pour exporter :

- Des données client à partir de profils utilisateur, accédez au [Centre d’administration](https://portal.office.com/adminportal/home). Dans le **Centre d’administration**, sélectionnez **Utilisateurs**. Dans la page **Utilisateurs actifs**, recherchez l’utilisateur dont vous voulez exporter les données. Supprimez tous les utilisateurs à l’exception de l’utilisateur cible, puis sélectionnez **Exporter** pour exporter les données dans un fichier .csv, que vous pourrez consulter dans Excel.
- Les adresses e-mail des destinataires d’une alerte (les seules données client présentes dans une alerte). Suivez les étapes dans [Gérer les destinataires d’alerte en tant qu’administrateur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#manage-alert-recipients-as-administrator). Sélectionnez ensuite **Exporter** pour télécharger une liste Excel des alertes qui incluent ce destinataire.
- Noms d’utilisateur de Power BI : [Engagement reporting](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/get-content-pack-for-power-bi) affiche les noms d’utilisateur dans les rapports de performances de l’équipe sur les réseaux sociaux. Pour exporter ces données, filtrez par utilisateur dans le tableau de bord PowerBI ou par [rapport](https://docs.microsoft.com/power-bi/power-bi-report-add-filter), et [exportez les données](https://docs.microsoft.com/power-bi/power-bi-visualization-export-data).

### <a name="rectifying-personal-data"></a>Rectification des données personnelles

Pour corriger des données personnelles inexactes ou incomplètes :

#### <a name="social-media-users-authors"></a>Utilisateurs de réseaux sociaux (auteurs)

- Vous devez demander au propriétaire des données (auteur) d’effectuer le changement sur la plateforme sociale (par exemple, Twitter, WordPress ou Tumblr). La personne concernée détient les données dans le compte du réseau social et par conséquent, elle est la seule personne à pouvoir les modifier. Dès lors que l’auteur effectue le changement, Social Engagement synchronise automatiquement les détails modifiés.
- des balises d’auteur, suivez les étapes de la section [Modifier des balises d’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/author-tags#change-author-tags).

##### <a name="your-employees"></a>Vos employés

- Profils utilisateur : pour apporter des modifications aux données client dans un profil utilisateur, consultez [Modifier un nom d’utilisateur et une adresse e-mail dans Office 365](https://support.office.com/article/change-a-user-name-and-email-address-in-office-365-fb5ac074-e203-4e1f-9843-b9d1a3e03297) et [Ajouter votre photo de profil dans Office 365](https://support.office.com/article/add-your-profile-photo-to-office-365-2eaf93fd-b3f1-43b9-9cdc-bdcd548435b7). Ces modifications sont synchronisées automatiquement dans Engagement social. Pour les trouver, accédez à **Paramètres** \> **Gestion des utilisateurs**.

- Destinataires d’alerte : vous pouvez [modifier une alerte](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#change-an-alert).

### <a name="restricting-the-processing-of-personal-data"></a>Restriction du traitement des données personnelles

#### <a name="social-media-users-authors"></a>Utilisateurs de réseaux sociaux (auteurs)

Pour arrêter le traitement des données client d’un auteur dans Social Engagement, [supprimez l’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-authors#delete-an-author).

Cela bloquera le futur traitement des données de cette personne concernée et tous les futurs posts et supprimera aussi toutes les données concernant cet auteur et créées par lui. Chaque fois que Social Engagement acquiert de nouveaux posts, il vérifie automatiquement si l’auteur a été supprimé précédemment et rejette les posts des auteurs supprimés. Cela n’a aucun effet sur le compte de l’utilisateur sur la plateforme sociale.

##### <a name="your-employees"></a>Vos employés

- Pour arrêter le traitement des données client d’employés, vous pouvez [supprimer leur licence](https://support.office.com/article/remove-licenses-from-users-in-office-365-for-business-9b497c85-d0a4-4735-80fa-d3565bc05bd1) dans Office 365. Cela a pour effet de supprimer tous les éléments en rapport avec Social Engagement comme les rôles et les profils utilisateur, tous les paramètres personnalisés définis par l’utilisateur, les alertes, les cartes d’activités et les flux associés. Les rubriques de recherche et les profils sociaux ne sont pas supprimés ; cependant, les administrateurs héritent de la propriété des profils sociaux des utilisateurs supprimés et peuvent les supprimer sur demande.
- Pour limiter l’envoi d’e-mails d’alerte, vous pouvez supprimer une adresse e-mail de toutes les alertes auxquelles elle a été ajoutée en suivant les étapes décrites dans la section [Gérer les destinataires d’alerte en tant qu’administrateur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#manage-alert-recipients-as-administrator).

### <a name="deleting-personal-data"></a>Suppression de données personnelles

Le RGPD donne aux personnes concernées le droit de demander au contrôleur de supprimer des données personnelles dans certaines circonstances. Le « droit à l’oubli » en supprimant ces données d’une organisation est une protection clé dans le RGPD.

#### <a name="social-media-users-authors"></a>Utilisateurs de réseaux sociaux (auteurs)

Pour supprimer définitivement l’ensemble des données personnelles d’un auteur dans Social Engagement, supprimez le profil social complet de cet auteur. Consultez la section [](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-authors)[Supprimer un auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-authors#delete-an-author).  

Cette action est définitive. Elle supprimera toutes les données concernant cet auteur et créées par lui sur Social Engagement et bloquera le futur traitement de ses données et tous ses futurs posts. Lorsque Social Engagement acquiert de nouveaux posts, il vérifie automatiquement si l’auteur a été supprimé précédemment et rejette les posts des auteurs supprimés. Cela n’a aucun effet sur le compte de l’utilisateur sur la plateforme sociale.

Pour supprimer des balises d’auteur, consultez la section [Supprimer des balises d’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/author-tags#remove-author-tags).

>[!NOTE]
>Si vous êtes invité à supprimer des informations concernant un auteur spécifique, nous vous recommandons de commencer par vérifier l’identité de cette personne pour valider la demande. Pour vérifier l’identité, vous pouvez demander à l’auteur de vous envoyer un message privé à partir de son compte de réseau social.

Social Engagement a implémenté des flux de conformité à partir de plusieurs plateformes sociales (par exemple, Twitter, WordPress, Tumblr) pour agir sur des signaux comme les suppressions de posts déclenchés directement sur les plateformes sociales. Cette fonctionnalité est activée automatiquement avec chaque installation de Social Engagement et ne requiert pas l’interaction de l’utilisateur. En outre, Social Engagement fournit un mécanisme qui permet aux services (comme Dynamics 365 for Customer Engagement, par exemple) qui créent du contenu social de Social Engagement d’hériter de ces signaux.

##### <a name="your-employees"></a>Vos employés

Pour supprimer définitivement toutes les données client d’un employé, vous pouvez [supprimer sa licence](https://support.office.com/article/remove-licenses-from-users-in-office-365-for-business-9b497c85-d0a4-4735-80fa-d3565bc05bd1) dans Office 365.

- Cela supprime tous les éléments liés à Social Engagement tels que les rôles et les profils utilisateur, tous les paramètres personnalisés définis par l’utilisateur associés, les alertes, les cartes d’activités et les flux. Les rubriques de recherche et les profils sociaux ne sont pas supprimés. (Les administrateurs héritent de la propriété des profils sociaux des utilisateurs supprimés et peuvent les supprimer sur demande.)
- Ces modifications sont synchronisées automatiquement dans Social Engagement. Pour les rechercher, accédez à **Paramètres \> Gestion des utilisateurs**.
- Les entrées d’un employé dans un rapport d’engagement PowerBI sont rendues anonymes lors de la suppression de ses données personnelles.

Vous pouvez [supprimer un profil social](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-social-profiles#delete-a-social-profile).

Pour supprimer une adresse e-mail dans toutes les alertes auxquelles elle a été ajoutée, suivez les étapes de la section [Gérer les destinataires d’alerte en tant qu’administrateur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#manage-alert-recipients-as-administrator).[](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#manage-alert-recipients-as-administrator)

### <a name="exporting-personal-data"></a>Exportation de données personnelles

Vous pouvez fournir aux personnes concernées leurs données personnelles dans un format électronique.

#### <a name="social-media-users-authors"></a>Utilisateurs de réseaux sociaux (auteurs)

Pour exporter les données personnelles d’auteurs, suivez les étapes de la section [Exporter des informations d’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/manage-authors#export-author-information) pour exporter les données vers un fichier Excel.

Pour extraire les balises d’auteur qui ont été ajoutées à un auteur spécifique, vous pouvez [exporter les données de balise d’auteur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/author-tags#export-author-tags-data).

##### <a name="your-employees"></a>Vos employés

Pour exporter :

- Des données client à partir de profils utilisateur, accédez au [Centre d’administration](https://portal.office.com/adminportal/home). Dans le **Centre d’administration**, sélectionnez **Utilisateurs**. Dans la page **Utilisateurs actifs**, recherchez l’utilisateur dont vous voulez exporter les données. Supprimez tous les utilisateurs à l’exception de l’utilisateur cible, puis sélectionnez **Exporter** pour exporter les données dans un fichier .csv, que vous pourrez consulter dans Excel.
- les adresses e-mail d’un destinataire d’alerte (les seules données personnelles dans une alerte), suivez les étapes de la section [Gérer les destinataires d’alerte en tant qu’administrateur](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/email-alerts#manage-alert-recipients-as-administrator). Sélectionnez ensuite **Exporter** pour télécharger une liste Excel des alertes qui inclut ce destinataire.
- Noms d’utilisateur de Power BI : [Engagement reporting](https://docs.microsoft.com/dynamics365/customer-engagement/social-engagement/get-content-pack-for-power-bi) affiche les noms d’utilisateur dans les rapports de performances de l’équipe sur les réseaux sociaux. Pour exporter ces données, filtrez par utilisateur dans le tableau de bord PowerBI ou par [rapport](https://docs.microsoft.com/power-bi/power-bi-report-add-filter), et [exportez les données](https://docs.microsoft.com/power-bi/power-bi-visualization-export-data)

## <a name="part-2-responding-to-dsrs-for-system-generated-logs"></a>Partie 2 : Répondre à des DSR pour les journaux générés par le système

Microsoft permet également de consulter, d’exporter et de supprimer les journaux générés par le système qui peuvent être considérés comme personnels en vertu de la définition large des « données personnelles » du RGPD. Voici des exemples de journaux générés par le système qui peuvent être considérés comme personnels en vertu du RGPD :

- Données relatives à l’utilisation de produits et de services tels que les journaux d’activité des utilisateurs
- Requêtes de recherche et données de requête des utilisateurs
- Données générées par les produits et services comme étant un produit des fonctionnalités du système et de l’interaction par les utilisateurs ou d’autres systèmes

Notez qu’il n’est pas possible de limiter ni de rectifier les données contenues dans des journaux générés par le système. Les données contenues dans des journaux générés par le système forment des actions factuelles effectuées dans le cloud Microsoft et les données de diagnostic, et des modifications apportées à ces données compromettraient l’enregistrement historique des actions, augmentant ainsi les risques de fraude et de sécurité.

### <a name="accessing-and-exporting-system-generated-logs"></a>Consultation et exportation des journaux générés par le système

Les administrateurs peuvent accéder aux journaux générés par le système associés à une utilisation particulière d’un utilisateur des applications et des services Dynamics 365. Pour accéder aux journaux générés par le système et les exporter, procédez comme suit :

1. Accédez au [portail d’approbation de service Microsoft](https://servicetrust.microsoft.com/) et connectez-vous en utilisant les identifiants d’un administrateur général Dynamics 365.
2. Dans la liste déroulante **Confidentialité** en haut de la page, cliquez sur **Demande des personnes concernées**.
3. Dans la page **Demande des personnes concernées**, sous **Journaux générés par le système**, cliquez sur **Exportation des journaux de données**.
    > [!NOTE]
    > L’**Exportation des journaux de données** s’affiche. Notez que la liste des demandes de données d’exportation transmises par votre organisation s’affiche.
4. Pour créer une demande pour un utilisateur, cliquez sur **Créer une demande de données d’exportation**.

Une fois la demande créée, elle apparaît sur la page **Exportation des journaux de données** où vous pouvez suivre son statut. Lorsqu’une demande est terminée, vous pouvez cliquer sur un lien pour accéder aux journaux générés par le système qui sont exportés vers l’emplacement de stockage Azure de votre organisation dans les 30 jours suivant la création de la demande. Les données sont enregistrées dans un format de fichier courant lisible par une machine tel que JSON ou XML. Si vous n’avez pas de compte Azure ni d’emplacement de stockage Azure, vous devez créer un compte Azure ou un emplacement de stockage Azure pour votre organisation de sorte que l’outil Exportation des journaux de données puisse exporter les journaux générés par le système. 

Azure prend cela en charge en permettant à votre organisation d’exporter les données au format JSON natif vers votre conteneur de stockage Azure spécifié[. Article de présentation du Stockage Microsoft Azure – Stockage Blob](https://docs.microsoft.com/azure/storage/common/storage-introduction#blob-storage).

> [!IMPORTANT]
> Pour exporter des données utilisateur à partir du client, vous devez être un administrateur client.

Le tableau suivant récapitule la consultation et l’exportation des journaux générés par le système :

| | |
|:----|:---|
| | |
|**Combien de temps faut-il à l’outil Exportation des journaux de données de Microsoft pour exécuter une demande ?**| Cela peut dépendre de plusieurs facteurs. Dans la plupart des cas, il nécessite un ou deux jours, mais cela peut prendre jusqu’à 30 jours. |
|**Quel est le format de sortie ?**| La sortie sera structurée sous forme de fichiers lisibles par une machine, comme XML, CSV ou JSON. |
|**Quelles données l’outil d’exportation des journaux de données renvoie-t-il ?**| L’outil Exportation des journaux de données renvoie les journaux générés par le système que Microsoft stocke. Les données exportées englobent différents services Microsoft, dont Office 365, Azure et Dynamics. |
|***Qui a accès à l’outil Exportation des journaux de données pour demander l’accès à des journaux générés par le système ?**| Les administrateurs généraux Dynamics 365 auront accès à l’utilitaire du gestionnaire des journaux du RGPD. |
|**Comment les données sont-elles renvoyées à l’utilisateur ?**| Les données sont exportées vers l’emplacement de stockage Azure de votre organisation. Les administrateurs de votre organisation doivent ensuite déterminer comment ils souhaitent afficher/renvoyer ces données aux utilisateurs. |
|**À quoi ressemblent les données dans les journaux générés par le système ?**| Exemple d’enregistrement de journal généré par le système au format JSON : <br><br> "DateTime": "2017-04-28T12:09:29-07:00", <br> "AppName": "SharePoint", <br> "Action": "OpenFile", <br> "IP": "154.192.13.131", <br> "DevicePlatform": "Windows 1.0.1607" |

> [!NOTE]
> Certaines fonctionnalités empêchent d’exporter ou de supprimer des journaux générés par le système contenant des informations personnelles afin de préserver l’intégrité de ces informations pour des raisons de sécurité et d’audit.

### <a name="deleting-system-generated-logs"></a>Suppression des journaux générés par le système

Pour supprimer des journaux générés par le système et récupérés via une demande d’accès, vous devez supprimer l’utilisateur du service et supprimer définitivement son compte Azure Active Directory. Pour obtenir des instructions sur comment supprimer définitivement un utilisateur, consultez la section [Suppression d’un utilisateur](https://microsoft-my.sharepoint.com/personal/kated_microsoft_com/Documents/DSR%20Guide%20v4%20-(newly%20created%20for%20O365%20only).docx#_Deleting_a_user) de ce guide. Il est important de noter que la suppression définitive d’un compte d’utilisateur est irréversible une fois amorcée.

La suppression définitive d’un compte d’utilisateur supprimera les données de l’utilisateur des journaux générés par le système pour pratiquement tous les services Dynamics 365 dans un délai de 30 jours.

## <a name="learn-more"></a>En savoir plus

- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/en-us/TrustCenter/Privacy/gdpr/default.aspx)
