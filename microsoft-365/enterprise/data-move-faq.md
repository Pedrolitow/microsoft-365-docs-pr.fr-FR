---
title: FAQ général relatif au déplacement de données
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
f1.keywords:
- NOCSH
description: Trouvez des réponses aux questions fréquemment posées sur le déplacement de données principales vers une nouvelle géodécenter Office 365.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: a7e59622e35604ebd9befbbe17a8a125ed15e101
ms.sourcegitcommit: c0cfb9b354db56fdd329aec2a89a9b2cf160c4b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50094654"
---
# <a name="data-move-general-faq"></a>FAQ général relatif au déplacement de données

Voici des réponses aux questions générales sur le déplacement des données client essentielles au repos vers une nouvelle géo de centres de données.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>Quels clients peuvent demander un déplacement ?
  
Les clients commerciaux Microsoft 365 existants qui ont sélectionné un pays éligible pour la nouvelle région de centres de données pourront demander un déplacement. Le programme existe uniquement pour les clients avec un code pays éligible affecté au client Microsoft 365 pour migrer les données client essentielles au repos pour les charges de travail éligibles vers la région de centre de données Microsoft 365 correspondante. Reportez-vous à la page [Comment demander votre](request-your-data-move.md) déplacement de données pour confirmer l’éligibilité du pays.   

## <a name="how-do-we-define-core-customer-data"></a>Comment définir les données client essentielles ?
 
Les données client essentielles sont un terme qui fait référence à un sous-ensemble de données client définies dans [les conditions Microsoft Online Services :](https://aka.ms/ost) 
- Contenu de boîte aux lettres Exchange Online (corps du courrier électronique, entrées de calendrier et contenu des pièces jointes des e-mails)
- Contenu du site SharePoint Online et fichiers stockés dans ce site
- Fichiers téléchargés vers OneDrive Entreprise 

## <a name="what-is-in-scope-for-teams-migration"></a>Qu’est-ce qui est dans l’étendue de la migration teams ?

En plus d’Exchange Online, SharePoint Online et OneDrive Entreprise ; Microsoft migre les données Teams vers le centre de données local. 
- Messages de conversation Teams, y compris les messages privés et les messages de canal. 
- Images Teams utilisées dans les conversations. 

Les fichiers Teams sont stockés dans SharePoint Online et les fichiers de conversation Teams sont stockés dans OneDrive Entreprise. La messagerie vocale, le calendrier et les contacts sont stockés dans Exchange Online. Dans de nombreux cas, Exchange Online, SharePoint Online et OneDrive Entreprise sont déjà utilisés par le client dans la zone géographique du centre de données local et font également partie du programme de migration Microsoft 365 pour les pays clients éligibles.

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>À quel stade ma migration est-elle terminée afin que les données client essentielles de mon client sont stockées au repos dans ma nouvelle géo ?

En raison des dépendances partagées entre Exchange Online et SharePoint Online/OneDrive Entreprise, toute migration ne peut pas être considérée comme terminée tant que les deux services n’ont pas été migrés. Exchange Online et SharePoint Online/OneDrive Entreprise migrent souvent à des moments distincts et indépendamment les uns des autres. Les administrateurs client reçoivent une confirmation dans le Centre de messages lorsque chaque migration de service est terminée et peuvent afficher la carte d’emplacement des données dans le Centre d’administration à tout moment pour confirmer les données client principales au repos pour chaque service.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Comment vous assurez-vous que mes données client sont sécurisées lors du déplacement et qu’il n’y aura pas de temps d’arrêt ?
  
Les déplacements de données sont une opération de service back-end ayant un impact minimal sur les utilisateurs finaux. Les fonctionnalités qui peuvent être impactées sont répertoriées dans [During et after your data move](during-and-after-your-data-move.md). Nous respectons le contrat Microsoft Online Services de niveau de [service (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) pour la disponibilité, de sorte que les clients n’ont rien à préparer ou à surveiller pendant le déplacement. 
  
Tous les services Microsoft 365 exécutent les mêmes versions dans les centres de données, afin que vous soyez assuré de la cohérence des fonctionnalités. Votre service est entièrement pris en charge tout au long du processus.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Quel est l’impact de la localisation de différents services dans différentes géos ?

Certains services Microsoft 365 peuvent se trouver dans des emplacements géographiques différents pour certains clients existants et pour les clients qui sont au milieu du processus de déplacement. Nos services s’exécutent indépendamment les uns des autres et n’ont aucun impact sur l’expérience utilisateur si c’est le cas. Toutefois, à des fins de résidence des données, une migration de client ne peut pas être considérée comme terminée tant qu’Exchange Online et SharePoint Online/OneDrive Entreprise n’ont pas été migrés vers la même géodécentre de données.

 ## <a name="where-is-my-core-customer-data-located"></a>Où se trouvent mes données client principales ?

Les administrateurs client peuvent afficher la carte d’emplacement des données dans le Centre d’administration à tout moment pour confirmer les données client principales au repos pour chaque service, en particulier pour leur client.  Nous publions également l’emplacement des régions de centres de données, des centres de données et de l’emplacement des données client Office 365 sur les cartes de centre de données interactives [Microsoft 365 ](https://office.com/datamaps) en tant que référence pour les données client essentielles par défaut actuelles aux emplacements de repos pour les nouveaux clients. Vous pouvez vérifier l’emplacement de vos données client au repos via la section Emplacement des données sous votre profil d’organisation dans le Centre d’administration Microsoft 365.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>Quand pourrai-je demander un déplacement ?
  
Reportez-vous à la page [Comment demander](request-your-data-move.md) votre déplacement de données pour les délais pris en charge pour votre géo de centre de données.
  
## <a name="how-can-i-request-to-be-moved"></a>Comment effectuer ma demande de déplacement ?
  
Les clients éligibles voient une page dans leur Centre [d’administration Microsoft 365.](https://admin.microsoft.com/) Reportez-vous à la section [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir des informations sur la demande de déplacement. 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>Puis-je modifier ma sélection après avoir demandé un déplacement ?
  
Nous ne pouvons pas vous enlever du processus une fois que vous avez envoyé votre demande.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Que se passe-t-il si je ne fais pas la demande de déplacement avant la date d’échéance ?
  
Nous ne pouvons pas accepter les demandes de migration après la période d’inscription ouverte.

## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Que se passe-t-il si je veux déplacer mes données afin de bénéficier de meilleures performances réseau ?
  
La proximité physique d’un centre de données Microsoft 365 ne garantit pas de meilleures performances réseau. De nombreux facteurs et composants affectent les performances réseau entre l’utilisateur final et le service Microsoft 365. Pour plus d’informations à ce sujet et sur l’optimisation des performances, voir Planification réseau et optimisation [des performances pour Microsoft 365.](network-planning-and-performance.md)
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Les données de tous les services sont-elles déplacées le même jour ?
 
Chaque service se déplace indépendamment et déplace probablement ses données à différents moments.
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Puis-je choisir la date du déplacement de mes données ?
 
Les clients ne sont pas en mesure de sélectionner une date spécifique, ils ne peuvent pas retarder leur déplacement et nous ne pouvons pas partager une date ou une période spécifique pour les déplacements.
  
 ## <a name="can-you-share-when-my-data-will-be-moved"></a>Pouvez-vous partager le moment où mes données seront déplacées ?
  
Les déplacements de données sont des opérations de base ayant un impact minimal sur les utilisateurs finaux. La complexité, la précision et l’échelle à laquelle nous devons effectuer des déplacements de données dans un environnement automatisé et géré globalement nous empêchent de partager quand un déplacement de données est prévu pour votre client ou tout autre client unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé. 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Que se passe-t-il si les utilisateurs accèdent à des services lors du déplacement des données ?

Reportez-vous à la section [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md) pour consulter la liste complète des fonctionnalités qui peuvent être limitées à certains moments du déplacement des données pour chaque service. 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>Comment savoir que le déplacement est terminé ?
  
Regardez le Centre de messages Microsoft 365 pour confirmer que le déplacement des données de chaque service est terminé. Lorsque les données de chaque service sont déplacées, nous publierons un avis d’achèvement afin que vous receviez trois notifications d’achèvement : une pour Exchange Online, SharePoint Online et Skype Entreprise Online. Vous pouvez également vérifier l’emplacement de vos données client au repos via la section Emplacement des données sous votre profil d’organisation dans le Centre d’administration Microsoft 365.  
  
## <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Je suis un client Microsoft 365 dans l’une des nouvelles région de centres de données, mais lorsque je me suis inscrit, j’ai sélectionné un autre pays. Comment puis-je être déplacé vers la nouvelle géo de centres de données ?

Il n’est pas possible de modifier le pays d’inscription associé à votre client. Au lieu de cela, vous devez créer un client Microsoft 365 avec un nouvel abonnement et déplacer manuellement vos utilisateurs et données vers le nouveau client.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Que se passe-t-il si nous sommes en train de migrer des données de messagerie vers Microsoft 365 lors du déplacement d’Exchange Online ?

Il s’agit d’un scénario très courant qui est entièrement pris en charge.  La migration cloud entre des centres de données géographiques n’interfère pas avec les migrations de boîtes aux lettres sur site vers le cloud.
  
 ## <a name="can-i-pilot-some-users"></a>Puis-je piloter certains utilisateurs ?
  
Vous pouvez créer un client d'évaluation distinct pour tester la connectivité, mais il ne peut pas être associé à votre client existant.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Je ne souhaite pas attendre que Microsoft déplace mes données. Puis-je simplement créer un client et le déplacer moi-même ?
  
Oui, toutefois le processus ne sera pas aussi transparent que s’il était effectué par Microsoft.
  
Si vous créez un client une fois que la nouvelle géo de centre de données est disponible, le nouveau client sera hébergé dans la nouvelle. Ce nouveau client est totalement distinct de votre client précédent et vous devez déplacer toutes les boîtes aux lettres utilisateur, le contenu du site, les noms de domaine et toutes les autres données. Notez que vous ne pouvez pas déplacer le nom du client d’un client vers un autre. Nous vous recommandons d’attendre le programme de déplacement fourni par Microsoft, car nous nous occuperons du déplacement de tous les paramètres, données et abonnements de vos utilisateurs.
  
## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Mes données client ont déjà été déplacées vers une nouvelle géo de centres de données. Puis-je les déplacer vers l’ancienne région ?
 
Non, ce n’est pas possible. Les clients qui ont été déplacés vers de nouveaux centres de données géographiques ne peuvent pas être déplacés vers de nouveaux centres de données géographiques. En tant que client dans n’importe quelle situation géographique, vous aurez la même qualité de service, les mêmes performances et les mêmes contrôles de sécurité qu’auparavant. [Microsoft 365 Multi Geo](https://aka.ms/multi-geo) est disponible pour certains clients en tant que modules de plateformes et permet à un seul client de créer plusieurs géos satellites et de déplacer des données utilisateur vers ces géos avec des engagements de résidence des données.
  
## <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Les clients Microsoft 365 hébergés dans les nouveaux centres de données seront-ils accessibles aux utilisateurs extérieurs au pays ?
  
Oui. Microsoft maintient un vaste réseau mondial avec des connexions Internet publiques dans plus de 130 emplacements dans 35 pays dans le monde avec des accords d’homologue avec plus de 2 700 fournisseurs de services Internet (ISP). Les utilisateurs pourront accéder aux centres de données par Internet, où qu’ils soient.

## <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mon client a configuré le module [add-on Multi-Géo.](https://aka.ms/multi-geo) Puis-je toujours m’inscrire à mon client dans le programme de déplacement Microsoft 365 pour modifier ma zone géographique par défaut et déplacer tout utilisateur qui n’est pas dans une région satellite vers la nouvelle zone géographique par défaut ?

Oui, votre client peut s’inscrire, mais il existe des considérations importantes, car le déplacement au niveau du client n’est pas entièrement pris en charge pour les clients qui ont configuré multigéogé.

SharePoint Online et OneDrive Entreprise ne peuvent pas migrer vers la nouvelle géo de centres de données au niveau du client via ce programme. L’administrateur client peut configurer les partages OneDrive Entreprise pour qu’ils se déplacent vers n’importe quelle région disponible à l’aide de Multi-Géo, mais l’emplacement par défaut du client ne peut pas être modifié une fois que Multi-Géo a été configuré pour un client.

Pour les clients qui optent pour la migration : nous déplacerons toutes les boîtes aux lettres Exchange Online de votre zone géographique par défaut actuelle vers votre nouvelle région de centre de données locale et nous mettreons à jour la région Exchange Online par défaut. Nous ne déplacerons pas les boîtes aux lettres EXO configurées dans les régions satellites multigé géographiques pour continuer à respecter la résidence des données de région satellite comme prévu. 

## <a name="related-topics"></a>Voir aussi

[Déplacement de données principales vers de nouvelles géos de centres de données Microsoft 365](moving-data-to-new-datacenter-geos.md)

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[Microsoft 365 Multi Geo](https://aka.ms/multi-geo)

[Carte interactive du centre de données Microsoft 365](https://office.com/datamaps)

[Microsoft 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Services Azure par région](https://azure.microsoft.com/regions/)
