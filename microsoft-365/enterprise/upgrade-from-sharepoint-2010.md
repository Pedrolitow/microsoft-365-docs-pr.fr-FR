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
description: Trouvez des informations et des ressources à mettre à niveau SharePoint 2010 et Sharepoint Server 2010. Le support pour les deux se termine le 13 avril 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 67b8174aa23027b64132cc4676e2e7bfb5675cd1deb4684d18945d58b5cf63ad
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53848153"
---
# <a name="upgrading-from-sharepoint-2010"></a>Mise à jour à jour de SharePoint 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft SharePoint 2010 et SharePoint Server 2010 arriveront à la fin du support le **13 avril 2021.** Cet article fournit des ressources pour vous aider à migrer vos données SharePoint Server 2010 existantes vers SharePoint Online dans Microsoft 365 ou à mettre à niveau votre environnement SharePoint Server 2010 local.

## <a name="what-is-end-of-support"></a>Qu’est-ce *que la fin de la prise en charge*?

La plupart des produits Microsoft ont un cycle de vie de support, au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Après la date de fin du support, le produit ne cesse pas de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.

- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura pas de mises à jour, de correctifs ou de correctifs supplémentaires pour le produit (y compris les correctifs/correctifs de sécurité). Le support Microsoft aura entièrement déplacé ses efforts de support vers des versions plus récentes.

À la fin de la prise en charge de SharePoint Server 2010, supprimez les données dont vous n’avez plus besoin avant de mettre à niveau le produit et de migrer vos données importantes.

