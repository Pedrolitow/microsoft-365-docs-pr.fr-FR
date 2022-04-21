---
title: Configurer des versions historiques dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez des versions historiques dans eDiscovery (Premium) pour collecter du contenu à partir de toutes les versions de documents stockés dans SharePoint et OneDrive.
ms.openlocfilehash: ebd706aa122da2f875adb0c210db8cb3a0c8ab10
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000617"
---
# <a name="set-up-historical-versions-in-ediscovery-premium-preview"></a>Configurer des versions historiques dans eDiscovery (Premium) (préversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

La fonctionnalité de versions historiques dans eDiscovery (Premium) permet aux responsables eDiscovery de votre organisation de rechercher et de collecter du contenu à partir de toutes les versions de documents stockés dans SharePoint Online et OneDrive Entreprise. Vous pouvez ensuite ajouter ce contenu à un ensemble de révisions à des fins d’analyse et de révision. Cela vous permet de rechercher et de passer en revue le contenu d’une version spécifique d’un document qui peut être pertinente pour un cas ou une enquête, même si la dernière version du même document ne contient pas les informations pertinentes.

Pour prendre en charge la fonctionnalité de versions historiques dans eDiscovery (Premium), SharePoint administrateurs doivent activer le contrôle de version pour les sites de leur organisation. Ensuite, lorsque les utilisateurs modifient des documents dans SharePoint ou OneDrive, des versions régulières implicites sont créées lorsque le document est enregistré (ou enregistré automatiquement). SharePoint contrôle de version permet de suivre l’activité effectuée sur SharePoint éléments (y compris les documents, les événements et les tâches). Cette fonctionnalité de contrôle de version laisse une piste d’audit qui peut fournir des preuves dans les enquêtes juridiques. Ces versions antérieures d’un document sont disponibles pour l’organisation, qui peut être tenue de partager ces versions qui ont du contenu sensible ou pertinent lors de la découverte judiciaire dans une affaire juridique.

Une fois qu’un administrateur eDiscovery a activé les versions historiques de l’organisation pour des sites SharePoint spécifiques, le service push de contenu SharePoint analyse toutes les versions majeures et mineures des documents sur les sites activés, puis envoie ces versions pour indexation. Une fois le processus d’analyse et d’indexation terminé, les documents et leurs versions sont disponibles pour la recherche eDiscovery. Tant qu’une version spécifique est accessible (par historique des versions), cette version est détectable dans une recherche de collection eDiscovery (Premium).

## <a name="set-up-historical-versions"></a>Configurer les versions historiques

Pour activer les versions historiques dans eDiscovery (Premium), votre organisation doit l’activer, puis activer des sites spécifiques afin que toutes les versions des documents stockés sur ces sites soient indexées pour la recherche. Avant de configurer eDiscovery (Premium) pour les versions historiques, vous devez activer la prise en charge du contrôle de version dans SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>Étape 1 : Activer le contrôle de version dans SharePoint

