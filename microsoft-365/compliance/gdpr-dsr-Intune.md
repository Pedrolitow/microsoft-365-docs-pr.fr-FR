---
title: Demandes des personnes associées aux données pour Intune concernant le RGPD
description: ''
keywords: Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365, RGPD
author: dougeby
localization_priority: Priority
audience: itpro
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: dougeby
manager: angrobe
ms.collection: GDPR
ms.openlocfilehash: eeb50954f849b0c110a88cc7d768844847d99255
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867472"
---
# <a name="intune-data-subject-requests-for-the-gdpr"></a>Demandes des personnes associées aux données pour Intune concernant le RGPD
Le Règlement général sur la protection des données (RGPD) de l’UE permet aux utilisateurs (désignés dans le règlement comme étant les *personnes concernées*) de gérer les données personnelles collectées par un employeur ou tout autre type d’agence ou organisation (le *contrôleur des données* ou le *contrôleur* uniquement). Les données personnelles sont définies de manière générale dans le cadre du RGPD comme correspondant aux données associées à une personne physique identifiée ou identifiable. Le RGPD octroie aux personnes concernées des droits spécifiques sur leurs données personnelles. Ces droits incluent l’obtention de copies des données personnelles, les demandes de corrections de ces dernières, la restriction de leur traitement, leur suppression ou leur réception dans un format électronique afin de les transférer à un autre contrôleur. Toute demande formelle effectuée par une personne concernée à un contrôleur au sujet de la prise de mesure sur ses données personnelles est appelée *demande de personne concernée* ou DSR. 

Le guide explique comment utiliser les outils d’administration, les services et les produits Microsoft pour aider nos clients contrôleurs à rechercher des données personnelles et à agir dessus pour répondre à des DSR. Plus précisément, il décrit comment rechercher, consulter et traiter des données personnelles stockées dans le cloud Microsoft. Voici un aperçu des processus décrits dans ce guide :

1.  ***Découvrir*** : utilisez les outils de recherche et de découverte pour rechercher plus facilement des données client qui peuvent être l’objet d’une DSR. Une fois que vous avez collecté les documents pouvant être utiles, vous pouvez effectuer une ou plusieurs des actions DSR décrites dans les étapes suivantes pour répondre à la demande. Par ailleurs, vous pouvez déterminer que la demande ne respecte pas les instructions de votre organisation pour répondre à des DSR.

2.  ***Accéder*** : récupérez des données personnelles qui résident dans le cloud Microsoft et, si nécessaire, effectuez-en une copie pour la personne concernée.

3.  ***Rectifier*** : modifiez ou mettez en œuvre d’autres actions demandées sur les données personnelles, le cas échéant.

4.  ***Limiter*** : limitez le traitement des données personnelles, soit en supprimant des licences pour différents services Azure, soit en désactivant les services souhaités, lorsque cela est possible. Vous pouvez également supprimer des données du cloud Microsoft et les conserver en local ou à un autre emplacement.

5.  ***Supprimer*** : supprimez définitivement des données personnelles qui résidaient dans le cloud Microsoft.

6.  ***Exporter*** : fournissez une copie électronique (dans un format lisible par une machine) des données personnelles à la personne concernée.

Chaque section de ce guide décrit les procédures techniques qu’une organisation de contrôleur des données peut suivre pour répondre à une DSR pour des données personnelles dans le cloud Microsoft.

<span id="_Toc511384801" class="anchor"><span id="_Toc511163872" class="anchor"><span id="_Toc511136229" class="anchor"><span id="_Toc511125162" class="anchor"><span id="_Toc511120749" class="anchor"><span id="_Toc511122656" class="anchor"><span id="_Toc508792503" class="anchor"></span></span></span></span></span></span></span>
#### <a name="terminology"></a>Terminologie

Vous trouverez ci-dessous des définitions de termes utilisés dans ce guide.