> [!NOTE]
> Un cycle de vie des logiciels dure généralement dix ans à partir de la version initiale. [Les fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) peuvent vous aider à passer à la prochaine version du logiciel ou à migrer vers Microsoft 365 migration (ou les deux). Assurez-vous de connaître également les dates de fin de prise en charge des technologies sous-jacentes critiques, en particulier pour la version de Microsoft SQL Server que vous utilisez avec SharePoint. Pour plus d’informations, voir [Politique de cycle de vie fixe.](https://support.microsoft.com/help/14085)

## <a name="plan-ahead"></a>Planifier à l’avance

Vérifiez les dates de fin de la prise en charge sur le [site Cycle de vie du produit.](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) Planifiez vos mises à niveau ou migrations en ayant ces dates à l’esprit. N’oubliez *pas que votre produit ne cessera pas de fonctionner* à la date répertoriée. Toutefois, étant donné que votre installation ne sera plus corrigé après cette date, vous souhaiterez planifier une transition en douceur vers la prochaine version du produit.

Cette matrice vous aide à tracer un cours parmi les options de migration :

|Produit de fin de support|Bonne |Idéale|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (local)|SharePoint Online|
||SharePoint Server 2013 hybride avec SharePoint Online|SharePoint Server 2016 (local)|
|||SharePoint Recherche hybride sur le cloud|

Si vous choisissez une option sur le bas de l’échelle (bonne), vous devrez commencer à planifier une autre mise à niveau peu de temps après votre migration à partir de SharePoint Server 2010.

Voici les trois chemins que vous pouvez prendre pour éviter la fin de la prise en charge de SharePoint Server 2010.

![SharePoint Chemins de mise à niveau de Server 2010](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> La fin de la prise en charge de SharePoint Server 2010 et SharePoint Foundation 2010 est actuellement prévue pour le 13 avril 2021. Mais assurez-vous de vérifier le [site de cycle de vie](https://support.microsoft.com/lifecycle) du produit pour les dates les plus à jour.

## <a name="whats-next"></a>Étape suivante

SharePoint Server 2013 et SharePoint Foundation 2013 peuvent être installés en local sur vos propres serveurs. Vous pouvez également utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Vous pouvez :

- Migrez vers SharePoint Online.

- Mettre à niveau SharePoint Server ou SharePoint Foundation en local.

- Faites les deux choses ci-dessus.

- Implémenter [SharePoint solution hybride](/sharepoint/hybrid/hybrid) hybride.

Prenez en compte les coûts masqués liés à la maintenance d’une batterie de serveurs, notamment la maintenance ou la migration des personnalisations et la mise à niveau du matériel. Si vous avez pris en compte ces facteurs, il sera plus facile de mettre à niveau en local. Si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation importante, vous pouvez bénéficier d’une migration planifiée vers SharePoint Online. Pour un environnement local SharePoint Server, vous pouvez également envisager de déplacer certaines données dans SharePoint Online afin de réduire la surcharge de gestion du matériel.

> [!NOTE]
> SharePoint administrateurs peuvent créer un abonnement Microsoft 365, configurer de nouveaux sites SharePoint Online, puis supprimer proprement SharePoint Server 2010, en prenant uniquement les documents essentiels vers les sites nouveaux. Ensuite, les données restantes peuvent être drainées du site SharePoint Server 2010 dans des archives sur site.

|SharePoint Online|SharePoint Serveur local|
|---|---|
|Coût élevé en temps (plan/exécution/vérification)|Coût élevé en temps (plan/exécution/vérification)|
|Moindre coût en fonds (aucun achat de matériel)|Coût plus élevé des fonds (achats de matériel)|
|Coût one-time lors de la migration|Coût à durée de vie répété par migration future|
|Faible coût total de possession/maintenance|Coût total élevé de possession/maintenance|

Un déplacement à une seule Microsoft 365 aura un coût plus élevé pendant que vous organisez les données et décidez de ce qu’il faut prendre dans le cloud et ce qu’il faut laisser. Mais une fois vos données migrées, les futures mises à niveau seront automatiques, car vous n’aurez plus besoin de gérer les mises à jour matérielles et logicielles. Et la durée de vie de votre batterie de serveurs sera d’après un contrat de niveau de [service (SLA) Microsoft.](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)

### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous SharePoint Online offre toutes les fonctionnalités dont vous avez besoin. Voir [SharePoint description du service.](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)

Vous ne pouvez pas migrer directement de SharePoint Server 2010 (ou SharePoint Foundation 2010) vers SharePoint Online. La plus grande partie du travail de migration est manuelle. Toutefois, cette étape vous donne la possibilité d’assaguer les données et les sites qui ne sont plus nécessaires avant le déplacement. Vous pouvez archiver d’autres données dans le stockage. 

N’oubliez SharePoint Server 2010 et SharePoint Foundation 2010 ne cesseront pas de fonctionner à la fin du support. Ainsi, les administrateurs peuvent avoir une période pendant SharePoint en cours d’exécution si leurs clients oublient de déplacer certaines de leurs données.

Si vous mettez à niveau vers SharePoint Server 2013 ou SharePoint Server 2016 et décidez de placer des données dans SharePoint Online, vous pouvez utiliser l’API de [migration SharePoint](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) pour migrer des informations vers OneDrive Entreprise.

|SharePoint Avantage en ligne|SharePoint Inconvénient en ligne|
|---|---|
|Microsoft fournit le matériel SPO et l’administration de tout le matériel.|Les fonctionnalités disponibles peuvent différer entre SharePoint server local et SPO.|
|Vous êtes l’administrateur général de votre abonnement et pouvez affecter des administrateurs à des sites SPO.|Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server local n’existent pas (ou ne sont pas nécessaires) dans le rôle administrateur SharePoint dans Microsoft 365. Toutefois, SharePoint administration, l’administration de la collection de sites et la propriété du site sont locales pour votre organisation.|
|Microsoft applique des correctifs, des correctifs et des mises à jour au matériel et aux logiciels sous-jacents, notamment SQL serveurs sur lesquels SharePoint Online s’exécute.|Étant donné qu’il n’y a pas d’accès au système de fichiers sous-jacent dans le service, la personnalisation est limitée.|
|Microsoft publie des [contrats de niveau de service](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) et se déplace rapidement pour résoudre les incidents au niveau du service.|Les options de sauvegarde et de restauration et d’autres options de récupération sont automatisées par le service dans SharePoint Online. Les sauvegardes sont écrasées si elles ne sont pas utilisées.|
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués en continu dans le service par Microsoft.|Les modifications apportées à l’interface utilisateur et aux autres fonctionnalités SharePoint sont installées par le service et peuvent avoir besoin d’être togged ou off.|
|Microsoft 365 répond à de nombreuses normes du secteur : [offres de conformité Microsoft](/compliance/regulatory/offering-home).|[L’assistance FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pour la migration est limitée.  <br/> La majeure partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans SharePoint Online et OneDrive feuille de route [du contenu de migration.](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets)|
|Les ingénieurs du support Microsoft et les employés du centre de données n’ont pas un accès administrateur illimité à votre abonnement.|Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la nouvelle version de SharePoint ou si une batterie secondaire est requise pour la mise à niveau.|
|Les fournisseurs de solutions peuvent vous aider à migrer vos données vers SharePoint Online.|Les modifications apportées à SharePoint Online ne sont pas toutes dans votre contrôle. Après la migration, les différences de conception dans les menus, les bibliothèques et d’autres fonctionnalités peuvent temporairement affecter l’utilisation.|
|Les produits en ligne sont mis à jour automatiquement dans l’ensemble du service. Les fonctionnalités peuvent se déprécier, mais il n’y a pas de véritable fin de cycle de vie du support.|Il existe un cycle de vie de fin de support pour SharePoint Server ou SharePoint Foundation, ainsi que pour les serveurs SQL sous-jacents.|

Si vous avez décidé de créer un site Microsoft 365 et migrez manuellement les données vers ce site si nécessaire, vérifiez vos [options Microsoft 365 de migration.](https://www.microsoft.com/microsoft-365/)

### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à SharePoint serveur local

À partir SharePoint Server 2019, les mises à niveau doivent être *mises à niveau en série.* Il n’existe aucun moyen de mettre à niveau SharePoint Server 2010 vers SharePoint Server 2016 ou vers SharePoint 2019 directement. Chemin de mise à niveau en série :

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Le suivi de l’intégralité du chemin d’accès entre SharePoint 2010 et SharePoint Server 2016 prendra du temps. Les mises à niveau impliquent des coûts pour le matériel (SQL serveurs doivent également être mis à niveau), les logiciels et l’administration. En outre, les personnalisations peuvent avoir besoin d’être mises à niveau ou même abandonnées. Veillez à documenter les personnalisations critiques avant de mettre à niveau SharePoint batterie de serveurs.

> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2010 de fin de prise en charge, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (afin que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle du contenu (pour télécharger et télécharger à nouveau du contenu, par exemple). Toutefois, ces déplacements manuels peuvent avoir des inconvénients, tels que les documents provenant de l’année 2010 ayant un compte de dernière modification actuel avec l’alias du compte qui le déplace manuellement. Et certains travaux doivent être effectués à l’avance, tels que la recréation de sites, de sous-sites, d’autorisations et de structures de listes. Veillez à nettoyer votre environnement avant la mise à niveau. Réfléchissez aux données que vous pouvez déplacer dans le stockage ou dont vous n’avez plus besoin. Cela peut réduire l’impact de la migration. Veillez à ce que votre batterie de serveurs existante soit fonctionnelle avant de mettre à niveau, et (certainement) avant de la désaffecter !

N’oubliez pas de passer en revue les *chemins de* mise à niveau pris en charge et non pris en charge :

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Si vous avez *des personnalisations,* il est essentiel de planifier chaque étape du chemin de migration :

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Avantage local|Inconvénient local|
|---|---|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint (et de ses SQL), à partir du matériel du serveur.|Toutes les interruptions et correctifs sont la responsabilité de votre entreprise. Toutefois, vous pouvez engager le Support Microsoft payant si votre produit n’a pas passé la fin du support.|
|Ensemble complet de fonctionnalités SharePoint Server local avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un abonnement hybride.|La mise à niveau, les correctifs, les correctifs de sécurité, les mises à niveau matérielles et toute la maintenance de SharePoint Server et de sa batterie de serveurs SQL sont gérés en local.|
|Accès complet pour des options de personnalisation plus importantes qu’avec SharePoint Online.|[Les offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.|
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués sur votre site sous votre contrôle.|Microsoft 365 pouvez mettre à la disposition de SharePoint Online qui n’interaront pas avec SharePoint Server local.|
|Les fournisseurs de solutions peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).|Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) comme le permet SharePoint Online.|
|Contrôle total des conventions d’attribution de noms, de la sauvegarde et de la restauration et d’autres options de récupération dans SharePoint Server local.|SharePoint Le serveur local est sensible aux cycles de vie des produits.|

### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par comparer la configuration matérielle et logicielle requise. Si votre environnement actuel ne répond pas aux exigences de base, vous de devez d’abord mettre à niveau le matériel de la batterie de serveurs ou SQL serveurs. 

Vous pouvez décider de déplacer certains de vos sites vers le matériel « persistant » de SharePoint Online. Une fois que vous avez effectué votre évaluation, suivez les chemins et méthodes de mise à niveau pris en charge.

- *Configuration matérielle/logicielle requise pour :*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0)  |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Limites et frontières logicielles pour :*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits)  |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Vue d’ensemble du processus de mise à niveau pour :*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14))  |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)  |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Créer une solution hybride avec SharePoint Online et SharePoint Server local

