---
title: Configurer des versions historiques dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez les versions historiques dans Advanced eDiscovery pour collecter du contenu à partir de toutes les versions des documents stockés SharePoint et OneDrive.
ms.openlocfilehash: 8da7b390a982b9be0a4752e167399ad633377854
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60779071"
---
# <a name="set-up-historical-versions-in-advanced-ediscovery-preview"></a>Configurer des versions historiques dans Advanced eDiscovery (prévisualisation)

La fonctionnalité des versions historiques dans Advanced eDiscovery permet aux gestionnaires eDiscovery de votre organisation de rechercher et de collecter du contenu à partir de toutes les versions des documents stockés dans SharePoint Online et OneDrive Entreprise. Vous pouvez ensuite ajouter ce contenu à un groupe de révision pour analyse et révision. Cela vous permet de rechercher et de consulter le contenu d’une version spécifique d’un document qui peut être pertinent pour un cas ou un examen, même si la dernière version du même document ne contient pas les informations pertinentes.

Pour prendre en charge la fonctionnalité de versions historiques dans Advanced eDiscovery, SharePoint administrateurs doivent activer le gestion des versions pour les sites de leur organisation. Ensuite, lorsque les utilisateurs modifient des documents dans SharePoint ou OneDrive, des versions régulières implicites sont créées lorsque le document est enregistré (ou enregistré automatiquement). SharePoint contrôle de version permet le suivi de l’activité effectuée sur les SharePoint (documents, événements et tâches, notamment). Cette fonctionnalité de contrôle de version laisse une piste d’audit qui peut fournir des preuves dans les enquêtes juridiques. Ces versions antérieures d’un document sont disponibles pour l’organisation, qui peut être tenue de partager ces versions qui ont du contenu sensible ou pertinent lors de la découverte de la cour dans une affaire juridique.

Une fois qu’un administrateur eDiscovery a activé les versions historiques de l’organisation, puis l’a activé pour des sites SharePoint spécifiques, le service push de contenu SharePoint analyse toutes les versions principales et mineures des documents sur les sites activés, puis envoie ces versions pour indexation. Une fois le processus d’analyse et d’indexation terminé, les documents et leurs versions sont disponibles pour la recherche de découverte électronique. Tant qu’une version spécifique est accessible (par l’historique des versions), cette version est alors découvrable dans une recherche Advanced eDiscovery collection.

## <a name="set-up-historical-versions"></a>Configurer des versions historiques

Pour activer les versions historiques dans Advanced eDiscovery, votre organisation doit l’activer, puis activer des sites spécifiques afin que toutes les versions des documents stockés sur ces sites soient indexées pour la recherche. Avant de configurer Advanced eDiscovery pour les versions historiques, vous devez activer la prise en charge du suivi des versions dans SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>Étape 1 : Activer le contrôle de version dans SharePoint