La première étape consiste à activer le contrôle de version dans SharePoint Online afin que toutes les versions d’un document soient conservées. Pour obtenir des instructions, consultez [Contrôle de version dans SharePoint](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>Étape 2 : Activer les versions historiques

L’étape suivante consiste à activer les versions historiques dans eDiscovery (Premium). Pour activer les versions historiques de votre organisation, une personne doit être un administrateur général ou un administrateur eDiscovery (membre du sous-groupe Administrateur eDiscovery dans le groupe de rôles gestionnaire eDiscovery). Une fois les versions historiques activées, elles s’appliquent à l’ensemble de votre organisation.

> [!IMPORTANT]
> Une fois que vous avez activé les versions historiques, vous ne pourrez plus la désactiver pendant la préversion publique. Vous pourrez le désactiver une fois les versions historiques publiées pour une disponibilité générale.

1. Dans le portail de conformité Microsoft Purview, accédez à [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) puis cliquez sur **les paramètres eDiscovery (Premium**).

   ![Sélectionner les paramètres eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. Dans la page **Paramètres**, sélectionnez l’onglet **Versions historiques (préversion),** puis activez le bouton bascule du **contrôle client Versions historiques**.

   ![Activer le bouton bascule pour activer les versions historiques](..\media\HistoricalVersions2.png)

   Un avertissement s’affiche indiquant que vous ne pourrez pas désactiver les versions historiques. Comme indiqué précédemment, vous ne pourrez pas désactiver les versions historiques tant que la fonctionnalité n’est pas publiée pour disponibilité générale.

3. Cliquez sur **Oui** pour activer les versions historiques.

### <a name="step-3-activate-sharepoint-sites"></a>Étape 3 : Activer SharePoint sites

Une fois que vous avez activé les versions historiques de votre organisation, la dernière étape consiste à activer SharePoint sites pour prendre en charge les versions historiques. Lorsque vous activez un site (en l’ajoutant à une liste de sites sous l’onglet **Versions historiques** ), le site est recradé et toutes les versions des documents stockés sur ce site sont indexées pour recherche.

> [!NOTE]
> Il existe une limite de 100 activations de site par organisation pendant la préversion publique des versions historiques. Une activation est comptabilisée dans cette limite chaque fois que vous activez ou désactivez un site pour les versions historiques. Si vous activez plusieurs sites, chaque site est compté comme une activation unique. Le nombre total d’activations s’affiche sous l’onglet **Versions historiques** .

1. Sous l’onglet **Versions historiques** de la page **Paramètres** eDiscovery (Premium), cliquez sur **Activer** pour activer les sites pour les versions historiques.

   ![Cliquez sur Activer pour activer les sites pour les versions historiques](..\media\HistoricalVersions3.png)  

   Une page de menu volant s’affiche et contient la liste de tous les sites SharePoint de votre organisation.

2. Sélectionnez un site à activer, puis cliquez sur **Activer** pour l’activer pour les versions historiques. Vous pouvez utiliser la zone de recherche pour rechercher un site spécifique.

   Un avertissement s’affiche indiquant que les versions de document sur le site seront indexées et que ce processus d’indexation prendra un certain temps avant que les versions soient prêtes à être recherchées. L’avertissement indique également que vous ne pourrez pas désactiver les versions historiques du site sélectionné pendant 30 jours.

3. Cliquez sur **Oui** pour activer le site pour les versions historiques.

   ![Le site activé et le nombre d’activations de site sont affichés](..\media\HistoricalVersions4.png)  

   Le site est ajouté à la liste des sites activés. Le compteur indiquant le nombre d’activations de site est également mis à jour.

4. Répétez les étapes précédentes pour chaque site que vous souhaitez activer pour les versions historiques.

## <a name="frequently-asked-questions"></a>Foire aux questions

**En quoi les versions historiques sont-elles différentes de l’option permettant de « collecter toutes les versions » lorsque vous validez un projet de collection dans un ensemble de révisions ?**

Actuellement, seule la dernière version des documents est indexée pour la recherche. Cela signifie que lorsque vous exécutez un brouillon de collection, seules les dernières versions des documents sont recherchées. Si un document correspond à la requête de mot clé pour la collection, il est retourné dans les résultats de la collection. Toutefois, si la dernière version d’un document ne correspond pas à une requête de recherche, l’événement ne sera pas retourné si les versions antérieures du document contiennent le mot clé. Pour atténuer cette situation, eDiscovery (Premium) vous permet de collecter toutes les versions du document lorsque vous [validez une collection dans un jeu de révision](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set). Cela signifie que toute version antérieure qui peut contenir le mot clé sera ajoutée au jeu de révisions.

Les versions historiques sont différentes et plus efficaces que la collecte de toutes les versions, car lorsque vous activez un site, toutes les versions d’un document (et pas seulement la dernière version) sont indexées pour la recherche. Le résultat est que si une version antérieure d’un document contient un mot clé qui correspond à la requête de recherche, elle est retournée par la collection.

**Lorsque les versions historiques sont activées pour un site, cela a-t-il un impact sur les performances du site ?**

Non. Une fois les versions historiques activées pour un site, les performances du site sont identiques à ce qu’elles étaient avant l’activation du site. Les processus d’analyse et d’indexation qui sont effectués sur le site après son activation se produisent à un rythme plus lent et sont effectués pendant les heures creuses. L’activation des versions historiques d’un site lance un processus de remblai, qui recherche toutes les versions des documents sur le site, puis envoie ces versions à l’index. En fonction du nombre de versions de document pour le site, ce processus de remblai peut avoir un impact sur l’intégrité du service. Nous avons atténué cet impact potentiel des manières suivantes :

- Nous faisons le meilleur effort pour traiter ces versions pendant les heures creuses.

- Nous traitons les versions de document dans nos files d’attente de priorité la plus basse, ce qui permet de déléguer la plupart des ressources de service aux modifications de l’utilisateur.

**Combien de temps dois-je attendre qu’un site soit activé jusqu’à ce que toutes les versions historiques des documents sur ce site soient toutes indexées et disponibles pour la recherche eDiscovery ?**

En fonction du nombre de documents d’un site et du nombre moyen de versions par document, nous essayons d’estimer le nombre total de fichiers par site. Sur cette base, une estimation de la durée d’indexation est la suivante :

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

La demi-journée est ajoutée en tant que mémoire tampon, car l’indexation des versions sur le site est optimisée pour s’exécuter pendant les heures creuses.

Par exemple, si le nombre total de documents et toutes les versions d’un site est de 150 000, le traitement du site pour les versions historiques prend au moins deux jours :

`150,000 files/100,000 files per day + .5 days = 2 days`

**Pourquoi n’est-il pas recommandé d’activer ou de désactiver fréquemment des sites pour les versions historiques ?**

Lorsque vous désactivez un site précédemment activé, un processus de nettoyage est déclenché. Ce processus prend du temps. Si ce même site est à nouveau activé, le processus de remblai de réindexation du site doit être réexécuté. Les processus de nettoyage et de remplissage sont longs et gourmands en ressources. Par conséquent, nous vous recommandons d’examiner attentivement et de planifier les sites que vous souhaitez activer pour la version historique afin d’éviter l’activation et la désactivation répétées des versions historiques d’un site.