-   *Contrôleur* : la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui, seul ou conjointement avec d’autres, détermine les finalités et les moyens du traitement des données personnelles ; lorsque les finalités et les moyens du traitement sont déterminés par la législation de l’Union ou des États membres, le contrôleur peut être désigné, ou les critères spécifiques relatifs à sa nomination peuvent être définis, par la législation de l’Union ou des États membres.

-   *Données personnelles* et *personne concernée* : elles correspondent aux informations relatives à une personne naturelle identifiée ou identifiable (« la personne concernée ») ; une personne naturelle identifiable est une personne qui peut être identifiée, directement ou indirectement, notamment par référence à un identificateur par exemple, un nom, un numéro d’identification, des données de localisation, un identificateur en ligne, ou un ou plusieurs facteurs spécifiques de l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne naturelle.

-   *Sous-traitant* : la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui traite des données personnelles pour le compte du contrôleur.

-   *Données client* : l’intégralité des données (textes, son, vidéo ou fichiers images, et logiciels) qui sont fournies à Microsoft par un client ou pour le compte d’un client par le biais du service d’entreprise. Les données client incluent à la fois les (1) informations d’identification personnelle des utilisateurs finaux (par exemple, les noms d’utilisateur et les informations de contact dans Azure Active Directory) et le contenu client chargé ou créé par un client dans des services spécifiques (par exemple, le contenu client dans un compte de stockage Azure, le contenu client d’un Azure SQL Database ou l’image de la machine virtuelle d’un client dans des machines virtuelles Azure).

-   *Journaux générés par le système* : les journaux et les données connexes générés par Microsoft qui aident Microsoft à fournir des services d’entreprise aux utilisateurs. Les journaux générés par le système contiennent principalement des données de pseudonymes comme des identificateurs uniques : généralement, un numéro généré par le système qui ne peut pas, en soi, identifier une personne individuelle, mais est utilisé pour fournir les services d’entreprise aux utilisateurs. Les journaux générés par le système peuvent aussi contenir des informations d’identification personnelle sur les utilisateurs finaux comme, par exemple, un nom d’utilisateur.  

<span id="_Toc511384802" class="anchor"><span id="_Toc511163873" class="anchor"><span id="_Toc511136230" class="anchor"><span id="_Toc511125163" class="anchor"><span id="_Toc511120750" class="anchor"><span id="_Toc511122657" class="anchor"><span id="_Toc508792504" class="anchor"></span></span></span></span></span></span></span>

#### <a name="how-to-use-this-guide"></a>Comment utiliser ce guide

Ce guide est composé de deux parties :

**Partie 1 : Répondre aux demandes de personne concernée pour des données client** : la première partie de ce guide explique comment rectifier, limiter, supprimer et exporter des données dans des applications dans lesquelles vous avez créé des données, et comment y accéder. Cette section explique en détail comment exécuter des DSR par rapport à un contenu client et des informations d’identification personnelle d’utilisateurs finaux.

**Partie 2 : Répondre aux demandes de personne concernée pour les journaux générés par le système** : lorsque vous utilisez les services d’entreprise de Microsoft, Microsoft génère des informations appelées Journaux générés par le système, pour fournir le service. La deuxième partie de ce guide explique comment supprimer et exporter ces informations pour Azure, et comment y accéder.

<span id="_Toc511384803" class="anchor"><span id="_Toc511163874" class="anchor"></span></span>







### <a name="understanding-dsrs-for-azure-active-directory-and-microsoft-intune"></a>Présentation des DSR pour Azure Active Directory et Microsoft Intune

Lorsqu’il est question des services fournis aux clients d’entreprise, l’exécution des DSR doit toujours être comprise dans le contexte d’un client Azure Active Directory (AAD) spécifique. Ces DSR sont notamment toujours exécutées dans un client AAD donné. Si un utilisateur participe à plusieurs clients, il est important de souligner qu’une DSR donnée est exécutée *uniquement* dans le contexte du client spécifique dans lequel la demande a été reçue. Il est essentiel de le comprendre car cela signifie que l’exécution d’une DSR par un client d’entreprise n’aura **pas** d’impact sur les données d’un client d’entreprise adjacent.