Une configuration hybride offre le meilleur des configurations en local et en ligne pour certains besoins de migration. Vous pouvez connecter SharePoint batteries de serveurs server 2013, 2016 ou 2019 à SharePoint Online pour créer un environnement SharePoint hybride : découvrez SharePoint [solutions hybrides.](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Si une batterie de serveurs SharePoint hybride est votre objectif de migration, vous devez déterminer les sites et les utilisateurs à déplacer en ligne et qui doivent rester en local. Le classement du SharePoint de votre batterie de serveurs avec un impact élevé, moyen ou faible sur votre entreprise peut vous aider à prendre cette décision. Vous devrez peut-être partager des comptes d’utilisateur uniquement pour la connexion et l’index de recherche SharePoint Server avec SharePoint Online. Toutefois, ce facteur n’est peut-être pas clair tant que vous n’avez pas d’examiner la façon dont vos sites sont utilisés. Si votre entreprise décide ultérieurement de migrer tout votre contenu vers SharePoint Online, vous pouvez déplacer tous les comptes et données restants en ligne et désaffecter votre batterie de serveurs sur site. La gestion/l’administration SharePoint batterie de serveurs sera effectuée via Microsoft 365 consoles à partir de ce moment- là.

N’oubliez pas de vous familiariser avec les types d’hybrides existants et de configurer la connexion entre votre batterie de serveurs SharePoint sur site et votre abonnement Microsoft 365 local.

|Option|Description|
|---|---|
|[Offres de conformité Microsoft](/compliance/regulatory/offering-home).|[L’assistance FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.<br/><br/> La majeure partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans SharePoint Online et OneDrive feuille de route [du contenu de migration.](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets)|
|Les ingénieurs du support Microsoft et les employés du centre de données n’ont pas un accès administrateur illimité à votre abonnement.|Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la nouvelle version de SharePoint, ou si une batterie secondaire est requise.|
|Les partenaires peuvent vous aider à migrer vos données vers SharePoint Online.||
|Les produits en ligne sont mis à jour automatiquement dans l’ensemble du service. Les fonctionnalités peuvent se déprécier, mais il n’y a pas de véritable fin de prise en charge.||

Si vous avez décidé de créer un site Microsoft 365 et de migrer manuellement les données vers ce site selon vos besoins, vérifiez vos [options Microsoft 365 de migration.](https://www.microsoft.com/microsoft-365/)

### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à SharePoint serveur local

Il n’existe aucun moyen d’ignorer les versions SharePoint mises à niveau. Cela signifie que les mises à niveau sont mises à niveau en série :

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Pour passer de SharePoint 2007 à SharePoint Server 2016, cela implique un investissement important en temps et implique du matériel (les serveurs SQL doivent également être mis à niveau), des logiciels et des coûts d’administration. Les personnalisations doivent être mises à niveau ou abandonnées, en fonction de la critique de la fonctionnalité.

> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 en fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle du contenu (pour télécharger et télécharger à nouveau du contenu, par exemple). Toutefois, ces déplacements manuels ont certains inconvénients, tels que les déplacements de documents remplaçant le dernier compte modifié par l’alias du compte qui le déplace manuellement. Et beaucoup de travail doit être effectué à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de listes. Dans tous les cas, réfléchissez aux données que vous pouvez déplacer dans le stockage ou que vous n’avez plus besoin de réduire l’impact de la migration.

Veillez à nettoyer votre environnement avant la mise à niveau. Veillez à ce que votre batterie de serveurs existante soit fonctionnelle avant la mise à niveau et avant de la désaffecter !

N’oubliez pas de passer en revue les *chemins de* mise à niveau pris en charge et non pris en charge :

- 
  [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Si vous avez *des personnalisations,* il est essentiel de planifier votre mise à niveau pour chaque étape du chemin de migration :

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Professionnel local|Con local|
|---|---|
|Contrôle total de tous les aspects de votre batterie de SharePoint, à partir du matériel du serveur.|Toutes les interruptions et correctifs sont la responsabilité de votre entreprise. (Mais vous pouvez engager le Support Microsoft payant si votre produit n’a pas fini de prendre en charge.)|
|Ensemble complet de fonctionnalités SharePoint Server local avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un abonnement hybride.|Mise à niveau, correctifs, correctifs de sécurité et maintenance SharePoint Server géré en local.|
|Accès complet pour une personnalisation plus importante.|[Les offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.|
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués sur votre site sous votre contrôle.|Microsoft 365 pouvez mettre à la disposition de SharePoint Online qui ne fonctionnent pas avec SharePoint Server local.|
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).|Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) comme le permet SharePoint Online.|
|Contrôle total des conventions d’attribution de noms, de la sauvegarde et de la restauration et d’autres options de récupération dans SharePoint Server local.|SharePoint Le serveur local est sensible aux cycles de vie des produits.|

### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Commencez par savoir que vous respectez la configuration matérielle et logicielle requise, puis suivez les méthodes de mise à niveau prise en charge.

- *Configuration matérielle/logicielle requise pour*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0)  |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Limites et frontières logicielles pour*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits)  |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Vue d’ensemble du processus de mise à niveau pour*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14))  |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)  |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et en local

