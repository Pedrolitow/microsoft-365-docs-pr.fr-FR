---
title: Data Residency pour d’autres services Microsoft 365
description: En savoir plus sur Data Residency pour d’autres services Microsoft 365
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
ms.openlocfilehash: 0c8cb3f31d2b4a553c190cd384978d30d7802ec4
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805565"
---
# <a name="data-residency-for-other-microsoft-365-services"></a>Data Residency pour d’autres services Microsoft 365

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

Utilisez les conseils suivants pour déterminer l’emplacement de vos données. Veuillez référencer la _géographie par défaut de_ votre _locataire_.

### <a name="azure-active-directory-aad"></a>Azure Active Directory (AAD)

Reportez-vous à [Emplacements de données Azure Active Directory](https://aka.ms/aaddatamap).

### <a name="forms"></a>Formulaires
Les locataires des pays membres de l’UE conservent les données dans _la macro région Géographie 1 – EMEA_. Tous les autres locataires ont des données client stockées dans le États-Unis.

### <a name="intune"></a>Intune
Reportez-vous à endpoint.microsoft.com | d’administration des locataires État du locataire pour les locataires existants. Si vous n’avez pas de locataire existant, créez un locataire d’évaluation et approvisionnez Intune.

- Microsoft ne stocke pas les données clientes Intune au repos en dehors de la zone géographique indiquée. sauf si :
- Il est nécessaire pour Microsoft de fournir un support technique, de résoudre les problèmes de service ou de respecter les exigences légales.
- Le client configure un compte afin d’autoriser le stockage des données client, y compris en utilisant les éléments suivants :
- Fonctionnalités conçues pour fonctionner globalement, telles que le réseau de distribution de contenu (CDN), qui fournit un service de mise en cache global et qui stocke les données client à des emplacements géographiques dans le monde entier.
- Pour Azure Active Directory : reportez-vous à [Emplacements de données Azure Active Directory](https://aka.ms/aaddatamap).
- Version d’évaluation, bêta ou autres services de mise à jour, qui stockent généralement les données client aux États-Unis, mais peuvent les stocker dans le monde entier. Quoi qu’il en soit, Microsoft ne contrôle pas ou ne limite pas la géolocalisation à partir de laquelle les clients ou les utilisateurs finaux peuvent accéder aux données des clients. De même, lorsque les données des clients d'autres services sont ensuite intégrées dans Intune, les données des clients d'origine continueront d'être stockées sous réserve des engagements Geo propres à l'autre service (le cas échéant) ; seule la copie des données des clients intégrée dans Intune sera stockée dans le Geo indiqué pour Intune.

### <a name="office-for-mobile"></a>Office pour les appareils mobiles
Les données client de ce service proviennent d’autres services, comme Exchange Online et SharePoint Online. Aucune donnée client n’est stockée en dehors de ces services, à l’exception de l’appareil mobile.

### <a name="onenote-services"></a>Services OneNote
OneNote stocke les données client dans OneDrive Entreprise. Toutefois, il dispose d’une API qui peut entraîner la mise en place de caches persistants en dehors de la zone Geography où OneDrive Entreprise stocke les données client.

### <a name="planner"></a>Planificateur
Consultez la section [Informations sur l’emplacement des données statiques pour certaines charges de travail](#static-data-location-information-for-select-workloads) .

### <a name="power-apps-for-microsoft-365"></a>Power Apps pour Microsoft 365
Reportez-vous à [la disponibilité de Dynamics 365 et aux emplacements de données | Microsoft Learn](/dynamics365/get-started/availability).

### <a name="stream"></a>Flux
Vous pouvez trouver ces informations à partir de l’option « ? » dans l’interface utilisateur stream, si vous l’avez en cours d’exécution, puis cliquez sur « À propos de Microsoft Stream » pour voir où vos données sont stockées. Si nécessaire, créez un locataire d’évaluation.

### <a name="viva-insights--advanced-mgr-leader"></a>Viva Insights – Avancé, Mgr, Leader
Consultez la section [Informations sur l’emplacement des données statiques pour certaines charges de travail](#static-data-location-information-for-select-workloads) .  La région de données pour Manager/Leader et Avancé est déterminée par la _zone géographique par défaut_ du _locataire_, et non par les utilisateurs individuels.

### <a name="viva-insights--personal"></a>Viva Insights – Personnel
Les données client sont traitées et stockées dans la boîte aux lettres Exchange Online de l’employé. La résidence des données pour Les informations personnelles dans Viva Insights est basée sur l’emplacement de la boîte aux lettres de l’employé. Pour plus d’informations, consultez [Informations personnelles dans Viva Insights guide de confidentialité pour les administrateurs](/viva/insights/personal/overview/privacy-guide-admins?branch=main#summary-of-key-points).

### <a name="viva-learning"></a>Viva Learning
Consultez la section [Informations sur l’emplacement des données statiques pour certaines charges de travail](#static-data-location-information-for-select-workloads) .

### <a name="whiteboard"></a>Tableau blanc collaboratif
Reportez-vous à [Gérer les données du tableau blanc Microsoft | Microsoft Learn](/whiteboard/manage-data-organizations).

### <a name="yammer"></a>Yammer
Reportez-vous à [Data Residency - Yammer | Microsoft Learn](/yammer/manage-security-and-compliance/data-residency).

## <a name="static-data-location-information-for-select-workloads"></a>Informations sur l’emplacement des données statiques pour certaines charges de travail

1. Macro-région Geography 1 – EMEA / Union européenne
1. Macro-région Géographie 2 - Asie-Pacifique
1. Macro Région Géographie 3 – Amériques
1. Australie
1. Canada
1. Japon

| Country Code | Nom du pays | Viva Insights Avancé | Viva Learning | Planificateur |
| --- | --- | --- | --- | --- |
| Af | Afghanistan | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Ax | Îles Åland | APC<sup>2</sup>| AMER<sup>3</sup>| EUR<sup>1</sup>|
| Al | Albanie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Dz | Algérie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| AS | Samoa américaines | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Ad | Andorre | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ao | Angola | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| IA | Anguilla | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Aq | Antarctique | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Ag | Antigua-et-Barbuda | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Ar | Argentine | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Suis | Arménie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| AW | Aruba | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| AU | Australie | APC<sup>2</sup>| AUS<sup>4</sup>| AUS<sup>4</sup>|
| AT | Autriche | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Az | Azerbaïdjan | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bs | Bahamas | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Bh | Bahreïn | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bd | Bangladesh | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Bb | Barbade | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| BY | Bélarus | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bve | Belgique | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bz | Bélize | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Bj | Bénin | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bm | Bermudes | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Bt | Bhoutan | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Bo | Bolivie | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Bq | Bonaire | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Ba | Bosnie-Herzégovine | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bw | Botswana | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bv | Île Bouvet | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Br | Brésil | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Io | Territoire britannique de l’Océan Indien | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Vg | Îles Vierges britanniques | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Bn | Brunei Darussalam | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| BG | Bulgarie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bf | Burkina Faso | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Bi | Burundi | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Kh | Cambodge | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Cm | Cameroun | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| CA | Canada | AMER<sup>3</sup>| AMER<sup>3</sup>| CAN<sup>5</sup>|
| VC | Cap-Vert | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ky | Îles Cayman | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Cf | République centrafricaine | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Td | Tchad | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Cl | Chili | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Cn | Chine | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Cx | Île Christmas | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Cc | Île Cocos (Keeling) | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| CO | Colombie | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| KM | Comores | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Cg | République du Congo (Brazzaville) | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Cd | République démocratique du Congo (Kinshasa) | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ck | Îles Cook | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Cr | Costa Rica | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| CI | Côte d'Ivoire | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| HR | Croatie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| CW | Curaçao | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Cy | Chypre | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Cz | République tchèque | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| DK | Danemark | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Dj | Djibouti | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Dm | Dominique | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Faire | République dominicaine | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Ce | Équateur | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Eg | Égypte | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| ED | El Salvador | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Gq | Guinée Équatoriale | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| ER | Érythrée | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ee | Estonie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| ET | Éthiopie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Fk | Îles Malouines (Malvinas) | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Fo | Îles Féroé | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Fm | États fédérés de Micronésie | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Fj | Fidji | APC<sup>2</sup>| APC<sup>2</sup>| AUS<sup>4</sup>|
| FI | Finlande | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| FR | France | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gf | Guyane française | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Pf | Polynésie française | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Tf | Territoires français du Sud | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Disponible | Gabon | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gm | Gambie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ge | Géorgie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| DE | Allemagne | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gh | Ghana | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gi | Gibraltar | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| GR | Grèce | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gl | Groenland | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Gd | Grenade | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Gp | Guadeloupe | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Gu | Guam | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Gt | Guatemala | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Gg | Guernesey | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gn | Guinée | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gw | Guinée-Bissau | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gy | Guyane | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Ht | Haïti | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Hm | Îles Heard and Mcdonald | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| VA | Saint-Siège (Cité du Vatican) | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Hn | Honduras | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Hk | Hong Kong, R.S. Chine | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Hu | Hongrie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Est | Islande | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| DANS | Inde | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| ID | Indonésie | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| IQ | Irak | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| IE | Irlande | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| IM (Messagerie instantanée) | Île de Man | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| IL | Israël | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Professionnels de l’informatique | Italie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Jm | Jamaïque | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Jp | Japon | APC<sup>2</sup>| APC<sup>2</sup>| JPN<sup>6</sup>|
| JE | Jersey | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| JO | Jordanie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Kz | Kazakhstan | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ke | Kenya | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ki | Kiribati | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Kp | Corée (Nord) | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Kr | Corée (Sud) | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Xk | Kosovo | EUR<sup>1</sup>| AMER<sup>3</sup>| EUR<sup>1</sup>|
| Kw | Koweït | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Kg | Kirghizstan | EUR<sup>1</sup>| APC<sup>2</sup>| EUR<sup>1</sup>|
| LA | Lao PDR | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Lv | Lettonie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Lb | Liban | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ls | Lesotho | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Lr | Libéria | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ly | Libye | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Li | Liechtenstein | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Lt | Lituanie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| LU | Luxembourg | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| MO | Macao, R.S. Chine | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Mg | Madagascar | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mw | Malawi | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mon | Malaisie | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Mv | Maldives | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Ml | Mali | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mt | Malte | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mh | Îles Marshall | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Mq | Martinique | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| M | Mauritanie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mu | Île Maurice | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Yt | Mayotte | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| MX | Mexique | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Mc | Monaco | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Md | Moldova | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| MN | Mongolie | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Moi | Monténégro | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ms | Montserrat | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| MA | Maroc | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mz | Mozambique | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| MM | Birmanie | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| N/A | Namibie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Nr | Nauru | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Np | Népal | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| NL | Pays-Bas | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Un | Antilles Néerlandaises | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Nc | Nouvelle-Calédonie | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Nz | Nouvelle-Zélande | APC<sup>2</sup>| APC<sup>2</sup>| AUS<sup>4</sup>|
| NI | Nicaragua | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| NE | Niger | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ng | Nigéria | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| NU | Niue | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Nf | Île Norfolk | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| MP | Îles Mariannes du Nord | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| NON | Norvège | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Om | Oman | EUR<sup>1</sup>| APC<sup>2</sup>| EUR<sup>1</sup>|
| Pk | Pakistan | EUR<sup>1</sup>| APC<sup>2</sup>| EUR<sup>1</sup>|
| PW | Palaos | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Ps | Autorité palestinienne | APC<sup>2</sup>| EUR<sup>1</sup>| APC<sup>2</sup>|
| Pa | Panama | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Pg | Papouasie-Nouvelle-Guinée | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Py | Paraguay | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Pe | Pérou | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| PH | Philippines | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Pn | Île Pitcairn | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| PL | Pologne | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Pt | Portugal | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Pr | Porto Rico | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Qa | Qator | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Mk | Macédoine du Nord | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Re | Réunion | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ro | Roumanie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ru | Russie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Rw | Rwanda | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Sh | Sainte-Hélène, Ascension et Tristan da Cunha | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Kn | Saint-Christophe-et-Nevis | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Lc | Sainte-Lucie | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Pm | Saint-Pierre-et-Miquelon | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Vc | Saint-Vincent-et-Les-Îles | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Bl | Saint-Barthélemy | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Mf | Saint-Martin (partie Français) | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Ws | État indépendant des Samoa | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Sm | Saint-Marin | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| St | Sao Tomé-et-Principe | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| SA | Arabie Saoudite | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Sn | Sénégal | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| RS | Serbie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Sc | Seychelles | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| SL | Sierra Leone | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Sg | Singapour | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Sx | Saint-Martin (néerlandais) | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Sk | Slovaquie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| SI | Slovénie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Sb | Îles Salomon | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| SO | Somalie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Za | Afrique du Sud | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Gs | Géorgie du Sud-et-les Îles Sandwich du Sud | AMER<sup>3</sup>| EUR<sup>1</sup>| AMER<sup>3</sup>|
| Ss | Soudan du Sud | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| ES | Espagne | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Lk | Sri Lanka | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Sr | Suriname | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Sj | Svalbard et les Îles Jan Mayen | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Sz | Eswatini | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| SE | Suède | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ch | Suisse | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Tw | Taïwan, République de Chine | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Tj | Tadjikistan | EUR<sup>1</sup>| APC<sup>2</sup>| EUR<sup>1</sup>|
| E | Thaïlande | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Tl | Timor-Leste | APC<sup>2</sup>| EUR<sup>1</sup>| APC<sup>2</sup>|
| Tg | Togo | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| TK | Tokelau | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| TO | Tonga | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| TT | Trinité-et-Tobago | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| TN | Tunisie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Tr | Turquie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Tm | Turkménistan | EUR<sup>1</sup>| APC<sup>2</sup>| EUR<sup>1</sup>|
| Tc | Îles Turks et Caicos | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Tv | Tuvalu | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Ug | Ouganda | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| UA | Ukraine | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Ae | Émirats arabes unis | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Go | Royaume-Uni | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Tz | Tanzanie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| US | États-Unis d’Amérique | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Uy | Uruguay | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Messagerie unifiée | Îles mineures éloignées des États-Unis | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Uz | Ouzbékistan | EUR<sup>1</sup>| APC<sup>2</sup>| EUR<sup>1</sup>|
| VU | Vanuatu | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Ve | Venezuela (République centrafricaine) | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Vn | Vietnam | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Vi | Îles Vierges (États-Unis) | AMER<sup>3</sup>| AMER<sup>3</sup>| AMER<sup>3</sup>|
| Wf | Wallis et Futuna | APC<sup>2</sup>| APC<sup>2</sup>| APC<sup>2</sup>|
| Hein | Sahara occidental | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Vous | Yémen | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Zm | Zambie | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
| Zw | Zimbabwe | EUR<sup>1</sup>| EUR<sup>1</sup>| EUR<sup>1</sup>|