Il en est de même pour Microsoft Intune fourni à un client d’entreprise : l’exécution d’une DSR par rapport à un compte de Intune *associé à un client AAD* **concernera uniquement** les données du client. Par ailleurs, il est important de comprendre les éléments suivants lors de la gestion de comptes Intune dans un client :

-   Si l’utilisateur d’un compte Intune crée un abonnement Azure, l’abonnement sera géré comme s’il s’agissait d’un client AAD. Par conséquent, les DSR sont limitées au client, comme décrit ci-dessus.

-   Si un abonnement Azure créé via un compte Intune est supprimé, **il n’affectera pas** le compte Intune en question. Une fois de plus, comme indiqué ci-dessus, les DSR exécutées dans l’abonnement Azure sont limitées à l’étendue du client lui-même.

Les DSR par rapport à un compte Intune lui-même, **en dehors d’un client donné**, sont exécutées via le tableau de bord de confidentialité du consommateur. Consultez le Guide des demandes des personnes associées aux données de Windows pour obtenir plus d’informations.

<span id="_Toc508792505" class="anchor"><span id="_Toc511384804" class="anchor"><span id="_Toc511163875" class="anchor"><span id="_Toc511136231" class="anchor"><span id="_Toc511125164" class="anchor"><span id="_Toc511120751" class="anchor"><span id="_Toc511122658" class="anchor"></span></span></span></span></span></span></span>

## <a name="part-1-dsr-guide-for-customer-data"></a>Partie 1 : Guide des DSR pour les données client

<span id="_Toc511384805" class="anchor"><span id="_Toc511163876" class="anchor"><span id="_Toc511136232" class="anchor"><span id="_Toc511125165" class="anchor"><span id="_Toc511120752" class="anchor"><span id="_Toc511122659" class="anchor"></span></span></span></span></span></span>

### <a name="executing-dsrs-against-customer-data"></a>Exécution des DSR par rapport aux données client

Microsoft permet de supprimer et d’exporter certaines données client, et d’y accéder, via le portail Azure et directement aussi via des interfaces de programmation d’applications (API) ou des interfaces utilisateur (UI) préexistantes pour des services spécifiques (également appelées *expériences intégrées au produit*). Vous trouverez des informations sur ces expériences intégrées au produit dans la documentation de référence des services respectifs.

>[!Important]  
>Les services qui prennent en charge les DSR intégrées au produit requièrent l’utilisation directe de l’API ou de l’UI du service, décrivant les applications CRUD (créer, lire, mettre à jour, supprimer) applicables. Par conséquent, l’exécution des DSR dans un service donné doit être effectuée en plus de l’exécution d’une DSR dans le portail Azure afin d’effectuer une demande complète pour une personne concernée donnée. Consultez la documentation de référence des services spécifiques pour plus d’informations.

<span id="_Discover" class="anchor"><span id="_Toc508792508" class="anchor"><span id="_Toc511122661" class="anchor"><span id="_Toc511120754" class="anchor"><span id="_Toc511125167" class="anchor"><span id="_Toc511136234" class="anchor"><span id="_Toc511163877" class="anchor"><span id="_Toc511384806" class="anchor"></span></span></span></span></span></span></span></span>
### <a name="step-1-discover"></a>Étape 1 : Découvrir

La première étape de la réponse à une DSR consiste à rechercher les données personnelles qui font l’objet de la demande. Cette première étape (recherche et passer en revue les données personnelles en question) vous aidera à déterminer si une DSR répond aux besoins de votre organisation pour accepter ou refuser une DSR. Par exemple, après avoir recherché et passé en revue les données personnelles en question, vous pouvez déterminer que la demande ne répond pas aux exigences de votre organisation, car cette action peut affecter défavorablement les droits et libertés d’autres personnes.

