---
title: Vue d’ensemble et définitions
description: En savoir plus sur Data Residency fonctionnalité Vue d’ensemble et définitions
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: c73910350027ff90fa54208e4e11c53b04538969
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805575"
---
# <a name="overview-and-definitions"></a>Vue d’ensemble et définitions

## <a name="definitions"></a>Définitions

Pour clarifier les descriptions ci-dessous sur les fonctionnalités et le comportement de résidence des données, il est nécessaire d’avoir des termes et des définitions clairs afin de mieux comprendre les fonctionnalités que Microsoft fournit dans ce domaine.

**Tableau 1 : Définitions et termes**

| **Terme** | **Définition** |
|:-----|:-----|
|Zone géographique de la macro  <br/> |Macro Region Geography 1 – EMEA, Macro Region Geography – Asie-Pacifique, Macro Region Geography – Amériques  <br/> |
|Macro Region Geography 1 - EMEA  <br/> |Centres de données en Autriche, Finlande, France, Irlande, Pays-Bas, Suède  <br/> |
|Macro-région Géographie 2 - Asie-Pacifique  <br/> |Centres de données à Hong Kong, Japon, Malaisie, Singapour, Corée du Sud  <br/> |
|Macro Region Geography 3 - Amériques  <br/> |Centres de données au Brésil, au Chili, États-Unis  <br/> |
|Géographie de la région locale  <br/> |Australie, Brésil, Canada, France, Allemagne, Inde, Japon, Qatar, Corée du Sud, Norvège, Afrique du Sud, Suède, Suisse, Émirats arabes unis, Royaume-Uni  <br/> |
|Zone géographique de la région locale étendue  <br/> |Pologne, Italie, Indonésie, Israël, Espagne, Mexique, Malaisie, Autriche, Chili, Nouvelle-Zélande, Danemark, Grèce, Taïwan  <br/> |
|Géographie  <br/> |_Région locale Géographie, Région locale développée Géographie_ ou _Macro Région Géographique_  <br/> |
|Géographie satellite  <br/> |Si un client s’abonne au service multigéographique, il peut entraîner le stockage des données client utilisateur définies dans d’autres zones géographiques en dehors de la zone _géographique approvisionnée_ principale du _locataire_  <br/> |
|Aad  <br/> |Azure Active Directory  <br/> |
|Tenant  <br/> |Un _locataire_ représente une organisation dans Azure Active Directory. Il s’agit d’une instance de service Azure AD réservée qu’une organisation reçoit et possède lorsqu’elle s’inscrit à un service cloud Microsoft tel qu’Azure ou Microsoft 365. Chaque _locataire_ Azure AD est distinct et distinct des autres _locataires_ Azure AD  <br/> |
|Géographie par défaut  <br/> |Lorsqu’un _locataire AAD_ est créé, un pays est fourni par le client pendant le processus d’inscription.  Ce pays détermine la zone géographique par défaut pour tous les services Microsoft 365.  Dans certains cas, tous les services ne sont pas en mesure de provisionner dans cette zone _géographique par défaut_ unique. Pour obtenir une description, consultez _Mappage d’approvisionnement du service Microsoft 365_ ci-dessous.  <br/> |
|Mappage d’approvisionnement du service Microsoft 365  <br/> |Tous les services Microsoft 365 utilisent la _zone géographique par défaut_ pour déterminer où les données spécifiées _d’un locataire_ donné seront approvisionnées et stockées.  <br/> |
|Mappage du pays d’approvisionnement du service Microsoft 365  <br/> |Reportez-vous aux [mappages de données](https://aka.ms/datamaps) pour savoir où un service donné provisionnera les données client spécifiées, en fonction de la _zone géographique par défaut du locataire._  <br/> |
|Géographie approvisionnée principale  <br/> |Un service Microsoft 365 donné utilise la _zone géographique par défaut du locataire_ combinée au _mappage de pays d’approvisionnement du service Microsoft 365_ pour déterminer dans quelle _zone géographique_ approvisionner les données client.   <br/> |
|Emplacement des données du centre de Administration Microsoft 365  <br/> |Pour afficher la _zone géographique approvisionnée principale_ pour Exchange Online, SharePoint Online et Microsoft Teams, reportez-vous à Office 365 Admin Center dans Paramètres . Paramètres de l’organisation ; Profil de l’organisation ; Carte d’emplacement des données.  <br/> |
|Fonctionnalités multigéographiques de Microsoft 365  <br/> |Les fonctionnalités multigéographiques de Microsoft 365 permettent à un seul _locataire_ de stocker les données client au repos dans plusieurs zones géographiques plutôt que d’être limité à la zone _géographique approvisionnée principale_ unique. Pour plus d’informations, consultez la description multigéographique.  <br/> |
|Preferred Data Location (PDL)  <br/> |Utilisé pour _les locataires_ avec un abonnement multigéographique.  Propriété définie par l’administrateur qui indique où les données de l’utilisateur ou de la ressource partagée doivent être stockées au repos.  Pour plus d’informations, consultez la description multigéographique.  <br/> |
|Advanced Data Residency (ADR)  <br/> |Nouveau service complémentaire Microsoft 365 qui garantit la résidence des données client pour un ensemble défini de services. Voir la section 3  <br/> |
|Conditions du produit de confidentialité et de sécurité  <br/> |Les conditions de confidentialité et de sécurité des services Microsoft 365 fournissent certains engagements liés à l’emplacement des données client.  Le document est disponible <a href="https://www.microsoft.com/licensing/terms/en-US/product/PrivacyandSecurityTerms/EAEAS" target="_blank">ici</a>. L’extrait de la section pertinente (le 1er novembre 2022) est :<br>**Office 365 Services.** Si le Client approvisionne son _Locataire_ en Australie, au Brésil, au Canada, dans l’Union européenne, en France, en Allemagne, en Inde, au Japon, en Norvège, au Qatar, en Afrique du Sud, en Corée du Sud, en Suède, en Suisse, au Royaume-Uni, aux Émirats arabes unis ou dans le États-Unis, Microsoft stocke les données client suivantes au repos uniquement dans cette zone géographique : (1) Exchange Online  contenu de boîte aux lettres (corps du courrier électronique, entrées de calendrier et contenu des pièces jointes de courrier électronique), (2) contenu du site SharePoint Online et les fichiers stockés dans ce site, (3) fichiers chargés sur OneDrive Entreprise et (4) messages de conversation Microsoft Teams (y compris les messages privés, les messages de canal, les messages de réunion et les images utilisés dans les conversations) et pour les clients utilisant Microsoft Stream  (sur SharePoint), enregistrements de réunion.
|Charges de travail  <br/> |Souvent utilisé pour faire référence à un service Microsoft 365 tel que, mais sans s’y limiter, Exchange Online, SharePoint Online, Microsoft Teams, etc.|

## <a name="overview-of-data-residency"></a>Vue d’ensemble de Data Residency

Les services cloud Microsoft 365 s’exécutent sur nos centres de données dans le monde entier et fournissent des services à des clients du monde entier.  Les données client peuvent être stockées dans plusieurs centres de données.  La résidence des données fait référence à l’emplacement géographique où les données client sont stockées au repos. La résidence des données est importante pour le gouvernement, le secteur public, l’éducation et les entités commerciales réglementées afin d’assurer la protection des informations personnelles et/ou sensibles.  Dans de nombreux pays, les clients sont censés se conformer aux lois, réglementations ou normes du secteur qui régissent explicitement l’emplacement du stockage des données.

Microsoft prend des décisions sur l’emplacement de stockage permanent des données client en fonction de deux facteurs :

1. _Géographie par défaut_ du _locataire_
1. Zones _géographiques_ disponibles pour un service donné

### <a name="_default-geography_-of-the-aad-_tenant_"></a>_Géographie par défaut_ du _locataire_ AAD

Lorsqu’un client crée un _locataire_ AAD, il entre dans un pays pendant le processus de création.  C’est ce pays qui définit la _zone géographique par défaut_ pour le _locataire_.  Il existe plusieurs chemins pour créer _des locataires_.  Ils peuvent être créés via des formulaires AAD, ils peuvent être créés lors de l’essai de nouveaux services Microsoft 365 (versions d’évaluation), etc.  Une fois qu’un _locataire_ est créé, la _zone géographique par défaut_ ne peut pas être modifiée.

### <a name="available-geographies-for-a-given-service"></a>Zones géographiques disponibles pour un service donné

Les services Microsoft 365 ne sont pas déployés dans tous les centres de données Microsoft à l’échelle mondiale.  Les services plus volumineux, tels que Exchange Online, SharePoint Online et Microsoft Teams, sont déployés universellement dans toutes les _zones géographiques_.   D’autres services décident où déployer leurs services en fonction du nombre de clients, des affiliations régionales et des architectures logicielles.  Lorsqu’un client utilise pour la première fois un service de cette catégorie, la logique d’approvisionnement utilise la _zone géographique par défaut_ et les _zones géographiques_ prises en charge pour déterminer où approvisionner un client donné.

Au fil du temps, un service particulier peut déployer son logiciel dans des _zones géographiques_ supplémentaires, de sorte que les emplacements d’approvisionnement des nouveaux clients peuvent changer au fil du temps, ce qui n’entraîne pas nécessairement le déplacement des données client vers une nouvelle _zone géographique_.

Pour comprendre où vos données sont stockées, pour un service donné, votre outil principal de compréhension se trouve dans le Centre de Administration _client_.  En tant qu’administrateur _client_, vous pouvez trouver l’emplacement réel des données en accédant à Administration->Paramètres->Paramètres de l’organisation->Profil de l’organisation->Emplacement des données.  Actuellement, l’emplacement des données est disponible pour Exchange Online, SharePoint Online et Microsoft Teams.  En plus de cette ressource, consultez la [page Data Maps](o365-data-locations.md).

Quelques exemples :

**Exemple 1 :** Pour un _locataire_ dont le pays d’inscription est « France » qui a un nouvel abonnement incluant Exchange Online, SharePoint Online et Microsoft Teams, les données client de ces services seront approvisionnées dans la zone géographique Français _région locale_. Pourquoi ?  Étant donné que ces services sont déployés dans le Français centres de données et que le _locataire_ a un pays d’inscription en France.

**Exemple 2 :**  Pour un _locataire_ dont le pays d’inscription est « Belgique » qui a un nouvel abonnement incluant Exchange Online, SharePoint Online et Microsoft Teams, les données client de ces services seront approvisionnées dans la _macro région Geography 1 – EMEA_.  Pourquoi ?  Parce qu’il n’y a pas de centres de données Microsoft 365 en Belgique et que la zone géographique la plus proche est _Macro Region Geography 1 - EMEA_.

**Exemple 3 :** Pour un _locataire_ dont le pays d’inscription est « Japon » qui dispose d’un nouvel abonnement incluant Microsoft Forms, les données client pour Forms seront approvisionnées dans la _macro région Géographie 3 - Amériques_.  Pourquoi ?  Étant donné que Forms est déployé uniquement dans _la macro région Geography 3 - Amériques_ et _macro région Geography 1 - EMEA_ ( _abonnés_ UE uniquement).

**Exemple 4a :** Pour un _locataire_ dont le pays d’inscription est « Suède » qui dispose d’un nouvel abonnement incluant Microsoft Yammer, les données client de Yammer seront approvisionnées dans la _macro région Geography 1 - EMEA_.  Pourquoi ?  Étant donné que Yammer est déployé dans _la macro région Geography 1,_ les locataires EMEA et Suédois sont mieux _servis_ à partir de cette _zone géographique_.

**Exemple 4b :** Pour un _locataire_ dont le pays d’inscription est « Suède » qui a un abonnement incluant Microsoft Yammer avant le déploiement de Yammer sur _Macro Regional Geography 1 - EMEA_, les données client pour Yammer se trouvent dans _Macro Region Geography 3 - Americas_.  Pourquoi ?  Car, à l’époque, Yammer n’avait qu’un seul déploiement pour tous les clients à ce _moment-là dans macro région Géographie 3 - Amériques_.

### <a name="migrationsmoves"></a>Migrations/déplacements

Une fois qu’un service Microsoft 365 provisionne un _locataire_ dans une _zone géographique_ particulière, il existe cinq façons de déplacer ces données vers une autre _zone géographique_ :

1. Le service Microsoft 365 décide de déplacer les données vers une nouvelle _zone géographique_ pour des raisons d’opérations de service, s’il n’existe aucune autre stratégie en place pour empêcher le déplacement.
1. Pour _les zones géographiques locales_ qui ont des centres de données Microsoft et pour _les locataires_ qui ont le même pays, il existe des options pour migrer des données des _zones géographiques régionales_ vers les _zones géographiques locales_.  Cette option n’est généralement disponible que pendant 6 mois après l’établissement d’une _zone géographique de région_ locale.
1. Si un _locataire_ s’abonne au service _multigéographique_, les données utilisateur des _locataires_ pour Exchange Online, SharePoint Online et Microsoft Teams peuvent être affectées à _des zones géographiques satellites_.
1. Si un _locataire_ a inscrit un pays en tant que _région locale geography_ ou _région locale étendue geography_ et a un abonnement au module complémentaire _du service Advanced Data Residency_, les données de _locataire_ pour les services inclus sont migrées de la _zone géographique régionale_ vers la _zone géographique de la région locale_ appropriée.
1. Parfois, Microsoft rouvre l’option Migration de _la zone géographique régionale_ vers les _zones géographiques locales_ ou les _zones géographiques locales étendues concernées_.

### <a name="durable-commitments-on-data-location"></a>Engagements durables sur l’emplacement des données

Il existe trois méthodes pour s’assurer que l’emplacement des données _client_ d’un service particulier ne change pas.

1. Conditions du produit : Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams approvisionnés dans n’importe quelle _région géographique_ locale, l’Union européenne ou l’États-Unis ont un engagement pour la résidence des données client exprimé dans les [Conditions du produit](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all).  Pour plus d’informations, consultez la [page d’Data Residency Conditions du produit](m365-dr-product-terms-dr.md).
1. _Abonnement multigéographique_ : permet aux clients d’attribuer l’emplacement des données pour Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams à n’importe quelle _zone géographique_ prise en charge.  Pour plus d’informations, consultez [Multi Geo Data Residency](microsoft-365-multi-geo.md).
1. _L’abonnement advanced Data Residency_ garantit la résidence des données pour un ensemble étendu de services Microsoft 365 dans une _zone géographique_ ou une _zone géographique de région locale étendue_.  Pour plus d’informations, consultez la [page Data Residency avancé](advanced-data-residency.md).

**Tableau 2 : Data Residency disponibles par charge de travail**

|**Nom du service**|**Conditions du produit**|**Multi-Géo**|**Adr**|
|:-----|:-----|:-----|:-----|
|Exchange Online <br/> |X<sup>1</sup>  <br/> |X<sup>2</sup>  <br/> |X<sup>3</sup>  <br/> |
| SharePoint Online / OneDrive Entreprise <br/> |X<sup>1</sup>  <br/> |X<sup>2</sup>  <br/> |X<sup>2</sup>  <br/> |
| Microsoft Teams <br/> |X<sup>1</sup>  <br/> |X<sup>2</sup>  <br/> |X<sup>2</sup>  <br/> |
| Microsoft Defender pour Office P1 <br/> |-  <br/> |-  <br/> |X<sup>2</sup>  <br/> |
| Office pour le web <br/> |-  <br/> |-  <br/> |X<sup>2</sup>  <br/> |
| Viva Connections <br/> |-  <br/> |-  <br/> |X<sup>2</sup>  <br/> |
| Sujets Viva <br/> |-  <br/> |-  <br/> |X<sup>2</sup>  <br/> |
| Microsoft Purview <br/> |-  <br/> |-  <br/> |X<sup>2</sup>  <br/> |

1. Disponible uniquement pour _les pays géographiques de la région locale_, l’Union européenne et le États-Unis.
1. Disponible dans _Région locale Géographie_, _Région locale étendue Géographie_ et _Régions géographiques régionales_
1. Disponible uniquement pour _les régions locales Géographie_ et _Région locale étendue Pays géographiques_ .

>[!NOTE]
>Pour plus d’informations sur ces rubriques, consultez la [section Fonctionnalités de Data Residency](m365-dr-workload-exo.md) de la charge de travail.

**Tableau 3 : Data Residency disponibles par pays**

| Pays    | Exchange Online  | SharePoint Online  | Teams  | MDO P1  | Office pour le web  | Viva Connections  | Sujets Viva  |  Compétence  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Australie  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Brésil  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Canada  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Union européenne  | P-M  | P-M  | P-M  | -  | -  | -  | -  | -  |
| France  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Allemagne  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Inde  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Japon  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Qatar  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Corée du Sud  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Norvège  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Afrique du Sud  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Suède  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Suisse  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Émirats arabes unis  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| Royaume-Uni  | P-M-A  | P-M-A  | P-M-A  | A  | A  | A  | A  | A  |
| États-Unis  | P-M  | P-M  | P-M  | -  | -  | -  | -  | -  |

P : Conditions du produit Data Residency<br>
M : Data Residency multigéographiques<br>
R : Data Residency avancé

### <a name="countryregion-specific-data-center-city-locations"></a>Pays/région des emplacements urbains précis des centres de données

Les zones géographiques régionales suivantes peuvent stocker des données au repos.

**Tableau 4 : Zones géographiques régionales**

|**Zones géographiques régionales** |**Emplacements pouvant stocker des données client**  |
|---------|---------|
|Macro Region Geography 1 - EMEA (Europe, Moyen-Orient et Afrique) |  Autriche, Finlande, France, Irlande, Pays-Bas, Suède  |
|Macro-région Géographie 2 - Asie-Pacifique |  Hong Kong, Japon, Malaisie, Singapour, Corée du Sud  |
|Macro Region Geography 3 - Amériques | Brésil, Chili, États-Unis  |

**Tableau 5 : Zones géographiques locales actuelles et emplacements des centres de données spécifiques à la région**

|Pays |Emplacement du centre de données  |
|---------|---------|
|Australie   |Sydney, Melbourne   |
|Brésil   |Rio, Campinas   |
|Canada      |Ville de Québec, Toronto    |
|Union européenne      |Autriche (Vienne), Finlande (Helsinki), France (Paris, Marseille), Irlande (Dublin), Pays-Bas (Amsterdam), Suède (Gvleä, Sandviken, Staffanstorp)     |
|France      |Paris, Marseille     |
|Allemagne     |Frankfort, Berlin       |
|Inde   |Chennai, Mumbai, Pune        |
|Japon     |Osaka, Tokyo      |
|Corée du Sud   |Busan, Séoul        |
|Norvège     |Oslo, Stavanger       |
|Qatar     |Doha          |
|Afrique du Sud       |Le Cap, Johannesburg        |
|Suède     |Gävle, Sandviken, Staffanstorp      |
|Suisse           |Genève, Zurich     |
|Émirats arabes unis    |Dubai, Abu Dhabi        |
|Royaume-Uni       |Durham, Londres, Cardiff      |
|États-Unis    |Boydton, Cheyenne, Chicago, Des Moines, Quincy, San Antonio, Santa Clara, San José       |

### <a name="faq"></a>Forum aux questions

#### <a name="how-does-microsoft-define-data"></a>Comment Microsoft définit-il des données ?
<details><summary>Cliquez pour développer</summary>

Passez en revue nos [définitions pour les différents types de données client](https://go.microsoft.com/fwlink/p/?linkid=864390) dans le Centre de gestion de la confidentialité Microsoft. Dans les [conditions de confidentialité & de sécurité](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all), Microsoft prend des engagements contractuels concernant les données client/vos données _client_ et utilisateur. Nous faisons référence aux données client comme étant les données client qui sont validées pour être stockées au repos uniquement dans la région _d’un locataire_ conformément aux [conditions de confidentialité & de sécurité](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all).

</details>

#### <a name="where-are-the-exact-addresses-of-the-data-centers"></a>Où se trouvent les adresses précises des centres de données ?

<details><summary>Cliquez pour développer</summary>

Microsoft ne dévoile pas les adresses précises de ses centres de données. Cette stratégie est mise en place pour contribuer à la sécurisation de nos centres de données. Toutefois, nous répertorions bel et bien les emplacements urbains. Pour en savoir plus, consultez le tableau 5 des emplacements des villes des [centres de données spécifiques au pays/](m365-dr-overview.md#countryregion-specific-data-center-city-locations) à la région sur la page Vue d’ensemble et définitions.

</details>

#### <a name="does-the-location-of-your-customer-data-have-a-direct-impact-on-your-end-users-experience"></a>L’emplacement de vos données client a-t-il une influence directe sur l’expérience de vos utilisateurs finaux ?
<details><summary>Cliquez pour développer</summary>

Les performances de Microsoft 365 ne sont pas simplement proportionnelles à la distance entre l’utilisateur _client_ et les emplacements du centre de données. Les investissements constants de Microsoft dans son réseau et son infrastructure cloud au niveau mondial, et l’architecture des services Microsoft 365 permettent aux utilisateurs de bénéficier d’une expérience unique et constante, indépendamment du lieu de stockage des données client au repos. Si vos utilisateurs rencontrent des problèmes de performance, il est conseillé de les résoudre de manière approfondie. Microsoft a publié des conseils aux clients Microsoft 365 pour planifier et optimiser les performances des utilisateurs finaux sur le [site web du Support Office](network-planning-and-performance.md).

</details>

#### <a name="how-does-microsoft-help-me-comply-with-my-national-regional-and-industry-specific-regulations"></a>Comment Microsoft m’aide-t-il à me conformer aux réglementations nationales, locales et sectorielles ?
<details><summary>Cliquez pour développer</summary>

Pour aider un _locataire_ à se conformer aux exigences nationales, régionales et sectorielles régissant la collecte et l’utilisation des données des individus, Microsoft 365 propose l’ensemble d’offres de conformité le plus complet de tous les fournisseurs de productivité cloud mondiaux. Veuillez consulter [nos offres de conformité](/compliance/regulatory/offering-home) et de plus amples détails dans la section [Microsoft Purview](https://go.microsoft.com/fwlink/p/?linkid=862317) du Centre de gestion de la confidentialité. En outre, certains plans Microsoft 365 offrent des solutions de conformité supplémentaires pour aider un _locataire_ à gérer ses données, à se conformer aux exigences légales et réglementaires et à surveiller les actions effectuées sur ses données.

</details>

#### <a name="who-can-access-your-data-and-according-to-what-rules"></a>Qui peut accéder à vos données et selon quelles règles ?
<details><summary>Cliquez pour développer</summary>

 Microsoft implémente des mesures fortes pour protéger les données client _d’un locataire_ contre tout accès ou utilisation inapproprié par des personnes non autorisées. Il s’agit notamment de restreindre l’accès par le personnel et les sous-traitants de Microsoft, et de scrupuleusement définir les conditions requises pour répondre aux demandes de gouvernements en matière de données client. Toutefois, vous pouvez accéder aux données client de votre locataire à tout moment et pour _n’importe_ quelle raison. D'autres informations sont disponibles dans le [Centre de gestion de la confidentialité Microsoft](https://go.microsoft.com/fwlink/p/?linkid=864392).

</details>

#### <a name="does-microsoft-access-your-data"></a>Microsoft a-t-il accès à vos données ?
<details><summary>Cliquez pour développer</summary>

Microsoft automatise la plupart des opérations Microsoft 365 tout en limitant son propre accès aux données client. Ceci permet de gérer Microsoft 365 à grande échelle et de remédier aux risques de menaces internes vis-à-vis des données client. Par défaut, les ingénieurs Microsoft ne disposent pas de privilège administratif permanent ni d'accès permanent aux données du client dans Microsoft 365. Un ingénieur Microsoft peut disposer d’un accès limité et journalisé aux données client pendant une certaine durée, mais uniquement lorsque des opérations de service habituelles l'exigent et avec l'accord d'un membre de l'équipe de direction de Microsoft (et pour des clients disposant d’une licence pour la fonctionnalité Customer Lockbox par client).

</details>

#### <a name="how-does-microsoft-secure-your-data"></a>Comment Microsoft protège-t-il vos données ?
<details><summary>Cliquez pour développer</summary>

Microsoft dispose de solides stratégies, contrôles et systèmes intégrés dans Microsoft 365 vous permettant de garantir la sécurité de vos informations. Pour plus d’informations, consultez la [rubrique sécurité Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=864393) dans le Centre de gestion de la confidentialité Microsoft.

</details>

#### <a name="does-microsoft-365-encrypt-your-data"></a>Est-ce que Microsoft 365 chiffrer vos données ?
<details><summary>Cliquez pour développer</summary>

Microsoft 365 utilise des technologies côté service qui chiffrent les données client au repos et en transit. Pour les données client au repos, Microsoft 365 utilise le chiffrement au niveau du volume et au niveau des fichiers. Pour les données client en transit, Microsoft 365 utilise de nombreuses technologies de chiffrement pour la communication des centres de données, et entre les clients et les serveurs, tels que les protocoles TLS (Transport Layer Security) et IPsec (Internet Protocol Security). Microsoft 365 intègre également des fonctionnalités de chiffrement gérées par le client.

</details>

#### <a name="where-can-i-find-data-residency-information-for-microsoft-azure"></a>Où puis-je trouver des informations en matière de résidence des données pour Microsoft Azure ?
<details><summary>Cliquez pour développer</summary>

Consultez la page [Produits disponibles par région](https://go.microsoft.com/fwlink/p/?linkid=2093451) pour trouver des informations sur la résidence des données Microsoft Azure.

</details>

#### <a name="why-do-i-see-my-microsoft-365-service-requests-for-my-data-at-rest-connecting-to-servers-in-countries-outside-of-my-region"></a>Pourquoi est-ce que je vois mes demandes de service Microsoft 365 pour mes données au repos se connecter à des serveurs dans des pays en dehors de ma région ?
<details><summary>Cliquez pour développer</summary>

Parfois, une demande client peut être gérée par des serveurs situés dans une région différente de l’emplacement où les données client _d’un client_ sont stockées au repos. Cela peut se produire lorsque les décisions de routage réseau choisissent un autre serveur pour le traitement de la demande, mais dans ce cas, les données client _du locataire ne_ sont pas déplacées vers un nouvel emplacement au repos.

</details>
