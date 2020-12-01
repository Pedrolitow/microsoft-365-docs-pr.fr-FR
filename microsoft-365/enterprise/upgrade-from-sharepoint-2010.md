---
title: Mise à jour à jour de SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: Trouvez des informations et des ressources à mettre à niveau à partir de SharePoint 2010 et SharePoint Server 2010. Prise en charge pour les deux extrémités du 13 avril 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fba095a15164f8a09ce1e0a1cbd5ee9cd298aa74
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519762"
---
# <a name="upgrading-from-sharepoint-2010"></a>Mise à jour à jour de SharePoint 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft SharePoint 2010 et SharePoint Server 2010 vont atteindre la fin de la prise en charge le **13 avril 2021**. Cet article fournit des ressources pour vous aider à migrer vos données SharePoint Server 2010 existantes vers SharePoint Online dans Microsoft 365 ou mettre à niveau votre environnement SharePoint Server 2010 sur site.

## <a name="what-is-end-of-support"></a>Qu’est-ce que la *fin du support*?

La plupart des produits Microsoft ont un cycle de vie de la prise en charge, pendant laquelle ils obtiennent de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Après la date de fin de prise en charge, le produit ne cesse de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes susceptibles de se produire.

- Correctifs de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura plus de mises à jour, de correctifs ou de correctifs pour le produit (y compris les correctifs de sécurité/correctifs). Le support Microsoft aura entièrement déplacé ses efforts de support vers des versions plus récentes.

À la fin de la prise en charge de SharePoint Server 2010, supprimez les données dont vous n’avez plus besoin avant de mettre à niveau le produit et de migrer vos données importantes.