La première étape consiste à activer le service de SharePoint Online afin que toutes les versions d’un document soient conservées. Pour obtenir des instructions, [consultez La version dans SharePoint](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>Étape 2 : Activer les versions historiques

L’étape suivante consiste à activer les versions historiques dans Advanced eDiscovery. Pour activer les versions historiques de votre organisation, une personne doit être administrateur général ou administrateur eDiscovery (membre du sous-groupe Administrateur eDiscovery dans le groupe de rôles Gestionnaire eDiscovery). Une fois que les versions historiques sont allumées, elles s’appliquent à l’ensemble de votre organisation.

> [!IMPORTANT]
> Une fois que vous avez activer les versions historiques, vous ne pourrez pas la désactiver pendant la prévisualisation publique. Vous pourrez la désactiver une fois que les versions historiques seront publiées pour une disponibilité générale.

1. Dans la Centre de conformité Microsoft 365, [Advanced eDiscovery,](https://go.microsoft.com/fwlink/p/?linkid=2173764)puis cliquez sur **Advanced eDiscovery paramètres.**

   ![Sélectionner Advanced eDiscovery paramètres](..\media\HistoricalVersions1.png)

2. Dans la page **Paramètres,** sélectionnez l’onglet Versions historiques  **(prévisualisation),** puis basculez le bouton bascule du contrôle client Versions historiques sur le bouton bascule.

   ![Activer le bouton bascule pour activer les versions historiques](..\media\HistoricalVersions2.png)

   Un avertissement s’affiche pour vous dire que vous ne pourrez pas désactiver les versions historiques. Comme indiqué précédemment, vous ne pourrez pas désactiver les versions historiques tant que la fonctionnalité n’aura pas été publiée pour une disponibilité générale.

3. Cliquez **sur Oui** pour activer les versions historiques.

### <a name="step-3-activate-sharepoint-sites"></a>Étape 3 : Activer SharePoint sites

Une fois que vous avez activé les versions historiques de votre organisation, la dernière étape consiste à activer SharePoint sites pour prendre en charge les versions historiques. Lorsque vous activez un site (en l’ajoutant à une liste de sites sous l’onglet **Versions** historiques), le site est réaxé et toutes les versions des documents stockés sur ce site sont indexées pour la recherche.

> [!NOTE]
> Il existe une limite de 100 activations de site par organisation lors de la prévisualisation publique des versions historiques. Une activation est comptabilisée dans cette limite chaque fois que vous activez ou désactivez un site pour les versions historiques. Si vous activez plusieurs sites, chaque site est compté comme une seule activation. Le nombre total d’activations s’affiche sous **l’onglet Versions historiques.**

1. Sous **l’onglet Versions historiques** de Advanced eDiscovery **Paramètres**  page, cliquez sur Activer pour activer les sites pour les versions historiques.

   ![Cliquez sur Activer pour activer les sites pour les versions historiques](..\media\HistoricalVersions3.png)  

   Une page volante s’affiche qui contient la liste de tous les sites SharePoint de votre organisation.

2. Sélectionnez un site à activer, puis cliquez sur **Activer** pour l’activer pour les versions historiques. Vous pouvez utiliser la zone de recherche pour rechercher un site spécifique.

   Un avertissement indique que les versions de document sur le site seront indexées et que ce processus d’indexation prendra un certain temps avant que les versions soient prêtes à être recherchés. L’avertissement indique également que vous ne pourrez pas désactiver les versions historiques du site sélectionné pendant 30 jours.

3. Cliquez **sur Oui** pour activer le site pour les versions historiques.

   ![Le site activé et le nombre d’activations de site sont affichés](..\media\HistoricalVersions4.png)  

   Le site est ajouté à la liste des sites activés. Le compteur indiquant le nombre d’activations de site est également mis à jour.

4. Répétez les étapes précédentes pour chaque site que vous souhaitez activer pour les versions historiques.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**En quoi les versions historiques sont-elles différentes de l’option de « collecte de toutes les versions » lorsque vous validerez un brouillon de collection dans un jeu à réviser ?**

Actuellement, seule la dernière version des documents est indexée pour la recherche. Cela signifie que lorsque vous exécutez un brouillon de collection, seules les versions les plus récentes des documents sont recherchés. Si un document correspond à la requête de mot clé pour la collection, il est renvoyé dans les résultats de la collection. Toutefois, si la dernière version d’un document ne correspond pas à une requête de recherche, le document ne sera pas renvoyé si les versions antérieures du document contiennent le mot clé. Pour atténuer cette situation, Advanced eDiscovery vous donne la possibilité de collecter toutes les versions du document lorsque vous validerez une collection dans un jeu [à réviser.](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set) Cela signifie que toute version antérieure qui peut contenir le mot clé sera ajoutée au jeu à réviser.

Les versions historiques sont différentes et plus efficaces que la « collecte de toutes les versions », car lorsque vous activez un site, toutes les versions d’un document (et pas seulement la dernière version) sont indexées pour la recherche. Le résultat est que si une version antérieure d’un document contient un mot clé qui correspond à la requête de recherche, il sera renvoyé par la collection.

**Lorsque les versions historiques sont activées pour un site, cela a-t-il un impact sur les performances du site ?**

Non. Une fois que les versions historiques sont activées pour un site, les performances du site sont identiques à ce qu’elles étaient avant l’exécution du site. Les processus d’analyse et d’indexation effectués sur le site une fois activés se produisent à un rythme plus lent et sont exécutés pendant les heures creuses. L’activation des versions historiques d’un site lance un processus de recalage, qui recherche toutes les versions des documents sur le site, puis envoie ces versions à l’index. Selon le nombre de versions de document pour le site, ce processus de recalage peut avoir un impact sur l’état du service. Nous avons atténué cet impact potentiel des manières suivantes :

- Nous faisons de notre mieux pour traiter ces versions pendant les heures creuses.

- Nous traiterons les versions de documents dans nos files d’attente de priorité la plus faible, ce qui permet de déléguer la plupart des ressources de service aux modifications apportées aux utilisateurs.

**Combien de temps dois-je attendre qu’un site soit activé jusqu’à ce que toutes les versions historiques des documents de ce site soient toutes indexées et disponibles pour la recherche eDiscovery ?**

En fonction du nombre de documents pour un site et du nombre moyen de versions par document, nous essayons d’estimer le nombre total de fichiers par site. Sur cette base, une estimation du temps d’indexation est la suivante :

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

La demi-journée est ajoutée en tant que mémoire tampon, car l’indexation des versions sur le site est optimisée pour s’exécuter pendant les heures creuses.

Par exemple, si le nombre total de documents et toutes les versions d’un site est de 150 000, il faudra au moins deux jours pour traiter le site pour les versions historiques :

`150,000 files/100,000 files per day + .5 days = 2 days`

**Pourquoi n’est-il pas recommandé d’activer ou de désactiver fréquemment des sites pour les versions historiques ?**

Lorsque vous désactivez un site précédemment activé, un processus de nettoyage est déclenché. Ce processus prendra du temps. Si ce même site est réactivé, le processus de recalage du site doit être réexécuté. Les processus de nettoyage et de recalage sont longs et longs. Par conséquent, nous vous recommandons d’envisager et de planifier soigneusement les sites que vous souhaitez activer pour la version historique afin d’éviter d’activer et de désactiver à plusieurs reprises les versions historiques d’un site.