Une fois que vous avez trouvé les données, vous pouvez ensuite effectuer l’action spécifique pour satisfaire la demande de la personne associée aux données. Pour obtenir plus d’informations, consultez les rubriques suivantes :
- [Collecte de données](https://docs.microsoft.com/intune/privacy-data-collect)
- [Traitement et stockage des données](https://docs.microsoft.com/intune/privacy-data-store-process)
- [Afficher les données personnelles](https://docs.microsoft.com/intune/privacy-data-view-correct#view-personal-data)

### <a name="step-2-access"></a>Étape 2 : Accéder
Une fois que vous avez trouvé les données client contenant des données personnelles répondant potentiellement à une DSR, vous et votre organisation devez décider quelles données fournir à la personne concernée. Vous pouvez les fournir avec une copie du document réel, une version correctement rédigée ou une capture d’écran des parties que vous considérez pouvoir partager. Pour chacune de ces réponses à une demande d’accès, vous devrez récupérer une copie du document ou de tout autre élément contenant les données pertinentes.

Lorsque vous fournissez une copie à la personne concernée, il se peut que vous deviez supprimer ou rédiger des informations personnelles sur d’autres personnes concernées et des informations confidentielles.

<span id="_Using_Content_Search_1" class="anchor"></span>La section suivante explique comment obtenir une copie de données pour répondre à la demande d’accès d’une DSR.

<span id="_Rectify" class="anchor"><span id="_Ref511119463" class="anchor"><span id="_Toc511122665" class="anchor"><span id="_Toc511120758" class="anchor"><span id="_Toc511125171" class="anchor"><span id="_Toc511136238" class="anchor"><span id="_Toc511163881" class="anchor"><span id="_Toc511384810" class="anchor"></span></span></span></span></span></span></span></span>

#### <a name="azure-active-directory"></a>Azure Active Directory

<span id="_Forms_1" class="anchor"></span>Microsoft offre un portail et des expériences intégrées au produit qui permettent à l’administrateur client du client d’entreprise de gérer les demandes d’accès d’une DSR. Les demandes d’accès d’une DSR permettent d’accéder aux données personnelles de l’utilisateur, ainsi qu’aux : (a) informations d’identification personnelle concernant un utilisateur final et (b) journaux générés par le système.

<span id="_Toc511384811" class="anchor"><span id="_Toc511163882" class="anchor"><span id="_Toc511136239" class="anchor"><span id="_Toc511125172" class="anchor"><span id="_Toc511120759" class="anchor"><span id="_Toc511122666" class="anchor"></span></span></span></span></span></span>
#### <a name="service-specific-interfaces"></a>Interfaces propres au service

Microsoft Intune permet de [découvrir des données client](#step-1-discover) directement via les interfaces utilisateur (IU) ou les interfaces de programmation d’applications préexistantes (API).

<span id="_Sway" class="anchor"><span id="_Toc508792516" class="anchor"><span id="_Toc511122667" class="anchor"><span id="_Toc511120760" class="anchor"><span id="_Toc511125173" class="anchor"><span id="_Toc511136240" class="anchor"><span id="_Toc511163883" class="anchor"><span id="_Toc511384812" class="anchor"></span></span></span></span></span></span></span></span>
### <a name="step-3-rectify"></a>Étape 3 : Rectifier

Si une personne associée aux données vous a demandé de rectifier les données personnelles qui figurent dans les données de votre organisation, vous et votre organisation devez déterminer s’il convient d’honorer cette demande. Rectifier les données peut éventuellement signifier prendre des mesures telles que la modification, la rédaction ou la suppression des données personnelles d’un document ou d’un autre type ou élément. 

<span id="_Toc511384813" class="anchor"><span id="_Toc511163884" class="anchor"><span id="_Toc511136241" class="anchor"><span id="_Toc511125174" class="anchor"><span id="_Toc511120761" class="anchor"><span id="_Toc511122668" class="anchor"></span></span></span></span></span></span>


 En qualité de responsable du traitement des données, Microsoft ne permet pas de corriger les journaux générés par le système, car ils représentent des activités factuelles et constituent un enregistrement historique d’événements au sein des services Microsoft. Par rapport à Intune, les administrateurs ne peuvent pas mettre à jour les informations spécifiques d’appareils ou d’applications. Si un utilisateur final souhaite corriger des données personnelles (par exemple, le nom de l’appareil), il doit le faire directement sur son appareil. Ces modifications sont synchronisées lors de la prochaine connexion à Intune.

### <a name="step-4-restrict"></a>Étape 4 : Limiter

<span id="_Delete" class="anchor"></span>Les personnes associées aux données peuvent vous demander de limiter le traitement de leurs données personnelles. Nous fournissons le portail Azure et les interfaces de programmation d’applications (API) ou interfaces utilisateur (UI) préexistantes. Ces expériences permettent à l’administrateur client du client d’entreprise de gérer ces DSR via une combinaison d’exportation de données et de suppression de données. Pour obtenir plus d’informations, consultez l’article [Traitement des données personnelles](https://docs.microsoft.com/intune/privacy-data-store-process#processing-personal-data).

<span id="_Toc508792528" class="anchor"><span id="_Toc511122671" class="anchor"><span id="_Toc511120764" class="anchor"><span id="_Toc511125177" class="anchor"><span id="_Toc511136244" class="anchor"><span id="_Toc511163887" class="anchor"><span id="_Toc511384816" class="anchor"></span></span></span></span></span></span></span>
### <a name="step-5-delete"></a>Étape 5 : Supprimer

Le « droit à l’effacement » par la suppression des données personnelles des données client d’une organisation est une protection clé du RGPD. La suppression des données personnelles inclut l’élimination de l’ensemble des données personnelles et des journaux générés par le système à l’exception des informations du journal d’audit. Pour obtenir plus d’informations, consultez l’article [Supprimer les données personnelles de l’utilisateur final](https://docs.microsoft.com/intune/privacy-data-audit-export-delete#delete-end-user-personal-data).


<span id="_Toc511384822" class="anchor"><span id="_Toc511163893" class="anchor"><span id="_Toc511136250" class="anchor"><span id="_Toc511125183" class="anchor"><span id="_Toc511120770" class="anchor"><span id="_Toc511122677" class="anchor"></span></span></span></span></span></span>
## <a name="part-2-system-generated-logs"></a>Partie 2 : Journaux générés par le système
Les journaux d’audit fournissent aux administrateurs client un enregistrement d’activités entraînant une modification dans Microsoft Intune. Les journaux d’audit sont disponibles pour de nombreuses activités de gestion et généralement des actions comme la création, la mise à jour (modification), la suppression et l’affectation. Les tâches à distance qui permettent de générer des événements d’audit peuvent aussi être révisées. Ces journaux d’audit contiennent parfois des données personnelles d’utilisateurs dont les appareils sont enregistrés dans Intune. Les administrateurs ne peuvent pas supprimer les journaux d’audit. Pour obtenir plus d’informations, consultez l’article [Données personnelles d’audit](https://docs.microsoft.com/intune/privacy-data-audit-export-delete#audit-personal-data).


## <a name="notify-about-exporting-or-deleting-issues"></a>Notification des problèmes d’exportation ou de suppression
Si vous rencontrez des problèmes lorsque vous exportez ou supprimez des données sur le portail Azure, accédez au panneau **Aide + Support** du portail Azure et envoyez un nouveau ticket sous **Gestion des abonnements > Autre demande de conformité et de sécurité > Confidentialité et demandes dans le cadre du RGPD**.

#### <a name="learn-more"></a>En savoir plus
[Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx)