---
title: FAQ général relatif au déplacement de données
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: ITPro
ms.topic: faq
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
ms.collection:
- scotvorg
description: Trouvez des réponses aux questions fréquentes (FAQ) sur le déplacement de données de base vers une nouvelle zone géographique de centre de données Office 365.
ms.openlocfilehash: af07ee89ffb8948ac2961db179112e70f3d0cfb4
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68209005"
---
# <a name="data-move-general-faq"></a>FAQ général relatif au déplacement de données

Voici des réponses aux questions générales sur le déplacement des données client principales au repos vers une nouvelle zone géographique de centre de données.

### <a name="what-customers-are-eligible-to-request-a-move"></a>Quels clients peuvent demander un déplacement ?
<details><summary>Cliquez pour développer</summary>

Les clients commerciaux Microsoft 365 existants qui ont sélectionné un pays éligible pour la nouvelle zone géographique du centre de données pourront demander un déplacement. Le programme existe uniquement pour les locataires avec un code de pays éligible affecté au locataire Microsoft 365 afin de migrer les données client principales au repos pour les charges de travail éligibles vers la zone géographique du centre de données Microsoft 365 correspondante. Découvrez [comment demander le déplacement de vos données](request-your-data-move.md) pour confirmer l’éligibilité du pays.

</details>

### <a name="how-do-we-define-core-customer-data"></a>Comment définir les données client principales ?
<details><summary>Cliquez pour développer</summary>