Si la réponse à vos besoins de migration se situe quelque part entre le contrôle proposé en local et le coût de possession inférieur proposé par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur SharePoint solutions hybrides](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Si vous décidez qu’une batterie de serveurs SharePoint hybride bénéficiera à votre entreprise, familiarisez-vous avec les types d’hybrides existants et comment configurer la connexion entre votre batterie de serveurs SharePoint sur site et votre abonnement Microsoft 365.

Vous pouvez créer un environnement de Microsoft 365/test, que vous pouvez configurer à l’aide des [Guides de laboratoire de test.](m365-enterprise-test-lab-guides.md) Après avoir acheté un abonnement d’essai ou Microsoft 365, vous pouvez créer les collections de sites, les sites web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données. Vous pouvez migrer manuellement, à l’aide de l’API de migration, ou, si vous souhaitez migrer le contenu du Site Mon site vers OneDrive Entreprise, via l’Assistant hybride.

> [!NOTE]
> Pour utiliser l’option hybride, votre batterie de serveurs SharePoint Server 2010 doit d’abord être mise à niveau en local vers SharePoint Server 2013 ou 2016. SharePoint Foundation 2010 et SharePoint Foundation 2013 ne prisent pas en charge les connexions hybrides avec SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client Office 2010 et les serveurs et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![End of support for Office 2010 clients and servers and Windows 7 poster](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche illustre les différents chemins d’accès que vous pouvez prendre pour éviter les produits client et serveur Office 2010 et la fin de la prise en charge de Windows 7, avec des chemins d’accès et des options préférés pris en charge dans Microsoft 365 Entreprise mis en évidence.

Vous pouvez également [télécharger cette](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="related-articles"></a>Articles connexes

[Ressources pour vous aider à mettre à niveau Office serveurs et clients 2007 ou 2010](upgrade-from-office-2010-servers-and-products.md)

[Vue d’ensemble du processus de mise à niveau de SharePoint 2010 vers SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[Meilleures pratiques pour la mise à niveau de SharePoint 2010 vers SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Rechercher des fournisseurs de solutions Microsoft pour vous aider dans votre mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)

[Stratégie de maintenance de produit mise à jour pour SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[Stratégie de maintenance de produit mise à jour pour SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)