> [!NOTE]
> Le cycle de vie d’un logiciel dure généralement dix ans à compter de la publication initiale. Les [fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) peuvent vous aider à effectuer une mise à niveau vers la prochaine version du logiciel ou à migrer vers la migration Microsoft 365 (ou les deux). Assurez-vous que vous avez pris connaissance des dates de fin de prise en charge des technologies sous-jacentes critiques, en particulier pour la version de Microsoft SQL Server que vous utilisez avec SharePoint. Pour plus d’informations, voir [stratégie de cycle de vie fixe](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planifier à l’avance

Vérifiez les dates qui prennent en charge les extrémités sur le [site du cycle de vie du produit](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Planifiez vos mises à niveau ou migrations à l’aide de ces dates à l’esprit. N’oubliez pas que votre produit *ne fonctionnera pas* à la date indiquée. Toutefois, étant donné que votre installation ne sera plus corrigée après cette date, vous devrez planifier une transition sans complication vers la prochaine version du produit.

Cette matrice permet de tracer un cours parmi les options de migration :

|Fin du produit de support|Bonne |Idéale|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (en local)|SharePoint Online|
||SharePoint Server 2013 hybride avec SharePoint Online|SharePoint Server 2016 (en local)|
|||Recherche hybride sur le Cloud SharePoint|

Si vous choisissez une option sur l’extrémité inférieure de l’unité (bon), vous devrez commencer à planifier une autre mise à niveau peu de temps après la migration de SharePoint Server 2010.

Voici les trois chemins que vous pouvez suivre pour éviter la fin de la prise en charge de SharePoint Server 2010.

![Chemins de mise à niveau vers SharePoint Server 2010](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> La fin de la prise en charge de SharePoint Server 2010 et de SharePoint Foundation 2010 est actuellement prévue pour le 13 avril 2021. Veillez à consulter le [site du cycle de vie des produits](https://support.microsoft.com/lifecycle) pour les dates les plus récentes.

## <a name="whats-next"></a>Étape suivante

SharePoint Server 2013 et SharePoint Foundation 2013 peuvent être installés en local sur vos propres serveurs. Ou vous pouvez utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Vous pouvez choisir l’une des actions suivantes :

- Migrer vers SharePoint Online.

- Mettre à niveau SharePoint Server ou SharePoint Foundation local.

- Effectuez les deux opérations ci-dessus.

- Implémentez une solution [SharePoint hybride](https://docs.microsoft.com/sharepoint/hybrid/hybrid) .

Prenez en compte les coûts cachés liés à la maintenance d’une batterie de serveurs, y compris la maintenance ou la migration des personnalisations et la mise à niveau du matériel. Si vous avez comptabilisé ces facteurs, il sera plus facile de procéder à une mise à niveau locale. Si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation élevée, vous pouvez bénéficier d’une migration planifiée vers SharePoint Online. Pour un environnement SharePoint Server local, vous pouvez également envisager de transférer des données dans SharePoint Online afin de réduire la charge de gestion du matériel.

> [!NOTE]
> Les administrateurs SharePoint peuvent créer un abonnement Microsoft 365, configurer de nouveaux sites SharePoint Online, puis se découper de SharePoint Server 2010 proprement, en prenant uniquement les documents essentiels sur les sites récents. Ensuite, toutes les données restantes peuvent être vidées du site SharePoint Server 2010 dans des archives locales.

|SharePoint Online|SharePoint Server en local|
|---|---|
|Coût élevé dans le temps (planification/exécution/vérification)|Coût élevé dans le temps (planification/exécution/vérification)|
|Coût réduit des fonds (sans achat de matériel)|Coût plus élevé des fonds (achats de matériel)|
|Coût unique lors de la migration|Coût unique répété par migration future|
|Faible coût total de possession/maintenance|Coût total de propriété/maintenance élevé|

Un déplacement unique vers Microsoft 365 aura un coût plus élevé lorsque vous organisez des données et que vous déciderez des éléments à prendre dans le Cloud et ce qu’il faut laisser derrière. Mais une fois vos données migrées, les mises à niveau futures seront automatiques, car vous n’aurez plus besoin de gérer les mises à jour matérielles et logicielles. Et le temps de mise à niveau de votre batterie de serveurs sera sauvegardé par un [contrat de niveau de service (SLA) Microsoft](https://go.microsoft.com/fwlink/?linkid=843153).

### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online offre toutes les fonctionnalités dont vous avez besoin. Voir [Description du service SharePoint](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

Vous ne pouvez pas migrer directement de SharePoint Server 2010 (ou SharePoint Foundation 2010) vers SharePoint Online. Une grande partie du travail de migration est manuelle. Mais cette étape vous permet de nettoyer les données et les sites qui ne sont plus nécessaires avant le déplacement. Vous pouvez archiver d’autres données dans le stockage. 

N’oubliez pas que SharePoint Server 2010 et SharePoint Foundation 2010 ne cesseront de fonctionner à la fin du support. Afin que les administrateurs puissent avoir un point lorsque SharePoint est toujours en cours d’exécution si leurs clients oublient de déplacer certaines de leurs données.

Si vous effectuez une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016 et que vous décidez de mettre des données dans SharePoint Online, vous pouvez utiliser l' [API de migration SharePoint](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) pour migrer des informations vers OneDrive entreprise.

|Avantages de SharePoint Online|Inconvénient de SharePoint Online|
|---|---|
|Microsoft fournit le matériel SPO et l’administration de toutes les ressources matérielles.|Les fonctionnalités disponibles peuvent varier entre SharePoint Server sur site et SPO.|
|Vous êtes l’administrateur général de votre abonnement et pouvez affecter des administrateurs aux sites SPO.|Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server local n’existent pas (ou ne sont pas nécessaires) dans le rôle d’administrateur SharePoint dans Microsoft 365. Toutefois, l’administration de SharePoint, l’administration de la collection de sites et la propriété du site sont locales pour votre organisation.|
|Microsoft applique les correctifs, les correctifs et les mises à jour sur le matériel et les logiciels sous-jacents, y compris les serveurs SQL sur lesquels SharePoint Online s’exécute.|Étant donné qu’il n’y a pas accès au système de fichiers sous-jacent dans le service, la personnalisation est limitée.|
|Microsoft publie des [contrats de niveau de service](https://go.microsoft.com/fwlink/?linkid=843153) et se déplace rapidement pour résoudre les incidents de niveau de service.|La sauvegarde et la restauration, ainsi que d’autres options de récupération, sont automatisées par le service dans SharePoint Online. Les sauvegardes sont remplacées si elles ne sont pas utilisées.|
|Les tests de sécurité et le réglage des performances du serveur sont effectués en continu dans le service par Microsoft.|Les modifications apportées à l’interface utilisateur et à d’autres fonctionnalités SharePoint sont installées par le service et doivent être activées ou désactivées.|
|Microsoft 365 répond à de nombreuses normes industrielles : [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165).|L’assistance [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).|
|Les ingénieurs du support technique Microsoft et les employés du centre de connaissances ne disposent pas d’un accès administrateur illimité à votre abonnement.|Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version plus récente de SharePoint ou si une batterie de serveurs secondaire est nécessaire pour la mise à niveau.|
|Les fournisseurs de solutions peuvent vous aider dans le travail unique de migration de vos données vers SharePoint Online.|Toutes les modifications apportées à SharePoint Online ne figurent pas dans votre contrôle. Après la migration, les différences de conception dans les menus, les bibliothèques et les autres fonctionnalités peuvent affecter temporairement la convivialité.|
|Les produits en ligne sont mis à jour automatiquement à travers le service. Les fonctionnalités peuvent être désapprouvées, mais il n’y a pas de fin de cycle de vie de la prise en charge.|Il existe un cycle de vie de fin de support pour SharePoint Server ou SharePoint Foundation, ainsi que des serveurs SQL sous-jacents.|

Si vous avez décidé de créer un nouveau site Microsoft 365 et de migrer manuellement les données vers ce dernier en fonction de vos besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

À partir de SharePoint Server 2019, les mises à niveau doivent passer en  *série*. Il n’existe aucun moyen de procéder à la mise à niveau directement de SharePoint Server 2010 vers SharePoint Server 2016 ou vers SharePoint 2019. Chemin de mise à niveau série :

- SharePoint Server 2010 \> SharePoint server 2013 \> sharepoint server 2016

Cela prend du temps et prévoit de suivre le chemin d’accès complet de SharePoint 2010 vers SharePoint Server 2016. Les mises à niveau impliquent des coûts pour le matériel (les serveurs SQL Server doivent également être mis à niveau), des logiciels et des tâches d’administration. De plus, il se peut que les personnalisations doivent être mises à niveau ou abandonnées. Veillez à documenter les personnalisations importantes avant de mettre à niveau votre batterie de serveurs SharePoint Server.

> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2010 de fin de prise en charge, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Toutefois, il existe des pièges potentiels à ces déplacements manuels, tels que des documents provenant de 2010 disposant d’un compte en dernier lieu modifié avec l’alias du compte qui effectue le déplacement manuel. D’autres tâches doivent être exécutées à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de liste. Veillez à nettoyer votre environnement avant de procéder à la mise à niveau. Déterminez les données que vous pouvez déplacer dans le stockage ou qui ne sont plus nécessaires. Cela peut réduire l’impact de la migration. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau avant de procéder à la mise hors service.

N’oubliez pas de vérifier les *chemins de mise à niveau pris en charge et non pris en charge*:

- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)

- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)

Si vous avez des *personnalisations*, il est essentiel de planifier chaque étape dans le chemin de migration :

- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)

- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)

|Avantages sur site|Inconvénient sur site|
|---|---|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint (et de son SQL), depuis le serveur.|Tous les sauts et correctifs sont la responsabilité de votre entreprise. Toutefois, vous pouvez contacter le support Microsoft payant si votre produit n’est pas au-delà de la fin du support.|
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.|La mise à niveau, les correctifs, les correctifs de sécurité, les mises à niveau matérielles et toutes les opérations de maintenance de SharePoint Server et de sa batterie SQL sont gérés en local.|
|Accès total pour des options de personnalisation plus importantes que SharePoint Online.|Les [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement en local.|
|Les tests de sécurité et le réglage des performances du serveur sont effectués sur votre site sous votre contrôle.|Microsoft 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server sur site.|
|Les fournisseurs de solutions peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).|Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme indiqué dans SharePoint Online.|
|Contrôle total des conventions d’affectation de noms et des options de sauvegarde et de restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.|SharePoint Server local est sensible au cycle de vie des produits.|

### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par comparer les configurations matérielle et logicielle requises. Si votre environnement actuel ne répond pas aux exigences de base, vous devrez peut-être mettre à niveau le matériel de la batterie ou des serveurs SQL en premier. 

Vous pouvez décider de déplacer certains de vos sites vers le matériel « persistant » de SharePoint Online. Une fois que vous avez effectué votre évaluation, suivez les méthodes et les chemins de mise à niveau pris en charge.

- *Configuration matérielle/logicielle requise pour :*

    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)

- *Limites et frontières logicielles pour :*

    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)

- *Vue d’ensemble du processus de mise à niveau pour :*

    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Créer une solution hybride avec SharePoint Online et SharePoint Server en local

Une configuration hybride offre le meilleur de l’environnement local et de la version en ligne pour certains besoins en matière de migration. Vous pouvez connecter des batteries de serveurs SharePoint Server 2013, 2016 ou 2019 à SharePoint Online pour créer un environnement hybride SharePoint : [en savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Si une batterie de serveurs SharePoint Server hybride est votre objectif de migration, configurez les sites et les utilisateurs à déplacer en ligne et ceux qui doivent rester en local. Classer votre contenu de batterie de serveurs SharePoint comme un impact élevé, moyen ou faible sur votre entreprise peut vous aider dans cette décision. Il se peut que vous deviez partager des comptes d’utilisateur pour la connexion et l’index de recherche SharePoint Server avec SharePoint Online. Toutefois, ce facteur peut ne pas être clair tant que vous n’avez pas pris l’œil sur l’utilisation de vos sites. Si vous décidez par la suite de migrer l’ensemble de votre contenu vers SharePoint Online, vous pouvez déplacer tous les comptes et données restants en ligne et mettre hors service votre batterie de serveurs locale. La gestion/l’administration de la batterie de serveurs SharePoint sera réalisée via les consoles Microsoft 365 à partir de ce point.

Veillez à vous familiariser avec les types de hybrides existants et à configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.

|Option|Description|
|---|---|
|[Offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165).|L’assistance [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.<br/><br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).|
|Les ingénieurs du support technique Microsoft et les employés du centre de connaissances ne disposent pas d’un accès administrateur illimité à votre abonnement.|Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version plus récente de SharePoint, ou si une batterie de serveurs secondaire est requise.|
|Les partenaires peuvent vous aider lors du travail unique de migration de vos données vers SharePoint Online.||
|Les produits en ligne sont mis à jour automatiquement à travers le service. Les fonctionnalités peuvent être désapprouvées, mais il n’y a pas de terminaison de prise en charge.||

Si vous avez décidé de créer un nouveau site Microsoft 365 et de migrer les données manuellement en fonction de vos besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe aucun moyen d’ignorer les versions des mises à niveau de SharePoint. Cela signifie que les mises à niveau sont en série :

- SharePoint 2007 \> SharePoint server 2010 SharePoint server \> 2013 \> SharePoint Server 2016

Pour tirer le chemin d’accès complet de SharePoint 2007 à SharePoint Server 2016, il s’agit d’un investissement considérable en termes de temps et implique le matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et les coûts d’administration. Les personnalisations doivent être mises à niveau ou abandonnées, en fonction de la criticité de la fonctionnalité.

> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 de fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Toutefois, il existe quelques inconvénients à ces déplacements manuels, tels que les déplacements de documents qui remplacent le dernier compte modifié par l’alias du compte qui effectue le déplacement manuel. Et la plupart des tâches doivent être exécutées à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de liste. Dans tous les cas, prenez en compte les données que vous pouvez déplacer dans le stockage ou qui n’ont plus besoin de réduire l’impact de la migration.

Assurez-vous de nettoyer votre environnement avant la mise à niveau. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau, et certainement avant la désaffectation.

N’oubliez pas de vérifier les *chemins de mise à niveau pris en charge et non pris en charge*:

- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)

- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)

- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)

Si vous avez des *personnalisations*, il est essentiel de planifier votre mise à niveau pour chaque étape dans le chemin de migration :

- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)

- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)

- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)

|Pro local|Con local|
|---|---|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, depuis le serveur.|Tous les sauts et correctifs sont la responsabilité de votre entreprise. (Mais vous pouvez contacter le support Microsoft payant si votre produit n’est pas au-delà de la fin du support.)|
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.|La mise à niveau, les correctifs, les correctifs de sécurité et la maintenance de SharePoint Server sur site.|
|Accès total pour une personnalisation accrue.|Les [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement en local.|
|Les tests de sécurité et le réglage des performances du serveur sont effectués sur votre site sous votre contrôle.|Microsoft 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server en local.|
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).|Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme indiqué dans SharePoint Online.|
|Contrôle total des conventions d’affectation de noms et des options de sauvegarde et de restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.|SharePoint Server local est sensible au cycle de vie des produits.|

### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par savoir que vous répondez à la configuration matérielle et logicielle requise, puis suivez les méthodes de mise à niveau prises en charge.

- *Configuration matérielle/logicielle requise pour*:

    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)

- Limites *et frontières logicielles pour*:

    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)

- *Vue d’ensemble du processus de mise à niveau pour*:

    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et l’environnement local

Si la réponse à vos besoins en matière de migration est comprise entre le contrôle offert par le service sur site et le coût de possession le plus bas offert par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Si vous décidez qu’une batterie de serveurs SharePoint Server hybride bénéficiera de votre entreprise, vous devez vous familiariser avec les types d’hybrides existants et configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.

Vous pouvez créer un environnement de développement/test Microsoft 365, que vous pouvez configurer à l’aide de [guides de laboratoire de test](m365-enterprise-test-lab-guides.md). Une fois que vous avez obtenu une version d’évaluation ou un abonnement à Microsoft 365, vous pouvez créer les collections de sites, les sites Web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données. Vous pouvez migrer manuellement, à l’aide de l’API de migration, ou si vous souhaitez migrer le contenu de mon site vers OneDrive entreprise, via l’Assistant hybride.

> [!NOTE]
> Pour utiliser l’option hybride, votre batterie de serveurs SharePoint Server 2010 doit d’abord être mise à niveau sur site vers SharePoint Server 2013 ou 2016. SharePoint Foundation 2010 et SharePoint Foundation 2013 ne prennent pas en charge les connexions hybrides avec SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Fin de la prise en charge des clients et serveurs Office 2010 et de l’affiche Windows 7](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche illustre les différents chemins que vous pouvez suivre pour éviter les produits client et serveur Office 2010 et la fin de la prise en charge de Windows 7, avec des chemins d’accès et des options par défaut dans Microsoft 365 entreprise en surbrillance.

Vous pouvez également [Télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format Letter, Legal ou tabloïd (11 x 17).

## <a name="related-articles"></a>Articles connexes

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007 ou 2010](upgrade-from-office-2010-servers-and-products.md)

[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/mt493301%28v=office.16%29.aspx)

[Meilleures pratiques pour la mise à niveau de SharePoint 2010 vers SharePoint 2013](https://technet.microsoft.com/library/mt493305%28v=office.16%29.aspx)

[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)

[Rechercher des fournisseurs de solutions Microsoft pour vous aider à la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)

[Stratégie de maintenance de produit mise à jour pour SharePoint 2013](https://technet.microsoft.com/library/mt493253%28v=office.16%29.aspx)

[Stratégie de maintenance de produit mise à jour pour SharePoint Server 2016](https://technet.microsoft.com/library/mt782882%28v=office.16%29.aspx)