Les données client de base sont un terme qui fait référence à un sous-ensemble de données client définies dans les [termes de Microsoft Online Services :](https://aka.ms/ost)

- Exchange Online contenu de boîte aux lettres (corps de l’e-mail, entrées de calendrier et contenu des pièces jointes)
- Contenu du site SharePoint Online et fichiers stockés dans ce site
- Fichiers chargés dans OneDrive Entreprise

</details>

### <a name="what-is-in-scope-for-teams-migration"></a>Quelle est l’étendue de la migration Teams ?
<details><summary>Cliquez pour développer</summary>

Outre Exchange Online, SharePoint Online et OneDrive Entreprise; Microsoft migrera les données Teams vers le centre de données local.

- Messages de conversation Teams, y compris les messages privés et les messages de canal.
- Images Teams utilisées dans les conversations.

Les fichiers Teams sont stockés dans SharePoint Online et les fichiers de conversation Teams sont stockés dans OneDrive Entreprise. La messagerie vocale, le calendrier et les contacts sont stockés dans Exchange Online. Dans de nombreux cas, Exchange Online, SharePoint Online et OneDrive Entreprise sont déjà utilisés par le client dans la zone géographique du centre de données local et font également partie du programme de migration Microsoft 365 pour les pays clients éligibles.

</details>

### <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>À quel moment ma migration est-elle terminée afin que les données client principales de mon locataire soient stockées au repos dans ma nouvelle zone géographique ?
<details><summary>Cliquez pour développer</summary>

En raison des dépendances partagées entre Exchange Online et SharePoint Online/OneDrive Entreprise, aucune migration ne peut être considérée comme terminée tant que les deux services ne sont pas migrés. Exchange Online et SharePoint Online/OneDrive Entreprise migrent souvent à des moments distincts et indépendamment les uns des autres. Les administrateurs de locataire client reçoivent une confirmation dans le Centre de messages lorsque chaque migration de service est terminée et peuvent afficher la carte d’emplacement des données dans le centre Administration à tout moment pour confirmer les données client principales à l’emplacement de repos de chaque service.

</details>

### <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Comment vous assurez-vous que mes données client sont sécurisées lors du déplacement et qu’il n’y aura pas de temps d’arrêt ?
<details><summary>Cliquez pour développer</summary>

Les déplacements de données sont une opération de service principal avec un impact minimal sur les utilisateurs finaux. Les fonctionnalités qui peuvent être affectées sont répertoriées pendant [et après le déplacement de vos données](during-and-after-your-data-move.md). Nous respectons le [Contrat de niveau de service (SLA) Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) pour la disponibilité afin que les clients n’ont rien à préparer ou à surveiller pendant le déplacement.

Tous les services Microsoft 365 exécutent les mêmes versions dans les centres de données, ce qui vous garantit une fonctionnalité cohérente. Votre service est entièrement pris en charge tout au long du processus.

</details>

### <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Quel est l’impact de la présence de différents services dans des zones géographiques différentes ?
<details><summary>Cliquez pour développer</summary>

Certains services Microsoft 365 peuvent se trouver dans des zones géographiques différentes pour certains clients existants et pour les clients qui sont au milieu du processus de déplacement. Nos services s’exécutent indépendamment les uns des autres et il n’y a aucun impact sur l’expérience utilisateur si c’est le cas. Toutefois, à des fins de résidence des données, une migration de locataire ne peut pas être considérée comme terminée tant que Exchange Online et SharePoint Online/OneDrive Entreprise ne sont pas migrés vers la même zone géographique de centre de données.

</details>

### <a name="where-is-my-core-customer-data-located"></a>Où se trouvent mes données client principales ?
<details><summary>Cliquez pour développer</summary>

Les administrateurs de locataire client peuvent afficher la carte d’emplacement des données dans le centre Administration à tout moment pour confirmer les données client principales à l’emplacement de repos de chaque service, en particulier pour leur locataire. Nous publions également l’emplacement des zones géographiques des centres de données, des centres de données et l’emplacement des données client Office 365 sur les [cartes de centre de données interactives Microsoft 365](https://office.com/datamaps) comme référence pour les données client principales par défaut actuelles aux emplacements de repos pour les nouveaux locataires. Vous pouvez vérifier l’emplacement de vos données client au repos via la section Emplacement des données sous votre profil d’organisation dans le Centre d'administration Microsoft 365.

</details>

### <a name="when-will-i-be-able-to-request-a-move"></a>Quand pourrai-je demander un déplacement ?
<details><summary>Cliquez pour développer</summary>

Reportez-vous à la page [Comment demander votre déplacement de données](request-your-data-move.md) pour connaître les délais pris en charge pour la zone géographique de votre centre de données.

</details>

### <a name="how-can-i-request-to-be-moved"></a>Comment effectuer ma demande de déplacement ?
<details><summary>Cliquez pour développer</summary>

Les clients éligibles verront une page dans leur [Centre d'administration Microsoft 365](https://admin.microsoft.com/). Reportez-vous à la section [Procédure de demande d'un déplacement de données](request-your-data-move.md) pour obtenir des informations sur la demande de déplacement.

</details>

### <a name="can-i-change-my-selection-after-requesting-a-move"></a>Puis-je modifier ma sélection après avoir demandé un déplacement ?
<details><summary>Cliquez pour développer</summary>

Nous ne pouvons pas vous enlever du processus une fois que vous avez envoyé votre demande.

</details>

### <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Que se passe-t-il si je ne fais pas la demande de déplacement avant la date d’échéance ?
<details><summary>Cliquez pour développer</summary>

Nous ne pouvons pas accepter les demandes de migration après la période d’inscription ouverte.

</details>

### <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Que se passe-t-il si je veux déplacer mes données afin de bénéficier de meilleures performances réseau ?
<details><summary>Cliquez pour développer</summary>

La proximité physique d’un centre de données Microsoft 365 n’est pas une garantie de meilleures performances réseau. De nombreux facteurs et composants affectent les performances réseau entre l’utilisateur final et le service Microsoft 365. Pour plus d’informations sur ce problème et sur le réglage des performances, consultez [Planification réseau et réglage des performances pour Microsoft 365](network-planning-and-performance.md).

</details>

### <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Les données de tous les services sont-elles déplacées le même jour ?
<details><summary>Cliquez pour développer</summary>

Chaque service se déplace indépendamment et déplacera probablement ses données à différents moments.

</details>

### <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Puis-je choisir la date du déplacement de mes données ?
<details><summary>Cliquez pour développer</summary>

Les clients ne sont pas en mesure de sélectionner une date spécifique, ils ne peuvent pas retarder leur déplacement, et nous ne pouvons pas partager une date ou une période spécifique pour les déplacements.

</details>

### <a name="can-you-share-when-my-data-will-be-moved"></a>Pouvez-vous partager quand mes données seront déplacées ?
<details><summary>Cliquez pour développer</summary>

Les déplacements de données sont une opération back-end avec un impact minimal sur les utilisateurs finaux. La complexité, la précision et l’échelle auxquelles nous devons effectuer des déplacements de données au sein d’un environnement géré à l’échelle mondiale et automatisée nous empêchent de partager quand un déplacement de données est supposé se terminer pour votre locataire ou tout autre locataire unique. Les clients recevront une confirmation dans le centre de messages pour chaque service concerné une fois que le déplacement des données sera terminé.

</details>

### <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Que se passe-t-il si les utilisateurs accèdent à des services lors du déplacement des données ?
<details><summary>Cliquez pour développer</summary>

Reportez-vous à la section [Pendant et après le déplacement de vos données](during-and-after-your-data-move.md) pour consulter la liste complète des fonctionnalités qui peuvent être limitées à certains moments du déplacement des données pour chaque service.

</details>

### <a name="how-do-i-know-the-move-is-complete"></a>Comment savoir que le déplacement est terminé ?
<details><summary>Cliquez pour développer</summary>

Regardez le Centre de messages Microsoft 365 pour confirmer que le déplacement des données de chaque service est terminé. Lorsque les données de chaque service sont déplacées, nous publierons un avis d’achèvement afin que vous obteniez trois avis d’achèvement : un pour Exchange Online, SharePoint Online et Skype Entreprise Online. Vous pouvez également vérifier l’emplacement de vos données client au repos via la section Emplacement des données sous votre profil d’organisation dans le Centre d'administration Microsoft 365.

</details>

### <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Je suis un client Microsoft 365 dans l’une des nouvelles zones géographiques du centre de données, mais quand je me suis inscrit, j’ai sélectionné un autre pays. Comment puis-je être déplacé vers la nouvelle zone géographique du centre de données ?
<details><summary>Cliquez pour développer</summary>

Il n’est pas possible de modifier le pays d’inscription associé à votre locataire. Au lieu de cela, vous devez créer un locataire Microsoft 365 avec un nouvel abonnement et déplacer manuellement vos utilisateurs et vos données vers le nouveau locataire.

</details>

### <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Que se passe-t-il si nous procédons à la migration des données de messagerie vers Microsoft 365 pendant le déplacement Exchange Online ?
<details><summary>Cliquez pour développer</summary>

Il s’agit d’un scénario très courant et entièrement pris en charge. La migration cloud entre les zones géographiques du centre de données n’interfère pas avec les migrations de boîtes aux lettres locales vers le cloud.

</details>

### <a name="can-i-pilot-some-users"></a>Puis-je piloter certains utilisateurs ?
<details><summary>Cliquez pour développer</summary>

Vous pouvez créer un client d'évaluation distinct pour tester la connectivité, mais il ne peut pas être associé à votre client existant.

</details>

### <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Je ne veux pas attendre que Microsoft déplace mes données. Puis-je simplement créer un client et le déplacer moi-même ?
<details><summary>Cliquez pour développer</summary>

Oui, toutefois le processus ne sera pas aussi transparent que s’il était effectué par Microsoft.

Si vous créez un locataire une fois la nouvelle zone géographique du centre de données disponible, le nouveau locataire est hébergé dans la nouvelle zone géographique. Ce nouveau locataire est complètement distinct de votre locataire précédent et vous êtes responsable du déplacement de toutes les boîtes aux lettres utilisateur, du contenu du site, des noms de domaine et de toutes les autres données. Notez que vous ne pouvez pas déplacer le nom du locataire d’un locataire à un autre. Nous vous recommandons d’attendre le programme de déplacement fourni par Microsoft, car nous allons nous occuper du déplacement de tous les paramètres, données et abonnements pour vos utilisateurs.

</details>

### <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Mes données client ont déjà été déplacées vers une nouvelle zone géographique de centre de données. Puis-je les déplacer vers l’ancienne région ?
<details><summary>Cliquez pour développer</summary>

Non, ce n’est pas possible. Les clients qui ont été déplacés vers de nouveaux centres de données géographiques ne peuvent pas être renvoyés. En tant que client dans n’importe quelle zone géographique, vous constaterez la même qualité de service, de performances et de contrôles de sécurité que vous l’avez fait précédemment. [Microsoft 365 Multi Geo](https://aka.ms/multi-geo) est disponible pour certains clients en tant que module complémentaire et permet à un seul locataire de créer plusieurs zones géographiques satellites et de déplacer des données utilisateur vers ces zones géographiques avec des engagements de résidence des données.

</details>

### <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Les locataires Microsoft 365 hébergés dans les nouveaux centres de données seront-ils disponibles pour les utilisateurs en dehors du pays ?
<details><summary>Cliquez pour développer</summary>

Oui. Microsoft gère un grand réseau mondial avec des connexions Internet publiques dans plus de 130 emplacements dans 35 pays à travers le monde avec des contrats de peering avec plus de 2 700 fournisseurs de services Internet (ISP). Les utilisateurs pourront accéder aux centres de données par Internet, où qu’ils soient.

</details>

### <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mon locataire a configuré le module complémentaire multigéographique. Puis-je toujours m’inscrire à mon locataire dans le programme de déplacement Microsoft 365 ? pour modifier ma zone géographique par défaut et déplacer tout utilisateur qui n’est pas dans une région satellite vers la nouvelle zone géographique par défaut ?
<details><summary>Cliquez pour développer</summary>

Oui, votre locataire est éligible à l’inscription, mais des considérations importantes sont à prendre en compte, car le déplacement au niveau du locataire n’est pas entièrement pris en charge pour les clients qui ont configuré [multigéographique](https://aka.ms/multi-geo).

SharePoint Online et OneDrive Entreprise ne peuvent pas migrer vers la nouvelle zone géographique du centre de données au niveau du locataire via ce programme. L’administrateur client peut configurer OneDrive Entreprise partages pour qu’ils soient déplacés vers n’importe quelle région disponible à l’aide de Multi-Geo, mais l’emplacement par défaut du locataire ne peut pas être modifié une fois multigéographique configuré pour un locataire.

Pour les clients qui optent pour la migration, nous allons déplacer toutes les boîtes aux lettres Exchange Online de votre zone géographique par défaut actuelle vers votre nouvelle zone géographique de centre de données local et mettre à jour la région de Exchange Online par défaut. Nous ne déplacerons aucune boîte aux lettres EXO configurée dans les régions satellites multigéographiques pour continuer à respecter la résidence des données de région satellite comme vous l’avez prévu.  Les migrations de locataires du service de conversation Teams pour les clients avec une configuration multigéographique se comportent de la même façon que Exchange Online.

</details>

### <a name="i-have-public-folders-deployed-in-my-tenant-what-will-be-the-impact-on-public-folder-access-during-or-after-the-move"></a>J’ai déployé des dossiers publics dans mon locataire. Quel sera l’impact sur l’accès aux dossiers publics pendant ou après le déplacement ?
<details><summary>Cliquez pour développer</summary>

Il n’y a aucun impact sur les utilisateurs finaux qui accèdent à des dossiers publics pendant ou après le déplacement de dossiers publics. Toutefois, les dossiers publics peuvent ne pas être disponibles pour l’administration dans l’outil Exchange Administration Center tant que toutes les boîtes aux lettres de dossiers publics ne sont pas déplacées dans la même région. Pour plus d’informations, consultez [cet article](https://aka.ms/pfxrf) .

</details>

### <a name="related-topics"></a>Voir aussi

[Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365](moving-data-to-new-datacenter-geos.md)

[Procédure de demande d’un déplacement de données](request-your-data-move.md)

[Microsoft 365 Multi Geo](https://aka.ms/multi-geo)

[Carte interactive du centre de données Microsoft 365](https://office.com/datamaps)

[Prise en charge de Microsoft 365](../admin/get-help-support.md)

[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)

[Services Azure par région](https://azure.microsoft.com/regions/)
